# GitHub Actions Lab - Automated Workflows

Repository: GitHubActionsLab-YourName

## Overview
This lab demonstrates two GitHub Actions workflows:
1. **Workflow 1 (dependent-jobs.yml)** shows job dependencies and execution order using `needs`.
2. **Workflow 2 (multi-platform.yml)** shows parallel jobs running on multiple operating systems using `runs-on`.

---

## Workflow 1: Dependent Jobs (Build → Test → Deploy)
**File:** `.github/workflows/dependent-jobs.yml`  
**Trigger:** `push` to the `main` branch

### Purpose
Demonstrates how to enforce a strict job order:
- `build` runs first
- `test` runs only after `build` succeeds
- `deploy` runs only after `test` succeeds

### Key Concepts
- **needs:** Creates job dependencies and controls order.
- **runs-on:** Defines the runner OS (`ubuntu-latest`).
- **steps:** Each job has multiple steps to show progress.

---

## Workflow 2: Multi-Platform Testing (Parallel Jobs)
**File:** `.github/workflows/multi-platform.yml`  
**Trigger:** `pull_request` to the `main` branch

### Purpose
Demonstrates running independent jobs in parallel on:
- Ubuntu (`ubuntu-latest`)
- Windows (`windows-latest`)
- macOS (`macos-latest`)

Each job:
- Checks out the repo (`actions/checkout@v4`)
- Prints OS information
- Runs an OS-specific command (`uname -a` on Linux/Mac, `systeminfo` on Windows)
- Creates a file and prints its contents

### Key Concepts
- **runs-on:** Selecting different OS runners.
- **No needs:** Jobs run simultaneously (parallel execution).
- **uses:** Using official actions like `actions/checkout@v4`.

---

## Screenshots to Submit (Checklist)
- Workflow file contents (both YAML files)
- Actions tab showing both workflows
- Workflow 1 visualization showing Build → Test → Deploy order
- Workflow 2 showing Ubuntu/Windows/macOS jobs running in parallel
- Logs showing successful execution for both workflows

---

## Challenges Faced / Fixes
(Write what happened for you, examples:)
- YAML indentation issues fixed by validating formatting
- Windows commands required PowerShell (`shell: pwsh`) instead of bash
- Trigger conditions verified by pushing to `main` and creating a PR
