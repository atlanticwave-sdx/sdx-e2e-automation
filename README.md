# sdx-e2e-automation

**End-to-End (E2E) Automation Framework for AtlanticWave-SDX**

This repository manages the automation of SDX end-to-end tests, result reporting, and GitHub Projects CI/CD integration. It is designed to extract, parse, and update test statuses from `results.xml` into GitHub Project fields.

---

## Features

- Parses JUnit-style XML test reports (`pytest --junitxml`)
- Updates GitHub Projects V2:
  - Test status (`Pass`, `Fail`, `Skipped`)
  - Test reason (detailed output and traceback)
  - Tracks `passes`, `fails`, `lastpass`, `lastfail`
- Triggered manually or via GitHub Actions
- Designed to integrate with containerized test environments 
( Docker/Mininet)

---

## Repo Structure

sdx-e2e-automation/
update_project_from_results.py   # Core script for syncing results 
results/  # Directory for incoming JUnit XML files 
 results.xml  # Sample results file 
.github/workflows/update-project.yml      # GitHub Actions workflow (manual trigger) 

---

## Environment Variables

The script relies on the following environment variables:

| Variable Name           | Description                          |
|------------------------|--------------------------------------|
| `GITHUB_TOKEN`         | GitHub token with project write access |
| `GITHUB_ORG`           | GitHub organization name              |
| `GITHUB_PROJECT_NUMBER`| Project number (not ID)               |

You can export them locally:

```bash
export GITHUB_TOKEN=ghp_...
export GITHUB_ORG=atlanticwave-sdx
export GITHUB_PROJECT_NUMBER=16

## Running the Script
python3 update_project_from_results.py

