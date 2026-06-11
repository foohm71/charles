# PROMPTS.md - OKR Scoring Multi-Agent System

This document records all prompts used to generate code in the OKR Scoring Multi-Agent System.

## Project Overview
**Project**: OKR Scoring Multi-Agent System  
**Date**: December 2024  
**Purpose**: LangGraph-based multi-agent system for scoring OKRs and providing status updates with blocker identification

## Main Prompts Used

### 1. System Architecture Prompt
**Context**: Designing the overall system architecture
**Prompt**: 
```
Build a LangGraph-based multi-agent system for OKR scoring with the following requirements:
- ACHIEVEMENT_SCORING_AGENT: Updates status and scores each KR based on updates
- BLOCKER_IDENTIFICATION_AGENT: Identifies blockers and challenges for each KR  
- STATUS_REPORTER: Creates output status and OKR score files
- SUPERVISOR: Coordinates workflow between agents
- Input: OKR, status, and update files
- Output: Updated status files and OKR score files
- Include LangSmith configuration for troubleshooting
```

### 2. Achievement Scoring Agent Prompt
**Context**: Creating the achievement scoring agent
**Prompt**:
```
You are an expert in OKR (Objectives and Key Results) achievement scoring. 
Your role is to analyze the OKR data, current status, and updates to:
1. Update the status of each Key Result based on the provided updates
2. Calculate completion percentages for each KR
3. Provide detailed scoring analysis

When analyzing updates, look for:
- Progress indicators and metrics mentioned
- Wins and achievements
- Completion percentages or progress descriptions
- Time-based progress indicators

Format your output as updated status for each KR with completion percentages.
Be precise and analytical in your scoring.
```

### 3. Blocker Identification Agent Prompt
**Context**: Creating the blocker identification agent
**Prompt**:
```
You are an expert in identifying and analyzing blockers and challenges in OKR execution. 
Your role is to:
1. Analyze the OKR data, current status, and updates
2. Identify specific blockers and challenges for each Key Result
3. Provide reframed perspectives on these challenges
4. Suggest actionable solutions or mitigation strategies

Look for:
- Explicit challenges mentioned in updates
- Resource constraints (time, people, budget)
- Technical or process obstacles
- Dependencies and coordination issues
- External factors and risks

Provide clear, actionable blocker identification for each KR with reframed perspectives.
```

### 4. Status Reporter Agent Prompt
**Context**: Creating the status reporter agent
**Prompt**:
```
You are an expert in creating comprehensive OKR status reports. 
Your role is to:
1. Synthesize the updated status from the Achievement Scoring Agent
2. Incorporate blocker analysis from the Blocker Identification Agent
3. Calculate the overall objective score based on KR completion
4. Create two output files:
   - Updated status file with reframed status and blockers
   - OKR score file with objective scoring breakdown

Format the status file to include:
- Updated KR status with completion percentages
- Identified blockers and reframed perspectives
- Next steps and recommendations

Format the OKR score file to include:
- Overall objective score
- Individual KR scores and weights
- Scoring methodology and rationale

Ensure all outputs are clear, actionable, and professional.
```

### 5. Supervisor Agent Prompt
**Context**: Creating the supervisor agent
**Prompt**:
```
You are a supervisor coordinating a team to analyze and score OKRs. 
The team consists of: ACHIEVEMENT_SCORING_AGENT (updates status and scores KRs), 
BLOCKER_IDENTIFICATION_AGENT (identifies blockers and challenges), 
and STATUS_REPORTER (creates final output files). 
Guide the workflow in this order: 
1. First, use ACHIEVEMENT_SCORING_AGENT to analyze and score the KRs 
2. Then, use BLOCKER_IDENTIFICATION_AGENT to identify blockers and challenges 
3. Finally, use STATUS_REPORTER to create the final output files 
When the final reports are ready and saved, respond with FINISH.
```

### 6. Tool Creation Prompts
**Context**: Creating file management and calculation tools
**Prompts**:
- File reading tool: "Create a tool to read text files and return contents as string"
- File writing tool: "Create a tool to write content to text files"
- OKR parsing tool: "Create a tool to parse OKR data and extract objectives and KRs with weights"
- Score calculation tool: "Create a tool to calculate objective scores based on KR completion percentages"

### 7. LangSmith Configuration Prompt
**Context**: Setting up monitoring and debugging
**Prompt**:
```
Set up LangSmith tracing for monitoring and debugging our multi-agent system.
Include:
- Environment variable configuration
- Project naming with unique identifiers
- API key setup instructions
- Full tracing of agent interactions, tool usage, and workflow execution
```

