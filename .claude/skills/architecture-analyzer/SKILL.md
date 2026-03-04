---
name: architecture-analyzer
description: Analyze software architecture and dependencies using SciTools Understand. Detect circular dependencies, tight coupling, architectural violations, and layer issues directly via und reports and queries.
argument-hint: [target] [analysis-type]
allowed-tools: Bash(und *), Read, Grep, Glob, Write
---

# Software Architecture and Dependency Analyzer

You are an expert in software architecture analysis using SciTools Understand (`und`). Analyze dependencies and architecture directly through und commands - export only when specifically requested.

## Core Analysis Workflow

### Step 1: Database Setup (if needed)

```bash
# Check for existing database
ls -la *.und 2>/dev/null

# Create new database
und create -db arch_analysis.und -local -languages $LANGUAGES
und add $SOURCE_DIR arch_analysis.und
und analyze arch_analysis.und
```

### Step 2: Analyze Dependencies Directly

```bash
# View file structure with dependencies
und list -tree files $DATABASE

# Show dependencies for specific file
und list -file path/to/file.c settings $DATABASE

# Get metrics for complexity analysis
und metrics -summary $DATABASE

# Architecture metrics
und metrics -arch "Directory Structure" $DATABASE
```

## Dependency Analysis via Reports

### Find High Fan-Out (Complex Dependencies)

Use dependency reports grouped by source:

```bash
# Show files with most outgoing dependencies
und export -dependencies -group from file csv fan_out.csv $DATABASE
head -20 fan_out.csv  # Show top 20

# Or use HTML report
und metrics -html $DATABASE
# Check archname_metrics/ for dependency visualization
```

**What to look for:**
- Files with >20 outgoing dependencies need refactoring
- Compare with complexity metrics (Cyclomatic)

### Find High Fan-In (Widely Used Files)

```bash
# Show files most depended upon
und export -dependencies -group to file csv fan_in.csv $DATABASE
head -20 fan_in.csv

# These are stable/core components - should have low complexity
```

**Interpretation:**
- High fan-in + high complexity = brittle core (refactor priority)
- High fan-in + low complexity = good abstraction

### Detect Circular Dependencies

```bash
# Export dependency data for cycle detection
und export -dependencies file csv deps.csv $DATABASE

# Check for bidirectional dependencies
und export -dependencies -col refs,froments,toents file csv bidirectional.csv $DATABASE

# Look for same file pair in both directions
awk -F',' '{print $1","$2}' bidirectional.csv | sort | uniq -d
```

**Or use architecture reports:**
```bash
# Generate dependency report
und report "Dependency Browser" $DATABASE
# Use interactive browser to trace cycles
```

### Check Layer Violations

```bash
# Export with short format to see directory-level dependencies
und export -dependencies -format short file csv layers.csv $DATABASE

# Check for violations (example: ui -> data)
grep "ui/.*data/" layers.csv

# Group by source directory
und export -dependencies -group from -format short file csv by_dir.csv $DATABASE
```

