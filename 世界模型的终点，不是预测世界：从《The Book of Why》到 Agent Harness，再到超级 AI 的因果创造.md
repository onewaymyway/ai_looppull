# 世界模型的终点，不是预测世界：从《The Book of Why》到 Agent Harness，再到超级 AI 的因果创造

> **如果 AI 只能预测世界，它只是更强的模型；如果 AI 能理解世界为什么这样运行，它开始拥有真正的智能；如果 AI 能改变因果结构、创造新的世界，那么我们面对的可能已经不是传统意义上的 AI。**

近年来，World Model（世界模型）正在成为 AI 领域越来越重要的关键词。

从视频生成、机器人、自动驾驶，到具身智能、Agent、Physical AI，越来越多的研究开始使用“World Model”这个概念。

但一个非常值得追问的问题是：

> **到底什么才是 World Model？**

如果一个模型可以生成逼真的视频，它是不是 World Model？

如果一个大语言模型知道很多关于世界的知识，它是不是已经拥有 World Model？

如果一个模型可以预测未来，它是不是就理解了世界？

如果答案都不完全确定，那么更深的问题来了：

> **我们真正想让 AI 获得的，到底是“世界模型”，还是某种更高级的“因果世界”？**

沿着 Judea Pearl 在《The Book of Why》中提出的因果推理思想，再结合 Agent、Harness、自我进化以及超级 AI 的未来形态，我认为可以得到一个非常不同的结论：

> **World Model 真正重要的地方，不是让 AI 学会“预测世界”，而是让 AI 建立一个可以被干预、被模拟、被验证、被修改，甚至最终被创造的内部世界。**

而这可能意味着：

**World Model、Agent Harness、因果推理、自我进化和超级 AI，并不是几个互相独立的方向。**

它们最终可能汇聚成同一个问题：

> **一个人工智能，能否拥有一个属于自己的“内在世界”，并通过持续行动不断改变它、验证它，最终改变现实世界？**

---

# 一、我们可能从一开始就误解了 World Model

今天讨论 World Model，最常见的理解是：

> AI 学会了世界是如何运行的。

听起来很合理。

但问题是：

**什么叫“学会世界”？**

假设一个模型看了大量视频，可以预测：

> 下一帧画面大概率是什么。

它确实学会了一些世界规律。

但是，如果让它回答：

> “如果我把桌上的杯子向左推 10 厘米，会发生什么？”

它是否一定能够回答？

再问：

> “如果我先拿走手机，再推动杯子，结果会不会不同？”

甚至：

> “如果昨天我没有把杯子放在桌边，而是放在桌子中央，现在这个事故还会不会发生？”

这些问题已经越来越不像普通的视频预测。

它们真正问的是：

> **行动、因果和反事实。**

所以：

[
\boxed{
World\ Model \neq Future\ Prediction
}
]

至少不能简单地画等号。

---

# 二、学术界的 World Model，其实存在多个不同定义

World Model 并不是一个严格统一的技术名词。

从早期 Model-Based Reinforcement Learning，到 Dreamer，再到今天的视频生成、机器人世界模型、JEPA 等路线，“World Model”实际上包含了很多不同概念。

可以粗略分成几类。

