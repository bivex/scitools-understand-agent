# SciTools Understand Expert Skill

This skill makes Claude Code an expert in using the SciTools Understand command-line interface (`und`), a powerful code analysis and comprehension tool.

## What is SciTools Understand?

SciTools Understand is a commercial code analysis tool that provides:
- Static code analysis across multiple languages
- Dependency visualization and analysis
- Code metrics and complexity measurements
- Architecture exploration
- Code standards checking (MISRA, CERT, etc.)
- Interactive reports and dashboards

## Installation

This skill is installed as a project skill at `.claude/skills/scitools-understand/`.

To use it system-wide, copy to your personal skills folder:
```bash
mkdir -p ~/.claude/skills/scitools-understand
cp .claude/skills/scitools-understand/SKILL.md ~/.claude/skills/scitools-understand/
```

## Requirements

- SciTools Understand must be installed and available in your PATH
- A valid Understand license

## Quick Start

### Create a New Project
```bash
# Ask Claude to set up a new Understand project
"Create an Understand database for my C++ project in src/"
```

### Analyze Code
```bash
# Run analysis and generate metrics
"Analyze my code and generate an HTML metrics report"
```

### Check Code Quality
```bash
# Run MISRA C 2012 checks
"Run MISRA C 2012 codecheck on my project"
```

### Dependency Analysis
```bash
# Export dependencies
"Export file dependencies to CSV"
```

## Supported Commands

| Command | Description |
|---------|-------------|
| `create` | Create a new Understand database |
| `add` | Add files/directories to project |
| `analyze` | Analyze source files |
| `report` | Generate interactive reports |
| `metrics` | Calculate and export metrics |
| `settings` | Modify project settings |
| `list` | View project information |
| `export` | Export data (settings, dependencies, etc.) |
| `import` | Import settings/architectures |
| `codecheck` | Run code standards inspections |
| `remove` | Remove items from project |
| `purge` | Remove parsed data |
| `process` | Run batch commands |
| `projectinfo` | Show project information |

## Supported Languages

- C/C++
- C#
- Java
- Python
- Fortran
- Ada
- COBOL
- JOVIAL
- Pascal
- VHDL
- Verilog
- Web (HTML, CSS, JavaScript, TypeScript, PHP)

## Examples

See [examples.md](examples.md) for detailed usage examples and prompts.

## Resources

- [SciTools Understand Documentation](https://scitools.com/documentation/)
- [Claude Code Skills Documentation](https://code.claude.com/docs)
