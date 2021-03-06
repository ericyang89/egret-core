白鹭引擎 5.0.0 发布日志
===============================


最近更新时间：2017年6月1日


欢迎您使用白鹭引擎

## 概述

白鹭引擎包含了白鹭时代研发的遵循HTML5标准的游戏引擎。他包括 2D / 3D 渲染核心、GUI体系、音频管理、资源管理等游戏引擎的常用模块。

通过使用白鹭引擎，开发者可以尽可能的不用关注浏览器的底层实现，解决HTML5游戏性能问题及碎片化问题，灵活地满足开发者开发2D或3D游戏的需求。

本次更新是白鹭引擎 5 的第一次发布，主要带来全新的基于 WebAssembly 的渲染架构。
在这次更新中，除了引擎运行时代码之外，白鹭引擎提供了全新的引擎代码库管理器。在新的代码库管理器的支持下，白鹭引擎的版本迭代速度会更加灵活。

## 更新内容

* 命令行工具
    * 引擎内置的压缩与解压缩命令从调用 java 调整为调用 node + asm.js ，因此开发者无需预装 java 环境

* 白鹭引擎 2D 渲染 - WebAssembly
    * 引入新的 WebAssembly 模块，大幅提升渲染速度
    * 在不支持 WebAssembly 的设备上回退至 asm.js 模式保证仍然可以流畅运行
    * WebAssembly 后续路线图
        * 设计并实现高性能 API
        * 内置动画、物理、粒子系统
        * 多线程离屏渲染技术
        * 单指令集多数据（ SIMD ）
        * 开放 C++ 代码

* 白鹭引擎 2D 渲染 - JavaScript
    * 保留现有的 JavaScript 渲染逻辑，开发者可以决定使用新的 WebAssembly 模式或者现有的 JavaScript 模式
    * 基于白鹭引擎 4.x 的 JavaScript 模式会长期维护保证现有开发者可以继续使用

* DragonBones
    * 引入二进制格式替代JSON文本格式、降低资源体积、内存占用，提升运行性能
    * 引入一个命令行脚本用于将旧的JSON文本格式切换为二进制格式

## 已知问题

* 开发者如果使用 WebAssembly 渲染，目前会在类的静态变量声明处创建对象时报错
* WebAssembly 渲染目前暂不支持 EUI 模块与 DragonBones 模块
