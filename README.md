## 先决条件

需要在```libs.versions.toml```中引入一些依赖，如果你还未引入的话

根据项目实际情况进行合并

``` toml
[versions]
agp = "9.1.0"
androidx-core = "1.18.0"
androidx-fragment = "1.8.9"

[libraries]
androidx-core-ktx = { group = "androidx.core", name = "core-ktx", version.ref = "androidx-core" }
androidx-fragment = { group = "androidx.fragment", name = "fragment", version.ref = "androidx-fragment" }

[plugins]
android-library = { id = "com.android.library", version.ref = "agp" }
```

## 引入子模块

将仓库添加到libs/qqstub

``` shell
git submodule add https://github.com/callng/qqStub libs/qqstub
```

后续更新(执行上方命令后可跳过本次)

``` shell
git submodule update --init --remote libs/qqStub
```

在```settings.gradle.kts```添加

``` kotlin
include(":libs:qqstub")
```

在(一般是app模块)```build.gradle.kts```的```dependencies```块里添加

``` kotlin
compileOnly(project(":libs:qqstub"))
```

最后同步项目，一切大功告成！
