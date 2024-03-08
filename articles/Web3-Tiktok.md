---
theme: github
---

## 目录

*   [项目准备](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-prerequisites)

*   [创建 React Native 项目](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-react-native-app)

    *   [设置导航](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-the-navigation)
    *   [设置 GraphQL 客户端](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-graphql-client)
    *   [设置 Livepeer](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-livepeer)
    *   [设置 WalletConnect](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-walletconnect)
    *   [设置客户端](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-the-clients)

*   [验证](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-authentication)

    *   [连接用户钱包](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-connecting-user-wallet)
    *   [签署消息](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-signing-the-message)

*   [主页](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-home)

    *   [设置底部选项卡](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-bottom-tabs)
    *   [从 Lens 获取视频](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-fetching-videos-from-lens)
    *   [添加视频播放器](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-adding-the-video-player)

*   [上传](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-upload)

    *   [上传视频到 Livepeer](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-uploading-video-to-livepeer)
    *   [将元数据保存到 IPFS](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-saving-metadata-to-ipfs)
    *   [将元数据发布到 Lens API](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-posting-the-metadata-to-lens-api)

*   [下一步是什么？](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-whats-next)

*   [总结](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-conclusion)


---


> 对于任何想要理解和开发去中心化项目的人来说，在 Web3 中构建现实世界的项目非常重要。获得使用最新技术和框架构建功能项目的实践经验至关重要。

> 通过参与 Tiktok 克隆等项目，您可以了解 Web3 的各个方面，例如社交图、数据查询、视频基础设施和钱包身份验证。这些技能可用于开发更复杂、更精密的去中心化项目，为互联网的未来铺平道路。

在本教程中，您将使用以下技术栈 构建全栈 Tiktok 克隆。

*   移动框架：React Native
*   社交图谱：Lens Protocol
*   查询数据：Lens API
*   视频基础设施：Livepeer
*   钱包认证：WalletConnect

