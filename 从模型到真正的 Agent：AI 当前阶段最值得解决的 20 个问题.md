# 从模型到真正的 Agent：AI 当前阶段最值得解决的 20 个问题

## 引言：模型已经越来越聪明，为什么真正的 Agent 仍然没有到来？

过去几年，人工智能的发展有一条非常清晰的主线：

> **让模型变得越来越聪明。**

从早期的语言模型，到大规模多模态模型，再到具备推理、工具调用和代码执行能力的新一代模型，AI 已经开始从“回答问题”走向“完成任务”。

尤其到了 2026 年，一个明显的变化正在发生：

**模型本身越来越不像最明显的瓶颈了。**

今天的模型已经可以：

* 阅读大量代码；
* 修改复杂项目；
* 调用搜索、浏览器和终端；
* 使用外部工具；
* 分解复杂任务；
* 连续执行几十甚至上百步；
* 在一定程度上进行自我检查和错误恢复；
* 在一些专业任务中表现出接近甚至超过普通人类专家的能力。

与此同时，一个反直觉的现象也越来越明显：

> **模型越来越强，不等于 Agent 已经足够可靠。**

我们仍然经常遇到这样的场景：

> AI 明明“知道怎么做”，但就是没有把事情做好。

它可能：

* 记错之前的要求；
* 选错工具；
* 在错误的方向上连续执行；
* 上下文越来越长之后逐渐失去重点；
* 修改了正确的代码，却破坏了另一个模块；
* 遇到异常后不知道如何恢复；
* 做出了看起来合理、实际上错误的决定；
* 明明任务已经完成，却不知道什么时候应该停止；
* 明明应该询问用户，却自作主张；
* 明明可以继续工作，却因为一次失败直接退出。

这说明：

> **从“模型”到“真正的 Agent”，中间仍然存在一整层巨大的系统工程。**

甚至可以把今天的 Agent 简化成：

```text
Agent
=
Model
+
Context
+
Memory
+
Skills
+
Tools
+
Execution
+
Verification
+
State
+
Permissions
+
Runtime
+
Environment
```

因此，未来几年真正值得关注的问题，可能已经不再是：

> “模型还能再大多少？”

而是：

> **“我们究竟还缺什么，才能让一个 AI 真正成为一个能够长期、可靠、自主完成工作的 Agent？”**

下面，我尝试提出当前阶段最值得解决的 20 个问题。

---

# 一、问题一：模型能力已经足够了吗？

这是所有问题的起点。

过去大家很容易认为：

> Agent 做不好事情，是因为模型不够聪明。

但现在这个解释正在越来越不充分。

一个模型可能已经具备：

* 很强的代码能力；
* 很强的推理能力；
* 很强的知识能力；
* 很强的工具调用能力。

但是把它放进真实环境以后，表现却可能明显下降。

原因在于：

```text
模型能力
≠
任务完成能力
```

真正的任务完成能力还受到：

```text
Context
Memory
Tools
Execution
Environment
Feedback
Verification
```

等因素影响。

最近关于 Harness Engineering 的研究也开始直接验证这一点：在相同模型和工具条件下，对执行约束、结构化规划、验证和恢复机制进行设计，可以显著改变 Agent 的执行稳定性，但这种收益并不是简单地“约束越多越好”，而需要针对具体模型和任务进行测量。

## 我的判断

**2026 年之后，模型能力仍然重要，但“模型决定一切”的时代正在结束。**

未来的竞争会越来越像：

```text
模型能力
×
Harness质量
×
上下文质量
×
工具能力
×
执行可靠性
```

而不是单纯比较模型参数或者 benchmark 分数。

## 长期预测

未来 3～5 年，基础模型可能越来越像：

> **计算平台中的 CPU。**

真正决定一个 Agent 好不好用的，将越来越多地转移到模型之上的系统。

---

# 二、问题二：为什么 Agent 会“会做”，却不能“可靠地做”？

这是当前 Agent 最核心的问题之一。

普通聊天模型只需要回答一次：

```text
问题 → 答案
```

而 Agent 面对的是：

```text
目标
 ↓
计划
 ↓
行动
 ↓
观察
 ↓
重新计划
 ↓
行动
 ↓
验证
 ↓
修正
 ↓
完成
```

