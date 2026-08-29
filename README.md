# YouMind Skill 上传器

把已经完成的 Agent Skill 整理并上传到 YouMind：自动生成后台文案与配图、填写创建表单，并校验最终发布结果。

这个 Skill 只在你明确要求「上传到 YouMind」「发布到 YouMind」或「更新 YouMind 上的 Skill」时运行。个人自用、日常修改、测试或仅推送 GitHub 的 Skill，不会被自动发布到 YouMind。

## ✨ 特点

- **面向现成 Skill**：读取已有的 `SKILL.md`、原始提示词、必要 references 和素材，不重新设计 Skill 的核心能力。
- **指令自动展开**：把分散在本地文件中的运行规则整理成 YouMind 可直接使用的完整指令，排除测试记录、Git 元数据和维护说明。
- **严格保留原文**：用户要求提示词原封不动时，保留原有文字、标点、占位符和换行。
- **只填写真实字段**：仅处理头像、技能名称、副标题、指令、输入提示、展示和描述，不虚构价格、标签、版本等后台不存在的字段。
- **自动生成配图**：调用当前 Agent 已有的生图能力制作方形头像和横版展示图，不绑定特定模型、API、接口或密钥。
- **自动操作后台**：使用当前 Agent 的浏览器控制能力填写 YouMind 表单，遵守登录、上传、确认和提交规则。
- **避免重复发布**：提交后先验证成功状态和最终地址；结果不明确时只检查，不盲目再次创建。

## 🚀 最简单：让 AI 帮你安装

如果你使用 Codex、Claude Code 或其他支持 Agent Skill 的工具，可以直接把下面这句话发给它：

> 请把这个 Skill 安装到我的 Agent：`https://github.com/pamelaaaaa1218/youmind-skill-uploader`。以后我明确要求把某个 Skill 上传到 YouMind 时，就使用它完成文案、配图、后台填写和发布校验。

也可以手动克隆到 Codex 用户技能目录：

```bash
git clone https://github.com/pamelaaaaa1218/youmind-skill-uploader.git \
  ~/.codex/skills/youmind-skill-uploader
```

安装后重新打开 Agent，让它读取 [`SKILL.md`](SKILL.md) 即可使用。

## 用法

上传一个现成 Skill：

```text
使用 $youmind-skill-uploader，把 /path/to/my-skill 上传到 YouMind。
```

从 GitHub 仓库上传：

```text
使用 $youmind-skill-uploader，把这个 Skill 上传到 YouMind：
https://github.com/owner/repository
```

只整理资料、由自己上传：

```text
使用 $youmind-skill-uploader，整理这个 Skill 的 YouMind 上架资料，我自己上传，不要提交。
```

## 后台内容

| 内容 | 默认要求 |
|---|---|
| 头像 | 1:1，建议 1024 × 1024 |
| 技能名称 | 不超过 40 个字符 |
| 副标题 | 不超过 60 个字符 |
| 指令 | 从现有 Skill 编译成自包含指令 |
| 输入提示 | 不超过 200 个字符 |
| 展示 | 最多 4 项，首张建议 16:9、1600 × 900 |
| 描述 | 说明功能、输入、输出、场景和差异点 |

YouMind 实时后台的字段、尺寸和校验规则优先于仓库中的默认规范。

## 工作流程

1. 确认用户是否明确要求上传、发布、更新或仅准备资料。
2. 读取指定 Skill 的 `SKILL.md`、必要 references 和现有素材。
3. 编译自包含指令，并校验受保护提示词是否保持原样。
4. 生成技能名称、副标题、输入提示、描述等后台文案。
5. 调用当前 Agent 的生图能力制作头像和展示图。
6. 检查字符数、图片尺寸、可读性和重复发布风险。
7. 在获得相应授权后填写并提交 YouMind 表单。
8. 验证发布状态、页面标题和最终 URL，输出上传回执。

## 使用边界

- 「帮我做一个 Skill」「帮我测试 Skill」「推到 GitHub」不会触发 YouMind 上传。
- 「整理 YouMind 上架资料，我自己上传」只生成资料，不操作后台或提交。
- 「上传到 YouMind」「发布到 YouMind」才进入后台填写与发布流程。
- 登录、验证码、法律声明或浏览器能力要求即时确认时，会暂停并交给用户处理或确认。
- 没有可用生图能力时，仍会完成文案和可复现的图片提示词，但不会拿占位图冒充最终素材。

## 📁 项目结构

```text
youmind-skill-uploader/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── image-assets.md
│   ├── output-template.md
│   ├── platform-fields.md
│   ├── source-conversion.md
│   └── upload-workflow.md
└── evals/
    └── baseline-findings.md
```

核心触发条件和执行流程见 [`SKILL.md`](SKILL.md)，后台字段与图片尺寸分别见 [`references/platform-fields.md`](references/platform-fields.md) 和 [`references/image-assets.md`](references/image-assets.md)。
