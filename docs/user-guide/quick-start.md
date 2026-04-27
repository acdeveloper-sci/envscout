# Quick Start

!!! warning "Work in progress"
    This page will be completed when the CLI is stable (Phase 2).

## Basic usage

```bash
# Scan current directory
envscout scan

# Scan a specific path
envscout scan /home/user/projects

# Parallel mode — faster on large directory trees
envscout scan /home/user/projects --parallel

# Save results to file
envscout scan /home/user/projects --save envs.txt
```