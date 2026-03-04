# Architecture Analyzer Skill

Analyzes and visualizes software architecture using SciTools Understand.

## What It Does

This skill uses SciTools Understand's powerful code analysis capabilities to:
- Discover system structure and components
- Extract and visualize dependencies
- Identify architectural patterns (layered, microservices, etc.)
- Detect architectural issues (circular dependencies, tight coupling)
- Generate architecture documentation
- Calculate architecture metrics

## Features

| Feature | Description |
|---------|-------------|
| **Structure Discovery** | Maps directories, files, and their relationships |
| **Dependency Analysis** | Exports file/class dependencies in multiple formats |
| **Pattern Detection** | Identifies layered, microservices, modular architectures |
| **Complexity Analysis** | Finds complexity hotspots and coupling issues |
| **Documentation** | Generates HTML reports, CSV exports, and diagrams |
| **Comparison** | Compares architectures across versions/branches |

## Quick Start

```bash
# Analyze current codebase
"Analyze the architecture of this project"

# Generate architecture report
"Create architecture documentation for my C++ project"

# Find issues
"Check for circular dependencies and coupling issues"
```

## Analysis Output

The skill produces several types of output:

### Visual Output
- HTML metrics reports with interactive charts
- Tree views of file structure
- Dependency matrices

### Data Output
- CSV files for further analysis
- XML architecture exports
- JSON for tool integration

### Analysis Output
- Architectural pattern identification
- Issue detection (circular deps, coupling)
- Refactoring recommendations

## Workflow

1. **Setup** - Create/validate Understand database
2. **Discover** - Map file structure and components
3. **Extract** - Export dependencies and metrics
4. **Analyze** - Identify patterns and issues
5. **Document** - Generate reports and visualizations

## Example: Complete Analysis

```
Perform a complete architecture audit:
1. Create Understand database for src/
2. Analyze dependencies between all modules
3. Identify the architectural pattern used
4. Check for circular dependencies
5. Find complexity hotspots
6. Generate HTML documentation
7. Create dependency CSV for graph tools
8. Summarize findings and recommendations
```

## Requirements

- SciTools Understand installed and in PATH
- Valid Understand license
- Source code to analyze

## Integration

This skill works with:
- **scitools-understand** - Core `und` command expertise
- Visualization tools (PlantUML, Mermaid, etc.)
- CI/CD pipelines for architecture validation

## See Also

- [SKILL.md](SKILL.md) - Detailed analysis process
- [examples.md](examples.md) - 100+ example prompts
- [scitools-understand](../scitools-understand/) - Core command reference

## Common Use Cases

### New Project Onboarding
Understand the architecture of a new codebase quickly.

### Refactoring Planning
Identify areas with tight coupling or high complexity before refactoring.

### Architecture Documentation
Generate up-to-date documentation from actual code structure.

### Microservices Extraction
Find natural boundaries for extracting microservices from a monolith.

### Technical Debt Assessment
Quantify architectural debt and prioritize improvements.

### CI/CD Gates
Validate architectural rules as part of automated pipelines.
