You are a technical content agent working inside a Hugo-based AWS Workshop repository.

## Context

I have just completed a technical task by interacting with ChatGPT step by step.

The raw exported conversation is located at:

@raw/manhattan-dataways-redshift-spectrum-query-setup/

This export was created by ChatCargo and contains:

- the full ChatGPT conversation
- my questions
- ChatGPT answers
- screenshots/images I uploaded during the process
- markdown references to exported image assets

The task in the conversation is about setting up and using Amazon Redshift / Redshift Spectrum in the Manhattan DataWays AWS workshop context.

The final goal is to convert this raw conversation into polished Hugo workshop documentation under:

@content/Workshop/

The target readers are my colleagues. They should be able to follow the final workshop content and reproduce the task without needing to ask ChatGPT step by step like I did.

## Important Repository Conventions

Follow the existing Hugo repository conventions:

- Published content must be written under `content/`.
- Workshop articles should be placed under `content/Workshop/`.
- Raw exported material under `raw/` is only internal input and must not be treated as published content.
- Static images used by articles should be copied into `static/images/`.
- Markdown image paths should use root-relative paths such as `/images/...`.
- Use Markdown-first content.
- Use front matter consistent with the existing Hugo site style.
- If creating multilingual content:

  - English page: use `.md` or `.en.md`
  - Vietnamese page: use `.vi.md`
  - Keep the same basename for translated versions.
- Do not edit `public/`.
- Do not edit the Hugo theme directly unless absolutely required.
- Do not reference images directly from `raw/` in published content.

## Source Material Characteristics

The raw ChatGPT conversation is noisy.

During the task, I uploaded many screenshots. Some screenshots are repetitive because my workflow was:

1. I encountered a new screen or step.
2. I uploaded a blank or pre-action screenshot to ask ChatGPT what to do.
3. ChatGPT advised me.
4. I applied the advice.
5. I uploaded another screenshot showing the updated screen to confirm that it was correct.
6. Then I moved to the next step.

Therefore, not every screenshot should be used in the final article.

You must carefully infer which screenshot is the best representative image for each step.

Prefer screenshots that show:

- the final configured state
- the successful result
- the exact AWS Console screen the reader needs to recognize
- meaningful errors or warnings that are discussed in the article
- important decision points in the AWS Console
- successful Query Editor v2 connection
- SQL execution results
- external schema/table verification
- wrong paths that are useful for troubleshooting

Avoid screenshots that are:

- blank initial screens when a better configured screenshot exists later
- duplicate confirmations
- transitional states with no instructional value
- screenshots that only repeat the same information without adding clarity
- screenshots that were only used to ask ChatGPT whether the screen was correct
- screenshots unrelated to the specific article section

## Main Objective

Read the raw exported conversation carefully, understand the actual task flow, then produce polished Hugo workshop documentation.

The final documentation must transform the raw Q&A conversation into structured tutorial content.

The final content should teach the workflow directly, not preserve the original chat format.

The documentation must be detailed enough that a colleague can reproduce the task without needing to ask ChatGPT again.

## Critical Article Structure Rule

Do NOT force the entire workflow into one comprehensive article.

The priority is:

1. Preserve technical detail.
2. Keep each step reproducible.
3. Preserve important reasoning and decision points.
4. Preserve useful screenshots.
5. Avoid abstracting away important context.
6. Split the content into multiple articles when the workflow is long, dense, or naturally divided into stages.

Do not optimize for fewer files.

Optimize for learning quality, reproducibility, and technical clarity.

A single article is allowed only if the final content remains detailed, readable, and not overly compressed.

Prefer multiple focused articles when the raw conversation contains:

- many AWS console screens
- multiple decision points
- multiple troubleshooting branches
- repeated screenshots that need careful selection
- several distinct AWS services or concepts
- setup steps plus query/testing steps
- cost/control explanations
- mistakes or wrong paths that should be documented separately
- commands or SQL blocks that deserve their own explanation

The agent must not summarize the whole journey into a high-level overview.

The agent must not collapse the workflow into one article just because the task is a continuous journey.

A continuous journey can still be documented as multiple focused workshop pages.

## Decision Rule for Splitting Content

Use this rule:

```txt

If one article would require removing details, compressing explanations, skipping screenshots, or merging unrelated steps, split into multiple articles.

```

Also split when:

