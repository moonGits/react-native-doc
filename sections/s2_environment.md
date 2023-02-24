# 环境


### 搭建开发环境
    开发平台: macOS (Windos/Linux)
    目标平台: Android iOS

- #### 安装依赖
        必须安装的依赖有：Node、JDK、Android Studio、Watchman、Xcode CocoaPods。
        虽然可以使用任何编辑器来开发应用（编写 js 代码），但仍然必须安装 Android Studio/Xcode 来获得编译 Android/iOS 应用所需的工具和环境。

- #### Node & Watchman
        watchman是由 Facebook 提供的监视文件系统变更的工具，优化了reload文件遍历机制，加入watchman的RN，reload会加快，没加的会遍历量很高，很慢。

    macOS推荐使用Homebrew(macOS包管理器)安装依赖。安装命令:
    <table>
    <tr><td bgcolor=#000000><font color=#FFFFF>brew install node
    <br/> brew install watchman</font></td></tr>
    </table>
   
   安装完 Node 后建议设置 npm 镜像（淘宝源)
    - 使用nrm工具切换淘宝源
        <table><tr><td bgcolor=#000000><font color=#FFFFF>npx nrm use taobao</font></td></tr></table>

    - 如果之后需要切换回官方源可使用
        <table><tr><td bgcolor=#000000><font color=#FFFFF>npx nrm use npm</font></td></tr></table>

- #### Yarn
    Yarn是 Facebook 提供的替代 npm 的工具，可以加速 node 模块的下载。
    <table><tr><td bgcolor=#000000><font color=#FFFFF>npm install -g yarn</font></td></tr></table>
    安装完 yarn 之后就可以用 yarn 代替 npm 了，例如用yarn代替npm install命令，用yarn add 某第三方库名代替npm install 某第三方库名。

- #### Java Development Kit
    安装由 Azul 提供的 名为 Zulu 的 OpenJDK 发行版。此发行版同时为 Intel 和 M1 芯片提供支持。在 M1 芯片架构的 Mac 上相比其他 JDK 在编译时有明显的性能优势
    <table>
    <tr><td bgcolor=#000000><font color=#FFFFF>brew tap homebrew/cask-versions 
    <br/> brew install --cask zulu11</font></td></tr>
    </table>

- #### Android 开发环境
  - ##### 安装 Android Studio。
    安装界面中选择"Custom"选项，确保选中了以下几项：
    - Android SDK
    - Android SDK Platform
    - Android Virtual Device
  - ##### 安装 Android SDK
    Android Studio 默认会安装最新版本的 Android SDK。目前编译 React Native 应用需要的是Android 12 (S)版本的 SDK（注意 SDK 版本不等于终端系统版本，RN 目前支持 android 5 以上设备）。可以在 Android Studio 的 SDK Manager 中选择安装各版本的 SDK。
    - 在 SDK Manager 确保安装：
      - Android SDK Platform 31
      - Intel x86 Atom_64 System Image(官方模拟器镜像文件，使用非官方模拟器不需要安装此组件)
  - ##### 配置 ANDROID_SDK_ROOT 环境变量
    React Native 需要通过环境变量来了解你的 Android SDK 装在什么路径，从而正常进行编译。具体的做法是把下面的命令加入到 shell 的配置文件中。如果你的 shell 是 zsh，则配置文件为~/.zshrc，如果是 bash 则为~/.bash_profile（可以使用echo $0命令查看你所使用的 shell。）:
    <table>
    <tr><td bgcolor=#000000>
    <font color=GRAY># 如果你不是通过Android Studio安装的sdk，则其路径可能不同，请自行确定清楚 </font><br/>
    <font color=#FFFFF>
    export ANDROID_SDK_ROOT=$HOME/Library/Android/sdk
    <br/> export PATH=$PATH:$ANDROID_SDK_ROOT/emulator
    <br/> export PATH=$PATH:$ANDROID_SDK_ROOT/tools
    <br/> export PATH=$PATH:$ANDROID_SDK_ROOT/tools/bin
    <br/> export PATH=$PATH:$ANDROID_SDK_ROOT/platform-tools
    </font></td></tr>
    </table>

- #### iOS开发环境
  - ##### Xcode 的命令行工具
    启动 Xcode，并在Xcode | Preferences | Locations菜单中检查一下是否装有某个版本的Command Line Tools。Xcode 的命令行工具中包含一些必须的工具，比如git等。
  - ##### 在 Xcode 中安装 iOS 模拟器
    安装模拟器只需打开 Xcode > Preferences... 菜单，然后选择 Components 选项，即可看到各种可供安装的不同的 iOS 版本的模拟器。
  - ##### CocoaPods
    CocoaPods是用 Ruby 编写的包管理器（可以理解为针对 iOS 的 npm）。从 0.60 版本开始 react native 的 iOS 版本需要使用 CocoaPods 来管理依赖。你可以使用下面的命令来安装 CocoaPods。CocoaPods 的版本需要 1.10 以上。 
    <table><tr><td bgcolor=#000000><font color=#FFFFF>sudo gem install cocoapods</font></td></tr><tr><td bgcolor=#000000><font color=#FFFFF>brew install cocoapods</font></td></tr></table>

- #### 创建新项目
    使用 React Native 内建的命令行工具来创建一个名为"AwesomeProject"的新项目。这个命令行工具不需要安装，可以直接用 node 自带的npx命令来使用（注意 init 命令默认会创建最新的版本）：
    <table><tr><td bgcolor=#000000><font color=#FFFFF>npx react-native init AwesomeProject</font></td></tr></table>

    [可选参数] 指定版本或项目模板:
    - 你可以使用--version参数（注意是两个杠）创建指定版本的项目。注意版本号必须精确到两个小数点。
    <table><tr><td bgcolor=#000000><font color=#FFFFF>npx react-native init AwesomeProject --version X.XX.X</font></td></tr></table>

    - 还可以使用--template来使用一些社区提供的模板，例如带有TypeScript配置的：
    <table><tr><td bgcolor=#000000><font color=#FFFFF>npx react-native init AwesomeTSProject --template react-native-template-typescript</font></td></tr></table>

- #### 编译并运行 React Native 应用
    <table>
    <tr><td bgcolor=#000000>
    <font color=#FFFFF>
    cd AwesomeProject
    <br/> yarn ios/android
    <br/> # 或者
    <br/> yarn react-native run-ios/android
    </font></td></tr>
    </table>

    上述命令会对项目的原生部分进行编译，同时在另外一个命令行中启动Metro服务对 js 代码进行实时打包处理（类似 webpack）。Metro服务也可以使用yarn start命令单独启动。
    启动成功如下图:
    <img src="../images/GettingStartediOSSuccess-e6dd7fc2baa303d1f30373d996a6e51d.png"/>


