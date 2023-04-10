---
tip: translate by openai@2023-04-11 08:30:21
...

# CHAPTER 2

# Fault Tolerant Mindset

The previous chapter defined the basic vocabulary and the four phases of fault tolerance. This chapter will look at techniques to design for fault tolerance and enhanced reliability and availability.

> 上一章定义了**基本词汇**和**容错的四个阶段**。本章将研究**设计容错和增强可靠性和可用性的技术**。

# _Fault Tolerant Mindset_

What can go wrong in any given situation? That is a key question to anyone trying to develop fault tolerant software. Thinking to ask the question and define the solution is called having a _Fault Tolerant Mindset_. In almost any situation something can go wrong. A fault tolerant program is prepared for these errors. Asking what-if questions and planning during design for the errors that _might_ happen during execution are the hallmarks of the Fault Tolerant Mindset. What if the stack pointer becomes negative? What if the wrong subclass is instantiated? What if the message arrives out of order?

> **在任何给定的情况下，会出现什么问题？**
> 这对于任何试图开发容错软件的人来说都是一个关键问题。思考提出问题并定义解决方案被称为拥有容错心态。**几乎在任何情况下都会出现问题。容错程序应该准备好这些错误。** 提出“如果”问题，并在设计时为可能在执行期间发生的错误做出计划，是容错心态的标志。如果堆栈指针变成负数会怎么样？如果实例化了错误的子类会怎么样？如果消息排序错误会怎么样？

Applying a Fault Tolerant Mindset to all stages of software development is beneficial. This includes both during requirements definition and test development as well as the traditional phases of software creation (architecture, design, coding).

> 在软件开发的所有阶段采用容错的思维方式是有益的。这包括在需求定义和测试开发期间，以及传统的软件创建阶段（架构，设计，编码）。

# _Design Tradeoffs_

‘Every problem in computer science boils down to tradeoffs’ – Professor L. J. Henschen.

> **"所有计算机科学的问题都归结为权衡取舍" - L. J. Henschen 教授**

Mean Time To Failure (MTTF) and Mean Time to Repair (MTTR) determine the reliability and availability of a system. These two parameters can be traded off against each other. In some contexts, MTTR is the more important attribute, especially if the system is striving for high availability. Examples include telecommunications systems.

> **平均故障时间(MTTF)和平均修复时间(MTTR)决定系统的可靠性和可用性。这两个参数可以相互抵消。** 在某些情况下，MTTR 是更重要的属性，特别是如果系统正在努力实现高可用性。例子包括电信系统。

In other cases the repair time, MTTR, can be long but the MTTF must also be very long. An example is the Space Shuttle, which must perform without failure for the mission duration but once it is on the ground the repair can take more than an instant.

> 在其他情况下，**维修时间 MTTR 可能会很长，但 MTTF 也必须很长**。一个例子是航天飞机，它**必须在任务期间不出故障，但一旦它落地，维修可能需要不止一瞬间**。

Other systems, such as an ATM banking system, must be failure-free but also highly available. This requires a thorough analysis during the design of the hardware and software components to ensure both high MTTF and low MTTR.

> 其他系统，如**自动取款机银行系统，必须无故障且具有高可用性**。这需要在硬件和软件组件的设计过程中进行彻底的分析，以确保高 MTTF 和低 MTTR。

# _Quality v. Fault Tolerance_

A common misconception is that good quality processes guarantee fault tolerance. This is not necessarily the case. The two ideas are related, but they are distinct from each other.

> **一个常见的误解是，良好的质量流程可以保证容错性。这并不一定是真的。这两个想法是相关的，但它们也是有区别的。**

Fault tolerance is the ability of the system to execute properly even though there are faults present. Fault tolerance happens at execution time. Saying that a system is fault tolerant says that it was designed in such a way that the system can still behave correctly and not have a failure, even if errors occur during the execution of the system. It also says that a failure will do limited harm

> **容错是系统在存在故障的情况下仍能正常执行的能力。** 容错发生在执行时。说**一个系统是容错的意味着它被设计成即使在执行过程中发生错误，系统仍能正确行为，不会发生故障。这也意味着，即使发生故障，也不会造成严重损害。**

