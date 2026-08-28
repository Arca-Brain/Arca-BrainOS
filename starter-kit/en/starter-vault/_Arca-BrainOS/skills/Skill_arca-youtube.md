# 🛠️ Skill: arca-youtube

## Trigger
Execute this workflow when the user types `arca-youtube` (or `brain-youtube`) followed by a YouTube URL.

## Objective
Extract the transcript and conceptual essence of a YouTube video to generate a structured, dense, and actionable inbox note.

## Sequential Execution Workflow

1. **Transcript Extraction:**
   - Retrieve the title, author/channel, timestamps, and transcript text from the provided URL.

2. **Synthesis Note Generation:**
   - Strictly apply the template `/_Arca-BrainOS/templates/Template-Transcript-Media.md`.
   - Extract the executive summary, key takeaways with time markers `[00:00]`, notable quotes, actionable steps, and cited references.

3. **Inbox Storage:**
   - Save the generated note inside `0-Inbox/Youtube/` (e.g. `0-Inbox/Youtube/transcript-[video-title].md`).

4. **System Logging & Registry:**
   - Append the URL to `/_Arca-BrainOS/scripts/historique_youtube_log.md` to prevent duplicate processing.
   - Append single-line log to `/_Arca-BrainOS/log.md`:
     `[YYYY-MM-DD HH:mm] - AI Action (YouTube): New video processed from [URL]`

---

## 🚫 Strict Output Formatting Rules (Anti-Chatter)
1. Output ONLY the pure Markdown content.
2. **NO introduction** (do not say "Here is the summary").
3. **NO conclusion** (do not say "Processing complete").
4. Response must start exactly with `---` (YAML frontmatter) and end at the bottom of the detailed summary.
