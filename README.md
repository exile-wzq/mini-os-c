##  mini-os-c

---
**mini-os-c** 是一个使用 **C 语言实现的教学型计算机系统模拟器。**
项目目标是通过实现一个简化的 x86 风格系统，复现现代计算机系统中的关键机制，包括 
**CPU 执行、x86 寻址方式、内存系统、分页机制、Cache 模拟以及 I/O 设备。**

该项目旨在帮助理解计算机系统底层原理，而不是实现完整的 x86 架构。

---
## 项目目标

### 本项目主要用于学习和实践以下计算机系统核心概念：

- Instruction Set Architecture (ISA)

- x86 Addressing Modes

- CPU Instruction Execution

- Memory Hierarchy

- Virtual Memory and Paging

- Cache Simulation

- Memory-mapped I/O Devices

通过逐步实现这些模块，可以系统理解计算机系统从 **CPU → 内存 → I/O → 操作系统** 的整体结构。

---

## 系统架构

### 项目整体结构如下：
```markdown
mini-x86-sim
│
├── src
│   ├── cpu                # CPU执行与指令周期
│   │   ├── cpu.c
│   │   ├── exec.c
│   │   └── decode.c
│   │
│   ├── isa                # 指令集架构
│   │   └── x86
│   │       ├── instr.c
│   │       └── addressing.c
│   │
│   ├── memory             # 内存系统
│   │   ├── paddr.c
│   │   ├── vaddr.c
│   │   └── paging.c
│   │
│   ├── cache              # Cache 模拟
│   │   └── cache.c
│   │
│   ├── device             # I/O 设备
│   │   ├── io.c
│   │   └── timer.c
│   │
│   ├── monitor            # 调试工具
│   │   └── debugger.c
│   │
│   └── utils              # 日志与工具函数
│       └── log.c
│
├── include                # 头文件
│   ├── cpu.h
│   ├── memory.h
│   └── isa.h
│
├── tests                  # 测试程序
│
├── build                  # 编译输出目录
│
├── Makefile               # 构建系统
└── README.md
```

---
## 核心模块

### CPU 模块

#### CPU 模块负责模拟处理器执行过程，包括：

- Program Counter (EIP)

- General Purpose Registers

- Instruction Fetch

- Instruction Decode

- Instruction Execute

#### CPU 执行流程：
```markdown
Fetch → Decode → Execute`
```
---

## x86 寻址方式

#### 本项目重点实现 **x86 的经典寻址结构**：

`[ base + index * scale + displacement ]`

#### 例如：

`mov eax, [ebx + ecx*4 + 8]`

#### 地址计算：

`addr = EBX + ECX * 4 + 8`

#### 该模块用于理解：

- 基址寄存器

- 变址寄存器

- 偏移量

- scale 因子

---

## 内存系统

#### 系统模拟一个简单的物理内存：

`Physical Memory`

#### 基本操作：
```markdown
mem_read(address)
mem_write(address)
```
支持字节级访问。

---

## 虚拟内存

#### 项目实现基础的虚拟地址转换：
```markdown
Virtual Address
↓
Page Table
↓
Physical Address
```

#### 主要组件：
- Page Directory

- Page Table

- Address Translation

用于理解操作系统中的 **分页机制**。

---

## Cache 模拟

#### 实现一个简化的 **Direct Mapped Cache**：
```markdown
CPU
↓
Cache
↓
Memory
```

#### Cache 结构：

```markdown
Tag
Index
Offset
```
#### 用于理解：

- Cache Hit

- Cache Miss

- Memory Hierarchy

---

## I/O 设备

#### 系统模拟简单的 **Memory-mapped I/O** 设备，例如：

- Timer

- Basic I/O device

#### I/O 访问方式：

`memory address → device`

用于理解设备与内存系统的交互方式。

---

## 构建项目

#### 确保系统安装：
```markdown
gcc
make
```

#### 编译：
```markdown
make
```
#### 生成可执行文件：
```markdown
build/mini-os-c
```

---

## 运行

#### 运行模拟器：
```markdown
make run
```
#### 或者：
```markdown
./build/mini-os-c
```
---
## 清理构建文件
```markdown
make clean
```
---

## 项目开发路线

### Stage 1

#### 基础系统框架

- 项目结构

- Makefile 构建系统

- CPU 状态结构

---

### Stage 2

#### CPU 与寻址

- x86 寄存器

- 基本指令执行

- x86 Addressing Modes

---

### Stage 3

#### 内存系统

- Physical Memory

- Virtual Address Translation

- Paging

---

### Stage 4

#### Cache 模拟

- Direct-mapped Cache

- Cache Hit / Miss

---

## Stage 5

#### I/O 设备

- Memory-mapped I/O

- Timer / Device simulation

---
## 学习目标

#### 该项目旨在帮助理解：

- Computer Organization

- Operating Systems

- Computer Architecture

- Memory Hierarchy

- Instruction Set Architecture

适合作为 **计算机系统基础课程的实践项目**。

---

## 参考资料

- NEMU

- xv6

- Operating Systems: Three Easy Pieces

- Computer Organization and Design

---

## License

MIT License