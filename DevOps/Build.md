# Build

## O3DE

o3de 基于cmake 构建

```shell
cmake -B <your build path> -S <your source path> -G "Visual Studio 16" -DLY_3RDPARTY_PATH=<3rdParty cache path> -DLY_UNITY_BUILD=ON -DLY_PROJECTS=AutomatedTesting 
cmake --build <your build path> --target AutomatedTesting.GameLauncher AssetProcessor Editor --config profile -- /m
```

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
