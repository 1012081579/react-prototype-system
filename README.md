# React Prototype System

A reusable Codex skill for turning Figma frames, screenshots, visual specifications, and existing UI designs into high-fidelity React prototypes.

It guides an AI coding agent through design intake, component architecture, state ownership, deterministic mocks, interaction flows, responsive behavior, accessibility, and browser-based visual verification.

## Install With AI

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

## Use

Attach a Figma link, screenshot, or design specification and use a prompt such as:

```text
Use $react-prototype-system to turn this design into a responsive React prototype.

Design source: [Figma URL or attached screenshots]
Target route: /search
Scope: search, filters, result cards, and detail drawer
States: populated, loading, empty, error, and retry

Reuse the repository's existing tokens, components, and icon library. Run the
application and verify the result in desktop and mobile browser viewports.
```

The skill can also review and improve an existing implementation:

```text
Use $react-prototype-system to review this React page for design fidelity,
component boundaries, state ownership, responsive behavior, accessibility,
and missing interaction states. Implement and verify the necessary fixes.
```

## What It Enforces

- Inspect the design source and repository before coding.
- Build through `tokens -> primitives -> patterns -> layouts -> screens -> flows`.
- Prefer stateless display components with explicit data and callbacks.
- Keep mocks, side effects, navigation, and orchestration outside visual components.
- Implement the primary path and a relevant failure or recovery path.
- Verify the rendered interface at representative desktop and mobile sizes.

## Repository Layout

```text
react-prototype-system/
  SKILL.md
  agents/openai.yaml
  references/
  assets/
  scripts/
```

The installable skill is in [`react-prototype-system/`](react-prototype-system/). The main workflow stays concise and loads detailed references only when needed.

## Manual Installation

Clone this repository, then copy or symlink the inner `react-prototype-system` directory to:

```text
$CODEX_HOME/skills/react-prototype-system
```

When `CODEX_HOME` is not set, use:

```text
~/.codex/skills/react-prototype-system
```

Do not overwrite an existing installation without reviewing local changes first.

## 中文说明

把下面这段话和链接直接发给 Codex：

```text
请使用 $skill-installer 安装这个 skill：
https://github.com/1012081579/react-prototype-system/tree/main/react-prototype-system
```

安装完成后的下一轮对话中，使用：

```text
使用 $react-prototype-system，把这个 Figma 设计稿还原成可交互、可响应式的 React prototype，并在浏览器中验证桌面端和移动端效果。
```

## License

[MIT](LICENSE)
