# Vibe-Git Skill

给第一次使用 Vibe-Git 的人准备的 Agent 协作助手。用户只需先安装 Skill 并明确要求自动安装；它会先检查 CLI，缺失时执行 `npm install -g @vibe-git/vibe-git`，再确认用户是队长还是队员，带用户连接房间、上传提案、领取任务、提交内部需求变更，并按需连接专用 Codex 审核池。

## Install

```powershell
npx skills add TFboy1/vibe-git-skill --skill vibe-git
```

安装后，打开 Codex，直接说：

> 我第一次使用 Vibe-Git，请先问我是队长还是队员，再按我的身份带我完成第一步。

也可以直接对支持 Agent Skill 和终端操作的智能体说：

> 请自动安装并配置 Vibe-Git；如果 CLI 没安装就执行 `npm install -g @vibe-git/vibe-git`，安装成功后先问我是队长还是队员，再带我开始。

当前教程面向 Trae、Codex、WorkBuddy、Coder、Claude Code 和 Antigravity。不同智能体的入口名称可能不同，但核心流程相同：先安装 Skill，再让 Skill 检查并安装 CLI。

Skill 会帮助你：

- 队长启动房间、发送安全的加入命令、发起对齐、裁决冲突并发布任务；
- 队员连接房间、整理并上传 UTF-8 Markdown 提案、拉取任务和确认完成；
- 把开发中的新想法整理成 Vibe-Git 内部需求变更单，并在你确认后执行 `pr submit`；
- 通过 `codex bind` 连接每个节点独立的专用 Codex 审核池；
- 遇到安装、工作区、连接或状态问题时，先检查 `status` 和 `logs`，不假装操作成功。

完整教程：<https://tfboy1.github.io/vibe-git/>

详细安装参考见 [`skills/vibe-git/references/install.md`](skills/vibe-git/references/install.md)，命令和角色流程见 [`skills/vibe-git/references/workflows.md`](skills/vibe-git/references/workflows.md)。Skill 定义见 [`skills/vibe-git/SKILL.md`](skills/vibe-git/SKILL.md)。