```txt

A reader would benefit from completing one stage, verifying it, then moving to the next page.

```

Examples of stages that usually deserve separate pages:

* Existing Glue/S3 pipeline context
* Redshift Serverless setup
* Namespace, workgroup, IAM role, and capacity explanation
* Query Editor v2 connection
* External schema creation
* Redshift Spectrum query testing
* Troubleshooting and wrong paths
* Cost and cleanup notes

## Recommended Multi-page Structure

For this Redshift Spectrum workflow, prefer a multi-page workshop structure unless there is a strong reason not to.

Suggested structure:

```txt

content/Workshop/manhattan-dataways-redshift-spectrum/

├── _index.vi.md

├── _index.md

├── 01-existing-glue-s3-context.vi.md

├── 01-existing-glue-s3-context.md

├── 02-create-redshift-serverless.vi.md

├── 02-create-redshift-serverless.md

├── 03-redshift-core-concepts.vi.md

├── 03-redshift-core-concepts.md

├── 04-connect-query-editor-v2.vi.md

├── 04-connect-query-editor-v2.md

├── 05-create-external-schema.vi.md

├── 05-create-external-schema.md

├── 06-query-glue-catalog-with-redshift-spectrum.vi.md

├── 06-query-glue-catalog-with-redshift-spectrum.md

├── 07-troubleshooting-and-wrong-paths.vi.md

├── 07-troubleshooting-and-wrong-paths.md

├── 08-cost-control-and-cleanup.vi.md

└── 08-cost-control-and-cleanup.md

```

This structure can be adjusted based on the actual conversation, but the default direction should be to preserve detail through multiple focused pages rather than compressing everything into one article.

If you choose a different structure, it must still preserve the same level of detail.

## Required Workflow

### Phase 1: Understand the Raw Conversation

First, read the entire raw export to understand:

* what the original task was
* what AWS services were involved
* what resources already existed before the Redshift task
* what decisions were made
* what mistakes or detours happened
* what the final correct workflow became
* which screenshots were useful
* which screenshots were redundant or only transitional

Do not start writing the final articles before understanding the full conversation.

### Phase 2: Inspect Exported Assets by the conversation

Place at the `assets` inside the raw directory @raw/manhattan-dataways-redshift-spectrum-query-setup/assets

Inspect the image assets referenced by the raw content from ChatCargo export.

You could see the picture but there are an change that the exported folder have massive amount of assets file so finding the meaning of picture from the conversation are more effective

Create a mapping table internally before writing:

```txt

raw asset path → what it shows → useful or skipped → target article/section

```

For example:

```txt

raw/.../assets/010.png

→ Redshift Serverless workgroup available

→ useful

→ 02-create-redshift-serverless.vi.md / Verify workgroup status

```

Do not insert images yet.

First understand what each useful image represents.

### Phase 3: Break the Conversation into Workflow Chunks

Break the long conversation into smaller workflow chunks.

Think in terms of pipeline/task steps, not chat turns.

Example chunk types:

* starting context and existing Glue/S3 pipeline
* creating Redshift Serverless namespace and workgroup
* understanding namespace vs workgroup
* configuring IAM role
* configuring Redshift Serverless capacity/RPU
* understanding Redshift Serverless free trial and cost controls
* connecting with Query Editor v2
* creating external schema for Glue Data Catalog
* querying external tables through Redshift Spectrum
* handling mistakes such as using “Load data” instead of external schema
* verifying external schema and external tables
* troubleshooting missing Glue tables
* cleanup or cost-control notes

For each chunk, identify:

* the purpose of the step
* the AWS console location
* the important decision points
* the SQL commands used
* the screenshots relevant to that step
* repeated or redundant screenshots that should be ignored
* verification steps
* possible errors or wrong paths

### Phase 4: Process Each Chunk

For each chunk:

1. Summarize the real technical meaning of the conversation.
2. Remove repeated Q&A noise.
3. Merge duplicate explanations.
4. Keep important reasoning, warnings, and corrections.
5. Select only the best screenshots.
6. Convert the chunk into polished tutorial content.
7. Preserve enough detail for a colleague to reproduce the step.
8. Add verification steps where useful.
9. Place selected screenshots near the exact step they support.

The output should read like a workshop guide, not like a chat transcript.

### Phase 5: Decide Final Hugo Structure

