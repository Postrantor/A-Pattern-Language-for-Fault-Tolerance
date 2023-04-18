# **Conclusion**

The previous five chapters contain patterns that can help make your software designs more fault tolerant. Chapter 4 contained architectural principles that you should use to structure your overall solution. Chapter 5 presented patterns to help detect the presence of errors and faults before failures occur. Chapters 6 and 7 gave ways to process errors. Sometimes the processing results in the system execution state changing, and sometimes the errors and faults can be processed in a way that doesn’t change the execution flow. Chapter 8 contained patterns to help treat the faults and return the erroneous component to availability. This chapter shows the complete pattern language and gives an example of how the patterns can work together.

> - 前五章包含了可以帮助你的软件设计更加**容错的模式**。
> - 第四章包含了你可以用来结构你的**整体解决方案的架构原则**。
> - 第五章提出了一些模式来帮助在发生**故障之前检测错误**和故障的存在。
> - 第六章和第七章给出了**处理错误的方法**。
>   - 有时候处理结果会导致系统执行状态发生变化，
>   - 有时候错误和故障可以以不改变执行流的方式处理。
> - 第八章包含了一些模式来帮助处理故障并让有问题的组件重新可用。
>   本章节**展示了完整的模式语言并给出了模式如何协同工作的例子**。

# _A Pattern Language for Fault Tolerant Software_

Each chapter began with a description of the patterns and how they related to each other and how they worked together to make a system more fault tolerant. Linkages between the patterns in different chapters were not highlighted, except in the individual pattern descriptions. See back of book for a map of all of the patterns. Within this overall pattern map you can see some of the linkages between the patterns of the individual phases.

> 每一章都以描述模式及其相互间的关系和如何协同工作以使系统更具容错性开始。除了在单独的模式描述中，各章之间的联系并未被突出。请参阅本书**背面的模式地图以查看所有模式的地图**。在整体模式地图中，您可以看到各个阶段模式之间的一些联系。

![A Pattern Language for Fault Tolerant Software](./OEBPS/images/301-1.jpg)

> [!NOTE]
> 这个图很好，但是就是有点糊呀！！！

This figure represents only one possible combination of these patterns into a usable language. Others are possible, because the choice of patterns to apply to a given design problem depends on the context and the nature of the system, as illustrated through the example in the next section.

> 这个图表只代表了将这些模式组合成一种可用语言的一种可能性。其他可能性也是存在的，因为对于给定的设计问题，选择要应用的模式取决于上下文和系统的性质，如下一节中的例子所示。

The key connections between the patterns in the different chapters, as well as within the chapters, are shown. Not every possible connection that you might make when combining these patterns into a project specific language are shown. Neither is every reference made in the pattern text shown.

> 在不同章节中模式之间以及章节内的关键关联已经展示出来。当把这些模式结合到特定项目的语言中时，不是每一个可能产生的关联都展示出来。模式文本中的每一个引用也不一定展示出来。

There are four main entry points (top level patterns) into this language map. These are UNITS OF MITIGATION (1), CORRECTING AUDITS (2), MINIMIZE HUMAN INTERVENTION (5) and SOFTWARE UPDATE(11). These four architectural patterns from Chapter 4 start many of the pattern sequences through the language.

> 本语言图有**四个主要入口点(顶级模式)。这些是减灾单元(1)、审计纠正(2)、最小化人工干预(5)和软件更新(11)**。这四个第 4 章的架构模式开启了语言中的许多模式序列。

The interconnections and flow of patterns beginning with UNITS OF MITIGATION (1) proceeds to REDUNDANCY (3) and to the active error processing patterns of ESCALATION (9) and QUARANTINE (28). These patterns form the basis for most of the patterns of error detection and error processing. This includes the recovery related patterns of RESTART (31), ROLLBACK(32), ROLL-FORWARD (33), and RETURN TO REFERENCE POINT (34) in addition to the patterns related to CHECKPOINTING (37). The SYSTEM MONITOR (15) and related patterns, HEARTBEAT (16), ACKNOWLEDGEMENTS (17), and WATCHDOG (18) are also reached through the starting point of UNITS OF MITIGATION. The error mitigation patterns found in Chapter 7 are reached through FAULT CORRELATION (12), which is one of the central patterns in the language and is reached from the UNITS OF MITIGATION starting point as well.

> 从缓解单元(1)开始的互连和模式流动，继而到冗余(3)，然后到升级(9)和隔离(28)的主动错误处理模式。这些模式构成了大多数错误检测和错误处理模式的基础。这还包括恢复相关的重启(31)、回滚(32)、滚动前进(33)和返回参考点(34)模式，以及与检查点(37)相关的模式。系统监视器(15)和相关模式，如心跳(16)、确认(17)和看门狗(18)也可以通过缓解单元的起点达到。第 7 章中发现的错误缓解模式可以通过故障相关(12)，这是语言中的一个中心模式，从缓解单元的起点达到。

CORRECTING AUDITS (2) starts the paths through the language that contain the data related patterns, such as CHECKSUM (25), ERROR CORRECTING CODES(57) and MARKED DATA (56). These patterns, and the others shown, provide the primary means to deal with faults in data or data storage.

