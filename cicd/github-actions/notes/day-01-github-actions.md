# Day 01 — GitHub Actions & CI/CD Basics

## WHAT?

GitHub Actions is a CI/CD automation platform provided by GitHub.

It helps automate:

* testing
* building
* Docker image creation
* deployment
* workflows

using YAML files.

---

# WHY?

Manual deployment and build processes are slow and error-prone.

GitHub Actions helps:

* automate repetitive tasks
* improve consistency
* reduce manual work
* enable CI/CD pipelines

---

# HOW?

A workflow YAML file is created inside:

```text id="jlwm1m"
.github/workflows/
```

GitHub automatically detects the workflow and executes it when trigger events happen.

Example trigger:

```yaml id="wjlwm4"
on:
  push:
    branches: [master]
```

This workflow runs whenever code is pushed to the master branch.

---

# WORKFLOW STRUCTURE UNDERSTANDING

Basic flow:

```text id="4jlwmv"
Trigger
→ Runner
→ Checkout Code
→ Docker Login
→ Build Image
→ Push Image
```

---

# WORKFLOW USED

```yaml id="8jlwm1"
name: CI

on:
  push:
    branches: [master]

jobs:
  build-and-push:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Docker setup [login]
        uses: docker/login-action@v3
        with:
          username: ${{ vars.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}

      - name: Docker build and push
        uses: docker/build-push-action@v6
        with:
          context: ./frontend
          push: true
          tags: ${{ vars.DOCKERHUB_USERNAME }}/devboard-frontend-master:latest
```

---

# IMPORTANT CONCEPTS LEARNED

## 1. GitHub Runner

GitHub creates a temporary virtual machine called a runner to execute workflow steps.

---

## 2. uses vs run

### uses

Used for reusable GitHub Actions.

Example:

```yaml id="vjlwm1"
uses: actions/checkout@v4
```

### run

Used for shell commands.

Example:

```yaml id="2jlwm4"
run: npm install
```

---

# 3. Secrets & Variables

## Secrets

Used for sensitive data.

Example:

```yaml id="9jlwm0"
${{ secrets.DOCKERHUB_TOKEN }}
```

## Variables

Used for reusable non-sensitive values.

Example:

```yaml id="7jlwm2"
${{ vars.DOCKERHUB_USERNAME }}
```

---

# 4. Docker Build Context

```yaml id="0jlwm7"
context: ./frontend
```

The build context tells Docker:

* where Dockerfile exists
* where application source code exists

Wrong context causes build failure.

---

# PROBLEM FACED

Workflow initially failed because Docker could not find the Dockerfile.

---

# ROOT CAUSE

Incorrect Docker build context path.

---

# FIX

Updated:

```yaml id="6jlwm8"
context: ./frontend
```

to point to correct folder containing the Dockerfile.

---

# REALIZATION

DevOps learning is not about memorizing YAML syntax.

It is about:

* understanding workflow sequence
* automation logic
* debugging failures
* solving problems

---

# KEY TAKEAWAYS

* GitHub Actions automates CI/CD workflows
* YAML defines workflow structure
* Docker login requires secrets
* Build context is very important
* Workflow failures help learning faster
* Official documentation is important

---

# NEXT TARGET

* Multi-job workflows
* Slack integration
* Jira integration
* Deployment workflows
* Kubernetes deployment pipelines

