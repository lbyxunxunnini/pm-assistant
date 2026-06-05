# Memory Rules

本文件定义 PM Assistant 的轻量记忆机制。它只用于断点恢复和版本索引，不替代正式产品文档。

## 1. 记忆边界

澄清阶段只创建和更新：

```text
pm-memory/
└── PROJECT-STATE.md
```

`PROJECT-STATE.md` 只保留最新 checkpoint，不保留历史，不记录完整问答，不记录完整决策链。

## 2. PROJECT-STATE.md 模板

```markdown
# Project State

## 产品名

## 当前阶段

## 当前状态
- 澄清中 / 准备建版 / 正式输出中：

## 产品类型
- C 端 / B 端 / 混合 / 未确认：

## 一句话产品摘要

## 已确认核心判断
- 最多 5 条：

## 当前版本
- 未建版 / <version>：

## 下一步
```

## 3. 澄清阶段 Checkpoint 字段

澄清阶段 checkpoint 包含：

- 产品名
- 当前阶段
- 当前状态：澄清中 / 准备建版 / 正式输出中
- 产品类型：C 端 / B 端 / 混合 / 未确认
- 一句话产品摘要
- 已确认核心判断，最多 5 条
- 当前版本：未建版或版本号
- 下一步

## 4. 更新规则

- 产品名确认后初始化 `PROJECT-STATE.md`。
- 每个阶段闭合时覆盖更新最新 checkpoint。
- 阶段内普通问答不写文件。
- 如果用户推翻方向，直接覆盖为新状态。
- 进入正式版本阶段后，可补充 `pm-memory/PROGRESS.md` 和 `pm-memory/OUTPUTS.md`，但仍只做状态索引。

## 5. 正式版本阶段记忆结构

```text
pm-memory/
├── PROJECT-STATE.md
├── PROGRESS.md
└── OUTPUTS.md
```

## 6. PROGRESS.md 作用

`PROGRESS.md` 只记录当前正式输出阶段的进度索引，例如：

- 当前版本号
- 正在生成或修订的正式产物
- S7 写入状态
- S8 一致性审查状态
- 下一步动作

不得把完整 PRD、完整模块详设或完整问答写入 `PROGRESS.md`。

## 7. OUTPUTS.md 作用

`OUTPUTS.md` 只记录版本化产物索引，例如：

- 版本号
- 产物路径
- 产物类型
- 创建 / 更新状态
- 是否通过 S8 一致性审查

正式内容必须保存在 `pm-output/iterations/<version>/`，不得沉淀到 `pm-memory/`。
