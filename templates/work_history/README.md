# Work History Documentation System

This system provides a structured approach to documenting changes, decisions, and progress throughout a project's development lifecycle.

## Overview

The work history documentation system is designed to:
- Track changes and their context
- Document technical decisions
- Maintain project knowledge
- Support future maintenance
- Facilitate team collaboration

## Structure

### File Organization
The file organization follows the meta-documentation submodule structure:
```
your-project/
├── meta-documentation/                  # Git submodule
│   └── templates/work_history/          # This directory - Rules and templates
│       ├── assets/                      # Template files and standards
│       │   ├── conversation_tracking.md # Context tracking template
│       │   ├── commit_message_convention.md # Commit standards
│       │   └── TEMPLATE.md              # WHEF template
│       └── README.md                    # This file
└── meta-documentation-outputs/          # Project-level outputs directory
    └── work_history/                    # Generated files location
        └── branches/                    # Branch-specific documentation
            ├── [branch-name]/           # Documentation for any branch
            │   ├── [WHEF]               # .md files
            │   └── ...
            └── ...
```

### Branch Organization
The system supports documentation for any branch in your project, for example:
- `main/` - For main branch documentation
- `dev/` - For development branch documentation
- `feature/` - For feature branches
- `bugfix/` - For bug fixes
- `release/` - For release branches
- Any other branch structure your project uses

Each branch folder in `meta-documentation-outputs/work_history/branches/` contains its own chronological documentation, maintaining a clear history of changes specific to that branch.

## Conventions

### Naming Conventions
For commit:
- Please refer to `assets/commit_message_convention.md`
- If the commit is associated with a WHEF (mostly the case), add a reference at the end of the description: `<description> - WHEF #XXX`

The naming convention for WHEF is: `XXX-dd_MM_yyyy-type(scope)-title.md`

### Intern numbers (`XXX`):
- Refer to a specific work history entry file (WHEF)
- Branch-specific numbering: each branch maintains its own sequence
- Start with 001 for first commit of the branch **after initial commit**
- Increment by 1 for each new commit of the branch
- Always use 3 digits (zero-padded)

### Date
`dd_MM_yyyy`: Date of the change (get the current date in UTC using a command)

### Type
The commit type (see #type in `assets/commit_message_convention.md`)

### Scope
The commit scope (if any, see #scope in `assets/commit_message_convention.md`)

### Title
Short title based on commit description (see #description in `assets/commit_message_convention.md`)
*Use underscores for spaces*

WHEF examples:
- `001-19_03_2024-feat(login)-user_login.md`
- `002-19_03_2024-feat(login)-login_auth.md`
- `003-20_03_2024-feat(api)-mailjet.md`
- `004-21_03_2024-fix(login)-password_hash.md`

Commits with WHEF examples:
- `chore: init`
- `feat(login): creating the user login api, web page and dtb table - WHEF #001`
- `feat(login): add password handler to user login, using bcrypt - WHEF #002`
- `feat: creating mailjet api and configuration - WHEF #003`
- ```
  fix(login)!: implementing password hashing - WHEF #004
  
  BREAKING CHANGE: password column in user dtb table is now CHAR(60)
  ```

## Usage

**PREREQUISITE: Create a work history entry file (WHEF) before committing changes. This file should be based on git status output and named according to the specified naming convention.**

**When creating a WHEF is not necessary: init commit, merge commit without any issue, trivial commit**

1. **Get git staging area**
   - Run `git status` to review the changes
   - If is empty, ask the user for changes to add in staging area, then restart the process

2. **Check if multiple commits are needed**
   - Check if changes should be separated in multiple commits for clarity:
      - If not, go to step 3
      - Else, share your thoughts with the user before proceeding:
         - If the user agree, then update the staging area and restart the process from step 1
         - Else go to step 3

3. **Create the WHEF**
   - Copy `meta-documentation/templates/work_history/assets/TEMPLATE.md` to appropriate branch folder in `meta-documentation-outputs/work_history/branches/[branch]/`
   - Rename using naming convention
   - Based on the git staging area, fill in details following template structure (including guideline parenthesis and validation checklist)

4. **Add Details**
   - Read `meta-documentation-outputs/templates/work_history/conversation_tracking.md`: Review the project's conversation tracking file to gather additional context and details about the changes made

5. **User Validation**
   - Present the draft entry to the user for review and approval
   - Only after user validation, remove all guideline parenthesis (e.g., "(must match filename)"), the validation checklist at the top, and the final checklist at the end
   - Ensure the entry is clean and ready for commit

6. **Last check before commit**
   - Run `git status` to review the changes one last time, check for unwanted or missing changes

### **Documentation Principles**
   - Be specific and precise
   - Include relevant technical details
   - Document both successes and failures
   - Focus on information useful for future reference
   - Avoid redundancy across sections

### **Best Practices**
   - Create entries for significant changes
   - Update documentation with each commit
   - Include both technical and contextual information
   - Maintain consistent format
   - Review and update as needed

### **Multiple Commits for a Single Logical Change**
   - If a single logical change requires multiple commits (e.g., staged work, large refactor):
     - Increment the commit number for each commit and create a separate work history entry for each
     - Use a consistent description prefix or part notation (e.g., 'part 1/3') in the commit messages and WHEF

## Validation Checklist

### 1. File Naming
- [ ] Date format is dd_MM_yyyy
- [ ] WHEF number follows branch sequence (XXX)
- [ ] Description is lowercase with underscores
- [ ] No special characters in filename
- [ ] File extension is .md

### 2. Work History Entry
- [ ] All required sections are present
- [ ] Date matches filename
- [ ] WHEF number matches filename and branch
- [ ] Title matches description
- [ ] Summary is clear and concise
- [ ] Changes are properly listed
- [ ] Technical details are included
- [ ] Testing section is filled
- [ ] Notes are relevant

### 3. Git Commit
- [ ] Changes are staged
- [ ] Commit message follows format
- [ ] Work history entry is created
- [ ] Branch is correct
- [ ] No sensitive data included

## Output Management

### File Organization
Generated WHEF files are stored in `meta-documentation-outputs/work_history/branches/[branch]/` following chronological order.

### Templates vs Outputs
- **Templates** (`meta-documentation/templates/work_history/`): Contains rules, conventions, and template files
- **Outputs** (`meta-documentation-outputs/work_history/`): Contains the actual generated WHEF files organized by branch

### Archive Management
- Keep all WHEF files for project history
- Maintain branch-specific organization in outputs directory
- Archive old branch directories when branches are deleted
- Preserve merge points and branch relationships

## Customization

The template can be customized for:
- Different project types
- Specific team needs
- Various documentation requirements
- Different technical domains 