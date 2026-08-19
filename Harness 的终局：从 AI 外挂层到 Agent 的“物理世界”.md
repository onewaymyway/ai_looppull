# Harness 的终局：从 AI 外挂层到 Agent 的“物理世界”

如果把今天的 Agent 系统拆开来看，大致可以看到这样一个结构：

> **大模型负责思考，Harness 负责让它行动。**

模型提供推理、理解和生成能力，Harness 则负责工具调用、上下文管理、记忆、任务循环、权限控制、文件系统以及各种外部能力。

因此，在今天的 Agent 体系中，Harness 很容易被理解成一种“外挂层”：

```text
用户
 ↓
Agent
 ↓
LLM
 ↑
Harness
 ↓
Tools / Memory / Context / Environment
```

于是，一个自然的问题出现了：

> **随着大模型越来越强，未来的 Harness 会不会越来越轻，最终只是模型外面的一层薄薄的胶水？**

我认为恰恰相反。

如果我们接受两个前提：

1. **未来的 Agent 必然会越来越自主，能够长期运行，而不是一次性完成任务；**
2. **未来的 Agent 必然会具备某种程度的自我学习、自我修改和自我进化能力；**

那么 Harness 的发展方向，很可能不是从“重”走向“轻”，而是从今天的 **外挂层**，逐渐演化成 **Agent Runtime**，最终成为一种真正意义上的 **Agent Operating Environment**。

甚至可以更激进地说：

> **Harness 的终局，也许不是 Framework，而是 Agent 的“物理世界”。**

---

# 一、今天的 Harness，为什么看起来像“外挂”？

当前的 Agent 大多仍然遵循一个比较简单的模式：

```text
用户提出任务
      ↓
Agent 思考
      ↓
调用工具
      ↓
观察结果
      ↓
继续思考
      ↓
完成任务
      ↓
结束
```

在这个模型里，Agent 是一次性的。

例如一个 Coding Agent：

```text
用户：
帮我修复这个 Bug

        ↓

Agent
        ↓
读取代码
        ↓
修改代码
        ↓
运行测试
        ↓
测试通过
        ↓
返回结果
```

任务完成以后，Agent 的生命周期基本就结束了。

因此，此时 Harness 最重要的作用就是：

* 给模型提供工具；
* 管理上下文；
* 执行 Agent Loop；
* 管理文件；
* 管理 Shell；
* 管理权限；
* 提供一些 Memory；
* 处理错误和重试。

所以我们完全可以把它理解成：

> **LLM 的执行外挂。**

在这个阶段，轻量化反而是一种优势。

因为模型本身越来越强，Harness 最好不要干涉模型太多。

---

# 二、真正的变化来自“自主 Agent”

但未来的 Agent 很可能不会一直停留在“一次任务，一次运行”的模式。

更合理的形态可能是：

```text
                    环境
                     ↓
                 Observation
                     ↓
              ┌──────────────┐
              │    Agent     │
              │              │
              │ Reasoning    │
              │ Planning     │
              │ Memory       │
              │ Learning     │
              └──────┬───────┘
                     ↓
                   Action
                     ↓
                    环境
                     ↑
                     │
                    循环
```

它不再只是：

> “帮我完成一个任务。”

而开始变成：

> **“我要长期存在于一个环境中，并不断追求某些目标。”**

这两个问题看起来只差了一点，但实际上意味着整个 Agent 架构会发生巨大变化。

---

# 三、长期运行的 Agent，需要什么？

假设一个 Agent 不是运行 10 分钟，而是运行一年。

它需要面对的问题就完全不同了。

它需要知道：

### 我是谁？

```text
Identity
```

### 我正在做什么？

```text
Current Goals
Tasks
Plans
```

### 我过去做过什么？

```text
Episodic Memory
Experience
History
```

### 我学到了什么？

```text
Knowledge
Skills
Patterns
```

### 我应该怎么做？

```text
Policies
Strategies
Workflows
```

### 我现在处于什么环境？

```text
Environment State
Resources
Other Agents
External Systems
```

### 如果我失败了怎么办？

```text
Retry
Recovery
Rollback
Alternative Strategy
```

### 如果我发现自己的方法不好怎么办？

```text
Reflection
Experiment
Self Modification
Learning
```

于是我们会发现：

> **一个长期自主运行的 Agent，需要的已经不是简单的 Tool Calling，而是一整套运行时系统。**

---

# 四、自我进化才是改变 Harness 地位的真正力量

我认为这里是整个问题最核心的地方。

普通 Agent 的结构是：

```text
Harness
   ↓
Agent
```

Harness 控制 Agent。

但如果 Agent 开始具备自我进化能力，结构会变成：

```text
                 Agent
                   ↓
              发现问题
                   ↓
              修改自己
                   ↓
              运行实验
                   ↓
              评价结果
                   ↓
              保留改进
```

