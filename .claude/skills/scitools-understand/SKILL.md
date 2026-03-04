---
name: scitools-understand
description: Expert knowledge of SciTools Understand CLI (und command). Use for code analysis, database creation, metrics, reports, codecheck inspections, dependency analysis, and project management with Understand databases.
argument-hint: [command] [options]
allowed-tools: Bash(und *)
---

# SciTools Understand CLI Expert

You are an expert in using the SciTools Understand command-line interface (`und`). This tool is used for code analysis, comprehension, metrics, and quality checking.

## Basic Command Structure

Most `und` commands follow these patterns:
- `und <command> <database.und>` - Direct command with database
- `und -db <database.und> <command>` - Database specified first
- Commands can be chained: `und -db project.und analyze metrics report`

## Core Commands Reference

### 1. Create - Generate New Database

```bash
# Basic database creation
und create -db newDatabase.und -languages c++ c#

# Save analysis data locally (for sharing between machines)
und create -db myProject.und -local -languages c++ c#

# Create database for specific git commit
und create -db myProject.und -gitcommit <githash> -languages c++

# Create with reference database (copies settings, sets as comparison)
und create -db newDb.und -refdb existingDb.und -gitcommit <hash> -gitrepo /path/to/repo
```

**Important Notes:**
- `-local` saves data in project's 'local' folder instead of AppData
- Git commit databases require identical source paths when sharing
- Creating at a specific commit doesn't auto-add files (use `und add`)

### 2. Add - Add Files/Directories to Project

```bash
# Add directory (most common)
und add thisDirectory myProject.und

# Add with options
und add -watch off -exclude "*.java","*.cpp" thisDirectory myProject.und

# Add files
und add file1.cpp file2.cpp myProject.und
und add @myFiles.txt myProject.und  # File with list of files

# Add CMake compile_commands.json
und add -cmake compile_commands.json myProject.und
und add -exclude "test*" -cmake compile_commands.json myProject.und

# Add Visual Studio project
und add -config "Debug|Win32" file.vcproj myProject.und

# Add named roots
und add -root root=value root2=value2 myProject.und
und add @myRoots.txt myProject.und

# Merge another database
und add -db todb.und fromdb.und
```

**Add options for directories:**
- `-watch <on|off>` - Watch directory for changes (default: on)
- `-subdir <on|off>` - Include subdirectories (default: on)
- `-exclude "pattern1,pattern2"` - Exclude matching files/dirs (default: `.*`)
- `-filter "pattern1,pattern2"` - Include only matching files
- `-lang <lang>` - Add files for specific language only

**Add options for import files:**
- `-cmake` - File is compile_commands.json
- `-vs` - File is Visual Studio project
- `-xcode` - File is Xcode project
- `-config <config>` - Configuration to use
- `-analyzelater` - Skip automatic analysis
- `-onetime` - Disable project sync
- `-exclude` - Semicolon-separated excludes

### 3. Analyze - Analyze Project Files

```bash
# Analyze all files (default)
und analyze myProject.und

# Analyze only changed files
und analyze -changed myProject.und

# Analyze specific files
und analyze -files file1.cpp file2.cpp myProject.und
und analyze -files @fileList.txt myProject.und

# Output options (only shows specified output + summary)
und analyze -errors myProject.und
und analyze -warnings myProject.und
und analyze -accuracy myProject.und
```

**Analyze switches:**
- `-all` - Analyze all files (default)
- `-changed` - Analyze only changed files since last analyze
- `-files` - Analyze specific files
- `-errors` - Show only analysis errors
- `-warnings` - Show only analysis warnings
- `-accuracy` - Show accuracy metric

### 4. Report - Generate Interactive Reports

```bash
# Basic report generation
und report "Report Name" output.pdf myProject.und

# Multiple formats
und report -format pdf,csv,png "Report Name" outdir myProject.und

# Report for specific entity
und report -ent @lchimaera@kchimaera@f./egrep.c "API Info" out.pdf myProject.und

# Report for architecture
und report -arch "Directory Structure" "Report Name" out.pdf myProject.und

# CodeCheck report from SARIF
und report -codecheck current.sarif "Results By File Report" outdir/byfile

# Report with options
und report -options "Show Violations Chart=False" "Compliance" out.pdf myProject.und

# Multiple reports
und -db myproject.und report "Report1" out1.pdf report "Report2" out2.pdf
```