> 正确审计(2)开启了包含数据相关模式的语言之路，如校验和(25)、纠错码(57)和标记数据(56)。这些模式以及其他显示的模式提供了处理数据或数据存储故障的主要方法。

MINIMIZE HUMAN INTERVENTION (5) starts the language paths related to information getting out of the system and to the people that are interested in the system’s operation. These include MAXIMIZE HUMAN PARTICIPATION (6), FAULT OBSERVER (10), the MINIMIZE MAINTENANCE INTERFACE (7), and the fault treatment pattern of REVISE PROCEDURE (63).

> 最小化人工干预(5)开始了与信息从系统出去，以及对系统运行感兴趣的人们相关的语言路径。这些包括最大化人类参与(6)，故障观察器(10)，最小化维护介面(7)和故障处理模式修改程序(63)。

The paths and flows that begin at SOFTWARE UPDATE (11) are also closely related to people. Many of the fault treatment (Chapter 8) patterns flow out of SOFTWARE UPDATE because they either assist in the process of updating the system’s software, or because they are related to the human processes that require or facilitate updating the system.

> 起始于软件更新(11)的路径和流程也与人有紧密的联系。许多故障处理(第 8 章)模式都源自软件更新，因为它们要么帮助更新系统的软件，要么与需要或促进更新系统的人类过程有关。

To make use of the patterns presented in this book you need to think about which ones will be most relevant and useful to the problem at hand. Most projects will not include all of these patterns. The next part of this chapter shows an example of selecting the patterns that are relevant and creating a design based upon them.

> 要利用本书中提出的模式，你**需要思考哪些模式对当前问题最相关和有用**。大多数项目不会包括所有这些模式。本章的下一部分展示了一个选择相关模式并基于它们创建设计的**示例**。

# _A Presence Server Example_

In this section an example system will be discussed, that of a Presence Server. The requirements and main functions of a Presence Server are introduced and then the section proceeds through the six step methodology to develop a fault tolerant Presence Server. At the appropriate stage of the method the patterns from the earlier chapters of this book will be assembled into a pattern language to design a fault tolerant system. There are many, many architecture and design issues involved with a system such as this. Only those directly related to fault tolerance and the patterns in this book will be mentioned.

> 在本节中，将讨论一个示例系统，即 Presence Server。介绍了 Presence Server 的要求和主要功能，然后本节通过六步方法来开发一个容错的 Presence Server。在方法的适当阶段，本书前面章节中的模式将被组装成一个模式语言来设计一个容错系统。这样的系统涉及到许多架构和设计问题。只有与容错和本书中的模式直接相关的问题才会提及。

A Presence Server collects, stores, and distributes information about an entity’s availability and willingness to communicate. A model for Presence Servers is described in RFC 2278 \[DRS00\]. This entity of interest is referred to as the _presentity_. The Presence Server receives notification events from the presentity’s agent, combines the events with other events related to the presentity, and makes their presence information available to interested watchers.

> 一个存在服务器收集、存储和分发有关实体可用性和愿意沟通的信息。 RFC 2278 \[DRS00\]描述了一个存在服务器的模型。这个感兴趣的实体被称为*presentity*。存在服务器从 presentity 的代理接收通知事件，将这些事件与与 presentity 相关的其他事件相结合，并将其存在信息提供给感兴趣的观察者。

Watchers are either _fetchers_ or _subscribers_. Fetchers actively poll the Presence Server for information about the presentities that they are interested in. Subscribers register their interest in advance and then the Presence Server publishes presence information to them.

> 监视者要么是抓取者，要么是订阅者。抓取者主动轮询存在服务器以获取有关他们感兴趣的存在者的信息。订阅者提前注册他们的兴趣，然后存在服务器向他们发布存在信息。

Presence information consists of _presence tuples_ that contain presence status, a communication address, and potentially other information related to the presentity. The communication address field consists of a communication means and an address. Updates to the presence information are received from the presentity’s user agents. The presence information is always available to fetchers. Changes to presence information are published by the Presence Server to the subscribers.

> 信息存在由*存在元组*组成，其中包含存在状态、通信地址以及与存在者相关的其他信息。通信地址字段由通信方式和地址组成。更新信息存在的来源是存在者的用户代理。信息存在总是可以被获取者访问。存在信息的变化由存在服务器发布给订阅者。

## Non-functional Requirements

The section above presents a general overview of the functions that a Presence Server must perform. Other requirements on the Presence Server define and constrain the non-functional requirements related to performance, reliability, and maintainability.

> 以上部分概述了 Presence 服务器必须执行的功能。其他关于性能、可靠性和可维护性的非功能性要求定义和限制了 Presence 服务器。

The Presence Server should be scalable to handle presence information for a large number of presentities. The requirements define how quickly presence information is made available to the watchers. The Presence Server should also be reliable, with as high availability as possible. For this discussion the actual performance and capacity requirement numbers are not needed.

