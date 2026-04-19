# DQ Copilot

Simple scaffold for a future multi-agent data quality copilot on a Snowflake-based data warehouse.

This repository is intentionally structure-only right now. No agent code, SQL scripts, DAGs, dbt models, or Streamlit app files have been added yet. We will add those pieces one by one as the design becomes clearer.

## Target Stack

- **Snowflake** for warehouse storage, query execution, observability tables, and Streamlit on Snowflake
- **Snowpipe** for continuous ingestion from cloud storage into Snowflake
- **AWS S3** for raw and curated file landing zones
- **AWS Glue** for optional profiling, cataloging, and batch data processing jobs
- **AWS Lambda** for lightweight event handling, ingestion triggers, and notifications
- **dbt** for transformations, tests, data contracts, and model documentation
- **Airflow** for scheduled pipeline orchestration
- **Python agents** for data quality analysis, recommendations, and user assistance
- **LangGraph** for coordinating multiple agents
- **Streamlit** for the user interface

## Folder Structure

```text
dq-copilot/
  agents/              # Python agents for profiling, analysis, remediation, reporting
  app/
    streamlit/         # Streamlit UI, later deployable to Snowflake
  config/              # Environment settings, agent config, DQ rules
  docs/                # Architecture notes, design decisions, runbooks
  graph/               # LangGraph workflow and routing definitions
  infra/
    aws/               # S3, Glue, Lambda setup and related scripts
    snowflake/         # Snowflake objects, Snowpipe, stages, Streamlit setup
  orchestration/
    airflow/           # Airflow DAGs and orchestration helpers
  transformations/
    dbt/               # dbt project for transformations and tests
  tests/               # Unit and integration tests
```

## Folder Use Cases

### `agents/`

Future home for Python agent modules.

Examples:

- Profiling agent
- Rule discovery agent
- Anomaly detection agent
- Root cause analysis agent
- Remediation recommendation agent
- Reporting/explanation agent

### `app/streamlit/`

Future home for the user interface.

This can eventually contain the Streamlit app used by data engineers, analysts, or data stewards to ask questions, review DQ findings, and approve remediation actions.

### `config/`

Future home for configuration that should not be hardcoded.

Examples:

- Environment settings
- Agent definitions
- Data quality rules
- Snowflake object names
- AWS resource names
- Model/provider settings

### `docs/`

Future home for human-readable documentation.

Examples:

- Architecture overview
- Data flow diagrams
- Runbooks
- Deployment notes
- Design decisions

### `graph/`

Future home for LangGraph orchestration.

This is where we will define how agents coordinate, pass state, retry failures, branch decisions, and produce final responses.

### `infra/aws/`

Future home for AWS-side setup and scripts.

Examples:

- S3 landing zone notes
- Glue job scripts
- Lambda handlers
- IAM policy templates
- Event notification setup

### `infra/snowflake/`

Future home for Snowflake setup files.

Examples:

- Database and schema creation
- Warehouses
- Stages
- File formats
- Snowpipe definitions
- Observability tables
- Streamlit deployment SQL

### `orchestration/airflow/`

Future home for Airflow DAGs.

Airflow can coordinate ingestion, profiling, dbt builds, DQ checks, and alerts.

### `transformations/dbt/`

Future home for the dbt project.

This will contain staging models, mart models, tests, macros, source definitions, freshness checks, and data contract logic.

### `tests/`

Future home for automated tests.

Examples:

- Agent unit tests
- Graph workflow tests
- Config validation tests
- Mocked Snowflake/AWS integration tests

## Suggested Build Order

1. Define configs and naming conventions.
2. Add Snowflake bootstrap SQL and Snowpipe setup.
3. Add the first dbt project files and tests.
4. Add AWS S3, Glue, and Lambda scripts.
5. Add Airflow DAGs.
6. Add Python agent contracts.
7. Add LangGraph orchestration.
8. Add the Streamlit UI.
9. Add tests and deployment automation.
