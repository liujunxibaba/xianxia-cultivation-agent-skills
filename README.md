# Xianxia Agent Skills｜tiktok/抖音短剧 仙侠创作技能合集

一套中文仙侠、修仙、玄幻及古偶奇幻创作 Skills，适用于 Codex、Kimi、Qoder，以及支持自定义指令、项目规则、知识文件或文件上传的其他 AI Agent。覆盖从世界观、故事、剧本到分镜、AI 视频提示词、接镜和声音设计的完整流程。

A platform-neutral collection of Chinese-language agent skills for xianxia, cultivation fantasy, eastern fantasy, and costume fantasy production—from worldbuilding and screenwriting to storyboards, AI-video prompting, continuity, and sound design.

核心能力全部由 Markdown 表达，不依赖特定模型、私有 API、MCP、操作系统或编程语言。平台专属元数据只是可选适配层，不影响其他环境使用。

## Skills

| Skill | 用途 |
| --- | --- |
| `xianxia-worldbuilding` | 世界规则、境界、宗门、功法、法宝、因果、飞升与轮回 |
| `xianxia-story-development` | 项目档案、人物关系、主线、分集大纲与节奏方案 |
| `xianxia-script-doctor` | 会诊结构、道心、升级爽点、战力、法术因果与伏笔 |
| `xianxia-script-drafting` | 撰写或续写可拍摄的完整剧本、单集与单场 |
| `xianxia-dialogue-polish` | 精修古风对白、称谓、誓言、咒诀、旁白与语言指纹 |
| `xianxia-asset-bible` | 建立角色、服装、场景、法宝、灵兽和灵力色谱资产圣经 |
| `xianxia-storyboard-director` | 把定稿剧本转成导演方案与可执行九列分镜 |
| `xianxia-video-prompt` | 生成多平台 AI 视频提示词、素材锚定与负面约束 |
| `xianxia-video-continuity` | 分析已生成视频并生成保持连续性的下一段提示词 |
| `xianxia-sound-design` | 设计 BGM、环境声、法术音色、声音桥与 Cue Sheet |

## 三种使用模式

### 1. 原生 Skills 模式

如果你的 Agent 支持文件夹式 Skills，将需要的 `skills/xianxia-*` 目录复制到该平台规定的 Skills 目录。每个目录都是一个独立 Skill，入口为 `SKILL.md`。

以 Codex 为例：

克隆仓库：

```powershell
git clone https://github.com/YOUR-USERNAME/xianxia-agent-skills.git
```

将全部 Skills 安装到 Codex：

```powershell
Copy-Item -Recurse .\xianxia-agent-skills\skills\xianxia-* "$env:USERPROFILE\.codex\skills\"
```

macOS / Linux：

```bash
cp -R ./xianxia-agent-skills/skills/xianxia-* ~/.codex/skills/
```

也可以只复制需要的单个 Skill 目录。平台实际安装位置可能随版本变化，请以该平台的 Skills 或自定义 Agent 文档为准。

### 2. 项目规则 / 自定义 Agent 模式

适合 Kimi、Qoder 或其他支持项目规则、自定义智能体、系统提示词、知识库的环境：

1. 把目标 Skill 的 `SKILL.md` 设为主指令或项目规则；
2. 把同目录的 `references/` 一并上传为知识文件；
3. 要求 Agent 在执行前按 `SKILL.md` 的说明读取相关引用文件；
4. 用 Skill 名称加具体任务发起请求。

通用启动指令：

```text
你将使用随附的 <skill-name> 文件夹完成任务。
先读取 SKILL.md，把它作为本任务的最高优先级工作流；
再按 SKILL.md 的要求读取 references/ 中与当前任务有关的文件。
不要虚构未提供的资料，不要跳过输入核对和输出检查。

我的任务：<在这里填写任务>
```

### 3. 普通聊天 / 文件上传模式

如果平台没有 Skills 或项目规则功能，直接上传目标 Skill 文件夹（或压缩包），再发送上面的通用启动指令。若平台只能接收单文件，可依次粘贴 `SKILL.md` 和它点名要求读取的 `references/` 文件，并明确标出文件名。

## 使用示例

```text
请用 xianxia-worldbuilding 帮我设计一个“飞升会夺走记忆”的修炼世界。

请用 xianxia-script-doctor 会诊这份仙侠短剧大纲，重点检查战力和法术因果。

请用 xianxia-storyboard-director 把这场渡劫戏拆成可执行分镜。

请用 xianxia-video-prompt 把分镜转换成 Kling 可执行的视频提示词。
```

每个 Skill 都可以单独使用。需要完整流程时，推荐顺序：

```text
worldbuilding → story-development → script-doctor → script-drafting
→ dialogue-polish → asset-bible → storyboard-director
→ video-prompt → video-continuity → sound-design
```

## 目录结构

```text
skills/<skill-name>/
├── SKILL.md
├── agents/openai.yaml  # 可选的 Codex/OpenAI UI 适配层
├── references/   # 按需加载的规则与模板
├── scripts/      # 可选的确定性工具
└── assets/       # 可选的输出素材
```

## 跨平台兼容原则

- `SKILL.md` 是唯一核心入口，使用通用 Markdown 和简单 YAML frontmatter；
- `references/` 只存放可按需读取的领域规则，不要求平台拥有专用工具；
- `agents/openai.yaml` 是可选 UI 元数据，非 OpenAI 平台可以忽略；
- 不在核心 Skill 中写死用户目录、系统命令、模型名称或平台 API；
- 平台没有自动触发能力时，通过“通用启动指令”显式调用；
- 平台无法读取多个文件时，需要手动提供相关引用文件，因此不能保证真正意义上的零配置。

更详细的接入说明见 [COMPATIBILITY.md](COMPATIBILITY.md)。

## 贡献

欢迎提交 Issue 或 Pull Request。修改时请保持：

- Skill 目录名与 `SKILL.md` 中的 `name` 一致；
- YAML frontmatter 只包含 `name` 和 `description`；
- 核心流程放在 `SKILL.md`，详细资料放在 `references/`；
- 不提交密钥、用户数据、未获授权的剧本、图片、字体或其他版权材料；
- 新增或修改 Skill 后完成结构校验和至少一次真实任务测试。

## License

MIT License。详见 [LICENSE](LICENSE)。