Quality, on the other hand, refers to how fault-free the system is. Quality techniques address ‘how’ the software/system is created. Were code inspections done? Was it fully tested?

> **质量指的是系统的无缺陷程度。** 质量技术解决的是软件/系统如何创建的问题。是否进行了代码检查？是否进行了完整的测试？

A high quality system will have fewer faults than a lower quality system, which in turn results in fewer errors occurring during execution in the higher quality system and hence fewer failures. Reduction in the number of faults present in the system doesn’t imply that the results of the faults are less severe. The system must take steps to reduce the impact of the errors and failures. These steps provide the system with the ability to tolerate the effects of errors.

> 高质量的系统比低质量的系统有更少的故障，这反过来又导致在高质量系统中执行时发生的错误更少，因此失败的可能性也更少。系统中故障的减少并不意味着故障的结果就会变得不那么严重。系统必须采取措施来减少错误和失败的影响。这些措施使系统能够容忍错误的影响。

Quality is aimed at preventing faults from entering the system. Reducing the number of faults per line of code (or other unit of measuring a program) is the goal because that will reduce the number of faults that can cause errors. Fault Prevention techniques aim to prevent the addition of faults to the system. Fault Prevention is sometimes considered one of the phases of fault tolerance.

> **质量的目的是防止缺陷进入系统。** 减少每行代码（或其他衡量程序的单位）的缺陷数量是目标，因为这将减少可能导致错误的缺陷数量。**故障预防技术旨在防止向系统添加缺陷。故障预防有时被认为是容错的一个阶段。**

# _Keep It Simple_

A well known principle of fault tolerant design is that of ‘KIS’, which means ‘Keep It Simple’. Complexity in the system makes it more difficult to ensure correct operation through the design and test processes. Additional complexity requires writing additional software, which for a given density of faults means that there will be more faults present.

> 一个众所周知的**容错设计原则是“KIS”，意思是“保持简单”**。系统的复杂性会使设计和测试过程变得更加困难。额外的复杂性需要编写额外的软件，对于给定的故障密度来说，将会存在更多的故障。

In many cases fault tolerant software is ‘good enough’ because to provide the thorough solution would mean adding too much extra code with too much risk of additional faults.

> 在许多情况下，容错软件已经足够“良好”，因为**要提供彻底的解决方案意味着要添加太多额外的代码，并且存在太多额外故障的风险**。

One common goal of the Keep It Simple principle is to reduce the number of lines of code dedicated to a task. Fewer lines of code mean fewer latent faults. Instead of designing an elaborate mechanism worthy of a graduate research project, build the simple mechanism that will be easier to maintain, easier to debug, and less likely to contain hidden faults.

> 一个保持简单原则的共同**目标是减少致力于一项任务的代码行数**。较少的代码行意味着较少的潜在故障。不要设计一个复杂的机制，值得毕业研究项目，而是构建一个更容易维护、更容易调试、更不容易出现隐藏故障的**简单机制**。

An important aspect of Keep It Simple is to build the right system. Build the system that the specifications call for and don’t add extra features or bells and whistles. The extra code will contain unnecessary faults.

> 采用简洁的方法很重要，要按照规格构建正确的系统，**不要添加额外的功能或装饰**。多余的代码会包含不必要的错误。

# _Incremental Additions of Reliability_

Many projects add fault tolerance incrementally. Through continual refinement many small enhancements will have large impacts in fault tolerance. A policy of studying every failure and implementing any design changes that are suggested by analysis is a certain way to improve the system’s fault tolerance.

> 许多项目逐步增加容错性。通过持续的精化，许多小的增强将在容错性方面产生巨大的影响。**研究每一次失败并实施分析建议的设计变化，是提高系统容错性的一种确定方法。**

For example the 4ESS™ Switch project had a policy to correct every fault that was identified. Every failure that was reported in the field was investigated and tracked back to a fault that could be identified and corrected in the next annual release of software, or sooner if necessary. This effort resulted in a highly reliable system that has been functioning in the US telephone network for over 30 years.

