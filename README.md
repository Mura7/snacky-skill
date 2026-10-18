# Snacky 🍿

**One bite-sized fact a day, picked from your interests.**

Snacky gives you one accurate, interesting fact per day as a small visual card. You pick your interests once from a list of 17 (science, space, history, technology, health, psychology, finance, nature, geography, art, music and film, sports, language, philosophy, business, food, and Quran verses & hadith). Each day Snacky rotates to the next interest. Claude writes the fact and checks it with web search when that's available; Snacky only standardizes the interests, the card format and the accuracy rules.

Snacky answers in the language you write in.

## Install

**Claude Code / Claude directory:** install the `snacky` plugin.

**Claude.ai (works on the Free plan):**

1. Download [`snacky.zip`](https://github.com/Mura7/snacky-skill/releases/latest/download/snacky.zip) from the latest [release](https://github.com/Mura7/snacky-skill/releases).
2. In Claude, open **Settings → Capabilities** and turn on **Code execution and file creation**.
3. Go to **Customize → Skills → + → Upload a skill** and upload `snacky.zip`.
4. In a new chat, type **"daily fact"** (or "günün bilgisi").

## Use it

| Say | What happens |
|---|---|
| `daily fact` | Today's card. The first time, an interest picker appears. |
| `another fact` | One more card from your interests |
| `change my interests` | Open the picker again |
| `show new categories` | Picker with newly added interests marked |
| `set up daily fact` | Creates a daily scheduled task, only when you ask for it |

The card has two buttons: **Send it daily** (asks Claude to create the daily task) and **Another fact**. Where Claude can't render visuals, the card falls back to Markdown. Icons are [Lucide](https://lucide.dev) (ISC License), embedded in the templates.

## Data

Snacky has no server, no API and no tracking. It sends nothing anywhere and contains no ads.

- If Claude's memory is on, Claude saves your chosen interests, a short list of the last 14 facts it showed you and a card counter, so it doesn't ask again or repeat itself. You can see and delete these in Claude's memory settings.
- Snacky is free and has no ads. If memory is on, after your 10th, 30th and 60th card it adds one short line saying you can support it on GitHub Sponsors; that's at most 3 times ever. It also gives the link if you ask how to support it.
- If web search is on, Claude searches the web to verify each fact and link its source.
- The **Quran Verses & Hadith** interest uses only official Diyanet sources ([kuran.diyanet.gov.tr](https://kuran.diyanet.gov.tr), [hadislerleislam.diyanet.gov.tr](https://hadislerleislam.diyanet.gov.tr)) and gives the exact reference.

## Repository layout

```
.claude-plugin/plugin.json   # plugin manifest
skills/snacky/               # the skill: SKILL.md, references/, assets/
```

Build the claude.ai upload zip: `cd skills && zip -r ../snacky.zip snacky`, then attach it to a GitHub release.

## Türkçe

Her gün ilgi alanına göre bir bilgi, görsel bir kart olarak. Kurulum: son [sürümden](https://github.com/Mura7/snacky-skill/releases/latest/download/snacky.zip) `snacky.zip` dosyasını indir, Claude'da **Özelleştirme → Skills → Ekle → Skill yükle** ile yükle, yeni sohbette **"günün bilgisi"** yaz.

## License

MIT. Source and issues: [github.com/Mura7/snacky-skill](https://github.com/Mura7/snacky-skill)
