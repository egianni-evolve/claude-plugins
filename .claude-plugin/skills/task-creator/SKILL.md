---
name: task-creator
description: Convert brain dumps, ideas, or new thoughts into actionable tasks with proper linking to Brain Dumps, Areas of Interest, and Key Results.
---

# Task Creator Skill

## When to Use This Skill
- User says: "make this a task", "create task", "add to tasks", "turn this into a task"
- User describes something actionable
- User is processing brain dumps and decides something is a task
- User wants to link a task to an OKR or area

## Technical Implementation

### Database Information
- Tasks Data Source: Use the Tasks database configured during `/setup`
- Brain Dump Data Source: Use the Brain Dump database configured during `/setup`
- Areas Data Source: Use the Areas of Interest database configured during `/setup`
- Key Results Data Source: Use the Key Results database configured during `/setup`

### Required Fields
- **Task Name** (title): The action to be taken
- **Status**: Default to "To Do"
- **Created Date**: ALWAYS set to today's date

### Optional Fields
- **Priority**: High, Medium (default), Low
- **Due Date**: When it needs to be done
- **Description**: Additional context
- **Tags**: Infer from content
- **Related Brain Dump, Area, Key Result**: Link as appropriate

## Interaction Patterns

### Simple Task
**User**: "Create task: Update LinkedIn with certification"
**Action**: Create task with tags, Created Date
**Response**: "Created task: Update LinkedIn with certification"

### From Brain Dump
**User**: "Turn my brain dump about CRAFT library into a task"
**Action**: Search brain dump, create task, link them, update brain dump status
**Response**: "Created task and linked to your brain dump."

### With Full Details
**User**: "Create task: Draft Q1 review. Due next Friday. High priority."
**Action**: Create with all details including Created Date
**Response**: "Created high-priority task due Jan 31: Draft Q1 review"

### Link to Area/KR
**User**: "Create task to research behavior design. Related to my AI adoption area."
**Action**: Create task, link to area
**Response**: "Created task and linked to AI adoption area."

## Smart Tag Inference
Based on content: Work, AI & Learning, Business, Personal, Health, Finances, Community, Other

## Priority & Date Inference
- **High**: "urgent", "ASAP", "critical", "by Friday"
- **Low**: "someday", "when I have time"
- **Dates**: "tomorrow", "next Friday", "end of month", "in 2 weeks"

## Response Style
- "Created task: [name]"
- "Task created and linked to [brain dump/area]."
- NOT "I have successfully created a new task entry..."

## Updating Brain Dump After Task Creation
When converting brain dump to task:
1. Update Brain Dump: Status="Processed", Action Taken="Created Task"
2. Link task to brain dump (two-way relation)

**Remember**: Tasks are the "do" part. Make creation fast, linking automatic.
