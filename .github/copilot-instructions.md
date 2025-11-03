# Rasa Codespaces Quickstart - AI Coding Agent Instructions

## Project Overview
This is a minimal Rasa Pro quickstart repository designed for GitHub Codespaces, providing a pre-configured development environment for conversational AI projects. The repository focuses on getting users up and running quickly with Rasa Pro in a containerized environment.

## Environment Setup Critical Path
1. **License Configuration**: Always check `.env` file first - the `RASA_LICENSE` environment variable is required for Rasa Pro functionality
2. **Virtual Environment**: The devcontainer auto-creates `.venv/` via `uv venv` - always activate with `source .venv/bin/activate`
3. **Environment Loading**: Run `source .env` to load license key before any Rasa commands
4. **Package Installation**: Uses `uv` package manager, not standard pip - Rasa Pro installed from private index at `https://europe-west3-python.pkg.dev/rasa-releases/rasa-pro-python/simple`

## Key Development Workflow
```bash
# Standard initialization sequence
source .env                    # Load license
source .venv/bin/activate     # Activate Python environment
rasa init --template tutorial # Initialize project
rasa train                    # Train model
rasa inspect                  # Launch web interface
```

## Container Architecture
- **Base Image**: `mcr.microsoft.com/devcontainers/python:1-3.10-bullseye`
- **Package Manager**: `uv` for fast dependency resolution
- **Python Version**: 3.10 (locked for Rasa compatibility)
- **Port Forwarding**: Automatic via Codespaces for `rasa inspect` web interface
- **Root User**: Container runs as root for simplified permissions

## Project-Specific Patterns
- **No Source Code**: This is a quickstart template - actual Rasa projects are created via `rasa init`
- **Ephemeral Nature**: Designed for temporary exploration, not persistent development
- **License-Dependent**: All Rasa commands fail without valid `RASA_LICENSE` in environment
- **Tutorial Focus**: Default template is the Rasa tutorial bot for learning

## Critical Files
- `.env`: License key storage (must be manually populated)
- `.devcontainer/devcontainer.json`: Complete environment definition
- `README.md`: Step-by-step user instructions (authoritative workflow)

## Custom Actions Setup (Rasa 3.10+)
When working with generated Rasa projects, verify `endpoints.yml` contains:
```yaml
action_endpoint:
  actions_module: "actions"
```

## VSCode Integration
- **Recommended Extension**: Google Cloud Code for Rasa Pro integration
- **Python Interpreter**: Auto-configured to `.venv/bin/python`
- **Terminal Activation**: Python environment auto-activates in new terminals

## Troubleshooting Common Issues
- **License Errors**: Verify `RASA_LICENSE` is set and environment is sourced
- **Package Not Found**: Ensure using `uv pip install` with Rasa Pro index URL
- **Port Access**: Use notification popups in Codespaces for `rasa inspect` access
- **Environment Issues**: Recreate with `uv venv && source .venv/bin/activate`