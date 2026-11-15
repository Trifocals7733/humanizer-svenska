# AGENTS.md: instruktioner för AI-kodningsagenter

Detta dokument tillhandahåller instruktioner och riktlinjer för alla AI-agenter (t.ex. **Pi Agents**, Claude Code, Cursor, Windsurf, GitHub Copilot, Cline, Aider) som arbetar i eller använder detta arkiv.

---

## 1. Repositoriets syfte och arkitektur

`humanizer-svenska` är en öppen, universell standard för att ta bort AI-genererade språkmönster ur professionell svensk text. Repositoriet är uppbyggt av **100 % ren, portabel Markdown** utan externa beroenden eller byggsteg.

### Filstruktur
- **`SKILL.md`:** Den centrala agent-skillen och regelboken (följer öppen Agent Skill-standard). Innehåller arbetsgången, utdatakontraktet för fyra lägen, faktaskyddet och de 33 mönstren i kortform.
- **`references/`:** Fördjupningen som agenten läser vid behov. `monster.md` (33 mönster med kännetecken, fix och källor), `svenska-ord.md` (ord- och frasbyten, falska vänner och ord som ändrar betydelsen), `typografi.md` (svensk form), `sjalvkontroll.md` (godkänt/ej godkänt-lista som körs före svar), `frekvenstest.md` (valfri kontroll mot Språkbankens korpusar när en fras är tveksam).
- **`genres/`:** Register- och nischguider för olika texttyper (affärstext, presentationer, rapporter, artiklar, sociala medier, klarspråk, e-handel, rekrytering, kunddialog).
- **`examples/`:** Sex fullständiga exempel i det format agenten ska leverera: råtext, identifierade mönster, och svaret med **Vad jag ändrade** och **Kvar för dig**. Inget exempel fyller i en sakuppgift eller en ståndpunkt som inte stod i råtexten. Läs `examples/README.md` först.
- **`platforms/`:** Plattformsspecifika konfigurationer och instruktioner (`pi/`, `cursor/`, `chatgpt/`, `copilot/`, `claude/`). De sammanfattar reglerna och pekar på `SKILL.md` i stället för att duplicera dem.
- **`tests/benchmark_prompts.md`:** Sju test för att utvärdera språkmodeller: fyra texter fulla av AI-fällor, ett om sakuppgifter, ett om ord som ändrar betydelsen och ett om eget skrivande.
- **`README.md` och `CHANGELOG.md`:** Dokumentation och versionshistorik.

---

## 2. Riktlinjer för agenter som ändrar i detta arkiv

När du som agent utför ändringar i detta repository ska du följa dessa strikta regler:

1. **Bevara 100 % ren Markdown:** Skapa inga Node/Python-byggskript eller externa beroenden om inte användaren uttryckligen ber om det. All logik ska vara direkt tillgänglig i ren Markdown.
2. **Följ alltid standardens egna skrivregler:** När du genererar eller uppdaterar svensk text och dokumentation i detta arkiv får du **aldrig** falla i de AI-fällor som projektet bekämpar. Det gäller även README, CHANGELOG och dina egna svar: inga dekorativa emojis, inga raka citattecken i löptext, ingen title case i rubriker, och `—` bara när du citerar en text som innehåller det.
3. **Hitta aldrig på sakuppgifter i exempel eller dokumentation.** Ett exempel som ser trovärdigt ut men innehåller ett påhittat kundnamn, telefonnummer eller en påhittad procentsats lär ut precis det standarden förbjuder. Samma sak med en påhittad ståndpunkt i ett exempelsvar.
4. **Dokumentationsspråk:** Huvuddokumentationen ska förbli på svenska (eftersom verktyget är för svenska skribenter), med undantag för den korta sammanfattningen i toppen av `README.md`.
5. **Mönstrens namn står i `references/monster.md`.** Rubrikerna där är namnen, och tabellen i `SKILL.md`, README, listan nedan och exemplen använder samma. Byter du namn på ett mönster, byt det överallt.

---

## 3. Hur en agent ska tillämpa Humanizer Svenska på en text

