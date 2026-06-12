# Version Notes

## 1.0.1 - 2026-06-12

### 产品类型体系扩展

- 产品类型从 `{C端, B端, 混合型}` 扩展为 `{B2C, B2B, 内部工具, 平台型, 混合型}`。
- 新增内部工具和平台型追问树、S5 额外覆盖项、视觉交互拷问。
- 统一全项目术语（C端→B2C、B端→B2B）。

### PRD 质量增强

- 新增 `prd-quality-checklist.md`：10 项自检清单 + PRD 反模式防护表 + 需求来源标注规则。
- 铁律新增第 13 条（不替代设计稿）和第 14 条（不遗漏角色视角）。
- `artifact-templates.md` 新增 SMART 目标表格、用户故事列、全局数据需求节、排期建议节、非功能需求表格化。
- `formal-output-rules.md` 新增 SMART 格式、反模糊表述、异常覆盖等 7 条门禁。
- S4 新增膨胀警告（功能点 >5 强制建议划分 MVP/V1.1/V2）。
- S5 新增业务规则门禁增强。

### 输入与分流

- 新增输入要求表（6 个字段）和信息完整度模式分流（快速/引导/概要/膨胀警告）。
- 新增 S1 类型自动推断规则和 PRD 侧重差异表。

### SKILL.md 瘦身重构

- SKILL.md 从 544 行压缩到 184 行（-66%），只保留铁律 + 阶段路由 + 硬门禁，细节下沉到 reference 文件。
- 新建 `workflow-rules.md`：批判框架、输入要求、模式分流、追问规则、闭合模板、联网规则。
- 新建 `s1-s2-type-and-scenario.md`：S1 类型推断 + PRD 差异表 + S2 全套追问树。
- 新建 `s5-type-specific-coverage.md`：B2B / 平台型 / 内部工具额外覆盖项。
- 扩充 `formal-output-rules.md`：原型边界、默认交付规则、S6 收尾规则。
- 扩充 `product-visual-interaction-interrogation.md`：S5.5 闭合输出格式。
- Reference 文件从 6 个增加到 10 个。

## 1.0.0 - 2026-06-09

- Promoted PM Assistant to the first stable release.
- Added explicit version metadata in `SKILL.md`, `agents/openai.yaml`, and `README.md`.
- Moved reference materials under `agents/references/` and updated documentation links to match the new package layout.
- Kept the formal output model focused on `PRD.md`, `modules/`, optional `开发交接.md`, and version-management files.
- Documented the release state so tag `1.0.0` has matching version notes.
