# Notebook Cell Tags Reference

This document provides tags for each cell in the `okr_scoring_system.ipynb` notebook to make it easy to reference specific cells when asking questions.

## Cell Tag Reference

### Setup and Configuration Cells

**Cell 0** - `#title-overview`
- **Type**: Markdown
- **Content**: Main title and system overview
- **Tag**: `title-overview`

**Cell 1** - `#setup-dependencies`
- **Type**: Markdown  
- **Content**: Setup and dependencies section header
- **Tag**: `setup-dependencies`

**Cell 2** - `#installation-header`
- **Type**: Markdown
- **Content**: Installation section header
- **Tag**: `installation-header`

**Cell 3** - `#install-packages`
- **Type**: Python
- **Content**: Package installation command
- **Tag**: `install-packages`

**Cell 4** - `#imports`
- **Type**: Python
- **Content**: All necessary imports and libraries
- **Tag**: `imports`

**Cell 5** - `#env-setup`
- **Type**: Python
- **Content**: Load environment variables from .env file
- **Tag**: `env-setup`

**Cell 5** - `#env-config-header`
- **Type**: Markdown
- **Content**: Environment configuration section header
- **Tag**: `env-config-header`

**Cell 6** - `#langsmith-setup`
- **Type**: Python
- **Content**: LangSmith tracing configuration
- **Tag**: `langsmith-setup`

**Cell 7** - `#openai-setup`
- **Type**: Python
- **Content**: OpenAI API key setup
- **Tag**: `openai-setup`

**Cell 8** - `#directory-setup-header`
- **Type**: Markdown
- **Content**: Working directory setup section header
- **Tag**: `directory-setup-header`

**Cell 9** - `#directory-config`
- **Type**: Python
- **Content**: Data and output directory configuration
- **Tag**: `directory-config`

### Core System Definition Cells

**Cell 10** - `#state-definition-header`
- **Type**: Markdown
- **Content**: State definition section header
- **Tag**: `state-definition-header`

**Cell 11** - `#state-class`
- **Type**: Python
- **Content**: OKRScoringState TypedDict definition
- **Tag**: `state-class`

**Cell 12** - `#tools-header`
- **Type**: Markdown
- **Content**: File management tools section header
- **Tag**: `tools-header`

**Cell 13** - `#file-tools`
- **Type**: Python
- **Content**: File management and calculation tools
- **Tag**: `file-tools`

**Cell 14** - `#helper-functions-header`
- **Type**: Markdown
- **Content**: Helper functions section header
- **Tag**: `helper-functions-header`

**Cell 15** - `#helper-functions`
- **Type**: Python
- **Content**: Agent creation and workflow helper functions
- **Tag**: `helper-functions`

**Cell 16** - `#llm-init-header`
- **Type**: Markdown
- **Content**: Language model initialization section header
- **Tag**: `llm-init-header`

**Cell 17** - `#llm-init`
- **Type**: Python
- **Content**: Language model initialization
- **Tag**: `llm-init`

### Agent Creation Cells

**Cell 18** - `#agent-creation-header`
- **Type**: Markdown
- **Content**: Agent creation section header
- **Tag**: `agent-creation-header`

**Cell 19** - `#achievement-agent-header`
- **Type**: Markdown
- **Content**: Achievement Scoring Agent section header
- **Tag**: `achievement-agent-header`

**Cell 20** - `#achievement-agent`
- **Type**: Python
- **Content**: Achievement Scoring Agent creation and configuration
- **Tag**: `achievement-agent`

**Cell 21** - `#blocker-agent-header`
- **Type**: Markdown
- **Content**: Blocker Identification Agent section header
- **Tag**: `blocker-agent-header`

**Cell 22** - `#blocker-agent`
- **Type**: Python
- **Content**: Blocker Identification Agent creation and configuration
- **Tag**: `blocker-agent`

**Cell 23** - `#reporter-agent-header`
- **Type**: Markdown
- **Content**: Status Reporter Agent section header
- **Tag**: `reporter-agent-header`

