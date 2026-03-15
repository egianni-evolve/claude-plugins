---
name: area-tracker
description: Manage areas of interest - the topics, domains, and themes you're exploring or developing expertise in. Track how brain dumps and tasks connect to these areas.
---

# Area of Interest Tracker Skill

## When to Use This Skill
- User says: "create area", "add to area", "track this topic", "new area of interest"
- User wants to organize related items under a theme
- User is noticing patterns
- User wants to see what topics they're spending time on

## Technical Implementation

### Database Information
- Areas Data Source: Use the Areas of Interest database configured during `/setup`
- Brain Dump Data Source: Use the Brain Dump database configured during `/setup`
- Tasks Data Source: Use the Tasks database configured during `/setup`

### Required Fields
- **Interest** (title): The topic/area name
- **Status**: Current engagement level
- **Date Added**: When identified

### Status Options
- **Idea Stage**: Just noticed, might be interesting
- **Watching/Curious**: Keeping an eye on it
- **Active Exploration**: Actively learning and engaging
- **Learning**: Structured learning, courses, reading
- **Integrated**: Absorbed into regular practice
- **Archived**: No longer pursuing

### Category Options
Customize to your domains. Default suggestions: Technology, Business, Operations, Learning, Writing, Health, Personal Growth, Other

## Interaction Patterns

### Create Area
**User**: "Create area: LinkedIn Content Strategy"
**Action**: Create with Status="Idea Stage", infer categories, set Date Added
**Response**: "Created area: LinkedIn Content Strategy"

### Create with Details
**User**: "Create area: Behavior Design for AI Adoption. I'm exploring how Tiny Habits applies to teams."
**Action**: Create with description and appropriate categories
**Response**: "Created area: Behavior Design for AI Adoption (Active Exploration)"

### Link to Area
**User**: "Add my brain dump about CRAFT to my AI Operations area"
**Action**: Search for area and brain dump, create link
**Response**: "Linked CRAFT brain dump to AI Operations area."

### Review Active
**User**: "Show me my active areas"
**Action**: Search Status = "Active Exploration" or "Learning"
**Response**:
```
Your active areas:
1. AI Governance (Active) - 3 brain dumps, 1 task
2. Behavior Design (Learning) - 5 brain dumps, 3 tasks
3. CRAFT Cycle (Active) - 8 brain dumps, 4 tasks
```

### Pattern Detection
**User**: "What topics am I thinking about most?"
**Action**: Count brain dumps by area, show top areas
**Response**: "Your top areas: CRAFT Methodology (8 items), AI Governance (5 items), LinkedIn Content (4 items)"

### Update Status
**User**: "Move my AI Governance area to Learning - I'm taking a course"
**Action**: Update Status
**Response**: "Updated AI Governance -> Learning"

## Smart Suggestions

**When to suggest creating area:**
- User has 3+ brain dumps on same topic
- Pattern emerges across captures

**When to suggest linking:**
- Brain dump/task clearly relates to existing area
- User mentions area name in content

**When to suggest status updates:**
- Area "Idea Stage" for 30+ days with activity -> suggest "Active Exploration"
- Area has 5+ completed tasks -> suggest "Integrated"
- No activity in 60+ days -> suggest "Archived"

## Response Style
- "Created area: [name]"
- "Linked to [area name]."
- NOT "I've successfully created a new area of interest..."

## Area Lifecycle

Idea Stage -> Watching/Curious -> Active Exploration -> Learning -> Integrated -> Archived

**Remember**: Areas are containers for ongoing curiosity and expertise. Flexible, not rigid. Easy to create, easy to archive, easy to resurrect.
