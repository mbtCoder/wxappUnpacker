
# 说明
- 原版来自网友 [wxappUnpacker](https://github.com/qwerty472123/wxappUnpacker "wxappUnpacker") 改进的开源项目。
- 分包改版来自网友 [wxappUnpacker](https://github.com/xuedingmiaojun/wxappUnpacker "wxappUnpacker") 的开源项目。

# 安装
```
npm install
```

# 安装依赖
```
npm install esprima
    
npm install css-tree
    
npm install cssbeautify
    
npm install vm2
    
npm install uglify-es
    
npm install js-beautify
```

# 提取wxapkg文件
+ iOS端需要越狱
+ Android端需要root
  - 1. /data/data/com.tencent.mm/MicroMsg/(一长串字符串)/Appbrand/pkg
  - 2. 找到wxapkg文件，将其提取到电脑上

# 常规解包
cd到解包工具目录，运行命令：

```
node wuWxapkg.js [wxapkg文件名]
```
运行完毕后可以看到解包后的源码目录。


# 分包功能

当检测到 wxapkg 为子包时, 添加-s 参数指定主包源码路径即可自动将子包的 wxss,wxml,js 解析到主包的对应位置下. 完整流程大致如下: 
1. 获取主包和若干子包
2. 解包主包 `./bingo.sh testpkg/master-xxx.wxapkg`
3. 解包子包 `./bingo.sh testpkg/sub-1-xxx.wxapkg -s=../master-xxx`

TIP
> -s 参数可为相对路径或绝对路径, 推荐使用绝对路径, 因为相对路径的起点不是当前目录 而是子包解包后的目录

```
├── testpkg
│   ├── sub-1-xxx.wxapkg #被解析子包
│   └── sub-1-xxx               #相对路径的起点
│       ├── app-service.js
│   ├── master-xxx.wxapkg
│   └── master-xxx             # ../master-xxx 就是这个目录
│       ├── app.json
```
