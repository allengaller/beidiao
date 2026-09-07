# 背调 beidiao

求职前的**反向背调**与职业发展研究技能：用公开信息交叉验证目标公司、团队、岗位与行业，输出风险分级报告（🟢🟡🔴⚪）。只依赖公开渠道，绝不绕过登录墙或付费墙。

English: a pre-offer reverse background-check and career-research skill. It cross-verifies target companies, teams, roles, and industries from public information and produces a risk-graded report. Public channels only — it never bypasses login or paywalls.

## 它做什么

| 输入 | 模式 | 跑哪些模块 |
|------|------|-----------|
| 公司名 | 公司背调（默认） | A 公司尽调风险 + B 口碑薪酬 |
| 公司名 + 岗位 | offer 全套评估 | A + B + C（团队级）+ D（行业） |
| 面试官/老板姓名 + 公司 | 人背调 | C 仅限（严守隐私红线） |
| 行业 / 职位名 | 职业发展研究 | D |
| 公司名 + "追踪/盯" | 长期监控 | 一次体检 + firecrawl_monitor 建监控 |

四大模块：

- **A 公司尽调与风险**：工商基础、司法风险（劳动仲裁/被执行/失信）、裁员欠薪、融资轨迹、参保人数与签约主体核验、上市/退市信号
- **B 口碑与薪酬**：看准/职友/知乎、Glassdoor、Blind、小红书/黑猫投诉、levels.fyi/OfferShow，含刷评识别
- **C 面试官与团队**：GitHub 活跃度、技术影响力、职业履历、岗位真实性（马甲岗/JD 红线词/培训贷陷阱）——仅限公开职业足迹
- **D 行业与职业发展**：行业趋势、竞品格局、JD 技能需求提炼、职级对标、长期追踪

报告结构：结论速览表 → 总体判断（倾向 + 置信度）→ 分模块明细 → 风险清单与面试验证问题 → 信息空白清单 → 来源清单，并附免责声明。

## 依赖与工具链

- 首选 **firecrawl MCP**（search / scrape / crawl / map / agent / monitor）；未授权或限流时自动降级 WebSearch / WebFetch
- 辅助 CLI：`gh api`（公司 GitHub 组织活跃度）、`curl` + `jq`
- 无需任何凭证或账号；有登录墙/付费墙的数据（天眼查、脉脉、领英站内全文）通过搜索引擎索引摘要与新闻转述获取，并标注来源层级

## 合规红线

- 只查公开信息，不绕登录墙/付费墙，不绕验证码
- 人背调只查职业公开足迹（工作经历、公开发言、开源贡献），不碰婚育/健康/家庭住址等隐私，不拼凑"个人档案"
- 报告必带免责声明；签 offer、辞职等重大决策提示通过官方渠道二次核实

## 安装

```bash
qoder plugin install beidiao
```

或从本地目录安装：

```bash
qoder plugin install --scope local /path/to/beidiao
```

安装后用 `/beidiao <公司名 / 面试官姓名+公司 / 行业或职位>` 触发。

## 来源与出处

- **来源**：原创技能，作者 Allen Galler，使用 Qoder CLI 创建并打包
- **Logo**：自制 SVG（assets/avatar.svg），无第三方素材
- **包含文件**：`skills/beidiao/SKILL.md`、`skills/beidiao/references/data-sources.md`（数据源矩阵与查询模板）、`skills/beidiao/references/report-template.md`（报告模板与评级规则）
- **省略文件**：无

## 验证

- 通过 qoder-create-plugin 离线校验器 `validate_qoder_plugin.py`（manifest、组件路径、SKILL.md frontmatter）
