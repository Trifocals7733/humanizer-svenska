# Användning med Claude (Claude Code och Claude-appen)

`humanizer-svenska` fungerar både i **Claude Code** och i Claude-appen.

---

## 1. Claude Code

### Installation som skill
Klona repot till din skills-katalog:

```bash
git clone https://github.com/Trifocals7733/humanizer-svenska.git ~/.claude/skills/humanizer-svenska
```

Eller installera via skills.sh:

```bash
npx skills add Trifocals7733/humanizer-svenska
```

Har du redan repot lokalt kan du länka det i stället, så att skillen följer med när du drar ner nya versioner:

```bash
ln -s "$(pwd)" ~/.claude/skills/humanizer-svenska
```

En kopia som installerats med `npx skills add` uppdateras inte av sig själv. Kör kommandot igen efter en ny version.

### Användning i Claude Code
När skillen är installerad kan du anropa den direkt i chatten:

```bash
# Standardläge:
/humanizer-svenska "Klistra in din text här"

# Med angiven texttyp:
/humanizer-svenska rapport "Klistra in din text här"

# Snabbtvätt utan förklaringar:
/humanizer-svenska --snabb "Klistra in din text här"

# Redaktörsgranskning:
/humanizer-svenska --granska "Klistra in din text här"
```

Du kan även be Claude direkt:
> *”Läs SKILL.md och humanisera rapporten i docs/sammanfattning.md”*

När Claude själv skriver svensk text, ett mejl, ett inlägg eller dokumentation, gäller läget Eget skrivande: bara texten, med hakparentes där en uppgift saknas.

Skillen är byggd för progressiv laddning. `SKILL.md` är ingången och beskriver arbetsgången. Claude läser `references/` bara när den behöver dem: `monster.md` för att förklara ett mönster, `svenska-ord.md` för ett konkret utbyte eller en falsk vän, `typografi.md` för formregler, `sjalvkontroll.md` före varje svar och `frekvenstest.md` när en fras är tveksam. Låt katalogerna `references/`, `genres/` och `examples/` ligga kvar bredvid `SKILL.md`, annars tappar skillen halva sitt innehåll.

---

## 2. Claude-appen

**Som skill:** packa hela mappen som en zip-fil, med `SKILL.md`, `references/`, `genres/` och `examples/`, och ladda upp den bland skills i inställningarna. Laddar du bara upp `SKILL.md` försvinner referensfilerna.

**Som projektinstruktion:**
1. Skapa eller öppna ett projekt.
2. Klistra in den fulla versionen från `platforms/chatgpt/system-prompt.md` i projektets instruktioner.
3. Ladda gärna upp `SKILL.md` och `references/` som projektfiler.

Då följer Claude reglerna för svensk text i alla chattar i projektet.
