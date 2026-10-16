# Reflektion — Inlämning 1

**Namn:** [Emma Löwing]  
**Datum:** [16-10-26]

---

## Vad var svårast?

Det svåraste var att förstå normalisering, framförallt att konkret se skillnaden på 1NF, 2NF och 3NF. Detta blev enklare att förstå när jag jobbade med ER-diagrammet. Jag hade även lite svårt att skilja på olika databasrelationer, ex One-to-Many(1:N) och Many-to-Many(M:N). Det blev lättare att förstå relationerna när jag arbetade med kopplingstabellen SongGenres och såg hur en låt kunde tillhöra flera genrer.

---

## Vad lärde du dig?

Jag har fått en bättre generell förståelse för SQL och det känns inte lika läskigt längre. Jag litar mer på min egen förmåga eftersom jag, även om jag inte alltid kan få fram exakt rätt kod direkt, ofta vet var jag ska börja och därefter kan lista ut steg för steg vad som ska göras härnäst.

---

## Hur använde du SQL i praktiken — vad kändes naturligt och vad var förvirrande?
Jag tycker att själva SQL-kodandet gick ganska bra. De flesta kommandon kändes relativt naturliga och jag kunde ofta förstå hur jag skulle bygga upp en fråga. Ibland behövde jag fundera lite extra, särskilt när flera kommandon skulle kombineras, men jag upplevde inte att själva kodandet var den svåraste delen.

Det som var mer förvirrande var teorin bakom hur databasen skulle struktureras, framförallt normalisering och de olika relationerna mellan tabellerna.


---

## Om du hade mer tid — vad hade du lagt till eller gjort annorlunda?

Om jag hade haft mer tid så hade jag velat inkludera alla album och alla låtar. Jag hade velat ha:
- en tabell för collabs med andra artister
- en tabell för låtar som är singlar
- en tabell för vilka låtar som inte är singlar men som har fler lyssningar än singlarna på samma album
- mer uppgifter om låtarna, ex datum då vissa låtar (ex singlar) ibland släppts tidigare än själva albumet
- en tabell kring vilka album som finns i Taylor's Version
- något som undersöker relationerna mellan ordningen som albumen släpptes i jämfört med ordningen som Taylor's Version av samma album släpptes i
- en tabell för låtar som används i film och tv-serier
- en tabell för vilka låtar som Max Martin har varit med och skrivit/producerat.
När jag skulle lägga in all data skrev jag det första själv för att visa att jag vet hur det ska skrivas samt för att repetera mönstret men jag använde mig av AI för att skriva in de sista delarna av datan. Jag skrev in alla låtar i både Fearless och Red själv men fick hjälp med resterande album. När det gäller SongGenres så skrev jag in de tre första låtarna från varje album själv och så fick AI skriva resten. Detta för att spara tid och fokusera på queries istället för inmatning av data. Jag valde att inkludera många album och låtar för att få ett stort datamaterial att arbeta med och kunna testa mina SQL-frågor på.

---

## (VG) Varför valde du just den här tabellstrukturen?

Resonera kring ditt designval: Vad hade hänt om du löst det på ett annat sätt? Vilka för- och nackdelar ser du med din lösning jämfört med ett alternativ?

Jag valde att dela upp databasen i fem tabeller för att undvika onödig upprepning av information och få en tydligare struktur.

Om jag hade samlat all information i en enda stor tabell hade det blivit mycket upprepning och ganska rörigt. Exempelvis hade artistens namn och albumets titel behövt upprepas för varje låt. Det hade också blivit svårare att uppdatera information. Om en artist exempelvis byter namn hade jag behövt ändra det på flera ställen, vilket gör att risken för fel blir exponentiellt mycket större ju mer databasen växer.

En nackdel med min lösning är att man inte kan se all information direkt eftersom den är uppdelad i olika tabeller. Det märks särskilt i SongGenres, där man bara ser song_id och genre_id. För att veta vilken låt och genre det handlar om måste man antingen leta upp ID-numren i de andra tabellerna eller använda JOIN. Det innebär att vissa SQL-frågor blir mer komplicerade.

Trots detta tycker jag att fördelarna väger tyngre än nackdelarna. Databasen blir mer organiserad, lättare att underhålla och mindre känslig för fel, särskilt om den skulle växa och innehålla betydligt fler album och låtar.

Jag valde också att använda SongGenres som en kopplingstabell eftersom en låt kan tillhöra flera genrer och en genre kan innehålla flera låtar. På så sätt kan jag hantera en Many-to-Many-relation utan att behöva lagra flera genrer i samma cell.