### 8. Graph Construction Prompt
**Context**: Building the LangGraph workflow
**Prompt**:
```
Build the LangGraph workflow by connecting all agents and defining the flow logic:
- Create state graph with OKRScoringState
- Add nodes for each agent
- Add edges from agents back to supervisor
- Add conditional edges from supervisor to agents
- Set supervisor as entry point
- Compile the graph
```

### 9. Execution Function Prompt
**Context**: Creating the main execution function
**Prompt**:
```
Create a function to execute the multi-agent system for OKR scoring:
- Process OKR scoring for a given person
- Construct file paths for OKR, status, and update files
- Check file existence and read data
- Create initial state with all data
- Stream workflow execution with error handling
- Check for output files and display results
- Return the compiled graph
```

### 10. Cell Tagging System Prompt
**Context**: Adding cell tags for easy reference
**Prompt**:
```
Add cell tags as comments to each code cell in the notebook so they can be easily referenced when asking questions. 
The tags should be descriptive and follow the pattern #tag-name. 
Add tags to all key cells including:
- Setup and configuration cells (#imports, #langsmith-setup, #openai-setup)
- Core system cells (#state-class, #file-tools, #helper-functions)
- Agent creation cells (#achievement-agent, #blocker-agent, #reporter-agent, #supervisor-agent)
- Workflow cells (#graph-construction, #execution-function)
- Usage example cells (#example-joe, #process-all-data)
```

### 11. OKR Data Structure Analysis Prompt
**Context**: Understanding KR format and percentage extraction
**Prompt**:
```
Analyze how the OKR data structure works:
- KRs are formatted as: KR{number}({number}%): {description}
- The percentage in parentheses represents the weight/contribution to the overall objective
- The parse_okr_data function does basic text parsing for display
- The calculate_objective_score function uses regex to extract weights: r'KR\d+\((\d+)%\)'
- Weighted scoring calculation: total_weighted_score += (weight * completion / 100)
- Final objective score is the sum of all weighted contributions
```

### 12. Model Selection Analysis Prompt
**Context**: Evaluating GPT-4o vs GPT-4o-mini for OKR scoring task
**User Question**: "Given the nuanced reasoning needed for scoring and updating OKR status, should we upgrade from gpt-4o-mini to gpt-4o?"

**Analysis Response**:
```
The OKR scoring system requires several types of nuanced reasoning:

1. Achievement Scoring Agent:
   - Analytical reasoning: Parse updates and extract progress indicators
   - Quantitative analysis: Calculate completion percentages from qualitative descriptions
   - Contextual understanding: Relate current status to updates and determine new status
   - Precision: Accurate scoring calculations

2. Blocker Identification Agent:
   - Complex reasoning: Identify implicit blockers from updates
   - Reframing: Transform challenges into actionable perspectives
   - Strategic thinking: Suggest mitigation strategies
   - Pattern recognition: Connect different types of constraints

3. Status Reporter Agent:
   - Synthesis: Combine multiple agent outputs coherently
   - Professional writing: Create clear, actionable reports
   - Scoring methodology: Explain rationale behind calculations

GPT-4o advantages for this task:
- Superior reasoning for complex analytical tasks
- More accurate interpretation of qualitative updates
- More reliable scoring calculations
- Higher quality professional report generation

Recommendation: YES, upgrade to GPT-4o for better nuanced reasoning capabilities.

**Implementation**: Updated #llm-init cell to use model="gpt-4o" instead of model="gpt-4o-mini"
```

### 13. JsonOutputFunctionsParser Error Fix
**Context**: Fixing "Could not parse function call: 'function_call'" error
**User Issue**: "Getting an error running the cell tagged #example-joe. The error is 'Could not parse function call: 'function_call'' - looks like this is the issue? @https://github.com/langchain-ai/langchain/issues/9460"

**Problem Analysis**:
```
The error is caused by JsonOutputFunctionsParser failing when GPT models return control characters in their function call responses. This is a known issue in LangChain GitHub issue #9460.

The problem was in the create_supervisor function using:
- llm.bind_tools(tools=[function_def], tool_choice="route")
- JsonOutputFunctionsParser()

This combination fails when GPT returns control characters in function calls.
```

**Solution Implemented**:
```
Replaced the complex function-calling supervisor with a simple state-based routing function:

def create_supervisor(llm: ChatOpenAI, system_prompt: str, members: List[str]) -> callable:
    def route_supervisor(state):
        messages = state["messages"]
        
        # Simple routing logic based on conversation state
        if "ACHIEVEMENT_SCORING_AGENT" not in str(messages):
            return {"next": "ACHIEVEMENT_SCORING_AGENT"}
        elif "BLOCKER_IDENTIFICATION_AGENT" not in str(messages):
            return {"next": "BLOCKER_IDENTIFICATION_AGENT"}
        elif "STATUS_REPORTER" not in str(messages):
            return {"next": "STATUS_REPORTER"}
        else:
            return {"next": "FINISH"}
    
    return route_supervisor

Also removed unused JsonOutputFunctionsParser import.
```