[**您可以在此处**](https://github.com/suhailkakar/decentralized-tiktok)找到项目的最终代码。

## 项目准备

在开始学习本教程之前，请确保您的计算机上安装了[**Node.js**](https://nodejs.org/en/) v16 或更高版本以及[Expo CLI](https://docs.expo.dev/workflow/expo-cli/)。

### [创建 React Native 项目](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-react-native-app "永久链接")

首先，您需要设置一个 React Native 项目并安装所需的依赖项。为此，只需在终端中运行以下命令：

```cmd
npx create-expo-app web3-tiktok
```

此命令使用 Expo CLI 创建一个新的 React Native 项目。该过程可能需要一些时间，具体取决于您的机器和互联网连接的速度。成功创建项目后，运行以下命令来安装其他依赖项。

> 译者更推荐 pnpm
>> `npm install -g pnpm `

```cmd
cd web3-tiktok && pnpm add react-native-webview react-native-walletconnect @react-native-async-storage/async-storage @apollo/client graphql @livepeer/react-native @react-navigation/native @react-navigation/stack react-native-screens react-native-safe-area-context @react-navigation/material-bottom-tabs expo-media-library react-native-gesture-handler expo-av livepeer react-native-svg
```

*   `react-native-walletconnect`为我们的项目提供了一种使用 WalletConnect 连接用户的加密钱包的方法。这很重要，因为我们想用钱包对用户进行身份验证。
*   `@react-native-async-storage/async-storage`提供了一种在我们的项目中存储键值数据的简单方法。我们可以用它来保存不同的数据，例如身份验证令牌、用户 ID 等。
*   `@apollo/client`是一个包，可让我们轻松地将您的项目连接到 GraphQL 服务器（Lens API）。
*   `graphql`是一种 API 查询语言，可与`@apollo/client`.
*   `@livepeer/react-native`是一个提供组件和挂钩的包，可以让我们在 React Native 项目中更轻松地使用 Livepeer 的视频基础设施。
*   `@react-navigation/native`是一个用于在 React Native 项目中实现导航的库
*   `react-native-screens`提供了一种在 React Native 项目中管理屏幕和转换的简单方法
*   `react-native-safe-area-context`用于处理我们项目中的安全区域插图
*   `@react-navigation/material-bottom-tabs`是一个用于在我们的项目中实现底部选项卡导航的包
*   `expo-media-library`用于访问和管理用户设备上的媒体资产（例如视频）

是的，我知道这个清单很长。但是，嘿，我们必须拥有所有这些库才能使我们的项目顺利运行。我的意思是，我们正在构建一个 Tiktok 克隆，所以我们必须确保它是正确的！

## 设置导航

现在我们可以继续并向我们的项目添加导航。我们将使用react-navigation，这是一个广泛用于反应本机项目的导航库。

首先，在项目的根目录中创建一个名为`screens`的新文件夹。然后，在该文件夹中创建一个名为`Login.js`. 现在，您可以将下面的简单代码片段添加到`Login.js`文件中，该代码片段将仅显示以下单词`Login Screen`：

```jsx
import { StyleSheet, Text, View } from 'react-native'
import React from 'react'

export default function Login() {
    return (
        <View style={styles.container}>
            <Text>Login Screen</Text>
        </View>
    )
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: "center",
        backgroundColor: "#fff",
        alignItems: "center"
    }
})
```

接下来，在根目录中创建一个名为`routes.js`的新文件，并将以下代码添加到其中。此代码导入我们刚刚创建的登录屏幕并将其添加到导航容器中：

```jsx
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import Login from './screens/Login';

const Stack = createStackNavigator();

function Routes() {
    return (
        <NavigationContainer>
            <Stack.Navigator
                screenOptions={{
                    headerShown: false
                }}
            >
                <Stack.Screen name="Login" component={Login} />
            </Stack.Navigator>
        </NavigationContainer>
    );
}
export default Routes;
```

最后，将`app.js`中现有的代码替换为以下代码，以导入并定义路由文件

```jsx
import React from 'react'
import Routes from './routes'

export default function App() {
  return (
    <Routes />
  )
}
```

通过这些步骤，我们已经为项目设置了基本的导航结构，现在我们可以根据需要轻松添加更多屏幕和导航选项。

### [设置 GraphQL 客户端](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-graphql-client "永久链接")

现在让我们设置 GraphQL 客户端，它允许我们与 Lens API 进行交互。我们将使用 Apollo GraphQL，这是一种流行且高效的设置 GraphQL 客户端的方法。

GraphQL 是一种开源查询语言，提供灵活且用户友好的语法来描述数据需求和交互。作为 REST 的替代方案，您可以创建 GraphQL 请求，其中包含来自单个 API 调用的各种来源的数据。

首先，在根目录中创建一个名为`clients`的新文件夹。在该`clients`文件夹内，创建一个名为`apollo.js`的新文件，并将以下代码添加到该文件中：

```jsx
import { ApolloClient, InMemoryCache } from "@apollo/client";

const APClient = new ApolloClient({
    link: "https://api-mumbai.lens.dev",
    cache: new InMemoryCache(),
});

export default APClient;
```

> *`https://api-mumbai.lens.dev`是用于测试网的Lens API，您可以用于`https://api.lens.dev/`主网。有关更多信息，请参阅[Lens 文档](https://docs.lens.xyz/docs/api-links)。*

### 设置 Livepeer

Livepeer 是一个去中心化视频处理网络和开发者平台，您可以使用它来构建视频项目。它速度非常快、易于集成且价格便宜。在本教程中，我们将使用 Livepeer 上传视频并播放它们。

如前所述，Livepeer 将用作我们项目中的视频基础设施。它会自动对用户上传的视频进行转码和服务，以实现无缝播放。

导航到 **[livepeer.studio/](https://livepeer.studio/register)** 然后在 Livepeer Studio 上注册并创建一个新帐户。

创建帐户后，在仪表板中，单击侧边栏上的**开发人员。**

然后，单击 **“创建 API 密钥”**， 为您的密钥命名，然后复制它，因为我们稍后会需要它。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a82a3e2618df4179888a2ece9d3b8261~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=3544\&h=2362\&s=146103\&e=jpg\&b=fdfdfd)

> Livepeer.js 是一个 JavaScript SDK，带有现成的钩子，使我们能够快速上传视频、提供视频并连接到 Livepeer Studio。

然后，在您之前创建的文件夹`clients`中创建一个名为`livepeer.js`的新文件，并向其中添加以下代码：

```jsx
import { createReactClient } from "@livepeer/react";
import { studioProvider } from "livepeer/providers/studio";

const LPClient = createReactClient({
  provider: studioProvider({ apiKey: "API_KEY" }),
});

export default LPClient;
```

上面的代码是我们将用来与 Livepeer 交互的客户端。不要忘记替换`API_KEY`为您从 Livepeer 仪表板复制的密钥。

### [](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-walletconnect "永久链接")设置 WalletConnect

WalletConnect 是一个开源协议，允许您的钱包与 DApp 和其他钱包连接并交互。在本教程中，我们将使用 WalletConnect 允许用户连接他们的钱包并验证他们的所有权。

在该`app.js`文件中，导入 WalletConnect 并将您的项目包装在其中：

```jsx
import React from 'react'
import Routes from './routes'
import WalletConnectProvider from "react-native-walletconnect";

export default function App() {
  return (
    <WalletConnectProvider>
      <Routes />
    </WalletConnectProvider>
  )
}
```

### 设置客户端

我们添加了两个客户端：Apollo GraphQL 和 Livepeer。接下来，我们需要将这两个添加到我们的`app.js`

与钱包连接类似，您只需要包装这些客户端的路由即可。您可以将里面替换`app.js`为下面的代码

```jsx
import React from 'react'
import Routes from './routes'
import WalletConnectProvider from "react-native-walletconnect";
import { LivepeerConfig } from '@livepeer/react-native';
import LPClient from './clients/livepeer';
import { ApolloProvider } from '@apollo/client';
import APClient from './clients/apollo';

export default function App() {
  return (
    <WalletConnectProvider>
      <ApolloProvider client={APClient}>
        <LivepeerConfig client={LPClient}>
          <Routes />
        </LivepeerConfig>
      </ApolloProvider>
    </WalletConnectProvider>
  )
}
```

现在是时候看看我们的项目如何运行了！打开终端并输入`npx expo start`已启动开发服务器。您可以在 iOS 模拟器（如果您有 Mac）、Android 模拟器或您自己的设备上运行该项目。选择首选设备后，Expo CLI 将在您的设备/模拟器上启动该项目。您现在应该看到该项目在您的设备上运行，看起来类似于：

![xray\_default.jpg](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/13f64fc4ec5d446c817108512e8638bb~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=514\&h=964\&s=61875\&e=png\&a=1\&b=f2f2f2)

唷，要设置的东西有很多，但我们才刚刚开始。那么，让我们继续进行身份验证部分。

## [验证](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-authentication "永久链接")

现在，是时候向我们的项目添加身份验证了。这涉及一系列步骤，包括连接用户的钱包，从Lens API获取消息，用用户的钱包对消息进行签名，并将其发送回Lens API进行验证，如果一切成功，我们将获得访问令牌和验证我们将保存到您的设备的令牌。

### [连接用户钱包](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-connecting-user-wallet "永久链接")

为了允许用户将他们的钱包连接到我们的项目，我们将使用`react-native-walletconnect`. 删除`Login.js`文件内的所有内容并添加以下代码。

```jsx
import { Pressable, StyleSheet, Text, TextBase, View } from 'react-native'
import React from 'react'
import { StatusBar } from 'expo-status-bar';
import { useWalletConnect } from "react-native-walletconnect";

export default function Login() {
    const {
        createSession,
        killSession,
        session,
        signPersonalMessage,
    } = useWalletConnect();

    return (
        <View style={styles.container}>
            <StatusBar />
            <Text style={styles.text}>Sign up for TikTok</Text>
            <Pressable
                onPress={createSession}
                style={styles.button}>
                <Text style={styles.buttonText}>
                    Connect your wallet
                </Text>
            </Pressable>
            <Text style={styles.footer}>
                Connecting your wallet & siging message, simply proves ownership of the wallet. Signing message doesn't initiate any transaction on the blockchain
            </Text>
        </View>
    )
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: "#fff",
        paddingTop: 50,
        paddingLeft: 30,
    },
    text: {
        fontSize: 40,
        fontWeight: "700",
        width: "50%",
        lineHeight: 50,
        marginTop: 50,
    },
    button: {
        borderWidth: 1,
        width: "90%",
        marginTop: 50,
        padding: 15,
        borderColor: "#ccc",
        alignItems: "center"
    },
    buttonText: {
        fontWeight: "600",
    },
    footer: {
        position: "absolute",
        bottom: 50,
        marginLeft: 30,
        textAlign: "center",
        color: "#aaa",
    }
})
```

在上面的代码中，

*   我们导入了各种 React Native 和 WalletConnect 库，例如`Pressable`、`StyleSheet`、`Text`、`View`和`useWalletConnect`。
*   接下来，在组件内部，`useWalletConnect`hook 用于创建会话、终止会话、获取当前会话以及签署交易。
*   主要`Login`组件返回`View`一个包含`Text`显示“注册 TikTok”标头的组件、单击时`Pressable`触发该功能的组件以及显示有关连接钱包和签署消息的目的的消息的组件。`createSession``Text`
*   该`StyleSheet`对象用于设置组件的样式，包括设置背景颜色、字体大小以及文本和按钮的位置。
*   最后，库`StatusBar`中的组件`expo-status-bar`用于在屏幕顶部显示状态栏。

完成文件编辑后，保存它，您应该会看到一个漂亮干净的登录屏幕：

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8a9e5d6e0f964e83bb46bf030c915250~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=375\&h=737\&s=36269\&e=png\&a=1\&b=fefefe)

如果您点击"Connect your wallet"按钮，将会弹出一个小窗口，让您从不同的钱包选项中进行选择。这是将钱包连接到项目的方法。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b3025f0ac75645ff82bc61fc47185335~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=419\&h=781\&s=50751\&e=png\&a=1\&b=25292e)

单击弹出窗口中的钱包选项后，您将被重定向到该钱包项目以完成连接过程。这就是项目知道您是钱包的所有者的方式。

现在我们已经完成了连接钱包部分，我们可以继续下一步，即与用户钱包签署消息并使用 Lens API 进行验证

### 签署消息

现在用户已经连接了他们的钱包，并且我们有了他们的钱包地址，我们可以继续部分登录。

在return语句前添加以下代码：

```jsx
const signMessage = async () => {
    const response = await client.query({
      query: gql`query Challenge {
        challenge(request: { address: "${address}" }) {
          text
        }
      }`,
    });
    let challenge = convertUtf8ToHex(response.data.challenge.text);
    const msgParams = [challenge, address];
    connector.signPersonalMessage(msgParams).then(async (result) => {
      getTokens(result);
    });
};


const getTokens = async (result) => {
    const response = await client.mutate({
      mutation: gql`mutation Authenticate {
        authenticate(request: {
          address: "${address}",
          signature: "${result}"
        }) {
          accessToken
          refreshToken
        }
      }`,
    });
    await saveItem("accessToken", response.data.authenticate.accessToken);
    await saveItem("refreshToken", response.data.authenticate.refreshToken);
};
```

那么现在我们即将要做的是：

*   首先，我们定义一个名为 的异步函数`signMessage`。此函数向 Lens API 进行查询并请求用户必须使用其私钥签名的 `质询字符串(the challenge string)` 以证明其身份。查询返回 质询字符串
*   接下来，使用质询字符串和用户地址作为参数的库`signPersonalMessage`中的方法。`wallet-connect`该方法使用用户的钱包对消息进行签名并返回结果。`getTokens`然后使用该结果调用该函数。
*   该`getTokens`函数使用 向服务器发送突变请求，并且请求包括用户的地址和该`signPersonalMessage`方法生成的签名。服务器验证签名，如果有效，则返回访问令牌和刷新令牌。然后使用异步存储将这些令牌存储在本地。

## 主页

现在我们已经完成了身份验证，让我们进入主屏幕。首先，我们需要为家庭创建一个屏幕。转到`screen`文件夹并创建一个名为`Home.js` 的新文件。在其中添加这个简单的组件：

```jsx
import { StyleSheet, Text, View } from 'react-native'
import React from 'react'

export default function Home() {
    return (
        <View style={styles.container}>
            <Text>Home Screen</Text>
        </View>
    )
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: "center",
        backgroundColor: "#fff",
        alignItems: "center"
    }
})

```

接下来，让我们设置底部选项卡。

### [设置底部选项卡](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-setting-up-bottom-tabs "永久链接")

首先，[从GitHub 存储库](https://github.com/suhailkakar/decentralized-tiktok/tree/main/assets)下载图标并将它们添加到资产文件夹中。然后创建一个名为 `Components` 的新文件夹，并在其中创建一个名为`BottomTabs.js`的文件.

```jsx
import { Image, StyleSheet } from "react-native";
import React from "react";

import { createBottomTabNavigator } from "@react-navigation/bottom-tabs";
import Home from "../screens/Home";

const BottomTab = createBottomTabNavigator();

export default function BottomTabs() {
    return (
        <BottomTab.Navigator
            screenOptions={{
                tabBarStyle: { backgroundColor: "black", borderWidth: 0 },
                headerShown: false,
                tabBarActiveTintColor: "white",
            }}
        >
            <BottomTab.Screen
                name="Home"
                component={Home}
                options={{
                    tabBarIcon: ({ focused }) => (
                        <Image
                            source={require("../assets/home.png")}
                            style={[
                                styles.bottomTabIcon,
                                focused && styles.bottomTabIconFocused,
                            ]}
                        />
                    ),
                }}
            />
            <BottomTab.Screen
                name="Discover"
                component={Home}
                options={{
                    tabBarIcon: ({ focused }) => (
                        <Image
                            source={require("../assets/search.png")}
                            style={[
                                styles.bottomTabIcon,
                                focused && styles.bottomTabIconFocused,
                            ]}
                        />
                    ),
                }}
            />
            <BottomTab.Screen
                name="NewVideo"
                component={Home}
                options={{
                    tabBarLabel: () => null,
                    tabBarIcon: ({ focused }) => (
                        <Image
                            source={require("../assets/new-video.png")}
                            style={[
                                styles.newVideoButton,
                                focused && styles.bottomTabIconFocused,
                            ]}
                        />
                    ),
                }}
            />
            <BottomTab.Screen
                name="Inbox"
                component={Home}
                options={{
                    tabBarIcon: ({ focused }) => (
                        <Image
                            source={require("../assets/message.png")}
                            style={[
                                styles.bottomTabIcon,
                                focused && styles.bottomTabIconFocused,
                            ]}
                        />
                    ),
                }}
            />
            <BottomTab.Screen
                name="Profile"
                component={Home}
                options={{
                    tabBarIcon: ({ focused }) => (
                        <Image
                            source={require("../assets/user.png")}
                            style={[
                                styles.bottomTabIcon,
                                focused && styles.bottomTabIconFocused,
                            ]}
                        />
                    ),
                }}
            />
        </BottomTab.Navigator>
    );
}

const styles = StyleSheet.create({
    bottomTabIcon: {
        width: 20,
        height: 20,
        tintColor: "grey",
    },
    bottomTabIconFocused: {
        tintColor: "white",
    },
    newVideoButton: {
        width: 50,
        height: 25,
    },
});
```

在上面的文件中，我们使用该库创建了类似于 Tiktok 的底部选项卡导航`@react-navigation/bottom-tabs`。我们还在底部选项卡中添加了自定义图标，使它们看起来与 TikTok 完全相同。

要使用底部选项卡导航，我们需要将其添加到我们的`routes.js`文件中。完成身份验证过程后，我们希望通过底部选项卡导航将用户重定向到主屏幕。

保存文件，然后在`routes.js`文件中的登录后添加底部选项卡。这是`routes.js`带有底部选项卡导航的更新文件：

    //... <Stack.Screen name="Login" component={Login} />
    <Stack.Screen name="Home" component={BottomTabs} />

现在，当用户成功登录时，他们将被重定向到主屏幕，其中包括底部选项卡导航。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8a76e0b9d53145c58d8bcba4ecedfb5d~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=448\&h=876\&s=36859\&e=png\&a=1\&b=ffffff)

### 从 Lens 获取视频

接下来，在根目录中创建一个名为的新文件`queries.js`，现在向其中添加 `探索帖子(explore posts)` 查询。

```jsx
import { gql } from "@apollo/client";
export const EXPLORE_POSTS = gql`
  query ($request: ExplorePublicationRequest!) {
    explorePublications(request: $request) {
      items {
        __typename
        ... on Post {
          ...PostFields
        }
      }
      pageInfo {
        prev
        next
        totalCount
      }
    }
  }
  fragment MediaFields on Media {
    url
    width
    height
    mimeType
  }
  fragment ProfileFields on Profile {
    id
    name
  }
  fragment PublicationStatsFields on PublicationStats {
    totalAmountOfMirrors
    totalUpvotes
    totalAmountOfCollects
    totalAmountOfComments
  }
  fragment MetadataOutputFields on MetadataOutput {
    name
    description
    content
    media {
      original {
        ...MediaFields
      }
      small {
        ...MediaFields
      }
      medium {
        ...MediaFields
      }
    }
  }

  fragment PostFields on Post {
    id
    profile {
      ...ProfileFields
    }
    stats {
      ...PublicationStatsFields
    }
    metadata {
      ...MetadataOutputFields
    }
    createdAt
  }
`;
```

返回，`home.js`用以下代码替换文件内的所有内容：

```jsx
import { FlatList, StyleSheet, View, Text, Dimensions } from "react-native";
import React, { useState } from "react";
import { EXPLORE_POSTS } from "../queries";
import { useQuery } from "@apollo/client";
import { useBottomTabBarHeight } from "@react-navigation/bottom-tabs";

export default function Home() {
    const [activeVideoIndex, setActiveVideoIndex] = useState(0);

    const bottomTabHeight = useBottomTabBarHeight();
    const { height: WINDOW_HEIGHT } = Dimensions.get("window");
    const { data } = useQuery(EXPLORE_POSTS, {
        variables: {
            request: {
                limit: 5,
                sources: ["lenstube-bytes"],
                publicationTypes: ["POST"],
                sortCriteria: "CURATED_PROFILES",
            },
        },
    });

    const pageInfo = data?.explorePublications?.pageInfo;
    const videos = data?.explorePublications?.items;

    return (
        <View style={styles.container}>
            <FlatList
                data={videos}
                pagingEnabled
                renderItem={({ item, index }) => <Text>{item.metadata.content}</Text>}
                onScroll={(e) => {
                    const index = Math.round(
                        e.nativeEvent.contentOffset.y / (WINDOW_HEIGHT - bottomTabHeight)
                    );
                    setActiveVideoIndex(index);
                }}
            />
        </View>
    );
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: "center",
        backgroundColor: "#fff",
        alignItems: "center",
    },
});
```

在上面的代码中，

*   首先，我们分别导入多个组件和库，包括来自 React 和 React Native 的`FlatList`、`StyleSheet`、`View`、`Text`、`Dimensions`和 ，`useState`以及分别来自 Apollo Client 和 React Navigation 的`useQuery`和`useBottomTabBarHeight`。
*   该`Home`函数是导出的主要组件。它包括`useState`创建一个名为 的状态变量的钩子`activeVideoIndex`，该变量最初设置为 0。该变量用于跟踪当前活动视频在稍后将渲染的视频列表中的索引。
*   该`useBottomTabBarHeight`钩子用于获取当前导航堆栈中底部标签栏的高度。该值存储在`bottomTabHeight`变量中。
*   该`useQuery`钩子用于从`EXPLORE_POSTS`前面定义的查询中获取数据。该`variables`选项用于指定查询的参数，包括限制、来源、发布类型和排序条件。
*   该`data`变量用于存储查询返回的数据。和变量是使用可选链接运算符 ( ) 从对象`pageInfo`中提取的。该变量包含有关当前视频页面的信息，而该变量包含视频对象的数组。`videos``data``?``pageInfo``videos`
*   最后，`FlatList`渲染一个组件，它显示视频列表。prop`data`设置为`videos`数组，`renderItem`prop 用于指定列表中的每个项目应如何呈现。在这种情况下，每个视频都被渲染为`Text`显示`metadata`视频属性的组件。
*   该`onScroll`prop 用于处理`FlatList`. 当用户滚动列表时，`onScroll`将使用事件对象调用该函数。该函数使用 方法`Math.round`根据`contentOffset`和`WINDOW_HEIGHT`和`bottomTabHeight`变量计算当前可见视频的索引。然后使用该索引来更新`activeVideoIndex`状态变量。

保存文件，正如您所看到的，我们现在只是渲染视频的元数据。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2d81a267dec64284b4d993f13ccddd04~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=448\&h=876\&s=73125\&e=png\&a=1\&b=fcfcfc)

