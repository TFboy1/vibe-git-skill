# 安装 Vibe-Git CLI

把 Vibe-Git 想成两个零件：**Skill 是教 Codex 怎么带你协作的说明书，CLI 是真正创建房间、上传文件和读取状态的工具**。只安装其中一个不能完成完整流程。

此仓库的 Git 根目录包含 `vibe-git/` 应用子目录。CLI、Host、网页都从该子目录构建。需要 Node.js 24+、Git，以及用于实际任务的 Codex CLI。首次 `host start` 还会尝试安装并启动 Cloudflare Quick Tunnel。

## 先判断自己是谁

- 要创建房间、邀请别人、收集提案、裁决分歧并发布任务：你是**队长**。
- 要加入别人创建的房间、提交自己的方案、领取任务并开发：你是**队员**。

安装 CLI 本身不决定身份。安装完成后必须回到自己的项目 Git 工作区，再根据身份执行命令；不要在 Vibe-Git 源码目录里误启动房间。

## 第一步：检查电脑环境

在 PowerShell 中逐行运行：

```powershell
node --version
npm.cmd --version
git --version
codex --version
```

Node.js 必须为 24 或更高版本；Git 和 Codex CLI 也必须能输出版本。某一行提示“不是内部或外部命令”时，先安装对应工具并重新打开终端。不要跳过检查，否则后面遇到的错误会很难判断。

## 第二步：安装 Skill

在你平时使用 Codex 的项目工作区执行：

```powershell
npx skills add TFboy1/vibe-git-skill --skill vibe-git
```

安装后，在 Codex 中可以直接说：

> 我第一次使用 Vibe-Git，请先问我是队长还是队员，再按我的身份带我完成安装后的第一步。

## 已有源码目录（PowerShell）

```powershell
Set-Location .\vibe-git  # 从已克隆仓库的 Git 根目录进入应用目录
node --version
npm.cmd --version
git --version
codex --version
npm.cmd ci
npm.cmd run build
npm.cmd link
vibe-git --help
```

执行安装步骤前确认 `package.json` 中的 `bin.vibe-git` 指向 `apps/cli/dist/index.js`。在其他 shell 中把 `npm.cmd` 换成 `npm`。

## 从 GitHub 获取（PowerShell）

```powershell
git clone https://github.com/TFboy1/vibe-git.git
Set-Location .\vibe-git\vibe-git
npm.cmd ci
npm.cmd run build
npm.cmd link
vibe-git --help
```

安装后在**自己的项目工作区**运行队长或成员命令。全局链接依赖这个源码目录；不要在使用期间移动或删除它。若不想建立全局链接，在任意工作区用 `node <应用目录的绝对路径>/apps/cli/dist/index.js <参数>` 调用，不能把相对路径误解为当前项目下的文件。

若 `vibe-git --help` 不可用，检查 `npm link` 是否成功、npm 全局 bin 是否在 PATH，再试绝对路径形式。不要用 `--version` 验证；当前 CLI 支持 `--help`，未实现 `--version`。

## 第四步：安装后立刻完成一次最小闭环

### 如果你是队长

进入你要协作的项目目录：

```powershell
Set-Location C:\path\to\your-project
vibe-git host start
vibe-git open
```

`host start` 成功后会显示给队员使用的加入命令。复制完整命令，私下发给队员；不要把它放进 Git、Issue 或公开聊天。`open` 只用于打开网页面板，不是给队员加入的链接。

### 如果你是队员

进入你自己的同一个项目目录，把队长发来的 URL 放进命令：

```powershell
Set-Location C:\path\to\your-project
vibe-git connect "<队长给你的完整加入 URL>"
vibe-git status
vibe-git open
```

连接成功后，告诉 Codex：

> 我是队员。请阅读当前项目，帮我起草一份提案；等我确认内容后，再用 `vibe-git plan submit` 上传，不要直接修改别人的提案。

## Skill 可以代用户完成的事情

安装 Skill 后，不必记住每个命令，可以直接提出明确目标：

- “帮我把这个项目的目标、现状、方案和验收标准整理成提案，确认后上传。”
- “我发现登录流程要改，请生成需求变更单，确认后提交内部 PR。”
- “帮我连接 Vibe-Git 的专用 Codex 审核池。”
- “我是队长，帮我查看当前提案并开始对齐。”
- “我是队员，帮我拉取任务、补充执行细节并开始任务。”

涉及上传、启动房间、连接节点、绑定账号或发布任务时，Skill 会先确认身份、工作区和目标 ID；用户确认后才执行，并且只在 CLI 成功回执后报告成功。

更新已安装源码时，先确认源码工作区没有需要保留的未提交修改，再按用户请求更新 Git 状态，重新执行 `npm.cmd ci`、`npm.cmd run build`、`npm.cmd link`。不要在更新 CLI 时随手停止已有 Host 或轮换邀请。