**Cell 24** - `#reporter-agent`
- **Type**: Python
- **Content**: Status Reporter Agent creation and configuration
- **Tag**: `reporter-agent`

**Cell 25** - `#supervisor-agent-header`
- **Type**: Markdown
- **Content**: Supervisor Agent section header
- **Tag**: `supervisor-agent-header`

**Cell 26** - `#supervisor-agent`
- **Type**: Python
- **Content**: Supervisor Agent creation and configuration
- **Tag**: `supervisor-agent`

### Workflow and Execution Cells

**Cell 27** - `#graph-construction-header`
- **Type**: Markdown
- **Content**: Graph construction section header
- **Tag**: `graph-construction-header`

**Cell 28** - `#graph-construction`
- **Type**: Python
- **Content**: LangGraph workflow construction and compilation
- **Tag**: `graph-construction`

**Cell 29** - `#execution-function-header`
- **Type**: Markdown
- **Content**: System execution function section header
- **Tag**: `execution-function-header`

**Cell 30** - `#execution-function`
- **Type**: Python
- **Content**: Main process_okr_scoring function
- **Tag**: `execution-function`

### Usage and Examples Cells

**Cell 31** - `#example-usage-header`
- **Type**: Markdown
- **Content**: Example usage section header
- **Tag**: `example-usage-header`

**Cell 32** - `#example-joe`
- **Type**: Python
- **Content**: Example usage with Joe's data
- **Tag**: `example-joe`

**Cell 33** - `#process-all-header`
- **Type**: Markdown
- **Content**: Process all data section header
- **Tag**: `process-all-header`

**Cell 34** - `#process-all-data`
- **Type**: Python
- **Content**: Process all available data files
- **Tag**: `process-all-data`

**Cell 35** - `#system-summary`
- **Type**: Markdown
- **Content**: System summary and capabilities
- **Tag**: `system-summary`

**Cell 36** - `#empty-cell`
- **Type**: Empty
- **Content**: Empty cell
- **Tag**: `empty-cell`

## Usage Instructions

When asking questions about the notebook, you can reference specific cells using their tags:

### Examples:
- "Can you explain the logic in the `#achievement-agent` cell?"
- "I want to modify the `#file-tools` cell to add a new tool"
- "The `#graph-construction` cell is giving me an error"
- "How does the `#execution-function` cell work?"
- "Can you show me the imports in the `#imports` cell?"

### Cell Categories:

**Setup Cells**: `#title-overview`, `#setup-dependencies`, `#installation-header`, `#install-packages`, `#imports`, `#env-config-header`, `#langsmith-setup`, `#openai-setup`, `#directory-setup-header`, `#directory-config`

**Core System**: `#state-definition-header`, `#state-class`, `#tools-header`, `#file-tools`, `#helper-functions-header`, `#helper-functions`, `#llm-init-header`, `#llm-init`

**Agents**: `#agent-creation-header`, `#achievement-agent-header`, `#achievement-agent`, `#blocker-agent-header`, `#blocker-agent`, `#reporter-agent-header`, `#reporter-agent`, `#supervisor-agent-header`, `#supervisor-agent`

**Workflow**: `#graph-construction-header`, `#graph-construction`, `#execution-function-header`, `#execution-function`

**Usage**: `#example-usage-header`, `#example-joe`, `#process-all-header`, `#process-all-data`, `#system-summary`

## Quick Reference by Functionality

- **Package Installation**: `#install-packages`
- **Imports**: `#imports`
- **Environment Setup**: `#langsmith-setup`, `#openai-setup`
- **Directory Setup**: `#directory-config`
- **State Definition**: `#state-class`
- **Tools**: `#file-tools`
- **Helper Functions**: `#helper-functions`
- **Language Model**: `#llm-init`
- **Achievement Agent**: `#achievement-agent`
- **Blocker Agent**: `#blocker-agent`
- **Reporter Agent**: `#reporter-agent`
- **Supervisor Agent**: `#supervisor-agent`
- **Graph Construction**: `#graph-construction`
- **Main Function**: `#execution-function`
- **Example Usage**: `#example-joe`
- **Process All**: `#process-all-data`
