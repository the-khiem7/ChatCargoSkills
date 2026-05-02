![ChatCargo Skills](ChatCargoSkills.png)

This repository contains Skills.sh-compatible skills for ChatCargo workflows, focused on turning raw chat exports into reusable technical documentation.

## Install

Install skills from this repository:

```bash
npx skills add the-khiem7/ChatCargoSkills
```

## ChatCargo Hugo Workshop Converter

Convert any ChatCargo export into structured, reproducible Hugo workshop documentation with curated screenshots.

### Install this skills

```bash
npx skills add https://github.com/the-khiem7/ChatCargoSkills --skill chatcargo-hugo-workshop-converter
```

### When to use

- You have a raw ChatCargo export and want to turn it into clean workshop content for your team.
- You want to remove Q&A noise while preserving technical flow and decision points.
- You want a multi-page tutorial structure instead of one long, hard-to-follow article.
- You want the source directory, Hugo content directory, and image path prefix to be controlled from the prompt.

### Quick start

1. Install skills from this repo using the command above.
2. Open your target workshop repository.
3. Ask your agent to process your raw export folder, for example `@raw/<conversation>/`.
4. Request output under `content/Workshop/` and images under `static/images/`.

The skill resolves task-specific paths from your prompt. For example, `@raw/my-export/` becomes the raw ChatCargo source, `@content/Workshop/` becomes the Hugo output root, and `/images/...` tells the skill to copy selected screenshots under `static/images/` and reference them with root-relative Markdown image paths.

### Example prompt

```text
Read @raw/my-export/ and convert it into a multi-page Hugo workshop under @content/Workshop/.
Keep technical detail, select high-value screenshots, and insert images using /images/... paths.
```

The skill infers a workshop slug from the raw export folder or the conversation topic. You can override it explicitly:

```text
Read @raw/my-export/ and convert it into a multi-page Hugo workshop under @content/Workshop/ with slug my-custom-workshop.
Copy selected screenshots under @static/images/my-custom-workshop/ and reference them using /images/my-custom-workshop/... paths.
```

## Multi-skill Structure

When adding a new skill, create a new folder using `skills/<kebab-case-skill-name>/SKILL.md` and update the skill list in this README.
