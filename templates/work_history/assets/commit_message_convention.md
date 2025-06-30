# Conventional Commit Messages
From : https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13#file-conventional-commits-cheatsheet-md

## Commit Message Formats

### General Commit
To create a commit message, use the following format:
```
<type>(<optional scope>): <description>
<optional body>
<optional footer>
```

Here's a breakdown of the components:
- type: The type of commit (see Type below)
- scope: Optional context for the commit (see Scope below)
- description: A concise description of the change (see Description below)
- body: Optional additional context for the commit (see Body below)
- footer: Optional information about breaking changes or issue references (see Footer below)

### Initial Commit 
`chore: init`

### Merge Commit
Follows default git merge message : `Merge branch '<branch name>'`

### Revert Commit
Follows default git revert message : `Revert "<reverted commit subject line>"`

### Type
- `docs`: Documentation changes (when the commit only focus on updating README, API docs, or other project documentation)
- `feat`: New features (adding or replacing a functionality, capability, or user interface element)
- `fix`: Bug fixes (resolving issue, patching vulnerability...)
- `refactor`: Code refactoring (improving code structure, readability, or performance without changing functionality)
- `test`: Adding tests
- `chore`: Routine maintenance tasks (cleanup tasks, updating dependencies...)
- `perf`: Performance optimizations
- `infra`: Infrastructure changes (configuration, build system, CI/CD pipeline...)
- `revert`: Reverting changes (reverting a commit or restoring a previous version)
- `data`: Changes related to data (adding or updating content, translations, or other data...)
- `init`: Initial commit
- `merge`: Specific for merging commit
- `misc`: Commits that don't fit elsewhere (you can propose new types in this case)

### Scope
- Use scopes to provide additional context and clarity when the changes made in the commit are specific to a particular area or component of the project. This helps to quickly understand the nature and impact of the changes. For example:
  - `login`: Changes related to the login feature
  - `dashboard`: Changes related to the dashboard component
  - `api`: Changes related to the API or backend infrastructure
- **Do not** use issue identifiers as scopes
- Scopes are not allowed in init commit and merge commit

### Breaking Changes Indicator
- A commit that introduce breaking changes **must** be indicated by an `!` before the `:` in the subject line (e.g., `feat(api)!: remove support for legacy intent format`)
- Breaking changes **should** be described in the commit footer section, if the commit description isn't sufficiently informative

### Description
The `description` contains a concise description of the change. 
- The description is a **mandatory** part
- Use the imperative, present tense: "change" not "changed" nor "changes"
  - Think of `This commit will...` or `This commit should...`
- **Do not** capitalize the first letter
- **Do not** end the description with a period (`.`)

### Body
The `body` should include the motivation for the change and contrast this with previous behavior.
- The body is an **optional** part
- Use the imperative, present tense: "change" not "changed" nor "changes"

### Footer
The `footer` should contain issue references and informations about **Breaking Changes**
- The footer is an **optional** part, except if the commit introduce breaking changes
- *Optionally* reference issue identifiers (e.g., `Closes #123`, `Fixes JIRA-456`) 
- **Breaking Changes** **must** start with the word `BREAKING CHANGE:`
  - For a single line description just add a space after `BREAKING CHANGE:`
  - For a multi line description add two new lines after `BREAKING CHANGE:`

### Versioning
- **If** your next release contains commit with...
  - **Breaking Changes** incremented the **major version**
  - **API relevant changes** (`feat` or `fix`) incremented the **minor version**
- **Else** increment the **patch version**


### Examples
- ```
  feat: add email notifications on new direct messages
  ```
- ```
  feat(shopping cart): add the amazing button
  ```
- ```
  feat!: remove ticket list endpoint

  refers to JIRA-1337

  BREAKING CHANGE: ticket endpoints no longer supports list all entities
  ```
- ```
  fix(shopping-cart): prevent order an empty shopping cart
  ```
- ```
  fix(api): fix wrong calculation of request body checksum
  ```
- ```
  fix: add missing parameter to service call

  The error occurred due to <reasons>.
  ```
- ```
  perf: decrease memory footprint for determine unique visitors by using HyperLogLog
  ```
- ```
  build: update dependencies
  ```
- ```
  build(release): bump version to 1.0.0
  ```
- ```
  refactor: implement fibonacci number calculation as recursion
  ```
- ```
  style: remove empty line
  ```