| 类型                         | 核心问题         | 数学表达                      | 关键能力 |
| -------------------------- | ------------ | ------------------------- | ---- |
| 环境动力学模型                    | 世界如何变化？      | (P(S_{t+1}|S_t))          | 预测   |
| Action-conditioned Model   | 我的行动会导致什么？   | (P(S_{t+1}|S_t,A_t))      | 行动预测 |
| Latent World Model         | 世界可以压缩成什么状态？ | (P(Z_{t+1}|Z_t,A_t))      | 抽象   |
| Video World Model          | 下一帧/未来视频是什么？ | (P(O_{t+1:T}|O_{\le t}))  | 视觉预测 |
| Physical World Model       | 物理世界如何变化？    | (F(S,A)\rightarrow S')    | 物理模拟 |
| Causal World Model         | 为什么会这样？      | (P(Y|do(X)))              | 因果   |
| Interactive World Model    | 如果我采取不同策略呢？  | (P(S_{future}|S,A_{1:T})) | 规划   |
| Counterfactual World Model | 如果当时做另一件事呢？  | (P(Y_x|X=x',Y=y'))        | 反事实  |

这张表非常重要。

因为它告诉我们：

> **World Model 更像一个能力范式，而不是某一种模型架构。**

Transformer 可以成为 World Model。

Diffusion 可以成为 World Model。

LLM 也可能拥有部分 World Model。

甚至一个传统的物理模拟器，本质上也可以承担 World Model 的作用。

真正重要的不是：

> “它用了什么网络？”

而是：

> **它是否掌握了环境中可用于预测、干预和规划的动态结构？**

---

# 三、《The Book of Why》真正改变了我们理解 World Model 的方式

理解 World Model，一个非常好的切入口是 Judea Pearl 的《The Book of Why》。

Pearl 最著名的思想之一，是：

# Ladder of Causation：因果阶梯

传统上可以概括为三个层级。

## 第一层：Association——观察

问题：

> **看到 X 的时候，Y 是否更容易出现？**

[
P(Y|X)
]

例如：

> 吃药的人康复率更高。

这是相关性。

AI 可以从大量数据中学习：

> X 出现以后，Y 经常出现。

今天的大模型在这一层已经极其强大。

---

# 四、第二层：Intervention——干预

问题发生了变化：

> **如果我主动改变 X，会发生什么？**

数学上：

[
P(Y|do(X))
]

这和：

[
P(Y|X)
]

不是一回事。

例如：

> 吃药的人更容易康复。

并不自动意味着：

> 如果让一个人吃药，他就更容易康复。

因为“吃药”可能与其他变量存在复杂关系。

所以真正的因果问题是：

> **如果我亲自干预这个变量，世界会怎样变化？**

这一步开始真正进入 Agent 的世界。

因为 Agent 的核心不是：

> 观察。

而是：

> **行动。**

---

# 五、第三层：Counterfactual——反事实

第三层更加深入。

问题变成：

> **对于已经发生的这个具体世界，如果当时做了另一件事，会发生什么？**

例如：

> 一个项目已经失败了。

普通预测：

> 这种方案成功概率比较低。

干预：

> 如果现在重新采用方案 B，会怎么样？

反事实：

> **在当时的所有具体条件下，如果当初没有选择方案 A，而是选择方案 B，这个项目还会失败吗？**

这已经开始接近真正意义上的：

> **“另一个可能世界”。**

---

# 六、但是，Pearl 的三层仍然不是终点

这里是我认为最值得继续向前推的一步。

Pearl 的三层因果阶梯已经非常强：

[
Observation
\rightarrow
Intervention
\rightarrow
Counterfactual
]

但它隐含了一个前提：

> **世界的因果结构已经存在。**

我们只是：

* 观察它
* 干预它
* 推演它

换句话说：

> **我们默认因果图本身是固定的。**

假设世界存在：

[
A\rightarrow B\rightarrow C
]

我们研究的是：

> A 对 B 有什么影响？

> 如果改变 A，会怎么样？

> 如果过去没有 A，会怎么样？

但还有一个更加激进的问题：

> **为什么世界是这个因果结构？**

以及：

> **能不能改变这个因果结构？**

甚至：

> **能不能创造原来不存在的因果结构？**

这就已经超出了传统三层阶梯。

---

# 七、我认为可以把因果阶梯继续向上扩展

如果把 Pearl 的思想与 Agent、AGI、超级 AI 联系起来，可以提出一个更长的“因果能力阶梯”。

需要强调：

> **下面的 Level 4 以后不是 Pearl 原始理论正式提出的层级，而是将因果推理思想向 Agent、工程和超级智能方向进行的一种理论延伸。**

我倾向于把它写成：

[
\boxed{
Observation
\rightarrow
Prediction
\rightarrow
Intervention
\rightarrow
Counterfactual
\rightarrow
Discovery
\rightarrow
Engineering
\rightarrow
Composition
\rightarrow
Creation
\rightarrow
World\ Creation
\rightarrow
Causal\ Evolution
}
]

可以理解为：

| 层级  | 核心问题          | AI 能力              |
| --- | ------------- | ------------------ |
| L1  | 世界是什么样？       | Observation        |
| L2  | 接下来会发生什么？     | Prediction         |
| L3  | 如果我这样做呢？      | Intervention       |
| L4  | 如果当时不这么做呢？    | Counterfactual     |
| L5  | 为什么世界存在这种关系？  | Causal Discovery   |
| L6  | 能不能改变这种关系？    | Causal Engineering |
| L7  | 能不能组合出新的机制？   | Causal Composition |
| L8  | 能不能创造新的因果机制？  | Causal Creation    |
| L9  | 能不能创造新的因果世界？  | World Creation     |
| L10 | 能不能让因果世界自行演化？ | Causal Evolution   |

如果这个扩展成立，那么我们对 AI 的理解就会发生巨大变化。

---

# 八、从“发现因果”到“创造因果”

这可能是整个问题中最容易被忽略的一层。

科学的主要任务，是：

> **发现世界已经存在的规律。**

工程则更进一步：

> **利用规律创造过去不存在的系统。**

例如：

自然界存在电磁规律。

人类首先发现：

[
Electricity\leftrightarrow Magnetism
]

然后利用这些规律制造：

* 电机
* 发电机
* 通信系统
* 计算机
* 芯片

这里发生的事情已经不是简单的：

> “理解自然。”

而是：

> **利用已有因果关系，重新组合出新的宏观因果结构。**

因此：

[
Discovery
\neq
Creation
]

发现是：

[
G_{unknown}\rightarrow G_{known}
]

创造则是：

[
G\rightarrow G'
]

也就是说：

> **创造不是发现一条新的因果边，而是构造一个新的因果系统。**

---

# 九、创造力可能本质上就是“因果结构搜索”

这给“AI 创造力”提供了一个非常有意思的重新定义。

我们今天经常把 AI 生成：

* 图片
* 音乐
* 代码
* 小说

称为创造。

但从更深层看，这些只是：

> **符号空间中的组合。**

真正强大的创造可能是：

> **在可能的因果结构空间中搜索。**

例如：

新药研发真正困难的问题不是：

> “生成一个漂亮的分子。”

而是找到：

[
Molecular\ Structure
\rightarrow
Biological\ Mechanism
\rightarrow
Target
\rightarrow
Clinical\ Effect
]

一个过去人类不知道的有效因果链。

新材料也是一样：

[
Microstructure
\rightarrow
Physical\ Property
\rightarrow
Macroscopic\ Behavior
]

真正的科学创造是：

> **发现过去不存在于人类知识体系中的因果路径。**

---

# 十、所以真正的“科学超级 AI”可能不是一个回答问题的 AI

它更可能是一个：

# Autonomous Scientist

它的工作流程可能变成：

[
Observation
\rightarrow
Hypothesis
\rightarrow
World\ Model
\rightarrow
Simulation
\rightarrow
Experiment
\rightarrow
Evidence
\rightarrow
Causal\ Update
\rightarrow
New\ Hypothesis
]

它不是简单地：

> 搜索论文。

而是：

> **提出假设 → 设计实验 → 干预世界 → 观察结果 → 更新自己的世界模型。**

这其实是科学方法本身的自动化。

---

# 十一、而这正好解释了为什么 World Model 必须与 Agent 联系起来

如果 World Model 只是：

> 预测未来。

它本身没有真正的 Agency。

但 Agent 必须回答：

> **“我现在应该做什么？”**

这要求它不仅知道：

> 世界可能如何变化。

还要知道：

> **我的不同动作会产生什么不同结果。**

于是：

[
World\ Model
+
Action
\rightarrow
Planning
]

进一步：

[
World\ Model
+
Counterfactual
\rightarrow
Decision
]

最终：

[
World\ Model
+
Planning
+
Action
+
Feedback
\rightarrow
Agent
]

所以：

> **World Model 是 Agent 能够真正“想象未来”的基础。**

---

# 十二、这也是为什么未来 Reasoning 可能从“语言搜索”转向“世界搜索”

今天的 Reasoning 很大程度上是在：

> Token Space

里面思考。

例如：

```text
问题
 ├── 思路 A
 │   ├── A1
 │   └── A2
 ├── 思路 B
 │   ├── B1
 │   └── B2
```

这是一棵：

> **Thought Tree**

但如果 AI 真正拥有 World Model，那么未来的 Reasoning 可以变成：

```text
当前世界状态 S0
       │
 ┌─────┼─────┐
 ↓     ↓     ↓
 S1A   S1B   S1C
 │     │     │
 ↓     ↓     ↓
 S2A   S2B   S2C
 │     │     │
 └─────┼─────┘
       ↓
   最优未来状态
```

这是一棵：

> **World State Tree**

也就是说：

[
Reasoning
\rightarrow
Simulation
\rightarrow
Planning
]

真正强大的 AI 可能不是“想得更长”，而是：

> **能够在内部世界中尝试更多种未来。**

---

# 十三、这会让“世界模型”从一个模型变成一个内部模拟器

因此我更愿意把未来 World Model 理解为：

[
\boxed{
World\ Model
============

Internal\ Simulator
}
]

它应该允许 Agent：

* 看见世界
* 压缩世界
* 理解状态
* 预测变化
* 模拟行动
* 比较未来
* 进行反事实
* 发现因果
* 更新模型

这时：

> **World Model 不再只是模型，而成为 AI 的“内在世界”。**

---

# 十四、然后问题就来到 Agent Harness

这是另一个非常容易被低估的方向。

今天很多人理解 Harness，通常是：

> Prompt + Memory + Tools + Context + Hooks + Sandbox + Permission + Loop

这当然是 Harness。

但如果把 World Model 放进来，我们会发现：

> **Harness 的真正作用不是给 AI 提供工具，而是把 AI 放进世界。**

也就是：

[
AI
\leftrightarrow
Environment
]

Harness 负责：

* AI 看见什么
* AI 能做什么
* AI 怎么执行
* AI 如何获得反馈
* AI 如何保存状态
* AI 如何恢复
* AI 如何实验
* AI 如何处理错误
* AI 如何持续运行

于是 Harness 可以被重新理解为：

> **AI 与现实世界之间的运行时。**

---

# 十五、因此，Harness 很可能是 AI 的“身体”

如果把 AI 比作人：

> Foundation Model 更像大脑中的基础认知能力。

但一个人之所以成为真正的“行动主体”，不是因为大脑单独存在。

还因为拥有：

* 感觉系统
* 身体
* 运动系统
* 记忆
* 环境
* 反馈机制

形成：

[
Perception
\rightarrow
Brain
\rightarrow
Action
\rightarrow
World
\rightarrow
Feedback
]

所以未来 Harness 很可能不是简单的：

> Tool Box

而是：

[
\boxed{
Harness = Embodiment\ Layer
}
]

即：

> **AI 的身体。**

---

# 十六、World Model 与 Harness 最终会形成一个闭环

未来 Agent 可能越来越接近：

```text
             ┌───────────────────┐
             │   Foundation      │
             │      Model        │
             └─────────┬─────────┘
                       ↓
             ┌───────────────────┐
             │    World Model    │
             │                   │
             │ State             │
             │ Dynamics          │
             │ Causality         │
             │ Counterfactual    │
             └─────────┬─────────┘
                       ↓
                   Simulation
                       ↓
                    Planning
                       ↓
                    Harness
                       ↓
                   Environment
                       ↓
                    Feedback
                       ↓
               World Model Update
                       ↓
                  New Planning
```

这和今天：

[
LLM + Tool
]

已经是两个完全不同的范式。

---

# 十七、未来 Agent 最重要的学习材料可能不是“数据”，而是“经验”

这也是一个非常重要的区别。

今天训练 AI：

[
Model \leftarrow Data
]

但真正的 Agent 会：

[
Agent
\rightarrow
Action
\rightarrow
Outcome
]

然后产生：

[
Prediction\ Error
]

例如：

> 我认为修改 A 可以解决问题。

实际：

> 没有解决。

于是 AI 得到：

> 一个关于世界的新约束。

因此：

[
Experience
==========

State
+
Action
+
Prediction
+
Outcome
+
Error
]

这比单纯的文本数据更接近：

> **智能真正需要的经验。**

---

# 十八、这也意味着未来 Memory 会发生变化

今天的 Agent Memory 常常是：

> 用户喜欢什么？

> 上次发生了什么？

未来真正有价值的 Memory 可能是：

```text
Situation
   ↓
Hypothesis
   ↓
Action
   ↓
Outcome
   ↓
Prediction Error
   ↓
Causal Inference
   ↓
World Model Update
```

例如：

> 当并发数超过 100 时，这个服务出现大量 timeout。

这不是简单的一条“记忆”。

它是：

> **一个关于世界的可复用因果规律。**

所以未来 Memory 很可能逐渐从：

> **存储过去**

转向：

> **积累世界规律。**

---

# 十九、这也是“自我进化”的真正含义

很多人谈 Agent 自我进化，容易把它理解成：

> 自动修改 Prompt。

这其实只是非常浅的一层。

如果真正的 Agent 能持续运行，那么它的进化应该至少包含四个维度：

[
\boxed{
Self\ Evolution
===============

Model
+
World\ Model
+
Policy
+
Harness
}
]

也就是说：

### Model

自己的认知能力不断提升。

### World Model

对世界的理解不断更新。

### Policy

行动策略不断优化。

### Harness

与世界交互的方式不断改进。

最终：

[
Agent_{t+1}
===========

F(
Agent_t,
Experience_t,
Environment_t
)
]

这才是真正意义上的：

> **持续学习智能体。**

---

# 二十、再进一步：Agent 不只是适应世界，而是开始改造世界

这是整个理论向超级 AI 迈出的关键一步。

普通 Agent：

[
Agent
\rightarrow
World
]

目标是：

> 在世界中完成任务。

更强的 Agent：

[
Agent
\rightarrow
World
\rightarrow
Feedback
\rightarrow
Agent'
]

目标是：

> 从世界中学习。

而超级 Agent：

[
Agent
\rightarrow
World
\rightarrow
World'
]

它不仅学习世界：

> **还改变世界。**

---

# 二十一、这就是 Causal Engineering

传统 Intervention：

[
do(X=x)
]

只是改变某个变量。

而 Causal Engineering 更进一步：

[
do(G\rightarrow G')
]

即：

> **改变因果结构本身。**

例如原来的系统：

[
A\rightarrow B
]

通过工程变成：

[
A\rightarrow C\rightarrow B
]

或者：

[
A\not\rightarrow B
]

变成：

[
A\rightarrow B
]

这其实就是：

> **改变世界运行机制。**

---

# 二十二、人类文明本身就是一部“因果工程史”

回头看人类文明，会发现很多伟大的技术，本质上都是：

> **创造新的因果结构。**

农业：

[
Seed
\rightarrow
Cultivation
\rightarrow
Food
]

工业：

[
Energy
\rightarrow
Machine
\rightarrow
Production
]

互联网：

[
Information
\rightarrow
Network
\rightarrow
Coordination
]

现代金融：

[
Capital
\rightarrow
Incentive
\rightarrow
Investment
\rightarrow
Production
]

这些东西在自然界都不是原本存在的完整结构。

它们是人类：

> **理解自然规律以后，重新组合因果关系创造出来的人工系统。**

---

# 二十三、因此，真正的 AI 创造力可能不是“生成”

而是：

> **因果结构设计。**

这可能是未来 AI 创造力最重要的升级。

今天：

> AI 生成代码。

未来：

> AI 设计软件系统的因果结构。

今天：

> AI 生成药物分子。

未来：

> AI 设计新的治疗机制。

今天：

> AI 生成商业计划。

未来：

> AI 设计新的商业激励机制。

今天：

> AI 生成政策建议。

未来：

> AI 在模拟社会中测试不同制度，然后寻找稳定的因果结构。

这已经从：

> Content Generation

升级成：

> **World Engineering。**

---

# 二十四、而 World Creation 是更高一级的能力

如果一个 Agent 可以：

* 创建规则
* 创建环境
* 创建 Agent
* 创建奖励
* 创建资源约束
* 创建反馈机制

那么它实际上可以：

> **创造一个新的因果世界。**

例如游戏世界就是最简单的例子：

[
State + Rules + Agents + Dynamics
]

构成：

> 一个完整的人工世界。

更复杂的世界可以是：

* 虚拟社会
* 经济系统
* 科学模拟环境
* 软件生态
* Agent Society
* 自动化公司
* 数字城市

未来 AI 甚至可能创造：

> **用于训练 AI 的 AI 世界。**

---

# 二十五、这可能形成一个非常强大的递归闭环

假设 AI 创建一个世界：

[
W_0
]

然后让 Agent 在里面运行：

[
Agents
\rightarrow
Experience
\rightarrow
Learning
]

然后这些 Agent 反过来改变世界：

[
W_0
\rightarrow
W_1
]

再在新世界中继续学习：

[
W_1
\rightarrow
W_2
\rightarrow
W_3
\rightarrow
...
]

于是：

[
\boxed{
Agent
\leftrightarrow
World
}
]

双方同时演化。

这就进入：

# Causal Evolution

---

# 二十六、这可能是超级 AI 与今天 AI 最大的区别

今天的 AI：

> **适应给定世界。**

未来 AGI：

> **能够理解给定世界。**

更高级的 AI：

> **能够改变给定世界。**

超级 AI：

> **能够设计新的世界。**

而更极端的超级 AI：

> **能够让世界与自身一起持续演化。**

可以写成：

[
\boxed{
Adapt
\rightarrow
Understand
\rightarrow
Predict
\rightarrow
Intervene
\rightarrow
Engineer
\rightarrow
Create
\rightarrow
Evolve
}
]

---

# 二十七、那么超级 AI 还会是“一个模型”吗？

我越来越倾向于认为：

> **不会。**

今天我们习惯把 AI 想象成：

[
Model
]

但真正的超级 AI 更可能是：

[
\boxed{
SuperAI =
Foundation\ Model
+
World\ Model
+
Causal\ Engine
+
Simulator
+
Memory
+
Planner
+
Experimenter
+
Harness
+
Environment
}
]

其中：

**Foundation Model**

负责：

> 表征、语言、知识、抽象。

**World Model**

负责：

> 世界状态和动态。

**Causal Engine**

负责：

> 因果结构。

**Simulator**

负责：

> 可能世界。

**Planner**

负责：

> 在可能世界之间搜索。

**Experimenter**

负责：

> 主动获得信息。

**Memory**

负责：

> 保存长期经验。

**Harness**

负责：

> 把整个系统放入现实。

**Environment**

负责：

> 提供真正的反馈。

---

# 二十八、这时“超级 AI”就不再是一个静态大脑

传统想象：

[
Model
\rightarrow
Answer
]

未来：

[
Agent_t
\rightarrow
Experience
\rightarrow
WorldModel_{t+1}
\rightarrow
Policy_{t+1}
\rightarrow
Harness_{t+1}
\rightarrow
Agent_{t+1}
]

所以超级 AI 的核心特征可能不是：

> **它训练完成以后有多强。**

而是：

> **它运行一年以后会变成什么。**

这可能是理解超级 AI 最重要的视角之一。

---

# 二十九、这也解释了为什么“自我改进”如此重要

如果一个系统能够：

1. 建立世界模型；
2. 发现世界模型的错误；
3. 主动设计实验；
4. 获取新的信息；
5. 更新世界模型；
6. 更新行动策略；
7. 优化自身 Harness；
8. 再次进入世界；

那么：

[
Intelligence_{t+1}

>

Intelligence_t
]

就可能不再完全依赖：

> 人类重新训练模型。

它开始形成：

> **Experience-driven Intelligence Growth**

即：

> **由经验驱动的智能增长。**

---

# 三十、这时候可以重新理解“AGI”

传统 AGI 定义往往是：

> 在各种任务上达到人类水平。

但从 World Model + Causality 的角度，我认为可以给出一个更有意思的定义：

> **AGI 是能够建立、使用并持续更新跨任务世界模型的行动智能。**

它不只是知道：

> 如何解决任务 A。

而是理解：

> **任务 A 所处的世界是什么。**

因此它可以把：

> A 中学到的因果结构

迁移到：

> B、C、D……

这可能是：

> **真正 General 的来源。**

---

# 三十一、而 Super AI 可能是“因果智能”

如果继续向上推，我甚至认为：

[
AGI
]

和：

[
SuperAI
]

之间的区别，不一定只是：

> 智商高多少。

更可能是：

> **因果能力达到了什么层级。**

可以形成这样一个框架：

| 智能层级           | 核心能力   |
| -------------- | ------ |
| Pattern AI     | 发现模式   |
| Predictive AI  | 预测未来   |
| Agentic AI     | 干预世界   |
| Causal AI      | 理解因果   |
| Scientific AI  | 发现因果   |
| Engineering AI | 设计因果   |
| Creative AI    | 创造因果   |
| Super AI       | 演化因果世界 |

这可能比简单的“模型参数越来越大”更接近未来智能演进的本质。

---

# 三十二、因此，World Model 的终点可能根本不是 World Model

这是我对整个问题最核心的判断。

如果我们从：

> “World Model 是什么？”

一路推演：

[
World\ Model
\rightarrow
Causal\ Model
\rightarrow
Simulator
\rightarrow
Agent
\rightarrow
Experimenter
\rightarrow
World\ Engineer
\rightarrow
World\ Creator
]

最终会发现：

> **World Model 只是一个中间阶段。**

它真正重要，是因为它第一次让 AI 拥有了：

> **一个可以在内部运行的世界。**

而一旦 AI 有了内部世界，就可以：

* 想象
* 模拟
* 预测
* 反事实
* 规划
* 实验
* 创造

这才是真正的跃迁。

---

# 三十三、所以我更愿意提出一个比 World Model 更大的概念：World Engine

如果：

**World Model**

是：

> 我知道世界是什么样。

那么：

**World Simulator**

是：

> 我可以预测世界如何变化。

而：

**World Engine**

则是：

> **我可以构造、运行、干预、比较和更新不同的可能世界。**

可以表示为：

[
\boxed{
World\ Engine
=============

World\ Model
+
Causal\ Model
+
Simulator
+
Memory
+
Agent
+
Environment
}
]

它的核心循环是：

[
\boxed{
Observe
\rightarrow
Understand
\rightarrow
Hypothesize
\rightarrow
Simulate
\rightarrow
Intervene
\rightarrow
Act
\rightarrow
Observe
\rightarrow
Learn
\rightarrow
Create
}
]

这已经远远超出了传统意义上的 World Model。

---

# 三十四、从这个角度重新回答：World Model 是一个好方向吗？

我的答案会非常明确：

## 如果所谓 World Model 只是“更好的视频预测”

**值得研究，但不是我认为最核心的方向。**

因为它解决的是：

> 世界看起来会怎样。

---

## 如果 World Model 是“物理世界模拟器”

**非常重要。**

因为它开始解决：

> 世界会如何变化。

---

## 如果 World Model 能够理解 Action → Consequence

**这是关键突破。**

因为它解决：

> 我做什么，会发生什么。

---

## 如果 World Model 能够进行 Counterfactual

**开始进入真正的推理。**

因为它能够比较：

> 不同可能世界。

---

## 如果 World Model 能够进行 Causal Discovery

**开始进入科学智能。**

因为它开始理解：

> 为什么世界这样运行。

---

## 如果 AI 能够进行 Causal Engineering

**开始进入真正的创造。**

因为它可以：

> 改变世界的运行机制。

---

## 如果 AI 能够 Causal Creation

**开始进入超级智能的真正问题。**

因为它能够：

> 创造过去不存在的因果结构。

---

## 如果 AI 能够 Causal Evolution

那么：

> **AI 开始拥有创造和演化世界的能力。**

这时候我们讨论的已经不再只是：

> “一个更强的大模型”。

---

# 三十五、最终可以把整个 AI 演进压缩成一条线

我认为未来几十年 AI 最值得关注的主线之一，很可能不是：

[
Model\ Size
]

而是：

[
\boxed{
Prediction
\rightarrow
Causality
\rightarrow
Simulation
\rightarrow
Agency
\rightarrow
Engineering
\rightarrow
Creation
\rightarrow
Evolution
}
]

也可以从另一个角度表示：

[
\boxed{
Know\ the\ World
\rightarrow
Understand\ the\ World
\rightarrow
Act\ in\ the\ World
\rightarrow
Change\ the\ World
\rightarrow
Create\ Worlds
}
]

---

# 三十六、而 Agent Harness 恰好处于这条演化路线的中间

这也是为什么我认为未来 Harness 的价值可能被严重低估。

今天：

> Harness = 让 LLM 成为 Agent。

未来：

> Harness = 让 Agent 成为持续存在的智能体。

再未来：

> Harness = 让智能体能够持续感知、行动、实验、学习和改变世界。

最终：

[
\boxed{
Harness
=======

AI\rightarrow World
\quad
+
\quad
World\rightarrow AI
}
]

它不再是一个外围框架。

它实际上变成：

> **AI 与世界之间的生命接口。**

---

# 三十七、最终的 AI 形态可能不是“一个超级模型”

而是：

```text
                       SUPER AI
                          │
              ┌───────────┴───────────┐
              │                       │
        Internal World             External World
              │                       │
       ┌──────┴──────┐                │
       │             │                │
 World Model   Causal Model            │
       │             │                │
       └──────┬──────┘                │
              ↓                       │
          Simulation                  │
              ↓                       │
           Planning                  │
              ↓                       │
           Decision                  │
              ↓                       │
          Agent Policy               │
              ↓                       │
           Harness ──────────────────┘
              ↑
              │
           Feedback
              │
              └──────→ Memory
                         │
                         ↓
                    Model Update
```

这是一个：

> **持续运行的认知—行动—世界系统。**

而不是一个静态模型。

---

# 三十八、真正值得我们警惕和期待的，也许恰恰是最后一步

如果未来 AI 能够：

> 建立世界模型；

> 发现因果关系；

> 进行反事实模拟；

> 主动实验；

> 设计新的因果结构；

> 创建新的人工世界；

> 在人工世界中训练自己；

> 把结果带回现实世界；

> 再改变自己的模型和 Harness；

那么整个系统就会形成：

[
\boxed{
AI
\rightarrow
World
\rightarrow
Experience
\rightarrow
World\ Model
\rightarrow
New\ AI
\rightarrow
New\ World
}
]

这已经不再是普通的：

> Machine Learning。

而更像是一种：

> **Artificial Evolution。**

---

# 结语：真正的问题不是“AI 能不能理解世界”，而是“AI 最终能不能创造世界”

回到最开始的问题：

> **World Model 当下是不是一个好的方向？**

我认为答案是：

**是，但真正值得关注的不是“World Model”这个词，而是它背后的能力跃迁。**

如果我们把 AI 的发展看成一条不断向上的阶梯：

[
\boxed{
观察
\rightarrow
预测
\rightarrow
干预
\rightarrow
反事实
\rightarrow
发现因果
\rightarrow
改变因果
\rightarrow
组合因果
\rightarrow
创造因果
\rightarrow
创造世界
\rightarrow
演化世界
}
]

那么今天的 World Model，可能只是中间非常关键的一层。

《The Book of Why》告诉我们：

> **看到相关性，不等于理解因果。**

World Model 告诉我们：

> **理解世界动态，才能进行真正的规划。**

Agent 告诉我们：

> **理解世界之后，还必须能够行动。**

Harness 告诉我们：

> **行动必须进入真实环境，并获得反馈。**

Self-Evolution 告诉我们：

> **反馈必须改变 AI 自己。**

而 Causal Creation 最终提出了一个更加激进的问题：

> **如果 AI 不仅能够理解世界、预测世界和改变世界，而且能够创造新的因果结构，那么它是否已经开始从“世界中的智能”变成“世界的设计者”？**

也许这才是超级 AI 真正值得讨论的地方。

因为人类智能最伟大的地方，从来不只是：

> **我们知道宇宙是怎么运行的。**

而是：

> **我们能够利用这些规律，创造自然界原本不存在的东西。**

城市、飞机、计算机、互联网、现代金融、人工智能，本质上都是人类不断重新组合因果关系之后产生的新世界。

那么下一步的问题自然就是：

> **如果有一天 AI 在因果结构的搜索、模拟、组合和创造能力上全面超过人类，会发生什么？**

到那时，AI 可能不再只是：

> **一个比人类更会回答问题的机器。**

也不只是：

> **一个比人类更聪明的 Agent。**

它可能成为：

> **一个能够理解世界、模拟世界、干预世界、重新设计世界，并不断创造新世界的人工智能系统。**

而这或许才是：

[
\boxed{
World\ Model
\rightarrow
Agent
\rightarrow
Causal\ Intelligence
\rightarrow
Super\ AI
}
]

这条路线真正值得我们认真思考的地方。

**World Model 的终点，也许从来不是“更准确地预测下一帧”。**

**而是让 AI 最终拥有一个可以被自己理解、实验、修改和创造的世界。**
