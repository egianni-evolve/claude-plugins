---
name: weekly-processing
description: Guide through systematically reviewing unprocessed brain dumps and deciding what to do with each one - create task, add to area, keep as reference, or discard.
---

# Weekly Processing Skill

## When to Use This Skill
- User says: "process my brain dumps", "weekly review", "review brain dumps", "let's process"
- Weekly/bi-weekly review sessions
- When brain dump database is getting full

## Technical Implementation

### Database Information
- Brain Dump Data Source: Use the Brain Dump database configured during `/setup`
- Tasks Data Source: Use the Tasks database configured during `/setup`
- Areas Data Source: Use the Areas of Interest database configured during `/setup`

## Processing Workflow

1. **Query for unprocessed items** (Status = "Unprocessed")
2. **For each item, ask**: "What should we do with this?"
3. **Options**:
   - Create Task -> Use Task Creator, link, mark processed
   - Add to Area -> Link to area, mark processed
   - Reference Only -> Mark processed
   - Discard -> Mark archived
   - Needs More Thought -> Keep unprocessed
   - Skip -> Leave unprocessed

## Interaction Patterns

### Start Session
**User**: "Let's process my brain dumps"
**Action**: Search Status="Unprocessed", count, present overview
**Response**: "You have 12 unprocessed brain dumps. Let's go through them. Want to go one by one, or should I group them by topic?"

### One-by-One
**Response**:
```
Item 1 of 12: "Create CRAFT library"
- Source: Brain Dump, Captured: Jan 24
What should we do? (Task/Area/Reference/Discard)
```

### Batch by Decision
**User**: "Show me all the ones that should be tasks"
**Action**: Identify actionable items (has verbs: create, follow up, schedule, review)
**Response**: "These 5 look actionable - want to create tasks for all?"

### End Summary
**Response**:
```
Processing complete!
- Created 8 tasks
- Added to 2 areas
- Kept 1 as reference
- Discarded 3 items
- Left 2 for more thought

12 of 14 processed (86%). Nice work!
```

## Smart Suggestions

**Actionable** (suggest Task): Contains action verbs, deadlines, deliverables
**Topic clusters** (suggest Area): Multiple dumps on same topic, exploratory
**Reference-only**: Informational, links, meeting notes
**Discard candidates**: Duplicates, completed, no longer relevant

## Response Style

Be efficient and rhythmic:

Good flow:
```
Item 1: "Create CRAFT library" -> What to do?
[User: Task]
Task created. (1/12)
```

Keep momentum - short questions, quick confirmations, progress tracking.

## Keyboard Shortcuts (Optional)
- T = Task
- A = Area
- R = Reference
- D = Discard
- S = Skip

## Mid-Session Pause
**User**: "Pause - I'll finish later"
**Response**: "Paused. Processed 8 of 12. Resume anytime with 'continue processing'."

**Remember**: Processing is about clearing the inbox and creating clarity. Keep it moving, make decisions easier not harder.
