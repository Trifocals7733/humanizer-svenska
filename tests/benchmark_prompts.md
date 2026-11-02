# Testtexter & Benchmarks för Humanizer Svenska

Dessa testtexter innehåller koncentrerade samlingar av typiska AI-fällor. Använd dem för att utvärdera hur väl olika modeller (t.ex. Claude, GPT-4o, Gemini, DeepSeek) och agenter (Pi, Cursor, Claude Code) klarar att humanisera svensk text.

## Så mäter du

Kör varje text två gånger: en gång utan skillen och en gång med. Jämför paren, inte intrycket.

1. **Faktaskyddet.** Har modellen lagt till en siffra, ett datum, ett kundnamn eller en källa som inte står i testtexten? Ett enda påhittat värde underkänner körningen, oavsett hur snyggt resten är skrivet.
2. **Rösten.** Går det att se att texten handlar om samma sak, med samma avsändare, eller har modellen bytt ut innehållet mot något mer allmänt?
3. **Mönstren.** Vilka av de 33 markörerna i [`../references/monster.md`](../references/monster.md) finns kvar? Räkna dem, namnge dem, skriv upp dem.
4. **Formen.** `—`, raka citattecken, `12.5%`, title case i rubriker. Dessa är binära och ska vara noll.
5. **Strukturen.** Läs bara styckelängderna och första ordet i varje stycke. Är texten byggd som ett inlägg?
6. **Leveransen.** Följer svaret utdatakontraktet i [`../SKILL.md`](../SKILL.md), eller börjar modellen med en rapport om vad den ska göra?

Självkontrollen i [`../references/sjalvkontroll.md`](../references/sjalvkontroll.md) är samma lista, avsedd för modellen själv. Den fungerar också som rättningsmall när du bedömer en körning.

---

## Test 1: B2B Affärskommunikation
**Mönster att fånga:** Landskapsinledning, signifikansuppblåsning, kopulaundvikande, anglifieringar, sycofancy.

```text
Hej Karin!

I dagens ständigt föränderliga affärsklimat är det avgörande att organisationer proaktivt navigerar de möjligheter och utmaningar som digitaliseringen medför. Vår mjukvarulösning utgör ett banbrytande verktyg som möjliggör en mer effektiv och hållbar process genom att automatisera repetitiva moment.

Det är viktigt att notera att implementeringen av detta arbetssätt bidrar till en ökad förståelse för kundernas behov, vilket i sin tur belyser vikten av att ta ägarskap över er digitala transformation. Sammantaget representerar detta en unik möjlighet att skapa mervärde och säkerställa långsiktig framgång.

Hoppas detta låter intressant! Vill du boka ett förutsättningslöst möte nästa vecka där vi kan djupdyka i era behov?
```

---

## Test 2: Klarspråk / Myndighetstext
**Mönster att fånga:** Nominaliseringsstaplar, passiv röst, förlegad byråkratprosa, dolda aktörer.

```text
Med anledning av inkommen ansökan rörande beviljande av tillstånd kan det konstateras att erforderliga handlingar ej har tillhandahållits i fullständig omfattning. I syfte att handläggning av ärendet ska kunna genomföras erfordras att kompletterande underlag inkommer till förvaltningen senast inom trettio dagar. 

Det bör påpekas att ett tillhandahållande av fullständiga uppgifter utgör en förutsättning för prövning av ärendet. I händelse av att begärda kompletteringar ej inkommer i rätt tid kan ärendet komma att avvisas med stöd av gällande författning.
```

---

## Test 3: Rekrytering / Platsannons
**Mönster att fånga:** Floskler, spindeln i nätet, falsk familjekänsla, tretalsmönster, tankstreck.

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

## Test 4: Sociala medier / Tankeledarskap

**Mönster att fånga:** Emojis, dekorativa punkter, negativ parallellism, platt frågehak, hashtag-stapel.

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

**Mönster att fånga:** Inga. Testet mäter motsatsen till de andra fyra: att varje belopp, datum och namn överlever redigeringen orört, att ingen ny siffra tillkommer, och att en text som redan är i gott skick inte skrivs om. Det är det enda testet som fångar påhittade mätvärden, och de andra fyra innehåller inte en enda siffra att tappa.

```text
Vi bytte fakturasystem i mars. Det tog tre veckor och kostade 84 000 kronor, varav 12 000 gick till konsult. Under första månaden ökade antalet kreditfakturor från 14 till 19, vilket vi inte hade räknat med, och Anna Berg på ekonomiavdelningen fick lägga mycket tid på att förklara för kollegorna varför siffrorna såg ut som de gjorde.
```

Godkänt svar rör sifferuppgifterna noll gånger. Delar texten i tre stycken, det är allt som behövs.