让我们创建一个视频播放器组件，然后将其渲染在 Flatlist 中。

### [添加视频播放器](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-adding-the-video-player "永久链接")

在组件目录中，创建一个名为`VideoPlayer.js`的新文件，并向其中添加以下代码。

```jsx
import React from "react";
import { Image, StatusBar, StyleSheet, Text, View } from "react-native";
import { useBottomTabBarHeight } from "@react-navigation/bottom-tabs";
import { Player } from "@livepeer/react-native";

export default function VideoPlayer({ data, isActive }) {
    const bottomTabHeight = useBottomTabBarHeight();
    const statusBarHeight = StatusBar.currentHeight || 0;

    const getIPFSLink = (hash) => {
        const gateway = "https://lens.infura-ipfs.io/ipfs/";

        return hash
            .replace(/^Qm[1-9A-Za-z]{44}/gm, `${gateway}${hash}`)
            .replace("https://ipfs.io/ipfs/", gateway)
            .replace("ipfs://", gateway);
    };

    return (
        <View
            style={[
                styles.container,
                { height: WINDOW_HEIGHT - bottomTabHeight - statusBarHeight },
            ]}
        >
            <StatusBar barStyle={"light-content"} />
            <Player
                src={getIPFSLink(data.metadata.media[0].original.url)}
                priority
                aspectRatio={"16:9"}
                loop
                autoplay={isActive}
            />
            <View style={styles.bottomSection}>
                <View style={styles.bottomLeftSection}>
                    <Text style={styles.channelName}>{data.profile.name}</Text>
                    <Text style={styles.caption}>{data.metadata.name}</Text>
                </View>
                <View style={styles.bottomRightSection}>
                    <Image
                        source={require("../assets/floating-music-note.png")}
                        style={[styles.floatingMusicNote]}
                    />
                    <Image
                        source={require("../assets/disc.png")}
                        style={[styles.musicDisc]}
                    />
                </View>
            </View>

            <View style={styles.verticalBar}>
                <View style={[styles.verticalBarItem, styles.avatarContainer]}>
                    <Image
                        style={styles.avatar}
                        source={{
                            uri: getIPFSLink(data.profile.picture.original.url),
                        }}
                    />
                    <View style={styles.followButton}>
                        <Image
                            source={require("../assets/plus-button.png")}
                            style={styles.followIcon}
                        />
                    </View>
                </View>
                <View style={styles.verticalBarItem}>
                    <Image
                        style={styles.verticalBarIcon}
                        source={require("../assets/heart.png")}
                    />
                </View>
                <View style={styles.verticalBarItem}>
                    <Image
                        style={styles.verticalBarIcon}
                        source={require("../assets/message-circle.png")}
                    />
                </View>
                <View style={styles.verticalBarItem}>
                    <Image
                        style={styles.verticalBarIcon}
                        source={require("../assets/reply.png")}
                    />
                </View>
            </View>
        </View>
    );
}

const styles = StyleSheet.create({
    container: {
        width: WINDOW_WIDTH,
    },
    video: {
        position: "absolute",
        width: "100%",
        height: "100%",
    },
    bottomSection: {
        position: "absolute",
        bottom: 0,
        flexDirection: "row",
        width: "100%",
        paddingHorizontal: 8,
        paddingBottom: 16,
    },
    bottomLeftSection: {
        flex: 4,
    },
    bottomRightSection: {
        flex: 1,
        justifyContent: "flex-end",
        alignItems: "flex-end",
    },
    channelName: {
        color: "white",
        fontWeight: "bold",
    },
    caption: {
        color: "white",
        marginVertical: 8,
    },
    musicNameContainer: {
        flexDirection: "row",
        alignItems: "center",
    },
    musicNameIcon: {
        width: 12,
        height: 12,
        marginRight: 8,
    },
    musicName: {
        color: "white",
    },
    musicDisc: {
        width: 40,
        height: 40,
    },
    verticalBar: {
        position: "absolute",
        right: 8,
        bottom: 72,
    },
    verticalBarItem: {
        marginBottom: 24,
        alignItems: "center",
    },
    verticalBarIcon: {
        width: 32,
        height: 32,
    },
    verticalBarText: {
        color: "white",
        marginTop: 4,
    },
    avatarContainer: {
        marginBottom: 48,
    },
    avatar: {
        width: 48,
        height: 48,
        borderRadius: 24,
    },
    followButton: {
        position: "absolute",
        bottom: -8,
    },
    followIcon: {
        width: 21,
        height: 21,
    },
    floatingMusicNote: {
        position: "absolute",
        right: 40,
        bottom: 16,
        width: 16,
        height: 16,
        tintColor: "white",
    },
});
```