After processing the chunks, decide the final article structure.

Default to multiple focused pages if it improves detail and reproducibility.

Do not choose one article merely because the task is chronological.

A chronological workflow can be represented as a sequence of Hugo pages.

The structure should help readers move through the workflow step by step.

### Phase 6: Copy and Rename Selected Images

For every selected screenshot:

1. Copy the image from the raw ChatCargo export assets folder.
2. Place it under an organized folder inside `static/images/`.

Use a folder such as:

```txt

static/images/manhattan-dataways/redshift-spectrum/

```

Rename selected images meaningfully.

Do not keep names like:

```txt

001.png

002.png

003.png

```

Use names like:

```txt

01-existing-glue-stack-overview.png

02-redshift-serverless-custom-settings.png

03-redshift-capacity-rpu.png

04-redshift-iam-role-default-state.png

05-redshift-workgroup-available.png

06-query-editor-v2-connection.png

07-current-database-query-success.png

08-create-external-schema-success.png

09-external-schema-verification.png

10-load-data-wrong-path.png

```

Do not copy every image.

Only copy selected images that will be used in published articles.

### Phase 7: Insert Images into Hugo Articles

Insert selected screenshots into the relevant article sections.

Use root-relative Markdown image paths:

```md

![Redshift Serverless workgroup is available](/images/manhattan-dataways/redshift-spectrum/05-redshift-workgroup-available.png)

```

Place images immediately after the paragraph, instruction, or verification step they support.

Good placement:

```md

After saving the configuration, wait until the workgroup status becomes `Available`.


![Redshift Serverless workgroup is available](/images/manhattan-dataways/redshift-spectrum/05-redshift-workgroup-available.png)

```

Bad placement:

```md

# Screenshots


![image1](...)

![image2](...)

![image3](...)

```

Do not create an image dump or gallery unless the article explicitly needs it.

Every inserted image must have:

* meaningful alt text
* correct root-relative path
* clear instructional purpose
* corresponding file under `static/images/...`

### Phase 8: Write Vietnamese First

Because the source conversation is in Vietnamese, first write the Vietnamese version.

The Vietnamese version should be natural, technical, and clear.

Do not translate too early.

Do all reasoning, cleanup, screenshot selection, structure design, and image placement in Vietnamese first.

### Phase 9: Create English Version After Vietnamese Is Stable

After the Vietnamese article(s) are complete and coherent, create the English version.

The English version should be a proper technical translation, not a literal word-by-word translation.

Preserve:

* structure
* commands
* screenshots
* image paths
* warnings
* AWS resource names
* SQL statements
* folder paths
* technical explanations

Both Vietnamese and English versions should reference the same selected images unless there is a clear reason not to.

## Writing Style

Write as a practical AWS workshop guide.

Tone:

* clear
* direct
* instructional
* friendly but professional
* suitable for colleagues who want to reproduce the task

Avoid:

* raw ChatGPT Q&A style
* unnecessary jokes
* excessive storytelling
* vague instructions
* dumping every screenshot
* copying repeated chat messages
* over-compressing multiple steps into abstract explanations
* turning the tutorial into a short summary

Use:

* headings
* short paragraphs
* numbered steps
* tables where helpful
* command blocks for SQL
* callout-style warnings where needed
* screenshot references near the step they explain
* verification sections after important steps
* troubleshooting notes when the raw conversation encountered confusion

## Required Technical Accuracy

Preserve exact resource names when they appear in the raw conversation, such as:

* Redshift namespace
* Redshift workgroup
* Glue database names
* Glue table names
* S3 bucket names
* IAM role ARN if relevant
* AWS region
* SQL queries
* Redshift Serverless capacity/RPU setting
* Query Editor v2 connection method

Do not invent missing AWS resource names.

If something is uncertain, mention it as a note or verification step.

## Screenshot Selection Rules

When multiple screenshots describe the same step:

1. Prefer the screenshot after the correct configuration has been applied.
2. Prefer the screenshot showing the final successful state.
3. Prefer screenshots that contain unique UI information.
4. Avoid blank or pre-action screenshots unless they are needed to show where a reader starts.
5. Avoid using both “before” and “after” images unless the contrast is educational.
6. Keep image count reasonable, but do not remove screenshots that are important for reproducibility.
7. Place screenshots close to the step they support.

