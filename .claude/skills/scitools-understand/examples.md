# Example Prompts for SciTools Understand Skill

This file contains example prompts you can use with the SciTools Understand skill.

## Getting Started

### Check if Understand is installed
```
Check if SciTools Understand is installed and show me the version.
```

### Explore an existing database
```
Show me information about myProject.und - what files are included and what settings are configured?
```

## Project Setup

### Create a new project
```
Create a new Understand database for my C++ project in the src/ directory.
Save it as myproject.und with local data storage.
```

### Create project with specific languages
```
Create an Understand database for my mixed C# and Java project.
The code is in src/ and lib/.
```

### Create project from git commit
```
Create an Understand database for commit abc1234f in my git repository.
Use the existing main.und as a reference database for comparison.
```

### Add CMake project
```
Add my compile_commands.json file to my Understand database.
```

### Add Visual Studio project
```
Import my Visual Studio solution using the Debug|x64 configuration.
```

## Code Analysis

### Analyze all files
```
Analyze all files in my Understand database and show me any errors.
```

### Analyze only changed files
```
Run analysis on only the files that have changed since the last analysis.
```

### Analyze specific files
```
Analyze only these files: src/main.cpp src/utils.cpp
```

## Metrics

### Generate project metrics
```
Generate an HTML metrics report for my entire project.
```

### Generate architecture metrics
```
Calculate metrics for the "Backend Services" architecture and save to CSV.
```

### Show metrics summary
```
Show me a summary of the key metrics for my project as text.
```

### Compare metrics
```
Generate metrics comparing my current code against the baseline database.
```

## Reports

### Generate dependency report
```
Create a PDF report showing all file dependencies in my project.
```

### Generate entity report
```
Generate an API Info report for the MyClass::processData function.
```

### Generate architecture report
```
Create a report showing the structure of my "Client-Server" architecture.
```

### Generate code check report
```
Generate a compliance report from my last codecheck inspection.
```

## Code Quality Checks

### Run MISRA C check
```
Run MISRA C 2012 codecheck on my entire C++ project.
Save results to the inspection_results folder.
```

### Run CERT C check
```
Run the CERT C coding standard check and generate a PDF report.
```

### Check only changed files
```
Run codecheck only on files that changed since my last inspection.
```

### Check git changes
```
Run codecheck on all uncommitted changes in my git repository.
```

### Check specific architecture
```
Run MISRA checks only on files in the "Safety Critical" architecture.
```

### Compare inspections
```
Compare my latest codecheck results against yesterday's inspection.
Show me new violations and fixed violations.
```

## Dependency Analysis

### Export file dependencies
```
Export all file dependencies to a CSV file called dependencies.csv
```

### Export class dependencies
```
Export class dependencies as a matrix showing which classes depend on each other.
```

### Export compile-time dependencies
```
Export compile-time dependencies instead of link-time dependencies.
```

### Filtered dependency export
```
Export only the references column for file dependencies.
Sort by the "To File" column.
```

## Settings and Configuration

### View all settings
```
Show me all the settings configured in my Understand database.
```

### Enable specific reports
```
Enable the "Data Dictionary" and "File Contents" reports in my project settings.
```

### Add include paths
```
Add /opt/local/include and /usr/local/include to my C++ include paths.
```

### Add preprocessor macros
```
Add the DEBUG=1 and VERSION="2.0" macros to my C++ project.
```

### Set file-specific overrides
```
For test_utils.cpp, add an extra include path for test/mock_headers
```

## Project Management

### List project contents
```
Show me a tree view of all files in my Understand database.
```

### List architectures
```
Show me all custom architectures defined in my project.
```

### Export project settings
```
Export all my project settings to an XML file for backup.
```

### Import project settings
```
Create a new database using the settings from backup.xml
```

### Remove files
```
Remove all test files from my Understand database.
```

### Purge database
```
Purge my database to reduce size for sharing (keep project definition only).
```

## Batch Operations

### Run workflow from file
```
Run all the und commands in my workflow.txt file.
```

### Create analysis script
```
Create a batch file that analyzes my code, runs metrics, and generates reports.
```

## Continuous Integration

### CI-friendly analysis
```
Run codecheck and return the number of violations as the exit code.
```

### Generate comparison reports
```
Generate reports comparing this build's metrics against the baseline.
Export to CSV for Jenkins to parse.
```

## Troubleshooting

### Check analysis errors
```
Analyze my project and show only the errors (hide warnings).
```

### Check accuracy
```
Show me the analysis accuracy metric for my project.
```

### List unmapped files
```
Show me all files that have an undefined named root.
```

## Git Integration

### Analyze specific commit
```
Create an Understand database for commit de4f5b6 and analyze it.
```

### Compare commits
```
Create databases for commits abc1234 and def5678, then export the differences.
```

### Analyze uncommitted changes
```
Run codecheck on my uncommitted git changes only.
```

## Complex Workflows

### Complete project setup
```
Set up a new Understand database for my C++ project:
1. Create database with local storage
2. Add all source files from src/
3. Add include paths from include/
4. Add DEBUG macro
5. Run full analysis
6. Generate HTML metrics report
```

### Safety-critical analysis
```
For my safety-critical C project:
1. Create database
2. Add source files
3. Run analysis
4. Run MISRA C 2012 check
5. Generate compliance report
6. Export violation counts to CSV
7. Return exit code with violation count
```

### Regression analysis
```
Compare my current code against last week's version:
1. Create reference database for last week's commit
2. Analyze current code
3. Export changed entities with complexity metrics
4. Generate comparison metrics
5. Show me functions with increased complexity
```

### Dependency cleanup
```
Help me identify unused dependencies:
1. Export file dependencies
2. Export class dependencies
3. Identify files with no incoming dependencies
4. Show me a report of potential cleanup candidates
```

## Tips for Better Prompts

1. **Be specific about the database** - Always mention the database file name or location
2. **Specify languages** - When creating new databases, list the programming languages
3. **Describe the output** - Mention what format you want (PDF, HTML, CSV)
4. **Filter appropriately** - Use architecture or file filters to narrow the scope
5. **Chain commands** - Ask for multiple steps in one prompt for efficiency

## Invoking the Skill

### Manual invocation
```
/scitools-understand create a new database for my Python project
```

### Automatic invocation
The skill will automatically activate when you ask about:
- Code analysis or code comprehension
- Generating metrics or complexity reports
- Dependency analysis
- Code quality checks or standards
- MISRA, CERT, or other coding standards
- Static analysis tools
- Understand databases (.und files)
