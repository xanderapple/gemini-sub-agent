# Gemini Sub-Agent Standalone

A lightweight wrapper to spawn isolated Gemini sub-agents for specific tasks.

## Overview

This package allows you to programmatically (Python) or manually (CLI) invoke a Gemini agent to perform a task in an isolated workspace.

It works by:
1.  Taking a user prompt.
2.  Spinning up a `gemini` CLI instance in an isolated `workspace/` directory.
3.  Instructing that instance to read the prompt and write the result to a file.
4.  Returning the result.

## Prerequisites

1.  **Gemini CLI**: You must have the `gemini` command-line tool installed and configured in your PATH.
2.  **Bash**: 
    *   **Linux/macOS**: Standard bash.
    *   **Windows**: Git Bash (usually `C:\Program Files\Git\bin\bash.exe`).

## Installation

Clone this folder into your project.

## Usage

### Python

```python
from gemini_subagent.sub_agent import call_sub_agent

result = call_sub_agent("Summarize the README.md in the current folder.")
print(result)
```

### Command Line

```bash
# Direct string
python sub_agent.py "Write a haiku about recursion."

# From file
python sub_agent.py my_task.txt
```

## Configuration

*   **Model**: The default model is set in `bin/run_agent.sh` (currently `gemini-2.0-flash-exp`). You can change this flag.
*   **Bash Path**: On Windows, the script tries to auto-detect Git Bash. You can override this by setting the `BASH_EXE` environment variable.

## Structure

*   `sub_agent.py`: Main Python entry point.
*   `bin/run_agent.sh`: The "engine" that sets up the environment and calls Gemini.
*   `workspace/`: The sandbox where the agent operates. Files created by the agent will appear here.
