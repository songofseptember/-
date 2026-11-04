# 飞书 CLI 云端技能集

此仓库包含 **28 个飞书 CLI Skill**，位于 `.agents/skills/`，包括完整的 `references`、`scripts`、`assets` 等配套文件。

## 技能目录

| 功能 | Skill |
| --- | --- |
| 配置、登录与权限 | `lark-shared` |
| 云文档、云盘与原生 Markdown | `lark-doc`、`lark-drive`、`lark-markdown` |
| 多维表格、电子表格与幻灯片 | `lark-base`、`lark-sheets`、`lark-slides` |
| 知识库与画板 | `lark-wiki`、`lark-whiteboard` |
| 日历、任务与通讯录 | `lark-calendar`、`lark-task`、`lark-contact` |
| 消息与邮件 | `lark-im`、`lark-mail` |
| 会议与妙记 | `lark-meeting` |
| 考勤、审批与 OKR | `lark-attendance`、`lark-approval`、`lark-okr` |
| 妙搭应用与实时事件 | `lark-apps`、`lark-event` |
| OpenAPI 探索与自定义技能 | `lark-openapi-explorer`、`lark-skill-maker` |
| 会议汇总与日程待办摘要 | `lark-workflow-meeting-summary`、`lark-workflow-standup-report` |
| 会议兼容别名，均转交 `lark-meeting` | `lark-minutes`、`lark-note`、`lark-vc`、`lark-vc-agent` |

## 来源与保留策略

- 新增的 25 个目录取自 [larksuite/cli v1.0.98](https://github.com/larksuite/cli/tree/v1.0.98/skills)，版本标签对应提交 `ac81f5056ab88f37d581d25916f3dab85abfca76`。
- 最初上传的 `lark-doc`、`lark-drive`、`lark-shared` 共 112 个文件原样保留；它们与官方标签中的版本存在部分内容差异。本仓库覆盖该版本的全部技能名称，但并非整个上游目录的逐字镜像。
- 上游授权条款见 [LICENSE.lark-cli](LICENSE.lark-cli)。
- Windows 本机的其他自定义技能不包含在此次迁移中；需要另行提供其文件。

## 在云端使用

在以本仓库为项目的 Codex 任务中，按 Skill 名称调用，例如：

```text
$lark-doc 读取这篇文档：<文档链接>
$lark-base 查询这个多维表格：<表格链接>
$lark-sheets 分析这个电子表格：<表格链接>
```

如果当前会话没有自动列出项目 Skill，显式读取对应 `.agents/skills/<名称>/SKILL.md` 及任务需要的参考文件；无需一次性加载所有技能。复制文件不会为现有聊天自动注册 `/lark doc` 指令。

已准备的云环境使用官方 `@larksuite/cli@1.0.98`。激活方式：

```bash
source /workspace/cloud-setup/lark-env.sh
cd /workspace/-
lark-cli --version
```

这是当前云环境的路径；其他克隆应使用各自的安装和工作目录。CLI 自带 `lark-cli skills list`、`lark-cli skills read <名称>`，但内嵌内容不包含这里的脚本和素材。

## 运行前提

- Skill 文件迁移完成不等于已连接飞书。还需生效的网络配置、应用配置和用户授权；不同业务功能可能要求额外权限和域名，应按实际任务配置。
- 基础飞书 API 与授权需要 `open.feishu.cn`、`accounts.feishu.cn`。当前环境已保存放行草稿；保存草稿本身不会应用或发布网络设置。
- 应用配置与用户授权尚未完成。新建外部应用需用户明确同意，也可安全绑定已有应用；不要在聊天或 Git 中提供 App Secret、Token 或密码。
- 部分表格辅助脚本使用 `pandas`；当前云环境已有该依赖。应用开发模板的项目依赖和实时事件进程按具体任务安装、启动。
- 首次业务验证应在授权后读取用户指定资源；尚未验证所有业务接口或新云任务的自动技能发现。