**Common violations to check:**
- `ui/` → `data/` (should go through service layer)
- `util/` → `domain/` (utilities shouldn't depend on domain)
- `infrastructure/` → `ui/` (infra shouldn't depend on presentation)

### Architecture-Level Analysis

```bash
# List all architectures
und list arches $DATABASE

# Get metrics for specific architecture
und metrics -arch "Directory Structure" $DATABASE

# Export architecture dependencies
und export -dependencies arch "Directory Structure" csv arch_deps.csv $DATABASE
```

## Direct Analysis Commands

### Analyze Specific File Dependencies

```bash
# Show what a file depends on
und export -dependencies file csv specific.csv $DATABASE | grep "From File.*my_file.c"

# Show what depends on a file
und export -dependencies file csv specific.csv $DATABASE | grep "To File.*my_file.c"
```

### Compile-Time vs Link-Time

```bash
# Compile-time (include dependencies)
und export -dependencies -mode compile file csv compile.csv $DATABASE

# Link-time (default)
und export -dependencies file csv link.csv $DATABASE

# Compare to find differences
diff compile.csv link.csv
```

### Class/Entity Level Analysis

```bash
# Class dependency matrix
und export -dependencies class matrix classes.csv $DATABASE

# Entity-level dependencies for specific file
und export -dependencies -col froments,toents file csv entities.csv $DATABASE | grep "my_file"
```

## Focused Reports

### Complexity + Dependency Hotspots

```bash
# Get complexity metrics
und metrics -summary $DATABASE > complexity.txt

# Get dependency counts
und export -dependencies -group from file csv fanout.txt $DATABASE

# Cross-reference to find problems:
# High complexity + high fan-out = refactoring candidate
```

### Architecture Health Summary

```bash
# Generate comprehensive HTML report
und metrics -html $DATABASE

# Check key indicators:
# - Circular dependencies (should be 0)
# - Max fan-out (should be <20)
# - Architecture instability metrics
```

### Dependency Rules Validation

```bash
# Export all dependencies for rule checking
und export -dependencies file csv all_deps.csv $DATABASE

# Check specific rules:
# No dependencies from ui to data
grep "^ui.*/,.*data/" all_deps.csv

# No dependencies from tests to production (reverse)
grep "^test.*/,.*src/" all_deps.csv
```

## Architecture Comparison

### Compare Two Architectures

```bash
# Metrics comparison
und metrics -arch "Architecture A" metrics_a.csv $DATABASE
und metrics -arch "Architecture B" metrics_b.csv $DATABASE

# Dependency comparison
und export -dependencies arch "Architecture A" csv deps_a.csv $DATABASE
und export -dependencies arch "Architecture B" csv deps_b.csv $DATABASE
```

### Compare Database Versions

```bash
# Create comparison database
und create -db new.und -refdb old.und -gitcommit $COMMIT -languages $LANG
und add src/ new.und
und analyze new.und

# Export changed dependencies
und export -changes -columns "Long Name,Kind Long Name,CountLineNew,CountLineChanged" changed.csv new.und
```

## Interactive Analysis

### Use Understand's Interactive Reports

```bash
# Launch interactive mode
und $DATABASE

# Interactive commands:
> list -tree files        # File tree
> list -all settings      # Show all settings
> metrics                 # Show metrics
> help report             # Available reports
```

### Generate Visual Reports

```bash
# Project Browser (interactive HTML)
und report "Project Browser" project_browser.html $DATABASE

# Dependency Browser
und report "Dependency Browser" deps.html $DATABASE

# Entity report by file
und report "Entity By File" entities.html $DATABASE
```

## Common Analysis Tasks

### Task 1: Quick Architecture Health Check

```bash
# 1. Check structure
und list -tree files $DATABASE | head -50

# 2. Get metrics summary
und metrics -summary $DATABASE

# 3. Check for obvious issues
und export -dependencies -group from file csv check.csv $DATABASE
head -5 check.csv  # Show highest fan-out

# 4. Generate HTML report
und metrics -html $DATABASE
```

### Task 2: Find Refactoring Candidates

```bash
# High complexity files
und metrics -summary $DATABASE | grep "Cyclomatic"

# High dependency files
und export -dependencies -group from file csv candidates.csv $DATABASE

# Cross-reference: look for files appearing in both
```

### Task 3: Validate Layer Architecture

```bash
# Export short-format dependencies
und export -dependencies -format short file csv validate.csv $DATABASE

# Check layer rules
grep "^ui.*/,.*data/" validate.csv      # ui -> data (BAD)
grep "^service.*/,.*ui/" validate.csv   # service -> ui (BAD)
```

### Task 4: Detect Circular Dependencies

```bash
# Export all file dependencies
und export -dependencies file csv cycles.csv $DATABASE

# Find bidirectional (same pair reversed)
awk -F',' '{print $1","$2}' cycles.csv | sort | uniq -c | sort -rn | head -20
```

### Task 5: Module Boundary Analysis

```bash
# See dependencies grouped by target
und export -dependencies -group to file csv boundaries.csv $DATABASE

# High counts = heavily used modules (good candidates for extraction)
```

## Metrics Interpretation

### Dependency Health Indicators

| Indicator | Good | Warning | Critical |
|-----------|------|---------|----------|
| Max fan-out | <10 | 10-20 | >20 |
| Bidirectional deps | 0 | <5 | >5 |
| Layer violations | 0 | <10 | >10 |
| Cycles | 0 | 0 | >0 |

### Complexity + Dependency Matrix

| Low Complexity | High Complexity |
|----------------|-----------------|
| **Low Fan-Out** | **Good** | **OK** - Simplify |
| **High Fan-In** | **Good abstraction** | **Danger** - Refactor |
| **Low Fan-In** | **Leaf node** | **Isolated complexity** |

### Architecture Patterns

**Good indicators:**
- Acyclic dependency graph
- Clear layer separation
- Unidirectional dependencies
- Low coupling between layers

**Bad indicators:**
- Circular dependencies
- Bidirectional layer links
- God objects (high fan-in + fan-out)
- Skyhook dependencies (skip layers)

## Report Output Options

### CSV Export (when needed)

```bash
# Minimal - for quick checks
und export -dependencies -col refs -format short file csv minimal.csv $DATABASE

# Full - for detailed analysis
und export -dependencies -col all file csv full.csv $DATABASE

# Grouped - for summaries
und export -dependencies -group to file csv summary.csv $DATABASE
```

### HTML Reports

```bash
# Metrics with visualization
und metrics -html $DATABASE

# Interactive browsers
und report "Project Browser" browser.html $DATABASE
und report "Dependency Browser" deps.html $DATABASE
```

### Text/Console Output

```bash
# Summary to stdout
und metrics -summary $DATABASE

# Tree view
und list -tree files $DATABASE

# Settings
und list -all settings $DATABASE
```

## Quick Reference

```bash
# Structure
und list -tree files $DATABASE

# Dependencies (minimal output)
und export -dependencies -col refs -format short file csv quick.csv $DATABASE

# High fan-out
und export -dependencies -group from file csv fanout.csv $DATABASE

# High fan-in
und export -dependencies -group to file csv fanin.csv $DATABASE

# Metrics
und metrics -summary $DATABASE
und metrics -html $DATABASE

# Architecture
und metrics -arch "Directory Structure" $DATABASE
und list arches $DATABASE

# HTML Reports
und report "Project Browser" index.html $DATABASE
```

## Best Practices

1. **Use HTML reports** for visual analysis - better than raw CSV
2. **Start with metrics summary** before deep diving
3. **Group exports** (-group from/to) to reduce output size
4. **Filter with grep** instead of exporting everything
5. **Use architectures** to analyze subsystems independently
6. **Interactive mode** (`und $DATABASE`) for exploration

## Additional Resources

- For a quick introduction, see [README.md](README.md)
- For detailed example prompts, see [examples.md](examples.md)
- For und command reference, use the [scitools-understand skill](../scitools-understand/)
