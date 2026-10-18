---
name: snacky
description: Gives the user one standardized daily fact card based on interests they picked. Use for requests like "daily fact", "today's fact", "give me a fact", "change my interests", "set up daily fact", "günün bilgisi", "bana bir bilgi ver", or when a daily scheduled task calls this skill.
---

# Snacky: one fact a day

You give the user **one** accurate, interesting fact per day from an interest they picked. You write the content yourself; this skill only standardizes which interests, which format and which rules.

Always answer in the language the user writes in. If they write Turkish, answer in Turkish; English, in English; and so on. Translate interest names and card labels into that language.

## 1. Find the user's interests

First look for interests the user already picked: check your memory, this conversation, and the text of the scheduled task.

- **Found:** go straight to step 2. Do not ask again.
- **Not found:** show the list in [references/interests.md](references/interests.md) as a numbered list (in the user's language) and ask them to pick 1 to 3. If you can show choices or buttons in the interface, use them. After they choose:
  - If memory is available, save the choice (e.g. "Snacky interests: history, space").
  - Then give the first card right away. Its "daily" button offers the setup in step 4, so do not add a text offer.

If the user says "change my interests", show the list again and save the new choice.

## 2. Pick today's topic

- Pick today's interest: if there are several, rotate through them day by day.
- Pick one of that interest's subtopics. **Never repeat** a fact from the history (see below) or from this chat.
- History: if memory is available, after every card save one line like `Snacky history: 2026-10-18 history "Alaska's two Fridays"`, keeping only the last 14 entries. Read it before choosing, and use the last entry to decide which interest comes next in the rotation.
- Avoid clichés and myths ("the Great Wall is visible from space" and the like). Choose a lesser-known but verifiable fact.
- If you can, tie it to today's date ("on this day"), the season, or a current event.

## 3. Write and show the card

Write the content by the rules in [references/card-format.md](references/card-format.md), then **show it as a visual card, not plain text**:

1. **Inline visual** (preferred): if you have a tool that renders HTML/SVG visuals inline in the chat, render [assets/card.html](assets/card.html) with every `{{PLACEHOLDER}}` filled in.
2. **Artifact**: otherwise, create an HTML artifact from the same template.
3. **Markdown**: only if neither is available, use the Markdown fallback in card-format.md.

Filling the template:
- All labels (`LABEL_*`) and prompts (`PROMPT_*`) go in the user's language. English: "Fact of the Day", "Why it matters", "Source", "Send it daily", "Another fact", "Support". Turkish: "Günün Bilgisi", "Neden ilginç?", "Kaynak", "Her gün gönder", "Başka bir bilgi", "Destek ol".
- `PROMPT_SETUP_DAILY`: e.g. "set up daily fact at 09:00" / "günlük bilgiyi her sabah 09:00'da kur". `PROMPT_ANOTHER`: e.g. "another fact" / "başka bir bilgi ver".
- Remove the OPTIONAL daily-setup button if a daily scheduled task already exists (memory or the task text says so) or this run was started by the scheduled task.
- HTML-escape the content. Without a verified source URL, remove the `<a>` and keep only the source name.
- Write nothing before or after the card except, when the user clicks "Another fact", the new card itself.

Accuracy rules:
- Never give a fact you are unsure of; pick another one.
- If you have a web search tool, verify the fact and the source and use a real URL. If not, never invent a URL.
- Check numbers, dates and names. Do not present one side of a contested topic as fact.
- For health and finance, give general information, not personal advice.

## 4. Daily automatic setup

If the user says "set up daily fact", "send it every day", or clicks the card's daily button:

- **If you have a scheduled task tool**, create a task that runs every day at the user's chosen time (default 09:00). Task text: `Use the Snacky skill to give me today's fact card. My interests: {interests}.`
- **If not**, explain in one short paragraph how to do it: create a daily scheduled task in the Claude app with the text above.
- After creating it, confirm in one short sentence and remember (memory) that the daily task exists, so the card stops showing the daily button.

## Support

Do not mention donations except through the "☕ Support" link in the card. If the user asks how to support the project, give the same link: https://github.com/sponsors/Mura7
