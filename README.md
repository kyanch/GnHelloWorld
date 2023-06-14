# GnHelloWorld
>  参考 《沉浸式剖析OpenHarmony源码 基于LTS3.0 版本》 ISBN: 978-7-115-60138-4
## 编译构建过程
1. 在当前目录中查找构建入口.gn文件
如果没找到.gn文件，就到上一级目录查找，直到找到.gn文件为止
如果到 `/` 都没找到.gn文件，编译失败
找到.gn文件以后，.gn的所在目录就为source root (root = "//:")
根据.gn文件里的 `buildconfig` 部分找到编译配置文件 `BUILDCONFIG.gn`, 如果.gn文件里配置了root ,则会更新source root

2. 加载 BUILDCONFIG.gn 文件
设置一些全局变量和编译工具链，将对后续的所有编译有效

3. 加载source root 下的 `BUILD.gn` 文件

4. 查找依赖关系，根据依赖关系加载指定路径下的 `BUILG.gn` 文件

如果在依赖目标指定的路径下找不到匹配的`BUILD.gn` 文件，就去.gn 文件中配置的`secondary_source` 路径下查找。如果仍然查找不到，缺少依赖目标错误。编译失败。

5. 查找依赖关系的过程中，没解决一个构建目标的依赖关系，就生成目标的`.ninja`文件

6. 当所有构建目标的依赖关系都解决后，会生成一个 `build.ninja` 文件

原英文解释在 [gn-reference](https://gn.googlesource.com/gn/+/main/docs/reference.md) 中 _Overall build flow_ 部分


