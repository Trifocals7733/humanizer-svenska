# Changelog

All notable changes to `humanizer-svenska` are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/).

---

## [4.0.0] - 2026-12-01

### Sammanfattning

Faktaskyddet blev standardens första regel, och skillen delades upp i en kort ingång med referensfiler som agenten läser vid behov. Arbetssättet gick från en förbudslista till en fyra-pass-process med röstskydd, utdatakontrakt och en självkontroll som körs före varje svar. Mönsterkatalogen utökades från 22 till 33 markörer, och varje markör fick ett källäge.

### Varför

Två problem drev bytet. Det första var att konkretionsregeln saknade spärr: standarden uppmanade modellen att byta vaga påståenden mot siffror, utan att säga var siffrorna skulle komma ifrån. Det bjöd in påhittade mätvärden i texter som ska gå till kunder. Det andra var att 22 förbud utan skydd för rösten producerar korrekt, jämn och död prosa. Fler regler ger mer enhetlighet, inte mer människa.

### Added

- **Faktaskyddet:** sakuppgifter rörs aldrig, konkretion får bara bygga på underlaget, och det som kräver uppgifter bara skribenten har hamnar under **Kvar för dig**.
- **`references/monster.md`:** 33 markörer med kännetecken, förklaring, fix och källäge, samt en ärlig lista över vilka som saknar auktoritativ svensk källa.
- **`references/svenska-ord.md`:** utbyteslistor för AI-favoritord, modeord, kanslisvenska enligt Svarta listan, ord-för-ord-svenska, engelska lånord med svensk ändelse, tomma fraser, garderingar, samt mejl, tilltal och avslutningstrappan.
- **`references/typografi.md`:** svenska formregler för tankstreck, citattecken, siffror, rubriker, punktlistor, datum, genitiv och versaler.
- **`references/sjalvkontroll.md`:** 49 punkter med godkänt eller ej godkänt, som körs före varje svar med rättning och omkörning vid underkänt.
- **Röstskyddet:** minsta effektiva ändring, starka meningar lämnas i fred, strykmängden ska stå i proportion till slopet, och minst en mening får vara orörd.
- **Strukturkontrollen:** mönster 32, inläggets form, mätt på styckelängder och första ordet i varje stycke.
- **Nya mönster 23–33:** ord-för-ord-svenska, engelska lånord med svensk ändelse, kanslisvenska verb, substantivsjuka, onödiga synonymbyten, avsändarlös text, retorisk fråga som besvaras, kolon som spänningsknep, den djupa slutraden, jämna stycken och engelsk typografi.

### Changed

- **`SKILL.md`** är omskriven från grunden: ordningen reglerna gäller i, utdatakontrakt per läge, fyra pass, röstskydd, faktaskydd, mönstertabell och routing till referensfilerna.
- **Tankstrecksregeln är korrigerad.** `—` är alltid fel i svensk text. `–` är svenskans tankstreck och används sparsamt: utan mellanslag i intervall, med mellanslag runt inskjutningar. Den tidigare regeln fällde korrekt svenska.
- **Granskningsläget** behåller AI-avtryck 1–10, men betyget beskrivs som ett redaktörsomdöme och ska motiveras med vad som drar upp det.
- **`platforms/`** är synkade mot de nya reglerna och pekar på `SKILL.md` i stället för att duplicera hela regelverket.
- **`tests/benchmark_prompts.md`** har en mätmetod: kör utan och med skillen, jämför faktaskydd, röst, mönster, form, struktur och leverans. Ett femte test tillagt, sakuppgiftstestet, eftersom de fyra ursprungliga texterna inte innehöll en enda siffra att tappa.
- **Citatregeln i loggen är förtydligad.** Det som står före **blev** ska vara ordagrant ur utkastet. Den nya formuleringen behöver inte vara det. Regeln gick inte att följa förut, eftersom ett normalt loggraderingspar citerar både före och efter.
- **`examples/` är omskrivna.** Alla sex visar nu svaret enligt standardläget: texten, **Vad jag ändrade** och **Kvar för dig**. Den tidigare "slutliga mänskliga versionen" fyllde i sakuppgifter som inte fanns i råtexten: ett företag, ett telefonnummer, en leverantör, fyra procentsatser och ett datum. Det lärde ut precis det faktaskyddet förbjuder. `examples/README.md` förklarar bytet.
- **`references/monster.md` står i nummerordning.** Den tematiska grupperingen finns kvar som register högst upp, så mönster 19 går att hitta utan att leta.
- **README är städad.** Inga dekorativa emojis, och texten säljer inte längre in sig mot AI-detektorer. Avsnittet om AI-motorn säger nu att detektorer inte är ett mått och att standarden siktar på läsaren.
- **`platforms/chatgpt/system-prompt.md` är delad i två.** Fältet *Anpassa instruktioner* tar 1 500 tecken och filen pekade dit med en prompt på 5 892. Nu finns en kort version på 1 461 tecken och en full på 5 954 för Custom GPT, Gem och Projects.

### Removed