*   首先，我们从 React Native 库以及一些第三方库（例如`@react-navigation/bottom-tabs`和 ）导入必要的组件`@livepeer/react-native`。
*   该组件接受两个 props，`data`并且`isActive`。接下来，在组件内部，我们 从`@react-navigation/bottom-tabs`使用hooks 来获取底部选项卡栏的高度，并使用`StatusBar.currentHeight`属性来获取状态栏的高度。
*   我们还定义了一个名为`getIPFSLink`的辅助函数，它接受哈希值并返回 IPFS 网关 (Infura) 的链接。
*   在 return 语句中，该`View`组件用于创建一个容器，其中包含要在屏幕上呈现的所有组件。容器的高度是通过窗口的高度减去底部标签栏和状态栏的高度来调整的。
*   该`StatusBar`组件用于将状态栏的颜色设置为白色。
*   从`@livepeer/react-native`导出的`Player`组件用于在屏幕上渲染视频播放器。视频源是`data.metadata`对象中的第一个媒体项。当 `isActive` prop 为 true 时，播放器设置为循环播放并自动播放。
*   容器中呈现的其余组件`View`是一些文本和图像组件，它们显示配置文件名称、标题和各种操作（例如点赞、评论和关注）的图标。最后，我们还使用该`StyleSheet.create`方法定义了一些样式。