这时候，一个非常重要的问题出现了：

> **谁允许 Agent 修改自己？**

假设一个 Coding Agent 发现：

> “我最近处理大型项目时，经常陷入无效循环。”

它可能采取这样的行动：

```text
修改 Prompt
     ↓
修改 Planning 策略
     ↓
增加一个新的 Skill
     ↓
修改工具选择策略
     ↓
修改 Memory 结构
     ↓
重新运行测试
     ↓
发现性能提升
     ↓
正式采用
```

这时候 Harness 已经不再只是：

> “帮 Agent 调用工具。”

它实际上开始负责：

> **管理 Agent 如何改变自己。**

这是 Harness 从“外挂”走向“Runtime”的关键一步。

---

# 五、未来 Harness 最重要的能力，可能不是 Tool Calling

过去我们讨论 Agent Framework，最喜欢比较：

* Tool Calling
* ReAct
* Planning
* Memory
* Multi-Agent
* Workflow

但如果 Agent 真正进入长期自主运行阶段，Harness 的核心能力可能发生变化。

未来最重要的问题可能变成：

> **Agent 可以改变什么？**

例如：

```text
Prompt
Skill
Memory
Workflow
Tool
Policy
Planning Strategy
Agent Architecture
```

然后：

> **谁批准它改变？**

可能是：

```text
Agent 自己
Supervisor Agent
Evaluator
Human
Policy Engine
```

然后：

> **怎么证明这个改变是好的？**

需要：

```text
Sandbox
Simulation
Benchmark
Regression Test
A/B Test
Canary
```

最后：

> **如果改变失败怎么办？**

需要：

```text
Versioning
Rollback
Recovery
```

所以未来 Harness 很可能会出现一个今天并不明显的核心能力：

# Change Management

也就是：

> **管理 Agent 的自我变化。**

---

# 六、Harness 会从 Runtime 进一步变成 Evolution Engine

如果把这个过程继续推演，就会出现一个非常有意思的闭环：

```text
        环境
         ↓
     Observation
         ↓
       Agent
         ↓
       Action
         ↓
       Outcome
         ↓
     Evaluation
         ↓
      Reflection
         ↓
  Self Modification
         ↓
     Experiment
         ↓
     Validation
         ↓
     New Agent
         │
         └──────────────→ 环境
```

这实际上已经不是普通的 Agent Loop 了。

它更像：

> **一个人工智能的进化循环。**

Agent 不只是执行程序。

它开始：

* 积累经验；
* 发现问题；
* 修改策略；
* 修改技能；
* 修改工具；
* 进行实验；
* 验证结果；
* 保留成功的变化；
* 淘汰失败的变化。

那么 Harness 所承担的角色就发生了根本变化。

它不再只是：

> **Execution Engine**

而开始成为：

> **Evolution Engine**

---

# 七、这意味着一个非常重要的变化：Agent 不再等于 Model

今天我们很容易把：

```text
Agent ≈ LLM + Prompt
```

但未来可能越来越不是这样。

一个真正长期存在的 Agent，可能由下面这些东西共同构成：

```text
Agent
│
├── Model
├── Identity
├── Memory
├── Goals
├── Skills
├── Policies
├── Experience
├── Environment
├── Runtime
└── Evolution History
```

其中 Model 甚至可能只是一个可替换组件。

今天：

```text
Model A
```

明天：

```text
Model B
```

后天：

```text
Model C
```

但是：

```text
Identity
Memory
Experience
Skills
Goals
Evolution History
```

仍然保持连续。

那么我们仍然会认为：

> **这是同一个 Agent。**

这会产生一个非常重要的结论：

> **未来 Agent 的“本体”，可能不再是 Model，而是它的持续性。**

---

# 八、这可能是 AI 系统最容易被忽略的一个方向

今天 AI 行业非常关注：

> 谁的模型更聪明？

未来可能还会出现另一个问题：

> **谁的 Agent 能够连续存在，并且在长期运行之后变得越来越强？**

假设两个 Agent：

### Agent A

初始能力：

```text
95
```

一年之后：

```text
95
```

### Agent B

初始能力：

```text
85
```

但是它每天：

```text
积累经验
↓
发现错误
↓
优化 Skill
↓
改进 Workflow
↓
更新 Memory
↓
测试新策略
↓
保留有效变化
```

一年之后：

```text
130
```

那么决定 Agent 长期能力的，就不再只是 Foundation Model。

而是：

> **它有没有一个优秀的学习与进化环境。**

而这个环境，很可能就是未来 Harness 的核心。

---

# 九、所以“重型还是轻量”其实不是最准确的问题

真正的问题应该是：

> **Harness 到底是在“控制 Agent”，还是在“承载 Agent”？**

如果 Harness 只是：

```text
控制 Agent
```

