# Requirements for a LangGraph Based Multi-Agent System to score and provide status updates of OKRs and identify/reframe blockers/challenges

## Overall Requirement

See [this document](references/Executive_Metrics_Initial_Thoughts.pdf) for high level objectives in particular the section titled "How will this work" . As you can see from Figure 3 in the document, we want to create a multi-agent system to 

* score as well as to provide status updates aligned to the Key Results (KR) 
* identify and reframe the blockers 
* Produce a report with reframed (a) status (b) blockers

You are to build a Python notebook to fulfill this requirement. 

### Input data

You will find the test data in the `data` folder. There are 3 file types (all raw text files):

1. `<name>.okr.txt` - these are where the KRs will be listed and their corresponding percentage contribution to the objective
2. `<name>.status.txt` - these are where the old status per KR are. These are to be reviewed with the updates per KR to derive the new status for the KR. 
3. `<name>.update.txt` - these are the updates per KR

### Output format

The output will be an updated `status` file ie. `<name>.status.txt` in the `output` folder. On top of that there is to be a `<name>.okrscore.txt` file with the scoring of that Objective based on the KRs that were achieved ie. if Objective has 2 KRs, KR1(30%) and KR2(70%) then if KR1 has achieved 15% completion and KR2 has achieved 40% completion then Objective score is (15 + 40) = 55%

## Overall System Design

The system will have the following LangGraph agents (see Figure 3 of [this document](references/Wellence_-_Executive_Metrics_Initial_Thoughts.pdf):

1. An `ACHIEVEMENT_SCORING_AGENT` that will take in the okr, status and update files of a given `<name>` and do 2 things:

   * use the update to generate an update the status of each KR
   * use the new status to score each KR
   
2. A `BLOCKER_IDENTIFICATION_AGENT` that will take in the okr, status and update files of a given `<name>` and identify the blocker of each KR

3. A `STATUS_REPORTER` that will take the output of the `ACHIEVEMENT_SCORING_AGENT` and `BLOCKER_IDENTIFICATION_AGENT` and create the output `status` file and `okrscore` file  

4. A `SUPERVISOR` agent to coordinate the work between the other 3 agents

Use this Python [notebook](references/research_paper_social_media_system.ipynb) as reference for the LangGraph LCEL multi-agent system. Note: we do not need a websearch tool but we will need 1 tool to read the input files and another to write the output files. 

## Other considerations

Please include the necessary configurations to troubleshoot this system via LangSmith 