返回到`home.js`，导入`VideoPlayer`组件并用它 替换 FlatList renderItem 属性。

```jsx
   <FlatList
        data={videos}
        pagingEnabled
        renderItem={({ item, index }) => (
            <VideoPlayer data={item} isActive={activeVideoIndex === index} />
        )}
        onScroll={(e) => {
            const index = Math.round(
                e.nativeEvent.contentOffset.y / (WINDOW_HEIGHT - bottomTabHeight)
            );
            setActiveVideoIndex(index);
        }}
    />
```

保存文件，您应该会看到带有视频信息的视频播放器。这看起来与 TikTok 非常相似。
![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e9b9e382099e477c9933b4653881bebc~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=448\&h=876\&s=78947\&e=png\&a=1\&b=101010)

## 上传

现在，是时候处理上传视频过程了。上传过程将是：

*   首先，用户从库中选择视频。
*   然后，我们将该视频上传到 Livepeer。
*   之后，我们将元数据保存到 IPFS。
*   最后，我们将元数据的 IPFS CID 发布到 Lens API。

在此之前，在 React Native 项目的`screens`文件夹中创建一个名为`upload.js`的新文件。现在，您可以向其中添加以下代码：
```jsx
import { StyleSheet, Text, View } from 'react-native'
import React from 'react'

export default function Home() {
    return (
        <View style={styles.container}>
            <Text>Home Screen</Text>
        </View>
    )
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: "center",
        backgroundColor: "#fff",
        alignItems: "center"
    }
})
```

