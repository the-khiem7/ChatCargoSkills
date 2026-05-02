# ChatCargo Skills

This folder contains Skills.sh-compatible skills for turning ChatCargo exports into reusable technical documentation.

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
- You want screenshots copied into Hugo static assets and referenced with clean `/images/...` paths.

### Quick start

1. Install skills from this repo using the command above.
2. Open your target workshop repository.
3. Mention the raw ChatCargo export folder in your prompt, for example `@raw/<conversation>/`.
4. Mention where the Hugo workshop should be created, for example `@content/Workshop/`.
5. Tell the agent how image links should look in Markdown, usually `/images/...`.

The skill reads these parts of your prompt and resolves the working paths automatically. You do not need to name internal variables. Write the prompt as a task: where to read from, where to publish, how screenshots should be referenced, and what quality constraints matter.

### How to Prompt It

Use a prompt with four practical pieces:

1. **Source**: point to the raw ChatCargo export directory.
2. **Destination**: point to the Hugo content directory or workshop section.
3. **Image rule**: say that selected screenshots should be copied and referenced with `/images/...` paths.
4. **Quality rule**: say whether to preserve detail, split into multiple pages, write bilingual content, or prioritize certain reader needs.

Good minimal prompt:

```text
Read @raw/my-export/ and convert it into a multi-page Hugo workshop under @content/Workshop/.
Keep technical detail, select high-value screenshots, and insert images using /images/... paths.
```

More explicit prompt:

```text
Read @raw/my-export/ and create a detailed Hugo workshop under @content/Workshop/.
Infer a clean workshop slug from the conversation topic.
Write Vietnamese first, then create the English version.
Copy only useful screenshots into the Hugo static image folder and reference them with /images/... Markdown paths.
Do not compress the workflow into one page if separate pages preserve the technical steps better.
```

Prompt with a fixed slug and image location:

```text
Read @raw/my-export/ and convert it into a Hugo workshop under @content/Workshop/ with slug my-custom-workshop.
Copy selected screenshots under @static/images/my-custom-workshop/.
Use Markdown image paths like /images/my-custom-workshop/<image-name>.png.
Keep the original technical reasoning, verification steps, commands, and troubleshooting notes.
```

### Prompting Tips

- Use `@raw/...` for the ChatCargo source folder so the agent knows what to read.
- Use `@content/Workshop/...` or `@content/Workshop/` for the Hugo destination.
- Use `/images/...` when you want published Markdown to avoid raw export paths.
- Say "multi-page" when the conversation is long, has screenshots, or contains setup plus troubleshooting.
- Say "Vietnamese first, then English" when you want bilingual output in the repository's usual `.vi.md` and `.md` pattern.
- Say "infer the slug" when the folder name is good enough, or "with slug ..." when you want a stable output folder.
- Say "keep technical detail" when the raw conversation contains important reasoning, mistakes, commands, SQL, or verification steps.

Avoid prompts that only say "summarize this export." That can lead to a short article and may lose the reproducible workshop flow.
