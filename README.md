# JYS Skill Suite

> 把带货短剧从选套路、剧情改造、选产品、逐段写作到最终拍摄稿，放进一套可以续接、可以协作、可以维护数据库的 JYS 工作流。

当前套件包含 `jys` 主控和 `jys-s1` 至 `jys-s5` 五个执行 Skill，必须一起安装。

## 你会得到什么

- `jys`：识别项目状态并调度下一步。
- `jys-s1`：选套路、录入剧本和产品、维护数据库。
- `jys-s2`：完成剧情骨架和替换设计。
- `jys-s3`：从产品库确认当前产品。
- `jys-s4`：事件级大纲、逐段写作和带货段专项处理。
- `jys-s5`：标题、人物、场景、道具及分幕拍摄稿整理。
- `jys/assets`：当前完整套路库、剧本库和产品库。

## Windows 最快安装

1. 解压整个文件夹，不要单独拿走某一个 Skill。
2. 双击 `install-jys.cmd`。
3. 安装完成后重新打开 Codex。
4. 对 Codex 说：`使用 JYS，从头制作一个带货短剧。`

安装脚本会把原有 JYS 移到“文档/JYS-skill-backups”后再安装，因此可以恢复，不会直接销毁旧版。

## 从 GitHub 安装

第一次上传请先看 [GITHUB-UPLOAD-GUIDE.md](GITHUB-UPLOAD-GUIDE.md)。

上传到 GitHub 后，在仓库页面点击绿色 **Code**，复制 HTTPS 地址，然后运行：

```cmd
npx skills add 这里粘贴仓库HTTPS地址 --list
npx skills add 这里粘贴仓库HTTPS地址 --skill "*" -a codex -g -y --copy
```

第一条命令应列出6个 Skill；第二条命令把它们全部安装到 Codex 全局目录。多 Skill 安装方式以 [vercel-labs/skills](https://github.com/vercel-labs/skills) 的当前说明为准。

## 使用示例

- `使用JYS，从头做一个带货短剧。`
- `继续上次那个JYS项目。`
- `把这个新剧本录入JYS套路库。`
- `继续默认下一步。`

## 前置条件

- [ ] 已安装并能正常使用 Codex Desktop 或 Codex CLI。
- [ ] 使用压缩包安装时：Windows PowerShell 可用，通常系统自带。
- [ ] 使用 GitHub 一行命令安装时：已安装 Node.js，运行 `node --version` 能看到版本号。
- [ ] 如需运行套件验证脚本：已安装 Python，运行 `python --version` 能看到版本号。

## 验证

双击 `verify-jys.cmd`，或运行：

```cmd
python skills\jys\scripts\validate_suite.py skills
python skills\jys\scripts\eval_state_routing.py --cases skills\jys\evals\state_transition_cases.json
```

## 更新数据库

套路、剧本和产品都位于 `skills/jys/assets`。团队成员更新后，应同步整个仓库；不要只发单个 `kernel.md` 或单个产品文件，以免索引和版本号不一致。

## 限制与安全

- JYS会读取和更新当前项目工作区；涉及数据库写入时应先核准目标路径。
- 套件不会自动替你发布到 GitHub，也不会上传项目素材。
- 团队内部使用建议先建立私有 GitHub 仓库；确认内容可以公开后再改为公开仓库。

## 常见问题

| 问题 | 处理方法 |
|---|---|
| Codex只识别到一个步骤 | 确认 `jys`、`jys-s1` 至 `jys-s5` 六个目录都已安装。 |
| 提示找不到共享文件 | 六个 Skill 必须位于同一个 `skills` 目录，不能分开放置。 |
| `npx` 不是内部命令 | 安装 Node.js，关闭并重新打开命令提示符。 |
| 更新后仍读取旧规则 | 重新打开 Codex，并运行 `verify-jys.cmd` 检查安装目录。 |
| 安装后想恢复旧版 | 从“文档/JYS-skill-backups/时间戳”取回原目录。 |

## English

JYS is a six-skill workflow for planning, writing, product integration, and final formatting of Chinese short-form commerce dramas. Keep all six skill directories together. From GitHub, list the skills first and then install all of them globally for Codex using `npx skills add`.
