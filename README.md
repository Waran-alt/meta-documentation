# Meta Directory

This directory contains all project-wide meta-documentation, guidelines, and organizational resources for development and maintenance.

## Purpose

The `meta/` folder centralizes:
- **Templates**: Generic, reusable documentation standards (`templates/`)
- **Outputs**: Project-specific generated files (`outputs/`)
- **Custom**: Project-specific configurations and guidelines (`custom/`)

This organization provides a single source of truth for project governance while maintaining clear separation between reusable and project-specific content.

## Structure

### Three-Tier Organization

```
meta/
├── templates/                        # Generic, reusable templates
│   └── [module]/                     # Template categories
│       ├── [content]/                # Template files and standards
│       └── README.md                 # Usage guidelines
├── outputs/                          # Project-specific generated files
│   └── [module]/                     # Output categories
│       └── [generated-content]/      # Actual output files
└── custom/                           # Project-specific customizations
    ├── public/                       # Tracked customizations (shared)
    └── private/                      # Local customizations (ignored by git)
```

### Current Implementation

- **`templates/work_history/`** - Templates and conventions for Work History Entry Files (WHEF)
- **`outputs/work_history/`** - Generated Work History Entry Files and project tracking
- **`custom/public/`** - Shareable project-specific documentation and guidelines
- **`custom/private/`** - Private project-specific notes and personal files

## Key Principles

- **Separation**: Generic templates vs project-specific outputs vs custom configurations
- **Reusability**: Templates can be used across multiple projects  
- **Flexibility**: Choose what custom content is shared (public) vs private
- **Consistency**: Parallel structure between templates and outputs
- **Scalability**: Easy to add new modules following the same pattern

## Workflow

1. **Define**: Create generic templates in `templates/[module]/`
2. **Generate**: Use templates to create files in `outputs/[module]/`
3. **Customize**: Add project-specific content in `custom/public/` or `custom/private/`
4. **Maintain**: Update templates as processes evolve

## Benefits

- **Professional Organization**: Clear, logical structure
- **Portfolio Ready**: Demonstrates excellent organizational skills
- **Maintainable**: Easy to understand and extend
- **Portable**: Templates can be reused across projects
- **Flexible**: Choose what custom content to share or keep private

## Expansion

New modules follow the same pattern:
```
templates/[new-module]/    # Generic templates and rules
outputs/[new-module]/      # Generated project files
```

Common expansions might include:
- **Code Standards**: Linting rules, style guides
- **Testing**: Test templates and results
- **Deployment**: Configuration templates and logs
- **Documentation**: API docs, user guides 