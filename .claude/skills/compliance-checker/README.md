# Compliance Checker Skill

Enforce coding standards and generate compliance reports using SciTools Understand.

## What It Does

This skill uses Understand's CodeCheck to validate code against industry and organizational coding standards:
- **MISRA** (C 2012, C++ 2008/2023) - Automotive and safety-critical systems
- **AUTOSAR** - Automotive ECU software
- **CERT** (C/C++) - Security-focused standards
- **CWE** - Common weakness enumeration
- **Custom** - Organization-specific guidelines

## Key Features

| Feature | Description |
|---------|-------------|
| **Standard Validation** | Check code against MISRA, AUTOSAR, CERT, CWE |
| **Compliance Reporting** | Generate PDF/HTML compliance dashboards |
| **Violation Tracking** | Track, filter, and analyze violations |
| **Regression Detection** | Compare against baselines, detect new violations |
| **CI/CD Integration** | Exit status support, git integration |
| **Trend Analysis** | Track compliance over time |

## Quick Start

```bash
# Run MISRA C 2012 compliance check
"Run MISRA C 2012 checks on my project and generate a compliance report"

# Check only changed files
"Check my uncommitted changes against MISRA standards"

# Compare with baseline
"Compare my current compliance against the baseline and show new violations"
```

## Typical Workflow

```
┌─────────────────┐
│ 1. Analyze Code │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 2. Run CodeCheck│  MISRA C 2012, AUTOSAR, CERT, etc.
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 3. Generate     │  Compliance reports, violations list,
│    Reports      │  summary by rule, dashboard
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 4. Compare &    │  Check for regressions, track trends,
│    Track        │  establish baselines
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ 5. Remediate    │  Prioritize fixes, update baselines
└─────────────────┘
```

## Supported Standards

### MISRA (Motor Industry Software Reliability Association)
- **MISRA C 2012** - Most widely adopted C standard
- **MISRA C 2023** - Latest C standard
- **MISRA C++ 2008** - Classic C++ standard
- **MISRA C++ 2023** - Latest C++ standard

### AUTOSAR (Automotive Open System Architecture)
- **AUTOSAR C++14** - Automotive C++ guidelines

### CERT (Computer Emergency Response Team)
- **CERT C** - Secure C programming
- **CERT C++** - Secure C++ programming

### CWE (Common Weakness Enumeration)
- **CWE Top 25** - Most dangerous software weaknesses

### Custom
- Organization-specific coding standards
- Project-specific rules
- Industry-specific guidelines

## Use Cases

### Safety-Critical Development
Automotive, medical, aerospace systems requiring strict compliance:
```bash
# Full MISRA + AUTOSAR check with documentation
und codecheck "MISRA C 2012" ./output project.und
und codecheck "AUTOSAR C++14" ./output project.und
und report -codecheck "Compliance" ./compliance.pdf project.und
```

### Security-Focused Development
Applications requiring secure coding practices:
```bash
# CERT + CWE checks for security vulnerabilities
und codecheck "CERT C" ./output project.und
und codecheck "CWE Top 25" ./output project.und
```

### CI/CD Quality Gates
Automated compliance checking in pipelines:
```bash
# Check with exit status for CI integration
und codecheck -exitstatus "MISRA C 2012" ./output project.und
if [ $? -ne 0 ]; then
    echo "Compliance check failed"
    exit 1
fi
```

### Development Workflow
Fast feedback during development:
```bash
# Check only uncommitted changes
und codecheck -gitfiles "MISRA C 2012" ./output project.und
```

## Report Types

| Report | Description | Format |
|--------|-------------|--------|
| **Compliance** | Overall compliance status with coverage | PDF, HTML |
| **Results By File** | Violations grouped by file | CSV, HTML |
| **Summary By Rule** | Violations grouped by rule | CSV, HTML |
| **Violations Chart** | Visual representation of violations | PDF, HTML |
| **New/Fixed** | Comparison with previous inspection | CSV |

## CI/CD Integration

### Pre-commit Hook
```bash
#!/bin/bash
und codecheck -gitfiles "MISRA C 2012" ./tmp project.und
[ $? -eq 0 ] || exit 1
```

### Pre-merge Gate
```bash
#!/bin/bash
und codecheck -exitstatus "MISRA C 2012" ./output project.und
VIOLATIONS=$?
[ $VIOLATIONS -eq 0 ] || { echo "Found $VIOLATIONS violations"; exit 1; }
```

### Jenkins/GitLab
```bash
und codecheck -sarif build_$BUILD_NUMBER.sarif \
    "MISRA C 2012" ./output project.und
```

## Requirements

- SciTools Understand with CodeCheck license
- Applicable coding standard configurations
- Analyzed Understand database

## Best Practices

1. **Establish Baselines** - Create baselines for regression tracking
2. **Automate Early** - Integrate into development workflow
3. **Check Changes** - Use `-gitfiles` for fast feedback
4. **Track Trends** - Monitor compliance over time
5. **Document** - Document suppression rationale
6. **Review Regularly** - Periodic review of suppressed violations

## See Also

- [SKILL.md](SKILL.md) - Detailed command reference
- [examples.md](examples.md) - 150+ example prompts
- [scitools-understand](../scitools-understand/) - Core command reference