> 例如，4ESS™ 交换机项目**有一个政策来纠正每一个被发现的故障**。每一个在现场报告的失败都被调查，并追踪到可以在下一个软件年度版本中识别和纠正的故障，或者如果有必要的话，更快地进行纠正。这项努力**产生了一个高可靠性的系统，已经在美国电话网络中运行了 30 多年**。

# _Defensive Programming Techniques_(_防御性编程技术_)

After the basics of the programming language have been mastered, _defensive programming_ techniques should be learned to produce fault tolerant code. Defensive programming builds on the Fault Tolerant Mindset to produce code that defends itself against the potential problems that arise. Programming defensively is done constantly, in every situation, by asking ‘what can go wrong here?’, ‘what errors can occur?’, ‘how might this fail?’, and ‘how can this code be protected from errors in other parts?’.

> 当编程语言的基础知识掌握后，应该**学习 _防御性编程_ 技术来创建容错的代码**。防御性编程基于容错思维模式，创造能够抵抗可能出现的问题的代码。防御性编程是一种持续不断的行为，在每一个情况下，**都要问“这里可能出现什么问题？”，“会出现什么错误？”，“这里可能失败吗？”，“这段代码如何受到其他部分错误的保护？”**。

## Faults in Fault Tolerance Code

Even the software written to perform only fault tolerant related activities can have faults. Given any constant density of faults per line of code, when there are more lines of code there will be more faults. Adding complexity to error handling code increases the risk of adding faults to the software. Keep it Simple!

> **即使是为执行故障容错相关活动而编写的软件也可能存在故障。鉴于每行代码的故障密度是恒定的，当有更多的代码行时，将会有更多的故障。增加错误处理代码的复杂性会增加软件出现故障的风险。保持简单！**

A related problem is that of accidentally adding faults to a system when trying to repair faults that have caused errors. This complicates the ultimate correction because now the system requires a ‘fix on fix’.

> 这种问题的一个相关问题是，在试图修复导致错误的故障时，会意外地添加故障到系统中。这使最终的修复变得复杂，因为现在系统需要“修复修复”。

Faults in the special software added to ensure fault tolerance might prevent error recovery or mitigation from ever completing successfully.

> 特殊软件中的故障可能会阻碍错误恢复或缓解成功完成。

## Memory Corruption(内存腐败)

You should not assume that data storage is always correct. There are many potential errors, from stray writes to bad memory chips to transient errors like **alpha particles**. Information retrieved from memory should be checked before it is used. This applies whether the memory is long term storage such as a disk or database, or short term such as a message queue. This is especially important when using the information to determine program execution paths.

> 你**不应该假定数据存储总是正确的**。有很多潜在的错误，从乱写到坏内存芯片到像 α 粒子这样的瞬态错误。**在使用信息之前，应该检查从内存中检索的信息**。无论存储是长期存储，如磁盘或数据库，还是短期存储，如消息队列，都是如此。当使用信息来确定程序执行路径时，这一点尤为重要。

> [!NOTE] > **在使用信息之前，应该检查从内存中检索的信息**

For example, a protocol standard defines a message type field in its messages with five valid message types defined in the standard. A three bit field is used to store the message type. A common way to process the message is to use a switch or case statement to branch to the appropriate section of the program. The software designers must ensure that the invalid message types are handled correctly, either by reporting them as an error, taking a default action or discarding the message. There are many reasons why the message might contain an invalid type field: message corruption from a communications line, the memory elements that made up the queue in which the messages was stored might have been faulty, a fault in the software that received and placed the message in the queue might have changed the messages type, etc.

> 例如，协议标准在其消息中定义了一个消息类型字段，标准中定义了五种有效消息类型。使用三位字段来存储消息类型。处理消息的一种常见方法是使用 switch 或 case 语句转到程序的适当部分。软件设计人员**必须确保正确处理无效消息类型**，要么报告它们为错误，要么采取默认操作或丢弃消息。消息可能包含无效类型字段的原因有很多：通信线路的消息损坏，构成消息存储队列的内存元素可能有故障，接收并将消息放入队列中的软件故障可能会改变消息类型等。

