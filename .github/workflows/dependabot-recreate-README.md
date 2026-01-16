# Dependabot Recreate Workflow

This workflow allows you to trigger a recreation of all open Dependabot pull requests in a specified GitHub repository.

## Usage

1. Go to the **Actions** tab in this repository
2. Select **Dependabot Recreate** from the workflow list
3. Click **Run workflow**
4. Fill in the parameter:
   - **repository**: Target repository where Dependabot PRs should be recreated
     - Examples: `owner/repo` or `https://github.com/owner/repo`

## Features

- **Automatic Detection**: Automatically identifies all open pull requests created by Dependabot
- **Bulk Recreation**: Adds "@dependabot recreate" comment to all Dependabot PRs in a single run
- **Rate Limiting**: Includes a 5-second delay between processing PRs to avoid hitting API rate limits
- **Error Resilience**: Errors when adding comments are logged but do not abort processing of remaining PRs

## What it does

The workflow performs the following steps:

1. Parses the repository parameter (accepts both full GitHub URLs and `owner/repo` format)
2. Fetches all open pull requests from the specified repository
3. Filters to find only PRs created by Dependabot
4. Adds a comment "@dependabot recreate" to each Dependabot PR
5. The "@dependabot recreate" command triggers Dependabot to recreate the PR from scratch

## Example

To recreate all Dependabot PRs in `iobroker-bot-orga/example-repo`:

```
repository: iobroker-bot-orga/example-repo
```

Or using full URL:

```
repository: https://github.com/iobroker-bot-orga/example-repo
```

## When to use this

This workflow is useful when you need to:
- Refresh outdated Dependabot PRs with the latest base branch changes
- Trigger Dependabot to re-run security checks
- Force Dependabot to recreate PRs that may have become stale or conflicted
