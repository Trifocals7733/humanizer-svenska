<div align="center">

# Humanizer på svenska

**Universell öppen standard och regelsamling för att ta bort AI-mönster ur professionell svensk text.**

[![skills.sh](https://skills.sh/b/Trifocals7733/humanizer-svenska)](https://skills.sh/Trifocals7733/humanizer-svenska)
[![Språk](https://img.shields.io/badge/språk-svenska-005293?style=flat-square)](./SKILL.md)
[![Pi Agents](https://img.shields.io/badge/Pi%20Agents-ready-7C3AED?style=flat-square)](./platforms/pi/README.md)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compatible-blueviolet?style=flat-square)](./SKILL.md)
[![Licens](https://img.shields.io/badge/licens-MIT-blue?style=flat-square)](./LICENSE)

<p align="center">
  <em>Universal Swedish text humanizer. Built from the ground up for the Swedish language in 100% pure Markdown.<br/>
  Compatible with <strong>Pi Agents</strong>, <strong>Claude Code</strong>, <strong>Cursor</strong>, <strong>ChatGPT</strong>, and <strong>Copilot</strong>.</em>
</p>

</div>

---

### Snabbtitt: före och efter

| Typisk AI-genererad svenska | Humaniserad professionell svenska |
|---|---|
| *”I en alltmer digitaliserad värld är det avgörande att organisationer proaktivt tar ägarskap över sina processer. Genom att koppla ihop Visma med lagersystemet har vi möjliggjort en sömlös integration som kortat orderhanteringen från tre dagar till 20 minuter, vilket skapar mervärde i linje med framtidens krav.”* | *”Vi har kopplat ihop Visma med lagersystemet. Orderhanteringen tar nu 20 minuter i stället för tre dagar.”* |

Varje uppgift i högerkolumnen står redan i vänsterkolumnen: Visma, lagersystemet, tre dagar och 20 minuter. Inget är tillagt, och talen har kvar sin form.

> [!TIP]
> **Varför reagerar läsaren?** Det beror sällan på enstaka ord. AI-text avslöjas oftare av formen: meningar som är ungefär lika långa, meningsbörjan som påfallande ofta är subjekt och verb, och det amerikanska strecket `—`. Därför arbetar standarden med formen lika mycket som med orden.

---

## Innehållsförteckning
1. [Varför detta projekt finns](#varför-detta-projekt-finns)
2. [Snabbstart per plattform](#snabbstart-per-plattform)
3. [Fyra arbetslägen](#fyra-arbetslägen)
4. [Skyddet mot AI-fällan (anti-AI-motorn)](#skyddet-mot-ai-fällan-anti-ai-motorn)
5. [De 33 AI-mönstren](#de-33-ai-mönstren)
6. [Ord som ändrar betydelsen](#ord-som-ändrar-betydelsen)
7. [Nischguider och textgenrer](#nischguider-och-textgenrer)
8. [Faktiska före- och efter-exempel](#faktiska-före--och-efter-exempel)
9. [Snabbreferens för ord- och frasbyten](#snabbreferens-för-ord--och-frasbyten)
10. [Faktaskydd och självkontroll](#faktaskydd-och-självkontroll)
11. [Testa med färdiga benchmarks](#testa-med-färdiga-benchmarks)
12. [Medvetna val och begränsningar](#medvetna-val-och-begränsningar)

---

## Varför detta projekt finns

De flesta AI-humanizers och prompt-instruktioner är utvecklade för engelska. När de översätts rakt av till svenska missar de hur språkmodeller faktiskt felar på svenska:

* **Stel låtsasbyråkrati:** AI staplar nominaliseringar (*”genomförandet av etableringen av...”*) och passiva satser i tron att det låter formellt och professionellt. I verkligheten strider det mot modernt svenskt klarspråk.
* **Monoton meningsbörjan:** Svenskan har V2-ordföljd och fritt fundament, och den som skriver varierar meningsbörjan. Modeller börjar påfallande ofta med subjekt och verb (*”Detta innebär...”, ”Företaget erbjuder...”*).
* **Det amerikanska strecket:** Modeller sprider `—` mitt i meningar. Svenska skrivregler har ett eget tankstreck, `–`, och det används sparsamt.
* **Jämntjock rytm (låg burstiness):** Modelltext lägger sig gärna runt 15–20 ord per mening. Texten saknar puls.
* **Neutraliserad diplomati:** AI slätar över konflikter med ”å ena sidan och å andra sidan”, utan att landa i en verklig slutsats.
* **Ord som säger något annat:** Modeller skriver *teknologi* för technology, *eventuellt* för eventually och *tack vare* om en negativ orsak. Orden ser svenska ut men betyder något annat än skribenten menar.

`humanizer-svenska` arbetar med både orden och meningsbyggnaden, och lär modellen att redigera som en erfaren svensk yrkesskribent, utan att hitta på något.

---

## Snabbstart per plattform

Projektet består av ren Markdown och fungerar i alla utvecklingsmiljöer:

### Installation via skills.sh
Installera skillen i dina kompatibla agenter med ett kommando:
```bash
npx skills add Trifocals7733/humanizer-svenska
```
En installerad kopia uppdateras inte av sig själv. Kör `npx skills update` när en ny version kommer.

### 1. Pi Agents (terminalagent)
Be Pi läsa `SKILL.md` direkt i sessionen:
```bash
pi "Läs SKILL.md och humanisera texten i draft.md med --snabb"
```
För att sätta det som standard för hela projektet, lägg till referensen i din `AGENTS.md`.  
Se full guide i [`platforms/pi/README.md`](./platforms/pi/README.md).

### 2. Cursor och Windsurf
Kopiera [`platforms/cursor/humanizer.mdc`](./platforms/cursor/humanizer.mdc) till `.cursor/rules/humanizer.mdc`. Regeln aktiveras automatiskt för markdown-filer och texter.

### 3. ChatGPT, Custom GPTs och Gemini Gems
Kopiera den färdiga systemprompten från [`platforms/chatgpt/system-prompt.md`](./platforms/chatgpt/system-prompt.md). Kortversionen ryms i fältet *Anpassa instruktioner*, och den fulla passar en Custom GPT eller en Gem.

### 4. Claude (Claude Code och Claude-appen)
* **Claude Code:** Klona repot till `~/.claude/skills/humanizer-svenska`, eller kör `npx skills add`, och anropa `/humanizer-svenska`.
* **Claude-appen:** Ladda upp hela mappen som zip-fil bland skills, eller klistra in systemprompten i ett projekts instruktioner.  
Se full guide i [`platforms/claude/README.md`](./platforms/claude/README.md).

### 5. GitHub Copilot
Kopiera anvisningarna från [`platforms/copilot/copilot-instructions.md`](./platforms/copilot/copilot-instructions.md) till din `.github/copilot-instructions.md`.

---

## Fyra arbetslägen

Du styr vad agenten lämnar tillbaka genom att ange ett läge:

1. **`--snabb` (snabbtvätt)**  
   Returnerar bara den färdiga texten. Inga kommentarer, inga punktlistor, ingen analys. Passar för redigering direkt i filer. Faktaskyddet gäller ändå: saknas en uppgift står meningen kvar allmän.
2. **Standardläge (rekommenderat)**  
   Levererar hela den omskrivna texten, följt av **Vad jag ändrade** med ordagranna citat ur utkastet, och sist **Kvar för dig** med det bara du kan fylla i: en saknad siffra, en källa, ett skäl att skriva just i dag. Ingen inledande rapport om vad agenten läst eller tänker göra.
3. **`--granska` (redaktörscoach)**  
   Skriver inte om texten. Agerar redaktör: namnger varje mönster med ett eget citat och en kort fix, och avslutar med ett **AI-avtryck 1–10**. Betyget är ett redaktörsomdöme, inte en detektormätning, och det ska motiveras med vad som drar upp det.
4. **Eget skrivande**  
   När agenten själv skriver svensk text och inget utkast finns. Den levererar bara texten, kör självkontrollen tyst och skriver en hakparentes som `[datum]` där en uppgift saknas, i stället för att hitta på den.

---

## Skyddet mot AI-fällan (anti-AI-motorn)

Många tror att det räcker med att byta ut några enstaka klyschor. Men texten avslöjas av strukturen, och en van läsare känner igen den utan att kunna peka på varför.

AI-detektorer är inget mått. De ger falska träffar på text som skrivits av människor, och de kan inte skilja på en städad text och en mänsklig. Standarden siktar därför på läsaren: en människa som arbetar med språk, och som märker när något inte stämmer.

Standarden följer sex principer:

1. **Radikal burstiness (meningslängdsvariation):**  
   Modelltext håller sig gärna runt 15–20 ord per mening. Standarden kräver tvära kast: en mening på några ord, sedan en lång period där tanken kräver det, sedan ett konstaterande. Ingen fast mall, för en mall blir en ny metronom. En rad korta hackiga meningar i följd är också en markör.
2. **Svensk fundamentvariation (V2-regeln):**  
   Svenskan har V2-ordföljd och fritt fundament. Tidsuttryck (*”I våras...”*), platser, bisatser (*”När testerna avbröts...”*) och villkor kan stå först. Flytta fundamentet när det passar, inte enligt en kvot: mekanisk variation syns lika tydligt som ingen variation.
3. **Hög perplexity genom konkretion:**  
   AI väljer statistiskt förutsägbara ord. Standarden kräver specifika fackord, exakta siffror, tidsramar och mätpunkter i stället för generella påståenden som *”stora möjligheter”* eller *”starka resultat”*. Uppgifterna måste redan finnas i underlaget. Hittar agenten inte siffran ska den lämna meningen allmän och säga det, aldrig fylla i en rimlig.
4. **Typografisk sanering:**  
   `—` hör inte hemma i svensk text. Svenska tankstrecket `–` används sparsamt: utan mellanslag i intervall (9–18) och med mellanslag runt inskjutningar. I övrigt punkt, komma eller parentes. Inget komma före och i uppräkningar. Dekorativa emojis och punktlistor rensas bort.
5. **Skyddad röst:**  
   Minsta effektiva ändring. Starka meningar lämnas i fred, och en text som var i gott skick kommer inte tillbaka halverad. En text där varje mening är putsad är jämn, och jämn är den starkaste markören av alla.
6. **Ställningstagande och nordisk ton:**  
   Svensk yrkeston bygger på saklighet, direkthet och understatement. Texten vågar prioritera bort det som inte fungerar och slutar låtsas att allt är problemfritt. Ståndpunkten är skribentens: agenten skriver fram den som finns i utkastet och hittar aldrig på en egen.

> [!IMPORTANT]
> **Faktaskyddet går före allt annat.** Belopp, datum, namn och källor rörs aldrig. Konkretion får bara bygga på uppgifter som redan finns i utkastet. Det som inte går att skriva konkret utan påhittade fakta hamnar under **Kvar för dig**, och i eget skrivande som en hakparentes. En påhittad uppgift hamnar aldrig i texten.

---

## De 33 AI-mönstren

Huvuddokumentet [`SKILL.md`](./SKILL.md) innehåller arbetsgången och mönstren i kortform. Den fullständiga katalogen med kännetecken, förklaring, fix och källor för varje mönster finns i [`references/monster.md`](./references/monster.md). Namnen nedan är desamma i alla filer, och i granskningsläget används de ordagrant.

<details open>
<summary><strong>Visa eller dölj mönsteröversikten</strong></summary>

<br/>

| # | Mönster | Exempel eller kännetecken |
|---|---|---|
| 1 | **Signifikansuppblåsning** | ”banbrytande”, ”avgörande”, ”paradigmskifte”, ”vittnar om” |
| 2 | **Landskaps- och trenduppramning** | ”i en alltmer digitaliserad värld”, ”spelplanen förändras” |
| 3 | **Participfraser som falsk analys** | ”belyser vikten av”, ”understryker behovet av” |
| 4 | **Vaga auktoriteter** | ”experter menar”, ”forskning visar”, ”branschkällor pekar på” |
| 5 | **Passiv formalitet** | ”det kan konstateras att”, ”det bör påpekas att” |
| 6 | **Nominaliseringsöverdrift** | ”implementeringen av”, ”säkerställandet av” |
| 7 | **Anglifieringsimporter** | ”ta ägarskap över”, ”navigera förändringen”, ”leverera värde” |
| 8 | **Tretalsregeln och falsk balans** | ”snabbt, enkelt och effektivt”, å ena sidan utan slutsats |
| 9 | **Negativ parallellism** | ”Det handlar inte om teknik, det handlar om människor” |
| 10 | **Sociala medier-fällor** | ”Jag delar en reflektion...”, generiska hashtag-staplar |
| 11 | **Fjäsk** | ”Vilken bra fråga!”, ”Hoppas detta hjälper dig!” |
| 12 | **Utfyllnadsfraser** | ”i syfte att uppnå”, ”på grund av det faktum att”, ”i nuläget” |
| 13 | **Överdriven gardering** | ”det kan möjligen argumenteras att detta eventuellt skulle kunna...” |
| 14 | **Kunskapsavgränsningar** | ”Baserat på tillgänglig info...”, ”Inom ramen för vad som är känt...” |
| 15 | **Kopulaundvikande** | ”utgör”, ”representerar”, ”fungerar som” i stället för ”är” |
| 16 | **Punktliste- och emojifeber** | Dekorativa listor med 🚀 💡 ✅ och fetstilta inledningsord |
| 17 | **Tankstrecksfrossa** | Meningar splittrade med `—` för att simulera eftertanke |
| 18 | **Inte bara X, utan även Y** | Kliché för att låta djupsinnig utan att tillföra fakta |
| 19 | **Modeord och säljfloskler** | ”sömlös”, ”robust”, ”skräddarsydd”, ”spjutspets”, ”i framkant” |
| 20 | **Låt oss djupdyka** | Föreläsaraktiga metakommentarer där AI kommenterar sitt skrivande |
| 21 | **Syntetisk tröst** | ”Vi förstår att detta kan kännas överväldigande...” |
| 22 | **Falsk sammanfattningsfeber** | Tvingande rubriker (”Slutsats:”) i korta texter under 300 ord |
| 23 | **Ord-för-ord-svenska** | ”adressera ett problem”, ”spendera tid”, ”vara på samma sida” |
| 24 | **Engelska lånord med svensk ändelse** | asken, caset, insighten, learnings |
| 25 | **Kanslisvenska verb** | erhålla, nyttja, erfordras, tillställa, åligger |
| 26 | **Substantivsjuka** | ”ta ett beslut”, ”göra en bedömning”, ”vidta åtgärder” |
| 27 | **Onödiga synonymbyten** | samma sak i tre olika ord i rad |
| 28 | **Avsändarlös text** | ”Många företag upplever att”, utan jag-form och förstahandsmaterial |
| 29 | **Retorisk fråga som besvaras** | ”Vad betyder det här? Det betyder att...” |
| 30 | **Kolon som spänningsknep** | nominalfras: poängen, med liten bokstav |
| 31 | **Den djupa slutraden** | en byggd aforism som sista mening |
| 32 | **Jämna stycken och inläggets form** | alla stycken en till tre meningar, ensamt fragment, kort slutrad |
| 33 | **Engelsk typografi** | `“ord”`, `12.5%`, title case, punkt efter rubrik, komma före och |

</details>

---

## Ord som ändrar betydelsen

Vissa fel ändrar vad texten säger. *Tack vare* säger att orsaken var något att tacka för. *Förväntas* säger att någon hoppas på det. *Ska* gör ett förslag till ett beslut, och 2 % är inte samma sak som 2 procentenheter. Till det kommer falska vänner som *eventuellt* för eventually, *realisera* för realize och *biljon* för billion.

Agenten rättar dem när utkastet visar vad som menas. Rör ordet en siffra eller ett åtagande låter agenten det stå och frågar under **Kvar för dig**. Listorna, kontrollerade mot TT-språket, finns i [`references/svenska-ord.md`](./references/svenska-ord.md).

Tvekar agenten om en fras är etablerad svenska kan den, om den har webbåtkomst, jämföra frekvenser i Språkbankens korpusar enligt [`references/frekvenstest.md`](./references/frekvenstest.md).

---

## Nischguider och textgenrer

Olika texttyper kräver olika register. Fördjupade guider finns i katalogen [`genres/`](./genres/):

* **[Affärsskrivande](./genres/affarstext.md):** Mejl, offerter och förslag. Ämnesrad, första meningen, ett ärende per mejl och lågmäld trovärdighet.
* **[Presentationer](./genres/presentation.md):** Rubriken som budskap, en poäng per bild och talmanus som går att säga högt.
* **[Rapportskrivande](./genres/rapport.md):** Utredningar och analyser. Krav på källhänvisningar, metod och hårda prioriteringar i slutsatserna.
* **[Artiklar och tankeledarskap](./genres/artikel.md):** Krönikor och debattinlägg. Öppna med tesen och skriv fram skribentens ståndpunkt.
* **[Sociala medier](./genres/sociala-medier.md):** LinkedIn. Verkliga observationer och misslyckanden i stället för framgångsteater och klyschor.
* **[Klarspråk och myndighetstext](./genres/klarsprak.md):** Offentlig förvaltning enligt **Språklagen 11 §** och ISO 24495-1. Tydliga roller (*vi* beslutar, *du* gör).
* **[E-handel och produkttexter](./genres/e-handel.md):** Konkret kundnytta, material, mått och passform i stället för tomma superlativ.
* **[Rekrytering och HR](./genres/rekrytering.md):** Ärliga platsannonser utan ”spindeln i nätet” eller ”många bollar i luften”.
* **[Kunddialog och support](./genres/kunddialog.md):** Snabb hjälp, tydliga steg för kunden och ingen servil låtsasempati.

---

## Faktiska före- och efter-exempel

Exemplen visar samma tre saker som svaret ska innehålla: råtexten, de mönster som hittades, och vad agenten lämnar tillbaka enligt standardläget. Alltså texten, **Vad jag ändrade** och **Kvar för dig**.

Ingen av dem fyller i en sakuppgift eller en ståndpunkt som inte stod i råtexten. Där underlaget inte räcker blir texten kortare och **Kvar för dig** längre. Läs [examples/README.md](./examples/README.md) för varför, och vad som ändrades i v4.0.0 och v4.1.0.

* [`examples/affarstext.md`](./examples/affarstext.md): kall B2B-outreach utan en enda uppgift
* [`examples/rapport.md`](./examples/rapport.md): sammanfattning utan resultat
* [`examples/artikel.md`](./examples/artikel.md): debattartikel där skribentens tes står kvar och agenten inte väljer sida
* [`examples/sociala-medier.md`](./examples/sociala-medier.md): LinkedIn-inlägg och inläggets form
* [`examples/klarsprak.md`](./examples/klarsprak.md): kommunalt bygglovsärende med juridiskt innehåll
* [`examples/rekrytering.md`](./examples/rekrytering.md): platsannons utan villkor

---

## Snabbreferens för ord- och frasbyten

<details>
<summary><strong>Öppna listan med ord- och frasbyten</strong></summary>

<br/>

| AI-svenska | Ersätt med naturlig svenska |
|---|---|
| ”det kan konstateras att” | skriv påståendet direkt |
| ”belyser vikten av” | stryk eller skriv vad som är viktigt och varför |
| ”i en alltmer digitaliserad värld” | stryk, gå rakt på poängen |
| ”sammantaget representerar detta” | stryk, avsluta med fakta |
| ”navigera förändringen” | ”hantera förändringen”, ”hitta rätt” |
| ”proaktivt” | ”tidigt”, ”i förväg”, eller stryk |
| ”holistiskt” | ”i sin helhet”, ”samlat” |
| ”ta ägarskap över” | ”ansvara för”, ”driva frågan” |
| ”implementeringen av” | ”att införa”, ”när vi inför” |
| ”å ena sidan... å andra sidan” | skribentens slutsats, eller en fråga till skribenten |
| ”möjligheterna är stora” | vilka möjligheter? för vem? |
| ”avgörande” / ”banbrytande” | stryk, eller sätt siffran om den finns |
| ”vittnar om” | ”visar”, ”tyder på” |
| ”utgör” / ”representerar” | ”är”, ”innebär” (utgör får stå om andelar) |
| ”fungerar som” | ”är”, ”kopplar ihop” |
| ”möjliggör” | ”gör det möjligt”, ”låter oss” |
| ”det är viktigt att notera” | skriv påståendet direkt |
| ”avslutningsvis” | stryk, avsluta med substans |
| ”Vilken bra fråga!” | stryk helt |
| ”Hoppas det hjälper!” | stryk helt |
| ”i syfte att uppnå” | ”för att” |
| ”på grund av det faktum att” | ”eftersom” |
| ”i dagsläget” / ”i nuläget” | ”nu” |
| ”gällande X” (som preposition) | ”om X” |
| ”baserat på tillgänglig info” | stryk, skriv vad du vet |
| ”det kan möjligen argumenteras” | skribentens ställning, eller osäkerheten med sitt skäl |
| ”tack vare” (om något negativt) | ”på grund av” |
| ”förväntas” (om en prognos) | ”väntas” |
| ”teknologi” | ”teknik” |
| ”eventuellt” (för eventually) | ”till slut”, ”så småningom” |
| ”sömlös” | ”automatisk”, ”utan avbrott” |
| ”robust” | ”stabil”, ”tålig”, ”beprövad” |
| ”skräddarsydd” | ”anpassad för X” |
| ”spjutspets” / ”i framkant” | beskriv den faktiska tekniken eller lösningen |
| ”brinner för” (rekrytering) | ”är intresserad av”, ”har erfarenhet av” |
| ”spindeln i nätet” | beskriv de faktiska samordningsuppgifterna |
| ”många bollar i luften” | ”prioriterar när flera uppgifter krockar” |
| ”låt oss djupdyka” | stryk och gå direkt på analysen |
| ”inte bara X, utan även Y” | formulera ett rakt påstående |
| tankstreck mitt i meningar (`—`) | använd `–` sparsamt, annars punkt eller kommatecken |
| dekorativa emojis (🚀, 💡, ✅) | stryk |

</details>

---

## Faktaskydd och självkontroll

Det som skiljer standarden från en vanlig ordlista ligger i [`references/`](./references/):

* **[`sjalvkontroll.md`](./references/sjalvkontroll.md):** 52 punkter som agenten kör före varje svar, med godkänt eller ej godkänt. Vid ej godkänt rättas texten och listan körs om. Användaren ser aldrig listan, bara det som läget lämnar tillbaka.
* **[`svenska-ord.md`](./references/svenska-ord.md)** och **[`typografi.md`](./references/typografi.md):** utbyteslistor för AI-ord, kanslisvenska, stel affärssvenska, ord-för-ord-svenska, falska vänner och ord som ändrar betydelsen, samt de svenska formreglerna för tecken, kommatering, siffror och rubriker.
* **[`frekvenstest.md`](./references/frekvenstest.md):** ett valfritt test mot Språkbankens korpusar, för agenter med webbåtkomst.

---

## Testa med färdiga benchmarks

Vill du utvärdera hur bra en modell eller agent presterar tillsammans med standarden? Kör testtexterna i [`tests/benchmark_prompts.md`](./tests/benchmark_prompts.md). Där finns sju test: fyra texter fulla av AI-mönster, ett om sakuppgifter, ett om ord som ändrar betydelsen och ett om eget skrivande.

---

## Medvetna val och begränsningar

* **`–` får användas sparsamt.** Språkrådet tillåter tankstreck vid paus och inskjutning, och standarden fäller inte korrekt svenska. `—` är alltid fel.
* **Tal byter aldrig form.** 3 blir inte tre och tre blir inte 3, även där skrivreglerna hade valt annorlunda. Ett omskrivet tal räknas som en ändrad sakuppgift.
* **Luckor fylls aldrig i.** Det som saknas står under **Kvar för dig** i stället för att agenten gissar.
* **Inte purist.** Agenda, team, design och fokusera på är etablerad affärssvenska och får stå.
* **% och kr som standard**, med mellanslag före. Utskrivet i talmanus.
* **Begränsningar:** Standarden är byggd för professionell sakprosa. Juridisk, akademisk och vetenskaplig svenska har egna konventioner. Ordvalen i AI-text ändras med nya modeller, så listorna behöver ses över, och korpusarna i frekvenstestet är mest från 2010-talet.

Källorna för formreglerna och ordvalen står sist i [`references/monster.md`](./references/monster.md): Språkrådet, TT-språket, Regeringskansliets Svarta listan och Språkbanken.

---

## Licens och versionshistorik

- **Licens:** [MIT License](./LICENSE)
- **Ändringslogg:** Fullständig historik finns i [`CHANGELOG.md`](./CHANGELOG.md).
- **Ursprung:** Projektet började som en fork av [nordefors-max/claude-humanizer-svenska](https://github.com/nordefors-max/claude-humanizer-svenska). Version 4.1.0 tar in regler från dess version 3.1.0, omskrivna och kontrollerade mot TT-språket och Språkrådet.