När en användare ber dig humanisera en svensk text eller fil, eller när du själv skriver svensk text:

### A. Identifiera arbetsläge
- **Om flaggan `--snabb` anges:** Leverera **enbart** den tvättade sluttexten direkt i filen eller svaret. Inga förklarande texter eller punktlistor. Faktaskyddet gäller ändå.
- **Om flaggan `--granska` anges:** Skriv **inte** om texten. Analysera texten som en redaktör: lista identifierade AI-mönster med citat, förklara varför de signalerar AI, föreslå fix, och sätt ett AI-avtryck 1–10 som är ett redaktörsomdöme, inte en mätning.
- **Standardläge:** 
  1. Hela den omskrivna texten.
  2. **Vad jag ändrade:** en rad per ändring som betyder något, med ordagranna citat ur utkastet.
  3. **Kvar för dig:** allt som bara skribenten kan fylla i (saknad siffra, källa, skäl att skriva just nu).
  4. Ingen inledande rapport om vad du läst eller tänker göra.
- **Eget skrivande** (du skriver själv svensk text, utan utkast): leverera bara texten och kör självkontrollen tyst. Där en uppgift saknas skriver du en hakparentes som `[datum]` i stället för att hitta på den.

### B. Faktaskyddet (gäller före allt annat)
1. **Rör aldrig sakuppgifter.** Belopp, datum, namn, kontonummer, källor och åtaganden står exakt som skribenten skrev dem. Ett tal som bytt form (3 → tre) räknas som ändrad sakuppgift.
2. **Hitta aldrig på innehåll.** Konkretion får bara bygga på uppgifter som finns i utkastet eller konversationen. En påhittad siffra är värre än en vag mening, för den går att citera.
3. **Lägg inte till led som utkastet saknar:** tidsordning ("efter det", "först, sedan"), orsak, villkor eller löften.
4. **Låt inte luckor passera tyst.** I standardläget hamnar det som inte går att göra konkret utan påhittade uppgifter under **Kvar för dig**, och i eget skrivande som en hakparentes. I snabbläget står meningen kvar allmän.
5. **Hitta aldrig på en ståndpunkt.** Skriv fram skribentens, och gör inte texten vassare eller mer tvärsäker än utkastet. Saknas en ståndpunkt hamnar frågan under **Kvar för dig**.
6. **Ord som bär betydelse rättas bara när utkastet visar vad som menas.** Tack vare om något negativt och förväntas om en prognos går att rätta direkt. Ska mot bör, procent mot procentenheter och biljon mot miljard ändrar du inte: frågan hamnar under **Kvar för dig**.

### C. Anti-AI-motorn (tvingande regler för textbearbetning)
För att texten ska läsa som skriven av en människa och tåla en van läsare:
1. **Radikal burstiness (meningslängd):** Variera meningslängden kraftigt. Blanda satser på några ord med längre resonerande meningar. Undvik jämntjocka meningar på 15–20 ord, men gör inte "kort, lång, kort" till en ny metronom.
2. **Svensk V2-fundamentvariation:** Börja inte varje mening med subjekt och verb (*"Detta visar...", "Företaget gör..."*). Placera tidsuttryck, bisatser, villkor eller objekt först när det passar. Ingen fast kvot.
3. **Konkretion (perplexity):** Ersätt svepande ord med specifika siffror, namn, tidsramar och mätpunkter som redan står i underlaget. Uppgifter du inte har får du aldrig hitta på, se faktaskyddet ovan.
4. **Typografisk sanering:** `—` hör inte hemma i svensk text. Använd `–` sparsamt: utan mellanslag i intervall (9–18), med mellanslag runt inskjutningar. Ersätt i övrigt med punkt, komma eller parentes. Inget komma före och i uppräkningar. Rensa dekorativa emojis (🚀, 💡, ✅) och mekaniska punktlistor.
5. **Skydda rösten:** Gör minsta effektiva ändring. Lämna starka meningar i fred. En text som var i gott skick ska inte komma tillbaka halverad, och en text där varje mening är putsad är jämn, vilket är den starkaste markören av alla.
6. **Nordisk röst:** Håll en direkt, saklig och lågmäld ton. Skriv fram skribentens ståndpunkt och slutsatser utan slätstrukna brasklappar. Finns ingen ståndpunkt i utkastet, uppfinn ingen.

