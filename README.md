> 文档模板：v0.4.2

<p align="center">
  <h1 align="center"> <code>react-native-better-banner</code> </h1>
</p>

本项目基于 [react-native-better-banner](https://github.com/tmxiong/better-banner) 开发。

该第三方库支持从 npm 下载，新的包名为：`@react-native-ohos/react-native-better-banner`，版本所属关系如下：

| 三方库名称 | 三方库版本（npm地址） | 发布信息 | 支持RN版本 | Autolink | 编译API版本 | 社区基线版本 | 源码地址 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| @react-native-ohos/react-native-better-banner | [~1.2.0](https://www.npmjs.com/package/@react-native-ohos/react-native-better-banner) | [Github Releases](https://github.com/react-native-oh-library/better-banner/releases) | 0.72.*/0.77.*/0.82.* | 否 | API12+ | 1.1.3 | [br_rnoh0.77](https://github.com/react-native-oh-library/better-banner/tree/br_rnoh0.77) |
| @react-native-ohos/react-native-better-banner | [~1.1.4](https://www.npmjs.com/package/@react-native-ohos/react-native-better-banner) | [Github Releases](https://github.com/react-native-oh-library/better-banner/releases) | 0.72.* | 否 | API12+ | 1.1.3 | [sig](https://github.com/react-native-oh-library/better-banner/tree/sig) |
| @react-native-oh-tpl/react-native-better-banner | [<=1.1.3-0.0.3@deprecated](https://www.npmjs.com/package/@react-native-oh-tpl/react-native-better-banner) | [Github Releases(deprecated)](https://github.com/react-native-oh-library/better-banner/releases) | 0.72.* | 否 | API12+ | 1.1.3 | [sig](https://github.com/react-native-oh-library/better-banner) |

## 简介

@react-native-ohos/react-native-better-banner 是基于 react-native-better-banner 进行鸿蒙化适配的轮播图组件，采用纯 JavaScript 方案实现，支持轮播图片或自定义组件，具备无缝滚动、定时滚动、指示器定制、标题同步显示以及点击与滚动事件回调等能力，可在 OpenHarmony 平台上使用，使用方式与跨平台一致，效果对标 iOS 或 Android 平台。

## 下载安装

进入到工程目录并输入以下命令：

**npm**

```bash
npm install @react-native-ohos/react-native-better-banner
```

**yarn**

```bash
yarn add @react-native-ohos/react-native-better-banner
```

## 约束与限制

### 兼容性

本文档内容基于以下版本验证通过：

1. RNOH: 0.77.18; SDK: HarmonyOS 6.0.0 Release SDK; IDE: DevEco Studio 6.0.0.858; ROM: 6.0.0.112;

### 编译运行API要求

> [!TIP] 当前三方库所有版本均已实现版本隔离，支持在 `API12+` 工程编译，及 `API12+` ROM运行。

## 使用示例

下面的代码展示了这个库的基本使用场景：

> [!WARNING] 使用时 import 的库名不变。

```jsx
import React from 'react';
import {
    StyleSheet,
    View,
    Text,
} from 'react-native';

import BetterBanner from 'react-native-better-banner';

const App = () => {
    return (
        <View style={styles.container}>
            <BetterBanner
                bannerComponents={[
                    <View style={{
                        width: '100%',
                        height: '100%',
                        backgroundColor: '#1997fc',
                        alignItems: 'center',
                        justifyContent: 'center'
                    }}>
                        <Text style={{fontSize: 35, color: '#fff', marginBottom: 10}}>Page 01</Text>
                        <Text style={{fontSize: 15, color: '#fff'}}>Welcome! have a good time</Text>
                    </View>,
                    <View style={{
                        width: '100%',
                        height: '100%',
                        backgroundColor: '#da578f',
                        alignItems: 'center',
                        justifyContent: 'center'
                    }}>
                        <Text style={{fontSize: 35, color: '#fff', marginBottom: 10}}>Page 02</Text>
                        <Text style={{fontSize: 15, color: '#fff'}}>Welcome! have a good time</Text>
                    </View>,
                    <View style={{
                        width: '100%',
                        height: '100%',
                        backgroundColor: '#7c3fe4',
                        alignItems: 'center',
                        justifyContent: 'center'
                    }}>
                        <Text style={{fontSize: 35, color: '#fff', marginBottom: 10}}>Page 03</Text>
                        <Text style={{fontSize: 15, color: '#fff'}}>Welcome! have a good time</Text>
                    </View>,
                ]}
                bannerTitles={["Page 01 Page 01 Page 01 Page 01 Page 01 Page 01 Page 01 ", "Page 02", "Page 03"]}
                onPress={(index) => alert('you pressed index is : ' + index)}
                indicatorContainerBackgroundColor={'rgba(0,0,0,0.3)'}
                isSeamlessScroll={true}
            />
        </View>
    );
};

const styles = StyleSheet.create({
   container: {
       flex: 1
   }
});

export default App;
```

## 使用说明

以下为 react-native-better-banner 的常用使用场景：

**轮播图片**

通过 `bannerImages` 传入图片列表即可轮播图片，与 `bannerComponents` 二选一：

```jsx
<BetterBanner
    bannerImages={[
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot01.png'},
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot02.png'},
    ]}
    bannerTitles={['Title 01', 'Title 02']}
/>
```

**定时自动轮播**

`isAutoScroll` 控制是否开启自动轮播（默认开启），`scrollInterval` 设置自动轮播的时间间隔，单位为毫秒：

```jsx
<BetterBanner
    bannerImages={[
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot01.png'},
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot02.png'},
    ]}
    isAutoScroll={true}
    scrollInterval={3000}
/>
```

**无缝滚动**

`isSeamlessScroll` 控制是否开启无缝滚动；若开启后在部分场景下滚动异常，可通过 `adaptSeamlessScrollValue` 设置是否显示 `ScrollView` 的 `scrollTo` 滚动动画：

```jsx
<BetterBanner
    bannerImages={[
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot01.png'},
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot02.png'},
    ]}
    isSeamlessScroll={true}
    adaptSeamlessScrollValue={true}
/>
```

**指示器与标题定制**

通过 `indicatorWidth`、`indicatorHeight`、`indicatorColor`、`indicatorGap`、`activeIndicatorColor`、`indicatorGroupPosition` 等属性定制指示器，通过 `bannerTitles`、`bannerTitleTextColor`、`bannerTitleTextSize` 同步显示并定制标题：

```jsx
<BetterBanner
    bannerImages={[
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot01.png'},
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot02.png'},
    ]}
    indicatorWidth={10}
    indicatorHeight={6}
    indicatorColor={'rgba(255,255,255,0.6)'}
    activeIndicatorColor={'#fff'}
    indicatorGap={6}
    indicatorGroupPosition={'right'}
    indicatorContainerBackgroundColor={'rgba(0,0,0,0.3)'}
    bannerTitles={['Title 01', 'Title 02']}
    bannerTitleTextColor={'#fff'}
    bannerTitleTextSize={14}
/>
```

## 接口说明

> [!TIP] "Platform"列表示该属性在原三方库上支持的平台。

> [!TIP] "OpenHarmony平台支持"列为 yes 表示 OpenHarmony 平台支持该属性；no 则表示不支持；partially 表示部分支持。使用方法跨平台一致，效果对标 iOS 或 Android 的效果。

以下为 react-native-better-banner 的常用属性，属性已验证。

| Name | Description | Type | Required | Platform | OpenHarmony平台支持 |
| ---- | ----------- | ---- | -------- | -------- | ------------------ |
| bannerImages | 用于展示轮播图片，与 bannerComponents 二选一 | Array | no | Android/iOS | yes |
| bannerComponents | 用于展示轮播自定义组件，与 bannerImages 二选一 | Array | no | Android/iOS | yes |
| bannerHeight | 轮播图的默认高度 | Number | no | Android/iOS | yes |
| bannerTitles | 每张图片或组件对应的标题 | Array | no | Android/iOS | yes |
| bannerTitleTextColor | 每张图片或组件对应的标题的文字颜色 | String | no | Android/iOS | yes |
| bannerTitleTextSize | 每张图片或组件对应的标题的文字大小 | Number | no | Android/iOS | yes |
| scrollInterval | 自动轮播的时间间隔，单位为毫秒 | Number | no | Android/iOS | yes |
| isAutoScroll | 是否开启自动轮播 | Boolean | no | Android/iOS | yes |
| isSeamlessScroll | 是否开启无缝滚动 | Boolean | no | Android/iOS | yes |
| adaptSeamlessScrollValue | 无缝滚动在某些机型滚动异常时，用于设置是否显示 ScrollView 的 scrollTo 滚动动画 | Boolean | no | Android/iOS | yes |
| indicatorWidth | 指示器宽度 | Number | no | Android/iOS | yes |
| indicatorHeight | 指示器高度 | Number | no | Android/iOS | yes |
| indicatorColor | 指示器颜色 | String | no | Android/iOS | yes |
| indicatorStyle | 指示器样式，可一次性设置指示器宽、高、颜色和圆角等，会覆盖 indicatorWidth、indicatorHeight、indicatorColor 属性 | Object | no | Android/iOS | yes |
| indicatorGap | 指示器之间的间隔 | Number | no | Android/iOS | yes |
| activeIndicatorColor | 活动指示器颜色 | String | no | Android/iOS | yes |
| indicatorGroupPosition | 指示器组的位置，可设置 left、center、right；若设置了 bannerTitles，则此属性只能是 right | String | no | Android/iOS | yes |
| indicatorGroupSideOffset | 指示器组的左右边距 | Number | no | Android/iOS | yes |
| indicatorContainerHeight | 指示器容器高度 | Number | no | Android/iOS | yes |
| indicatorContainerBackgroundColor | 指示器容器背景色 | String | no | Android/iOS | yes |
| onPress | 点击轮播图后的回调函数，会传回 banner 的 index | Function | no | Android/iOS | yes |
| onScrollEnd | 滚动完每张轮播图的回调函数，等同于 ScrollView 的 onMomentumScrollEnd | Function | no | Android/iOS | yes |

## 遗留问题

无

## 其他

无

## 目录结构

````
/react-native-better-banner  # 项目根目录
├── harmony                      # 鸿蒙适配目录
│   └── .gitkeep                 # 目录占位文件
├── index.js                     # 入口文件，转发上游 react-native-better-banner 组件
├── index.harmony.js             # 鸿蒙侧实现，导出 BetterBanner 轮播图组件
├── CHANGELOG.md                 # 版本变更记录
├── COMMITTERS.md                # 提交者列表
├── OAT.xml                      # 开源审计工具配置文件
├── README.OpenSource            # 开源信息声明
├── package.json                 # 包配置文件
├── LICENSE                      # 开源协议文件
├── README.md                    # 中文安装使用方法
└── README_en.md                 # 英文安装使用方法
````

## 贡献代码

使用过程中发现任何问题都可以提交 [Issue](https://github.com/react-native-oh-library/better-banner/issues)，当然，也非常欢迎提交 [PR](https://github.com/react-native-oh-library/better-banner/pulls) 。

## 开源协议

本项目基于 [The MIT License (MIT)](https://github.com/react-native-oh-library/better-banner/blob/br_rnoh0.77/LICENSE) ，请自由地享受和参与开源。
