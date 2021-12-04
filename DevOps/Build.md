# Build

## Workflows (工作流)

平台 - 工具链 - 目标产物

e.g windows - msbuild(vc++) - msi 

① 首先，我们看平台，当前主流平台包括但不限于下列：

- Windows (Mircosoft) 
- Mac (Apple)
- Linux
- Android
- iOS 
- Console (Xbox / PS / Switch )
- Web (Chronium / Firefox ...)

② 其次，当前构建工具/工具链包括但不限于下列：

![image-20211111224524721](https://wx1.sinaimg.cn/bmiddle/61662705gy1gwbluf2jpgj20le0b078g.jpg)

③ 最后，构建完成后制品打包：

- CPack / vcpkg (C++)
- vcpkg / wix (Windows)
- Webpack / Gulp / Grunt (Web)

## Building the Open-Sources (构建开源软件)

### [Github: O3DE](https://github.com/o3de/o3de)

![image](https://user-images.githubusercontent.com/11768073/141129945-e8408469-7252-4913-9014-116720fd09d1.png)

1. 普通编译

```shell
cmake -B <your build path> -S <your source path> -G "Visual Studio 16" -DLY_3RDPARTY_PATH=<3rdParty cache path> -DLY_UNITY_BUILD=ON -DLY_PROJECTS=AutomatedTesting 
cmake --build <your build path> --target AutomatedTesting.GameLauncher AssetProcessor Editor --config profile -- /m
```

2. 分布式加速编译构建
使用 IncrediBuild 分布式编译加速构建 —— 全量构建 32min

```
# 设置必须变量
$env:LY_PACKAGE_SERVER_URLS="https://d2c171ws20a1rv.cloudfront.net"
# 配置工程，生成 O3DE.sln
cmake -B "D:\o3de\My_build" -S "D:\o3de" -G "Visual Studio 16 2019" -DLY_3RDPARTY_PATH="D:\3rdParty-windows-no-symbols-rev10\3rdParty" -DLY_UNITY_BUILD=ON -DLY_PROJECTS="AutomatedTesting;AtomTest;AtomSampleViewer"
# 开始编译
BuildConsole.exe .\o3de\My_build\O3DE.sln /rebuild /usemsbuild /cfg="profile|x64" /avoidlocal=off /showtime
```

![](https://wx2.sinaimg.cn/mw2000/61662705gy1gw95mg6tanj219m0q8qsd.jpg)

### [Google: Chronium](https://www.chromium.org/Home)

1. 普通编译

Chronium 主要使用 ninja 工具构建，配合 GN 工具生成 .ninja 文件：

```powershell
$ gn gen out/Default
```

2. 加速构建

- 硬件
  - faster disk (e.g SSD)
  - RAM
- 软件加速
  - gn flags
  - goma (google employees only)

🔗 links: [Setting up the build](https://chromium.googlesource.com/chromium/src/+/main/docs/windows_build_instructions.md#setting-up-the-build)