- Den valfria sammanfattningen i standardläget, som konkurrerade med texten om uppmärksamheten. Den får finnas kvar, men efter **Kvar för dig**.
- Påståendet att standarden lurar AI-detektorer. Standarden riktar sig till läsare och språkvård, och ett betyg är ett omdöme.
- De påhittade sakuppgifterna i exempelfilerna: Alviks Byggteknik, Henrik Lindberg med telefonnummer, Kök & Hem, Voyado, CSRD-siffrorna, datumen i bygglovsbrevet och de 40 sparade arbetstimmarna. Alla var påhittade, och alla togs bort i stället för att skrivas om.

---

## [3.0.0] - 2026-11-01

### Summary

Universell omvandling och stor innehållsuppgradering. Gjorde standarden 100 % plattformsoberoende i ren Markdown med explicit stöd för minimalistiska terminalagenter (Pi Agents), kodredigerare (Cursor, Windsurf), chattgränssnitt (ChatGPT, Claude, Gemini) och GitHub Copilot. 

Implementerade en dedikerad "Anti-AI Engine" mot detektorer (burstiness, V2-fundamentvariation, perplexity, typografisk sanering) samt sex nya AI-mönster (17–22), fyra nya nischer (Klarspråk, E-handel, Rekrytering, Kunddialog) och tre flexibla arbetslägen.

---

### Added

**Universellt stöd & plattformsadaptrar (`platforms/`):**
- **AGENTS.md:** Skapade officiell `AGENTS.md` i enlighet med öppna standarder från Agentic AI Foundation (AAIF) för universellt stöd i alla kodningsagenter.
- **skills.sh:** Lade till officiell badge och installationsinstruktioner för Vercel Labs `skills` CLI (`npx skills add Trifocals7733/humanizer-svenska`).
- **Pi Agents:** Fullt stöd för Mario Zechners minimalistiska terminalagent (`platforms/pi/README.md`) med instruktioner för sessionsanrop och `AGENTS.md`.
- **ChatGPT & Custom GPTs / Gemini Gems:** Högdensitets systemprompt optimerad för tokenbegränsningar (`platforms/chatgpt/system-prompt.md`).
- **Cursor & Windsurf:** Färdig Cursor-regel i modernt MDC-format (`platforms/cursor/humanizer.mdc`).
- **GitHub Copilot:** Workspace-instruktion för `.github/copilot-instructions.md` (`platforms/copilot/copilot-instructions.md`).
- **Anthropic Claude:** Uppdaterad guide för Claude Code och Claude.ai Projects (`platforms/claude/README.md`).

**Anti-AI Engine (Skydd mot detektorer och mänsklig granskning):**
- **Radikal Burstiness:** Tvingande variation i meningslängd (ultrakorta 3–6 ord vs. längre 20–30+ ord) för att krossa AI:s jämntjocka rytm.
- **Svensk V2-Fundamentvariation:** Aktiv växling av fundamentet (tidsadverbial, bisatser, villkor och objekt först) för att bryta subjekt-verb-monotonin.
- **Perplexity-höjning:** Konkretionsprincip som ersätter generiska abstraktioner med specifika mätpunkter, siffror och domäntermer.
- **Typografisk sanering:** Förbud mot engelska tankstreck (`—` eller ` – `) mitt i meningar samt radering av dekorativa emojis och punktlistfeber.

**Nya AI-mönster (6):**
- **Mönster 17: Tankstrecksfrossa (Em-dashes):** Detekterar och eliminerar direktimporterade engelska tankstreck som splittrar meningsbyggnaden.
- **Mönster 18: "Inte bara X, utan även Y"-syndromet:** Avlägsnar klyschan som används för att simulera djup.
- **Mönster 19: Moderna modord & säljfloskler:** Sanerar ord som "sömlös", "robust", "skräddarsydd", "spjutspets", "i framkant".
- **Mönster 20: "Låt oss djupdyka" och metakommentarer:** Raderar föreläsaraktiga metakommentarer där AI kommenterar sitt eget skrivande.
- **Mönster 21: Syntetisk tröst & empati:** Tar bort påklistrad terapeutisk ton i professionella texter.
- **Mönster 22: Falsk sammanfattningsfeber:** Eliminerar mekaniska rubriker ("Slutsats:", "Viktiga lärdomar:") i korta texter under 300 ord.

**Nya nischguider (`genres/`):**
- `genres/klarsprak.md` – Förankrad i **Språklagen (2009:600) 11 §**, ISO 24495-1 och Språkrådets (ISOF) klarspråksprinciper.
- `genres/e-handel.md` – Konkret kundnytta, material, mått och passform framför tomma amerikanska superlativ.
- `genres/rekrytering.md` – Ärliga platsannonser och kravprofiler utan floskler som "spindeln i nätet" och "många bollar i luften".
- `genres/kunddialog.md` – Saklig och snabb service med tydliga steg, utan överdriven servilitet.
- `genres/affarstext.md`, `genres/rapport.md`, `genres/artikel.md`, `genres/sociala-medier.md` – Modulärt utbrutna och fördjupade guider för befintliga genrer.

