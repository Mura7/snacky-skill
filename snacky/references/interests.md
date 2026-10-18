# Interests

**List version: 2**

The user picks **as many interests as they like** (at least one) from this list. If they ask for something not on the list, suggest the closest one; do not go outside the list. Show names in the user's language (Turkish names are given for convenience).

| No | Code | Interest | Türkçe | Subtopics (rotate for variety) |
|---|---|---|---|---|
| 1 | science | Science | Bilim | physics, chemistry, biology, experiments, scientists |
| 2 | space | Space & Astronomy | Uzay ve Astronomi | planets, stars, space missions, sky events |
| 3 | history | History | Tarih | ancient world, Ottoman Empire, world history, on this day |
| 4 | technology | Technology | Teknoloji | inventions, software, AI, history of the internet |
| 5 | health | Health & Nutrition | Sağlık ve Beslenme | the body, sleep, nutrition, exercise (not medical advice) |
| 6 | psychology | Psychology | Psikoloji | cognitive biases, habits, emotions, famous experiments |
| 7 | finance | Economics & Personal Finance | Ekonomi ve Kişisel Finans | basic concepts, history of money, budgeting, investing terms (not investment advice) |
| 8 | nature | Nature & Animals | Doğa ve Hayvanlar | animal behavior, plants, ecosystems, climate |
| 9 | geography | Geography & Cultures | Coğrafya ve Kültürler | countries, traditions, languages, unusual places |
| 10 | art | Art & Literature | Sanat ve Edebiyat | painters, works, writers, movements |
| 11 | music | Music & Film | Müzik ve Sinema | composers, genres, film history, behind the scenes |
| 12 | sports | Sports | Spor | rules, records, sports history, athletes |
| 13 | language | Language & Words | Dil ve Kelimeler | word origins, idioms, a foreign word of the day |
| 14 | philosophy | Philosophy | Felsefe | thinkers, concepts, thought experiments |
| 15 | business | Business & Entrepreneurship | İş ve Girişimcilik | company stories, productivity, marketing concepts |
| 16 | food | Food & Cooking | Yemek ve Mutfak | origins of dishes, kitchen science, practical tips |
| 17 | faith | Quran Verses & Hadith | Ayet ve Hadis | a verse with its meaning, a hadith, context of revelation, a prophet's story from the Quran, a word from the Quran |

Emoji for the Markdown fallback only (the visual card and picker use Lucide icons by code): 🔬 science, 🚀 space, 🏛️ history, 💻 technology, 🫀 health, 🧠 psychology, 💰 finance, 🌿 nature, 🌍 geography, 🎨 art, 🎵 music, ⚽ sports, 🔤 language, 🤔 philosophy, 📈 business, 🍳 food, 📖 faith.

## Changelog

Bump **List version** whenever interests are added. Each line lists the codes that are new in that version; the skill uses this to tell users about new categories.

| Version | New codes |
|---|---|
| 1 | science, space, history, technology, health, psychology, finance, nature, geography, art, music, sports, language, philosophy, business, food |
| 2 | faith |

## Quran Verses & Hadith (faith): sources

Content for this interest must come **only** from the official sources of the Presidency of Religious Affairs of Türkiye (Diyanet İşleri Başkanlığı):

| Content | Source | Address |
|---|---|---|
| Verse text, Diyanet translation (meal), commentary | Diyanet Kur'an-ı Kerim Portalı | https://kuran.diyanet.gov.tr (commentary page per surah: `https://kuran.diyanet.gov.tr/tefsir/sure/{surah number}?kaynak=1`) |
| Hadith with explanation | Hadislerle İslâm (Diyanet, 7 volumes, full text and search) | https://hadislerleislam.diyanet.gov.tr (search: https://hadislerleislam.diyanet.gov.tr/indexarama.php) |
| Hadith and sīra books | Diyanet Dijital library | https://dijital.diyanet.gov.tr/Kitaplik/hadis-ve-siyer |
| Background only (people, places, terms) | TDV İslâm Ansiklopedisi | https://islamansiklopedisi.org.tr |

Rules:
- Before writing the card, open the source page with your web tools and take the verse translation or hadith text **from that page**. Quote it word for word; do not paraphrase inside quotation marks.
- Always give the exact reference: verses as `Surah name surah:verse` (e.g. "İnşirâh 94:5-6"); hadiths with the collection, chapter and number exactly as Hadislerle İslâm gives them.
- Only hadiths found in Hadislerle İslâm or a Diyanet book. Never use a hadith you cannot find there, and never use weak or popular-but-unsourced sayings.
- If you cannot open a Diyanet page in this run, do not quote from memory: give the reference and a short, clearly labeled summary of the meaning instead ("meali özetle"), or pick a hadith from Hadislerle İslâm, which loads as plain text.
- Respectful, non-sectarian tone. No fatwas, rulings or personal religious advice; for questions point to Diyanet's official channels. Do not compare religions or comment on politics.
- In the card, `FACT` holds the verse translation or hadith in quotation marks; `WHY` holds one sentence of context from the Diyanet commentary or explanation.
