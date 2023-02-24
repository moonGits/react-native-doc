# 入门


### React 基础
- #### React Native 是一个使用React和应用平台的原生功能来构建 Android 和 iOS 应用的开源框架。 基础是React.
- #### React 的核心概念:
  - components 组件
  - JSX（ES6）
  - props 属性
  - state 状态
 
---

### 核心组件与原生组件

  <img src="../images/diagram_react-native-components.svg"/>

- #### 视图（Views）与移动开发
  在 Android 和 iOS 开发中，视图是 UI 的基本组成部分。应用程序最小的视觉元素（例如一行文本或一个按钮）也都是各种视图。某些类型的视图可以包含其他视图。全部都是视图。Android和iOS应用中多种视图的一些示例。如下图：  
  <img src="../images/diagram_ios-android-views.svg"/>
- #### 原生组件
  Android 开发中是使用 Kotlin 或 Java 来编写视图；在 iOS 开发中是使用 Swift 或 Objective-C 来编写视图。在 React Native 中，则使用 React 组件通过 JavaScript 来调用这些视图。在运行时，React Native 为这些组件创建相应的 Android 和 iOS 视图。本质上,React Native 组件就是对原生视图的封装。这些平台支持的组件称为原生组件。
  React Native 允许我们为 Android 和 iOS 构建自己的 Native Components（原生组件）
- #### 核心组件
  React Native 包括一组基本的，随时可用的原生组件，可以使用它们来构建应用程序。这些是 React Native 的核心组件。
  React Native 具有许多核心组件，从表单控件到活动指示器，应有尽有。

  常用的的核心组件：
  <table><thead><tr><th>React Native UI Component</th><th>Android View</th><th>iOS View</th><th>Web Analog</th><th>说明</th></tr></thead><tbody><tr><td><code>&lt;View&gt;</code></td><td><code>&lt;ViewGroup&gt;</code></td><td><code>&lt;UIView&gt;</code></td><td>A non-scrollling <code>&lt;div&gt;</code></td><td>A container that supports layout with flexbox, style, some touch handling, and accessibility controls</td></tr><tr><td><code>&lt;Text&gt;</code></td><td><code>&lt;TextView&gt;</code></td><td><code>&lt;UITextView&gt;</code></td><td><code>&lt;p&gt;</code></td><td>Displays, styles, and nests strings of text and even handles touch events</td></tr><tr><td><code>&lt;Image&gt;</code></td><td><code>&lt;ImageView&gt;</code></td><td><code>&lt;UIImageView&gt;</code></td><td><code>&lt;img&gt;</code></td><td>Displays different types of images</td></tr><tr><td><code>&lt;ScrollView&gt;</code></td><td><code>&lt;ScrollView&gt;</code></td><td><code>&lt;UIScrollView&gt;</code></td><td><code>&lt;div&gt;</code></td><td>A generic scrolling container that can contain multiple components and views</td></tr><tr><td><code>&lt;TextInput&gt;</code></td><td><code>&lt;EditText&gt;</code></td><td><code>&lt;UITextField&gt;</code></td><td><code>&lt;input type="text"&gt;</code></td><td>Allows the user to enter text</td></tr></tbody></table>

---

