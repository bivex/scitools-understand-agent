# Architecture Analyzer - Example Prompts

## Quick Start Prompts

### Analyze my current codebase
```
Analyze the architecture of this codebase. Show me the main components and their dependencies.
```

### Create architecture documentation
```
Generate architecture documentation for my project including dependency graphs and metrics.
```

### Find architectural issues
```
Analyze my codebase for architectural problems like circular dependencies or tight coupling.
```

## Discovery and Exploration

### Discover overall structure
```
Show me the overall structure of my project. What are the main directories and how do they relate?
```

### Identify architectural layers
```
Identify the layers in my application. Is there a clear separation between UI, business logic, and data access?
```

### Find microservices/modules
```
Analyze my codebase to identify if it follows a microservices or modular architecture. What are the boundaries?
```

### Explore components
```
What are the main components in my system? Show me how they connect to each other.
```

## Dependency Analysis

### Find circular dependencies
```
Check my codebase for circular dependencies between files or modules. Export to CSV and show me the cycles.
```

### Analyze coupling
```
Which files or classes have the most dependencies? Show me fan-in and fan-out analysis.
```

### Find god objects
```
Identify god objects - files that have both high incoming and outgoing dependencies.
```

### Tight coupling detection
```
Find files with excessive outgoing dependencies (fan-out > 20). These are candidates for refactoring.
```

### Dependency graph data
```
Export dependency data in CSV format that I can import into Excel for pivot table analysis.
```

### Compile-time vs runtime dependencies
```
Show me the compile-time dependencies in my C++ project. Export both link-time and compile-time for comparison.
```

### Find unused code
```
Identify files or classes that have no incoming dependencies (potentially unused code).
```

### Bidirectional dependencies
```
Find all bidirectional dependencies between files. These indicate tight coupling.
```

### Export class dependency matrix
```
Export the class dependency matrix so I can create a heatmap visualization.
```

### Grouped dependency analysis
```
Export dependencies grouped by target file to see which files are most depended upon.
```

### Export for Excel pivot
```
Export all dependency data with full columns for Excel pivot table analysis.
```

### Layer violation check
```
Check if any UI layer files depend on data layer files directly (should go through service layer).
```

### Architecture dependency export
```
Export dependencies for a specific architecture to analyze subsystem coupling.
```

### Dependency summary
```
Create a summary showing:
- Total number of dependencies
- Files with highest fan-out
- Files with highest fan-in
- Any circular dependencies found
```

## Complexity Analysis

### Find complex code
```
Which functions or classes are the most complex? Show me the cyclomatic complexity hotspot.
```

### Large files analysis
```
Identify the largest files in my project and their complexity metrics.
```

### Complexity by layer
```
Show me complexity metrics broken down by architectural layer.
```

## Architecture Patterns

### Check layered architecture
```
Does my project follow a layered architecture? Show me the layer structure and any violations.
```

### Check hexagonal architecture
```
Analyze if my project follows hexagonal/ports-and-adapters architecture.
```

### Check domain-driven design
```
Identify if my codebase follows domain-driven design patterns. What are the domains and bounded contexts?
```

### Check MVC/MVVM
```
Analyze my application's architecture. Is it following MVC or MVVM pattern correctly?
```

## Comparative Analysis

### Compare two versions
```
Compare the architecture of my current code with last month's version. What changed?
```

### Compare branches
```
Show me the architectural differences between the main branch and the feature branch.
```

### Baseline comparison
```
How does my current architecture differ from our baseline architecture?
```

## Documentation Generation

### Generate architecture report
```
Create a comprehensive architecture report with diagrams and metrics.
```

### Export for diagram tools
```
Export dependency data in a format I can use with visualization tools like plantuml or mermaid.
```

### Create component catalog
```
Generate a catalog of all components with their responsibilities and dependencies.
```

## Specific Technologies

### Java/Spring Boot
```
Analyze the architecture of my Spring Boot application. Show me the controllers, services, and repositories.
```

### C++ project
```
Analyze my C++ project architecture. Show me the header dependencies and potential compilation issues.
```

### Python/Django
```
Analyze my Django project structure. Show me the apps and their interdependencies.
```

### JavaScript/TypeScript
```
Analyze the architecture of my Node.js or frontend project. Show me the module structure.
```

## Refactoring Support

### Suggest architectural improvements
```
Analyze my architecture and suggest improvements for better maintainability.
```

### Identify refactoring candidates
```
Which parts of my codebase need architectural refactoring? Show me the candidates with reasons.
```

### Module extraction
```
Can you identify components that could be extracted into separate modules?
```

## Team Collaboration

