# Compose Config Inspector — User Guide

Compose Config Inspector shows the effective configuration produced by Docker Compose after file merging, profile selection, and environment interpolation.

## Requirements

- IntelliJ IDEA 2025.3 or newer
- Docker Compose installed locally
- A project containing at least one Compose YAML file

The plugin runs entirely on your computer. It has no telemetry, account system, or backend service.

## Getting started

1. Open a project containing `compose.yaml`, `compose.yml`, or `docker-compose*.yml`.
2. Open **View | Tool Windows | Compose Inspector** or choose **Tools | Compose Effective Config**.
3. Add the Compose files you want to inspect.
4. Reorder the files so they match the precedence order used by your Docker Compose command. Later files override earlier files.
5. Select any required profiles and an environment file.
6. Click **Inspect**.
7. Browse or search the effective configuration tree.

## Understanding the result

Select a value in the effective configuration tree to see:

- its canonical JSON path and resolved value;
- the contributing Compose YAML file and approximate source location;
- earlier values that were overridden;
- changes compared with the previous inspection.

Use the available actions to open the matching YAML source or copy the value or JSON path.

## Refreshing the inspection

Run **Inspect** again after changing Compose files, profiles, environment variables, or the selected environment file. The previous successful result is retained so changed scalar values can be highlighted.

## Troubleshooting

### Docker Compose is unavailable

Run `docker compose version` in a terminal and confirm that Docker Compose is installed and available on your system path. The installed version must support `docker compose config --format json`.

### The result contains an interpolation or YAML error

Review the error displayed in the Compose Inspector, then check the selected environment file, active profiles, Compose file order, and the referenced YAML source.

### A source location is approximate

Docker Compose normalizes some structures, especially list forms such as ports. For those values, provenance and source locations may be approximate.

## Privacy

All inspection processing stays local. See the [Privacy Policy](PRIVACY.md) for details.

## Support and issue reports

Please use the [GitHub issue tracker](https://github.com/serape/compose-config-inspector-docs/issues) for bug reports and feature requests. Include your IDE version, Docker Compose version, the steps to reproduce the problem, and a sanitized error message. Do not include passwords, tokens, or private environment values.

## Legal

Use of the plugin is governed by the [End User License Agreement](EULA.md).