假设每一步成功率都是 95%。

连续执行 20 步：

```text
0.95^20 ≈ 35.8%
```

这意味着：

> 单步很强，不代表长链任务可靠。

这也是为什么很多 Agent Demo 看起来非常惊艳，但一旦进入复杂生产环境，就开始暴露问题。

## 真正需要解决的不是“能力”，而是“可靠性”

未来 Agent 应该具备：

```text
执行
 ↓
检查
 ↓
发现异常
 ↓
定位原因
 ↓
恢复
 ↓
重新规划
 ↓
继续
```

而不是：

```text
执行
 ↓
失败
 ↓
结束
```

## 我的判断

未来 Agent 的核心评价指标不会只是：

> “它能不能完成任务？”

而会变成：

> **“在没有人盯着的情况下，它完成任务的概率是多少？”**

## 长期预测

未来 Agent Benchmark 很可能从：

```text
一次成功率
```

逐渐转向：

```text
长期任务成功率
+
错误恢复率
+
无监督成功率
+
安全失败率
```

也就是说：

> **Agent Reliability 会成为类似传统软件工程中 SLO 一样重要的概念。**

---

# 三、问题三：Agent 到底需要多少自主性？

今天大家经常把“自主”当成一个正向指标。

好像：

> 越 Autonomous 越先进。

但实际上完全不是这样。

例如：

**写一篇文章：**

AI 可以高度自主。

**删除生产数据库：**

AI 不应该高度自主。

**修改代码：**

可以自主。

**部署生产环境：**

可能需要审批。

因此真正的问题不是：

> Agent 应该多自主？

而是：

> **什么任务应该由 AI 决定，什么任务应该由人决定？**

可以建立一个简单的自主等级：

```text
L0：只回答

L1：调用工具

L2：自主规划

L3：连续执行

L4：自主恢复

L5：主动发现任务

L6：持续运行

L7：自主优化策略
```

不同任务应该有不同等级。

## 我的判断

未来不会出现一个：

> “100% Autonomous Agent”

真正成熟的 Agent 更可能是：

> **动态自主性。**

也就是：

```text
低风险任务 → 高自主
高风险任务 → 低自主
不确定任务 → 请求人类
```

## 长期预测

未来 Agent 的权限系统可能不再只是：

```text
允许 / 禁止
```

而是：

```text
任务级权限
步骤级权限
资源级权限
金额级权限
风险级权限
```

Agent 的“自主性控制”会逐渐成为一种基础设施。

---

# 四、问题四：Context Engineering 会不会比 Prompt Engineering 更重要？

过去我们习惯说：

> Prompt Engineering。

未来可能越来越需要讨论：

> Context Engineering。

因为一个 Agent 真正需要面对的不是一句 Prompt，而是：

```text
System Prompt
+
User Request
+
历史对话
+
Memory
+
Knowledge
+
Tools
+
Environment State
+
Previous Actions
+
Current Task State
```

问题来了：

> **这些信息应该全部给模型吗？**

当然不是。

信息太少：

> AI 不知道发生过什么。

信息太多：

> AI 找不到真正重要的信息。

因此真正的问题是：

> **Agent 在当前这一刻，到底应该看到什么？**

这和人的认知其实非常相似。

人类并不是把一生的记忆全部放进工作记忆，而是不断进行：

```text
检索
筛选
压缩
关联
忽略
```

近期关于 Agent Memory 的研究也发现，不同记忆存储方式并不存在一个对所有任务都最优的方案；在某些任务中，更多检索反而会把注意力从真正重要的行动上下文中带走。

## 我的判断

未来 Agent 的核心能力之一会变成：

> **构造正确 Context 的能力。**

## 长期预测

未来可能出现一种新的基础设施：

```text
Context Compiler
```

它负责：

```text
World State
 ↓
Memory
 ↓
Knowledge
 ↓
Task State
 ↓
User State
 ↓
Context Selection
 ↓
Model
```

模型负责思考。

Context Compiler 决定：

> **模型应该思考什么。**

---

# 五、问题五：Agent 的 Memory 到底应该是什么？

“给 Agent 加 Memory”看起来简单。

实际上，这是一个非常难的问题。

因为 Memory 并不是简单地：

```text
把聊天记录保存下来
```

真正的长期记忆至少包括：