Memory leakage is a common potential fault. A common scenario for this is a task acquiring a block of memory which is accessed by a pointer. Then the task terminates without releasing the block of memory that it was allocated. Since the only way to access that block of memory was via the pointer that was local to the task that has terminated, the only pointer to the memory is gone. The memory is unavailable for use. Even if the task that acquired the memory does not terminate holding the only copy of the pointer, subsequent faults might result in the pointer being deleted without the memory being freed for other usage.

> **内存泄漏是一个常见的潜在缺陷。** 一个常见的场景是任务获取一个由指针访问的内存块。然后**任务终止而没有释放它分配的内存块**。由于访问该内存块的唯一方法是通过已终止的任务的本地指针，唯一的指针就消失了。该内存不可用于使用。即使获取内存的任务没有终止持有唯一的指针，后续故障也可能导致指针被删除而内存未被释放以供其他用途。

Pointers are dangerous because they enable access directly to memory and memory structures without many safeguards. Through the use of pointers, regions of memory can be accessed in ways that they weren’t designed for. This allows great power in the hands of a skilled expert, but also presents the risk of security breaches or mistakes.

> 指针很危险，因为它们可以直接访问内存和内存结构，而没有太多的保护措施。通过使用指针，可以以未设计的方式访问内存区域。这给熟练的专家提供了强大的力量，但也带来了安全漏洞或错误的风险。

Another potential problem with pointers is pointers and the regions of memory to which they point are allocated and deallocated independently. Pointers can still be maintained and used, even after the region of memory has been deallocated and possibly reallocated to another task, enabling access to the new task’s memory.

> 指针的另一个潜在问题是，**指针指向的内存区域是独立分配和释放的。即使内存区域已经被释放，并可能被分配给另一个任务，指针仍然可以维护和使用，从而访问新任务的内存。**

Whenever using pointers, consider how they can be misused or accidentally create problems. Design the use of pointers in the safest possible way.

> 使用指针时，要考虑它们可能被误用或意外造成问题。**以最安全的方式设计使用指针**。

## Data Structure Design

Data structures should be designed so that they can be _audited_, or checked, for correctness. Audits should check both for correct values and to ensure that the data structure integrity is intact. For example, the check will ensure that impossible data is not stored in a linked list structure and that the list elements are correctly linked.

> **数据结构应该设计得可以被审计，或检查它们的正确性。** 审计既要检查正确的值，也要确保数据结构的完整性。例如，检查将确保链表结构中不会存储不可能的数据，并且列表元素会正确链接。

Data structure design should also support correction of the data. An example of a design for data correction is to include both forward and backward links in important linked lists. This provides redundant connection information and enables a check to ensure that both ends of a link know that they are in fact linked. It also provides enough information to allow the linkage to be reconstructed, if necessary.

> **数据结构设计也应支持数据的纠正。** 一个用于数据纠正的设计示例是在重要的**链表中包含前向和后向链接。这提供了冗余的连接信息**，并使得链接的两端都知道它们实际上是连接的。它还提供了足够的信息，**以便在必要时重建链接**。

## Design for Maintainability

Fault tolerant systems last a long time. Design them in a way that will make the life of the maintainer easier, because they might not be the initial designer. Use short modules, methods and functions. Make the code readable through the use of white space and comments. Keep the control flow simple because that will be easier to understand and to change if that becomes necessary.

> 系统容错能够持续很长时间。请以让维护者更轻松的方式设计它们，因为他们可能不是最初的设计者。使用短小的模块、方法和函数。通过使用空格和注释使代码可读。保持控制流程简单，因为这样更容易理解和在需要时更改。

## Coding Standards

Coding standards are another way of improving the quality of software as it is written. Many of the defensive coding techniques just mentioned are best implemented as coding standards. Projects adopt a number of principles that they then use to guide development and to judge the quality of the final code. A principle to remember when dealing with coding standards is this: people cannot remember a large number of things. If a project has 100 standards, it is unlikely that the project members can effectively remember and follow each of them. Having a small number that can be followed and verified will result in higher quality software. And higher quality software means that fewer errors will need to be handled at execution time to ensure fault tolerance.

