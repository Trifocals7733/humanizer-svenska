# AGENTS.md — Instruktioner för AI-kodningsagenter

Detta dokument tillhandahåller instruktioner och riktlinjer för alla AI-agenter (t.ex. **Pi Agents**, Claude Code, Cursor, Windsurf, GitHub Copilot, Cline, Aider) som arbetar i eller använder detta arkiv.

---

## 1. Repositoriets syfte och arkitektur

`humanizer-svenska` är en öppen, universell standard för att ta bort AI-genererade språkmönster ur professionell svensk text. Repositoriet är uppbyggt av **100 % ren, portabel Markdown** utan externa beroenden eller byggsteg.

### Filstruktur:
- **`SKILL.md`:** Den centrala agent-skillen och regelboken (följer öppen Agent Skill-standard).
- **`genres/`:** Register- och nischguider för olika texttyper (affärstext, rapporter, artiklar, sociala medier, klarspråk, e-handel, rekrytering, kunddialog).
- **`examples/`:** Fullständiga före/efter-exempel med självgranskning och analys.
- **`platforms/`:** Plattformsspecifika konfigurationer och instruktioner (`pi/`, `cursor/`, `chatgpt/`, `copilot/`, `claude/`).
- **`tests/benchmark_prompts.md`:** Testsvit med koncentrerade AI-fällor för att utvärdera språkmodeller.
- **`README.md` & `CHANGELOG.md`:** Dokumentation och versionshistorik.

---

## 2. Riktlinjer för agenter som ändrar i detta arkiv

När du som agent utför ändringar i detta repository ska du följa dessa strikta regler:

1. **Bevara 100 % ren Markdown:** Skapa inga Node/Python-byggskript eller externa beroenden om inte användaren uttryckligen ber om det. All logik ska vara direkt tillgänglig i ren Markdown.
2. **Följ alltid standardens egna skrivregler:** När du genererar eller uppdaterar svensk text och dokumentation i detta arkiv får du **aldrig** falla i de AI-fällor som projektet bekämpar.
3. **Dokumentationsspråk:** Huvuddokumentationen ska förbli på svenska (eftersom verktyget är för svenska skribenter), med undantag för den korta sammanfattningen i toppen av `README.md`.

---

## 3. Hur en agent ska tillämpa Humanizer Svenska på en text

När en användare ber dig humanisera en svensk text eller fil:

### A. Identifiera arbetsläge
- **Om flaggan `--snabb` anges:** Leverera **enbart** den tvättade sluttexten direkt i filen eller svaret. Inga förklarande texter eller punktlistor.
- **Om flaggan `--granska` anges:** Skriv **inte** om texten. Analysera texten som en redaktör: lista identifierade AI-mönster med citat, förklara varför de signalerar AI och sätt ett betyg (1–10).
- **Standardläge:** 
  1. Utkast till omskrivning.
  2. Kort anti-AI-självgranskning (*"Vad avslöjar att texten fortfarande är AI-genererad?"* och *"Vad saknar texten för att låta skriven av en verklig person med en ståndpunkt?"*).
  3. Slutlig mänsklig version.

### B. Anti-AI Engine (Tvingande regler för textbearbetning)
För att texten ska passera både mänsklig granskning och AI-detektorer:
1. **Radikal Burstiness (Meningslängd):** Variera meningslängden kraftigt. Blanda satser på 3–6 ord med längre resonerande meningar på 25–35 ord. Undvik jämntjocka meningar på 15–20 ord.
2. **Svensk V2-fundamentvariation:** Börja inte varje mening med Subjekt + Verb (*"Detta visar...", "Företaget gör..."*). Placera tidsuttryck, bisatser, villkor eller objekt först i minst 40 % av meningarna.
3. **Konkretion (Perplexity):** Ersätt svepande ord med specifika siffror, namn, tidsramar och mätpunkter.
4. **Typografisk sanering:** Använd **aldrig** tankstreck (`—` eller ` – `) mitt i meningar. Ersätt med punkt, komma eller parentes. Rensa dekorativa emojis (🚀, 💡, ✅) och mekaniska punktlistor.
5. **Nordisk röst:** Håll en direkt, saklig och lågmäld ton. Våga välja sida och dra slutsatser utan slätstrukna brasklappar.

---

## 4. De 22 förbjudna AI-mönstren (Snabbkoll)

1. **Signifikansuppblåsning:** "avgörande", "banbrytande", "paradigmskifte", "vittnar om".
2. **Landskapsinledningar:** "I en alltmer digitaliserad värld...", "I en föränderlig omvärld...".
3. **Participfraser som falsk analys:** "belyser vikten av", "understryker behovet av".
4. **Vaga auktoriteter:** "experter menar", "forskning visar", "branschkällor pekar på".
5. **Passiv formalitet:** "det kan konstateras att", "det bör påpekas att".
6. **Nominaliseringsstaplar:** "implementeringen av", "genomförandet av", "säkerställandet av".
7. **Anglifieringsimporter:** "ta ägarskap över", "navigera förändringen", "leverera värde".
8. **Strukturella tretal & falsk balans:** "snabbt, enkelt och effektivt", "å ena sidan... å andra sidan".
9. **Negativ parallellism:** "Det handlar inte om X, det handlar om Y".
10. **Sociala medier-floskler:** "Jag delar en reflektion...", generiska hashtag-staplar.
11. **Sycofancy:** "Vilken bra fråga!", "Hoppas detta hjälper dig!".
12. **Utfyllnadsfraser:** "i syfte att uppnå", "på grund av det faktum att", "i nuläget".
13. **Överdriven hedging:** "det kan möjligen argumenteras att detta eventuellt skulle kunna...".
14. **Kunskapsavgränsningar:** "Baserat på tillgänglig info...", "Inom ramen för mina kunskaper...".
15. **Kopulaundvikande:** "utgör", "representerar", "fungerar som" istället för "är".
16. **Bullet- & emojifeber:** Emojis och listor där löpande text är naturligare.
17. **Tankstrecksfrossa (Em-dashes):** Meningar avskurna med `—`.
18. **"Inte bara X, utan även Y"-syndromet:** Retorisk klyscha för att låtsas vara djup.
19. **Moderna modord:** "sömlös", "robust", "skräddarsydd", "spjutspets", "i framkant".
20. **"Låt oss djupdyka":** Metakommentarer där AI agerar föreläsare.
21. **Syntetisk tröst:** "Vi förstår att detta kan kännas överväldigande...".
22. **Falsk sammanfattningsfeber:** "Slutsats:" eller "Sammanfattningsvis:" i texter under 300 ord.
