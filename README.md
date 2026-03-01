# Notion Productivity Plugin

A complete productivity system that connects Claude to your Notion workspace. Capture thoughts, create tasks, organize by theme, set quarterly goals, and review weekly — all through natural language and slash commands.

## How It Works

```
Thought → Brain Dump → Weekly Processing → Task or Area → Link to OKR
```

Capture ideas as they come. Process them weekly. Route them to tasks or areas of interest. Link tasks to quarterly objectives. Every piece connects to a bigger picture.

## Quick Start

1. Install this plugin in Claude
2. Connect your Notion workspace when prompted
3. Run `/setup` to connect your databases
4. Start capturing with `/brain-dump` or process what you have with `/weekly-process`

## Commands

| Command | What It Does | Example |
|---------|-------------|---------|
| `/setup` | Connect your Notion databases to the system | `/setup` |
| `/brain-dump` | Quick-capture a thought | `/brain-dump Follow up with mentor about CRAFT` |
| `/create-task` | Create an actionable task | `/create-task Update LinkedIn. Due Friday. High priority.` |
| `/weekly-process` | Review and route unprocessed brain dumps | `/weekly-process` |
| `/okr` | Check or manage quarterly goals | `/okr` or `/okr update LinkedIn posts to 7` |
| `/interest-area` | Create or review areas of interest | `/interest-area Behavior Design` or `/interest-area list` |

## Skills

The plugin includes 5 skills that Claude triggers automatically based on what you say:

| Skill | Triggered By | Purpose |
|-------|-------------|---------|
| **brain-dump-capture** | "capture this", "brain dump", "remember this" | Frictionless thought capture |
| **task-creator** | "create task", "make this a task" | Convert ideas to actionable tasks with linking |
| **area-tracker** | "create area", "show my areas" | Organize knowledge by theme |
| **okr-manager** | "create OKR", "how's Q1 looking?" | Quarterly goal setting and tracking |
| **weekly-processing** | "process my brain dumps", "weekly review" | Systematic review of captured thoughts |

## How the Skills Connect

The power isn't in any single skill — it's in the relationships between them.

**brain-dump-capture** feeds into **weekly-processing**, which routes items to either **task-creator** (actionable) or **area-tracker** (thematic). Tasks can link to Key Results managed by **okr-manager**, connecting daily work to quarterly strategy.

## Smart Tagging

All skills auto-tag content using a consistent 10-domain vocabulary:

Career · Business · AI & Learning · Finances · Health · Home & Family · Education · Community · Travel & Shopping · Other

## Notion Setup

The plugin requires 6 databases in your Notion workspace. Running `/setup` will walk you through finding or creating them:

1. **Brain Dump** — thought capture inbox
2. **Tasks** — actionable items
3. **Areas of Interest** — topics and themes you're exploring
4. **Objectives** — quarterly goals
5. **Key Results** — measurable outcomes linked to objectives
6. **Progress Log** — monthly narrative updates on key results

These databases connect through Notion relations so data flows automatically between them.

## Customization

Fork and adapt to fit your workflow:

- **Change tag domains** — edit the Smart Tag Inference section in brain-dump-capture, task-creator, and area-tracker
- **Add status options** — extend the status selects in any database
- **Adjust trigger phrases** — modify the "When to Use" section in each skill
- **Add fields** — extend database schemas and update the corresponding skill

## License

MIT License — use freely, modify as needed.
