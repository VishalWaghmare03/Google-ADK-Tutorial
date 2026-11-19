# How to Use GitHub Tools with AI Agents

This guide explains how to effectively use GitHub tools via Model Context Protocol (MCP) and GitHub API integrations for automated repository management, file operations, and workflow automation.

---

## 1. Overview of Key GitHub Tools

GitHub tools allow AI agents and developers to interact directly with GitHub repositories remotely. Key capabilities include:

- **Repository Management**: Search, list, create, or fork repositories.
- **File Operations**: Create, read, update, or delete files directly on remote branches.
- **Branch & Pull Request Workflows**: Create branches, submit PRs, request reviews, and merge changes.
- **Issue Tracking**: Create, update, comment on, and manage issues and sub-issues.
- **Code & Commit Search**: Find specific functions, files, or commit logs across GitHub.

---

## 2. Common Workflows & Tool Examples

### A. Repository Operations

- **Creating a Repository**:
  - Tool: `create_repository`
  - Parameters: `name`, `description`, `private`, `autoInit`
  - Example: Create a new project repository initialized with a README.

- **Listing Repositories**:
  - Tool: `search_repositories`
  - Query: `user:<username>` to discover user projects.

### B. File Management on GitHub

- **Creating or Updating Files**:
  - Tool: `create_or_update_file` / `push_files`
  - Requires: `owner`, `repo`, `path`, `content`, `message`, `branch`.
  - *Tip*: When updating an existing file, retrieve its blob SHA using `get_file_contents` first.

- **Pushing Multiple Files at Once**:
  - Tool: `push_files`
  - Allows single-commit updates for multiple files across a branch.

### C. Issue Management

- **Creating an Issue**:
  - Tool: `issue_write` (method: `create`)
  - Parameters: `owner`, `repo`, `title`, `body`, `labels`, `assignees`

- **Reading Issues & Hierarchy**:
  - Tool: `issue_read` (method: `get`, `get_comments`, `get_sub_issues`)

### D. Pull Request & Review Workflows

- **Creating a Branch**:
  - Tool: `create_branch` (from default branch or base branch).

- **Opening a Pull Request**:
  - Tool: `create_pull_request`
  - Parameters: `owner`, `repo`, `title`, `head`, `base`, `body`

- **Reviewing & Merging PRs**:
  - Tool: `pull_request_review_write` / `merge_pull_request`

---

## 3. Best Practices for GitHub Automation

1. **Check Existing State First**: Before modifying or creating files, check current branch status, blob SHAs, or existing issues.
2. **Atomic Commits**: Group related changes in single commits using multi-file push tools (`push_files`).
3. **Use Informative Descriptors**: Write meaningful commit messages and detailed PR descriptions to maintain clear repository history.
4. **Security & Secrets**: Avoid committing API keys, tokens, or sensitive credentials. Run secret scanning before pushing code.

---

*Generated for Google ADK Tutorial.*
