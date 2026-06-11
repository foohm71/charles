# MERGE.md - Instructions for Merging OKR Scoring System

This document provides instructions for merging the OKR Scoring Multi-Agent System changes back to the main branch.

## Project Summary

**Feature**: OKR Scoring Multi-Agent System  
**Files Added/Modified**:
- `okr_scoring_system.ipynb` - Main implementation notebook
- `PROMPTS.md` - Documentation of all prompts used
- `MERGE.md` - This merge instruction file

## Pre-Merge Checklist

- [ ] All notebook cells have been tested and run successfully
- [ ] Output files are generated correctly in the `output/` directory
- [ ] LangSmith tracing is working properly
- [ ] All required dependencies are documented
- [ ] No sensitive information (API keys) is committed to the repository

## Merge Instructions

### Option 1: GitHub Pull Request (Recommended)

1. **Create a new branch** (if not already on one):
   ```bash
   git checkout -b feature/okr-scoring-system
   ```

2. **Add and commit all changes**:
   ```bash
   git add okr_scoring_system.ipynb
   git add PROMPTS.md
   git add MERGE.md
   git add output/  # if output files should be tracked
   git commit -m "Add OKR Scoring Multi-Agent System

   - Implement LangGraph-based multi-agent system for OKR scoring
   - Add ACHIEVEMENT_SCORING_AGENT for status updates and scoring
   - Add BLOCKER_IDENTIFICATION_AGENT for challenge analysis
   - Add STATUS_REPORTER for output file generation
   - Add SUPERVISOR for workflow coordination
   - Include LangSmith configuration for monitoring
   - Add comprehensive documentation and prompts"
   ```

3. **Push the branch to GitHub**:
   ```bash
   git push origin feature/okr-scoring-system
   ```

4. **Create a Pull Request**:
   - Go to your GitHub repository
   - Click "Compare & pull request" for the new branch
   - Add a descriptive title: "Add OKR Scoring Multi-Agent System"
   - Add a detailed description:
     ```markdown
     ## Overview
     This PR adds a comprehensive LangGraph-based multi-agent system for OKR (Objectives and Key Results) scoring and status updates.

     ## Features Added
     - **Multi-Agent Architecture**: 4 specialized agents working together
     - **OKR Processing**: Automated analysis of OKR data, status, and updates
     - **Scoring Algorithm**: Calculation of KR completion percentages and objective scores
     - **Blocker Identification**: Systematic identification and reframing of challenges
     - **Report Generation**: Professional output files with updated status and scoring
     - **LangSmith Integration**: Full tracing and monitoring capabilities

     ## Files Added
     - `okr_scoring_system.ipynb` - Main implementation notebook
     - `PROMPTS.md` - Documentation of all prompts used
     - `MERGE.md` - Merge instructions

     ## Testing
     - [ ] All notebook cells execute successfully
     - [ ] Output files are generated correctly
     - [ ] LangSmith tracing is functional
     - [ ] System processes all available data files (joe, nancy, walter)

     ## Dependencies
     - langchain
     - langchain-openai
     - langchain-community
     - langgraph
     - langsmith
     ```

5. **Review and Merge**:
   - Request reviews from team members
   - Address any feedback or requested changes
   - Merge the PR once approved

### Option 2: GitHub CLI

1. **Install GitHub CLI** (if not already installed):
   ```bash
   # macOS
   brew install gh
   
   # Ubuntu/Debian
   sudo apt install gh
   
   # Windows
   winget install GitHub.cli
   ```

2. **Authenticate with GitHub**:
   ```bash
   gh auth login
   ```

3. **Create and push branch**:
   ```bash
   git checkout -b feature/okr-scoring-system
   git add .
   git commit -m "Add OKR Scoring Multi-Agent System

   - Implement LangGraph-based multi-agent system for OKR scoring
   - Add comprehensive agent architecture with supervisor coordination
   - Include LangSmith monitoring and documentation"
   git push origin feature/okr-scoring-system
   ```

4. **Create Pull Request via CLI**:
   ```bash
   gh pr create \
     --title "Add OKR Scoring Multi-Agent System" \
     --body "## Overview
   This PR adds a comprehensive LangGraph-based multi-agent system for OKR scoring and status updates.

   ## Features
   - Multi-agent architecture with 4 specialized agents
   - OKR processing and scoring algorithms
   - Blocker identification and reframing
   - Professional report generation
   - LangSmith monitoring integration

   ## Files Added
   - okr_scoring_system.ipynb
   - PROMPTS.md
   - MERGE.md

   ## Testing Completed
   - All notebook cells execute successfully
   - Output files generated correctly
   - System processes all test data files" \
     --assignee @me \
     --reviewer team-member1,team-member2
   ```

5. **Merge the PR**:
   ```bash
   gh pr merge --squash --delete-branch
   ```

## Post-Merge Steps

1. **Verify the merge**:
   ```bash
   git checkout main
   git pull origin main
   ```

2. **Test the merged code**:
   - Open the notebook and verify all cells work
   - Run a test with the available data files
   - Confirm output files are generated correctly

3. **Update documentation** (if needed):
   - Update README.md with new system information
   - Add usage instructions for the OKR scoring system
   - Update any project documentation

4. **Clean up**:
   - Delete the feature branch locally: `git branch -d feature/okr-scoring-system`
   - Remove remote branch (if not auto-deleted): `git push origin --delete feature/okr-scoring-system`

## Rollback Instructions (if needed)

If issues are discovered after merging:

1. **Identify the problematic commit**:
   ```bash
   git log --oneline
   ```

2. **Revert the merge commit**:
   ```bash
   git revert -m 1 <merge-commit-hash>
   ```

3. **Push the revert**:
   ```bash
   git push origin main
   ```

## Contact Information

For questions about this merge or the OKR Scoring System:
- Review the `PROMPTS.md` file for implementation details
- Check the notebook documentation for usage instructions
- Refer to the original requirements in `ProjectCharlieRequirements.md`

## Notes

- The system requires API keys for OpenAI and LangSmith (set as environment variables)
- Input data should be placed in the `data/` directory
- Output files will be generated in the `output/` directory
- All prompts and implementation decisions are documented in `PROMPTS.md`