### [上传视频到 Livepeer](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-uploading-video-to-livepeer "永久链接")

第一步是允许用户从库中选择视频。在上传屏幕内，创建一个名为的函数`pickVideo`，该函数将允许用户从设备的媒体库中选择视频，并向其中添加以下代码：
```js
const pickVideo = async () => {
  const { status } = await requestMediaLibraryPermissionsAsync();
  if (status !== "granted") {
    alert("Sorry, we need camera roll permissions to make this work!");
    return;
  }
  const result = await launchImageLibraryAsync({
    mediaTypes: MediaTypeOptions.Videos,
    allowsEditing: true,
  });
  if (!result.cancelled) {
    setVideo(result);
  }
};
```

这里我们使用`expo-media-library`选择视频，然后将视频状态设置为结果。现在我们有了视频，我们可以使用Livepeer SDK将这些视频上传到Livepeer Studio。

我们可以将以下hooks添加到文件顶部，然后将视频传递给它
```js
const { mutate: createAsset,progress,error } = useCreateAsset({
    sources: [{ name: "video", file: media }],
});
```


接下来，您可以将此视频添加到 Lens 元数据中，然后我们可以使用它来播放来自 Livepeer 的视频。

### [将元数据保存到 IPFS](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-saving-metadata-to-ipfs "永久链接")

