# 确演运行时 · QueYan Runtime

版本 1.0.0    |    许可证 AGPL v3    |    JIT编译    |    分代GC

确演运行时为确演OS之应用执行环境，实现确演字节码之解释执行与即时编译。虚拟机采用栈帧架构，支持类型推导与内联缓存。垃圾回收器实现分代并发标记-清除，写屏障采用卡表算法。JIT编译器基于Sea-of-Nodes IR，实现逃逸分析与锁粗化优化。

技术特征

- 解释器采用直接线程码技术，指令分派延迟小于2纳秒
- JIT编译阈值动态调整，热点探测采用计数器衰减算法
- GC实现并发标记与增量压缩，停顿时间小于3毫秒
- 类型系统支持泛型特化与单态化，消除运行时类型检查开销

性能指标

冷启动时间：小于180毫秒
解释执行吞吐量：约5200万指令每秒
JIT峰值吞吐量：约6.2亿指令每秒
GC暂停时间：小于2.8毫秒

编译与部署

git clone https://github.com/9178139191/queyan-runtime
cd queyan-runtime
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
make -j$(nproc)

---

English Abstract

QueYan Runtime is the application execution environment for QueYan OS, featuring a stack-based virtual machine with type inference and inline caching. The garbage collector implements generational concurrent mark-sweep with card table write barriers. The JIT compiler uses Sea-of-Nodes IR with escape analysis and lock coarsening optimizations.

GNU Affero General Public License v3.0

This program is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License along with this program. If not, see https://www.gnu.org/licenses/.

Copyright © 2026 确演OS. 保留所有权利。
