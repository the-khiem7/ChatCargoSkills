# ChatCargo Skills

This repository contains Skills.sh-compatible skills for ChatCargo workflows, focused on turning raw chat exports into reusable technical documentation.

## Install

Install skills from this repository:

```bash
npx skills add the-khiem7/ChatCargoSkills
```

## ChatCargo Hugo Workshop Converter

Convert ChatCargo exports into structured, reproducible Hugo workshop documentation with curated screenshots.

### Install this skills

```bash
npx skills add https://github.com/the-khiem7/ChatCargoSkills --skill chatcargo-hugo-workshop-converter
```

### When to use

- You have a raw ChatCargo export and want to turn it into clean workshop content for your team.
- You want to remove Q&A noise while preserving technical flow and decision points.
- You want a multi-page tutorial structure instead of one long, hard-to-follow article.

### Quick start

1. Install skills from this repo using the command above.
2. Open your target workshop repository.
3. Ask your agent to process your raw export folder, for example `@raw/<conversation>/`.
4. Request output under `content/Workshop/` and images under `static/images/`.

### Example prompt

```text
Read @raw/my-export/ and convert it into a multi-page Hugo workshop under @content/Workshop/.
Keep technical detail, select high-value screenshots, and insert images using /images/... paths.
```

## Multi-skill Structure

When adding a new skill, create a new folder using `skills/<kebab-case-skill-name>/SKILL.md` and update the skill list in this README.
