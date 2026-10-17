> Document Template: v0.4.2

<p align="center">
  <h1 align="center"> <code>react-native-better-banner</code> </h1>
</p>

This project is based on [react-native-better-banner](https://github.com/tmxiong/better-banner).

This third-party library supports direct download from npm, the new package name is: `@react-native-ohos/react-native-better-banner`, the version correspondence details are as follows:

| Name | Version(Npm Address) | Release Information | Supported RN Version | Supported Autolink | Compile API Version | Community Baseline Version | Source code address |
| --- | --- | --- | --- | --- | --- | --- | --- |
| @react-native-ohos/react-native-better-banner | [~1.2.0](https://www.npmjs.com/package/@react-native-ohos/react-native-better-banner) | [Github Releases](https://github.com/react-native-oh-library/better-banner/releases) | 0.72.*/0.77.*/0.82.* | No | API12+ | 1.1.3 | [br_rnoh0.77](https://github.com/react-native-oh-library/better-banner/tree/br_rnoh0.77) |
| @react-native-ohos/react-native-better-banner | [~1.1.4](https://www.npmjs.com/package/@react-native-ohos/react-native-better-banner) | [Github Releases](https://github.com/react-native-oh-library/better-banner/releases) | 0.72.* | No | API12+ | 1.1.3 | [sig](https://github.com/react-native-oh-library/better-banner/tree/sig) |
| @react-native-oh-tpl/react-native-better-banner | [<=1.1.3-0.0.3@deprecated](https://www.npmjs.com/package/@react-native-oh-tpl/react-native-better-banner) | [Github Releases(deprecated)](https://github.com/react-native-oh-library/better-banner/releases) | 0.72.* | No | API12+ | 1.1.3 | [sig](https://github.com/react-native-oh-library/better-banner) |

## Introduction

@react-native-ohos/react-native-better-banner is a banner (carousel) component adapted for OpenHarmony based on react-native-better-banner. It is implemented with a pure JavaScript solution and supports displaying images or custom components in the banner, with seamless scrolling, timed scrolling, indicator customization, synchronized title display, and click and scroll event callbacks. It can be used on the OpenHarmony platform, the usage is consistent across platforms and the effect is equivalent to iOS or Android.

## Installation

Go to the project directory and execute the following command:

**npm**

```bash
npm install @react-native-ohos/react-native-better-banner
```

**yarn**

```bash
yarn add @react-native-ohos/react-native-better-banner
```

## Constraints

### Compatibility

This document is verified based on the following versions:

1. RNOH: 0.77.18; SDK: HarmonyOS 6.0.0 Release SDK; IDE: DevEco Studio 6.0.0.858; ROM: 6.0.0.112;

### API requirements

> [!TIP] All versions of the current third-party libraries have implemented version isolation, supporting compilation in `API12+` projects and execution on `API12+` ROMs.

## Example

The following code shows the basic use scenario of the repository:

> [!WARNING] The name of the imported repository remains unchanged.

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

## How to Use

The following are common usage scenarios of react-native-better-banner:

**Displaying images**

Pass the image list through `bannerImages` to display images in the banner, used alternatively with `bannerComponents`:

```jsx
<BetterBanner
    bannerImages={[
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot01.png'},
        {uri: 'https://raw.githubusercontent.com/tmxiong/better-banner/master/src/screenshot/screenshot02.png'},
    ]}
    bannerTitles={['Title 01', 'Title 02']}
/>
```

**Timed automatic scrolling**

`isAutoScroll` controls whether to enable automatic scrolling (enabled by default), and `scrollInterval` sets the time interval of automatic scrolling in milliseconds:

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

**Seamless scrolling**

`isSeamlessScroll` controls whether to enable seamless scrolling. If scrolling behaves abnormally in some scenarios after it is enabled, you can use `adaptSeamlessScrollValue` to set whether to display the scrolling animation of the `ScrollView`'s `scrollTo`:

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

**Indicator and title customization**

Customize the indicators through properties such as `indicatorWidth`, `indicatorHeight`, `indicatorColor`, `indicatorGap`, `activeIndicatorColor` and `indicatorGroupPosition`, and display and customize the titles synchronously through `bannerTitles`, `bannerTitleTextColor` and `bannerTitleTextSize`:

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

## Available APIs

> [!TIP] The "Platform" column indicates the platforms supported by the property in the original third-party library.

> [!TIP] If the value of "OpenHarmony Platform Support" is yes, it means that the OpenHarmony platform supports this property; no means the opposite; partially means some capabilities of this property are supported. The usage method is the same on different platforms and the effect is the same as that of iOS or Android.

The following are the common properties of react-native-better-banner. The properties have been verified.

| Name | Description | Type | Required | Platform | OpenHarmony Platform Support |
| ---- | ----------- | ---- | -------- | -------- | ------------------ |
| bannerImages | The image list to display in the banner, used alternatively with bannerComponents | Array | no | Android/iOS | yes |
| bannerComponents | The custom component list to display in the banner, used alternatively with bannerImages | Array | no | Android/iOS | yes |
| bannerHeight | The default height of the banner | Number | no | Android/iOS | yes |
| bannerTitles | The title corresponding to each image or component | Array | no | Android/iOS | yes |
| bannerTitleTextColor | The text color of the title of each image or component | String | no | Android/iOS | yes |
| bannerTitleTextSize | The text size of the title of each image or component | Number | no | Android/iOS | yes |
| scrollInterval | The time interval of automatic scrolling, in milliseconds | Number | no | Android/iOS | yes |
| isAutoScroll | Whether to enable automatic scrolling | Boolean | no | Android/iOS | yes |
| isSeamlessScroll | Whether to enable seamless scrolling | Boolean | no | Android/iOS | yes |
| adaptSeamlessScrollValue | When seamless scrolling behaves abnormally on some devices, it is used to set whether to display the scrolling animation of the ScrollView's scrollTo | Boolean | no | Android/iOS | yes |
| indicatorWidth | The width of the indicator | Number | no | Android/iOS | yes |
| indicatorHeight | The height of the indicator | Number | no | Android/iOS | yes |
| indicatorColor | The color of the indicator | String | no | Android/iOS | yes |
| indicatorStyle | The style of the indicator. You can set the width, height, color and corner radius of the indicator at one time, which will override the indicatorWidth, indicatorHeight and indicatorColor properties | Object | no | Android/iOS | yes |
| indicatorGap | The gap between indicators | Number | no | Android/iOS | yes |
| activeIndicatorColor | The color of the active indicator | String | no | Android/iOS | yes |
| indicatorGroupPosition | The position of the indicator group, which can be set to left, center or right. If bannerTitles is set, this property can only be right | String | no | Android/iOS | yes |
| indicatorGroupSideOffset | The left and right margin of the indicator group | Number | no | Android/iOS | yes |
| indicatorContainerHeight | The height of the indicator container | Number | no | Android/iOS | yes |
| indicatorContainerBackgroundColor | The background color of the indicator container | String | no | Android/iOS | yes |
| onPress | The callback function after the banner is clicked, which returns the index of the banner | Function | no | Android/iOS | yes |
| onScrollEnd | The callback function after each banner is scrolled, equivalent to the onMomentumScrollEnd of the ScrollView | Function | no | Android/iOS | yes |

## Known Issues

None

## Other

None

## Directory Structure

````
/react-native-better-banner  # Project root directory
├── harmony                      # HarmonyOS adaptation directory
│   └── .gitkeep                 # Directory placeholder file
├── index.js                     # Entry file, forwarding the upstream react-native-better-banner component
├── index.harmony.js             # HarmonyOS-side implementation, exporting the BetterBanner component
├── CHANGELOG.md                 # Version change records
├── COMMITTERS.md                # Committer list
├── OAT.xml                      # Open-source audit tool configuration file
├── README.OpenSource            # Open-source information statement
├── package.json                 # Package configuration file
├── LICENSE                      # License file
├── README.md                    # Chinese installation and usage instructions
└── README_en.md                 # English installation and usage instructions
````

## How to Contribute

If you find any problem when using the library, submit an [Issue](https://github.com/react-native-oh-library/better-banner/issues), and pull requests are also welcome.

## License

This project is based on [The MIT License (MIT)](https://github.com/react-native-oh-library/better-banner/blob/br_rnoh0.77/LICENSE).