---

## 4. De 33 AI-mönstren (snabbkoll)

Fullständig katalog med kännetecken, förklaring, fix och källor: `references/monster.md`. Mönstren är kännetecken att väga, inte förbud att verkställa mekaniskt.

1. **Signifikansuppblåsning:** "avgörande", "banbrytande", "paradigmskifte", "vittnar om".
2. **Landskaps- och trenduppramning:** "I en alltmer digitaliserad värld...", "I en föränderlig omvärld...".
3. **Participfraser som falsk analys:** "belyser vikten av", "understryker behovet av".
4. **Vaga auktoriteter:** "experter menar", "forskning visar", "branschkällor pekar på".
5. **Passiv formalitet:** "det kan konstateras att", "det bör påpekas att". Vanlig s-passiv får stå.
6. **Nominaliseringsöverdrift:** "implementeringen av", "genomförandet av", "säkerställandet av".
7. **Anglifieringsimporter:** "ta ägarskap över", "navigera förändringen", "leverera värde".
8. **Tretalsregeln och falsk balans:** "snabbt, enkelt och effektivt", "å ena sidan... å andra sidan".
9. **Negativ parallellism:** "Det handlar inte om X, det handlar om Y".
10. **Sociala medier-fällor:** "Jag delar en reflektion...", generiska hashtag-staplar.
11. **Fjäsk:** "Vilken bra fråga!", "Hoppas detta hjälper dig!".
12. **Utfyllnadsfraser:** "i syfte att uppnå", "på grund av det faktum att", "i nuläget".
13. **Överdriven gardering:** "det kan möjligen argumenteras att detta eventuellt skulle kunna...".
14. **Kunskapsavgränsningar:** "Baserat på tillgänglig info...", "Inom ramen för mina kunskaper...".
15. **Kopulaundvikande:** "utgör", "representerar", "fungerar som" i stället för "är". Utgör får stå om andelar.
16. **Punktliste- och emojifeber:** Emojis och listor där löpande text är naturligare.
17. **Tankstrecksfrossa:** Meningar avskurna med `—`.
18. **Inte bara X, utan även Y:** Retorisk klyscha för att låtsas vara djup.
19. **Modeord och säljfloskler:** "sömlös", "robust", "skräddarsydd", "spjutspets", "i framkant".
20. **Låt oss djupdyka:** Metakommentarer där AI agerar föreläsare.
21. **Syntetisk tröst:** "Vi förstår att detta kan kännas överväldigande...".
22. **Falsk sammanfattningsfeber:** "Slutsats:" eller "Sammanfattningsvis:" i texter under 300 ord.
23. **Ord-för-ord-svenska:** "adressera ett problem", "spendera tid", "vara på samma sida", "följa upp på".
24. **Engelska lånord med svensk ändelse:** asken, caset, insighten, learnings, settingen.
25. **Kanslisvenska verb:** erhålla, nyttja, erfordras, tillställa, åligger, därest.
26. **Substantivsjuka:** "ta ett beslut", "göra en bedömning", "vidta åtgärder".
27. **Onödiga synonymbyten:** samma sak i tre olika ord i rad.
28. **Avsändarlös text:** "Många företag upplever att...", utan jag-form och utan förstahandsmaterial.
29. **Retorisk fråga som besvaras:** "Vad betyder det här? Det betyder att...".
30. **Kolon som spänningsknep:** nominalfras, kolon, poäng med liten bokstav.
31. **Den djupa slutraden:** en byggd aforism som sista mening.
32. **Jämna stycken och inläggets form:** alla stycken en till tre meningar, ensamt fragment som trumslag, kort slutrad.
33. **Engelsk typografi:** `“ord”` i stället för `”ord”`, `12.5%` i stället för `12,5 %`, title case i rubriker, punkt efter rubrik, komma före och i uppräkningar.
