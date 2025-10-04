<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# 🛠️ Gerrit Reports

Automated reports on Linux Foundation Gerrit servers and the projects/repositories they contain.

## Overview

This repository contains automatically generated reports for various Linux Foundation projects. Reports are published automatically by the [project-reports](https://github.com/modeseven-lfit/project-reports) repository's CI/CD workflow.

## Report Structure

Reports are organized in a hierarchical folder structure:

```
projects/
├── onap/
│   ├── report.html
│   └── .provenance.json
├── opendaylight/
│   ├── report.html
│   └── .provenance.json
└── [project-slug]/
    ├── report.html
    └── .provenance.json
```

Each project folder contains:
- **`report.html`**: The main report file with comprehensive analytics
- **`.provenance.json`**: Metadata about when and how the report was generated

## Project Report Links

### Active Projects

- [AGL](https://modeseven-lfit.github.io/gerrit-reports/projects/agl/report.html)
- [FDio](https://modeseven-lfit.github.io/gerrit-reports/projects/fdio/report.html)
- [LF Broadband](https://modeseven-lfit.github.io/gerrit-reports/projects/lf-broadband/report.html)
- [Linux Foundation](https://modeseven-lfit.github.io/gerrit-reports/projects/linux-foundation/report.html)
- [O-RAN-SC](https://modeseven-lfit.github.io/gerrit-reports/projects/o-ran-sc/report.html)
- [ONAP](https://modeseven-lfit.github.io/gerrit-reports/projects/onap/report.html)
- [Opendaylight](https://modeseven-lfit.github.io/gerrit-reports/projects/opendaylight/report.html)
- [OPNFV](https://modeseven-lfit.github.io/gerrit-reports/projects/opnfv/report.html)


> **Note**: Reports are updated automatically every Monday at 7:00 AM UTC, or can be triggered manually via workflow dispatch.

## Viewing Reports

Reports can be viewed in several ways:

1. **GitHub Pages** (recommended): Click any project link above to view the rendered HTML report
2. **Raw HTML**: Access via GitHub's raw content URLs
3. **Local Clone**: Clone this repository and open the HTML files in your browser

## Report Contents

Each report includes comprehensive analytics such as:

- Repository statistics and metrics
- Commit activity and contributor information
- Code review metrics
- Project health indicators
- Historical trends and analysis

## Automation

Reports are automatically generated and published by the [project-reports workflow](https://github.com/modeseven-lfit/project-reports/blob/main/.github/workflows/reporting.yaml).

### How It Works

1. The workflow runs on a schedule (weekly) or manual trigger
2. For each configured project, it:
   - Clones all Gerrit repositories
   - Runs comprehensive analytics
   - Generates an HTML report
   - Publishes the report to this repository
3. Reports are committed with metadata tracking the source run
4. This Pages workflow automatically updates the index and deploys to GitHub Pages

### Project Slug Naming

Project names are converted to slugs using the following rules:
- Converted to lowercase
- Non-alphanumeric characters replaced with hyphens
- Leading/trailing hyphens removed

Examples:
- `ONAP` → `onap`
- `OpenDaylight` → `opendaylight`
- `LF Broadband` → `lf-broadband`

## Contributing

This repository is automatically maintained. If you need to:

- **Add a new project**: Update the `PROJECTS_JSON` variable in the [project-reports repository](https://github.com/modeseven-lfit/project-reports)
- **Modify report generation**: Update the Python scripts in the [project-reports repository](https://github.com/modeseven-lfit/project-reports)
- **Report issues**: Open an issue in the [project-reports repository](https://github.com/modeseven-lfit/project-reports/issues)

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