> **编码标准是提高软件质量的另一种方法。** 刚才提到的许多防御性编码技术最好以编码标准的形式实施。项目采用了许多原则，然后使用这些原则来指导开发，并判断最终代码的质量。处理编码标准时要记住的一个原则是：人们不能记住大量的东西。如果一个项目有 100 个标准，那么项目成员不太可能有效地记住和遵循每一个标准。只有少量的标准可以遵循和验证，才能产生更高质量的软件。更高质量的软件意味着在执行时需要处理更少的错误，以确保容错性。

## Redundancy

Redundancy is one of the cornerstones of fault tolerance. It will be discussed in the pattern REDUNDANCY (3) in Chapter 4. Redundancy refers to duplicate capabilities in a system which enables for more rapid error recovery and fault treatment. When added to a system to support fault tolerance, redundancy is meant to improve operational quality, not to improve the functionality of the system.

> **冗余是容错性的基石之一。** 它将在第 4 章的 REDUNDANCY（3）模式中进行讨论。冗余指的是系统中的重复功能，可以更快地恢复错误和处理故障。当添加到系统中以支持容错性时，**冗余的目的是提高操作质量，而不是提高系统的功能**。

You can think about redundancy in both time and space dimensions. Time based redundancy can be the sequential execution of different versions of a program followed by a selection, or VOTING (21), of which result to use. Other time based redundancy includes recalculating parameters that don’t change frequently (or ever) to ensure that the parameter value in use is always correct. Space based redundancy is usually implemented by executing a program on different computers. The programs might be identical, or they might be different versions. The different computers are typically located within a cluster, and can be geographically dispersed also.

> 你可以**在时间和空间维度上考虑冗余**。
>
> - 基于时间的冗余可以是连续执行不同版本的程序，然后进行选择或投票（21），以选择使用哪个结果。其他基于时间的冗余还包括重新计算不经常（或从不）改变的参数，以确保使用的参数值始终正确。
> - 基于空间的冗余通常是在不同的计算机上执行程序。这些程序可能是相同的，也可能是不同的版本。不同的计算机通常位于集群中，也可以在地理上分散。

## Static Analysis Tools

## N-Version Programming

With N-Version Programming, NVP, independent development teams use the same specification to generate multiple implementations. During development the design teams are kept separate and do not share their designs, nor do they discuss the specification’s meaning with each other. The design teams should use different algorithms and different programming languages to produce multiple versions that all contain different faults.

> 使用 **N 版本编程（NVP）**，独立的开发团队使用相同的规范来生成多个实现。在开发过程中，设计团队保持分离，不共享设计，也不彼此讨论规范的含义。设计团队应使用不同的算法和不同的编程语言来生成多个版本，所有这些版本都包含不同的错误。

NVP employs redundancy at all levels from design/development to execution. NVP enables parallel execution of computational blocks. A technique discussed in Chapter 4, RECOVERY BLOCKS (4), provides for sequential computation of computational blocks. Serial execution of this parallelism is possible on a uniprocessor as long as there is separation between versions.

> NVP 在从设计/开发到执行的所有层面都采用冗余。NVP 可以并行执行计算块。第 4 章讨论的技术 RECOVERY BLOCKS（4）可以对计算块进行顺序计算。**只要版本之间有分离，就可以在单处理器上实现这种并行性的串行执行。**

The fundamental principle of NVP is that there are multiple implementations done by different development teams. The same developer cannot make multiple implementations with multiple understandings of the same specification. The assumption is that when a latent fault activates in one version then the other versions of the system do not contain the same fault. Research by Knight and Leveson [KL86][kl90] has shown that the assumption of independence between the faults produced by the different design teams does not hold. Research into NVP continues for example in work by Cai, Lyu and Vouk [CLV05].

> NVP 的基本原则是由不同的开发团队完成多种实现。同一开发者不能用多种理解对同一规范进行多种实现。**假设当一个潜在故障在一个版本中激活时，其他版本的系统中不包含相同的故障。** Knight 和 Leveson [KL86][kl90]的研究表明，不同设计团队产生的故障之间的独立性假设是不成立的。Cai、Lyu 和 Vouk [CLV05]等人对 NVP 的研究仍在继续。

Because of the need for multiple design teams, NVP is not something that an individual or small team can decide on their own to undertake. For this reason, this book does not discuss NVP.