那么它当然应该尽量轻。

但如果 Harness 需要：

```text
承载 Agent
```

那么它就必须负责：

```text
Process
State
Memory
Scheduling
Persistence
Security
Sandbox
Resources
Events
Evaluation
Versioning
Rollback
Evolution
```

这已经不可能只是一个轻量外挂。

因此，我更倾向于认为：

> **未来 Harness 会变重，但不是变成一个“大而全的 Agent Framework”，而是变成一个底层越来越重、上层越来越简单的 Agent Runtime。**

---

# 十、未来可能出现“底层极重，上层极轻”

这其实和操作系统的发展非常类似。

我们今天写一个程序：

```python
run()
```

看起来非常简单。

但底层操作系统却需要处理：

```text
Process
Memory
Filesystem
Scheduling
Networking
Security
Drivers
Isolation
```

Agent Runtime 很可能也会经历类似的发展。

未来一个 Agent 开发者可能只需要：

```python
agent.run(goal)
```

但下面实际上运行着：

```text
┌────────────────────────────────────┐
│              Agent                │
├────────────────────────────────────┤
│ Identity                          │
│ Goals                             │
│ Memory                            │
│ Skills                            │
│ Planning                          │
├────────────────────────────────────┤
│        Agent Runtime              │
│                                    │
│ Scheduler                          │
│ State Manager                      │
│ Event System                       │
│ Tool Runtime                       │
│ Sandbox                            │
│ Permission                         │
│ Resource Manager                   │
│ Persistence                        │
│ Observability                      │
│ Evaluation                         │
│ Versioning                         │
│ Rollback                           │
│ Evolution Engine                   │
└────────────────────────────────────┘
```

所以：

> **开发者看到的是轻量 Agent API，底层却是一套非常重的 Runtime。**

这可能是未来 Harness 最合理的形态。

---

# 十一、为什么我认为“重型 Framework”反而未必是终局？

这里需要区分两个概念：

### 重型 Framework

通常意味着：

```text
大量抽象
大量强制规范
大量开发范式
大量 Orchestration
```

这种东西未必会长期存在。

因为模型越来越强以后，很多原本需要 Framework 写死的逻辑，可以直接交给 Agent 自己完成。

例如今天：

```text
Framework：
先调用 Planner
↓
再调用 Executor
↓
再调用 Critic
```

未来可能直接变成：

```text
Agent：
我判断现在应该怎么做。
```

模型能力越强，越不需要大量人为规定“智能应该如何运行”。

---

# 十二、但有一些东西，模型再强也替代不了

例如：

> Agent 的进程被杀掉以后怎么办？

> Agent 的状态怎么恢复？

> 两个 Agent 如何共享资源？

> 一个 Agent 修改自己的代码后怎么回滚？

> Agent 如何获得权限？

> Agent 如何被隔离？

> Agent 如何管理自己的计算预算？

> 一个运行三年的 Agent 如何保存和检索海量经验？

> Agent 如何证明一次自我修改没有破坏原有能力？

这些问题不是单纯的“智能问题”。

它们是：

> **运行世界的问题。**

因此，它们最终一定会沉淀到 Runtime。

这也是为什么我认为：

> **未来不会是 Harness 消失，而是 Harness 从 Framework 逐渐向 Runtime 演化。**

---

# 十三、如果把这个逻辑推到极致，Harness 会是什么？

这里可以进入一个更激进的推演。

假设未来 Agent 可以：

```text
自主行动
自主学习
自主修改
自主复制
自主协作
自主竞争
自主优化
```

那么 Harness 需要决定：

```text
它能看到什么？
它能做什么？
它能改变什么？
它可以使用多少资源？
它如何学习？
它如何验证自己？
它如何复制？
它如何恢复？
它如何与其他 Agent 竞争？
```

这时候 Harness 已经不只是软件基础设施。

它实际上开始定义：

> **Agent 所处世界的基本规则。**

---

# 十四、这就是“Agent 的物理世界”

可以把传统计算机系统类比成：

```text
物理世界
    ↓
操作系统
    ↓
应用程序
```

而未来可能出现：

```text
人类世界
    ↓
Agent Environment
    ↓
Agent
```

那么 Environment + Runtime 所定义的东西，就类似于 Agent 世界里的“物理规律”。

例如：

```text
资源守恒
权限边界
行动成本
时间
记忆
因果反馈
失败
恢复
复制
竞争
协作
学习
进化
```

这些规则共同决定：

> **Agent 能够成为什么样的存在。**

因此，如果把这个概念继续向前推进：

> **AgentOS 的终局可能不是“AI 的操作系统”，而是一套人工智能可以长期存在、行动、学习和进化的人工物理环境。**

---

# 十五、从这个角度重新理解“Harness”

所以，我更愿意把 Harness 的演化理解成下面这条路径：

