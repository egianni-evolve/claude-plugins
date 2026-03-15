---
name: brain-dump-capture
description: Quick capture tool for dumping thoughts, ideas, notes, and random musings directly into your Notion Brain Dump database. Minimal friction, maximum speed.
---

# Brain Dump Capture Skill

## When to Use This Skill
- User says things like: "capture this", "brain dump", "remember this", "add to brain dump", "quick note"
- User shares a thought without explicit instruction
- User wants to save something for later processing

## Core Behavior

When the user wants to capture something to their brain dump:

1. **Extract the content** - Get the actual thought/note from what they said
2. **Infer the source** - Determine where this is coming from based on context
3. **Create the entry** - Add to Notion with minimal required fields
4. **Confirm briefly** - Let them know it's captured, don't interrupt their flow

## Technical Implementation

### Database Information
- Data Source: Use the Brain Dump database configured during `/setup`

### Required Fields
- **Note** (title): The actual content being captured
- **Source** (select): Where this came from

### Optional Fields (set smart defaults)
- **Status**: Always "Unprocessed" for new captures
- **Priority**: Default to "Medium" unless user indicates urgency
- **Tags**: Infer from content if obvious, otherwise leave blank
- **Date Captured**: Auto-set by Notion

### Source Options
- Voice Note, Brain Dump (default), Email, ChatGPT, Claude, Gemini, Meeting Notes, Random Thought, Other

## Interaction Patterns

### Pattern 1: Explicit Capture
**User**: "Capture this: I need to follow up with mentor about methodology application"

**Action**: Create entry with Note, Source="Brain Dump", Status="Unprocessed", infer tags

**Response**: "Captured: Follow up with mentor about methodology application."

### Pattern 2: Quick Fire Multiple
**User**: "Brain dump: 1) Update LinkedIn, 2) Schedule coffee chat, 3) Review Q1 metrics"

**Action**: Create 3 separate entries

**Response**: "Captured 3 items to brain dump."

## Smart Tag Inference
- **Work**: company, projects, employer mentions
- **AI & Learning**: AI, automation, courses, certifications
- **Business**: consulting, clients, networking, partnerships
- **Personal**: family, home, personal goals
- **Health**: exercise, walking, wellness
- **Finances**: budget, investments, expenses
- **Community**: volunteering, events, groups
- **Other**: fallback

## Priority Inference
- **High**: "urgent", "ASAP", "important", "critical"
- **Low**: "someday", "maybe", "when I have time"
- **Medium**: Default

## Response Style
Keep confirmations SHORT:
- "Captured."
- "Added to brain dump."
- NOT "I've successfully added your thought to the Brain Dump database..."

## Error Handling
If Notion fails: "Couldn't save to Notion right now - want me to try again or save it here for you to copy?"

**Remember**: Speed and frictionless capture. Process later, capture now.