> 由于需要多个设计团队，NVP 不是一个个人或小团队可以自行决定去承担的事情。因此，本书不讨论 NVP。

## Redundant Disks [PGK88][ms00]

RAID, or ‘redundant array of inexpensive disks’, is a technology for grouping disks together to make a complex that provides redundancy and hence fault tolerance that is unavailable on a single disk. There are five levels of RAID that increase the level of disk redundancy, RAID-1 through RAID-5. An additional level, RAID-0, is an alternate method of writing data to a disk, which does not increase redundancy.

> RAID，即“廉价冗余磁盘阵列”，是一种把磁盘组合在一起的技术，可以**提供单个磁盘所不具备的冗余性和容错性**。RAID 有五个级别，从 RAID-1 到 RAID-5，可以提高磁盘的冗余性。另外一个级别 RAID-0 是将数据写入磁盘的另一种方法，不增加冗余性。

RAID works by combining groups of disk drives into a single element. The data is spread over the disks in one of several ways. Disk striping, used by RAID-0, stores consecutive chunks of data spread over a number of disks. This enables parallelism in reading and writing and hence faster access. Disk striping alone does not increase reliability, but it increases performance.

> RAID 通过将磁盘驱动器组合成一个单一元素来工作。数据以多种方式在磁盘之间分散。RAID-0 使用的磁盘条带存储在多个磁盘上分散的连续块数据。**这使得并行读写成为可能，从而提高访问速度。仅仅使用磁盘条带不会增加可靠性，但可以提高性能。**

Disk mirroring is used by RAID-1. The same data is written to multiple disks simultaneously. It is synchronized between the disks, so that if any of the disks fail there are redundant, identical copies of the data. This increases the reliability of the data with only a small performance increase.

> RAID-1 使用磁盘镜像。相同的数据同时写入多个磁盘。它**在磁盘之间同步**，这样如果任何磁盘出现故障，就会有冗余的相同数据副本。这只会增加少量性能，但可以提高数据的可靠性。

