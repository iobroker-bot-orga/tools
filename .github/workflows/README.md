# Copy Issues Workflow

This workflow allows you to copy issues from one GitHub repository to another.

## Usage

1. Go to the **Actions** tab in this repository
2. Select **Copy Issues** from the workflow list
3. Click **Run workflow**
4. Fill in the parameters:
   - **target**: Target repository where issues should be created
     - Examples: `owner/repo` or `https://github.com/owner/repo`
   - **source**: Source repository or specific issue to copy
     - Examples: 
       - Single issue: `https://github.com/owner/repo/issues/123`
       - Repository: `owner/repo` or `https://github.com/owner/repo`
   - **force**: Force copy even if issue already exists (default: false)
   - **include-closed**: Include closed issues when copying from a repository (default: false)

## Features

- **Duplicate Detection**: By default, the workflow checks if an issue with the same title that references the original issue already exists in the target repository
- **Metadata Preservation**: Each copied issue includes:
  - Link to the original issue
  - Original creator's username
  - Original creation timestamp
  - All original content with formatting preserved
- **Comment Copying**: All comments from the original issue are copied with attribution
- **Rate Limiting**: Automatically adds a 1-minute delay between processing multiple issues to avoid hitting API rate limits

## Example

To copy all open issues from `source-org/source-repo` to `target-org/target-repo`:

```
target: target-org/target-repo
source: source-org/source-repo
force: false
include-closed: false
```

To copy a specific issue:

```
target: target-org/target-repo
source: https://github.com/source-org/source-repo/issues/42
force: false
include-closed: false
```
