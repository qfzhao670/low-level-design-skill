# SOLID 原则速查

判断"类与职责如何划分、依赖如何组织"的五条经验法则。它们是**判断标准**，不是必须逐条套用的教条——用它们来回答"我这段代码哪里别扭、该怎么拆"，而不是"我要不要再加个接口凑够 SOLID"。

## S — Single Responsibility Principle（单一职责原则）

- **定义**：A class should have only one reason to change（一个类只应有一个引起它变化的原因）。一个类只做一件事。
- **识别信号**：一个类/函数里同时塞了多种不相干的逻辑；改一个功能要动到一个不相干的类。
- **反例**：`User` 类里同时包含用户字段、数据库读写、邮件通知逻辑。
- **正例**：拆成 `User`（数据）+ `UserRepository`（持久化）+ `NotificationService`（通知）。
- **何时用**：改代码时发现"这个类同时在做多件不相关的事"，按职责切开。
- **不要过度**：拆得太碎（每个类只剩一个方法）会制造大量跳转，同样难维护。职责边界按**变化原因**划，而不是按方法数量。

## O — Open/Closed Principle（开闭原则）

- **定义**：Software entities should be open for extension but closed for modification（对扩展开放、对修改关闭）——加新功能时应能通过"新增"而不是"修改已有代码"完成。
- **识别信号**：每加一个新类型/新分支，就要改动一个已经稳定运行的大 `switch` / `if-else`。
- **反例**：折扣逻辑写成一个巨大的 `if-else`，每加一种折扣就改一次这个函数。
- **正例**：定义 `DiscountStrategy` 接口 + 各折扣策略类；新增折扣只加新类，不改旧代码。
- **何时用**：某个维度已经/预期会**频繁新增变体**时，用多态（接口/继承）替换按类型分发。
- **不要过度**：为一个"未来可能变化"的点预留一堆扩展点是镀金（gold-plating）。等变化真正出现、甚至出现第二次再抽象（配合三次法则）。

## L — Liskov Substitution Principle（里氏替换原则）

- **定义**：Objects of a parent class should be replaceable with objects of a child class without breaking the program（子类对象应能替换父类对象，而不破坏程序）——子类必须遵守父类承诺的行为契约。
- **识别信号**：子类重写父类方法后抛出异常、返回不符合契约的结果；代码里用 `isinstance` / 类型判断去"特判"某个子类。
- **反例**：`Bird` 有 `fly()`，`Penguin` 继承 `Bird` 却在 `fly()` 里抛异常；或 `FixedDeposit`（定期存款）继承 `Account`，但 `withdraw()` 不可用。
- **正例**：把"可提现"抽象成 `WithdrawableAccount` 接口，只有真正能提现的账户（如 `SavingsAccount`）才实现它。
- **何时用**：发现"继承了一个行为并不完全适用的父类"时，把不共用的能力下放到更窄的抽象里。
- **不要过度**：不要因为"看起来像"就继承——继承意味着 is-a 且**行为兼容**；否则用组合或更窄的接口。

## I — Interface Segregation Principle（接口隔离原则）

- **定义**：Clients should not be forced to depend on methods they do not use（不应强迫类实现它用不到的方法）。
- **识别信号**：一个接口很大，多个实现类只能实现其中一部分，其余方法抛 `NotImplementedError` / 留空实现。
- **反例**：一个大 `Worker` 接口同时要求实现 `work()` 和 `eat()`，机器人被迫实现 `eat()`。
- **正例**：拆成 `Workable` 和 `Eatable` 两个小而专的接口，各取所需。
- **何时用**：发现"接口肥了"、实现类出现大量空实现/假实现时，按调用方需求切分接口。
- **不要过度**：把接口切到"每个接口只有一个方法"同样是过度设计。按**使用方**分组，而不是按方法数。

## D — Dependency Inversion Principle（依赖倒置原则）

- **定义**：High-level modules should not depend on low-level modules; both should depend on abstractions（高层模块不依赖低层具体实现，二者都依赖抽象）。
- **识别信号**：业务代码直接 `new` 具体类、直接 import 具体实现；想换一个底层实现（换邮件服务、换数据库）就得改高层业务代码。
- **反例**：`NotificationService` 内部直接创建 `EmailService` / `SmsService` 实例，换实现要改它。
- **正例**：依赖 `NotificationChannel` 抽象，通过构造器注入具体实现，调用方只面向抽象。
- **何时用**：某个依赖**真的会被替换**、或需要 mock 出来做测试时，面向抽象编程。
- **不要过度**：只有一种实现且不会变时，直接 `new` 就够了，别急着上 interface + DI 容器。依赖倒置不一定要依赖注入框架，构造器传参即可。

## 坏味道 → 原则对照表

| 坏味道（code smell） | 优先考虑的原则 |
| --- | --- |
| 一个类同时做多件不相干的事 | SRP |
| 每次加新类型都要改一个大 switch/if-else | OCP（配合 Strategy 等模式） |
| 子类重写后行为与父类契约冲突 | LSP |
| 接口很大、实现类被迫实现用不到的方法 | ISP |
| 高层业务直接依赖/`new` 具体实现、换实现要改高层 | DIP |

> 记住：SOLID 是**诊断工具**。先用它看出问题，再用最小的改动修；不要反过来为了"凑齐 SOLID"去加抽象。
