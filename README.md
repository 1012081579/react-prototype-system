# React Prototype System

[English](#english) | [简体中文](#简体中文) | [日本語](#日本語)

## English

### Overview

A reusable Codex skill for turning Figma frames, screenshots, visual specifications, and existing UI designs into high-fidelity React prototypes, using TypeScript and Tailwind CSS by default for new or unconstrained implementations.

It guides an AI coding agent through design intake, component architecture, state ownership, deterministic mocks, interaction flows, responsive behavior, accessibility, and browser-based visual verification.

### Install With AI

Send this prompt to Codex or another AI agent that can install Agent Skills:

```text
Install this skill and make it available for future tasks:
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

For Codex, the explicit version is:

```text
Use $skill-installer to install:
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

After installation, start a new turn and invoke the skill with `$react-prototype-system`.

### Use

Attach a Figma link, screenshot, or design specification and use a prompt such as:

```text
Use $react-prototype-system to turn this design into a responsive React prototype.

Design source: [Figma URL or attached screenshots]
Target route: /search
Scope: search, filters, result cards, and detail drawer
States: populated, loading, empty, error, and retry
Implementation stack: TypeScript and Tailwind CSS

Reuse the repository's existing tokens, components, and icon library. Run the
application and verify the result in desktop and mobile browser viewports.
```

The skill can also review and improve an existing implementation:

```text
Use $react-prototype-system to review this React page for design fidelity,
component boundaries, state ownership, responsive behavior, accessibility,
and missing interaction states. Implement and verify the necessary fixes.
```

### What It Enforces

- Inspect the design source and repository before coding.
- Default new or unconstrained React implementations to TypeScript and Tailwind CSS.
- Preserve meaningful Figma names and infer missing names from product context.
- Map a Figma design system into Tailwind-compatible variables before implementation; use Tailwind defaults when no design system exists.
- Keep each component in a matching named file, make it responsive, and compose pages from those components.
- Build through `tokens -> primitives -> patterns -> layouts -> screens -> flows`.
- Prefer stateless display components with explicit data and callbacks.
- Keep mocks, side effects, navigation, and orchestration outside visual components.
- Implement the primary path and a relevant failure or recovery path.
- Verify the rendered interface at representative desktop and mobile sizes.

### Repository Layout

```text
react-prototype-system/
  SKILL.md
  agents/openai.yaml
  references/
  assets/
  scripts/
```

The installable skill is in [`react-prototype-system/`](react-prototype-system/). The main workflow stays concise and loads detailed references only when needed.

### Manual Installation

Clone this repository, then copy or symlink the inner `react-prototype-system` directory to:

```text
$CODEX_HOME/skills/react-prototype-system
```

When `CODEX_HOME` is not set, use:

```text
~/.codex/skills/react-prototype-system
```

Do not overwrite an existing installation without reviewing local changes first.

### License

[MIT](LICENSE)

## 简体中文

### 概述

一个可复用的 Codex skill，用于将 Figma 画框、截图、视觉规范和已有 UI 设计转化为高保真的 React prototype，并在新项目或未指定实现方式时默认使用 TypeScript 和 Tailwind CSS。

它会引导 AI coding agent 完成设计信息读取、组件架构、状态归属、确定性 mock、交互流程、响应式行为、无障碍支持，以及基于浏览器的视觉验证。

### 通过 AI 安装

将下面的提示词发送给 Codex，或其他能够安装 Agent Skills 的 AI agent：

```text
安装这个 skill，并让它可以在后续任务中使用：
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

在 Codex 中可以使用更明确的版本：

```text
请使用 $skill-installer 安装：
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

安装完成后，开始新一轮对话，并通过 `$react-prototype-system` 调用这个 skill。

### 使用方法

附上 Figma 链接、截图或设计规范，然后使用类似下面的提示词：

```text
使用 $react-prototype-system，把这个设计转化为响应式 React prototype。

设计来源：[Figma URL 或已附加的截图]
目标路由：/search
实现范围：搜索、筛选、结果卡片和详情抽屉
状态：有数据、加载中、空状态、错误和重试
实现技术栈：TypeScript 和 Tailwind CSS

复用仓库中已有的 tokens、组件和 icon library。运行应用，并在桌面端和
移动端浏览器视口中验证最终效果。
```

这个 skill 也可以检查并改进已有实现：

```text
使用 $react-prototype-system，检查这个 React 页面在设计还原度、组件边界、
状态归属、响应式行为、无障碍支持和缺失交互状态方面的问题。
实现并验证所有必要的修复。
```

### 核心规范

- 编码之前先检查设计来源和代码仓库。
- 新项目或未指定实现方式的 React 实现默认使用 TypeScript 和 Tailwind CSS。
- 尽可能保留有意义的 Figma 命名，并根据产品上下文推断缺失的名称。
- 如果 Figma 中存在设计系统，先映射为 Tailwind 兼容变量；如果不存在，则使用 Tailwind 默认设计体系。
- 每个组件放入同名文件并完成响应式实现，再使用这些组件组合页面。
- 按照 `tokens -> primitives -> patterns -> layouts -> screens -> flows` 构建。
- 优先使用通过明确数据和 callback 控制的无状态展示组件。
- 将 mock、副作用、导航和流程编排放在视觉组件之外。
- 实现主要流程，以及一个相关的失败或恢复流程。
- 在具有代表性的桌面端和移动端尺寸下验证渲染结果。

### 仓库结构

```text
react-prototype-system/
  SKILL.md
  agents/openai.yaml
  references/
  assets/
  scripts/
```

可安装的 skill 位于 [`react-prototype-system/`](react-prototype-system/) 目录。主工作流保持精简，只在需要时加载详细 reference。

### 手动安装

克隆这个仓库，然后将内部的 `react-prototype-system` 目录复制或链接到：

```text
$CODEX_HOME/skills/react-prototype-system
```

如果没有设置 `CODEX_HOME`，请使用：

```text
~/.codex/skills/react-prototype-system
```

在覆盖已有安装之前，请先检查其中是否包含本地修改。

### 许可证

[MIT](LICENSE)

## 日本語

### 概要

Figmaフレーム、スクリーンショット、ビジュアル仕様、既存のUIデザインを高忠実度のReactプロトタイプへ変換し、新規または実装方法が未指定の場合にTypeScriptとTailwind CSSを標準使用する、再利用可能なCodex skillです。

AI coding agentに対して、デザイン情報の確認、コンポーネント設計、状態の所有範囲、再現可能なmock、操作フロー、
レスポンシブ対応、アクセシビリティ、ブラウザ上でのビジュアル検証まで一貫した手順を提供します。

### AIでインストール

次のプロンプトをCodex、またはAgent Skillsをインストールできる別のAI agentへ送信します：

```text
このskillをインストールし、今後のタスクで利用できるようにしてください：
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

Codexでは、次のように明示的に指定できます：

```text
$skill-installer を使用してインストールしてください：
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

インストール後は新しいターンを開始し、`$react-prototype-system` でskillを呼び出します。

### 使用方法

Figmaリンク、スクリーンショット、またはデザイン仕様を添付し、次のようなプロンプトを使用します：

```text
$react-prototype-system を使用して、このデザインをレスポンシブなReactプロトタイプに変換してください。

デザインソース：[Figma URLまたは添付したスクリーンショット]
対象ルート：/search
対象範囲：検索、フィルター、結果カード、詳細ドロワー
状態：データあり、読み込み中、空、エラー、再試行
実装スタック：TypeScriptとTailwind CSS

リポジトリ既存のtokens、コンポーネント、icon libraryを再利用してください。
アプリを実行し、デスクトップとモバイルのブラウザviewportで結果を検証してください。
```

このskillは、既存の実装をレビューして改善する用途にも利用できます：

```text
$react-prototype-system を使用して、このReactページのデザイン再現度、
コンポーネント境界、状態の所有範囲、レスポンシブ対応、アクセシビリティ、
不足している操作状態を確認し、必要な修正を実装して検証してください。
```

### 適用するルール

- コーディング前にデザインソースとリポジトリを確認します。
- 新規または実装方法が未指定のReact実装では、TypeScriptとTailwind CSSを標準使用します。
- 意味のあるFigma名を可能な限り維持し、不足する名前はプロダクトの文脈から推定します。
- Figmaにデザインシステムがある場合は先にTailwind互換変数へ変換し、ない場合はTailwindのデフォルト体系を使用します。
- 各コンポーネントを同名ファイルに置いてレスポンシブ対応し、それらを組み合わせてページを構築します。
- `tokens -> primitives -> patterns -> layouts -> screens -> flows` の順序で構築します。
- 明示的なデータとcallbackで制御する、状態を持たない表示コンポーネントを優先します。
- mock、副作用、ナビゲーション、フロー制御を表示コンポーネントの外側に置きます。
- 主要フローと、関連する失敗または復旧フローを実装します。
- 代表的なデスクトップとモバイルのサイズで、描画されたUIを検証します。

### リポジトリ構成

```text
react-prototype-system/
  SKILL.md
  agents/openai.yaml
  references/
  assets/
  scripts/
```

インストール対象のskillは [`react-prototype-system/`](react-prototype-system/) にあります。メインのワークフローは簡潔に保ち、必要な場合のみ詳細なreferenceを読み込みます。

### 手動インストール

このリポジトリをcloneし、内側の `react-prototype-system` ディレクトリを次の場所へcopy、またはsymlinkします：

```text
$CODEX_HOME/skills/react-prototype-system
```

`CODEX_HOME` が設定されていない場合は、次の場所を使用します：

```text
~/.codex/skills/react-prototype-system
```

既存のインストールを上書きする前に、ローカル変更が含まれていないか確認してください。

### ライセンス

[MIT](LICENSE)