```text
用户事实
用户偏好
历史经验
任务状态
失败记录
成功案例
重要决策
长期目标
工作习惯
工具使用方式
```

更复杂的是：

> **什么应该被记住？**

以及：

> **什么时候应该忘记？**

如果 Agent 把所有事情都记住，长期下来反而会越来越糟。

因此真正的 Memory 应该具备：

```text
Write
 ↓
Store
 ↓
Retrieve
 ↓
Update
 ↓
Forget
 ↓
Consolidate
```

最近的 Agent Memory 研究正在从简单的向量检索，逐渐扩展到结构化、层级化、长期记忆和动态路由等方向。

## 我的判断

未来 Agent Memory 不会是一个简单的：

> Vector Database。

而会更像：

> **一种新的认知存储系统。**

## 长期预测

未来成熟 Agent 可能同时拥有：

```text
Working Memory
短期工作记忆

Episodic Memory
事件记忆

Semantic Memory
事实知识

Procedural Memory
技能与流程

User Memory
用户模型

Self Memory
Agent自身历史
```

这可能会成为 Agent 基础设施最重要的一层。

---

# 六、问题六：Skill、Workflow、Memory 到底应该如何划分？

今天 Agent 系统中有很多概念：

* Prompt
* Skill
* Workflow
* Tool
* Memory
* Knowledge
* Policy

但它们之间的边界并不清晰。

例如：

> “如何部署一个 Python 项目。”

到底是：

* Skill？
* Workflow？
* Knowledge？
* Memory？

未来这个边界很可能发生变化。

我更倾向于这样理解：

```text
Knowledge
= 知道什么

Skill
= 会做什么

Workflow
= 按什么步骤做

Memory
= 以前发生过什么

Policy
= 什么不能做

Tool
= 可以作用于什么

Context
= 当前应该知道什么
```

这其实构成了 Agent 的“认知操作系统”。

## 我的判断

未来 Skill 不会只是静态 Markdown 文件。

它可能逐渐变成：

```text
Skill
+
Examples
+
Experience
+
Evaluation
+
Version
```

也就是说：

> **Skill 会开始拥有生命周期。**

## 长期预测

未来可能出现：

```text
Skill Creation
Skill Testing
Skill Evaluation
Skill Optimization
Skill Versioning
Skill Retirement
```

最终：

> **Skill 可能成为 Agent 能力演化的最小单位。**

---

# 七、问题七：Agent 能不能从自己的经历中真正学习？

这是我认为“AI 自我进化”最现实的切入点。

我们没有必要马上讨论：

> AI 修改自己的模型。

现在就可以问：

> **Agent 做了 1000 次任务之后，会不会比第一次更会做？**

例如：

```text
任务 1
失败

任务 2
失败

任务 3
成功

任务 4
成功
```

Agent 能不能总结：

> “以后遇到这种任务，应该采用方案 B，而不是方案 A。”

这就是：

```text
Experience
 ↓
Reflection
 ↓
Evaluation
 ↓
Strategy
 ↓
Skill Update
```

这是一种非常现实的 Self-Improvement。

## 我的判断

真正有价值的 Agent 自我进化，最早不会发生在：

> Model Weights。

而会发生在：

> **Harness、Memory、Skill、Workflow 和 Strategy。**

近期已经出现直接探索持续 Harness、自我改进和跨轨迹保留 memory、skills、prompts 的 Agent 系统，这说明“经验积累 → 策略优化”正在从概念逐渐进入工程阶段。

## 长期预测

未来 Agent 可能出现：

```text
Base Model
+
Personal Experience
+
Domain Experience
+
Self-Evaluation
+
Strategy Learning
```

最终：

> **同一个基础模型，可以因为不同的长期经历，形成完全不同的 Agent。**

---

# 八、问题八：Harness 到底是什么？

这是未来几年我认为非常值得关注的概念。

过去可以把 Harness 理解成：

> 模型外面的一层代码。

但这个定义已经越来越不够用了。

一个真正的 Agent Harness 可能负责：

```text
Context
Memory
Tools
Planning
Execution
State
Permissions
Retry
Recovery
Verification
Logging
Evaluation
Scheduling
```

也就是说：

> **Harness 正在从“胶水层”变成“Agent Runtime”。**

