# A28 WP Theme Assistant

A reusable coding-agent skill by adhit28 for turning Figma designs into custom WordPress themes, with Codex integration included. Defaults to Timber v2, Twig, and structured ACF fields for new projects; supports native PHP themes and preserves existing stacks.

This is an instruction package for a coding agent, not a WordPress plugin, starter theme, Figma connector, or hosted service. It does not include Timber, ACF Pro, fonts, or design assets.

## Install

Copy the complete `a28-wp-theme-assistant` folder, including its references and `agents` directory, into your Codex personal skills directory (`$CODEX_HOME/skills`, commonly `~/.codex/skills`). Keep exactly one folder level between the skills directory and this skill's `SKILL.md`. Preserve or back up any existing customized copy before replacing it. Reload your Codex session if it does not appear.

No other A28 skill is required. For direct Figma inspection, configure an available Figma integration or accessible browser session; design exports also work. Theme execution and verification require the project's compatible PHP/WordPress environment. New Timber projects need Composer dependency support, and ACF-based features need the appropriate ACF edition. Existing project tools are reused.

## Other models and coding agents

The core instructions are model-independent Markdown. A model reads and follows them; the application running that model determines skill discovery, installation, and access to tools. Changing models does not by itself install the skill or provide Figma access.

- **Other models in Codex:** use the same installed skill when it is available in the session. No model-specific rewrite is needed.
- **Other coding agents:** if the agent supports `SKILL.md` packages, install the complete folder using that agent's documented skill location and invocation method. Preserve the relative `references/` paths. Do not assume Codex's installation path or `$a28-wp-theme-assistant` syntax applies elsewhere.
- **Agents without skill discovery:** explicitly ask the agent to read `SKILL.md` and the relevant linked references from the supplied folder before performing the task.
- **Chat-only models:** upload `SKILL.md` and the needed references, or paste their contents. They can provide guidance and code, but cannot inspect files, access Figma, or run WordPress checks unless their application supplies those capabilities.

`agents/openai.yaml` supplies Codex-facing metadata and is optional outside Codex; other agents can ignore it. The workflow does not require another A28 skill or a particular model provider. It also does not grant tools, credentials, or permissions: direct design inspection needs Figma/browser access, implementation needs file-editing tools, and runtime verification needs an appropriate terminal, WordPress environment, and browser.

Example without Codex-specific invocation syntax:

```text
Read a28-wp-theme-assistant/SKILL.md and follow its relevant linked
references. Build these Figma pages: <frame links> in this WordPress
theme project using Timber + ACF. Report any checks your tools cannot run.
```

Compatibility here means the instructions can be read and followed across agents. It is not a claim of tested integration with every application or identical results across models; output quality depends on the model, available tools, and supplied project/design context.

## Use in Codex

Open the target theme project and provide a Figma link and the pages to implement:

```text
Use $a28-wp-theme-assistant to build the homepage and about page from
these Figma frames: <frame links>. Use Timber + ACF and make the hero
copy, image, and call to action editable. The local site is <local URL>.
```

For classic PHP:

```text
Use $a28-wp-theme-assistant to implement this Figma page in our existing
native PHP theme. Keep the current tooling and do not add Timber or ACF.
```

For a focused comparison:

```text
Use $a28-wp-theme-assistant to compare this local page with this Figma
frame. Report the differences first; do not change code yet.
```

Provide mobile frames when available. When only desktop is provided, the agent infers responsive behavior and identifies that assumption. Without Figma access, provide exports or screenshots. A written brief is also supported.

## What changes in your workflow

1. Inspect the design and repository to understand the intended appearance and existing architecture.
2. Map Figma sections to templates, reusable components, native WordPress content, and ACF fields.
3. Implement shared components and page templates with responsive behavior and editor controls.
4. Compare actual rendered pages against the design and check relevant WordPress behavior.
5. Hand off implemented pages, editor instructions, verified checks, and any remaining limitations.

The skill defaults to structured page fields, not an unrestricted page builder. Flexible Content and blocks remain options when the task calls for them. It does not authorize publication or deployment by itself.

## Validation and limitations

Package validation checks skill metadata and structure. Editorial review covers workflow routing and portability; these are not proof of a successful generated theme. Each theme still needs its own runtime, editor, and visual checks. Missing tools, assets, and plugins must be reported rather than treated as passed tests.

## License

MIT; see [LICENSE](LICENSE). This license covers the skill package. Third-party software and supplied design assets retain their own terms. This is an independent community skill, not an official WordPress, Timber, ACF, Figma, or OpenAI product.
