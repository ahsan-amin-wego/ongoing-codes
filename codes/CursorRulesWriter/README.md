# Cursor Rules for Jira Ticket Creation

This repository contains Cursor Rules for automating the process of analyzing input files, creating structured Jira tickets, and generating formatted output documents.

## Directory Structure

- `input/` - Place your input files here (requirements, specifications, etc.)
- `tickets/` - Generated ticket files in markdown format
- `output/` - Formatted output documents (RFCs, specifications, etc.)
- `.cursor/rules/` - Cursor Rules that guide the workflow

## Available Rules

1. **Input to Jira Workflow** (`.cursor/rules/input-to-jira-workflow.mdc`)
   - Orchestrates the overall process from reading input files to creating Jira tickets
   - Defines the sequence of actions and provides user guidance

2. **Input File Processing** (`.cursor/rules/input-file-processing.mdc`)
   - Standards for processing different types of input files
   - Extraction guidelines for various file formats (Markdown, JSON, CSV, etc.)

3. **Jira Ticket Creation** (`.cursor/rules/jira-ticket-creation.mdc`)
   - Standards for creating structured Jira tickets
   - Defines ticket file format, required sections, and formatting guidelines

4. **Output File Formatting** (`.cursor/rules/output-file-formatting.mdc`)
   - Standards for formatting output documents
   - Guidelines for creating RFCs, technical specifications, and other documents

## Workflow

1. **Add Input Files**
   - Place your input files (requirements, specifications, etc.) in the `input/` directory

2. **Analyze Input Files**
   - Ask Claude to analyze the input files: "Can you analyze the files in the input folder?"
   - Claude will summarize the available files and potential ticket topics

3. **Extract Information**
   - Request deeper analysis of specific files: "Please extract information from input/filename.md for potential tickets"
   - Claude will extract structured information suitable for ticket creation

4. **Suggest Potential Tickets**
   - Ask for ticket suggestions: "What tickets do you suggest we create based on the input files?"
   - Claude will suggest potential Jira tickets based on the analysis

5. **Create Ticket Files**
   - Confirm ticket creation: "Create a ticket file for [topic] based on [input file]"
   - Claude will generate structured ticket files in the tickets/ directory

6. **Review and Revise Tickets**
   - Review the generated ticket files before submission
   - Request revisions as needed: "Review and revise the ticket file for [topic]"

7. **Submit to Jira**
   - When ready, request submission: "Submit the [ticket_name] to Jira under project [PROJECT] and epic [EPIC]"
   - Claude will use MCP Atlassian integration to create the tickets in Jira

8. **Create Refined Output**
   - When needed, request formatted output documents: "Create a formatted RFC based on input/requirements.md in the output folder"
   - Claude will generate properly formatted documents following the output guidelines

## Examples

### Analyzing Input Files

```
User: "Can you analyze the files in the input folder?"

Claude: "I've analyzed the input files and found:
- input/requirements.md: Contains 3 main feature requirements that could be split into separate tickets
- input/architecture.pdf: Technical architecture document with system components
- input/dependencies.csv: List of external dependencies and versions
Would you like me to extract specific information from any of these files for potential tickets?"
```

### Creating a Ticket

```
User: "Please create a ticket file for the user authentication feature described in input/requirements.md"

Claude: "I'll create a ticket file for user authentication. Here's what I'll include:
- Title: Implement user authentication system
- Description: [extracted from requirements.md]
- Acceptance Criteria: [based on requirements]
- Implementation Details: [technical information extracted]

I'll save this as tickets/user-authentication.md. Would you like to review it before I finalize?"
```

### Submitting to Jira

```
User: "Submit the user-authentication.md ticket to Jira under project AUTH and epic USER-SYSTEM"

Claude: "I'll submit the user authentication ticket to Jira with the following details:
- Project: AUTH
- Epic: USER-SYSTEM
- Title: Implement user authentication system
[Additional details from the ticket file]

Would you like me to proceed with the submission?"
```

## Note on Jira Integration

This workflow uses MCP (Model Control Protocol) Atlassian integrations to interact with Jira. You'll need proper authentication and permissions configured for the MCP server to create tickets in your Jira instance. 