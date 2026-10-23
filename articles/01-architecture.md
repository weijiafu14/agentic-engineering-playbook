# Why AI Cannot Build Complex Systems Alone

This is the first chapter of my series on **the future of AI-driven software development**: **Architecture**.

AI can already produce demos quickly. In many cases, it can even build a feature in one shot.

But a demo is not the real challenge.

The real challenge is building a complex system that runs for years, evolves continuously, and remains safe to maintain.

This is not about small differences between coding agents: context compression, tool calling, or slightly better code generation. Those differences matter, but I do not think they create an order of magnitude improvement in engineering productivity.

The larger shift comes from building an engineering system designed for agentic development.

Even as AI coding capabilities improve, the following will remain necessary for a long time. In fact, they will become more important.

## 1. A repository needs complete, living architecture documentation

A complex codebase cannot be understood reliably by asking a model to read all the code.

Even if the context window becomes large enough, putting an entire repository into context does not create genuine system understanding. Code contains local implementation details, historical baggage, and implicit constraints. Without a stable architectural representation, model performance degrades quickly.

Architecture documentation is therefore not onboarding material and not a diagram that becomes obsolete after it is drawn.

It should be a shared map for humans and agents. It should explain:

- the real business scenarios and critical flows;
- each module’s responsibility;
- module boundaries and collaboration patterns;
- how data, state, and side effects move through the system;
- constraints that must not be broken;
- high risk areas that require stronger validation.

The purpose is not to replace code. It is to keep agents from having to infer the entire system from scratch for every change.

## 2. Architecture must reflect real business pressure

Good architecture does not mean making every module technically optimal.

It means estimating the actual pressure the business will create, then defining the appropriate engineering standard for each part of the system.

Some modules need extreme reliability. Some need low latency. Some need scalability. Others only need to remain stable within a predictable workload.

This matters even more with AI. Agents are good at local optimization, but they do not naturally know whether a component deserves additional complexity.

Humans still need to define constraints, priorities, and risk budgets. Only then can agents work efficiently within the right boundaries.

## 3. Loose coupling directly affects the cost and safety of AI development

Module boundaries still matter in the AI era, for stronger reasons than before.

First, release safety.

When one requirement touches many modules, risk rises sharply. Every individual change may look reasonable, while their combination creates unexpected failures. Current agents cannot guarantee correctness across broad changes.

Second, engineering cost.

A large change requires more code to understand, generate, review, test, and regress. It consumes more tokens, takes more time, and creates more context complexity.

A good architecture keeps most changes local. The blast radius is clear, validation is cheaper, and failures are easier to diagnose and roll back.

Architecture also matters because AI is good at finding solutions to individual problems, but much less reliable at assessing each solution’s impact on the whole system. Clear module boundaries and dependencies make the impact path visible: when one module changes, we can see which upstream and downstream modules may be affected, along with the system capabilities and related scenarios that depend on them. That gives both people and AI a clearer basis for evaluating a change’s effects on the wider system and its related scenarios.

Loose coupling is not an abstract design preference. It is a safety boundary and a cost control mechanism for agentic engineering.

## 4. Testability becomes a core capability

AI will write and modify code faster and faster. Human attention will not scale at the same rate.

If engineers still need to read every line of every change to estimate its real impact, AI productivity will eventually be bottlenecked by human review capacity.

The answer cannot be “a human looked at the code and it seemed fine.”

Modules need to be testable, and tests need to cover real user scenarios. Tests should protect important system behavior and constraints, not merely prove that code executes.

When a change passes effective and sufficiently complete validation, release risk can be reduced dramatically. Humans can focus on the decisions that actually require judgment: business tradeoffs, architecture, risk, and product quality.

## 5. Complex systems need replayable real-world cases

Consider agent or harness development.

A few hand written unit tests are rarely enough to prove correctness. Real platforms accumulate valuable cases: user inputs, model outputs, tool calls, failure paths, and final outcomes.

After a harness iteration, historical model responses should be replayed against the new version. The question is simple: does the new harness still handle the real situations the platform has already encountered?

A case library and replay system become the system’s operational memory.

They turn past failures and edge cases into constraints that future versions must satisfy. The system stops relearning the same lessons on every iteration.

## Closing thought

AI will become much better at writing code. But the hard part of complex systems has never been code generation alone.

The real productivity ceiling depends on whether we can build systems that agents can understand safely, modify locally, validate effectively, and regress continuously.

The durable engineering paradigm may not be a particular “best” coding agent.

It will be:

clear architectural representations, sensible module boundaries, real business constraints, verifiable system behavior, and a growing body of replayable cases and regression evidence.

AI will keep improving. These capabilities will not become less important.

They will become the foundation that makes AI development reliable at scale.

---

# 为什么 AI 不能独自构建复杂系统

这是我的「未来 AI 研发体系」系列第一篇：**架构篇**。

AI 已经能快速做出 Demo，甚至能一把成地完成很多产品功能。

但真正困难的研发目标，从来不是 Demo，而是构建一个复杂、长期运行、持续迭代，并且可以安全维护的系统。