近期关于 Harness Engineering 的研究已经开始直接把确定性执行、结构化规划、工具约束、输出验证、重试和状态管理视为独立的系统工程问题。

## 我的判断

未来很可能出现一个反直觉趋势：

> **模型越强，Harness 不一定越简单。**

因为：

```text
模型能力 ↑
 ↓
能做的事情 ↑
 ↓
行动空间 ↑
 ↓
环境复杂度 ↑
 ↓
状态复杂度 ↑
 ↓
Harness重要性 ↑
```

## 长期预测

未来 Agent 的竞争可能越来越像：

> **Model Engineering + Harness Engineering**

甚至最终：

> **Model 是“大脑”，Harness 是操作系统和神经系统。**

---

# 九、问题九：Agent 为什么需要一个 Runtime？

如果 Agent 只是：

```text
输入
→
思考
→
输出
```

当然不需要 Runtime。

但如果它要持续工作：

```text
任务
 ↓
执行
 ↓
暂停
 ↓
等待
 ↓
恢复
 ↓
继续
 ↓
失败
 ↓
恢复
```

那么 Runtime 就变得非常重要。

它需要管理：

```text
Process
State
Memory
Files
Tools
Permissions
Secrets
Schedules
Events
Checkpoints
Logs
Recovery
```

这已经越来越像操作系统。

## 我的判断

未来 Agent Framework 会逐渐分裂成两个方向：

### 一类

负责：

> **让模型更容易开发 Agent。**

### 另一类

负责：

> **让 Agent 可以长期运行。**

后者可能最终形成真正的：

> **Agent Runtime。**

## 长期预测

未来几年可能出现类似：

```text
Operating System
        ↓
Application
```

这样的结构：

```text
Agent Runtime
        ↓
Agent
```

Agent 不再只是一个 Python Loop。

---

# 十、问题十：Agent 如何拥有“时间”？

这是一个目前非常值得重视的问题。

今天大多数 AI 是：

```text
用户输入
 ↓
Agent运行
 ↓
任务结束
 ↓
Agent消失
```

这其实不是一个真正的长期 Agent。

真正的个人 Agent 应该是：

```text
今天
 ↓
明天
 ↓
下周
 ↓
下个月
```

它知道：

* 上次做到了哪里；
* 什么任务没有完成；
* 什么事情正在等待；
* 用户最近发生了什么；
* 哪些计划发生了变化；
* 哪些事情值得主动处理。

近期已经有产品探索让 Coding Agent 持续运行、主动产生后续任务，并在适当情况下主动通知用户。

## 我的判断

这可能是：

> **Chatbot → Agent**

最重要的分界线之一。

## 长期预测

未来 Agent 会从：

> Session-based AI

逐渐转向：

> **Time-based AI。**

也就是说：

> AI 不再是一段对话，而成为一个持续运行的过程。

---

# 十一、问题十一：Agent 什么时候应该主动找你？

这实际上是“长期 Agent”的另一个核心问题。

如果 Agent 永远不主动：

> 它不像助手。

如果 Agent 什么都主动：

> 它会非常烦。

因此存在一个连续区间：

```text
被动
←──────────────→
主动
```

真正成熟的 Agent 应该知道：

> **什么时候值得打扰用户。**

例如：

### 不值得打扰

“我搜索到了一个普通结果。”

### 值得打扰

“我发现你的项目连续三次部署失败，可能存在同一个根因。”

### 必须打扰

“生产数据库删除操作需要你的确认。”

所以主动性应该与：

```text
Importance
+
Urgency
+
Confidence
+
Risk
```

共同决定。

## 长期预测

未来 Agent 会拥有一种：

> **Attention Policy**

它决定：

> **什么时候应该占用人类的注意力。**

这可能成为个人 AI 最重要的产品设计之一。

---

# 十二、问题十二：Agent 如何知道自己做对了？

这是一个非常容易被忽略的问题。

传统程序：

```text
输入
→
程序
→
输出
```

只要测试通过，就可以判断结果。

但 Agent 是：

```text
目标
→
计划
→
行动
→
结果
```

问题在于：

> **结果看起来正确，不代表真的正确。**

因此 Agent 必须拥有：

> Verification。

例如 Coding Agent：

