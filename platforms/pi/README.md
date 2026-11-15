# Användning med Pi (terminalagent för kod och text)

**Pi** (av Mario Zechner / `badlogic`) är en minimalistisk och snabb terminalagent för kodning och textbearbetning. Pi har lite inbyggd prompt och förlitar sig på enkla verktyg (`read`, `write`, `edit`, `bash`) och direkta markdown-instruktioner.

`humanizer-svenska` fungerar med Pi utan anpassning, eftersom projektet består av ren Markdown utan krav på särskilda verktyg.

---

## Hur du använder humanizern i Pi

### Metod 1: Direkt i terminalsessionen (enklast)
Be Pi läsa `SKILL.md` när du vill bearbeta en text eller fil:

```bash
# I din Pi-prompt:
pi "Läs SKILL.md och humanisera texten i draft.md med --snabb"
```

Eller under en pågående interaktiv session i Pi:
> *”Läs SKILL.md och granska den här texten med --granska: [klistra in text]”*

---

### Metod 2: Integrera i `AGENTS.md` för hela projektet
Om du har ett repo där Pi ofta skriver eller redigerar svensk text, till exempel dokumentation, blogginlägg, release notes eller webbcopy, kan du lägga till en referens i din `AGENTS.md` i projektroten:

```markdown
<!-- I din AGENTS.md -->
## Svensk språkvård och humanisering
När du skriver eller redigerar svensk text, följ riktlinjerna och mönsterkatalogen i `SKILL.md`:
- Rör aldrig sakuppgifter. Hitta aldrig på en siffra, ett datum, en källa eller en ståndpunkt för att göra texten konkret.
- Undvik de 33 AI-mönstren (inga landskapsinledningar, ingen signifikansuppblåsning, inget `—`, ingen ord-för-ord-svenska).
- Rätta falska vänner och värdeladdade ord (tack vare, förväntas, eventuellt) bara när betydelsen är klar. Annars: fråga.
- Variera meningslängden kraftigt, utan mall.
- Variera fundamentet enligt svensk syntax (börja inte varje mening med subjekt och verb).
- Formreglerna i `references/typografi.md` är fel, inte stilfrågor.
- Kör `references/sjalvkontroll.md` före du svarar.
- För specifika texttyper, se katalogen `genres/`.
```

---

### Metod 3: Snabba kommandon med flaggor i Pi
Med lägesflaggorna styr du vad Pi lämnar tillbaka:
- **`--snabb`**: Pi returnerar bara den färdiga texten, praktiskt när du ber Pi uppdatera en befintlig fil med `edit`.
- **`--granska`**: Pi pekar ut vilka AI-mönster texten innehåller utan att skriva om den.
- **Utan flagga**: texten, följd av **Vad jag ändrade** och **Kvar för dig**.
