# Användning med Anthropic Claude (Claude Code & Claude.ai)

`humanizer-svenska` är fullt bakåtkompatibel med Anthropic Claude och kan användas både i **Claude Code** (terminalverktyget) och på **Claude.ai** (webb/projekt).

---

## 1. Claude Code (Terminal)

### Installation som skill
Kopiera eller klona detta arkiv till din lokala skills-katalog:

```bash
# Klona direkt
git clone https://github.com/humanizer-svenska.git ~/.claude/skills/humanizer-svenska

# Eller skapa en symlänk om du redan har repot nedladdat:
ln -s "$(pwd)" ~/.claude/skills/humanizer-svenska
```

### Användning i Claude Code
När skillen är installerad kan du anropa den direkt i chatten:

```bash
# Standardläge:
/humanizer-svenska "Klistra in din text här"

# Med angiven texttyp:
/humanizer-svenska rapport "Klistra in din text här"

# Snabbtvätt utan reflektion:
/humanizer-svenska --snabb "Klistra in din text här"

# Redaktörsgranskning:
/humanizer-svenska --granska "Klistra in din text här"
```

Du kan även be Claude direkt:
> *"Läs SKILL.md och humanisera rapporten i docs/sammanfattning.md"*

Skillen är byggd för progressiv laddning. `SKILL.md` är ingången och beskriver arbetsgången. Claude läser `references/` bara när den behöver dem: `monster.md` för att namnge ett mönster, `svenska-ord.md` för ett konkret utbyte, `typografi.md` för formregler, `sjalvkontroll.md` före varje svar. Låt katalogen `references/` ligga kvar bredvid `SKILL.md`, annars tappar skillen halva sitt innehåll.

---

## 2. Claude.ai Projects (Webbgränssnitt)

1. Skapa eller öppna ett projekt i [Claude.ai](https://claude.ai).
2. Klicka på **Set Project Instructions**.
3. Klistra in innehållet från `platforms/chatgpt/system-prompt.md` i fältet för projektinstruktioner.
4. Ladda gärna upp `SKILL.md` som en projektresurs (*Project Knowledge*).
5. Nu humaniserar Claude all svensk text automatiskt i alla chattar inom det projektet!