**Faktiska före/efter-exempel (`examples/`):**
- Återskapade och kompletterade den saknade `examples/`-katalogen med sex fullständiga genomgångar:
  - `examples/affarstext.md`
  - `examples/rapport.md`
  - `examples/artikel.md`
  - `examples/sociala-medier.md`
  - `examples/klarsprak.md`
  - `examples/rekrytering.md`

**Arbetslägen:**
- Införde tre tydliga lägen: `--snabb` (snabbtvätt), Standard (med Anti-AI-reflektion) och `--granska` (redaktörscoach).

**Testtexter:**
- Skapade `tests/benchmark_prompts.md` för att utvärdera modeller och agenter.

---

### Changed

- Versionsbump till 3.0.0.
- `SKILL.md` rensad från Claude-specifik frontmatter (`allowed-tools: [AskUserQuestion]`) och anpassad till universella öppna agent-standarder.
- Snabbreferenstabellen utökad till 36 vanliga AI-byten.
- `README.md` helt omskriven med universell plattformsguide och moderna instruktioner.

---

## [2.0.0] - 2026-03-18

### Summary

Major update. Six new pattern sections, expanded tool access, a Swedish voice demonstration, and an extended quick reference table. The skill now covers the AI writing patterns that were most commonly missed in v1.0.0.

---

### Added

**New pattern sections (6):**

- **Pattern 11: Sycophantic openers and closers** — Detects and removes AI-typical praise phrases ("Vilken bra fråga!", "Hoppas det hjälper!") that immediately signal non-human origin.
- **Pattern 12: Filler phrases** — Targets phrases that add length without content: "i syfte att uppnå detta mål", "på grund av det faktum att", "i nuläget", "det är viktigt att notera att".
- **Pattern 13: Excessive hedging** — Addresses stacked qualifiers ("det kan möjligen argumenteras att detta eventuellt skulle kunna...") with guidance on expressing genuine uncertainty concisely instead.
- **Pattern 14: Knowledge-cutoff disclaimers** — Removes boilerplate like "baserat på tillgänglig information" and "inom ramen för mina kunskaper" that no human writer would include.
- **Pattern 15: Copula avoidance** — Promotes "utgör", "representerar", "fungerar som", "kan beskrivas som" to their own named section with explicit replacement guidance. Previously partially covered under Pattern 1 without a clear fix list.
- **Pattern 16: Bullet/emoji formatting as AI signal** — Addresses the pattern of AI structuring continuous reasoning as decorated bullet lists (💡 🚀 ✅) even when the content does not require list format.

**Voice section:**
- Added "Röst i praktiken: Innan och efter" — a Swedish before/after demonstrating the transformation from technically clean but voiceless text to text with an actual position. Previously the personality section stated principles without a Swedish demonstration.

**Tools:**
- Added `AskUserQuestion` to `allowed-tools`. The skill can now ask for text type when it is not clear from input, enabling correct register application before editing begins.

**Process:**
- Step 1 now explicitly prompts the skill to ask for text type if unclear, paired with the new AskUserQuestion capability.
- Self-critique loop updated to include the third question: "Vad saknar texten för att låta skriven av en verklig person med en verklig åsikt?" — carried over from a gap identified relative to the English humanizer skill.

**Quick reference table:**
- Extended with 10 new rows covering sycophancy, filler phrases, hedging, knowledge disclaimers, copula variants, and emoji/bullet patterns.

---

### Changed

- Version bumped from 1.0.0 to 2.0.0 (breaking in the sense of substantially expanded scope and changed process steps).
- Skill description updated to reflect the six new pattern categories.
- Process section renumbered from 9 steps to 10 steps.

---

### Not changed

- All 10 original patterns retained without modification.
- All four worked examples (affärsskrivande, rapportskrivande, artikel, sociala medier) retained unchanged.
- Register guidance section (four text types) retained unchanged.
- Core philosophy and Nordic voice principles unchanged.

---

## [1.0.0] - 2025-11-01

### Summary

Initial release. Swedish-specific humanizer skill covering 10 AI writing patterns common in professional Swedish text.

### Added

- Pattern 1: Significance inflation (signifikansuppblåsning)
- Pattern 2: Landscape and trend framing (landskap- och trenduppramning)
- Pattern 3: Participle phrases as fake analysis (participfraser som falsk analys)
- Pattern 4: Vague attributions (vaga attributioner)
- Pattern 5: Passive voice as false formality (passiv röst som falsk formalitet)
- Pattern 6: Nominalization overuse (nominaliseringsöverdrift)
- Pattern 7: Anglification imports (anglifieringsimporter)
- Pattern 8: Structural AI patterns (strukturella AI-mönster)
- Pattern 9: Negative parallelism, Swedish variant
- Pattern 10: Social media-specific patterns
- Register guidance for four text types: affärsskrivande, rapportskrivande, artiklar, sociala medier
- Four full worked examples with before/during/after structure
- Quick reference table with 19 swap pairs
- Nordic professional voice section
- Two-step self-critique process
