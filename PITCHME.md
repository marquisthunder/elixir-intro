# Elixir
![Elixir](https://img.creditx.com/2017-07-07-09-47-00-201777.png)

![Erlang](https://img.creditx.com/2017-07-07-09-45-51-201777.png)

---
- [Elixir](#elixir)
- [Erlang & Elixir](#erlang-elixir)
    - [Joe Armstrong](#joe-armstrong)
    - [José Valim](#jos-valim)
- [Elixir的语法](#elixir)
- [Elixir的设计目标](#elixir)
- [Elixir兼容Erlang](#elixir-erlang)
- [Elixir的高效率](#elixir)
- [Elixir的可扩展](#elixir)
- [Elixir擅长并行和分布式应用](#elixir)
- [Elixir的开发体验](#elixir)
- [OTP Behavior](#otp-behavior)
    - [Supervisor](#supervisor)
    - [Gen*](#gen)
        - [GenServer](#genserver)
        - [GenEvent](#genevent)
        - [GenStage](#genstage)
            - [Word Count](#word-count)
            - [Eager](#eager)
            - [Lazy](#lazy)
            - [Concurrent](#concurrent)
            - [GenStage: Demand-driven](#genstage-demand-driven)

+++
# Erlang & Elixir

## Joe Armstrong
Erlang设计者
![Joe](https://img.creditx.com/2017-07-07-11-39-42-201777.png)
![Video](https://www.youtube.com/watch?v=uKfKtXYLG78)
---
## José Valim
Elixir设计者，Rails核心团队成员，Plataformatec联合创始人

![José Valim](https://img.creditx.com/2017-07-07-08-37-27-201777.png)
---

```
"99.9999999% reliability (9 nines) (31 ms. year!)"
http://ll2.ai.mit.edu/talks/armstrong.pdf
```
```
“The AXD301 has achieved a NINE nines
reliability (yes, you read that right,
99.9999999%). Let’s put this in context: 5 nines
is reckoned to be good (5.2 minutes of
downtime/year). 7 nines almost unachievable …
but we did 9.”
http://www.pragprog.com/articles/erlang
```
+++
---
# Elixir的语法

对于宏系统，只有在一种编程语言的语法能通过它自身的数据结构，以一种很直接的方式表达的情况下才合理。

设计了一种非常简洁的语法，而后逐步增加层次，这部分灵感大多来自Ruby和Erlang中的惯用法。

由于Elixir的目的是增强Erlang，所以我在做设计决定时经常向Erlang的语法和语义靠拢，这样就可以帮助开发者更好地融入生态圈。

---
+++
# Elixir的设计目标

José Valim：Elixir的设计目标可以概括为兼容性、高效率和扩展性这几部分。

---
# Elixir兼容Erlang
之前已谈到兼容Erlang VM是Elixir的目标之一，当我们谈到Erlang这个词，可以将它分解为下面三部分：

- 一种函数式编程语言Erlang
- 一系列设计原则，称为OTP |
- Erlang虚拟机，称为EVM或BEAM |

![Erlang Process](https://img.creditx.com/2017-07-07-11-23-12-201777.png)

---
# Elixir的高效率
- 所有Elixir代码在轻量级进程中运行，包含自己的状态，用于彼此交换信息。Erlang VM将这些进程分配到多个处理器核心中，使代码可以轻松地并行执行。

- Erlang运行时在CPU中的所有核心都在开动。当像Parallel这种技术变得更容易获取且成本更低廉时，你很难忽视Erlang VM所能提供的强大能力。未来Erlang VM将会被用来搭建能永久运行、能自我修复和扩展的系统。 |

- 效率很难测量，能高效开发桌面应用的编程语言却可能在数学运算领域捉襟见肘，它与你期望从事的领域、生态圈中的可用工具，以及是否能方便地创造和扩展这些工具有关。 |

---
# Elixir的可扩展
- 基于简洁的语言核心，开发者可以构建和扩展针对自己领域的语言。 
    - if
    - with

- 生态

---
# Elixir擅长并行和分布式应用
对于学习曲线的问题，没办法，谁让你不得不同时在学四件事情呢：erlang语法; 函数式语言的编程思想；一个几乎等同于操作系统的 VM；以及一套实用的设计模式。然而，这些付出的代价是值得的，它将你的系统级设计能力和分布式软件系统开发的能力提升了一个档次。即便你不用 erlang，这个代价也很值得，你可以把它的很多思想带入你所熟悉的语言中去解决问题。


+++

+++
# Elixir的开发体验

在这些领域，Elixir补充了下面一些标准库：

- Unicode字符串和相应的操作

- 强大的单元测试框架
![2017-07-07-08-50-09-201777](https://img.creditx.com/2017-07-07-08-50-09-201777.png)

- 更多数据类型

- 多态记录

- 便于脚本操作的函数，例如路径和文件系统

- 一些用于编译和测试Elixir代码的项目管理工具。

---

- 严格和惰性枚举API
    - Eager
    - Stream
    - Flow

- 自带分布式基础设施
    - gossip
    - multi-paxos

- REPL驱动开发

+++

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
![GenEvent](https://img.creditx.com/2017-07-07-08-55-57-201777.png)
+++
### GenStage
Prelude:

From eager,

to lazy, to concurrent,

to distributed

---
#### Word Count
```
“roses are red\n
violets are blue\n"
↓
%{“are” => 2,
“blue” => 1,
“red” => 1,
“roses" => 1,
“violets" => 1}
```
---
#### Eager
```
File.read!("source")
|> String.split("\n")
|> Enum.flat_map(&String.split/1)
|> Enum.reduce(%{}, fn word, map ->
 Map.update(map, word, 1, & &1 + 1)
end)
↓
%{“are” => 2,
 “blue” => 1,
 “red” => 1,
 “roses" => 1,
 “violets" => 1}
```
+++
- Simple
- Efficient for small collections
- Inefficient for large collections with multiple passes
---
#### Lazy
```
File.stream!("source", :line)
|> Stream.flat_map(&String.split/1)
|> Enum.reduce(%{}, fn word, map ->
 Map.update(map, word, 1, & &1 + 1)
end)
↓
%{“are” => 2,
 “blue” => 1,
 “red” => 1,
 “roses" => 1,
 “violets" => 1}
```
+++
- Folds computations, goes item by item
- Less memory usage at the cost of computation
- Allows us to work with large or infinite collections
---
#### Concurrent
```
File.stream!("source", :line)
|> Flow.from_enumerable()
|> Flow.flat_map(&String.split/1)
|> Flow.partition()
|> Flow.reduce(fn -> %{} end, fn word, map ->
 Map.update(map, word, 1, & &1 + 1)
end)
|> Enum.into(%{})
↓
%{“are” => 2,
 “blue” => 1,
 “red” => 1,
 “roses" => 1,
 “violets" => 1}
```
+++
- Give up ordering and process
locality for concurrency
- Tools for working with bounded and
unbounded data
---
![GenStage](https://img.creditx.com/2017-07-07-08-58-49-201777.png)
---
#### GenStage: Demand-driven
![GenStage-PC](https://img.creditx.com/2017-07-07-08-59-26-201777.png)
---
![GenStage-PBC](https://img.creditx.com/2017-07-07-09-00-21-201777.png)
---
- It is a message contract
- It pushes back-pressure to the boundary
- GenStage is one impl of this contract
- Inspired by Akka Streams
+++