**Report formats:** pdf, html, txt, csv, png

**Report targets:**
- `-codecheck [sarif]` - Run on inspection in SARIF file
- `-ent [uniquename]` - Run on specific entity
- `-arch [longname]` - Run on specific architecture

**Report options:** Semicolon-separated key=value pairs via `-options`

### 5. Metrics - Generate Metrics

```bash
# Project metrics (uses current settings)
und metrics myProject.und

# Architecture metrics
und metrics -arch myArch myProject.und
und metrics -arch outputFile.csv myArch  # Specify output file

# HTML metrics report
und metrics -html myProject.und
und metrics -html archName1 archName2 /output/directory

# Summary to stdout
und metrics -summary myProject.und
und metrics -summary -csv myProject.und
```

### 6. Settings - Modify Project Settings

```bash
# View all settings
und list -all settings myProject.und

# Set a value (mush strategy: -CategoryNameSetting)
und settings -ReportDisplayCreationDate on myProject.und
und settings -ReportFileNameDisplayMode full myProject.und

# Add to list (without clearing)
settings -ReportReportsAdd "Data Dictionary"

# Add macros
settings -C++MacrosAdd MYLONG="Long Text"

# Custom values
settings -ReportNumberOfPages NEntity=250

# Override for specific file
und settings -override_c++Includes file.cpp include1 include2

# Override from file
und settings -override @overrideFile.txt myProject.und

# Load from text file
und settings @settingsFile.txt myProject.und
```

**Settings patterns:**
- `-CategoryName` - Setting category (e.g., `-ReportDisplayCreationDate`)
- Use `Add` suffix to append to lists instead of replacing
- Override commands: `-override_c++Includes`, `-override_file_encoding`, etc.
- Text file format: `#` for comments (except when preceded by `-c`)

### 7. List - View Project Information

```bash
# List files
und list files myProject.und
und list -tree files myProject.und

# List architectures
und list arches myProject.und

# List named roots
und list roots myProject.und
und list -unmapped -unportable roots myProject.und

# List baselines
und list baselines myProject.und

# List settings
und list settings myProject.und
und list -all settings myProject.und
und list -metrics settings myProject.und
und list -report settings myProject.und
und list -lang C++ settings myProject.und
und list -override file1.cpp settings myProject.und
und list -macros -includes settings myProject.und
```

### 8. Export - Export Data

```bash
# Export project settings to XML
und export toHere.xml myProject.und

# Export architecture
und export -arch "Directory Structure" toHere.xml myProject.und

# Export dependencies
und export -dependencies file csv output.csv myProject.und
und export -dependencies class matrix output.csv myProject.und
und export -dependencies arch myArch csv output.csv myProject.und
und export -dependencies -col refs -sort to -format short file csv output.csv myProject.und

# Export macros/includes
und export -macros myProject.und
und export -includes -lang C++ myProject.und

# Export changed entities
und export -changes -columns "Status,Long Name,PercentChanged" output.csv myProject.und
und export -changes -cmpdb comparison.und output.csv myProject.und
```

**Export dependency options:**
- `-mode <compile|link>` - Compile time vs link time dependencies
- `-col <none|refs|froments|toents|all>` - Columns to include
- `-format <short|long|longnoroot>` - Filename format
- `-sort <to|from>` - Sort by column
- `-group <to|from|none>` - Group entries

### 9. Import - Import Data

```bash
# Import project settings
und create import settings.xml newProject.und
und -db existing.und import settings.xml

# Import architecture
und import -arch myArch.xml myProject.und

# Import baseline
und import -baseline path/to/results.sarif myProject.und
```

### 10. CodeCheck - Run Inspections

```bash
# Basic codecheck
und codecheck myConfiguration /output/dir myProject.und

# Codecheck on specific files
und codecheck -files fileList.txt config outputDir myProject.und

# Codecheck on architecture
und codecheck -arch "Directory Structure/src" config outputDir myProject.und

# Codecheck on git changed files
und codecheck -gitfiles config outputDir myProject.und
und codecheck -gitfiles 1ff2406b after config outputDir myProject.und

# Codecheck with custom SARIF output
und codecheck -sarif mysarif.sarif config outputDir myProject.und

# Codecheck with specific reports
und codecheck -reports Compliance config outputDir myProject.und
und codecheck -reports all config outputDir myProject.und

# Compare with previous inspection
und codecheck -previous yesterday/results.sarif config outputDir myProject.und

# Exit status with violations
und codecheck -exitstatus config outputDir myProject.und
und codecheck -exitstatus errors config outputDir myProject.und
```

