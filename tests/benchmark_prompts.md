# Testtexter och benchmarks för Humanizer Svenska

Testtexterna innehåller koncentrerade samlingar av typiska AI-fällor. Använd dem för att utvärdera hur väl olika modeller och agenter klarar att humanisera svensk text.

## Så mäter du

Kör varje text två gånger: en gång utan skillen och en gång med. Jämför paren, inte intrycket.

1. **Faktaskyddet.** Har modellen lagt till en siffra, ett datum, ett kundnamn, en källa eller en ståndpunkt som inte står i testtexten? Ett enda påhittat värde underkänner körningen, oavsett hur snyggt resten är skrivet.
2. **Rösten.** Går det att se att texten handlar om samma sak, med samma avsändare, eller har modellen bytt ut innehållet mot något mer allmänt?
3. **Mönstren.** Vilka av de 33 markörerna i [`../references/monster.md`](../references/monster.md) finns kvar? Räkna dem, namnge dem, skriv upp dem.
4. **Formen.** `—`, raka citattecken, `12.5%`, title case i rubriker, komma före och i uppräkningar. Dessa är binära och ska vara noll.
5. **Strukturen.** Läs bara styckelängderna och första ordet i varje stycke. Är texten byggd som ett inlägg?
6. **Leveransen.** Följer svaret utdatakontraktet i [`../SKILL.md`](../SKILL.md), eller börjar modellen med en rapport om vad den ska göra?

Självkontrollen i [`../references/sjalvkontroll.md`](../references/sjalvkontroll.md) är samma lista, avsedd för modellen själv. Den fungerar också som rättningsmall när du bedömer en körning.

---

## Test 1: B2B-affärskommunikation
**Mönster att fånga:** 1 Signifikansuppblåsning, 2 Landskaps- och trenduppramning, 3 Participfraser som falsk analys, 6 Nominaliseringsöverdrift, 7 Anglifieringsimporter, 11 Fjäsk, 12 Utfyllnadsfraser, 15 Kopulaundvikande, 20 Låt oss djupdyka, 22 Falsk sammanfattningsfeber.

```text
Hej Karin!

I dagens ständigt föränderliga affärsklimat är det avgörande att organisationer proaktivt navigerar de möjligheter och utmaningar som digitaliseringen medför. Vår mjukvarulösning utgör ett banbrytande verktyg som möjliggör en mer effektiv och hållbar process genom att automatisera repetitiva moment.

Det är viktigt att notera att implementeringen av detta arbetssätt bidrar till en ökad förståelse för kundernas behov, vilket i sin tur belyser vikten av att ta ägarskap över er digitala transformation. Sammantaget representerar detta en unik möjlighet att skapa mervärde och säkerställa långsiktig framgång.

Hoppas detta låter intressant! Vill du boka ett förutsättningslöst möte nästa vecka där vi kan djupdyka i era behov?
```

---

## Test 2: Klarspråk och myndighetstext
**Mönster att fånga:** 5 Passiv formalitet, 6 Nominaliseringsöverdrift, 12 Utfyllnadsfraser, 15 Kopulaundvikande, 25 Kanslisvenska verb, 28 Avsändarlös text.

```text
Med anledning av inkommen ansökan rörande beviljande av tillstånd kan det konstateras att erforderliga handlingar ej har tillhandahållits i fullständig omfattning. I syfte att handläggning av ärendet ska kunna genomföras erfordras att kompletterande underlag inkommer till förvaltningen senast inom trettio dagar. 

Det bör påpekas att ett tillhandahållande av fullständiga uppgifter utgör en förutsättning för prövning av ärendet. I händelse av att begärda kompletteringar ej inkommer i rätt tid kan ärendet komma att avvisas med stöd av gällande författning.
```

---

## Test 3: Rekrytering och platsannons
**Mönster att fånga:** 1 Signifikansuppblåsning, 2 Landskaps- och trenduppramning, 7 Anglifieringsimporter, 8 Tretalsregeln och falsk balans, 17 Tankstrecksfrossa, 18 Inte bara X, utan även Y, 19 Modeord och säljfloskler.

```text
Är du en driven stjärna som brinner för digitalisering och vill göra en skillnad på riktigt?

I en snabbfotad miljö söker vi nu en engagerad projektledare till vårt fantastiska team! Hos oss är du inte bara en anställd — du blir en del av vår familj. I rollen som spindeln i nätet kommer du att agera proaktivt och navigera komplexa utmaningar på ett holistiskt sätt.

Vi söker dig som:
- Har många bollar i luften och älskar högt tempo
- Är strukturerad, flexibel och lösningsorienterad
- Brinner för att leverera värde i världsklass

Bli en del av vår spännande resa och ansök redan idag!
```

