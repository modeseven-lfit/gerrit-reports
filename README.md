<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# 🛠️ Project Reporting Artifacts

This repository stores generated reports and data artifacts from the
[Project Reporting Tool][tool-repo]. Reports are produced automatically by a
daily GitHub Actions workflow running in the tool repository, then copied here
for long-term storage and historical archival.

> **Note**: Reports are generated automatically every day at 7:00 AM UTC.
> Published reports are available at the [GitHub Pages site][pages-site].

## Repository Structure

All report artifacts are stored in the `data/artifacts/` directory, organized
by date:

```text
data/artifacts/
└── YYYY-MM-DD/
    ├── README.md                     # Summary of that day's run
    ├── reports-<slug>/               # Generated reports
    │   ├── report.html               # Interactive HTML report
    │   ├── report.md                 # Markdown report
    │   ├── report_raw.json           # Complete raw data
    │   ├── config_resolved.json      # Applied configuration
    │   ├── metadata.json             # Generation metadata
    │   ├── theme.css                 # Report styling
    │   └── <PROJECT>_report_bundle.zip
    ├── raw-data-<slug>/              # Raw JSON data files
    │   ├── report_raw.json
    │   ├── config_resolved.json
    │   └── metadata.json
    └── clone-manifest-<slug>/        # Repository clone manifests
        └── clone-manifest.json
```

This structure preserves a complete history of daily report runs for all
configured Linux Foundation projects.

## Viewing Reports

For the latest published reports, visit the [GitHub Pages site][pages-site]
hosted by the project-reporting-tool repository.

To browse historical data stored here:

1. **GitHub web interface** — Navigate the `data/artifacts/YYYY-MM-DD/`
   directories to find reports from a specific date
2. **Clone locally** — Clone this repository and open HTML files in a browser

## Report Contents

Each report includes comprehensive analytics such as:

- Repository statistics and metrics
- Commit activity and contributor information
- INFO.yaml project metadata and committer tracking
- Jenkins job allocation and CI/CD workflow status
- Feature detection (documentation, security tools, dependency management)
- Historical trends and analysis

## How Reports Are Generated

The [Project Reporting Tool][tool-repo] runs a production workflow daily:

1. The workflow clones all repositories from each configured Gerrit server
2. For each project, it analyzes repositories and generates reports in multiple
   formats (JSON, Markdown, HTML)
3. Reports are uploaded as workflow artifacts
4. A final job copies all artifacts to this repository, organized by date

For details on report generation, see the [tool documentation][tool-docs].

## Contributing

This repository is automatically maintained. Manual changes will be overwritten
by subsequent workflow runs.

To make changes:

- **Add a new project** — Update the `PROJECTS_JSON` secret in the
  [tool repository][tool-repo]
- **Modify report generation** — Update the Python code or templates in the
  [tool repository][tool-repo]
- **Report issues** — Open an issue in the [tool repository issues][tool-issues]

## License

All content is licensed under the Apache License 2.0 — see the [LICENSE][lic]
file for details.

<!-- Link references -->

[tool-repo]: https://github.com/modeseven-lfit/project-reporting-tool
[tool-docs]: https://github.com/modeseven-lfit/project-reporting-tool#readme
[tool-issues]: https://github.com/modeseven-lfit/project-reporting-tool/issues
[pages-site]: https://modeseven-lfit.github.io/project-reporting-tool/
[lic]: LICENSE