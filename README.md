# Airbean_exam

Airbean är en applikation för ett företag som säljer kaffe med leverans av drönare. 
I denna uppgiften tränar vi på de fyra områdena inom datalogist tänkande och applicerar detta på en färdig figmaskiss. 
[Den figmaskiss som vi har jobbat med](https://www.figma.com/file/ONcO3UQRPBLQsZc3FkysMt/AirBean-v.1.1---with-profile?type=design&node-id=0-1&mode=design)

## Decomposition 

Vi inledde vår decomposition-analys med att observera att vi arbetade med en app istället för en webbsida, vilket innebar att responsiv design inte var nödvändig i **gränssnittsdesign** kategorin då vi endast hade en mobilskiss att utgå ifrån. Även om vi övervägde att appen eventuellt skulle fungera på plattor, valde vi att fokusera på det vi såg i skissen.

Andra vanliga kategorier som **användarhantering, produkthantering och varukorgshantering** var ganska grundläggande. I **användarhantering** inkluderade vi inte bara inloggning och kontoskapande utan även möjligheten att beställa som gäst. För att visa tidigare beställningar krävdes en databas för att lagra information och möjliggöra framtida analys.

Vi noterade avsaknaden av produktbeskrivningar i Figma-skissen, så vi baserade våra antaganden i **produkthantering** kategorin endast på produktlistan. Vi såg också att det inte fanns någon möjlighet att ta bort produkter från varukorgen i appen, vilket vi därför inte inkluderade i vår analys. Att tydligt visa pris inklusive moms och leveransavgifter ansågs vara viktigt för användarupplevelsen.

För **orderhantering** övervägde vi alternativen att erbjuda orderbekräftelse via push-meddelanden eller SMS istället för e-post, vilket kändes smidigare för en app som Airbean.

I **betalningshanteringen** integrerade vi en betaltjänst för att hantera betalningar och likaså planerade vi att integrera GPS-tjänster för positionsdata i **positionshantering** kategorin istället för att utveckla något nytt från grunden.

*Vi observerade avsaknaden av kundtjänst- eller FAQ-logotyp i skissen och antog därför att vår app för tillfället inte erbjöd sådana funktioner.*

## Pattern recognition 

Pattern recognition innebär att identifier mönster, trender och regelbundenhet inom data. Genom att analysera och förstå dessa mönster kan man dra slutsatser och fatta informerande beslut. 

Som vi kan se i denna övning så har vi ett stort behov av att spara information i **databaser** för att kunna se saker som produkter, användaruppgifter och beställningshistorik. 
Detta är även viktigt för att saker som autentisering, pris och saldo skall fungera korrekt. 

Vi har också ett mönster i form av **gränssnittsdesign** i appen. 
Färger, font och utformning är lika över hela appen (med vissa undandag för att färtydliga en aktion eller något med specifikt) för att få en mer bekant och lättanvändlig upplevelse.
Vi har en tydlig meny högst till vänster upp på sidan i form av en hamburgarmeny där man enkelt kan byta kategorier. Uppe till höger har vi en varukorg där man får en överblick på antal varor men kan också enkelt klicka sig vidare in i varukorgen.


**Beställningsstegen** är samma oavsett om du redan har ett konto och är inloggad eller inte. Det som kan skilja sig åt är *personliga rekommendationer* för den som är redan har ett konto baserat på orderhistorik. 

## Abstraction 
Abstraktion handlar om att förenkla saker och inte se det svåra och krångliga arbetet bakom en webbsida eller app.
I vårat fall med airbeans kan man dela upp irrelevanta och revalanta moment.

De irrelavanta i det här fallet är varukorgens komplexivitet med dess databashantering , samt öppnande för ett nytt konto eller login där även databaser har en stor uppgift för att slutanvändaren  skall kunna hantera appen eller websidan på ett korrekt sätt.

Slutanvändaren av appen eller hemsidan skall inte behöva funder på backend arbetet utan bara kunna få en så bra upplevelse som den bara kan när den exempelvis handlar en kaffe på våran airbeans app.

Irrelevanta detaljer:

Den tekniska sidan av drönaren dvs vad som gör att den lyfter

Specefika detaljer om användarnas personliga information som inte är kopplade till beställningen.

login-sida

Skapa ny användare

positionshantering

Databashanteringen som lagrar användarinformationen

Relevanta detaljer :

Användargränssnittet där användaren beställer kaffe och placerar en beställning

Drönarens GPS funktion samt anslutning till servern

Lagring av beställningsdata, hantering av flera beställningar samtidigt.

bekräftelse av betalningar.

Inloggningsprocessen där användaren kan skapa ett konto eller lägga in.

Lagring av användaruppgifter som användarnamn samt epost adresser.



## Algorithm Design 

Sammanfattning för vårat Flödesdiagram. 

Öppna Airbean-appen:
Användaren startar Airbean-appen för att komma åt dess funktioner och tjänster.

Öppna meny:
Användaren navigerar genom appens meny för att utforska de olika alternativen som finns tillgängliga.

Titta på produkter:
Användaren granskar de kaffe-produkter som erbjuds i appen för att fatta ett beslut om vad de vill köpa.

Välj produkt:
När användaren funnit sin önskade produkt och vill köpa den så går hen vidare genom att trycka på plus-tecknet brevid produkten. Vill användaren inte köpa produkten återvänder hen till menyn och fortsätter sitt sökande.

Lägga till i varukorg:
Om användaren bestämmer sig för att köpa produkten, placeras den i varukorgen för senare bekräftelse och slutförande av köpet.

Handlat färdigt?
Användaren avgör om de har avslutat sin shopping och är redo att gå vidare till betalning och utcheckning. Vill användaren köpa mer produkter återvänder hen återigen till menyn och upprepar punkterna ovan.

Klicka på utcheckning:
Användaren initierar betalningsprocessen genom att gå vidare till utcheckning. I denna appen står det "Take my money" istället för "utcheckning" eller "gå till utcheckning". 

Inloggad?
Appen kontrollerar om användaren redan är inloggad för att underlätta betalningsprocessen och för att spara tid.

Logga in:
Om användaren inte är inloggad, ges de möjlighet att logga in för att ansluta köpet till deras konto och för att spåra ordern. Om användaren inte vill logga in kan hen fortsätta som gäst.

Fylla i leveransinformation:
Användaren anger nödvändig information för leveransen, inklusive leveransadress och önskat leveransdatum. Är användaren redan inloggad kan man tänka sig att leveransinformation redan finns sparad från tidigare köp (Om användaren har godkänt det).

Fylla i betalningsinformation:
Användaren matar in betalningsuppgifter, inklusive kortnummer och säkerhetskod. Även denna information kan man tänka sig finns sparad för att underlätta köpet för användaren.

Verifiera betalningsinformation:
Appen verifierar att de angivna betalningsuppgifterna är giltiga och korrekta.

Finns det pengar på kontot?
Appen kontrollerar om det finns tillräckligt med pengar på användarens konto för att täcka kostnaden för köpet.  Om det inte finns tillräckligt med pengar på användarens konto skickas hen tillbaka till "fylla i betalningsinformation". 

Bekräfta köp:
Om betalningsinformationen är godkänd och det finns tillräckligt med pengar på kontot, bekräftas köpet och ordern slutförs.

Skicka bekräftelse:
En bekräftelse skickas till användaren (push-notis eller sms), som inkluderar en sammanfattning av ordern och andra relevanta detaljer.

## Hur markdown fungerar i en README.md fil 

# Huvudrubrik

Detta är en kort beskrivning av projektet.

## Underrubrik 1

Här är lite mer information om en specifik del av projektet.

### Underrubrik 2

Detaljerad information om en underdel av projektet.

## Enkel punktlista

- Första punkten
- Andra punkten
- Tredje punkten

## Numrerad punktlista

1. Första punkten
2. Andra punkten
3. Tredje punkten

## Länkar

[Förklaring av en länk](https://www.example.com)

## Fet text

**Detta är fet text.**

## Kursiv text

*Detta är kursiv text.*