```text
Harness
   ↓
Agent Executor
   ↓
Agent Runtime
   ↓
Agent Operating System
   ↓
Agent Evolution Engine
   ↓
Agent Environment
   ↓
Artificial Physics
```

它不是简单地“越来越重”。

而是：

> **责任边界不断向下扩张。**

最开始，它只负责：

> “怎么让模型调用工具？”

后来，它负责：

> “怎么让 Agent 长期运行？”

再后来，它负责：

> “怎么让 Agent 自己改变？”

最终，它负责：

> **“什么样的变化可以发生，以及这些变化如何成为 Agent 的一部分？”**

---

# 十六、未来真正重要的可能是“进化闭环”

如果一定要找未来 Agent 基础设施最核心的东西，我认为不是：

* Prompt
* Tool Calling
* Workflow
* Multi-Agent

而是下面这个闭环：

```text
       Goal
        ↓
   Observation
        ↓
      Action
        ↓
     Outcome
        ↓
    Evaluation
        ↓
    Reflection
        ↓
    Modification
        ↓
    Experiment
        ↓
    Validation
        ↓
     Learning
        ↓
      New State
        ↓
      Action
        ↺
```

这个循环一旦真正成立：

> Agent 就不再只是一个“程序”。

它开始具有某种意义上的：

> **持续存在性。**

而 Harness，就是这个持续存在性的基础。

---

# 十七、这也会改变未来 Agent 开发者的角色

今天的 Agent 开发者主要在做：

```text
设计 Prompt
设计 Workflow
接 Tool
写代码
调模型
```

未来可能逐渐变成：

```text
设计 Goal
设计 Environment
设计 Memory
设计 Feedback
设计 Evaluation
设计 Evolution Rules
设计 Safety Boundary
```

换句话说：

> **未来真正高级的 Agent 工程师，可能不是在“写 Agent”，而是在设计 Agent 的生存环境。**

这和传统软件工程会出现很大的区别。

传统程序：

> 程序员定义程序如何运行。

未来 Agent：

> 程序员定义 Agent 可以如何生存和进化。

---

# 十八、因此，我对未来 Harness 的最终判断

如果一定要在：

> **重型基础设施**

和

> **轻量外挂层**

之间选择一个答案：

## 我的答案是：重型基础设施。

但这个答案需要加上三个限定。

### 第一，它不会表现为“大框架”

而会表现为：

> **底层重 Runtime，上层轻 API。**

---

### 第二，它的价值不会主要是“让 Agent 更聪明”

而会是：

> **让 Agent 能够长期、安全、可靠地自主运行。**

---

### 第三，它最终最核心的能力不是执行，而是进化

未来真正优秀的 Harness，应该能够回答：

```text
Agent 如何存在？
Agent 如何行动？
Agent 如何记忆？
Agent 如何失败？
Agent 如何恢复？
Agent 如何学习？
Agent 如何修改自己？
Agent 如何验证自己？
Agent 如何保留成功的变化？
Agent 如何避免错误的变化？
Agent 如何长期保持身份连续性？
```

如果这些问题都被统一起来，那么我们面对的已经不再是今天意义上的 Harness。

而是：

> **Agent Runtime。**

再往前一步：

> **AgentOS。**

再往前一步：

> **Agent 的人工物理世界。**

---

# 结语：Harness 可能才是 Agent 革命真正被低估的部分

过去几年，AI 行业的注意力几乎全部集中在 Model 上。

我们不断讨论：

```text
参数量
Benchmark
Reasoning
Context
Multimodal
Inference
Training
```

但如果 Agent 真正进入长期自主运行时代，竞争的核心可能会逐渐发生转移。

因为一个真正长期存在的智能体，不能只有一个聪明的大脑。

它还需要：

```text
身体
记忆
环境
行动能力
资源
边界
经验
反馈
学习机制
进化机制
```

而这些东西，恰恰构成了 Harness 的未来。

所以，Harness 的真正终局可能不是：

> **“如何把 LLM 包起来？”**

而是：

> **“如何让一个智能体能够在一个人工世界中持续存在？”**

当这个问题成为 Agent 系统的核心问题之后，Harness 就不再是模型外面的一层薄薄的胶水。

它会变成 Agent 的：

> **Runtime、身体、记忆载体、生存系统，以及进化环境。**

最终，我们甚至可能不再问：

> “这个 Agent 使用什么模型？”

而会开始问：

> **“这个 Agent 在什么世界里生存？它如何学习？它如何进化？它最终会变成什么？”**

如果这一天真的到来，那么今天我们称之为 **Harness** 的东西，很可能就是未来 **AgentOS 的雏形**。

而真正值得思考的问题，也就从：

> **“如何构建一个更好的 Agent？”**

变成了：

> **“如何构建一个能够自己变得越来越好的世界？”**