这篇不讨论不同 Coding Agent 在上下文压缩、工具调用、代码生成等细节能力上的差异。它们当然重要，但我不认为这些小能力的领先，能带来研发效率一个数量级的变化。

真正能让研发效率提升一个层级的，是一套面向 Agent 编程的研发基础设施和工程范式。

即使 AI 的 Coding 能力持续进化，下面这些能力在很长时间内仍然需要，甚至会变得更重要。

## 1. 代码仓库必须有完整、可维护的技术架构文档

复杂工程不可能靠模型「把全部代码读一遍」来理解。

即使上下文窗口足够大，把所有代码塞进去也不等于模型真正理解了系统。代码包含大量局部实现细节、历史包袱和隐含约束；当关键信息没有被提炼成稳定的架构表达时，模型的判断质量会明显下降。

所以，架构文档不是给新人看的说明书，也不是画完就不再维护的流程图。

它应该成为人和 Agent 共同使用的系统地图，至少回答这些问题：

- 业务场景和核心链路是什么；
- 每个模块解决什么问题，承担什么责任；
- 模块之间如何协作，边界在哪里；
- 哪些数据、状态和副作用会跨模块流动；
- 哪些约束是不能被破坏的；
- 哪些区域风险高，修改时需要额外验证。

架构文档的目标不是替代代码，而是让 Agent 不必从零开始猜测系统。

## 2. 技术架构首先要服务真实业务压力

技术架构不等于每个模块都追求技术上的最优解。

更重要的是：在能够预估业务带来的实际压力后，清晰评估不同模块应该达到什么技术标准。

有些模块需要极高可靠性，有些模块需要低延迟，有些模块需要强扩展性，有些模块只需要在可预见的业务规模内稳定运行。技术投入应该和真实业务风险匹配。

这件事在 AI 时代更重要，因为 Agent 很擅长局部优化，却不会天然知道「这个模块究竟值不值得复杂化」。

人需要先定义系统的约束、优先级和风险预算。Agent 才能在正确的边界内高效工作。

## 3. 模块边界和松耦合，会直接决定 AI 研发的成本与安全性

AI 时代依然需要模块之间松耦合，而且理由比过去更充分。

第一，是上线安全。

如果一个需求导致大量模块被同时修改，那么即使每一处改动看起来都合理，组合起来也会显著提高风险。以当前 Agent 的能力，还不能保证大范围改动始终不出错。

第二，是研发成本。

大范围改动意味着更多代码需要被理解、生成、审查、测试和回归，也意味着更多 Token 消耗、更长执行时间，以及更高的上下文复杂度。

一个好的架构，应该让大多数需求都能被限制在少量模块中完成。这样每次改动的影响范围更清晰，验证成本更低，出现问题时也更容易定位和回滚。

架构也很重要，因为 AI 很擅长搜索某个问题的解决方案，却很难评估每个方案对整个系统带来的影响。清晰的模块边界和依赖关系，能让改动的影响路径变得可见：一个模块发生变化，会影响哪些上游、下游模块，又会波及哪些全局能力和关联场景。这样，人和 AI 都能更准确地评估改动对全局和其他关联场景的影响。

松耦合不是抽象上的洁癖，它是 Agent 时代的安全边界和成本控制手段。

## 4. 可测试性会成为 AI 研发体系的核心能力

AI 生成和修改代码的速度会越来越快，但人的注意力不会同步扩张。

如果人仍然需要逐行阅读大量改动，试图凭经验判断每次变更的真实影响，那么 AI 带来的效率最终只会卡在人类审查能力上。

所以，未来研发不能依赖「人看代码觉得没问题」。

我们需要让模块本身具备可测试性，并让测试覆盖真实用户场景。测试不只是判断代码能不能运行，而是锁住系统最重要的行为和约束。

当改动通过了足够有效、完整的测试后，我们才能把上线风险降到很低，让人把精力放在真正需要判断的地方：业务取舍、架构方向、风险识别和产品质量。

## 5. 系统必须积累可回放的真实案例

以 Agent 或 Harness 为例，系统的正确性很难只靠几条人工构造的单元测试证明。

平台上会积累大量真实案例：用户输入、模型返回、工具调用过程、异常路径，以及最终结果。

当我们完成一轮 Harness 迭代后，应该把历史上的模型返回重新喂给新版本的 Harness，验证改动是否仍能正确处理这些真实场景。

这类案例库和回放机制，本质上是复杂系统的「经验记忆」。

它能把过去踩过的坑转化为未来版本必须通过的约束，让系统不是每次迭代都重新学习同样的教训。

## 结尾

AI 会越来越擅长写代码，但复杂系统的核心问题从来不只是「如何生成代码」。

真正决定研发效率上限的，是我们是否能构建一套让 Agent 安全理解、局部修改、有效验证、持续回归的系统。

未来固定下来的研发范式，未必是某个最强的 Coding Agent。

更可能是：

清晰的架构表达、合理的模块边界、真实的业务约束、可验证的系统行为，以及可持续积累的案例与回归能力。

AI 会不断进化，但这些能力不会过时。恰恰相反，AI 越强，它们越重要。
