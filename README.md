# /ST: SillyTavern 集成调度 Skill

> Claude Code / SillyTavern 全栈任务的统一入口与调度中枢。

## 简介

`/ST` 是一个 Claude Code Skill，用于响应所有与 SillyTavern（酒馆）相关的请求。它本身不承载具体实现，而是作为**唯一入口**，自动识别用户意图并调度到对应的子 Skill：

- 同人沙盒角色卡与 BP 战斗
- 完整角色卡写作方法论
- 写卡知识库与自查清单
- 通用叙事/战斗思维链模板
- 酒馆助手前端车间
- Web 项目 SillyTavern 集成
- 预设制作与模板改造

## 安装

### 方式一：Git 克隆

```bash
# macOS / Linux
$ git clone https://github.com/KATOUIV/ST-writer.git ~/.claude/skills/ST

# Windows
> git clone https://github.com/KATOUIV/ST-writer.git %USERPROFILE%\.claude\skills\ST
```

### 方式二：ZIP 导入（推荐）

Release 中提供了打包好的 Skill 合集：

- **文件**：`sillytavern角色卡skills[解压让cc从zip导入即可].zip`
- **仓库**：https://github.com/KATOUIV/ST-writer/

下载后解压到 Claude Code 的 skills 目录，即可通过 `/ST` 及所有子 Skill 触发。

### 目录结构

解压或克隆后应包含：

```text
.claude/skills/ST/
├── SKILL.md
├── README.md
└── references/
    └── skill-index.md
```

> 注意：`/ST` 调度时会引用其他 7 个子 Skill。ZIP 包内已包含全部子 Skill，建议直接整体导入。

## 使用方式

在 Claude Code 中直接描述你的 SillyTavern 相关需求即可触发 `/ST`，例如：

- "帮我写一张鬼灭同人沙盒卡"
- "给角色卡加一个 BP 战斗状态栏"
- "按晴空妈妈的教程写人设"
- "在 React 项目里集成 SillyTavern 的 lorebook"
- "做一个缝合预设"

`/ST` 会首先读取 `references/skill-index.md`，然后根据意图显式调用一个或多个子 Skill，并整合输出。

## 子 Skill 总览

| 子 Skill | 定位 | 关键词 |
|---|---|---|
| `st-鬼灭` | 同人沙盒角色卡精简流程 | 同人、沙盒、BP、状态栏、D0、蓝灯、绿灯、世界书 |
| `st-三明月` | 完整角色卡写作方法论 | 写卡、人设、调色盘、三面性、核心人格层、意象、WTC |
| `st-知识库` | 写卡知识库与教程 | 晴空妈妈、写卡教室、自查、一键写卡器、世界书配置 |
| `st-通用` | 叙事/战斗思维链模板 | narrative combat、story_driver、combat_driver、十步战斗法 |
| `st-车间` | 酒馆助手前端与脚本 | 前端、脚本、MVU、Vue、Webpack、状态栏 UI、流式楼层 |
| `st-前端` | Web 项目自动集成 | React、lorebook、AI chat、自动安装 |
| `st-预设` | 预设制作与模板改造 | preset、破甲、防抢话、COT、正则美化、模块化提示词 |

## 调度示例

| 用户请求 | 调用顺序 |
|---|---|
| 写张有战斗系统的同人卡 | `st-鬼灭` → `st-三明月` → `st-知识库` → `st-通用` |
| 帮我写人设再加个状态栏前端 | `st-三明月` → `st-知识库` → `st-车间` |
| 把这份小说设定做成可玩的战斗卡 | `st-鬼灭` → `st-通用` → `st-三明月` |
| 在 React 项目里集成 SillyTavern 的 lorebook | `st-前端` → `st-车间` |
| 做预设 / 缝合预设 / 改造预设模板 | `st-预设` |

详细决策树与冲突仲裁规则见 `SKILL.md`。

## 依赖

- Claude Code（或其他兼容的 Skill 运行环境）
- 同一 skills 目录下需安装 `/ST` 调度的 7 个子 Skill（ZIP 包内已包含）

## 贡献

欢迎提交 Issue 或 Pull Request。新增子 Skill 或调整调度顺序时，请同步更新：

1. `SKILL.md` 中的子 Skill 总览、决策树、检查清单
2. `references/skill-index.md` 中的资源索引与冲突仲裁顺序

## 许可证

MIT