### Architecture overview for new developers
```
Create an architecture overview document that would help a new developer understand the system.
```

### API boundaries documentation
```
Document the API boundaries and interfaces between major components.
```

### Onboarding guide
```
Generate an architectural guide for onboarding new team members.
```

## CI/CD Integration

### Architecture validation
```
Create a script that validates architectural rules as part of CI/CD pipeline.
```

### Dependency rules check
```
Check if my code follows the dependency rules defined in our architecture guidelines.
```

### Architecture metrics dashboard
```
Generate metrics that can be displayed on an architecture dashboard.
```

## Complete Analysis Workflows

### Full architecture audit
```
Perform a complete architecture audit of my project:
1. Create and analyze the Understand database
2. Document the overall structure
3. Identify all dependencies
4. Find circular dependencies
5. Analyze complexity hotspots
6. Identify architectural patterns
7. Generate a comprehensive report
8. List recommendations for improvements
```

### Microservices extraction analysis
```
Analyze my monolith to identify potential microservices boundaries:
1. Map all dependencies
2. Find loosely coupled components
3. Identify natural boundaries
4. Estimate extraction complexity
5. Recommend extraction order
```

### Legacy modernization assessment
```
Assess my legacy codebase for modernization:
1. Identify outdated patterns
2. Find tight coupling points
3. Assess technical debt
4. Prioritize refactoring areas
5. Create modernization roadmap
```

## Custom Analyses

### Custom layer definitions
```
Analyze my code assuming these layers: web, api, business, data, infrastructure.
Show me if dependencies flow correctly between these layers.
```

### Custom boundaries
```
Check if dependencies cross these boundaries: module-a, module-b, shared.
Report any violations.
```

### Focus on specific area
```
Analyze only the payment-processing module. Show its internal structure and dependencies.
```

## Output Formats

### Generate PlantUML diagram
```
Create a PlantUML component diagram from my dependency analysis.
```

### Generate Mermaid diagram
```
Export my architecture as a Mermaid diagram for markdown documentation.
```

### Generate JSON output
```
Export architecture data as JSON for processing by other tools.
```

### Generate spreadsheet
```
Create a spreadsheet with all architecture metrics and dependencies.
```

## Troubleshooting

### Analysis takes too long
```
Analyze only the core modules of my large project, skip test files.
```

### Too much output
```
Show me only the top 10 most critical architectural issues.
```

### Focus on specific problem
```
I'm concerned about circular dependencies. Focus analysis only on that.
```

## Tips for Best Results

1. **Specify the database**: If you have an existing `.und` file, mention it
2. **Define scope**: Be clear about what part of the system to analyze
3. **Specify output format**: Mention if you want HTML, CSV, or diagrams
4. **Set constraints**: Exclude test files, vendor directories, or generated code
5. **Define context**: Share architectural patterns or standards you're following

## Multi-Step Workflows

### Morning health check
```
Every morning, run a quick architecture health check:
1. Analyze changed files only
2. Check for new circular dependencies
3. Identify complexity increases
4. Report any architectural violations
```

### Pre-commit architecture check
```
Before committing, check if my changes follow architectural rules:
1. Check if new dependencies follow layer constraints
2. Verify no new circular dependencies introduced
3. Confirm complexity within acceptable range
```

### Release architecture validation
```
Before release, validate the architecture:
1. Full dependency analysis
2. Compare with previous release
3. Generate architecture documentation
4. Create changelog of architectural changes
```

## CSV/Excel Analysis Workflows

### Prepare dependency data for Excel
```
Export all dependencies with full column data for Excel pivot analysis:
1. Export file dependencies with all columns
2. Export class dependency matrix
3. Export grouped by source and target
4. Create summary sheet with key metrics
```

### Create Excel dashboard
```
Help me create an Excel dashboard from dependency data:
1. Export dependencies to CSV
2. Create pivot tables for fan-in/fan-out
3. Add conditional formatting for high values
4. Create charts for visualization
```

### Analyze in Excel
```
Export dependencies and tell me how to analyze them in Excel:
- What pivot tables to create
- What formulas to use
- What charts to generate
```

### Generate heatmap data
```
Export class dependency matrix formatted for creating a dependency heatmap.
```

### Trend analysis in spreadsheet
```
Create a spreadsheet that tracks dependency metrics over time.
```

### Compare architectures in Excel
```
Export two architectures to separate CSV files that I can compare in Excel.
```

### Filter dependency data
```
Export dependencies but exclude test files and vendor directories.
```

### Specific dependency export
```
Export only dependencies that match certain criteria (e.g., more than 5 references).
```
