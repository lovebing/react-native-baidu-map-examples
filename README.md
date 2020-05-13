# react-native-baidu-map-examples

## 开发环境
- XCode: 11.3
- node: v14.1.0

## API Key 相关：
- API Key: sIMQlfmOXhQmPLF1QMh4aBp8zZO9Lb2A
- iOS Bundle Identifier: org.lovebing.example.rn

## v62
目录通过以下命令生成：
```shell
npx react-native init v62 --version 0.62.2
```
此版本有以下特点：
- Android 使用 androidx
- iOS 使用 CocoaPods 管理依赖

### 添加依赖
package.json 的 dependencies 增加
```
"react-native-baidu-map": "*"
```
```shell
yarn install
cd ios
pod install
```

### 运行
```shell
yarn ios
yarn android
```

## v59
目录通过以下命令生成：
```shell
react-native init v59 --version 0.59.10
```
此版本有以下特点：
- Android 没有使用 androidx
- iOS 没有使用 CocoaPods 管理依赖

### 添加依赖
package.json 的 dependencies 增加
```
"react-native-baidu-map-old": "*"
```
```shell
npm install
react-native link --platforms android react-native-baidu-map
```

#### 使用 CocoaPods 安装 SDK
```shell
cd ios
pod init
```
Podfile 在 target 'v59' do 后面添加
```
  pod 'BaiduMapKit', '4.2.0'
  pod 'BMKLocationKit', '1.3.0.2'
  pod 'OpenSSL-Universal'
```

```shell
pod install
```

#### 手动导入地图 SDK，参考：
- http://lbsyun.baidu.com/index.php?title=iossdk/guide/create-project/oc
- http://lbsyun.baidu.com/index.php?title=ios-locsdk/guide/create-project/manual-create

#### 添加 react-native-baidu-map 相关文件
项目目录 -> v59 -> 右键 Add Files to -> 选择  node_modules/react-native-baidu-map/ios/RCTBaiduMap 下的所有文件（不包括文件夹，注意不要保留目录结构）

### 运行
```shell
react-native run-ios
react-native run-android
```


## 常见问题

### The 'Pods-xx' target has libraries with conflicting names: libcrypto.a and libssl.a.
解决方法：
```shell
pod cache list | grep BaiduMapKit
```
删除 pod 缓存中的 BaiduMapKit/thirdlibs/ 下的文件，重新执行 pod install

### ld: library not found for -lcrypto
根据前面提到的方法删除 百度地图自带的 libcrypto.a 和 libssl.a，使用 OpenSSL-Universal 代替

### pod install 很慢
通常是因为连接 github.com 太慢，可以设置终端代理如 export all_proxy="http://127.0.0.1:8888" 或使用全局 VPN