[**Table 2.1**](#c02.htm#tab2.1a) RAID levels

```
    <table class="bodytable">
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <tbody>
    <tr class="odd" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black; border-top: 1px solid black; background-color: black; color: white"><strong>RAID LEVEL</strong></td>
    <td class="bodycell" style="border-bottom: 1px solid black; border-top: 1px solid black; background-color: black; color: white"><strong>MECHANISM</strong></td>
    <td class="bodycell" style="border-bottom: 1px solid black; border-top: 1px solid black; background-color: black; color: white"><strong>REDUNDANCY EFFECT</strong></td>
    </tr>
    <tr class="even" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black; width: 20%">RAID-0</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Disk striping: data is spread over multiple disks</td>
    <td class="bodycell" style="border-bottom: 1px solid black">No redundancy improvement, primarily a performance enhancement</td>
    </tr>
    <tr class="odd" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black">RAID-1</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Disk Mirroring. The same data is kept synchronized on a second disk</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Slight performance increase because one disk can be writing while the other is reading.<br />
    Second copy available immediately if a disk fails</td>

    </tr>
    <tr class="even" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black">RAID-2</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Hamming Encoding. Encode data on the disk with an error correcting code</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Data on a single disk is correctable should an error be detected</td>
    </tr>
    <tr class="odd" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black">RAID-3</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Virtual Disk Blocks, data stored striped across disks with a separate disk for parity information</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Data can be reconstructed based on parity</td>
    </tr>
    <tr class="even" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black">RAID-4</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Dedicated Parity Disk. Parity for all data is stored on a separate disk</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Data can be reconstructed based on parity for data</td>
    </tr>
    <tr class="odd" data-valign="top">
    <td class="bodycell" style="border-bottom: 1px solid black">RAID-5</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Striped Parity Disk. Parity is stored striped across all the disks</td>
    <td class="bodycell" style="border-bottom: 1px solid black">Data can be reconstructed based on parity information</td>
    </tr>
    </tbody>
    </table>
```

RAID technology is common and is included in many commercial products today. For more information about RAID, refer to product literature or Marcus and Stern [MS00].

> RAID 技术在当今的商业产品中很常见。有关 RAID 的更多信息，请参阅产品文献或 Marcus 和 Stern [MS00]。

# _The Role of Verification_

Testing and verification are essential to the creation of fault tolerant computing systems because they ensure that fault prevention and quality efforts are successful. Testing and verification also provide the data needed by a project’s software reliability engineers to compute the expected reliability of a system.

> 测试和验证对于创建容错计算系统是至关重要的，因为它们确保故障预防和质量努力取得成功。测试和验证也提供项目软件可靠性工程师需要计算系统预期可靠性的数据。

A useful kind of testing for fault tolerant systems is operational profile testing. An operational profile describes the usage of the system in quantitative terms and the most typical scenarios that the system will process. This information helps define the most appropriate tests to be run, and how to focus testing efforts. Operational profiles are the scenarios that are used in design, development, and test. To test the reliability and performance of the system the operational profile adds quantitative information to the descriptions of typical scenarios. For more information on operational profiles, refer to Musa et al. [MFI+96]

> 对于容错系统，运行配置测试是一种有用的测试方式。运行配置描述了系统使用的定量信息以及系统最常见的场景。这些信息有助于定义最适合的测试，以及如何集中测试工作。运行配置是用于设计、开发和测试的场景。为了测试系统的可靠性和性能，运行配置为典型场景提供定量信息。有关运行配置的更多信息，请参阅 Musa 等人[MFI+96]。

_The Handbook of Software Reliability Engineering_ [Lyu96] contains more detailed information about testing and verification for reliability.

> 《软件可靠性工程手册》[Lyu96]包含有关可靠性测试和验证的更详细的信息。

# _Fault Insertion Testing_

A technique that is used during the testing and verification phase of a project is fault insertion testing. Testers insert known faults into the system and the system’s behavior is monitored. This testing serves the dual purpose of identifying faults in the system’s error handling processes and of providing data for the computation of coverage factors.

> 插入故障测试是在项目测试和验证阶段使用的一种技术。测试人员将已知的故障插入系统，并监视系统的行为。这种测试具有双重目的，一是识别系统错误处理过程中的故障，二是为覆盖因素的计算提供数据。

Fault insertion testing is the only way that a system’s coverage factor can be determined. Known faults are introduced into the system, which is then observed to see if the system was able to handle the faults automatically. The coverage is computed as the percentage of cases in which recovery was successful.

> 故障插入测试是唯一可以确定系统覆盖率的方法。将已知故障插入系统中，然后观察系统是否能够自动处理故障。覆盖率计算为恢复成功的情况下的百分比。

Software fault insertion testing is done by providing erroneous inputs to the system. One way is to alter the normal input to determine the system’s behavior to incorrect values. This is commonly called boundary testing. The next level beyond this is to place ‘hooks’ into the software, or use a debugging tool, to enable internal values and state to be altered.

> 软件故障插入测试是通过向系统提供错误的输入来完成的。一种方法是改变正常的输入以确定系统对不正确值的行为。这通常被称为边界测试。超越此级别的下一步是在软件中放置“钩子”，或使用调试工具来使内部值和状态可被更改。

# _Fault Tolerant Design Methodology_

This chapter has discussed a number of aspects of the Fault Tolerant Mindset and has offered some guidelines for creating fault tolerant systems. The following six-step methodology is useful to build upon the Fault Tolerant Mindset and produce a highly available system.

> 本章讨论了容错思维的许多方面，并提供了一些创建容错系统的准则。以下六步法有助于建立容错思维，并产生高可用系统。

**1.** The first step is to assess the things that can go wrong with the system. What can go wrong? What are the failures? The technique of _fault trees_ can be useful at this stage. [Dug95]

> **1.** 首先要评估系统可能出现的问题。出现什么问题？会出现什么失败？这一步骤可以使用*故障树*技术来有效地完成。[Dug95]

**2.** After the risks have been identified, strategies must be defined to mitigate the risks. For each of the potential failures that were identified, how could they be identified and detected before becoming an actual failure? What things could be done in the system to prevent the failures from occurring, and the faults from activating? The project specific pattern language that will be used during design is identified in step 2.

> **2.** 在识别出风险后，必须定义策略来减轻风险。对于识别出的潜在故障，如何在变成实际故障之前发现和检测它们？系统中可以做些什么事情来防止故障发生和故障激活？在第二步中确定了将在设计过程中使用的项目特定语言模式。

**3.** Create a mental model of your system identifying the primary system dividing points and modes of redundancy.

> **3.** 建立一个系统的心理模型，识别主要的系统分割点和冗余模式。

**4.** At this point the architectural and major design decisions can be made. These are the ones that influence the whole system. Chapter 4 contains patterns for these high level decisions.

> **4.** 在这一点上，可以做出建筑和主要设计决策。这些决策会影响整个系统。第 4 章包含了这些高级决策的模式。

**5.** Design in the capabilities for the system to implement the risk mitigation strategies identified in step 2. There are a wide variety of techniques that are presented in Chapters 5 through 8, organized by the four phases of fault tolerance.

> **5.** 为系统设计实施第 2 步确定的风险缓解策略的能力。**第 5 到第 8 章提供了各种技术，按照容错的四个阶段进行组织。**

**6.** Almost all systems, no matter how fault tolerant they are, require some provisions that enable them to be managed and administered by people. Some of these provisions are done inside the design and some aspects relate to the user’s environment and your assumptions about that environment. Designing these human computer interactions and modes of management are important and must be done sensibly to ensure that failures won’t be caused by the people who are trying to administer the system. The techniques for this are not covered in this work. For more information you can look at _Designing Interfaces_ by Tidwell [Tid05] or ‘An Input and Output Pattern Language’ [HS00].

> 几乎所有的系统，无论它们有多么容错，都需要一些规定来使它们能够被人管理和维护。这些规定有些是在设计中完成的，有些是与用户环境和您对该环境的假设有关的。设计这些人机交互和管理模式非常重要，必须明智地完成，以确保故障不会由试图管理系统的人引起。本文不涉及这些技术。要了解更多信息，可以参考 Tidwell [Tid05]的《设计界面》或‘An Input and Output Pattern Language’ [HS00]。

This methodology is adapted from one in _Secure Coding_, Graff and van Wyk [GvW03]. It has been put in terms of fault tolerance and the Fault Tolerant Mindset.

> 这种方法是从 Graff 和 van Wyk [GvW03]的《安全编码》中改编而来的。它已经用容错性和容错性思维方式来表达。

This methodology will be used in an example problem, to design a fault tolerant Presence Server in the Conclusion.

> 这种方法将在结论中用于一个示例问题中，以设计一个容错的存在服务器。

The benefit of this methodology is that it will get you thinking about what can go wrong with the system. The Fault Tolerant Mindset begins in step 1 where you identify the failures and the risks factors that can cause them. Step 5 comes back to the risks and failures to see if mitigation techniques have been added to the design to cover the risks. Step 2 gives you a chance to think about the risks and the patterns and other techniques that will be useful to mitigate the risks. The pattern language for your project is created in this step. Steps 3 and 4 are where the fault tolerant design starts to take shape. Any elements of redundancy present in the system that can be leveraged to mitigate risks are studied and enhanced in step 3. Step 4 continues the design of the error detection and error processing capabilities of the system. People will interact with the system being designed both as users and as operating personnel. Step 6 considers how the human computer interface can be made more robust and more error-free.

> 这种方法的好处是它会让你思考系统可能出现的错误。容错思维从步骤 1 开始，在这一步，你要识别可能导致错误的失败和风险因素。步骤 5 则回到这些风险和失败，看看设计中是否添加了抵御风险的缓解技术。步骤 2 给你一个机会去思考风险和模式以及其他可以用来缓解风险的技术。这一步是为你的项目创建模式语言。步骤 3 和 4 是容错设计开始形成的阶段。步骤 3 研究系统中可以利用来缓解风险的冗余元素并进行增强。步骤 4 继续设计系统的错误检测和错误处理能力。人们将以用户和操作人员的身份与被设计的系统进行交互。步骤 6 考虑如何使人机界面更加健壮和错误率更低。

<span id="c03.htm"></span>