准备好 `元数据对象(metadata)` 后，您可以使用任何 ipfs 服务或 Arweave 上传元数据。在本教程中，我们将使用 IPFS。在选择视频功能后添加以下功能：
```js
const saveToIPFS = async (body: any) => {
  var config = {
    method: "post",
    url: "",
    data: body,
  };

  const response = await axios(config);
  return response.data.cid;
};
```

### [将元数据(metadata)发布到 Lens API](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-posting-the-metadata-to-lens-api "永久链接")

现在我们也有了 IPFS CID，我们可以用它来将元数据发布到 Lens API。将以下查询添加到`queries`文件中：
```js
export const CreatePostViaDispatcher = gql`
  mutation CreatePostViaDispatcher($request: CreatePublicPostRequest!) {
    createPostViaDispatcher(request: $request) {
      ... on RelayerResult {
        txHash
        txId
      }
      ... on RelayError {
        reason
      }
    }
  }
`;
```

然后，在`upload.js`屏幕内部，您可以使用`useMutation`将元数据发布到 Lens API：

```js
  const [createPostViaDispatcher] = useMutation(CreatePostViaDispatcher, {
    onCompleted: (data) => {
      if (data.createPostViaDispatcher.__typename === "RelayerResult") {
        generateOptimisticPost(data.createPostViaDispatcher);
      }
    },
  });
```


