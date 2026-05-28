# cc-slidev

基于 [Slidev](https://sli.dev/) 的 Claude Code 演示文稿插件，用于在 Claude Code 中创建、编辑和导出 Slidev 演示文稿。

> 本仓库是 [rhuss/cc-slidev](https://github.com/rhuss/cc-slidev) 的 Fork 版本，修复了原版 0.1.0 中的 YAML frontmatter 解析错误，当前版本为 `0.2.0_hyj`。

## 修复内容

相较于原版 0.1.0，修复了以下导致插件无法加载的问题：

| 文件 | 问题 | 修复 |
|------|------|------|
| `skills/slide-management/SKILL.md` | description 字段过长且含 Markdown 粗体语法 | 精简为单行描述 |
| `skills/diagram-design/SKILL.md` | 缺少 YAML frontmatter | 添加标准 frontmatter |
| `agents/visual-suggester.md` | description 含 `<example>` XML 标签 | 精简为单行描述 |
| `agents/outline-validator.md` | description 含 `<example>` XML 标签 | 精简为单行描述 |

## 安装

克隆本仓库后，通过本地 marketplace 方式安装：

```bash
# 1. 克隆仓库
git clone https://github.com/heyongjin/cc-slidev.git
cd cc-slidev

# 2. 添加本地仓库为插件市场
claude plugin marketplace add /完整路径/cc-slidev

# 3. 安装插件
claude plugin install slidev

# 4. 重新加载插件
/reload-plugins
```

安装完成后，所有 `/slidev:*` 命令和技能即可使用。

## 更新

拉取最新代码后重新安装：

```bash
cd /完整路径/cc-slidev
git pull
claude plugin remove slidev
claude plugin marketplace remove slidev-dev-marketplace
claude plugin marketplace add /完整路径/cc-slidev
claude plugin install slidev
/reload-plugins
```

## 可用命令

| 命令 | 说明 |
|------|------|
| `/slidev:init` | 初始化 Slidev 演示文稿项目 |
| `/slidev:brainstorm` | 交互式头脑风暴与研究阶段 |
| `/slidev:frame` | 定义演示范围、时长和幻灯片数量目标 |
| `/slidev:outline` | 创建演示文稿大纲 |
| `/slidev:generate` | 根据大纲生成 Slidev 幻灯片 |
| `/slidev:edit` | 编辑指定幻灯片 |
| `/slidev:add` | 添加新幻灯片 |
| `/slidev:delete` | 删除幻灯片 |
| `/slidev:move` | 移动幻灯片位置（自动重新编号） |
| `/slidev:visuals` | 为幻灯片建议视觉增强 |
| `/slidev:diagram` | 创建多平台图表 |
| `/slidev:notes` | 生成或增强演讲者备注 |
| `/slidev:export` | 导出为 PDF |
| `/slidev:preview` | 预览演示文稿 |
| `/slidev:continue` | 继续未完成的演示文稿工作 |

## 可选依赖

以下工具为可选项，用于增强图表渲染和 PDF 导出功能：

```bash
# PDF 导出（需要 LaTeX 支持）
brew install --cask mactex-no-gui

# Mermaid 图表渲染
npm install -g @mermaid-js/mermaid-cli

# Excalidraw 图表渲染
npm install -g excalidraw-brute-export-cli

# Playwright 浏览器（用于图表渲染）
npx playwright install-deps
npx playwright install chromium
```

## 版本历史

- **0.2.0_hyj** — 修复 YAML frontmatter 解析错误，插件可正常加载
- **0.1.0** — 原版（上游），存在 frontmatter 解析 bug
