# Enforce linking Pull Requests to Jira

Failing to link pull requests to issues can lead to a lack of visibility into the development process, making it difficult to track progress and identify potential issues early on.

## Usage

- Create the following file `.github/workflows/jira-issue-key-checker.yml`
- Copy paste the yaml contents below to the newly create file
- Update `project: "SRENEW"` to your own project key. 
- (Optional) If you want to support multiple project checks within the same repository your can use `|` operator like `project: 'SRENEW|PROD|ENG'`


```yaml
name: JIRA Connection

on:
  pull_request:
    types:
      - opened
      - reopened
      - edited
      - synchronize

jobs:
  enforce-issue:
    runs-on: ubuntu-latest
    name: JIRA Association
    steps:
      - name: Check for JIRA ISSUE
        id: check
        uses: usehaystack/jira-pr-link-action@v4
        with:
          ignore-author: dependabot[bot]
          project: "SRENEW"
```