```text
修改代码
 ↓
运行测试
 ↓
静态检查
 ↓
运行集成测试
 ↓
检查日志
 ↓
确认结果
```

Research Agent：

```text
生成结论
 ↓
查证来源
 ↓
交叉验证
 ↓
检查矛盾
 ↓
输出
```

## 我的判断

未来真正可靠的 Agent，必须把：

> **Action 和 Verification**

设计成一对基本组件。

## 长期预测

未来 Agent Architecture 可能越来越像：

```text
Planner
   ↓
Executor
   ↓
Verifier
   ↓
Critic
   ↓
Recovery
```

而不是单纯的：

```text
LLM Loop
```

---

# 十三、问题十三：Agent 的 Evaluation 为什么这么难？

传统模型可以测试：

```text
输入
→
答案
```

Agent 却是：

```text
输入
→
10～1000 次行动
→
最终结果
```

这带来一个问题：

> **Agent 到底应该如何评价？**

最终答案对不对？

还是过程对不对？

工具调用对不对？

成本是否合理？

有没有越权？

有没有浪费大量 Token？

有没有走弯路？

有没有造成安全问题？

最近的 Agent 工程实践已经把 observability 和 evaluation 作为生产部署的核心基础设施；例如 LangChain 的 2026 调查显示，Agent tracing 已经比较普遍，但离线和在线评测的普及程度仍明显低于 observability。

## 我的判断

未来 Agent Evaluation 会从：

> Final Answer Evaluation

转向：

> **Trajectory Evaluation。**

也就是评价整个：

```text
Thought
+
Tool
+
State
+
Action
+
Recovery
+
Result
```

## 长期预测

未来可能形成：

```text
Agent Benchmark
=
Capability
+
Reliability
+
Efficiency
+
Safety
+
Recovery
+
Long-Horizon Performance
```

Agent 的排行榜会越来越像软件工程 Benchmark，而不是传统语言模型 Benchmark。

---

# 十四、问题十四：Agent 的成本到底应该怎么算？

今天很多人比较模型，只看：

> 每百万 Token 多少钱。

但真正运行一个 Agent，成本远不止 Token。

例如：

```text
Model
+
Search
+
Browser
+
API
+
Compute
+
Storage
+
Memory
+
Human Review
+
Failure Recovery
```

更重要的是：

> **完成一个真正任务到底多少钱？**

比如：

```text
任务价值：100 元

模型：5 元
搜索：2 元
工具：1 元
人工审核：10 元
错误修复：8 元

最终成本：26 元
```

那么 Agent 的经济价值就完全不同了。

## 我的判断

未来真正重要的指标会从：

> Cost per Token

转向：

> **Cost per Successful Task**

进一步：

> **Cost per Useful Outcome**

## 长期预测

Agent 的经济学可能逐渐形成：

```text
Agent ROI
=
任务创造价值
/
模型成本 + 工具成本 + 基础设施成本 + 人工监督成本 + 错误成本
```

这会决定哪些 Agent 最终真正能够商业化。

---

# 十五、问题十五：Agent 的权限应该如何设计？

这是 Agent 进入真实世界以后不可回避的问题。

传统软件权限：

```text
用户
→
程序
→
权限
```

Agent 更复杂：

```text
用户
→
Agent
→
规划
→
工具
→
子Agent
→
外部系统
```

问题是：

> **Agent 到底拥有什么权限？**

如果给太少：

> 做不了事情。

如果给太多：

> 一旦出错，后果巨大。

因此未来权限应该逐渐从：

```text
有权限 / 没权限
```

转向：

```text
任务级权限
动作级权限
资源级权限
金额级权限
时间级权限
风险级权限
```

## 我的判断

Agent Security 不应该只是：

> “防止 Prompt Injection。”

而应该变成：

> **完整的 Agent Governance。**

2026 年关于 Agent 治理的讨论已经明显从“模型安全”扩展到 Agent 的身份、权限、行为链、可见性和实时监控。

## 长期预测

未来企业可能需要一个：

> **Agent Control Plane**

统一管理：

```text
Agent Identity
Permissions
Tools
Policies
Audit
Monitoring
Approval
```

---

# 十六、问题十六：Agent 如何处理“不确定性”？

人类非常擅长说：

> “我不知道。”

而 AI 很容易：

> “我猜一个。”

