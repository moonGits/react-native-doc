# connectivity


### Networking
#### Fetch
- ##### request
    - 要从任意地址获取内容的话，只需简单地将网址作为参数传递给 fetch 方法即可：
    fetch('https://mywebsite.com/mydata.json');
    </br>
    - Fetch 还有可选的第二个参数，可以用来定制 HTTP 请求一些参数。你可以指定 header 参数，或是指定使用 POST 方法，又或是提交数据等等:
    fetch('https://mywebsite.com/endpoint/', {
    method: 'POST',
    headers: {
        Accept: 'application/json',
        'Content-Type': 'application/json',
    },
    body: JSON.stringify({
        firstParam: 'yourValue',
        secondParam: 'yourOtherValue',
    }),
    });    

- ##### response
    - Promise:
    const getMoviesFromApi = () => {
    return fetch('https://reactnative.dev/movies.json')
        .then(response => response.json())
        .then(json => {
        return json.movies;
        })
        .catch(error => {
        console.error(error);
        });
    };
    - async / await:
    const getMoviesFromApiAsync = async () => {
    try {
        const response = await fetch(
        'https://reactnative.dev/movies.json',
        );
        const json = await response.json();
        return json.movies;
    } catch (error) {
        console.error(error);
    }
    };

#### Other Networking Libraries
    React Native中已经内置了XMLHttpRequest API(ajax)。一些基于 XMLHttpRequest 封装的第三方库也可以使用，例如frisbee或是axios等。
    const request = new XMLHttpRequest();
    request.onreadystatechange = (e) => {
    if (request.readyState !== 4) {
        return;
    }

    if (request.status === 200) {
        console.log('success', request.responseText);
    } else {
        console.warn('error');
    }
    };

    request.open('GET', 'https://mywebsite.com/endpoint/');
    request.send();

#### WebSocket Support
    const ws = new WebSocket('ws://host.com/path');

    ws.onopen = () => {
    // connection opened
    ws.send('something'); // send a message
    };

    ws.onmessage = (e) => {
    // a message was received
    console.log(e.data);
    };

    ws.onerror = (e) => {
    // an error occurred
    console.log(e.message);
    };

    ws.onclose = (e) => {
    // connection closed
    console.log(e.code, e.reason);
    }

--- 

### Security
<img src="../images/d_security_chart.svg"/>

#### Storing Sensitive Info
- ##### Async Storage
        Async Storage是React Native的社区维护模块，提供异步、未加密的密钥值存储。
        数据无法在应用程序之间共享。（每个应用程序都有自己的沙盒环境，无法访问其他应用程序的数据）
    <table><thead><tr><th><strong>Do</strong> use async storage when...</th><th><strong>Don't</strong> use async storage for...</th></tr></thead><tbody><tr><td>Persisting non-sensitive data across app runs</td><td>Token storage</td></tr><tr><td>Persisting Redux state</td><td>Secrets</td></tr><tr><td>Persisting GraphQL state</td><td></td></tr><tr><td>Storing global app-wide variables</td><td></td></tr></tbody></table>
- ##### Secure Storage
    React Native不附带任何存储敏感数据的方法。Android和iOS原生平台是具备的。
  - 原生安全存储
    - iOS - Keychain Services
      存储 certificates, tokens, passwords, and any 其他 sensitive information
    - Android - Secure Shared Preferences
      Android持久密钥值数据存储
    - Android - Keystore
      非对称加密存储
  - RN集成的Lib
    - react-native-keychain
    - react-native-sensitive-info
    - redux-persist-sensitive-storage

- ##### Authentication and Deep Linking
  - Deep Linking
    - what
      - 它可以唤起指定应用并向其传递数据，根据传递的数据显示特定内容页的详细信息；
      - 它不再受制于应用，只通过一个链接便可唤起应用并跳转到指定页面；
      - 它使应用之间产生了联系，使应用不再孤立存在；
      - 它优化了用户体验，这一点是它最终要达到的目的
    - unsecure
    <img src="../images/d_security_deep-linking.svg"/>
    app没有集中管理注册url的机制。这也就意味着，如果我们通过deeplinking发送敏感信息会被恶意软件拦截。
      
  - OAuth2 and Redirects
    <img src="../images/diagram_pkce-e0b4a829176ac05d07b0bcec73994985.svg"/>
