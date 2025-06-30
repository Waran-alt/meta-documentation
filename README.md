# Meta-Documentation Templates

This repository contains reusable documentation templates designed for git submodule integration across multiple projects.

## Purpose

The `meta-documentation/` submodule provides:
- **Templates**: Generic, reusable documentation standards (`templates/`)

This organization provides a single source of truth for documentation templates that can be reused across multiple projects.

## Structure

### Git Submodule Organization

```
your-project/
├── meta-documentation/               # This git submodule
│   └── templates/                    # Generic, reusable templates
│       └── [module]/                 # Template categories
│           ├── [content]/            # Template files and standards
│           └── README.md             # Usage guidelines
└── meta-documentation-outputs/       # Project-specific generated files (recommended name)
    └── [module]/                     # Output categories matching templates
        └── [generated-content]/      # Actual output files
```

### Current Implementation

- **`templates/work_history/`** - Templates and conventions for Work History Entry Files (WHEF)

### Project-Level Usage

Projects using this submodule should create their own outputs directory (e.g., `meta-documentation-outputs/`) at the project root level, outside the submodule directory.

## Key Principles

- **Separation**: Generic templates (in submodule) vs project-specific outputs (in parent project)
- **Reusability**: Templates can be used across multiple projects  
- **Consistency**: Parallel structure between templates and outputs
- **Scalability**: Easy to add new modules following the same pattern

## Workflow

1. **Add Submodule**: Add meta-documentation as a git submodule to your project
2. **Create Outputs**: Create project-level outputs directory (e.g., `meta-documentation-outputs/`)
3. **Generate**: Use templates to create files in your project's outputs directory
4. **Maintain**: Templates evolve in this repo, outputs stay in your project

## Benefits

- **Professional Organization**: Clear, logical structure
- **Portfolio Ready**: Demonstrates excellent organizational skills
- **Maintainable**: Easy to understand and extend
- **Portable**: Templates can be reused across projects
- **Version Controlled**: Template updates can be managed via git submodule updates

## Adding to Your Project

```bash
# Add as git submodule
git submodule add https://github.com/Waran-alt/meta-documentation.git meta-documentation

# Create project-level outputs directory
mkdir meta-documentation-outputs

# Initialize submodule
git submodule update --init --recursive
```

## Expansion

New modules follow the same pattern:
```
templates/[new-module]/    # Generic templates and rules (in submodule)
meta-documentation-outputs/[new-module]/ # Generated project files (in parent project)
```

Common expansions might include:
- **Code Standards**: Linting rules, style guides
- **Testing**: Test templates and results
- **Deployment**: Configuration templates and logs
- **Documentation**: API docs, user guides 