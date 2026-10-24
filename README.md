# AI 味设计评审 Skill

**可分享的指令型 Skill｜包版本 0.2.1｜评分草案 v0.2｜MIT License**

用于产品界面、截图和内容封面的 AI 味试评。把感受落到表达贡献、注意力分配、构成关系与视觉平衡上，输出暂评分、具体证据、影响、修改方向及待判项。它不判断作品是否由 AI 生成，也不默认极简风格更好。

本包根据阿橙与助手共同推敲的评分草案及截图案例整理；需要能查看图片、读取 Markdown 引用文件的模型环境。不需要 API 密钥、联网服务、执行脚本或私人设计技能。

## 怎么用

### 1. 让 Codex 帮你安装（推荐）

把下面这段话复制给 Codex：

```text
请使用 $skill-installer 安装 GitHub 仓库
hygge20211-prog/ai-flavor-review 根目录的 Skill。

仓库内路径为 .，安装名为 ai-flavor-review。
请保留全部 references 文件和案例图片。
```

这个仓库的 `SKILL.md` 位于根目录，所以安装路径为 `.`，并明确安装名为 `ai-flavor-review`。安装器会下载完整的技能文件夹。安装完成后，在下一轮对话中使用；如果没有识别到新技能，重启 Codex。[OpenAI 官方安装说明](https://learn.chatgpt.com/docs/build-skills#install-curated-skills-for-local-use)

### 2. 上传截图并开始评审

附上待评截图，把任务和状态换成你自己的情况，再发送：

```text
请使用 $ai-flavor-review 评估这张界面的 AI 味。

用户任务：查看本月预算剩余。
当前状态：正常使用。
评估范围：截图中的完整首屏。

请给出 0–10 的暂评分、具体证据、影响、修改方向和待判项。
```

分数越高，表示本框架下的问题越明显。输出会结合表达贡献、注意力分配、构成关系与视觉平衡解释原因，并区分已见证据、判断推测和无法判断的部分。

比较两个页面时，附上两张图并发送：

```text
请使用 $ai-flavor-review 比较这两个页面。
页面一用于浏览当月流水，页面二用于管理周期计划。
分别评分，并说明哪些分差有证据、哪些来自任务差异。
```

只有截图也可以开始：请它先做视觉暂评，标明任务假设与待判项。没有背景的信息不会自动算作没有问题。

### 手动安装

1. 点击本仓库的 **Code → Download ZIP**，或直接[下载仓库 ZIP](https://github.com/hygge20211-prog/ai-flavor-review/archive/refs/heads/main.zip)。
2. 解压后，将包含 `SKILL.md` 的这一层文件夹命名为 `ai-flavor-review`，保留 `agents/`、`references/` 等全部内容。
3. 所有项目都要使用时，放入个人技能目录 `~/.agents/skills/ai-flavor-review/`；只给一个项目使用时，放入该项目的 `.agents/skills/ai-flavor-review/`。`~` 代表用户主目录。
4. 确认 `SKILL.md` 直接位于上述目录中，再在下一轮对话使用 `$ai-flavor-review`。若未被识别，重启 Codex。

这些是 Codex 的本地技能目录；其他支持 Agent Skills 的工具，按自身安装说明放置完整文件夹。`agents/openai.yaml` 是可选的 OpenAI 界面元数据，其他宿主可忽略。[OpenAI 官方技能目录说明](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills)

### 只用 ChatGPT 网页版怎么办

上面的本地目录步骤面向 Codex。只把 GitHub 链接贴进聊天，不代表已安装这个 Skill。

如果当前对话支持文件和图片上传，可以先下载仓库，将 `SKILL.md`、`references/rubric.md`、`references/calibration-cases.md`、`references/output-format.md` 作为评审说明上传，并附上待评截图；需要对照案例时也提供相应案例图片。请模型先读取这些说明，再进行评审。这是按文档使用的方式，不等同于持久安装。

## 包里有什么

```text
ai-flavor-review/
├── LICENSE
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── rubric.md
│   ├── calibration-cases.md
│   ├── output-format.md
│   └── images/                 7 张案例及标注截图
└── README.md
```

- [技能入口](SKILL.md)：触发范围、评审流程、判断边界和引用路由。
- [评分标准](references/rubric.md)：三维标准、对齐/边距/重心、证据与未知、根因去重、0–10 粗档及校准方式。
- [校准案例](references/calibration-cases.md)：4 个带参考分的界面、1 组封面对照，以及正例和边界案例。
- [输出格式](references/output-format.md)：简评、完整评审、双图比较、调分规则和一份完整示例。
- [MIT 许可证](LICENSE)：版权与许可声明。

## 上传 GitHub

1. 在 GitHub 新建公开仓库，建议命名 `ai-flavor-review`，简介可写“AI 味设计评审 Skill：基于具体证据检查表达、层级、对齐、边距与视觉平衡”。本包已包含 README 和 LICENSE，无需再生成同名文件。
2. 解压 GitHub 版 ZIP，将 `README.md`、`LICENSE`、`SKILL.md`、`agents/`、`references/` 一起上传到仓库根目录，保留子目录。ZIP 内就是这层文件，无额外包装目录。
3. 提交说明可填 `Publish AI flavor review skill v0.2.1`。提交后检查首页说明、案例图片与内部链接能否正常打开，再分享仓库链接。

GitHub 版 ZIP 用于解压后上传文件；GitHub 网页上传不会自动展开 ZIP。后续通过仓库维护评分标准、案例和反馈，并按实际修改更新版本。

## 分享与后续维护

直接分享整个文件夹或 ZIP。接收者需安装/载入，并自行提供待评图片。把 Skill 放入本地目录或 GitHub 不会自动公开到 ChatGPT/Codex 的公共目录；本包目前只是可分享文件，不含公开插件发布配置。

案例分数是上下文中的参照，不能机械照抄。更新标准时用相同材料重新比较，保留分歧与调分理由，并在 GitHub 维护版本、收集案例和反馈。

## 许可证

本项目采用 [MIT License](LICENSE)，版权署名为 **2026 阿橙**。允许使用、修改和分发，需保留版权及许可声明；完整条款以 LICENSE 为准。

案例截图中的第三方商标、标志和其他第三方素材，其既有权利不因本项目许可证而改变。

本包可在阅读结构、引用资源和实际评审中继续验证；当前不宣称已完成大样本、跨模型的一致性校准。
