# 协作模式示例

> 这些是参考示例，协调器可根据实际情况自由组合或创新

## 示例1：单专家模式

**适用场景**：简单任务，单一专家可独立完成

**调用示例**：
```
Task(subagent_type="code-vanguard-phoenix", prompt="设计架构...")
Task(subagent_type="code-vanguard-viper", prompt="实现功能...")
Task(subagent_type="code-vanguard-ghost", prompt="测试代码...")
Task(subagent_type="code-vanguard-oracle", prompt="调研技术...")
```

## 示例2：链式协作（设计→实现→测试）

**适用场景**：完整项目开发，需要多阶段协作

**调用示例**：
```
Step 1: Task(subagent_type="code-vanguard-phoenix", prompt="设计系统架构...")
        ↓ 获取架构设计文档

Step 2: Task(subagent_type="code-vanguard-viper", prompt="基于架构设计实现代码...")
        ↓ 获取实现代码

Step 3: Task(subagent_type="code-vanguard-ghost", prompt="测试实现代码...")
        ↓ 获取测试报告
```

## 示例3：并行协作

**适用场景**：多个独立模块同时开发

**调用示例**：
```
同时调用多个 Viper：
- Task(subagent_type="code-vanguard-viper", prompt="实现用户模块...")
- Task(subagent_type="code-vanguard-viper", prompt="实现订单模块...")
- Task(subagent_type="code-vanguard-viper", prompt="实现支付模块...")
```

## 示例4：顾问式协作

**适用场景**：主专家执行 + 顾问专家复核

**调用示例**：
```
Step 1: Task(subagent_type="code-vanguard-viper", prompt="实现算法...")
Step 2: Task(subagent_type="code-vanguard-oracle", prompt="复核算法方案...")
Step 3: 如有问题，调用 Viper 修正
```

## 示例5：动态调整

**场景**：执行中发现新问题

**应对**：
- 原计划单专家，发现需要架构设计 → 先调用 Phoenix
- 原计划链式，某环节简单 → 跳过或合并
- 发现技术难点 → 引入 Oracle 顾问
- 遇到复杂问题 → 使用 AskUserQuestion 与用户确认

---

**关键**：以上都是示例，协调器应保持灵活性，不被预设限制
