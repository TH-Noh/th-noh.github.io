---
layout: page
title: Meeting Agent Ops
description: AI-Powered Meeting Workflow Automation System
img: assets/img/meetingops_main.png
importance: 1
category: competition
related_publications: False
---

<div><h3><b>Overview</b></h3></div>

Meeting Agent Ops is an `AI-powered meeting workflow` system designed to help teams turn meeting conversations into structured memory, actionable tasks, and review-safe follow-up actions. The project addresses a common problem in team collaboration: meeting notes are often inconsistent, action items are not clearly tracked, and important context from previous meetings is difficult to retrieve when teams meet again.

The system **automatically captures or ingests meeting content, summarizes discussions, extracts key tasks, classifies follow-up actions, and supports automated execution for approved actions** such as sending emails or creating calendar events. It also provides project- and team-based meeting memory through RAG, allowing users to retrieve prior meeting context and prepare for future meetings more effectively.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Demo Video</b></h3></div>

This demo showcases the end-to-end workflow of Meeting Agent Ops, from meeting content ingestion and AI summarization to task classification, review-safe automation, and project-based meeting memory retrieval.

[Watch the Demo Video](https://drive.google.com/file/d/18KDSH9yvAZGBkQFCS7Hn1HglxW_uY0Cy/view?usp=sharing)

<hr style="border: 1px solid #ccc;">

<div><h3><b>Problem</b></h3></div>

Teams often leave meetings with important decisions, follow-ups, and open questions, but this context can quickly become scattered across personal notes, chat messages, and incomplete task lists. As a result, team members may forget what was discussed, lose track of responsibilities, or spend the beginning of the next meeting reconstructing previous decisions.

The core problems addressed in this project include:

- Meeting notes are taken inconsistently across team members.
- Action items are not always clearly assigned or tracked.
- Follow-up tasks such as sending emails or scheduling meetings require additional manual work.
- Past meeting context is difficult to search and reuse.
- Teams often struggle to convert meeting discussions into reliable execution.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Proposed Solution</b></h3></div>

Meeting Agent Ops transforms meeting notes, transcripts, and summaries into structured project memory and executable follow-up workflows. When a meeting starts, the agent can process meeting audio, recognize speech, and generate a summary of the discussion. After the meeting content is captured, the system analyzes the meeting summary, notes, and transcript to extract key tasks and classify them into categories such as `email follow-up`, `calendar event creation`, or `manual review required`.

Before any external action is executed, the system keeps the user in control by generating a reviewable task list. Users can inspect the suggested action, confirm or reject it, and then allow the system to automatically execute approved tasks. This review-safe workflow helps teams benefit from automation while maintaining traceability and human oversight.

Key capabilities include:

- **Automatically summarize meeting discussions** from audio, notes, or transcripts.
- Extract structured **action items** from meeting content.
- **Classify tasks** into email sending, calendar creation, or manual review.
- **Generate reviewable task** lists before executing external actions.
- Send emails or create Google Calendar events after user confirmation.
- Store meetings under teams and projects for organized collaboration.
- **Retrieve prior meeting** context using RAG.
- Provide previous meeting summaries before a new meeting starts.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/meetingops_history.png" title="Meeting History" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/meetingops_calendarview.png" title="Calendar View" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>AI Meeting Agent Workflow</b></h3></div>

The system was designed as a multi-step AI workflow that supports the entire meeting lifecycle, from live capture to follow-through. Users can create a meeting through live capture or file upload. Once submitted, the app processes the content, organizes it under the selected team and project, retrieves relevant prior context, extracts actionable tasks, and routes the tasks into a review flow before any external action is taken.

The workflow consists of the following stages:

- `Meeting Capture:` The agent starts when the meeting begins and processes meeting audio or uploaded transcript files.
- `Speech and Transcript Processing:` Audio is converted and prepared for downstream analysis, including speaker diarization and transcript generation.
- `Meeting Summarization:` The system generates a concise summary of the meeting discussion.
- `Task Extraction:` Key action items are extracted from the meeting summary, meeting notes, and transcript.
- `Task Labeling:` Each task is classified into the appropriate next-step category, such as email, calendar, or manual review.
- `Human Review:` Users review the suggested tasks and approve or reject each action.
- `Automated Execution:` Approved email and calendar tasks are executed automatically.
- `Project Memory Update:` Meeting content and vector chunks are stored for future retrieval.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/meetingops_workflow.png" title="Meeting Agent Ops Workflow" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>RAG-Based Meeting Memory</b></h3></div>

One of the main features of Meeting Agent Ops is its `project- and team-based meeting memory.` Since team members often meet repeatedly for the same project, the system stores meeting summaries, notes, transcripts, and vectorized chunks so that prior context can be retrieved later.

Before a new meeting starts, the system can **retrieve relevant summaries** from previous meetings and provide users with a pre-meeting briefing. This helps teams avoid repeating discussions, remember unresolved action items, and maintain continuity across multiple meetings.

The RAG component supports:

- Searching previous meetings within the same team or project.
- Retrieving relevant prior discussions and decisions.
- Providing previous meeting summaries at the start of a new meeting.
- Maintaining a centralized memory of project progress.
- Reducing context loss across recurring meetings.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/meetingops_brows_RAG.png" title="RAG Memory" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>System Implementation</b></h3></div>

Meeting Agent Ops was implemented as an end-to-end web application with frontend, backend, database, authentication, AI workflow, and third-party API integrations. The project integrated Google sign-in, EmailJS, Google Calendar, Supabase, and OpenAI to support authentication, task execution, storage, and AI-based meeting analysis.

The system includes:

- `Frontend Interface:` Provides meeting creation, workspace navigation, review queues, and task confirmation UI.
- `Backend Workflow:` Handles meeting processing, AI orchestration, task extraction, task labeling, and execution logic.
- `Google Authentication:` Enables users to log in securely using Google sign-in.
- `Database Layer:` Manages users, teams, projects, meetings, transcripts, summaries, vector chunks, and user credentials.
- `RAG Pipeline:` Stores and retrieves meeting content by project/team context.
- `Email Automation:` Generates and sends email follow-ups after user approval.
- `Calendar Automation:` Creates calendar events based on approved meeting tasks.
- `Review System:` Allows users to inspect, edit, approve, or reject suggested actions before execution.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Human-in-the-Loop Task Execution</b></h3></div>

A key design principle of Meeting Agent Ops is that automation should remain review-safe. Instead of directly sending emails or creating calendar events without user approval, the system creates a list of suggested follow-up actions. Each task can be reviewed by the user before execution.

For example, if the meeting transcript indicates that someone should send a follow-up email, the system labels the item as an email task and prepares it for review. If the transcript includes a future meeting or deadline, the system can suggest a calendar event. If the task is ambiguous, sensitive, or incomplete, it can be routed to manual review.

This approach helps balance automation with user control by ensuring that external actions are only executed after confirmation.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/meetingops_humanreview1.png" title="Task List" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/meetingops_humanreview2.png" title="Human Approval" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>Key Contributions</b></h3></div>

- Developed an **AI-powered meeting workflow system** that converts meeting content into structured summaries, tasks, and follow-up actions.
- Implemented meeting **audio processing** for speech recognition, speaker diarization, transcript preparation, and JSON output generation.
- Built AI workflows for **summarization, action-item extraction, task classification, and retrieval support**.
- Designed a **_human-in-the-loop_** review process before executing email or calendar actions.
- Implemented **RAG-based meeting memory** for project- and team-level context retrieval.
- Built Google login functionality for user **authentication**.
- Implemented **database structures** for teams, projects, meetings, transcripts, summaries, vector chunks, user credentials, and task workflows.
- Integrated Google Calendar and email automation for approved follow-up actions.
- Developed a workspace interface for managing meeting history, reviewing tasks, and retrieving previous meeting context.
