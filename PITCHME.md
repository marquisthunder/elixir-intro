# Elixir

![2017-07-07-09-03-50-201777](https://img.creditx.com/2017-07-07-09-03-50-201777.png)

---

# Elixir作者
![Elixir设计者，Rails核心团队成员，Plataformatec联合创始人José Valim](https://img.creditx.com/2017-07-07-08-37-27-201777.png)
---

# Elixir的语法在很大程度上借鉴了Erlang和Ruby，为什么你没有选择一种更激进的变化？

José Valim：在Elixir设计初期，我知道自己需要Elixir具备宏系统，这是从Lisp中得到的启发。对于宏系统，只有在一种编程语言的语法能通过它自身的数据结构，以一种很直接的方式表达的情况下才合理。带着这个目标，我设计了一种非常简洁的语法，而后逐步增加层次，这部分灵感大多来自Ruby和Erlang中的惯用法。

由于Elixir的目的是增强Erlang，所以我在做设计决定时经常向Erlang的语法和语义靠拢，这样就可以帮助开发者更好地融入生态圈。

---

# Elixir的设计目标

José Valim：Elixir的设计目标可以概括为兼容性、高效率和扩展性这几部分。

之前已谈到兼容Erlang VM是Elixir的目标之一，当我们谈到Erlang这个词，可以将它分解为下面三部分：

- 一种函数式编程语言Erlang；
- 一系列设计原则，称为OTP；
- Erlang虚拟机，称为EVM或BEAM。

---
Elixir与Erlang运行在同一种虚拟机上，并兼容OTP。不仅如此，所有Erlang生态系统中使用的工具和库，Elixir也能使用，因为在Erlang中调用Elixir没有任何性能代价，反过来也是如此。

所有Elixir代码在轻量级进程中运行，包含自己的状态，用于彼此交换信息。Erlang VM将这些进程分配到多个处理器核心中，使代码可以轻松地并行执行。

如果你编译Elixir代码，会发现CPU中的所有核心都在开动。当像Parallella这种技术变得更容易获取且成本更低廉时，你很难忽视Erlang VM所能提供的强大能力。未来Erlang VM将会被用来搭建能永久运行、能自我修复和扩展的系统。

效率很难测量，能高效开发桌面应用的编程语言却可能在数学运算领域捉襟见肘，它与你期望从事的领域、生态圈中的可用工具，以及是否能方便地创造和扩展这些工具有关。

基于这种原因，我们选择了简约的语言核心。在许多编程语言中，if、case、try这些关键词都需要专门的语法分析器，而Elixir中只有宏。这样做的好处之一是，开发者可以自己扩展语言，以适应他们自己的工作领域。宏还是Elixir元编程的构建基础：具备通过代码生成代码的能力，令开发者能摆脱烦琐的工作，创造出更强大的工具。

宏也对语法有巨大的影响，前面已经提到。尽管许多关于语言的话题一开始就会讨论语法，但在Elixir身上，从未将“简单地提供另一种不同语法”作为它的目标。

尽管基于简洁的语言核心，开发者可以构建和扩展针对自己领域的语言。但Elixir还继承了擅长并行和分布式应用的特点。

---

# Elixir 开发体验

在这些领域，Elixir补充了下面一些标准库：

- Unicode字符串和相应的操作

- 强大的单元测试框架
![2017-07-07-08-50-09-201777](https://img.creditx.com/2017-07-07-08-50-09-201777.png)
- 更多数据类型

- 多态记录

- 严格和惰性枚举API；

- 便于脚本操作的函数，例如路径和文件系统；

- 一些用于编译和测试Elixir代码的项目管理工具。
Mix 

此外，还有更多库、模块、协议等便于扩展的特性。

---
# OTP Behavior
一种系统工程语言

---
## Supervisor
- one_for_one
- one_for_all
- rest_for_all
- simple_one_for_one
    - Used for spawning children dynamically
    - init/1 must return a single child
    - Many APIs expect different values 

---
## Gen*
---
### GenServer
---
### GenEvent
![2017-07-07-08-55-57-201777](https://img.creditx.com/2017-07-07-08-55-57-201777.png)
---
### GenStage
---
![2017-07-07-08-58-49-201777](https://img.creditx.com/2017-07-07-08-58-49-201777.png)
---
#### GenStage: Demand-driven
![2017-07-07-08-59-26-201777](https://img.creditx.com/2017-07-07-08-59-26-201777.png)
---
![2017-07-07-09-00-21-201777](https://img.creditx.com/2017-07-07-09-00-21-201777.png)
---
- It is a message contract
- It pushes back-pressure to the boundary
- GenStage is one impl of this contract
- Inspired by Akka Streams
---
