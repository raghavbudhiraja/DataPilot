# DataPilot --- Agentic Data Analyst

DataPilot is a polished, demo-ready AI-assisted analytics application
that answers natural-language questions about tabular data by selecting
and executing analytical tools. Numerical answers must be grounded in
actual computations over the active dataset.

## Project goals

Build a reliable, full-stack data-analysis experience that works
immediately after launch, without requiring an API key, a file upload,
or manual configuration.

The default experience should load a realistic retail or e-commerce
dataset automatically and let an evaluator explore the application
through a professional analytics dashboard and natural-language analysis
interface.

## Core requirements

### Analytical tools

Implement at least seven genuinely distinct tools:

1.  **Dataset profiling and data quality** --- inspect schema, types,
    missing values, duplicates, and other quality indicators.
2.  **Statistical analysis** --- calculate descriptive statistics and
    numerical summaries.
3.  **Filtering, grouping, aggregation, and ranking** --- answer
    questions about subsets, group-level metrics, and top or bottom
    performers.
4.  **Correlation analysis** --- compute correlations between numeric
    variables and identify the strongest relationships.
5.  **Time-series trend analysis** --- aggregate date-based metrics over
    time and describe changes in trend.
6.  **Statistical anomaly detection** --- identify unusual records or
    values using a documented statistical method.
7.  **Data visualization** --- generate charts that reflect computed
    results.

The agent should select and execute appropriate tools for each question.
Do not hardcode example answers, fabricate results, or run unrestricted
model-generated code.

### Dashboard and user experience

The application should include:

-   A professional, modern analytics dashboard.
-   Dataset overview, data preview, and data-quality metrics.
-   Interactive charts and tables.
-   A natural-language question input.
-   Clickable example questions that execute real analyses.
-   Visible tool-execution history and computed outputs.
-   Clear answers supported by numerical evidence.
-   Graceful handling of invalid questions, missing columns, unsupported
    data, and other errors.
-   Optional CSV and Excel uploads, while keeping uploads unnecessary
    for the default demonstration.

### Demonstration questions

Provide working examples such as:

-   Which five products generate the most revenue?
-   Which region performs best?
-   How has monthly revenue changed?
-   Which month had the largest decline?
-   Are there unusual transactions?
-   Which numerical variables are most strongly correlated?

Every example must run against the active dataset and derive its answer
from real computations.

## Technical expectations

-   **Language:** Python
-   **Data analysis:** pandas
-   **Frontend:** Streamlit is the preferred default unless the existing
    workspace provides a better-fitting stack.
-   **Agent behavior:** Use an LLM with tool calling only if an existing
    connection is available. Otherwise, implement a reliable
    deterministic agent that works without API keys and describe it
    honestly as deterministic rather than LLM-powered.
-   **Dataset compatibility:** Support unfamiliar tabular datasets and
    infer likely semantic columns despite different column names.
-   **Safety:** Never execute unrestricted model-generated code.
-   **Memory:** Add persistent memory for reusable analytical
    definitions if practical, without compromising core reliability.

## Default demo

On first launch, the app should automatically load a realistic retail or
e-commerce sample dataset. The evaluator should be able to ask questions
and inspect the results immediately, without uploading a file or
configuring credentials.

## Project deliverables

The completed repository should include:

-   The application and supporting modules.
-   A sample dataset used by the default demo.
-   Dependency and configuration files.
-   Automated tests for analytical tools and agent workflows.
-   A comprehensive README documenting architecture, analytical tools,
    limitations, and run instructions.

## Quality and verification

Before considering the project complete:

-   Run the application and automated tests where the environment
    permits.
-   Verify numerical accuracy against independently checkable
    calculations.
-   Fix discovered issues where possible.
-   Ensure the default demo works without API keys, uploads, or manual
    setup.
-   Clearly distinguish checks that were actually run from checks that
    could not be run.
-   Do not claim tests passed unless they were executed.

## Suggested architecture

A maintainable implementation can separate responsibilities into modules
such as:

-   **Data loading:** sample data, CSV and Excel imports, and
    validation.
-   **Profiling:** schema, quality metrics, and dataset summaries.
-   **Analysis tools:** statistics, aggregation, correlation, trends,
    and anomaly detection.
-   **Agent/router:** map natural-language questions to safe, typed tool
    calls.
-   **Visualization:** build charts from computed data.
-   **User interface:** dashboard, question input, examples, execution
    history, and result display.
-   **Tests:** deterministic checks for tool outputs, routing, edge
    cases, and numerical correctness.

This is a suggested separation of concerns, not a requirement to use
these exact filenames or modules.

## Limitations and transparency

-   Results depend on the quality and meaning of the uploaded or sample
    data.
-   Column detection for unfamiliar datasets is heuristic and should
    report ambiguity rather than silently inventing semantics.
-   Correlation does not establish causation.
-   Anomaly detection flags statistical unusualness; it does not by
    itself prove that a transaction is fraudulent or erroneous.
-   If no LLM connection is available, natural-language routing should
    use documented deterministic rules and must not be represented as an
    LLM.
-   The interface should explain when a question cannot be answered
    reliably from the available columns.

## Running the application

The final README should include the exact commands needed to install
dependencies, launch the application, and run tests, based on the files
and tooling actually present in the repository. For a Streamlit
implementation, the expected commands would typically be:

``` bash
python -m venv .venv
# Activate the virtual environment for your operating system.
pip install -r requirements.txt
streamlit run app.py
```

Run tests with the project's configured test command, commonly:

``` bash
pytest
```

Adjust these commands to match the final repository structure. Do not
document commands or capabilities that have not been verified.

## Completion standard

DataPilot is ready for demonstration when it launches with its sample
dataset, supports the seven analytical capabilities, executes example
questions against real data, presents evidence and tool history clearly,
handles common errors gracefully, and has tests and documentation that
accurately reflect the implementation.
