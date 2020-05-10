# react-native-baidu-map-examples
## v62
目录通过以下命令生成：
```shell
npx react-native init v62 --version 0.62.2
```
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

### 设置 ios 的 Bundle Identifier
Bundle Identifier 改为 org.lovebing.example.rn


## 常见问题
### The 'Pods-xx' target has libraries with conflicting names: libcrypto.a and libssl.a.
解决方法：
```shell
pod cache list | grep BaiduMapKit
```
删除 BaiduMapKit/thirdlibs/ 下的文件，重新执行 pod install

### pod install 很慢
通常是因为连接 github.com 太慢，可以设置终端代理如 export all_proxy="http://127.0.0.1:8888" 或使用全局 VPN

