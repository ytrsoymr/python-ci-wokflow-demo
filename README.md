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
```

File Header
```yaml

name: Python Application
```
This sets "Python Application" as the display name for the workflow in the GitHub Actions UI.
Trigger Configuration
```yaml
on: [push]
This workflow runs whenever code is pushed to any branch in the repository.
```
Alternative Trigger Example
You could limit the workflow to specific branches:
```yaml
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
```
This would run the workflow only on pushes or pull requests to the main branch.
Job Configuration
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
```
jobs contains all the jobs that will run in this workflow
build is the name for this specific job
The job runs on the latest Ubuntu virtual machine environment provided by GitHub

# Workflow Steps
## 1. Checkout Code
```yaml
steps:
  - name: Checkout code
    uses: actions/checkout@v3
```
This step pulls the code from your repository, making it available to subsequent steps.
## 2. Set up Python
```yaml
 - name: Set up Python
    uses: actions/setup-python@v4
    with:
      python-version: '3.10'
```
This configures Python 3.10 on the runner environment.
## 3. Install Dependencies
```yaml
  - name: Install dependencies
    run: |
      pip install -r requirements.txt
```
This installs all the project dependencies specified in your requirements.txt file.
## 4. Run Tests
```yaml
  - name: Run tests
    run: |
      pytest
```
This executes your Python tests using pytest.

# 💡 Summary:
## This workflow:

Triggers on any push

1. Runs a job on Ubuntu

2. Checks out your code

3. Sets up Python 3.10

4. Installs dependencies from requirements.txt

5. Runs tests with pytest

🏁 Try It Yourself
1. Fork or clone the repo.

2. Push a change to calculator.py or test_calculator.py.

3. Go to the Actions tab on GitHub.

4. See your workflow running automatically!

