# Come Logo Skills

团队共享的 Codex Logo 生成 Skill。

## 包含的 Skill

### `rainbow-script-logo`

根据内置参考图生成黑底彩虹书写体英文或数字 Logo，严格分为两个阶段：

1. 先生成纯黑底、纯白字形的结构稿。
2. 收到明确的“通过，上色”后，锁定结构并进行彩虹渐变渲染。

## 在 Codex 中使用

克隆本仓库，并在仓库目录中打开 Codex。Codex 会自动扫描：

```text
.agents/skills/rainbow-script-logo/
```

调用示例：

```text
$rainbow-script-logo M3
```

确认黑白结构稿后输入：

```text
通过，上色
```

如果 Skill 没有立即出现，请重启 Codex，并使用 `/skills` 检查。

## 安装为个人 Skill

如果希望在其他所有仓库中使用，可将完整目录复制到：

```text
$HOME/.agents/skills/rainbow-script-logo/
```

请保留 `SKILL.md`、`agents/`、`assets/` 和 `references/` 的目录结构。