> 服务器应该可扩展以处理大量存在信息。要求定义了观察者可以获取存在信息的速度。服务器也应该可靠，尽可能提供高可用性。在此讨论中，不需要实际的性能和容量要求数字。

Some commercial processors and operating systems require periodic reboots as preventive maintenance. Rebooting the Presence Server once per week seems like an acceptable alternative. If the reboot is done during a period of low activity, and if the data is saved over reboot, will that be sufficient to meet the requirements? Assume that the reboot takes one minute. One minute times 52 weeks equals 52 minutes per year. This is very close to 99.99%, or four nines, availability. In some usage scenarios four nines will be sufficient. For the purposes of this chapter, assume that this is acceptable. Higher than 99.99% availability will be needed if Presence Server will be used by a network provider as a service to many customers. They will have thousands and thousands of presentities that do not share a common one minute per week in which the server can be rebooted.

> 一些商业处理器和操作系统需要定期重启以进行预防性维护。每周重启一次 Presence Server 似乎是一个可接受的替代方案。如果重启是在活动量较低的时期进行的，并且如果数据被保存在重启之后，这样是否足以满足要求？假设重启需要一分钟。一分钟乘以 52 周等于 52 分钟每年。**这与 99.99％，或四个九，可用性非常接近。** 在某些使用场景中，四个九的可用性足够了。在本章的目的，假设这是可接受的。如果 Presence Server 将被网络提供商用作为服务提供给许多客户，则需要更高于 99.99％的可用性。他们将拥有成千上万的 presentities，它们不会共享一分钟的时间，在这一分钟内可以重新启动服务器。

The Presence Server should operate unattended without constant human oversight.

> 服务器应该可以在没有持续人工监督的情况下自动运行。

## Implementation Choices

For the purposes of this example, consider that the architects of the Presence Server have decided a few things. These will help shape the discussion of use of patterns later. The architects want to be able to add processors in a clustering arrangement to support growth and reliability. These processors will be active-active and load balancing. In the initial and smallest configuration there will be only two processors. Additional processors will be added as they are needed. <a href="#bm.htm#fig1.101" id="bm.htm#fig1.101a">Figure 101</a> shows a view of the hardware building blocks. Load balancing of incoming presence information is done by one of the two processors which shares the workload by passing some of the incoming information to the other processors for service.

> 为了本例的目的，考虑到 Presence Server 的建筑师已经做出了一些决定。这些将有助于形成后面关于模式使用的讨论。建筑师希望能够以群集排列的方式添加处理器，以支持增长和可靠性。这些处理器将是主动-主动的，并进行负载平衡。在最初和最小的配置中，只有两个处理器。随着需要，将添加其他处理器。<a href="#bm.htm#fig1.101" id="bm.htm#fig1.101a">图 101</a>显示了硬件构建块的视图。通过共享工作负载，其中一个处理器将传入的存在信息进行负载平衡，并将一些传入信息传递给其他处理器以提供服务。

