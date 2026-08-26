# COME联运logo自动化

团队共享的 Codex Logo 生成 Skill。

## 包含的 Skill

### `come-logo-automation`

根据内置参考图生成黑底彩虹书写体英文或数字 Logo，严格分为两个阶段：

1. 点击技能后只需在提示词末尾输入 Logo 名称，默认一次生成 4 张独立的纯黑底、纯白字形结构稿；也可指定 5 张或 6 张。
2. 选择一个方案并明确“通过上色”后，锁定结构并进行彩虹渐变渲染。

技能没有默认 Logo 名称；参考图中的 `Come` 只用于展示风格，不会作为生成内容。

## 在 Codex 中使用

克隆本仓库，并在仓库目录中打开 Codex。Codex 会自动扫描：

```text
.agents/skills/come-logo-automation/
```

调用示例：

```text
$come-logo-automation M3
```

或点击技能后，在自动出现的短提示后直接输入：

```text
AXC9
```

确认黑白结构稿后输入：

```text
B，通过上色
```

如果 Skill 没有立即出现，请刷新技能列表，并使用 `/skills` 检查。

## 安装为个人 Skill

如果希望在其他所有仓库中使用，可将完整目录复制到：

```text
$HOME/.agents/skills/come-logo-automation/
```

请保留 `SKILL.md`、`agents/`、`assets/` 和 `references/` 的目录结构。
