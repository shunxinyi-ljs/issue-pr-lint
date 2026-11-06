# issue-pr-lint

## 这是什么

一个给 AI 编码助手用的 GitHub Issue / PR **提交前审查** skill。
单文件（`SKILL.md`），无依赖。

## 有什么用

在文案发出去之前，逐条核对每个断言能不能指回证据——diff、测试输出、仓库代码。
防止"看起来有道理、其实没验证过"的描述进入公开仓库。

它会：

- 把文案拆成断言并按证据强度分级（E1 有直接证据 → E0 无依据）
- 判"无证据"之前**先真的去搜**，不能拿"我没看过"当理由
- 保护用户价值陈述（提示文案、用户可见变化），不因缺代码证据就删
- 改动涉及错误码 / 默认值时，检查下游有没有对应处理
- 可选：临时撤下修复，验证测试确实会失败

它**不**判断方案好坏，也不发现代码 bug——只查说法有没有根据。

## 怎么用

```bash
mkdir -p ~/.claude/skills/issue-pr-lint
cp issue-pr-lint/SKILL.md ~/.claude/skills/issue-pr-lint/
```

然后对 Claude Code 说：

```
用 issue-pr-lint 审一下这个 PR
```

或直接 `/issue-pr-lint`。

适用于文案已写完、准备发布的时点。调查、复现、改代码阶段不适用。

---

> 仓库名为 `issue-pr-link`，skill 名为 `issue-pr-lint`（l**i**nt）。文件与目录统一使用 `issue-pr-lint`。