## **下一步是什么？**

那么，您已经做到了这一点！这太棒了，它告诉我您对创建 Web3 项目充满热情。现在，如果您愿意的话，我有一些关于如何将您的项目提升到新水平的想法：

-   让用户能够搜索其他用户和视频怎么样？它可以使您的项目更加用户友好和方便。
-   您还可以尝试使用 Arweave 而不是 IFPS，看看这如何影响您的项目的性能。
-   如果您希望使您的项目更加全面，为什么不添加一些额外的屏幕，例如用户个人资料部分？这可以让您的项目更具深度，并允许用户个性化他们的体验。
-   最后，如果您想让您的项目为黄金时段做好准备，请不要忘记让"点赞"和"评论"按钮真正发挥作用！添加这些功能将使您的项目更具吸引力，并让用户回访更多。

这些只是一些想法，但可能性是无限的。不要害怕发挥创意并享受其中的乐趣！

## [**结论**](https://blog.suhailkakar.com/building-a-full-stack-web3-tiktok-clone-with-react-native-livepeer-and-lens-protocol#heading-conclusion "永久链接")

这就是本文的内容。我希望这篇文章对您有用，如果您需要任何帮助，请在评论部分告诉我或[**在 Twitter 上私信我**](https://twitter.com/SuhailKakar)。

让我们在[**Twitter**](https://twitter.com/suhailkakar)和[**LinkedIn**](https://linkedin.com/in/suhailkakar/)上联系。

👋感谢您的阅读，我们下次再见