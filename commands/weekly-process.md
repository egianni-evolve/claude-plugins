---
description: Review and route your unprocessed brain dumps
argument-hint: [optional: "batch" for batch mode, or leave blank for one-by-one]
---

Start a weekly processing session using the weekly-processing skill.

Query the user's Brain Dump database for all items with Status = "Unprocessed". Count them and present an overview.

If the user specified "batch", group items by likely action (tasks vs areas vs discards) and present for bulk decisions.

Otherwise, present items one by one with quick options: Task (T), Area (A), Reference (R), Discard (D), Skip (S).

Track progress throughout. End with a summary of actions taken.
