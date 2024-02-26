# GitHub Actions

GitHub Actions is a CI/CD pipeline directly integrated with your GitHub repository.

GitHub Actions files are defined as YAML files located in the .github/workflow folder in your repo.

**Workflow Runs** - Basically cloudwatch logs, tells you if the action was a succes or a failure and how long it took to run.

## Event Triggers

An event trigger causes a GitHub Action to run. The "on" attribute specifies the event trigger to be used.

Examples of common GitHub Actions that could be triggered:

- Pushes
- Pull Requests
- Issues
- Releases
- Scheduled Events
- Manual Triggers