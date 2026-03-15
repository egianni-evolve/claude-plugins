---
description: Connect your Notion databases to the productivity system
argument-hint:
---

Walk the user through connecting their Notion databases to this plugin.

## Setup Process

1. **Check Notion connection**: Verify the user has connected their Notion workspace to Claude.

2. **Find or create databases**: For each of the 6 required databases, search the user's Notion workspace and ask them to confirm which database to use:

   - **Brain Dump** - thought capture inbox (needs: Note title, Source select, Status select, Priority select, Tags multi-select, Date Captured date)
   - **Tasks** - actionable items (needs: Task Name title, Status select, Priority select, Created Date date, Due Date date, Tags multi-select, Description text)
   - **Areas of Interest** - topics and themes (needs: Interest title, Status select, Category multi-select, Date Added date)
   - **Objectives** - quarterly goals (needs: Objective title, Intent text, Quarter select, Status select)
   - **Key Results** - measurable outcomes (needs: Key Result title, Target text, Unit select, Current Progress number, Status select)
   - **Progress Log** - monthly narratives (needs: Current Progress title, Month select, Year select, Progress Notes text)

3. **Verify relations**: Ensure the following Notion relations exist between databases:
   - Brain Dump <-> Tasks (two-way)
   - Brain Dump <-> Areas of Interest (two-way)
   - Tasks <-> Areas of Interest (two-way)
   - Tasks <-> Key Results (two-way)
   - Objectives <-> Key Results (two-way)
   - Key Results <-> Progress Log (two-way)

4. **Confirm setup**: List all connected databases and their status. Suggest the user try a quick brain dump capture to test.

If any database is missing fields, guide the user through adding them in Notion.
