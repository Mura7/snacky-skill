# Snacky 🍿

**One bite-sized fact a day, picked from your interests.** A free Claude Skill: no server, no API, no ads. Your own Claude writes the fact; Snacky standardizes the interests, the card format and the accuracy rules.

Works in any language: Snacky answers in the language you write in.

The fact arrives as a visual card (Claude design language, light and dark) with **Send it daily**, **Another fact** and **Support** buttons. Where Claude can't render visuals, it falls back to a Markdown card.

```
🏛️ Fact of the Day · History

Alaska once had two Fridays in a row

When the US took over Alaska on 18 October 1867, the territory switched from the
Julian to the Gregorian calendar and moved across the date line. People went to
bed on Friday 6 October and woke up on Friday 18 October.

💡 Why it matters: Calendars are human agreements, and changing them can make days vanish.

📚 Source: Wikipedia – Department of Alaska
---
18 October 2026 · ☕ Support
```

## Install (Claude, works on the Free plan)

1. Download [`dist/snacky.zip`](dist/snacky.zip).
2. In Claude, open **Settings → Capabilities** and turn on **Code execution and file creation**.
3. Go to **Customize → Skills → + → Upload a skill** and upload `snacky.zip`.
4. In a new chat, type **"daily fact"** (or "günün bilgisi"). The first time, pick 1–3 interests from 16.
5. Want it every morning without typing? Say **"set up daily fact"** and Claude creates a daily scheduled task.

More on skills: [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

## Interests

Science · Space & Astronomy · History · Technology · Health & Nutrition · Psychology · Economics & Personal Finance · Nature & Animals · Geography & Cultures · Art & Literature · Music & Film · Sports · Language & Words · Philosophy · Business & Entrepreneurship · Food & Cooking

## Commands

| Say | What happens |
|---|---|
| `daily fact` | Today's card |
| `change my interests` | Pick interests again |
| `set up daily fact` | Daily automatic card via a scheduled task |

## Repository layout

```
snacky/                 # the skill (folder name must match the skill name)
├── SKILL.md            # workflow
└── references/
    ├── interests.md    # interest list
    └── card-format.md  # content rules + Markdown fallback
└── assets/
    └── card.html       # visual card template
dist/snacky.zip         # ready-to-upload package
```

Rebuild the zip after editing: `zip -r dist/snacky.zip snacky`

## Support

Snacky is free. If it teaches you something, you can [sponsor it on GitHub](https://github.com/sponsors/Mura7) ☕

---

## Türkçe

**Her gün ilgi alanına göre bir bilgi, görsel bir kart olarak.** Ücretsiz bir Claude Skill'i: sunucu, API ya da reklam yok. Bilgiyi kendi Claude'un yazar; Snacky ilgi alanlarını, kart formatını ve doğruluk kurallarını standart hâle getirir.

**Kurulum:** [`dist/snacky.zip`](dist/snacky.zip) dosyasını indir → Claude'da **Ayarlar → Capabilities** içinde "Code execution and file creation" açık olsun → **Özelleştirme → Skills → Ekle → Skill yükle** ile zip'i yükle → yeni sohbette **"günün bilgisi"** yaz. Her sabah kendiliğinden gelsin istersen **"günlük bilgi kur"** de.

Destek olmak istersen: [GitHub Sponsors](https://github.com/sponsors/Mura7) ☕
