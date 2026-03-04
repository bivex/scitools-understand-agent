# Compliance Checker - Example Prompts

## MISRA Compliance

### Full MISRA C 2012 Check
```
Run a complete MISRA C 2012 compliance check on my project and generate a PDF compliance report.
```

### MISRA C++ 2008 Check
```
Check my C++ code against MISRA C++ 2008 standard and show me all violations.
```

### MISRA Dashboard
```
Create a MISRA compliance dashboard showing:
- Overall compliance percentage
- Violations by rule
- Most violated files
- Severity breakdown
```

### MISRA with Suppressions
```
Run MISRA C 2012 check but exclude suppressed violations from the report.
```

### MISRA on Safety Critical Code Only
```
Run MISRA checks only on files in the "Safety Critical" architecture.
```

## AUTOSAR Compliance

### AUTOSAR C++14 Check
```
Check my code against AUTOSAR C++14 coding guidelines.
```

### AUTOSAR with Custom Rules
```
Run AUTOSAR checks with additional company-specific rules.
```

### AUTOSAR Compliance Report
```
Generate an AUTOSAR compliance report for our safety assessment documentation.
```

## CERT Standards

### CERT C Security Check
```
Run CERT C coding standard checks to identify security vulnerabilities.
```

### CERT C++ Check
```
Check my C++ code against CERT C++ secure coding standards.
```

### High Priority Security Issues
```
Show me only high and medium severity CERT violations.
```

### Security-Focused Compliance
```
Run both CERT and CWE checks to identify potential security issues.
```

## CI/CD Integration

### Pre-commit Check
```
Create a pre-commit hook that runs MISRA checks on changed files only.
```

### Merge Gate Check
```
Set up a compliance gate that blocks merge if new violations are introduced.
```

### CI Pipeline Check
```
Configure compliance checking in Jenkins with trend tracking.
```

### Exit Status Integration
```
Run CodeCheck and return the violation count as exit code for CI scripts.
```

## Git Integration

### Check Uncommitted Changes
```
Run MISRA checks on my uncommitted git changes only.
```

### Check Since Last Release
```
Check compliance for all changes since the v1.0.0 release tag.
```

### Pre-push Validation
```
Validate that my changes don't introduce new compliance violations before pushing.
```

### Branch Comparison
```
Compare compliance between my feature branch and main branch.
```

## Comparison and Regression

### Establish Baseline
```
Create a compliance baseline for my project to track future regressions.
```

### Compare Against Baseline
```
Check my current code against the established baseline and show new violations.
```

### Regression Report
```
Generate a report showing violations fixed and introduced since last check.
```

### Trend Analysis
```
Show me compliance trends over the past month.
```

### Sprint Comparison
```
Compare compliance status between sprint start and end.
```

## Filtering and Targeting

### Check Specific Files
```
Run MISRA checks only on these files: src/main.c src/driver.c
```

### Exclude Test Files
```
Run compliance checks but exclude all files in test/ directory.
```

### Check by Component
```
Run CERT checks only on the network communication module.
```

### Changed Files Only
```
Run quick compliance check on files modified since last analysis.
```

## Reporting

### Executive Summary
```
Create a one-page executive summary of compliance status for management.
```

### Detailed Technical Report
```
Generate a detailed technical report with all violations and locations.
```

### Violations by Rule
```
Show me a breakdown of violations grouped by each MISRA rule.
```

### Violations by File
```
List all files with their violation counts, sorted by severity.
```

### Compliance Dashboard
```
Generate an HTML compliance dashboard with charts and graphs.
```

### Export to Spreadsheet
```
Export all violations to CSV format for analysis in Excel.
```

## Multiple Standards

### Multi-Standard Check
```
Run checks against MISRA C, AUTOSAR, and CERT standards.
```

### Compare Standards
```
Compare the violation counts across different coding standards.
```

### Combined Report
```
Create a unified report showing compliance across all applicable standards.
```

## Custom Standards

### Run Company Standard
```
Run our internal coding standard checks defined in "Company Standard".
```

### Import and Run Custom Config
```
Import the coding_standard.xml configuration and run checks.
```

### Create Custom Check
```
Help me create a custom CodeCheck configuration for our project rules.
```

## Analysis and Insights

### Most Violated Rules
```
Which MISRA rules are most commonly violated in my codebase?
```

### Riskiest Files
```
Identify the files with the highest number of critical violations.
```