---

## Test 4: Sociala medier och tankeledarskap

**Mönster att fånga:** 2 Landskaps- och trenduppramning, 9 Negativ parallellism, 10 Sociala medier-fällor, 16 Punktliste- och emojifeber, 17 Tankstrecksfrossa, 20 Låt oss djupdyka, 32 Jämna stycken och inläggets form.

```text
🚀 I en värld som snurrar allt snabbare är det inte längre en fråga om om, utan när! 💡

Det handlar inte om teknik — det handlar om människor. Under året har vi implementerat ett nytt arbetssätt som revolutionerat hur vi samarbetar.

Här är mina viktigaste insikter:
✅ **Innovation:** Våga testa nya vägar.
✅ **Kultur:** Skapa psykologisk trygghet.
✅ **Fokus:** Prioritera det som skapar mervärde.

Framtiden ser ljus ut för de aktörer som vågar ta steget! Vad tänker du om detta? Dela gärna dina reflektioner i kommentarerna! 👇

#Ledarskap #DigitalTransformation #Innovation #Framtid #Agilt
```

---

## Test 5: Sakuppgifter (faktaskyddet)

**Mönster att fånga:** Inga. Testet mäter motsatsen till test 1–4: att varje belopp, datum och namn överlever redigeringen orört, att ingen ny siffra tillkommer, och att en text som redan är i gott skick inte skrivs om. Test 1–4 innehåller inte en enda siffra att tappa.

```text
Vi bytte fakturasystem i mars. Det tog tre veckor och kostade 84 000 kronor, varav 12 000 gick till konsult. Under första månaden ökade antalet kreditfakturor från 14 till 19, vilket vi inte hade räknat med, och Anna Berg på ekonomiavdelningen fick lägga mycket tid på att förklara för kollegorna varför siffrorna såg ut som de gjorde.
```

Godkänt svar rör sifferuppgifterna noll gånger. Delar texten i tre stycken, det är allt som behövs.

---

## Test 6: Ord som ändrar betydelsen

**Mönster att fånga:** Inga av de 33. Testet mäter avsnitten om falska vänner och ord som säger mer än du menar i [`../references/svenska-ord.md`](../references/svenska-ord.md): håller modellen isär det som går att rätta från det som måste lämnas till skribenten?

```text
Tack vare den svaga kronan förväntas importkostnaderna öka med 3%, vilket innebär att marginalen kommer att minska med 2% och att vi ska se över prissättningen. Vi har redan mindre kunder än i fjol, och eventuellt kommer vi att behöva säga upp avtalet med leverantören. Koncernens omsättning ligger på 1,2 biljoner kronor.
```

Godkänt svar rättar det som meningen själv avgör. *Tack vare* blir *på grund av*, eftersom orsaken är negativ. *Förväntas* blir *väntas*, eftersom det är en prognos. *3%* och *2%* får mellanslag före procenttecknet. Allt annat står kvar, med en fråga under **Kvar för dig**: om *2 %* menar procent eller procentenheter, om *ska* är ett beslut eller ett förslag, om *mindre kunder* betyder färre eller mindre, om *eventuellt* menar kanske eller till slut, och om *biljoner* ska vara miljarder. Ett svar som tyst skriver om någon av de fem underkänns, hur rimlig gissningen än är.

---

## Test 7: Eget skrivande

**Mönster att fånga:** Alla. Testet har inget utkast. Det mäter läget Eget skrivande i [`../SKILL.md`](../SKILL.md): att modellen skriver en kort svensk text utan AI-mönster och utan att hitta på det den inte vet.

```text
Skriv ett kort mejl till Karin på ekonomiavdelningen. Leveransen av de nya datorerna är försenad, och jag vet inte när den kommer.
```

Godkänt svar är ett kort mejl som börjar med ärendet. Det innehåller inget leveransdatum, ingen orsak till förseningen, inget antal datorer och ingen leverantör, eftersom inget av det står i uppdraget. Behöver mejlet en uppgift, som avsändarens namn, står den som hakparentes: `[ditt namn]`. Inget fjäsk i slutet, och ingen variant av ”hoppas detta mejl finner dig väl”.
