# Color Theory Skill for Claude Code

A color theory intelligence skill that gives Claude deep knowledge of color harmony, accessibility, psychology, and design systems.

## What It Does

When activated, Claude can help you:

- **Choose color palettes** using harmony schemes (complementary, analogous, triadic, etc.)
- **Apply the 60-30-10 rule** for balanced color distribution
- **Check WCAG accessibility** — contrast ratios, color blindness safety
- **Understand color psychology** — what colors communicate and when to use them
- **Build dark/light mode** with proper color adjustments
- **Structure design system tokens** with semantic naming

## Installation

### Claude Code (CLI)

Copy the skill folder to your Claude skills directory:

```bash
mkdir -p ~/.claude/skills/color-theory
cp -r . ~/.claude/skills/color-theory/
```

### Claude.ai (Projects)

Upload `SKILL.md` and the `references/` files to a Claude project's knowledge base.

## Files

| File | Description |
|------|-------------|
| `SKILL.md` | Main skill prompt with decision guide, harmony schemes, 60-30-10 rule, accessibility, and examples |
| `references/history-and-models.md` | Color wheel history, RGB/CMYK/OKLCH models, gamut details |
| `references/psychology-and-perception.md` | Full hue association table, cultural variations, perception phenomena |

## Usage Examples

- "Help me pick colors for a SaaS dashboard"
- "Are these colors accessible?"
- "Set up color tokens for our design system"
- "What colors go well with `#3B82F6`?"
- "Check the contrast ratio of white text on this background"

## License

MIT
