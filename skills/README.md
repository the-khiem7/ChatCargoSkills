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
