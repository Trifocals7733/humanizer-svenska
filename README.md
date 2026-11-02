<div align="center">

# 🇸🇪 Humanizer på Svenska

**Universell öppen standard och regelsamling för att ta bort AI-mönster ur professionell svensk text.**

[![skills.sh](https://skills.sh/b/Trifocals7733/humanizer-svenska)](https://skills.sh/Trifocals7733/humanizer-svenska)
[![Språk](https://img.shields.io/badge/språk-svenska%20🇸🇪-005293?style=flat-square)](./SKILL.md)
[![Pi Agents](https://img.shields.io/badge/Pi%20Agents-ready-7C3AED?style=flat-square)](./platforms/pi/README.md)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compatible-blueviolet?style=flat-square)](./SKILL.md)
[![Licens](https://img.shields.io/badge/licens-MIT-blue?style=flat-square)](./LICENSE)

<p align="center">
  <em>Universal Swedish text humanizer. Built from the ground up for the Swedish language in 100% pure Markdown.<br/>
  Compatible with <strong>Pi Agents</strong>, <strong>Claude Code</strong>, <strong>Cursor</strong>, <strong>ChatGPT</strong>, and <strong>Copilot</strong>.</em>
</p>

</div>

---

### ⚡ Snabbtitt: Före och efter

| ❌ Typisk AI-genererad svenska | ✅ Humaniserad professionell svenska |
|---|---|
| *"I en alltmer digitaliserad värld är det avgörande att organisationer proaktivt tar ägarskap över sina processer. Vår innovativa helhetslösning utgör ett banbrytande verktyg som möjliggör en sömlös integration och skapar mervärde i linje med framtidens krav."* | *"Vi kortade orderhanteringen från tre dagar till 20 minuter genom att koppla ihop Visma direkt med lagersystemet. Inga nya konsulter, bara ett API som synkar var femte minut."* |

> [!TIP]
> **Varför reagerar AI-detektorer och läsare?** Det beror sällan på enstaka ord. AI-text avslöjas framför allt av **monoton meningslängd** (alla meningar är 15–20 ord långa), **stel meningsbyggnad** (80 % av meningarna börjar med Subjekt + Verb) och **engelska tankstreck (`—`)**. Standarden tvingar fram naturlig rytm och äkta svenskt språkflöde.

---

## Innehållsförteckning
1. [Varför detta projekt finns](#varför-detta-projekt-finns)
2. [Snabbstart per plattform](#snabbstart-per-plattform)
3. [Tre arbetslägen](#tre-arbetslägen)
4. [Skyddet mot AI-fällan (Anti-AI Engine)](#skyddet-mot-ai-fällan-anti-ai-engine)
5. [De 33 AI-mönstren](#de-33-ai-mönstren)
6. [Nischguider och textgenrer](#nischguider-och-textgenrer)
7. [Faktiska före- och efter-exempel](#faktiska-före--och-efter-exempel)
8. [Snabbreferens för ord- och frasbyten](#snabbreferens-för-ord--och-frasbyten)
9. [Faktaskydd och självkontroll](#faktaskydd-och-självkontroll)
10. [Testa med färdiga benchmarks](#testa-med-färdiga-benchmarks)

---

## Varför detta projekt finns

De flesta AI-humanizers och prompt-instruktioner är utvecklade för engelska. När de översätts rakt av till svenska missar de helt hur språkmodeller faktiskt felar på svenska:

* **Stel låtsasbyråkrati:** AI staplar nominaliseringar (*"genomförandet av etableringen av..."*) och passiva satser i tron att det låter formellt och professionellt. I verkligheten strider det mot modernt svenskt klarspråk.
* **Syntaxfel (V2-monotoni):** På svenska ska verbet komma på andra plats, och infödda skribenter varierar meningsbörjan flitigt. AI börjar nästan varje mening med Subjekt + Verb (*"Detta innebär...", "Företaget erbjuder..."*).
* **Em-dash-sjukan:** Engelska modeller sprider tankstreck (`—`) mitt i meningar, vilket ger en onaturlig och uppstyltad textrytm.
* **Jämntjock rytm (Låg burstiness):** AI skriver nästan alla meningar mellan 14 och 22 ord. Texten saknar mänsklig puls och dynamik.
* **Neutraliserad diplomati:** AI vägrar att ta ställning och slätar över konflikter med "å ena sidan och å andra sidan", utan att landa i en verklig slutsats.

`humanizer-svenska` åtgärdar inte bara orden, utan lär språkmodellen att bygga meningar och argumentera som en erfaren svensk yrkesskribent.

---

## Snabbstart per plattform

Projektet består av ren Markdown och fungerar i alla utvecklingsmiljöer:

### Universal installation via skills.sh CLI
Installera skillen direkt i dina kompatibla agenter med ett enda kommando:
```bash
npx skills add Trifocals7733/humanizer-svenska
```

### 1. Pi Agents (Terminal AI Agent)
Be Pi läsa `SKILL.md` direkt i sessionen:
```bash
pi "Läs SKILL.md och humanisera texten i draft.md (--snabb)"
```
För att sätta det som standard för hela projektet, lägg till referensen i din `AGENTS.md`.  
👉 Se full guide i [`platforms/pi/README.md`](./platforms/pi/README.md).

### 2. Cursor & Windsurf
Lägg regeln i projektets `.cursor/rules/`:
Kopiera [`platforms/cursor/humanizer.mdc`](./platforms/cursor/humanizer.mdc) till `.cursor/rules/humanizer.mdc`. Regeln aktiveras automatiskt för markdown-filer och texter.

### 3. ChatGPT, Custom GPTs & Gemini Gems
Kopiera den färdiga systempromptern från [`platforms/chatgpt/system-prompt.md`](./platforms/chatgpt/system-prompt.md) och klistra in i dina Custom Instructions eller som instruktion i en Custom GPT / Gem.

### 4. Anthropic Claude (Claude Code & Projects)
* **Claude Code:** Klona repot till `~/.claude/skills/humanizer-svenska` och kör `/humanizer-svenska`.
* **Claude.ai Projects:** Klistra in systeminstruktionen i dina Project Instructions.  
👉 Se full guide i [`platforms/claude/README.md`](./platforms/claude/README.md).

### 5. GitHub Copilot
Kopiera anvisningarna från [`platforms/copilot/copilot-instructions.md`](./platforms/copilot/copilot-instructions.md) till din `.github/copilot-instructions.md`.

---

## Tre arbetslägen

Du kan styra hur agenten levererar texten genom att ange ett läge:

1. **`--snabb` (Snabbtvätt)**  
   Returnerar enbart den färdiga texten direkt. Inga kommentarer, inga punktlistor, ingen analys. Perfekt för snabb redigering direkt i filer.
2. **Standardläge (Rekommenderat)**  
   Levererar hela den omskrivna texten, följt av **Vad jag ändrade** med ordagranna citat ur utkastet, och sist **Kvar för dig** med det bara du kan fylla i: en saknad siffra, en källa, ett skäl att skriva just i dag. Ingen inledande rapport om vad agenten läst eller tänker göra.
3. **`--granska` (Redaktörscoach)**  
   Skriver inte om texten. Agerar redaktör: namnger varje mönster med ett eget citat och en kort fix, och avslutar med ett **AI-avtryck 1–10**. Betyget är ett redaktörsomdöme, inte en detektormätning, och det ska motiveras med vad som drar upp det.

---

## Skyddet mot AI-fällan (Anti-AI Engine)

Många tror att det räcker med att byta ut några enstaka klyschor. Men matematiska AI-detektorer (Copyleaks, GPTZero, Turnitin) och vana mänskliga läsare reagerar på underliggande matematiska och stilistiska mönster.

Standarden tvingar därför modellen att följa fem strukturella principer:

1. **Radikal Burstiness (Meningslängdsvariation):**  
   AI håller sig bekvämt i mitten (15–20 ord). Standarden tvingar fram tvära kast: en mening på några ord, sedan en lång period där tanken kräver det, sedan ett konstaterande. Ingen fast mall, för en mall blir en ny metronom. En rad korta hackiga meningar i följd är också en markör.
2. **Svensk fundamentvariation (V2-regeln):**  
   Förbjuder att mer än hälften av meningarna inleds med Subjekt + Verb. Tidsuttryck (*"I våras..."*), platser, bisatser (*"När testerna avbröts..."*) och villkor kan stå först och skapa ett naturligt svenskt flöde. Flytta fundamentet när det passar, inte enligt en kvot: mekanisk variation syns lika tydligt som ingen variation.
3. **Hög Perplexity genom konkretion:**  
   AI väljer statistiskt förutsägbara ord. Standarden kräver specifika fackord, exakta siffror, tidsramar och mätpunkter istället för generella påståenden som *"stora möjligheter"* eller *"starka resultat"*. Uppgifterna måste redan finnas i underlaget. Hittar agenten inte siffran ska den lämna meningen allmän och säga det, aldrig fylla i en rimlig.
4. **Typografisk sanering (Stoppa em-dashes):**  
   `—` hör inte hemma i svensk text. Svenska tankstrecket `–` används sparsamt: utan mellanslag i intervall (9–18) och med mellanslag runt inskjutningar. I övrigt punkt, komma eller parentes. Dekorativa emojis och punktlistor rensas bort.
5. **Skyddad röst:**  
   Minsta effektiva ändring. Starka meningar lämnas i fred, och en text som var i gott skick kommer inte tillbaka halverad. En text där varje mening är putsad är jämn, och jämn är den starkaste markören av alla.
6. **Ställningstagande och nordisk ton:**  
   Svensk yrkeston bygger på saklighet, direkthet och understatement. Texten vågar prioritera bort det som inte fungerar och slutar låtsas att allt är problemfritt.

> [!IMPORTANT]
> **Faktaskyddet går före allt annat.** Belopp, datum, namn och källor rörs aldrig. Konkretion får bara bygga på uppgifter som redan finns i utkastet. Det som inte går att skriva konkret utan påhittade fakta hamnar under **Kvar för dig**, aldrig i texten.

---

## De 33 AI-mönstren

Huvuddokumentet [`SKILL.md`](./SKILL.md) innehåller arbetsgången och mönstren i kortform. Den fullständiga katalogen med kännetecken, förklaring, fix och källor för varje mönster finns i [`references/monster.md`](./references/monster.md):

<details open>
<summary><strong>📋 Klicka här för att visa/dölja mönsteröversikten</strong></summary>

<br/>

| # | Mönster | Exempel / Trigger |
|---|---|---|
| 1 | **Signifikansuppblåsning** | "banbrytande", "avgörande", "paradigmskifte", "vittnar om" |
| 2 | **Landskaps- och trendinledningar** | "i en alltmer digitaliserad värld", "spelplanen förändras" |
| 3 | **Participfraser som falsk analys** | "belyser vikten av", "understryker behovet av" |
| 4 | **Vaga auktoriteter** | "experter menar", "forskning visar", "branschkällor pekar på" |
| 5 | **Passiv röst som falsk formalitet** | "det kan konstateras att", "det bör påpekas att" |
| 6 | **Nominaliseringsöverdrift** | "implementeringen av", "säkerställandet av" |
| 7 | **Anglifieringsimporter** | "ta ägarskap över", "navigera förändringen", "leverera värde" |
| 8 | **Strukturella mönster & tretal** | "snabbt, enkelt och effektivt", falsk balans, jämna stycken |
| 9 | **Negativ parallellism** | "Det handlar inte om teknik, det handlar om människor" |
| 10 | **Sociala medier-tells** | "Jag delar en reflektion...", generiska hashtag-staplar |
| 11 | **Sycofantiska artighetsfraser** | "Vilken bra fråga!", "Hoppas detta hjälper dig!" |
| 12 | **Utfyllnadsfraser** | "i syfte att uppnå", "på grund av det faktum att", "i nuläget" |
| 13 | **Överdriven hedging** | "det kan möjligen argumenteras att detta eventuellt skulle kunna..." |
| 14 | **Kunskapsavgränsningar** | "Baserat på tillgänglig info...", "Inom ramen för vad som är känt..." |
| 15 | **Kopulaundvikande** | "utgör", "representerar", "fungerar som" (istället för "är") |
| 16 | **Bullet- och emojifeber** | Dekorativa listor med 🚀 💡 ✅ och fetstilta inledningsord |
| 17 | **Tankstrecksfrossa (Em-dashes)** | Meningar splittrade med `—` för att simulera eftertanke |
| 18 | **"Inte bara X, utan även Y"** | Kliché för att låta djupsinnig utan att tillföra fakta |
| 19 | **Moderna modord & floskler** | "sömlös", "robust", "skräddarsydd", "spjutspets", "i framkant" |
| 20 | **"Låt oss djupdyka"** | Föreläsaraktiga metakommentarer där AI kommenterar sitt skrivande |
| 21 | **Syntetisk tröst & empati** | "Vi förstår att detta kan kännas överväldigande..." |
| 22 | **Falsk sammanfattningsfeber** | Tvingande rubriker ("Slutsats:") i korta texter under 300 ord |
| 23 | **Ord-för-ord-svenska** | "adressera ett problem", "spendera tid", "vara på samma sida" |
| 24 | **Engelska lånord med svensk ändelse** | asken, caset, insighten, learnings |
| 25 | **Kanslisvenska verb** | erhålla, nyttja, erfordras, tillställa, åligger |
| 26 | **Substantivsjuka** | "ta ett beslut", "göra en bedömning", "vidta åtgärder" |
| 27 | **Onödiga synonymbyten** | samma sak i tre olika ord i rad |
| 28 | **Avsändarlös text** | "Många företag upplever att", utan jag-form och förstahandsmaterial |
| 29 | **Retorisk fråga som besvaras** | "Vad betyder det här? Det betyder att..." |
| 30 | **Kolon som spänningsknep** | nominalfras: poängen, med liten bokstav |
| 31 | **Den djupa slutraden** | en byggd aforism som sista mening |
| 32 | **Jämna stycken och inläggets form** | alla stycken en till tre meningar, ensamt fragment, kort slutrad |
| 33 | **Engelsk typografi** | `“ord”`, `12.5%`, title case, punkt efter rubrik |

</details>

---

## Nischguider och textgenrer

Olika texttyper kräver olika register. Fördjupade guider finns i katalogen [`genres/`](./genres/):

* **[Affärsskrivande](./genres/affarstext.md):** Mejl, offerter och förslag. Fokus på direkthet, tydliga priser och lågmäld trovärdighet.
* **[Rapportskrivande](./genres/rapport.md):** Utredningar och analyser. Krav på källhänvisningar, metod och hårda prioriteringar i slutsatserna.
* **[Artiklar & Tankeledarskap](./genres/artikel.md):** Krönikor och debattinlägg. Öppna med tesen, skapa friktion och ta ställning.
* **[Sociala medier](./genres/sociala-medier.md):** LinkedIn. Verkliga observationer och misslyckanden istället för framgångsteater och klyschor.
* **[Klarspråk & Myndighetstext](./genres/klarsprak.md):** Offentlig förvaltning enligt **Språklagen 11 §** och ISO 24495-1. Tydliga roller (*vi* beslutar, *du* gör).
* **[E-handel & Produkttexter](./genres/e-handel.md):** Konkret kundnytta, material, mått och passform istället för tomma superlativ.
* **[Rekrytering & HR](./genres/rekrytering.md):** Ärliga platsannonser utan "spindeln i nätet" eller "många bollar i luften".
* **[Kunddialog & Support](./genres/kunddialog.md):** Snabb hjälp, tydliga steg för kunden och noll servil låtsasempati.

---

## Faktiska före- och efter-exempel

Exemplen visar arbetsprocessen: råtext, identifierade mönster, utkast, självgranskning och slutversion. Själva svarsformatet, alltså vad agenten lämnar tillbaka, står i avsnitt 2 i [`SKILL.md`](./SKILL.md).

I katalogen [`examples/`](./examples/) hittar du fullständiga genomgångar med råtext från AI, identifierade mönster, utkast, anti-AI-självgranskning och slutlig mänsklig version:

* [`examples/affarstext.md`](./examples/affarstext.md) – B2B-försäljning och integrationer
* [`examples/rapport.md`](./examples/rapport.md) – Hållbarhetsrapport enligt CSRD
* [`examples/artikel.md`](./examples/artikel.md) – Debattartikel om generativ AI inom marknadsföring
* [`examples/sociala-medier.md`](./examples/sociala-medier.md) – LinkedIn-inlägg om möteskultur
* [`examples/klarsprak.md`](./examples/klarsprak.md) – Kommunalt bygglovsärende
* [`examples/rekrytering.md`](./examples/rekrytering.md) – Platsannons för projektledare inom bygg och installation

---

## Snabbreferens för ord- och frasbyten

<details>
<summary><strong>🔍 Klicka här för att öppna den kompletta listan med 36 ord- och frasbyten</strong></summary>

<br/>

| AI-svenska | Ersätt med naturlig svenska |
|---|---|
| "det kan konstateras att" | skriv påståendet direkt |
| "belyser vikten av" | stryk eller skriv vad som är viktigt och varför |
| "i en alltmer digitaliserad värld" | stryk, gå rakt på poängen |
| "sammantaget representerar detta" | stryk, avsluta med fakta |
| "navigera förändringen" | "hantera förändringen", "hitta rätt" |
| "proaktivt" | "tidigt", "i förväg", eller stryk |
| "holistiskt" | "i sin helhet", "samlat" |
| "ta ägarskap över" | "ansvara för", "driva frågan" |
| "implementeringen av" | "att införa", "när vi inför" |
| "å ena sidan... å andra sidan" | ta ställning och dra slutsats |
| "möjligheterna är stora" | vilka möjligheter? för vem? |
| "avgörande" / "banbrytande" | stryk eller bevisa med mätdata |
| "vittnar om" | "visar", "tyder på" |
| "utgör" / "representerar" | "är", "innebär" |
| "fungerar som" | "är", "kopplar ihop" |
| "möjliggör" | "gör det möjligt", "låter oss" |
| "det är viktigt att notera" | skriv påståendet direkt |
| "avslutningsvis" | stryk, avsluta med substans |
| "Vilken bra fråga!" | stryk helt |
| "Hoppas det hjälper!" | stryk helt |
| "i syfte att uppnå" | "för att" |
| "på grund av det faktum att" | "eftersom" |
| "i dagsläget" / "i nuläget" | "nu" |
| "baserat på tillgänglig info" | stryk, skriv vad du vet |
| "det kan möjligen argumenteras" | ta ställning eller precisera osäkerheten |
| "sömlös" | "automatisk", "utan avbrott" |
| "robust" | "stabil", "tålig", "beprövad" |
| "skräddarsydd" | "anpassad för X" |
| "spjutspets" / "i framkant" | beskriv den faktiska tekniken/lösningen |
| "brinner för" (rekrytering) | "är intresserad av", "har erfarenhet av" |
| "spindeln i nätet" | beskriv de faktiska samordningsuppgifterna |
| "många bollar i luften" | "prioriterar när flera uppgifter krockar" |
| "låt oss djupdyka" | stryk och gå direkt på analysen |
| "inte bara X, utan även Y" | formulera ett rakt påstående |
| tankstreck mitt i meningar (`—`) | använd `–` sparsamt, annars punkt eller kommatecken |
| dekorativa emojis (🚀, 💡, ✅) | stryk |

</details>

---

## Faktaskydd och självkontroll

Två saker skiljer standarden från en vanlig ordlista, och de ligger i [`references/`](./references/):

* **[`sjalvkontroll.md`](./references/sjalvkontroll.md):** 49 punkter som agenten kör före varje svar, med godkänt eller ej godkänt. Vid ej godkänt rättas texten och listan körs om. Användaren ser bara texten, **Vad jag ändrade** och **Kvar för dig**.
* **[`svenska-ord.md`](./references/svenska-ord.md)** och **[`typografi.md`](./references/typografi.md):** utbyteslistor för AI-ord, kanslisvenska, ord-för-ord-svenska och engelska lånord, samt de svenska formreglerna för tecken, siffror och rubriker.

---

## Testa med färdiga benchmarks

Vill du utvärdera hur bra en specifik modell (t.ex. Claude 3.7, GPT-4o, Gemini 2.5) eller agent presterar tillsammans med standarden?  
Kör testtexterna i [`tests/benchmark_prompts.md`](./tests/benchmark_prompts.md).

---

## Licens & Versionshistorik

- **Licens:** [MIT License](./LICENSE)
- **Ändringslogg:** Fullständig historik finns i [`CHANGELOG.md`](./CHANGELOG.md).