**CodeCheck options:**
- `-gitfiles [hash after]` - Only uncommitted changed files
- `-changedfiles` - Only files changed since last CodeCheck
- `-arch <name>` - Files in specific architecture
- `-files <listfile>` - Specific files (optional line ranges)
- `-sarif <filename>` - Custom SARIF output location
- `-reports <name> ...` - Specific reports to generate
- `-previous <sarif>` - Compare with previous inspection
- `-exitstatus [withexcluded|errors]` - Return violations as exit code

### 11. Remove - Remove Items from Project

```bash
# Remove files/directories
und remove someFile.cpp myProject.und
und remove C:\\SomeDirectory myProject.und

# Remove with force type
und remove -file someFile myProject.und
und remove -vs vsFile.vcproj myProject.und
und remove -root NAMED_ROOT myProject.und
und remove -arch myArch myProject.und

# Remove from list file
und remove @listfile.txt myProject.und
```

**Remove options:**
- `-file` - Force treat as file
- `-vs` - Force treat as Visual Studio file
- `-root` - Force treat as named root
- `-arch` - Force treat as architecture
- `-baseline` - Force treat as baseline
- `-analyzelater` - Skip automatic analysis

### 12. Purge - Remove Parsed Data

```bash
# Remove all parsed data (keeps project definition)
und purge myProject.und
```

Useful for backing up or sharing projects (re-run analyze to repopulate).

### 13. Process - Batch Commands

```bash
# Run commands from text file
und process commands.txt myProject.und
```

**Process file format:**
```
# Comments start with #
-db myProject.und  # Set database
add file.h
add "myFile.cpp"
# Only one command per line
```

### 14. ProjectInfo

```bash
# Show version, date, and project folder locations
und projectinfo myProject.und
```

## Common Workflows

### New Project Setup
```bash
und create -db myProject.und -local -languages c++ c#
und add src/ myProject.und
und analyze myProject.und
und metrics -html myProject.und
```

### Git Commit Analysis
```bash
und create -db commitDb.und -gitcommit abc12345 -languages c++ -gitrepo /path/to/repo
und add src/ commitDb.und
und analyze commitDb.und
und export -changes commitVsMain.csv commitDb.und
```

### Code Quality Check
```bash
und codecheck "MISRA C 2012" outputDir myProject.und
und report -codecheck "Compliance" outputDir/compliance.pdf myProject.und
```

### Dependency Analysis
```bash
und export -dependencies file csv deps.csv myProject.und
und export -dependencies class matrix classDeps.csv myProject.und
```

### Continuous Monitoring
```bash
und analyze -changed myProject.und
und codecheck -changedfiles "My Config" outputDir myProject.und
und codecheck -previous baseline/results.sarif "My Config" newOutputDir myProject.und
```

## Interactive Mode

When you run `und` without a database, you enter interactive mode:
```bash
und
> myProject.und  # Set active database
> add src/
> analyze
> metrics
> exit
```

## Supported Languages

Common language codes for `-languages`:
- `c++` or `c`
- `c#` or `csharp`
- `java`
- `python` or `py`
- `fortran` or `f90`
- `ada`
- `cobol`
- `jovial`
- `pascal`
- `vhdl`
- `verilog`
- `web` (HTML, CSS, JavaScript, TypeScript, PHP)

## Tips and Best Practices

1. **Use `-local` for shared projects** - Ensures consistent file paths across machines
2. **Reference databases** - Use `-refdb` when creating databases for different commits
3. **Named roots** - Use `-root` for portable include paths
4. **List before setting** - Always `und list -all settings` before changing settings
5. **Batch commands** - Use `und process` for repetitive workflows
6. **Export for backup** - Export settings and architectures before major changes
7. **Purge before sharing** - Use `und purge` to reduce database size when sharing

## Additional Resources

- For a quick introduction to the skill, see [README.md](README.md)
- For detailed example prompts and workflows, see [examples.md](examples.md)
