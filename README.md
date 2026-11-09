# victor-skill

Victor 的个人 Codex Skill：让 AI 结合他的背景、说话方式和偏好来协助学习、科研、写作、笔记整理和生活规划。技能标识与仓库同名，可用 `$victor-skill` 调用。

## 它能做什么

- 结合个人背景给建议：课程与 AI 零基础学习、升学与工具方案比较、论文报告写作、笔记整理，以及购物、出行等生活事务。
- 按 Victor 的表达习惯理解请求：消息常很短、口语化、分多条迭代，技能会按字面意图合并处理。
- 固定回答偏好：高效为主兼顾自然、术语先解释配例子、先给结论、涉及选择先比较方案再由他决定、不编造事实。

## 结构

```text
skills/victor-skill/
├── SKILL.md                          入口：默认偏好与参考文件路由
├── agents/openai.yaml                UI 名称、简介、默认提示、调用策略
└── references/
    ├── victor-profile.md             个人资料（事实与待确认项）
    ├── how-to-respond.md             说话方式、高频问题、回答方式与边界
    ├── writing.md                    写作与润色规范
    ├── research-and-technical.md     科研与技术文档
    └── notes-and-planning.md         笔记整理与任务规划
```

`SKILL.md` 只保留共用偏好和路由；具体规则和资料放在 `references/`，按任务加载对应文件。

## 安装

技能目录是标准可安装布局。用 GitHub CLI 安装到当前用户（全局，所有项目可用）：

```sh
gh skill install myyylnee/victor-skill victor-skill --agent codex --scope user
```

或手动复制整个技能文件夹到 Codex 用户级技能目录：

```sh
skill_root="${CODEX_HOME:-$HOME/.codex}/skills"
mkdir -p "$skill_root"
cp -R skills/victor-skill "$skill_root/"
```

装好后在能识别新技能的会话里用 `$victor-skill` 调用。要在每个会话默认生效，可在 `~/.codex/AGENTS.md` 里加一条指向本技能的说明。技能结构见 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 更新与隐私

新增或修改偏好时，事实类写入 `references/victor-profile.md`，互动规则写入 `references/how-to-respond.md`，并更新记录日期。每次任务里的明确要求优先于技能默认规则。

仓库包含 Victor 的个人资料，当前为公开可见。技能不收录任何凭据或密码、银行卡号、身份证号、精确住址等敏感信息；如需保护隐私，可把仓库改为 private。
