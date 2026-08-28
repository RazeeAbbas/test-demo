# GitHub Actions Pipeline Troubleshooting Guide

This guide documents common GitHub Actions CI/CD pipeline failures,
their causes, fixes, and prevention methods.

The purpose of this guide is to help identify and resolve common
pipeline problems during development and deployment.

## 1. Syntax Error

### Problem

The GitHub Actions workflow contains invalid YAML syntax.

### Example

```yaml
steps:
  - name: Run Test
    run: pytest
      echo "Testing"


---

# Step 12: Scenario 2 — Missing Secret

```markdown
## 2. Missing Secret

### Problem

The workflow expects a secret but the secret has not been configured.

### Cause

The repository secret does not exist or has been given the wrong name.

### Fix

Go to:

GitHub → Settings → Secrets and variables → Actions → Secrets

Create the required secret.

For example:

```text
DEMO_SECRET


---

# Step 13: Scenario 3 — Wrong Path

```markdown
## 3. Wrong File or Directory Path

### Problem

The workflow cannot find a file or directory.

### Example

```bash
cp app.py build/


---

# Step 14: Scenario 4 — Failed Test

```markdown
## 4. Failed Test

### Problem

The automated test returns a failure.

### Example

```text
FAILED test_app.py


---

# Step 15: Scenario 5 — Permission Issue

```markdown
## 5. Permission Issue

### Problem

A pipeline command cannot access or execute a file.

### Example

```text
Permission denied



---

# Step 16: Scenario 6 — Dependency Issue

```markdown
## 6. Dependency Issue

### Problem

The workflow cannot install or find a required dependency.

### Example

```text
ModuleNotFoundError


---

# Step 17: Scenario 7 — Branch Trigger Issue

```markdown
## 7. Branch Trigger Issue

### Problem

The workflow does not start after pushing code.

### Cause

The workflow trigger may be configured for a different branch.

For example:

```yaml
on:
  push:
    branches:
      - main

      
---

# Step 18: Scenario 8 — Artifact Upload Failure

```markdown
## 8. Artifact Upload Failure

### Problem

The workflow cannot upload the build artifact.

### Example

```text
No files were found with the provided path


---

# Step 19: Scenario 9 — Docker Build Failure

```markdown
## 9. Docker Build Failure

### Problem

The Docker image cannot be built.

### Example

```text
failed to solve


---

# Step 20: Scenario 10 — Timeout

```markdown
## 10. Pipeline Timeout

### Problem

A workflow runs for too long and is automatically stopped.

### Example

```text
The job exceeded the maximum execution time


---

# Step 21: Add a troubleshooting summary table

At the end of the file, add:

```markdown
# Troubleshooting Summary

| Failure | Common Cause | Main Fix |
|---|---|---|
| Syntax Error | Invalid YAML | Fix YAML syntax/indentation |
| Missing Secret | Secret not configured | Add repository secret |
| Wrong Path | Incorrect file path | Verify path |
| Failed Test | Code doesn't meet expected result | Fix code/test |
| Permission Issue | Insufficient permissions | Correct permissions |
| Dependency Issue | Missing/incompatible package | Fix dependencies |
| Branch Trigger | Wrong workflow trigger | Check branch configuration |
| Artifact Failure | Artifact path missing | Create/check build path |
| Docker Build Failure | Dockerfile/build problem | Fix Dockerfile/build |
| Timeout | Step takes too long | Investigate and optimize |