这在普通聊天中问题不大。

但 Agent 一旦开始执行真实操作，就非常危险。

例如：

```text
AI：我认为这个文件应该删除。
```

如果它真的删了呢？

所以 Agent 应该拥有：

```text
Confidence
```

甚至：

```text
Uncertainty Estimation
```

当：

```text
Confidence > 95%
```

自动执行。

当：

```text
60% < Confidence < 95%
```

继续调查。

当：

```text
Confidence < 60%
```

请求人类。

## 我的判断

未来成熟 Agent 不会只是：

> “知道答案。”

而应该知道：

> **“自己有多确定。”**

## 长期预测

未来 Agent 的决策系统可能越来越类似：

```text
Action
+
Confidence
+
Risk
+
Expected Value
```

而不是单纯：

```text
Action
```

---

# 十七、问题十七：多 Agent 真的是未来吗？

现在一个很流行的观点是：

> 一个 Agent 不够强，就让十个 Agent 一起工作。

于是：

```text
Research Agent
Coding Agent
Testing Agent
Planning Agent
Review Agent
Manager Agent
```

组成一个 Multi-Agent System。

但问题是：

> **Agent 越多，系统真的越强吗？**

不一定。

多个 Agent 会增加：

```text
通信成本
状态同步
上下文损失
协调错误
重复工作
Token 成本
权限复杂度
```

因此：

```text
10个Agent
```

不一定比：

```text
1个强Agent
+
优秀Harness
```

更好。

## 我的判断

未来不会是：

> Multi-Agent Everywhere。

而会是：

> **必要时并行，不必要时单体。**

## 长期预测

未来多 Agent 架构可能类似：

```text
一个主Agent
+
少量专用Agent
+
共享Memory
+
共享Runtime
+
统一Evaluation
```

而不是无限增加 Agent 数量。

---

# 十八、问题十八：AI 写代码越来越强以后，软件工程真正的瓶颈在哪里？

这是当前最现实的问题之一。

如果 AI 可以快速生成：

```text
代码
测试
文档
重构
Bug Fix
```

那么软件开发成本会下降。

但问题是：

> **软件真正稀缺的东西可能不是代码。**

而是：

```text
需求
架构
约束
验证
安全
系统理解
产品判断
```

因此：

```text
Coding Cost ↓↓↓
```

不一定意味着：

```text
Software Engineering Cost ↓↓↓
```

因为瓶颈可能转移。

AI Coding Agent 的最新评测也开始强调，单纯的 pass@k 并不能充分描述 Agent 的真实可靠性和安全性，需要更严格的多次运行可靠性指标。

## 我的判断

未来程序员的核心价值会逐渐从：

> 写代码

转向：

> **定义系统、验证系统、控制系统。**

## 长期预测

软件工程可能从：

```text
Human writes code
AI assists
```

逐渐变成：

```text
Human defines intent
AI constructs system
AI tests system
AI maintains system
Human governs system
```

---

# 十九、问题十九：Agent 能不能真正成为一个“持续工作的个人助手”？

这是所有上述问题最终汇聚的地方。

今天的 AI Assistant 更像：

```text
你叫它
 ↓
它回答
 ↓
结束
```

真正的个人 Agent 应该是：

```text
用户
 ↓
长期目标
 ↓
Agent
 ↓
持续观察
 ↓
持续记忆
 ↓
持续执行
 ↓
主动发现机会
 ↓
主动提醒
 ↓
持续优化
```

例如：

你说：

> “我准备做一个 AI 产品。”

一个真正的 Agent 不应该只回答：

> “好的，这是一个产品规划。”

而应该：

```text
今天：
建立项目

明天：
整理竞品

三天后：
发现一个技术问题

一周后：
提醒你 MVP 还缺一个功能

两周后：
分析用户反馈

一个月后：
根据数据建议修改方向
```

这才真正开始接近：

> **Agent。**

近期对 persistent agent 的探索，实际上已经开始朝这个方向发展：让 Agent 在没有每次用户显式触发的情况下持续工作、产生后续任务，并在受到权限约束的情况下主动与用户交互。

## 我的判断

个人 AI 真正的价值，不在：

> “它回答得比 ChatGPT 更好。”

而在：

> **它是否能够持续参与一个人的生活和工作。**

## 长期预测

