# Vibe-Git Skill

给第一次使用 Vibe-Git 的人准备的 Codex 协作助手。它会先确认你是队长还是队员，再带你安装、连接房间、上传提案、领取任务、提交内部需求变更，并按需连接专用 Codex 审核池。

## Install

```powershell
npx skills add TFboy1/vibe-git-skill --skill vibe-git
```

安装后，打开 Codex，直接说：

> 我第一次使用 Vibe-Git，请先问我是队长还是队员，再按我的身份带我完成第一步。

Skill 会帮助你：

- 队长启动房间、发送安全的加入命令、发起对齐、裁决冲突并发布任务；
- 队员连接房间、整理并上传 UTF-8 Markdown 提案、拉取任务和确认完成；
- 把开发中的新想法整理成 Vibe-Git 内部需求变更单，并在你确认后执行 `pr submit`；
- 通过 `codex bind` 连接每个节点独立的专用 Codex 审核池；
- 遇到安装、工作区、连接或状态问题时，先检查 `status` 和 `logs`，不假装操作成功。

完整教程：<https://tfboy1.github.io/vibe-git/>

详细安装参考见 [`skills/vibe-git/references/install.md`](skills/vibe-git/references/install.md)，命令和角色流程见 [`skills/vibe-git/references/workflows.md`](skills/vibe-git/references/workflows.md)。Skill 定义见 [`skills/vibe-git/SKILL.md`](skills/vibe-git/SKILL.md)。
