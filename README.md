# Task 1.2 and 1.3: Multi-Agent Coordination

This Python script demonstrates the configuration and usage of a coordinator agent for orchestrating parallel research tasks using subagents.

## Overview

The script defines:
- A coordinator agent configuration for efficient task decomposition and delegation.
- Example tool calls for spawning subagents to research environmental, economic, and policy aspects of offshore wind energy in the EU.

## Features

- **Coordinator Agent**: Uses a cost-efficient model (claude-haiku-4-5) for orchestration.
- **Parallel Execution**: Demonstrates how to run multiple subagents simultaneously in a single response.
- **Task Tool**: Enables spawning of specialized subagents with specific prompts and allowed tools.

## Usage

Run the script with Python:

```bash
python "task_1.2 and 1.3.py"
```

Note: This is a demonstration script and may require integration with an actual agent framework to execute the tool calls.

## Files

- `task_1.2 and 1.3.py`: Main script with agent configurations.
- `api_check.py`: (If present) API verification script.
- `task Statement 1.1.py`: (If present) Related task script.

## Requirements

- Python 3.x
- No external dependencies for this demonstration script.