# OKR Scoring Multi-Agent System

A LangGraph-based multi-agent system for scoring OKRs (Objectives and Key Results) and providing status updates with blocker identification.

## 🎯 Overview

This system uses four specialized AI agents working together to:
- **Score and update status** of Key Results based on updates
- **Identify and reframe blockers/challenges** 
- **Produce comprehensive reports** with reframed status and blockers

## 🏗️ System Architecture

The system consists of 4 main agents:

1. **ACHIEVEMENT_SCORING_AGENT**: Updates status and scores each KR based on updates
2. **BLOCKER_IDENTIFICATION_AGENT**: Identifies blockers and challenges for each KR
3. **STATUS_REPORTER**: Creates output status and OKR score files
4. **SUPERVISOR**: Coordinates workflow between agents

## 📁 Project Structure

```
charlie/
├── data/                          # Input data files
│   ├── joe.okr.txt               # Joe's OKR data
│   ├── joe.status.txt            # Joe's current status
│   ├── joe.update.txt            # Joe's recent updates
│   ├── nancy.okr.txt             # Nancy's OKR data
│   ├── nancy.status.txt          # Nancy's current status
│   ├── nancy.update.txt          # Nancy's recent updates
│   ├── walter.okr.txt            # Walter's OKR data
│   ├── walter.status.txt         # Walter's current status
│   └── walter.update.txt         # Walter's recent updates
├── output/                        # Generated output files
│   └── YYMMDD-HHMMSS/            # Timestamped execution folders
├── references/                    # Reference materials
│   ├── research_paper_social_media_system.ipynb
│   ├── ResearchPaperSocialMediaRequirements.md
│   └── Wellence_-_Executive_Metrics_Initial_Thoughts.pdf
├── okr_scoring_system.ipynb      # Main implementation notebook
├── PROMPTS.md                    # Documentation of all prompts used
├── NOTEBOOK_CELL_TAGS.md         # Cell reference tags
├── MERGE.md                      # Merge instructions
├── ProjectCharlieRequirements.md # Original requirements
└── README.md                     # This file
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- OpenAI API key
- LangSmith API key (optional, for monitoring)

### Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd charlie
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   
   Or install manually:
   ```bash
   pip install langchain langchain-openai langchain-community langgraph langsmith python-dotenv
   ```

3. **Set up environment variables**:
   
   **Option A: Using .env file (Recommended)**:
   ```bash
   # Copy the template file
   cp env.template .env
   
   # Edit .env file with your actual API keys
   nano .env
   ```
   
   **Option B: Using environment variables**:
   ```bash
   export OPENAI_API_KEY="your-openai-api-key"
   export LANGCHAIN_API_KEY="your-langsmith-api-key"  # Optional
   export LANGCHAIN_TRACING_V2="true"  # Optional
   ```

### Usage

1. **Open the notebook**:
   ```bash
   jupyter notebook okr_scoring_system.ipynb
   ```

2. **Run the cells** in order to:
   - Set up the environment
   - Initialize the multi-agent system
   - Process OKR scoring

3. **Example usage**:
   ```python
   # Process OKR scoring for Joe
   result = process_okr_scoring("joe")
   ```

## 📊 Input Data Format

### OKR Files (`<name>.okr.txt`)
```
Objective: Improve system reliability for core API.
KR1(20%): Reduce p95 latency from 500ms → 250ms.
KR2(40%): Achieve 99.95% uptime SLA.
KR3(40%): Resolve 90% of high-priority bugs within 7 days.
```

### Status Files (`<name>.status.txt`)
```
KR1: Latency down to 310ms, improvements from caching rollout.
KR2: SLA at 99.92% YTD; still short due to May incident.
KR3: Bug backlog reduced, 87% resolved within SLA.
```

### Update Files (`<name>.update.txt`)
```
Wins: Successful rollout of caching reduced load by 25%.
Challenges: Need clarity on incident escalation ownership between SRE and Eng.
Next Steps: Draft shared incident response playbook and propose in next leads sync.
```

## 📈 Output Files

The system generates two types of output files in timestamped subdirectories within the `output/` directory:

### File Organization
- Each execution creates a new timestamped folder: `output/YYMMDD-HHMMSS/`
- Format: `YYMMDD-HHMMSS` (e.g., `250102-143000` for January 2, 2025 at 2:30:00 PM)
- This prevents file overwrites and organizes outputs by execution time

### Status Files (`<name>.status.txt`)
- Updated KR status with completion percentages
- Identified blockers and reframed perspectives
- Next steps and recommendations

### OKR Score Files (`<name>.okrscore.txt`)
- Overall objective score
- Individual KR scores and weights
- Scoring methodology and rationale

### Agent Prompts File (`PROMPTS.txt`)
- Complete prompts used by all agents in the session
- Includes agent roles, responsibilities, and instructions
- Lists available tools and their descriptions
- Generated timestamp and session information

## 🔧 Technical Details

### Key Features
- **Multi-Agent Coordination**: LangGraph workflow with supervisor routing
- **OKR Processing**: Automated analysis of OKR data, status, and updates
- **Scoring Algorithm**: Calculation of KR completion percentages and objective scores
- **Blocker Analysis**: Systematic identification and reframing of challenges
- **Report Generation**: Professional output files with updated status and scoring
- **LangSmith Integration**: Full tracing and monitoring capabilities

### Model Configuration
- **Language Model**: GPT-4o (upgraded from GPT-4o-mini for better nuanced reasoning)
- **Temperature**: 0 (deterministic outputs)
- **Framework**: LangChain + LangGraph

## 📝 Documentation

- **[PROMPTS.md](PROMPTS.md)**: Complete documentation of all prompts used
- **[NOTEBOOK_CELL_TAGS.md](NOTEBOOK_CELL_TAGS.md)**: Cell reference tags for easy navigation
- **[MERGE.md](MERGE.md)**: Instructions for merging changes
- **[ProjectCharlieRequirements.md](ProjectCharlieRequirements.md)**: Original requirements

## 🐛 Troubleshooting

### Common Issues

1. **"Could not parse function call" error**:
   - This has been fixed by replacing JsonOutputFunctionsParser with a simple routing function
   - See PROMPTS.md for details

2. **Files not saved to output directory**:
   - The write_file tool has been updated to automatically save to the output/ directory
   - Ensure proper file naming convention is used

3. **Missing API keys**:
   - Set OPENAI_API_KEY environment variable
   - Optionally set LANGCHAIN_API_KEY for monitoring

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Follow the merge instructions in [MERGE.md](MERGE.md)

## 📄 License

This project is part of the Project Charlie initiative for OKR management and scoring.

## 🔗 References

- [LangChain Documentation](https://python.langchain.com/)
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [LangSmith Monitoring](https://smith.langchain.com/)

---

**Note**: This system is designed for OKR management and scoring. Ensure you have appropriate API keys and follow your organization's data handling policies.
