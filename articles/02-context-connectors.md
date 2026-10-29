# A Framework Built Around Context Assembly and Feedback

## 中文标题：围绕上下文装配与反馈构建框架

I really like the design philosophy behind the DSH framework, and I have a few framework-level ideas I’d love to discuss with you.

I see Skills and MCP as concepts introduced to adapt to existing development workflows and make adoption easier. If we return to the essence of ReAct, they can all be abstracted as one mechanism: the program provides context to the model and receives feedback from it.

If the framework standardized only context assembly and context feedback, concepts such as workspaces—and even sessions—would not need to be part of the framework itself. Major service providers, such as sandbox services, session management services, and Git services, could instead become replaceable context connectors.

At the product level, users could flexibly choose which connectors to combine for each turn. At the architecture level, service providers would no longer be constrained by today’s Skill and MCP forms. They could expose their full services through DSH’s standardized service layer, making capabilities such as permissions and billing easier to implement.

I’m exploring a framework design based on this abstraction, and I’d really like to hear your thoughts.

---

# 关于 DSH：以上下文装配与反馈作为框架边界

我非常喜欢 DSH 框架的理念，有一些框架层面的想法想和您探讨一下。

我认为，Skill、MCP 这些概念，是为了适配过去的研发模式、便于推广而提出的。回到 ReAct 的本质，它们都可以抽象为一种机制：程序向大模型提供上下文，并接收大模型的反馈。

如果框架层面只提供上下文装配和上下文反馈的标准化能力，那么工作区，甚至会话这些概念，都不必包含在框架之内。大的服务提供商，比如沙箱服务、会话管理服务，甚至 Git 服务，都可以成为可替换的上下文连接器。

未来在产品上，用户可以灵活选择每一轮通过哪些连接器组合执行。在技术架构上，服务商也不必受限于现在的 Skill、MCP 形式，而是可以把完整的服务能力提供在 DSH 的标准化服务之上，权限、收费等能力也都能更容易实现。

我正在尝试这种抽象下的框架设计，非常想听听您的意见。