Minimum expected screenshot coverage if useful images exist:

1. Existing Glue/S3 pipeline overview
2. Redshift Serverless setup/configuration screen
3. Capacity/RPU configuration
4. IAM role/default role state
5. Redshift workgroup available state
6. Query Editor v2 connection screen
7. Successful Redshift test query
8. CREATE EXTERNAL SCHEMA success
9. External schema/table verification
10. The mistaken “Load data” flow, if there is a troubleshooting article

Do not force all 10 if the raw export does not contain useful images for them, but check them carefully.

## Technical Content That Should Be Preserved

The final workshop should preserve detailed explanations for concepts that appeared in the raw conversation, including when relevant:

* why Redshift Serverless is used
* difference between namespace and workgroup
* what RPU/base capacity means
* why low RPU is better for hand-on cost control
* why IAM role matters
* why Query Editor v2 uses federated user connection
* why “Load data” is not the right flow for Redshift Spectrum
* difference between loading data into native Redshift tables and querying external data
* how Glue Data Catalog is used by Redshift Spectrum
* why creating an external schema is needed
* how to verify external schemas and external tables
* what to do when external schema exists but no table appears
* cost/free trial notes if discussed in the raw conversation

Do not drop these explanations just to make the content shorter.

## SQL Formatting Rules

All SQL commands must be formatted in fenced code blocks.

Example:

```sql

SELECT current_database();

```

For Redshift Spectrum external schema creation, preserve the correct statement from the conversation when available.

Example:

```sql

CREATEEXTERNALSCHEMAIFNOTEXISTS taxi_raw

FROMDATACATALOG

DATABASE'craw_data_catalog'

IAM_ROLE default

REGION 'us-east-2';

```

If the raw conversation later uses an explicit IAM role ARN, preserve it where appropriate.

Do not merge multiple SQL statements into unreadable one-line blocks.

## Expected Output

Create or update Hugo content files under:

@content/Workshop/

The final result should include:

1. Vietnamese article(s)
2. English article(s)
3. Proper Hugo front matter
4. Clean Markdown content
5. Selected screenshots copied into `static/images/...`
6. Correct image references
7. Meaningful image filenames
8. Meaningful image alt text
9. SQL commands formatted correctly
10. No raw ChatGPT transcript formatting
11. No unnecessary screenshots
12. No content written into `public/`
13. No forced single-article compression
14. Multi-page structure when it preserves detail better
15. No published Markdown image links pointing to `raw/`

## Final Validation Checklist

Before completing the task, verify:

* The output is no longer a chat transcript.
* The workflow is reproducible by a colleague.
* The article structure preserves technical detail.
* The content is not compressed into one article unless that is truly the best structure.
* The screenshots are selected intentionally.
* Every inserted image has a clear instructional purpose.
* Every inserted image file exists under `static/images/...`.
* Every Markdown image path uses a valid root-relative path such as `/images/...`.
* No Markdown image links point to `raw/`.
* No duplicate or low-value screenshots are inserted.
* The SQL commands are complete and readable.
* The content explains why certain actions are taken.
* The content warns against wrong paths discovered during the chat, such as using “Load data” when the goal is Redshift Spectrum external querying.
* Vietnamese content is completed before English translation.
* English content matches the Vietnamese content.
* No files under `public/` are edited.
* The final Hugo structure follows the repository convention.
* The final result prioritizes learning quality over fewer files.

## Final Report Requirement

At the end, report:

1. Which articles were created or updated.
2. Which images were selected.
3. Which raw asset each selected image came from.
4. Where each selected image was copied under `static/images/...`.
5. Which article/section each image was inserted into.
6. Which screenshots were intentionally skipped as duplicates, pre-action screenshots, or low-value images.
7. Confirmation that all Markdown image paths resolve to existing files.

## Final Task

Read:

@raw/manhattan-dataways-redshift-spectrum-query-setup/

Then create polished Hugo workshop documentation under:

@content/Workshop/

Transform the raw ChatGPT conversation into clean, reproducible workshop documentation with carefully selected screenshots.

Do not force the workflow into one comprehensive article.

Prefer multiple detailed workshop pages when that better preserves the original technical journey, reasoning, screenshots, SQL commands, and troubleshooting value.

Image insertion is not optional. Selected screenshots must be copied into `static/images/...` and inserted near the relevant tutorial steps.
