# gh-cli

一个单文件的 **GitHub CLI（`gh`）命令参考** 技能（Skill），面向 AI Agent 使用。

把 `SKILL.md` 放进你的技能目录，Agent 就能在需要操作 GitHub 时，直接查到 `gh` 的正确命令与参数，而不必凭记忆猜。

---

## 内容

覆盖 `gh` 的完整命令面，按子命令组织：

| 分类 | 覆盖范围 |
| --- | --- |
| 认证 | `auth login / logout / status / switch / token / refresh / setup-git` |
| 仓库 | `repo create / clone / list / view / edit / fork / sync / deploy-key / rename` |
| Issue | 创建、查询、编辑、评论、关闭、转移、锁定、置顶 |
| PR | 创建、查看、检出、diff、review、merge、revert、checks |
| Actions | `run`、`workflow`、`cache`、`secret`、`variable` |
| 其他 | Release、Gist、Codespaces、Project、Search、Label、SSH/GPG Key、Ruleset、Attestation、Alias、API |

除命令清单外，还包含：

- **CLI 结构树** —— 一眼看清全部子命令的层级
- **全局参数表** —— `--json` / `--jq` / `--template` / `--paginate` 等
- **输出格式化** —— JSON 提取与 Go template 的写法
- **常见工作流** —— 从 Issue 建 PR、批量操作、CI 联动、Fork 同步
- **环境变量** —— `GH_TOKEN` / `GH_REPO` / `GH_HOST` 等

---

## 安装

### Trae / 兼容 `SKILL.md` 的客户端

全局安装（对所有项目生效）：

```bash
mkdir -p ~/.trae-cn/skills/gh-cli
curl -fsSL https://raw.githubusercontent.com/<owner>/gh-cli/main/SKILL.md \
  -o ~/.trae-cn/skills/gh-cli/SKILL.md
```

Windows PowerShell：

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.trae-cn\skills\gh-cli" | Out-Null
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/<owner>/gh-cli/main/SKILL.md" `
  -OutFile "$env:USERPROFILE\.trae-cn\skills\gh-cli\SKILL.md"
```

把 `<owner>` 换成仓库所属账号即可；也可以直接在仓库页面点开 `SKILL.md`，用「Raw」按钮另存。

也可以只装到单个项目：放到项目根目录的 `.trae/skills/gh-cli/SKILL.md`。

### 前置条件

`gh` 本身需要自行安装并登录：

```bash
# Windows
winget install --id GitHub.cli

# macOS
brew install gh

# Linux（Debian/Ubuntu）
sudo apt install gh

gh auth login
```

---

## 使用

装上之后无需手动调用，Agent 在遇到 GitHub 相关任务时会自行加载。也可以显式引用：

> 用 gh-cli 技能帮我查一下这个仓库最近的 workflow 运行记录

---

## 说明

`SKILL.md` 里的命令示例统一使用 `gh` 直接调用。如果你的 `gh` 未加入 `PATH`（例如便携版），把它所在目录加到 `PATH`，或在命令前补上完整路径。

文件里不含任何令牌、密钥或账号信息。`gh` 的凭据由它自己的 keyring 管理，不应写入技能文件。

---

## 许可

[MIT](LICENSE)