**Result**: Fixed the parsing error and simplified the supervisor routing logic.
```

### 14. Output Directory File Storage Fix
**Context**: Files not being saved to output directory
**User Issue**: "I see the output files generated but why are they not stored in the output folder?"

**Problem Analysis**:
```
The agents were creating files but they were being saved to the current working directory instead of the output/ directory. The write_file tool was not using the OUTPUT_DIRECTORY path, and the agents weren't using the correct file naming convention expected by the execution function.
```

**Solution Implemented**:
```
1. Updated write_file tool to automatically save files to OUTPUT_DIRECTORY:
   - Added logic to check if file_path starts with OUTPUT_DIRECTORY
   - If not, prepend OUTPUT_DIRECTORY to the file path
   - Ensures all files are saved to the correct location

2. Updated STATUS_REPORTER agent prompt to use correct file naming:
   - Specified exact naming convention: '{person_name}.status.txt' and '{person_name}.okrscore.txt'
   - Added instruction that files will be automatically saved to output directory
   - This matches what the execution function expects to find
```

**Result**: Files are now properly saved to the output/ directory with correct naming convention.
```

### 15. GitHub Repository Creation
**Context**: Creating GitHub repository for the OKR Scoring System
**User Request**: "I now want to create a github repo for this"

**Implementation**:
```
1. Initialized local git repository: git init
2. Created comprehensive README.md with:
   - Project overview and architecture
   - Installation and usage instructions
   - Input/output data format examples
   - Technical details and troubleshooting
   - Complete documentation links

3. Created .gitignore file to exclude:
   - Python cache files and virtual environments
   - API keys and sensitive files
   - IDE and OS specific files
   - Temporary files

4. Created requirements.txt with all dependencies

5. Made initial commit with comprehensive message covering:
   - All implemented features
   - Bug fixes and improvements
   - Documentation additions

6. Connected to GitHub repository: git@github.com:foohm71/charlie.git
7. Pushed code to main branch successfully
```

**Repository URL**: https://github.com/foohm71/charlie
**Result**: Complete OKR Scoring Multi-Agent System now available on GitHub with full documentation.
```

### 16. Timestamped Output Directories Implementation
**Context**: Adding timestamped folders for better file organization
**User Request**: "I created a subfolder 20251002-145800 which is a timestamp in the format YYMMDD-HHMMSS - can you (a) modify the code so that the notebook creates such a folder each time we have to save output files and then (b) update github with the changes"

**Implementation**:
```
1. Updated #directory-config cell to:
   - Import datetime module
   - Create timestamp in YYMMDD-HHMMSS format
   - Create SESSION_OUTPUT_DIR = OUTPUT_DIRECTORY / timestamp
   - Display session output directory path

2. Updated write_file tool in #file-tools cell to:
   - Use SESSION_OUTPUT_DIR instead of OUTPUT_DIRECTORY
   - Save all files to timestamped session directory
   - Updated docstring to reflect session directory usage

3. Updated #execution-function cell to:
   - Look for output files in SESSION_OUTPUT_DIR
   - Check for files in the correct timestamped directory

4. Updated STATUS_REPORTER agent prompt to:
   - Mention timestamped session directory in instructions
   - Clarify where files will be saved

5. Committed and pushed changes to GitHub with descriptive commit message
```

**Benefits**:
- Prevents file overwrites between different execution runs
- Organizes output files by execution timestamp
- Makes it easy to track when each analysis was performed
- Improves overall file organization and debugging

**Result**: Each notebook execution now creates a unique timestamped directory for output files.
```

### 17. Automatic Agent Prompts Saving
**Context**: Saving agent prompts to session directories for transparency and debugging
**User Request**: "ok can the prompts for each of the agents be saved in a PROMPTS.txt file in each of the subfolders in the output folder after each run as well?"

**Implementation**:
```
1. Added save_agent_prompts() function in #file-tools cell:
   - Creates comprehensive PROMPTS.txt file with all agent prompts
   - Includes session timestamp and generation date
   - Contains complete prompts for all 4 agents:
     * ACHIEVEMENT_SCORING_AGENT
     * BLOCKER_IDENTIFICATION_AGENT  
     * STATUS_REPORTER
     * SUPERVISOR
   - Lists all available tools and their descriptions

2. Updated #execution-function to:
   - Call save_agent_prompts() at start of each run
   - Include PROMPTS.txt in created files list
   - Display PROMPTS.txt content in output

3. Updated README.md to document:
   - PROMPTS.txt feature and contents
   - Agent roles and responsibilities
   - Tools descriptions

4. Added PROMPTS.txt to existing 20251002-145800 session directory
```

