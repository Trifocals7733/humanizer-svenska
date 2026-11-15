# Frekvenstest: är frasen etablerad svenska?

Läs den här filen när du tvekar om en fras är naturlig svenska eller en översättning, och du har webbåtkomst. Testet jämför hur ofta frasen och ett svenskt alternativ förekommer i Språkbankens korpusar. Språkrådet rekommenderar själv Korp för egna undersökningar av språkbruket (Snabba skrivregler, avsnitt 8.3.2).

Testet är valfritt. Saknar du webbåtkomst, hoppa över det och använd listorna i `svenska-ord.md`.

## När testet är värt besväret

- Vid verklig tveksamhet, oftast om mönster 23 och 24: en fras som kan vara ord-för-ord-svenska, eller ett lånord som kan vara etablerat.
- Inte på varje text, och inte på ord som redan står i listorna.
- Inte för att avgöra betydelse. Testet mäter form. Teknologi är ett vanligt ord, men det betyder läran om teknik, och det säger frekvensen ingenting om.

## Så gör du

Fråga Korps API, med samma korpusar för frasen och för alternativet:

```
https://ws.spraakbanken.gu.se/ws/korp/v8/count?cqp=[word="ORD1"][word="ORD2"]&corpus=KUBORD2-DN-2024,GP2013,WEBBNYHETER2010,BLOGGMIX2015,FAMILJELIV-ALLMANNA-FAMILJELIV&group_by=word
```

- Ett ord per hakparentes. Böjningsformer skiljs med lodstreck: `[word="adressera|adresserar|adresserade|adresserat"]`.
- Ett valfritt mellanord skrivs `[]{0,2}`. Mellanord ger fler falska träffar, så läs ett urval i Korps webbgränssnitt innan du litar på siffran.
- URL-koda frågan om ditt verktyg inte gör det åt dig.
- Totalen står i svaret under `combined`, `sums`, `absolute`.
- De tre första korpusarna är nyhetstext. Fråga dem för sig när du vill veta hur frasen fungerar i formell text.

## Så läser du siffrorna

Jämför frasen med alternativet. Det här är en tumregel, inte en gräns:

| Frasen har | Gör så här |
|---|---|
| under en tiondel av alternativets träffar | byt |
| mellan en tiondel och hälften | båda fungerar, välj efter register |
| ungefär lika många eller fler | frasen är etablerad, låt den stå om inte registret säger annat |

## Uppmätta exempel

Mätt i november 2026 med frågorna nedan.

| Fras | Träffar | Alternativ | Träffar | Slutsats |
|---|---|---|---|---|
| adressera problemet, frågan | 1 | ta itu med | 799 | byt |
| byta ut X med | 52 | byta ut X mot | 674 | byt |
| på daglig basis | 0 | varje dag | 13 811 | byt |
| spendera … tid, alla fem korpusarna | 739 | tillbringa … tid | 463 | etablerad i ledig text |
| spendera … tid, bara nyhetstext | 32 | tillbringa … tid | 192 | båda fungerar, välj efter register |

De tre första är tydliga byten. De två sista visar att testet kan gå frasens väg, och att registret avgör: spendera tid är vanligt i bloggar och forum men ovanligare i nyhetstext. I en offert eller rapport är lägga tid på eller ägna tid åt det säkrare valet.

Frågorna:

- `[word="adressera|adresserar|adresserade|adresserat"][word="problemet|frågan"]` mot `[word="ta|tar|tog|tagit"][word="itu"][word="med"]`
- `[word="byta|byter|bytte|bytt"][word="ut"][]{0,3}[word="med"]` mot samma fråga med `[word="mot"]`
- `[word="på"][word="daglig"][word="basis"]` mot `[word="varje"][word="dag"]`
- `[word="spendera|spenderar|spenderade|spenderat"][]{0,2}[word="tid|tiden"]` mot `[word="tillbringa|tillbringar|tillbringade|tillbringat"][]{0,2}[word="tid|tiden"]`

## Begränsningar

- De flesta korpusarna är från 2010-talet. Ny affärsjargong syns dåligt.
- Bloggar och forum drar åt det informella. En fras som är vanlig där kan vara fel i en offert.
- Frågor med mellanord ger falska träffar. Läs ett urval innan du drar slutsatser.
- Testet visar vad som är vanligt, inte vad som är rätt eller vad som passar texten.
- Redovisa siffrorna bara om användaren ber om dem.
