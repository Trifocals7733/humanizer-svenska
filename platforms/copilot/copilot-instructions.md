# GitHub Copilot: svensk språkvård

Lägg till avsnittet nedan i `.github/copilot-instructions.md` i det repo där Copilot skriver svensk text. Har repot `SKILL.md` från humanizer-svenska, räcker det att peka på den i stället.

```markdown
## Svensk text: humanizer-svenska

När du skriver, redigerar eller granskar svensk text i det här repot:

1. **Rör aldrig sakuppgifter.** Belopp, datum, namn, siffror och källor står som skribenten skrev dem. Hitta aldrig på en siffra, en källa eller en ståndpunkt för att göra texten konkret. Saknas uppgiften när du redigerar: lämna meningen allmän. Saknas den när du skriver nytt: skriv en hakparentes som `[datum]`.
2. **Bevara rösten.** Lämna starka meningar i fred och gör minsta effektiva ändring. En text som var i gott skick ska inte skrivas om, och den ska inte bli vassare eller mer tvärsäker än skribenten.
3. **Ta bort AI-mönster.** Inga landskapsinledningar ("i en alltmer digitaliserad värld"), ingen uppblåst betydelse ("avgörande", "banbrytande"), ingen falsk analys ("belyser vikten av"), inga vaga auktoriteter ("experter menar"), inget kopulaundvikande ("utgör", "representerar"), inget "inte bara X, utan även Y", inga modeord ("sömlös", "robust", "i framkant"). Vanlig s-passiv får stå.
4. **Variera rytmen.** Blanda korta satser med längre resonemang. Börja inte varje mening med subjekt och verb: svenskan har V2-ordföljd och fritt fundament.
5. **Svensk form.** `–` är tankstreck, `—` är alltid fel. Citattecken `”så här”`. Decimalkomma och mellanslag i tusental: `12,5 %` och `1 450`. Inget komma före och i uppräkningar. Ingen title case i rubriker, ingen punkt efter rubrik. Mejl, inte mail.
6. **Ord-för-ord-svenska.** Läs varje mening högt. Går den att översätta rakt tillbaka till engelska utan att något går förlorat, kom den därifrån.
7. **Ord som byter betydelse.** Tack vare bara om något positivt, väntas om en prognos, teknik i stället för teknologi. Falska vänner som eventuellt för eventually och biljon för billion rättas bara när betydelsen är klar. Annars frågar du.
```

Full katalog med 33 mönster, ordlistor och självkontroll finns i `SKILL.md` och `references/`.
