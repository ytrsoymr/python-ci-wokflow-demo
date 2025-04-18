# GitHub Actions Guide

## 🔧 What is GitHub Actions?
GitHub Actions lets you automate tasks like:
- Running tests on every pull request
- Deploying your app when code is pushed to main
- Linting and formatting your code automatically

## 🧠 Core Concepts
- **Workflow**: A YAML file that defines the automation process. It's stored in `.github/workflows/`.
- **Job**: A set of steps that run on the same runner.
- **Step**: A single task (e.g., running a script, installing dependencies).
- **Action**: A reusable extension that performs a task (e.g., checkout code, set up Python).
- **Runner**: The server where jobs run (GitHub provides these, or you can self-host).

## 🚀 Basic Example
Here's a workflow that runs Python tests on push:

```yaml
# .github/workflows/python-app.yml
name: Python Application

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'

      - name: Install dependencies
        run: |
          pip install -r requirements.txt

      - name: Run tests
        run: |
          pytest
