# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is an [Upptime](https://upptime.js.org) status page repository for Elfsquad services. Upptime is a GitHub-powered uptime monitor that uses GitHub Actions for monitoring, GitHub Issues for incident reports, and GitHub Pages for the status page.

## Architecture

**Configuration-driven**: The entire system is configured through `.upptimerc.yml`. All GitHub workflow files in `.github/workflows/` are auto-generated from this config and should NOT be edited directly - they get overwritten on template updates (weekly by default).

**Automated workflows**:
- `uptime.yml` - Checks endpoint status every 5 minutes
- `graphs.yml` - Generates response time graphs daily
- `summary.yml` - Updates README with status summary daily
- `site.yml` - Builds and deploys the status page to GitHub Pages daily
- `response-time.yml` - Records response time data
- `update-template.yml` - Syncs workflow files from Upptime template

**Auto-generated directories** (do not manually edit):
- `api/` - JSON files with uptime/response-time data per site
- `history/` - YAML files tracking historical status per site
- `graphs/` - PNG response time graphs

## Configuration

All customization happens in `.upptimerc.yml`:
- `sites` array defines monitored endpoints
- `status-website` configures the public status page (theme, branding, navbar)
- Custom CSS is embedded for Elfsquad branding

Currently monitored sites:
- Elfsquad homepage (https://www.elfsquad.io/)
- EMS (https://ems.elfsquad.io/)

## Adding/Modifying Monitored Sites

Edit the `sites` array in `.upptimerc.yml`:
```yaml
sites:
  - name: Service Name
    url: https://example.com/
```

After pushing changes, the workflows will automatically create the corresponding `api/`, `history/`, and `graphs/` entries.

## Documentation

Full Upptime documentation: https://upptime.js.org/docs/configuration
