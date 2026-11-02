# Användning med Pi Agents (Terminal AI Coding Agent)

**Pi** (av Mario Zechner / `badlogic`) är en minimalistisk, snabb och icke-åsiktsstyrd terminalagent för kodning och textbearbetning. Till skillnad från mer rigida verktyg har Pi minimal prompt-overhead och förlitar sig på rena verktyg (`read`, `write`, `edit`, `bash`) och direkta markdown-instruktioner.

`humanizer-svenska` fungerar helt sömlöst med Pi eftersom projektet är uppbyggt av 100 % ren, portabel Markdown utan proprietära verktygskrav.

---

## Hur du använder humanizern i Pi

### Metod 1: Direkt i terminalsessionen (Enklast)
Be bara Pi läsa `SKILL.md` när du vill bearbeta en text eller fil:

```bash
# I din Pi-prompt:
pi "Läs SKILL.md och humanisera texten i draft.md. Kör enligt läge: snabb."
```

Eller under en pågående interaktiv session i Pi:
> *"Läs SKILL.md och granska den här texten enligt Läge 3 (Granskning): [klistra in text]"*

---

### Metod 2: Integrera i `AGENTS.md` för hela projektet
Om du har ett repo där Pi ofta skriver eller redigerar svensk text (t.ex. dokumentation, blogginlägg, release notes eller webbcopy), kan du lägga till en referens i din `AGENTS.md` i projektroten:

```markdown
<!-- I din AGENTS.md -->
## Svensk språkvård & humanisering
När du skriver eller redigerar svensk text, följ riktlinjerna och mönsterkatalogen i `SKILL.md`:
- Rör aldrig sakuppgifter. Hitta aldrig på en siffra, ett datum eller en källa för att göra texten konkret.
- Undvik de 33 AI-mönstren (inga landskapsinledningar, ingen signifikansuppblåsning, inga em-dashes, ingen ord-för-ord-svenska).
- Variera meningslängder radikalt (hög burstiness).
- Variera fundamentet enligt svensk syntax (börja inte varje mening med subjekt + verb).
- Formreglerna i `references/typografi.md` är fel, inte stilfrågor.
- Kör `references/sjalvkontroll.md` före du svarar.
- För specifika texttyper, se fördjupning i katalogen `genres/`.
```

---

### Metod 3: Snabba kommandon med flaggor i Pi
Tack vare lägesväljaren kan du styra utdatan exakt:
- **`--snabb`**: Pi returnerar endast den färdiga texten direkt, perfekt när du ber Pi uppdatera en befintlig fil med `edit`.
- **`--granska`**: Pi pekar ut vilka AI-fällor texten innehåller utan att skriva om den.
