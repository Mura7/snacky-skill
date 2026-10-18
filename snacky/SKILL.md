---
name: snacky
description: Gives the user one standardized daily fact card based on interests they picked. Use for requests like "daily fact", "today's fact", "give me a fact", "change my interests", "show new categories", "set up daily fact", "günün bilgisi", "bana bir bilgi ver", "ilgi alanlarımı değiştir", or when a daily scheduled task calls this skill.
---

# Snacky: one fact a day

You give the user **one** accurate, interesting fact per day from an interest they picked. You write the content yourself; this skill only standardizes which interests, which format and which rules.

Always answer in the language the user writes in. If they write Turkish, answer in Turkish; English, in English; and so on. Translate interest names and card labels into that language.

## 1. Find the user's interests

First look for interests the user already picked: check your memory, this conversation, and the text of the scheduled task.

- **Found:** go straight to step 2. Do not ask again.
- **Not found**, or the user says "change my interests": show the **interest picker** (below). The user may pick as many interests as they like. After they choose:
  - If memory is available, save the choice and the list version, e.g. `Snacky interests: history, space, faith` and `Snacky list version seen: 2`.
  - If memory refuses to save part of the choice (for example, Claude's memory may block religious topics like the faith interest unless the user allows sensitive topics in memory settings), save the rest, say so in one short sentence, and mention that the daily task text keeps the full list. Never rename or encode an interest to get around a memory restriction.
  - If a daily Snacky scheduled task exists, update its text with the new interests (or, if you cannot edit tasks, tell the user in one sentence).
  - Then give the first card right away. Its "daily" button offers the setup in step 4, so do not add a text offer.

### The interest picker

Never ask with a plain text list when you can render visuals. In order of preference:

1. **Inline visual**: render [assets/picker.html](assets/picker.html). Replace `{{CHIPS}}` with one button per interest in [references/interests.md](references/interests.md), in table order:
   `<button class="chip" data-code="history" data-icon="history" data-label="Tarih" aria-pressed="false">Tarih</button>`
   - Do not add emoji: the template draws a Lucide icon from `data-icon` (same as the code).
   - `data-label` and the visible name in the user's language; `data-code` is the code from the table.
   - When changing interests, set `aria-pressed="true"` on the user's current interests.
   - On interests that are new since the user's seen list version, add `<span class="new">{{LABEL_NEW}}</span>` inside the button (EN "New", TR "Yeni").
   - Labels: `LABEL_TITLE` (EN "Pick your interests", TR "İlgi alanlarını seç"), `LABEL_HINT` (EN "Pick as many as you like. You get one fact a day, rotating through them.", TR "İstediğin kadar seç. Her gün birinden bir bilgi gelir."), `LABEL_SELECT_ALL` (EN "Select all", TR "Hepsini seç"), `LABEL_CONFIRM` (EN "Start", TR "Başla"), `PROMPT_PREFIX` (EN "My Snacky interests:", TR "Snacky ilgi alanlarım:").
   - The confirm button sends e.g. `Snacky ilgi alanlarım: Tarih, Uzay [history,space]`. Treat that message as the user's choice.
2. **Artifact**: otherwise, an HTML artifact from the same template.
3. **Text**: only if neither works, a numbered list; the user may answer with any number of numbers.

Write nothing before or after the picker except one short line when it helps (e.g. which interests are pre-selected).

### New categories (list version)

`interests.md` has a **List version** and a changelog of which codes each version added.

- If memory holds `Snacky list version seen: N` and the current list version is higher (or the user has saved interests but no seen version, which means version 1), there are new categories: the codes added after version N.
- Then, on today's card, keep the OPTIONAL new-categories notice in [assets/card.html](assets/card.html): `LABEL_NEW_CATEGORIES` names the new interests (EN "New categories: Quran Verses & Hadith. Want to take a look?", TR "Yeni kategoriler geldi: Ayet ve Hadis. Bakmak ister misin?"), `LABEL_SHOW_NEW` (EN "Take a look", TR "Göz at"), `PROMPT_SHOW_NEW` (EN "show me the new Snacky categories", TR "yeni Snacky kategorilerini göster").
- Right after showing the notice, update memory to the current list version, so the notice appears only once.
- If the user clicks it, show the picker with their current interests pre-selected and the new ones marked "New".
- Without memory, skip this; never show the notice twice in one chat.

## 2. Pick today's topic

- Pick today's interest: if there are several, rotate through them day by day.
- Pick one of that interest's subtopics. **Never repeat** a fact from the history (see below) or from this chat.
- History: if memory is available, after every card save one line like `Snacky history: 2026-10-18 history "Alaska's two Fridays"`, keeping only the last 14 entries. Read it before choosing, and use the last entry to decide which interest comes next in the rotation.
- For the **faith** interest (Quran verses and hadith), follow the source rules in [references/interests.md](references/interests.md): only Diyanet sources, verbatim quote, exact reference.
- Avoid clichés and myths ("the Great Wall is visible from space" and the like). Choose a lesser-known but verifiable fact.
- If you can, tie it to today's date ("on this day"), the season, or a current event.

## 3. Write and show the card

Write the content by the rules in [references/card-format.md](references/card-format.md), then **show it as a visual card, not plain text**:

1. **Inline visual** (preferred): if you have a tool that renders HTML/SVG visuals inline in the chat, render [assets/card.html](assets/card.html) with every `{{PLACEHOLDER}}` filled in.
2. **Artifact**: otherwise, create an HTML artifact from the same template.
3. **Markdown**: only if neither is available, use the Markdown fallback in card-format.md.

Filling the template:
- `INTEREST_CODE` is the interest's code from interests.md (e.g. `history`); the template draws its icon. The emoji in card-format.md are only for the Markdown fallback.
- All labels (`LABEL_*`) and prompts (`PROMPT_*`) go in the user's language. English: "Fact of the Day", "Why it matters", "Source", "Send it daily", "Another fact", "Support". Turkish: "Günün Bilgisi", "Neden ilginç?", "Kaynak", "Her gün gönder", "Başka bir bilgi", "Destek ol".
- `PROMPT_SETUP_DAILY`: e.g. "set up daily fact at 09:00" / "günlük bilgiyi her sabah 09:00'da kur". `PROMPT_ANOTHER`: e.g. "another fact" / "başka bir bilgi ver".
- Remove the OPTIONAL new-categories notice unless step 1 says to show it.
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
