# Redshift Spectrum Example Reference

This file is an illustrative example only.

Do not copy these paths, slugs, service names, resource names, or article structure unless the user's task explicitly matches a Redshift Spectrum workflow.

## Example Source and Target

Example raw export:

```txt
raw/manhattan-dataways-redshift-spectrum-query-setup/
```

Example Hugo output:

```txt
content/Workshop/manhattan-dataways-redshift-spectrum/
```

Example image output:

```txt
static/images/manhattan-dataways/redshift-spectrum/
```

Example public image prefix:

```txt
/images/manhattan-dataways/redshift-spectrum/
```

## Example Topic Context

The task in this example conversation is about setting up and using Amazon Redshift / Redshift Spectrum in the Manhattan DataWays AWS workshop context.

The target readers are colleagues. They should be able to follow the final workshop content and reproduce the task without needing to ask ChatGPT step by step.

## Example Multi-page Structure

For a long Redshift Spectrum workflow, a multi-page workshop structure may be appropriate:

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

This structure should be adjusted based on the actual conversation. The default direction is to preserve detail through multiple focused pages rather than compressing everything into one article.

## Example Workflow Chunks

For this Redshift Spectrum example, useful chunks may include:

- existing Glue/S3 pipeline context
- creating Redshift Serverless namespace and workgroup
- understanding namespace vs workgroup
- configuring IAM role
- configuring Redshift Serverless capacity/RPU
- understanding Redshift Serverless free trial and cost controls
- connecting with Query Editor v2
- creating external schema for Glue Data Catalog
- querying external tables through Redshift Spectrum
- handling mistakes such as using "Load data" instead of external schema
- verifying external schema and external tables
- troubleshooting missing Glue tables
- cleanup or cost-control notes

For each chunk, identify:

- the purpose of the step
- the AWS console location
- important decision points
- SQL commands used
- screenshots relevant to that step
- repeated or redundant screenshots that should be ignored
- verification steps
- possible errors or wrong paths

## Example Image Naming

Selected images should be copied and renamed meaningfully, for example:

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

Do not copy every image. Only copy selected screenshots that will be used in published articles.

## Example Screenshot Coverage

If useful images exist in the raw export, check for screenshots covering:

1. Existing Glue/S3 pipeline overview
2. Redshift Serverless setup/configuration screen
3. Capacity/RPU configuration
4. IAM role/default role state
5. Redshift workgroup available state
6. Query Editor v2 connection screen
7. Successful Redshift test query
8. `CREATE EXTERNAL SCHEMA` success
9. External schema/table verification
10. The mistaken "Load data" flow, if there is a troubleshooting article

Do not force all 10 if the raw export does not contain useful images for them, but check them carefully.

## Example Technical Content to Preserve

For this Redshift Spectrum example, preserve detailed explanations when they appear in the raw conversation:

- why Redshift Serverless is used
- difference between namespace and workgroup
- what RPU/base capacity means
- why low RPU is better for hands-on cost control
- why IAM role matters
- why Query Editor v2 uses federated user connection
- why "Load data" is not the right flow for Redshift Spectrum
- difference between loading data into native Redshift tables and querying external data
- how Glue Data Catalog is used by Redshift Spectrum
- why creating an external schema is needed
- how to verify external schemas and external tables
- what to do when external schema exists but no table appears
- cost/free trial notes if discussed in the raw conversation

## Example SQL

Preserve the correct SQL statement from the conversation when available.

Example only:

```sql
CREATE EXTERNAL SCHEMA IF NOT EXISTS taxi_raw
FROM DATA CATALOG
DATABASE 'craw_data_catalog'
IAM_ROLE default
REGION 'us-east-2';
```

If the raw conversation later uses an explicit IAM role ARN, preserve it where appropriate.

Do not merge multiple SQL statements into unreadable one-line blocks.