### Compliance Hotspots
```
Show me areas of the code that need the most compliance work.
```

### False Positive Analysis
```
Help me analyze potential false positives in the violation report.
```

### Suppression Review
```
Show me all suppressed violations for periodic review.
```

## Remediation

### Fix Priority Queue
```
Prioritize violations for fixing based on severity and impact.
```

### Auto-fixable Issues
```
Identify violations that could be automatically fixed.
```

### Remediation Plan
```
Create a remediation plan to achieve 100% MISRA compliance.
```

### Incremental Compliance
```
Plan incremental compliance improvements across sprints.
```

## Specific Scenarios

### Safety Critical Project
```
My project is safety-critical. Run full MISRA C 2012 and AUTOSAR checks with detailed reporting.
```

### Medical Device Software
```
Run compliance checks suitable for IEC 62304 requirements.
```

### Automotive ECU Software
```
Check compliance for automotive ECU software (MISRA + AUTOSAR).
```

### Security Assessment
```
Run CERT and CWE checks for security assessment before release.
```

### Legacy Code Migration
```
Assess compliance gap in legacy code being migrated to safety-critical system.
```

### Third-Party Code Review
```
Check compliance of vendor-supplied code before integration.
```

## Quick Checks

### Quick Smoke Test
```
Run a quick compliance smoke test to catch obvious issues.
```

### High Severity Only
```
Show me only critical and high-severity violations.
```

### Five-Minute Check
```
Run a fast compliance check on changed files only.
```

### Verify Fix
```
Re-check specific file to verify violations were fixed.
```

## Documentation

### Compliance Certificate
```
Generate a compliance certificate for our customer documentation.
```

### Evidence Package
```
Create an evidence package for safety audit including all reports.
```

### Traceability Matrix
```
Generate a traceability matrix linking requirements to checks.
```

### Configuration Export
```
Export the CodeCheck configuration for version control.
```

## Troubleshooting

### Check Failed
```
My CodeCheck failed with errors. Help me diagnose the issue.
```

### Database Not Analyzed
```
Fix "database not analyzed" error before running CodeCheck.
```

### Missing Configuration
```
Find available CodeCheck configurations in my project.
```

### Performance Issues
```
Optimize CodeCheck performance for large codebase.
```

## Complex Workflows

### Complete Compliance Assessment
```
Perform a complete compliance assessment for my safety-critical project:
1. Ensure database is fully analyzed
2. Run MISRA C 2012 checks
3. Run AUTOSAR C++14 checks
4. Generate compliance dashboard
5. Create executive summary
6. Export detailed violations to CSV
7. Compare against baseline
8. Identify new violations
9. Prioritize remediation
10. Create remediation plan
```

### Continuous Compliance Monitoring
```
Set up continuous compliance monitoring:
1. Establish baseline
2. Configure pre-commit hook for changed files
3. Configure CI gate for full checks
4. Set up trend tracking
5. Create weekly compliance reports
6. Alert on regression
```

### Release Compliance Package
```
Create a complete compliance package for release:
1. Run full compliance check
2. Generate all standard reports
3. Compare with previous release
4. Document all changes
5. Create summary for stakeholders
6. Package all artifacts for audit
```

### Third-Party Integration
```
Evaluate third-party library for compliance:
1. Create separate database for vendor code
2. Run applicable checks
3. Document all violations
4. Assess risk level
5. Create waiver request if needed
6. Generate integration guidance
```

### Multi-Project Comparison
```
Compare compliance across multiple projects:
1. Check each project
2. Normalize results
3. Create comparison report
4. Identify best practices
5. Share lessons learned
```

## Team Collaboration

### Compliance Review Meeting
```
Prepare materials for compliance review meeting:
1. Current compliance status
2. Recent changes
3. Top violations
4. Remediation progress
5. Blockers and issues
```

### Developer Guidance
```
Create developer-friendly compliance guidelines based on our actual violations.
```

### Training Identification
```
Identify training needs based on common violation patterns.
```

### Quality Metrics Dashboard
```
Create a dashboard showing compliance metrics for the team.
```

## Regulatory Support

### ISO 26262 Support
```
Generate documentation to support ISO 26262 compliance assessment.
```

### IEC 61508 Support
```
Create evidence package for IEC 61508 functional safety assessment.
```

### DO-178C Support
```
Generate compliance evidence for DO-178C avionics software certification.
```

### EN 50128 Support
```
Create compliance documentation for EN 50128 railway applications.
```
