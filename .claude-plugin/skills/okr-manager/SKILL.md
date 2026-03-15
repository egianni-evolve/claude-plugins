---
name: okr-manager
description: Manage Objectives and Key Results for quarterly goal setting and tracking. Create objectives with measurable key results, track monthly progress, link tasks to KRs.
---

# OKR Manager Skill

## When to Use This Skill
- User says: "create OKR", "set quarterly goals", "track my key results", "log progress", "review OKRs"
- Beginning of quarter (goal setting)
- End of month (progress logging)
- End of quarter (review)
- When linking tasks to strategic goals

## Technical Implementation

### Database Information
- OKRs (Objectives) Data Source: Use the Objectives database configured during `/setup`
- Key Results Data Source: Use the Key Results database configured during `/setup`
- Monthly Progress Log Data Source: Use the Progress Log database configured during `/setup`
- Tasks Data Source: Use the Tasks database configured during `/setup`

### OKR Fields
- **Objective** (title): The qualitative goal
- **Intent**: The "why" behind the objective
- **Quarter**: Q1, Q2, Q3, Q4
- **Status**: Planning, Active, Completed, Paused, Abandoned

### Key Result Fields
- **Key Result** (title): Measurable outcome
- **Target**: Goal number (text)
- **Unit**: posts, clients, revenue, hours, certifications, projects, count, other
- **Current Progress**: Where you are now (number)
- **Status**: Not Started, On Track, At Risk, Behind, Completed

### Progress Log Fields
- **Current Progress** (title): Entry name
- **Month**: January, February, etc.
- **Year**: 2026 (select)
- **Progress Notes**: Qualitative narrative

## Interaction Patterns

### Create OKR
**User**: "Create Q1 2026 OKR: Build consulting credibility. KRs: Publish 12 LinkedIn posts, Complete 3 discovery calls"

**Action**:
1. Create Objective with Intent, Quarter="Q1", Status="Active"
2. Create 2 Key Results linked to objective

**Response**:
```
Created Q1 2026 OKR: Build consulting credibility

Key Results:
1. Publish 12 LinkedIn posts (0/12)
2. Complete 3 discovery calls (0/3)

Ready to link tasks or log progress?
```

### Update Progress
**User**: "Update LinkedIn posts KR to 7"
**Action**: Update Current Progress=7, calculate 7/12=58%, update Status="On Track"
**Response**: "Updated: LinkedIn posts -> 7/12 (58%, On Track)"

### Log Monthly Progress
**User**: "Log January progress for LinkedIn posts KR: Published 3 posts focused on AI governance."

**Action**: Create Progress Log entry with month, year, narrative, linked to KR

**Response**: "Logged January progress for LinkedIn posts KR."

### Review Quarter
**User**: "How's Q1 looking?"
**Action**: Fetch Q1 OKRs and KRs, calculate health
**Response**:
```
Q1 2026 OKRs (as of Jan 25):

Build consulting credibility (Active)
  LinkedIn posts: 7/12 (58%, On Track)
  Discovery calls: 1/3 (33%, At Risk)

Overall: 2 months in, mixed progress
```

### Link Task to KR
**User**: "Link my 'Draft LinkedIn post' task to LinkedIn posts KR"
**Action**: Create relation between task and KR
**Response**: "Linked task to LinkedIn posts KR."

## Smart Status Inference

Based on time elapsed in quarter + progress:

**Month 1 (0-33%):**
- 0-10% = Not Started
- 10-40% = On Track
- 40%+ = Ahead

**Month 2 (33-67%):**
- 0-20% = Behind
- 20-50% = At Risk
- 50-75% = On Track
- 75%+ = Ahead

**Month 3 (67-100%):**
- 0-50% = Behind
- 50-80% = At Risk
- 80-95% = On Track
- 95%+ = Completed

## Response Style
- "Created Q1 OKR with 3 key results"
- "LinkedIn posts -> 7/12 (58%, On Track)"
- NOT long explanations

## Quarterly Cadence

**Start**: Create OKRs, define KRs with targets
**During**: Update progress, log monthly narratives, link tasks
**End**: Final updates, review what worked, reflect, plan next quarter

**Remember**: OKRs are about focus, not perfection. 70% completion = success. The goal is learning and improvement quarter over quarter.
