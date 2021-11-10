# Build

## O3DE

o3de 基于cmake 构建

```shell
cmake -B <your build path> -S <your source path> -G "Visual Studio 16" -DLY_3RDPARTY_PATH=<3rdParty cache path> -DLY_UNITY_BUILD=ON -DLY_PROJECTS=AutomatedTesting 
cmake --build <your build path> --target AutomatedTesting.GameLauncher AssetProcessor Editor --config profile -- /m
```

使用 IncrediBuild 分布式编译加速构建 —— 全量构建 32min

```
BuildConsole.exe .\o3de\My_build\O3DE.sln /rebuild /usemsbuild /cfg="profile|x64" /avoidlocal=off /showtime
```

![](https://wx2.sinaimg.cn/mw2000/61662705gy1gw95mg6tanj219m0q8qsd.jpg)