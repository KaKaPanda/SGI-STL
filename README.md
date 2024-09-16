# SGI-STL
SGI-STL (Silicon Graphics Computer Systems, Inc.) source code analysis and note.

SGI-STL 是 Alexander Stepanov 博士等人投注心力的 STL 实现版本, 无论在技术层次、源代码组织、源代码可读性上均有卓越的表现, 并被纳入 GNU C++ 标准程序库的一部分. STL 提供六大组件, 彼此可以组合套用:

1. 容器 (containers): 各种数据结构, 如 vector, list, deque, set, map 用来存放数据. 从实现的角度看, STL 容器是一种 class template.

2. 算法 (algorithms): 各种常用算法, 如 sort, search, copy, erase... 从实现的角度看, STL 算法是一种 function template.

3. 迭代器 (iterators): 扮演容器与算法之间的胶合剂, 是所谓的"泛型指针". 共有五种类型, 以及其他衍生变化. 从实现的角度看, 迭代器是一种将 operator*, operator->, operator++, operator-- 等指针相关操作予以重载的 class template.

4. 仿函数 (functors): 行为类似函数, 可做为算法的某种策略 (policy). 从实现的角度看, 仿函数是一种重载了 operator() 的 class 或 class template. 一般函数指针可视为狭义的仿函数.

5. 配接器 (adapters): 一种用来修饰容器 (containers) 或仿函数 (functors) 或迭代器 (iterators) 接口的东西. 例如 STL 提供的 queue 和 stack, 虽然看似容器, 其实只能算是一种容器配接器, 因为它们的底部完全借助 deque, 所有动作都由底层的 deque 供应.

6. 配置器 (allocators): 负责空间配置与管理. 从实现的角度看, 配置器是一个实现了动态空间配置、空间管理、空间释放的 class template.