**[Figure 101](#bm.htm#fig1.101a)** System building blocks

> **[图 101](#bm.htm#fig1.101a)** 系统构建模块

![](./OEBPS/images/250-1.jpg)

The presence information will be stored on disks local to the cluster. The overhead of a database management system outweighs the benefits of the system, so the Presence Server will not use an off the shelf database.

> **信息将存储在集群本地的磁盘上。** 数据库管理系统的开销超过了系统的好处，因此 Presence Server 不会使用现成的数据库。

# _Designing for Fault Tolerance_

In Chapter 2 a six step method for designing for fault tolerance was introduced. The main benefit of this method is that it provides a structure to employ the Fault Tolerant Mindset and examine the system’s potential failures and risks and to mitigate them through the application of patterns. The six steps are:

> 在第二章中，引入了一种设计容错的六步法。该方法的主要好处是它提供了一个结构，以采用容错的心态，检查系统的潜在故障和风险，并通过应用模式来减轻它们。六个步骤是：

**1.** Determine the things that can go wrong with the system.
**2.** Define the strategies needed to mitigate the risks
**3.** Identifying the primary system dividing points and modes of redundancy.
**4.** Make the architectural and major design decisions.
**5.** Design in the capabilities for the system to implement the risk mitigation strategies identified in step 2.
**6.** Designing human computer interactions and modes of management are important and must be done sensibly to ensure that failures won’t be initiated by the people who are trying to administer the system.

> **1.** 确定系统可能出现的问题。
> **2.** 定义需要缓解风险的策略
> **3.** 确定主要的系统划分点和冗余模式。
> **4.** 做出建筑和主要设计决定。
> **5.** 设计系统，以实施第 2 步中确定的风险缓解策略。
> **6.** 设计人机交互和管理模式是重要的，必须明智地处理，以确保不会由试图管理系统的人员发起失败。

## Step 1: Assess the Things that can go Wrong

The first step is to begin by determining what can go wrong. Define what is a failure for the presence server. Well written specifications will clearly identify the failures as situations to be avoided.

> 首先，要开始的第一步是确定可能出现的问题。定义服务器故障是什么。编写良好的规范将清楚地把故障定义为要避免的情况。

For the Presence Server there are three main failure types: incorrect information, untimely information, and Presence Server unavailability.

> 对于 Presence 服务器，有三种主要故障类型：
>
> - 信息不正确、
> - 信息不及时以及 Presence 服务器
> - 不可用。

Incorrect presence information failures: Incorrect, either incomplete or not current, presence information given to subscribers. Incorrect, either incomplete or not current, presence information made available to the fetchers. All presence information that arrives at the system should be processed, even though some of it will be invalid, for example data that has been superceded because the presentity’s state has changed.

> 不正确的存在信息失败：不正确，无论是不完整的还是不完整的，都提供给订户的存在信息。不正确，无论是不完整还是不正确，都提供给 fetchers 提供的存在信息。即使其中一些信息无效，也应处理到达系统的所有存在信息，例如，由于演示性的状态已更改，因此已被升级的数据。

Untimely presence information failures: Presence information is not available within the time window defined in the specifications.

> 不合时宜的存在信息失败：在规范中定义的时间窗口中，存在信息不可用。

Presence server unavailability failures: When the Presence Server is not able to receive presentity notifications, the Presence Server is unable to send presence information and the Presence Server is not able to process requests for information from the fetching watchers.

> 在场服务器无法可用性故障：当存在服务器无法接收礼拜通知时，在场服务器无法发送出现信息，并且在线服务器无法从获取观察者那里处理信息请求。

Once the failures are identified, what are the faults that can lead to them? <a href="#bm.htm#tab1" id="bm.htm#tab1a">Table 1</a> lists some of the possible faults for each of these potential failures.

> 一旦发现失败，可能导致它们的故障是什么？<a href="#bm.htm#tab1" id="bm.htm#tab1a">表 1</a>列出了每个潜在失败的一些可能故障。

[**Table 1**](#bm.htm#tab1a) Potential failures(潜在的失败)

<table class="bodytable">
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd" data-valign="top">
<td class="bodycell" style="border-bottom: 1px solid black; border-top: 1px solid black; background-color: black; color: white"><strong>FAILURE</strong></td>
<td class="bodycell" style="border-bottom: 1px solid black; border-top: 1px solid black; background-color: black; color: white"><strong>POSSIBLE FAULTS</strong></td>
</tr>
<tr class="even" data-valign="top">
<td class="bodycell" style="border-bottom: 1px solid black">Incorrect presence information</td>
<td class="bodycell" style="border-bottom: 1px solid black">Incorrect notification from presentity<br />

Presentity notification received incorrectly<br />

> 表示通知不正确地收到<br />
> Presentity update combined incorrectly with stored presence information<br />
> 表现更新与存储的存在信息<br />不正确地结合在一起
> Presence information saved incorrectly internally<br />
> 存在信息在内部保存错误<br />
> Presentity identification incorrect so misplaced data</td>
> 表现标识不正确，因此数据放错了数据</td>

</tr>
<tr class="odd" data-valign="top">
<td class="bodycell" style="border-bottom: 1px solid black">Untimely information</td>
<td class="bodycell" style="border-bottom: 1px solid black">Message buffered for too long<br />

Presentity updates coming at higher rate than the system can handle<br />

> 表现更新的速率比系统可以处理<br />更高
> Publication not occurring frequently enough<br />
> 出版物不够经常出现<br />
> Publication not happening<br />
> 出版物没有发生<br />
> Fetches ignored<br />
> 获取被忽略的<br />
> Fetches buffered for too long<br />
> 取得缓冲太长<br />
> Fetches coming at a higher rate than specified in requirements</td>
> 提取的速度比要求中指定的速度高</td>

</tr>
<tr class="even" data-valign="top">
<td class="bodycell" style="border-bottom: 1px solid black">Presence Server unavailability</td>
<td class="bodycell" style="border-bottom: 1px solid black">Presence server in an infinite loop<br />

Presence server network interfaces faulty<br />

> 存在服务器网络接口故障<br />
> Application failed to restart<br />
> 应用程序无法重新启动<br />
> Operating system fault keeps it from executing<br />
> 操作系统故障可防止执行<br />
> Presence Server application stopped</td>
> 存在服务器应用程序停止</td>

</tr>
</tbody>
</table>

## Step 2: Decide how to Mitigate the Risks

Step 2 is where the patterns in this book come in. Identify the patterns that help mitigate the failures described in the previous step. While you are getting started designing fault tolerant systems with the patterns in this book and other sources, explicitly noting the ones that are useful to the situation will be helpful, as shown in <a href="#bm.htm#tab2" id="bm.htm#tab2a">Table 2</a>. Diagramming them helps to understand and remember how they interrelate and build upon each other (Please see <a href="#bm.htm#fig1.102" id="bm.htm#fig1.102a">Figure 102</a>).

> 步骤 2 是本书中模式的地方。识别有助于缓解上一步中描述的失败的模式。在您开始使用本书中的模式和其他来源设计容错系统时，明确注明对该情况有用的模式将是有帮助的，如<a href="#bm.htm#tab2" id="bm.htm#tab2a">表 2</a>所示。对它们进行图表分析有助于理解和记住它们如何相互关联并相互建立(请参见<a href="#bm.htm#fig1.102" id="bm.htm#fig1.102a">图 102</a>)。

[**Table 2**](#bm.htm#tab2a) Presence Server pattern language(存在服务器模式语言)

![](./OEBPS/images/252-1.gif)

**[Figure 102](#bm.htm#fig1.102a)** Presence Server pattern language map(存在服务器模式语言图)

![](./OEBPS/images/254-1.jpg)

### _Applying the Language_

To apply the patterns in this book to the solution of the example problem, first build a working pattern language for the project. The language will contain those elements of the fault tolerant vocabulary presented here that will be useful in the design of the system. Patterns are not included if they will clearly not be needed or useful.

> 要将本书中的模式应用于示例问题的解决方案，首先为该项目构建一种工作模式语言。该语言将包含本文介绍的错误容错词汇中那些对系统设计有用的元素。如果模式明显不需要或不可用，则不包括模式。

[Table 2](#bm.htm#tab2) lists the patterns in our pattern language.

> 表 2(#bm.htm#tab2)列出了我们模式语言中的模式。

Why these patterns? These are the ones that will be the most useful in our system. The specification for the Presence Server indicates that it must be scalable in size and availability. This has resulted in REDUNDANCY (3) being added to the system. RECOVERY BLOCKS (4), a means of implementing software redundancy, is not added to the pattern language because the systems’ requirements are not stringent enough to warrant the extra work required to implement the recovery blocks. In order to support REDUNDANCY a system of HEARTBEATS (16) monitored by a SYSTEM MONITOR(15) will be used.

> 为什么这些模式？这些是在我们的**系统中最有用的**。Presence Server 的规范**表明它必须具有可伸缩的大小和可用性**。这导致系统中**添加了冗余(3)**。恢复块(4)，一种实现软件冗余的方法，没有添加到模式语言中，因为系统的要求不够严格，不需要实现恢复块所需的额外工作。**为了支持冗余，将使用由系统监视器(15)监视的心跳(16)系统。**

A number of patterns were eliminated because the Presence Server is only a four nines system. For example, an occasional reboot is okay, so the patterns that restart processing more quickly than a RESTART (31), such as ROLLBACK (32) and ROLL-FORWARD (33) are not included. Automatic correction of data like that provided by ERROR CORRECTING CODES(57) is similarly not needed and so is not included in our pattern language.

> **一些模式被淘汰，因为 Presence Server 只是一个四九系统。** 例如，**偶尔重启是可以的**，因此比 RESTART(31)更快地重新启动处理的模式，如 **ROLLBACK(32)和 ROLL-FORWARD(33)不包括在内。** 像错误纠正码(57)提供的**自动纠正数据也不需要**，因此不包括在我们的模式语言中。

CHECKPOINT (37) and related patterns also do not appear in our pattern language because of the nature of the presence related transactions. The notification events can be processed quickly. This means that they are short lived and CHECKPOINTS are most useful when the system has a considerable investment in completing long lived transactions.

> **检查点(37)和相关模式也不会**出现在我们的模式语言中，因为存在相关交易的性质。通知事件可以快速处理。这意味着**它们是短暂的**，而**检查点在系统投入大量资源完成长期交易时最有用**。

A number of the patterns listed above will appear in almost all fault tolerant project’s languages. Every system will need SOFTWARE UPDATE(11) capabilities. Almost all can make good use of a MAINTENANCE INTERFACE(7). Determining the UNITS OF MITIGATION(1) is a basic activity of the designer, so that pattern is included. The number of nines in the system’s availability goes down rapidly if every error requires a person to act upon it, so MINIMIZE HUMAN INTERVENTION(5) is included. It is also included because of the requirement for unattended operation.

> 许多上述列出的模式几乎都会出现在所有容错项目的语言中。每个系统都需要软件更新(11)功能。几乎所有系统都可以充分利用维护界面(7)。确定缓解单位(1)是设计师的基本活动，因此包括该模式。如果每个错误都需要人来处理，系统的可用性的九的数量会迅速下降，因此包括**最小化人工干预(5)**。也是因为无人值守操作的要求而包括它。

The choice of mitigation techniques is also guided by the overall availability need of the system. With a four nines or better goal, failure does not require that extra unused capabilities that can be activated as EXPANSIVE AUTOMATIC CONTROLS(47) be added to the system. Since the requirement of the system is to present presence information in a timely and correct fashion, all requests are important. The load shedding patterns are not included. QUEUE FOR RESOURCES(46) is added to the language because we anticipate the need to queue presence information during periods of overload to handle it when there is time. FRESH WORK BEFORE STALE(55) is in the language because by adding arrival time information to the presence information stored, the system will have the ability to discard some presentity updates if more recent ones have already been processed.

> 选择缓解技术的方式也受系统的整体可用性需求的指导。对于达到四个 9 或更高的目标，失败不需要添加额外的未使用的功能，作为扩展自动控制(47)。由于系统的要求是及时准确地提供存在信息，所有的请求都是重要的。负载削减模式不包括在内。为了预计在负载过载期间需要对存在信息进行排队处理，添加了资源队列(46)到语言中。新工作在旧工作之前(55)被包含在语言中，因为通过将到达时间信息添加到存储的存在信息中，系统将具有丢弃一些存在更新的能力，如果已经处理了更新的信息。

Since the system will not use a database to store the presence information, CORRECTING AUDITS (2) will be used to keep the data correct. CHECKSUM (25) will be used for detection by CORRECTING AUDITS and also to detect errors in messages. MARKED DATA (56) will be used in conjunction with DATA RESET (41) to process errors in the data.

> 由于**系统不使用数据库来存储存在信息，因此将使用校正审计(2)来保持数据的正确性**。校验和(25)将用于校正审计检测，并用于检测消息中的错误。**标记数据(56)将与数据重置(41)一起用于处理数据中的错误。**

You want the system to get better over time, so you will fix problems as they are detected and also correct deficiencies in the system. This plan introduces SOFTWARE UPDATE (11), REPRODUCIBLE ERROR (60), REINTEGRATION (59) and ROOT CAUSE ANALYSIS (62) into the project pattern language.

> 你希望系统能够随着时间的推移而得到改善，因此你将会在发现问题时修复它们，并纠正系统中的不足。这个计划将软件更新(11)、可重现错误(60)、重新整合(59)和根本原因分析(62)引入项目模式语言中。

Putting all these patterns together and drawing the language and relationship between these patterns results in [Figure 102](#bm.htm#fig1.102).

> 将所有这些模式放在一起，绘制这些模式之间的语言和关系，结果如[图 102](#bm.htm#fig1.102)所示。

## Step 3: Identifying Redundancy

Redundancy is a basic property of fault tolerant systems. In this step the redundancy of the system is assessed by comparing the architecture elements such as the chosen processor architecture and the system specification with the availability requirements.

> **冗余是容错系统的基本特性。** 在这一步中，通过比较所选的处理器体系结构和系统规范与可用性要求来评估系统的冗余性。

The UNITS OF MITIGATION (1) and the boundaries needed for REDUNDANCY (3) are led by the system requirements. A system with four nines availability requirements does not need high levels of redundancy, in either the hardware or the software. However it will be built in a cluster that can grow. In the case of the Presence Server, the system should be designed to support the migration of key functions from one processor to another as the system size and scope increases. Single processors will be the basic unit of hardware and system redundancy.

> 单元缓解(1)和为冗余(3)所需的边界由系统要求领导。具有**四个九号可用性要求的系统不需要在硬件或软件上高度冗余。** 但是它将被构建成一个可以扩展的集群。在 Presence Server 的情况下，系统应该被设计为支持在系统规模和范围增加时，**将关键功能从一个处理器迁移到另一个处理器。单处理器将是硬件和系统冗余的基本单元。**

> [!note]
> 可用性以 9999 来衡量，这下终于是找到指标了

Depending on the type of disk and its inherent failure rate redundant disks, and the volume of presence information expected, a disk redundancy method such as RAID-1 or RAID-2 should be used to mitigate the disk error rates.

> 根据磁盘类型及其固有的失效率、冗余磁盘以及预期的存在信息量，应该**使用 RAID-1 或 RAID-2 等磁盘冗余方法来减轻磁盘错误率**。

> [!NOTE]
> 这里还给出了对于磁盘的安全的要求
> 对应的应该是内存纠错吧

The ability to monitor the active Presence Server processors is needed. A FAULT OBSERVER (10) interface to an external monitor is one option. Since the system includes multiple processors they should watch each other through heartbeating mechanisms such as HEARTBEAT (16).

> 需要监控活动的 Presence Server 处理器的能力。将外部监视器连接到一个**故障观察器(10)接口**是一种选择。由于系统包括多个处理器，它们应该**通过心跳机制(如心跳(16))彼此监视**。

## Step 4: Architectural Design Decisions

During this step the aspects of the system that have impact across the whole system will be added. This is done by deciding how the architectural patterns in our language will be implemented.

> 在这一步中，会添加对整个系统有影响的系统方面。这是通过决定我们语言中的架构模式如何实现来完成的。

The previous steps have identified the basic UNITS OF MITIGATION (1) and REDUNDANCY (3). The system specification states that the system should not require active human intervention, so MINIMIZE HUMAN INTERVENTION (5) will be used. A FAULT OBSERVER (10) interface is needed to report the status to monitoring systems. This is a capability that might not be needed in the initial release, but will be required when the system grows to more processors eventually.

> **上一步已经确定了基本的减灾单元(1)和冗余(3)。** 系统规范指出，系统不应该要求主动的人工干预，因此将使用最小化人工干预(5)。**需要一个故障观察者(10)接口来向监控系统报告状态。** 这可能不是初始版本所需要的功能，但是**当系统最终增加到更多处理器时将是必需的**。

> [!NOTE]
> 所以我们这个系统现在就是必须的

Load sharing will be accomplished by having all the network traffic delivered to the two lowest numbered processors in the system. Number refers to whatever identification system is used for the cluster members. The processor with the lowest number is always the master that receives the presence tuples and fetcher requests and distributes them evenly across all the processors in the cluster. A HEARTBEAT (16) is established between these two processors. If the lowest numbered processor should fail and stop heartbeating then the next lowest numbered processor will assume the responsibility for load distribution to the active processors in the cluster. After the lowest number has recovered, it will resume heartbeats with the other processor and again assume the load distribution responsibility.

> **负载分担将通过将所有网络流量传送到系统中两个编号最低的处理器来实现。** 编号指的是用于群集成员的任何标识系统。编号最低的处理器始终是主处理器，它接收存在元组和抓取器请求并将它们均匀地分布到群集中的所有处理器。在**这两个处理器之间建立一个心跳(16)**。如果**编号最低的处理器失败并停止心跳，则编号次低的处理器将承担负责向活动处理器分发负载的责任。编号最低的处理器恢复后，它将与另一个处理器重新建立心跳，并再次承担负载分配责任。**

> [!NOTE]
> 这个不就是我们目前的需求嘛！
> 可以将这段话抄过来

If there are enough processors in the cluster then the task of publishing presence information to subscribers will be assigned to a pair of processors that aren’t doing the incoming load balancing, e.g. the third and fourth processors in the cluster. These two processors will watch each other (via a HEARTBEAT (16)) to ensure that one of them is always active and publishing presence information to the subscribers.

> **如果集群中有足够的处理器，那么将将任务分配给不执行传入负载平衡的一对处理器，例如集群中的第三和第四个处理器。这两个处理器将互相监视(通过心跳(16))，以确保其中一个始终处于活动状态，并向订阅者发布存在信息。**

HEARTBEATS (16) will be instituted between the two processors with the lowest numbers and all the other processors in the cluster. This will enable the two processors that are balancing the load to maintain a list of active processors to which work can be distributed.

> 在集群中，**两个数字最小的处理器之间将建立心跳(16)，其他所有处理器也将加入其中。这将使得平衡负载的这两个处理器能够保持一个活动处理器的列表，以便可以将工作分发给它们。**

> [!NOTE]
> 不是很明白这句话

All of the system’s HEARTBEATS (16) will be subject to REALISTIC THRESHOLDS (19). RIDING OVER TRANSIENTS (26) will be used to provide appropriate system response to short duration processor problems.

> 所有系统的**心跳(16)将受到现实的阈值(19)的约束**。跨越瞬变(26)将用于提供适当的系统响应以应对短暂的处理器问题。

All presence information arriving at the system will be given a timestamp and QUEUED FOR RESOURCES (46) and processed within a FRESH WORK BEFORE STALE (55) Last In First Out queue. If a presence tuple with a later timestamp has already been processed then the earlier one can be discarded without being processed. This ensures that both the recent change in status and the old requests are processed eventually, and will maximize the correctness of the presence information.

> 所有到达系统的存在**信息都将被赋予时间戳，并被排队等待资源(46)**，并在新工作之前进行旧工作(55)的先进先出队列中处理。如果已经处理了具有较新时间戳的存在元组，则可以丢弃较早的存在元组而不必处理。这可以确保最终处理最近的状态变化和旧请求，并最大限度地提高存在信息的正确性。

CORRECTING AUDITS (2) are used to ensure that data is correctly stored. Some example audits include: Verification that queue pointers are correct and there are no isolated elements in the queues. Verification that the presence tuple data stored on disk is correctly organized. All arriving presence information should be verified with CHECKSUMS (25) to determine if it was received correctly.

> 检查审计(2)用于确保数据正确存储。一些示例审计包括：验证队列指针是否正确，队列中是否有孤立元素。验证存储在磁盘上的存在元组数据是否正确组织。所有到达的存在信息都应使用 CHECKSUMS(25)进行验证，以确定其是否正确接收。

The ability to correct faults and add new capabilities is always required so the provisions for SOFTWARE UPDATE (11) are included at this point.

> 能够纠正错误并增加新功能总是必需的，因此在此处包括了软件更新(11)的规定。

## Step 5: Risk Mitigation Capabilities

Step 5 is concerned with the strategies needed to mitigate the risks mentioned in the earlier sections. The list of risks discussed in the previous section is shown with the patterns that can be used to mitigate them in <a href="#bm.htm#tab3" id="bm.htm#tab3a">Table 3</a>. This step serves as a check to see if the risks and failure causes identified in Step 1 have been mitigated.

> 步骤 5 涉及到需要用来**减轻前面部分提到的风险的策略**。前一节中讨论的风险列表在<a href="#bm.htm#tab3" id="bm.htm#tab3a">表 3</a>中显示了可用于减轻它们的模式。此步骤作为检查，以查看步骤 1 中确定的风险和故障原因是否已经得到缓解。

[**Table 3**](#bm.htm#tab3a) Risk mitigations

```
    **RISK** **PATTERNS TO MITIGATE RISK**
    Incorrect notification from presentity CHECKSUM (25)
    Presentity notification received incorrectly CHECKSUM (25), FRESH WORK BEFORE STALE (55)
    Presentity update combined incorrectly with stored presence information CHECKSUM (25), CORRECTING AUDITS (2)
    Presence information saved incorrectly internally CHECKSUM (25), CORRECTING AUDITS (2)
    Presentity identification incorrect so misplaced data CHECKSUM (25), CORRECTING AUDITS (2)
    Message buffered for too long FRESH WORK BEFORE STALE (55)
    Presentity updates coming at higher rate than specified in requirements QUEUE FOR RESOURCES (46), FRESH WORK BEFORE STALE (55)
    Publication not occurring frequently enough FRESH WORK BEFORE STALE (55), SYSTEM MONITOR (15)
    Publication not happening ACKNOWLEDGEMENT (17), HEARTBEAT (16), SYSTEM MONITOR (15)
    Fetches ignored ACKNOWLEDGEMENT (17), SYSTEM MONITOR (15)
    Fetches buffered for too long FRESH WORK BEFORE STALE (55), SYSTEM MONITOR (15)
    Fetches coming at a higher rate than specified in requirements QUEUE FOR RESOURCES (46), FRESH WORK BEFORE STALE (55)
    Presence server in an infinite loop ACKNOWLEDGEMENT (17), SYSTEM MONITOR (15)
    Presence server network interfaces faulty ACKNOWLEDGEMENT (18), CHECKSUM (25), HEARTBEAT (16), FAULT OBSERVER (10)
    Application failed to restart SYSTEM MONITOR (15), HEARTBEAT (16), FAULT OBSERVER (10)
    Operating system fault keeps it from executing HEARTBEAT (16), SYSTEM MONITOR (15), FAULT OBSERVER (10)
    Presence server application stopped HEARTBEAT (16), SYSTEM MONITOR (16), FAULT OBSERVER (10)
    ---

    > 来自表现校验和的通知不正确(25)
    > 表示通知不正确地收到了校验和校验之前的新作品(55)
    > 表现更新与存储的存在信息校验和校正审核(2)混合不正确地结合在一起
    > 存在信息保存错误的内部校验和校正审核(2)
    > 表达式识别不正确，因此数据校验和校正审核(2)
    > 消息缓冲在陈旧之前的新鲜工作太长时间(55)
    > 表达式更新的速度比要求队列的资源队列(46)，陈旧之前的新作品(55)更高的速度更新(46)
    > 出版物在陈旧之前不经常进行新鲜工作(55)，系统监视器(15)
    > 出版物没有发生确认(17)，心跳(16)，系统监视器(15)
    > 获取忽略的确认(17)，系统监视器(15)
    > 在陈旧之前(55)，系统监视器(15)之前的新鲜工作太长时间了(15)
    > 提取的速度比要求队列的资源队列(46)，陈旧之前的新作品(55)提取的速度高(46)
    > 无限循环确认(17)中的存在服务器，系统监视器(15)
    > 存在服务器网络接口错误的确认(18)，校验和心跳(16)，故障观察者(10)
    > 应用程序无法重新启动系统监视器(15)，心跳(16)，故障观察者(10)
    > 操作系统故障避免执行心跳(16)，系统监视器(15)，故障观察者(10)
    > 存在服务器应用程序停止心跳(16)，系统监视器(16)，故障观察者(10)
```

## Step 6: Human Computer Interactions

In this last step the style and means of human interaction with the system is defined. The Presence Server will have primarily a maintenance interaction with humans, which can effectively be implemented through a simple web form interface style.

> 在最后一步，定义了**人类与系统交互的方式和手段**。Presence Server 主要与人类进行维护交互，可以通过简单的 Web 表单界面风格有效地实现。

# _Software Structure_

<a href="#bm.htm#fig1.103" id="bm.htm#fig1.103a">Figure 103</a> shows a possible block diagram of the major software components in the system. Note that the application that writes to the presence information store is a gray box that has had little done to it to support the system’s reliability.

> <a href="#bm.htm#fig1.103" id="bm.htm#fig1.103a">图 103 </a>显示了系统中主要软件组件的可能框图。请注意，写在《存在信息商店》上的应用程序是一个灰色框，它几乎没有为支持系统的可靠性而做。

**[Figure 103](#bm.htm#fig1.103a)** Presence Server Software Architecture

![](./OEBPS/images/257-1.jpg)

> [!NOTE]
> 这个图很好，我应该提供的也是这样一个状态流程图？一个处理策略

This design includes several primary components with responsibility for other parts. These components were identified partly for clarity of the example in this chapter. Their functions follow the recommendations offered within the patterns. When the system is actually being implemented further combination of the functions is possible. For examples, the Maintenance Interface and the Fault Observer can be combined, as can the System Monitor and the Overload Monitor.

> 这个设计包括几个主要组件，负责其他部分。这些组件部分是为了清晰地说明本章的示例而识别出来的。它们的功能遵循模式提出的建议。当系统实际实施时，进一步组合功能是可能的。例如，维护接口和故障观察器可以组合在一起，系统监视器和负载监视器也可以组合在一起。

While the design is being implemented its reliability and availability should be assessed through testing and reliability engineering.

> 在实施设计时，应通过测试和可靠性工程来评估其可靠性和可用性。
