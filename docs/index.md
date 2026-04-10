# Continuous Intelligence

This site provides documentation for this project.
Use the navigation to explore module-specific materials.

## How-To Guide

Many instructions are common to all our projects.

See
[⭐ **Workflow: Apply Example**](https://denisecase.github.io/pro-analytics-02/workflow-b-apply-example-project/)
to get these projects running on your machine.

## Project Documentation Pages (docs/)

- **Home** - this documentation landing page
- **Project Instructions** - instructions specific to this module
- **Your Files** - how to copy the example and create your version
- **Glossary** - project terms and concepts

## Additional Resources

- [Suggested Datasets](https://denisecase.github.io/pro-analytics-02/reference/datasets/cintel/)

## Custom Project

### Dataset
Two CSV files: a **reference** dataset and a **current** dataset (recent behavior).
Each contains `requests`, `errors`, and `total_latency_ms` columns, where each row is one system observation.

### Signals
Three difference signals (current avg minus reference avg) with drift flags:
- `requests_mean_difference` — flagged if absolute difference > 20.0
- `errors_mean_difference` — flagged if absolute difference > 2.0
- `latency_mean_difference_ms` — flagged if absolute difference > 1000.0

### Experiments
Added rows to `current_metrics_jugurtha.csv` that mirror reference values,
to test whether the pipeline would correctly resolve previously detected drift.

### Results
All three drift flags returned `False` after adding the reference values —
no drift detected.

### Interpretation
Mean-based drift detection self-corrects as accurate data accumulates.
A drift flag signals a need to investigate, not necessarily a permanent failure —
if values stabilize, the flag clears on its own.
