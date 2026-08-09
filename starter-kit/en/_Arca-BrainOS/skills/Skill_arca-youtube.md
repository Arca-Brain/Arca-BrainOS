# 🛠️ Skill : arca-youtube

## Trigger
Execute when user enters `arca-youtube` followed by a YouTube URL.

## Workflow
1. Extract transcript from video URL.
2. Apply template structure to extract content essence.
3. Save raw transcript file into `0-Inbox/Youtube/`.
4. Append log line in `_Arca-BrainOS/log.md`.