未来个人 Agent 最重要的资产可能不是：

> 模型。

而是：

```text
你的历史
+
你的目标
+
你的偏好
+
你的工作
+
你的关系
+
你的知识
+
你的长期计划
```

也就是说：

> **个人 Agent 最终会成为个人数字世界的长期操作层。**

---

# 二十、问题二十：Agent 能不能真正形成一个“自我改进闭环”？

这是最后一个，也是我认为最重要的问题。

前面 19 个问题实际上最终都可以汇聚到这里。

一个真正成熟的 Agent 不应该是：

```text
Model
 ↓
Task
 ↓
Answer
```

而应该是：

```text
Task
 ↓
Plan
 ↓
Action
 ↓
Result
 ↓
Evaluation
 ↓
Reflection
 ↓
Memory
 ↓
Strategy Update
 ↓
Skill Update
 ↓
Better Agent
 ↓
Next Task
```

这才是真正意义上的：

> **Agentic Learning Loop。**

注意，这里并不要求 AI 修改自己的神经网络。

第一阶段只需要：

```text
经验积累
```

第二阶段：

```text
策略优化
```

第三阶段：

```text
Skill优化
```

第四阶段：

```text
Workflow优化
```

第五阶段：

```text
Harness优化
```

最后才可能涉及：

```text
Model优化
```

因此：

> **AI 自我进化最早发生的地方，很可能根本不是模型。**

而是模型之外。

---

# 结语：真正的 Agent，不是一个更大的模型

如果把今天的 AI 发展重新画一遍，我认为真正重要的路线可能不是：

```text
GPT-1
 ↓
GPT-2
 ↓
GPT-3
 ↓
GPT-4
 ↓
GPT-5
 ↓
更大的模型
```

而应该是：

```text
Model
 ↓
Reasoning
 ↓
Tool Use
 ↓
Context Engineering
 ↓
Memory
 ↓
Skills
 ↓
Execution
 ↓
Verification
 ↓
Recovery
 ↓
Persistence
 ↓
Self-Improvement
 ↓
Agent
```

这两条路线最大的区别是：

> 第一条路线关注的是“智能有多强”。

第二条路线关注的是：

> **“智能能不能持续作用于世界。”**

而这可能正是今天 AI 所处的历史阶段。

---

# 一、从模型到 Agent，本质上发生了什么？

模型解决的是：

> **“我能不能理解并生成？”**

Agent 需要解决的是：

> **“我能不能持续地把事情做完？”**

这两个问题完全不同。

可以把它简单表示成：

```text
模型：

输入
 ↓
推理
 ↓
输出
```

而 Agent：

```text
目标
 ↓
理解
 ↓
规划
 ↓
行动
 ↓
观察
 ↓
记忆
 ↓
验证
 ↓
修正
 ↓
继续
```

因此：

> **Agent 不是模型的一个应用形态，而可能是模型能力进入现实世界之后的一种新计算范式。**

---

# 二、未来几年，真正值得关注的可能不是“谁的模型最大”

而是下面这几个问题：

```text
谁拥有最好的 Context？

谁拥有最好的 Memory？

谁拥有最好的 Harness？

谁拥有最好的 Agent Runtime？

谁拥有最好的 Evaluation？

谁能够让 Agent 长期运行？

谁能够让 Agent 自己恢复？

谁能够让 Agent 从经验中学习？

谁能够把 Agent 的成本降下来？

谁能够让人真正放心地把事情交给 Agent？
```

这意味着 AI 产业可能正在经历一个非常重要的结构变化：

```text
第一阶段
模型竞争

        ↓

第二阶段
模型 + Agent竞争

        ↓

第三阶段
Agent系统竞争

        ↓

第四阶段
长期自主系统竞争
```

今天我们可能正处在第二阶段向第三阶段过渡的过程中。

---

# 三、我对未来 1～3 年的判断

如果只看未来几年，而不是几十年，我认为最可能出现的变化是：

### 1. Model 会越来越商品化

模型能力仍然继续快速提升。

但模型之间的差距会越来越难以单独决定产品体验。

---

### 2. Harness Engineering 会成为新的工程方向

企业开始意识到：

> 同一个模型，不同 Harness，最终表现可以完全不同。