**Benefits**:
- Complete transparency of agent prompts used in each session
- Easy debugging and analysis of agent behavior
- Historical record of prompt changes over time
- Clear documentation of system capabilities

**Result**: Each execution now automatically saves complete agent prompts to PROMPTS.txt in the session directory.
```

### 18. Quality Control Agent Design Discussion
**Context**: Addressing inconsistent outputs issue with multi-agent system
**User Question**: "So validation would be a Quality Control Agent?"

**Analysis of Inconsistent Outputs Issue**:
```
Identified non-deterministic LLM behavior causing different results across sessions:
- Different KR completion percentages (80% vs 76% for same data)
- Different output formats ("KR1 (20% weight): 80% completion" vs "KR1 (20%): 76% complete")
- Inconsistent tool usage (some sessions use improved calculator, others don't)
- Varying content depth and detail levels

Root cause: LLM making different choices each time despite same prompts and code.
```

**Quality Control Agent Solution**:
```
Role & Responsibilities:
- Validate all outputs for consistency and completeness
- Correct formatting and calculation errors
- Ensure all required information is present
- Standardize output formats across sessions
- Flag any inconsistencies or missing data

Architecture: ACHIEVEMENT_SCORING_AGENT → BLOCKER_IDENTIFICATION_AGENT → STATUS_REPORTER → QUALITY_CONTROL_AGENT → FINAL_OUTPUT

Tools:
- validate_kr_completion_percentages(): Validate KR completion percentages
- validate_objective_score_calculation(): Verify and recalculate objective score
- standardize_output_format(): Ensure consistent output formatting
- check_completeness(): Check required information is present
- correct_calculation_errors(): Fix calculation or formatting errors

Quality Control Agent Prompt:
"You are a Quality Control Agent responsible for ensuring consistent, accurate, and complete outputs from the OKR scoring system. Your role is to validate all KR completion percentages, verify objective score calculations, ensure output formats match templates, check completeness, and correct any errors found."

Validation Checklist:
- [ ] All KRs have completion percentages
- [ ] Completion percentages are between 0-100%
- [ ] Objective score calculation is correct
- [ ] Output format matches template
- [ ] All required sections are present
- [ ] No missing or inconsistent data
```

**Benefits**:
- Consistency enforcement across all sessions
- Error detection and correction
- Quality assurance and professional output
- Maintainable centralized quality control logic
- Solves current issues: consistent scores, standardized formats, complete information

**Implementation Strategy**:
1. Add Quality Control Agent to existing multi-agent system
2. Create validation tools for each output type
3. Update workflow to include quality control step
4. Test with existing data to validate improvements
5. Monitor quality metrics to measure success

**Result**: Quality Control Agent provides deterministic, high-quality outputs while maintaining LLM flexibility for analysis tasks.
```

## Implementation Notes

### Key Design Decisions
1. **State Management**: Used TypedDict for type safety and clear state structure
2. **Tool Integration**: Created specialized tools for file operations and score calculations
3. **Error Handling**: Implemented comprehensive error handling throughout the workflow
4. **Output Formatting**: Designed clear, professional output formats for status and score files
5. **Monitoring**: Integrated LangSmith for full system observability

### Technical Specifications
- **Language**: Python 3.8+
- **Frameworks**: LangChain, LangGraph, OpenAI
- **Monitoring**: LangSmith integration
- **Input Format**: Text files (OKR, status, update)
- **Output Format**: Text files (status, score)

### File Structure
- `okr_scoring_system.ipynb`: Main notebook implementation
- `PROMPTS.md`: This file documenting all prompts
- `data/`: Input data directory
- `output/`: Output files directory

## Usage Instructions

1. Install required packages: `langchain`, `langchain-openai`, `langchain-community`, `langgraph`, `langsmith`
2. Set up LangSmith API key and OpenAI API key
3. Place input files in `data/` directory with format: `{name}.okr.txt`, `{name}.status.txt`, `{name}.update.txt`
4. Run the notebook cells to process OKR scoring
5. Check `output/` directory for generated status and score files

## Future Enhancements

Potential improvements to consider:
1. Add support for multiple OKR formats
2. Implement batch processing capabilities
3. Add visualization components for OKR dashboards
4. Integrate with external OKR management systems
5. Add advanced scoring algorithms and metrics