因此 Context、Memory、Tools、Runtime、Evaluation 会逐渐成为独立的工程领域。

---

### 3. Agent Memory 会成为重要基础设施

现在 Memory 仍然很早期。

未来会逐渐从：

> “保存聊天记录”

进化到：

> **“构建 Agent 的长期认知状态。”**

---

### 4. Evaluation 会从答案评价转向过程评价

未来真正重要的不是：

> “这次回答对不对？”

而是：

> “这个 Agent 在 1000 次真实任务中表现怎么样？”

---

### 5. Agent 会从 Session 转向 Persistent

AI 不再每次都从零开始。

而是：

```text
昨天
 ↓
今天
 ↓
明天
 ↓
持续运行
```

---

### 6. Agent 会逐渐拥有主动性

但不是无限主动。

而是：

> **根据任务价值、风险和用户偏好决定什么时候行动。**

---

### 7. AI 自我改进首先发生在模型之外

最早出现的不是：

> AI 自己训练自己。

而是：

```text
AI
 ↓
记录经验
 ↓
评价结果
 ↓
优化策略
 ↓
更新Skill
 ↓
更新Workflow
```

这是距离今天最近、也最现实的 AI 自我进化。

---

# 四、再往后 3～5 年，会发生什么？

我更倾向于认为：

```text
AI Assistant
        ↓
AI Agent
        ↓
Persistent Agent
        ↓
Personal/Enterprise Agent Runtime
        ↓
Self-Improving Agent
```

真正的变化不是：

> AI 更像一个人。

而是：

> **AI 开始像一个持续存在的软件主体。**

它有：

```text
身份
状态
记忆
能力
权限
经验
目标
历史
```

它不会每次被调用以后重新开始。

而是：

> **一直在那里。**

---

# 五、最终可能发生的一个关键转变

过去的软件是：

```text
人
 ↓
软件
 ↓
机器
```

人告诉软件：

> “执行这个程序。”

未来可能变成：

```text
人
 ↓
Agent
 ↓
软件
 ↓
机器
 ↓
现实世界
```

人不再告诉 AI：

> 每一步应该怎么做。

而只告诉它：

> **我想要什么。**

然后 Agent 自己：

```text
理解目标
 ↓
制定计划
 ↓
调用工具
 ↓
执行
 ↓
验证
 ↓
修正
 ↓
持续运行
```

这才是我认为真正意义上的：

# **从模型到 Agent。**

---

# 六、所以，今天最值得问的问题已经变了

过去的问题是：

> **“下一代模型什么时候出现？”**

现在更值得问的是：

> **“下一代 Agent 的操作系统什么时候出现？”**

过去我们研究：

> 如何让模型拥有更多知识。

现在更应该研究：

> **如何让 Agent 正确地知道自己现在需要什么信息。**

过去我们研究：

> 如何让模型回答得更好。

现在更应该研究：

> **如何让 Agent 把任务真正完成。**

过去我们研究：

> 如何让模型减少幻觉。

现在更应该研究：

> **如何让 Agent 在犯错之后发现错误、恢复错误，并且不再犯同样的错误。**

过去我们研究：

> 如何让 AI 更聪明。

现在更应该研究：

> **如何让 AI 的智能能够持续地作用于世界。**

这可能就是当前 AI 发展阶段最重要的一次范式转移：

> **从“模型智能”走向“系统智能”。**

而真正值得关注的下一代 AI 公司，也许未必是训练出参数规模最大的模型的公司。

它们可能是那些最先解决以下问题的公司：

> **如何让一个 AI 在没有人持续盯着的情况下，连续工作一个星期、一个月甚至一年，而且越来越可靠、越来越了解环境、越来越懂得如何完成任务。**

如果这件事情真正被解决，那么我们今天所谓的“Agent”才可能真正从一个产品形态，变成一种新的计算基础设施。

而今天我们看到的各种 Agent——Coding Agent、Research Agent、Browser Agent、Personal Agent、Enterprise Agent——也许只是这个过程最早期的形态。

**模型只是让 AI 拥有了“思考能力”。**

**Harness、Memory、Runtime、Tools、Environment 和持续学习机制，才可能让这种能力真正变成“行动能力”。**

而从行动能力走向长期自主能力，可能就是未来几年 AI 最值得研究、也最值得投入的方向。**
