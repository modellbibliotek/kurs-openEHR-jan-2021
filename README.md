# Övningsmaterial för SFMIs openEHR-kurs (Januari 2021)

Se https://discourse.openehr.org/t/digital-utbildningsserie-om-openehr-nov-2020-jan-2021/1105 och https://www.sfmi.se/ för detaljer om kursen.

Spana gärna in https://discourse.openehr.org/t/openehr-se-borja-lasa-har/391 för mer info om svenskt arketyparbete.

Vi rekommenderar att du använder Google Chrome för Archetype Designer, men vissa andra moderna webbläsare kan också funka. Var beredd på att det tar tid (uppåt en halvminut) att öppna ett repository och flera sekunder att sedan öppna eller spara en enskild arketyp i verktyget.

Kom ihåg att du kan spana in, översätta och ladda ner arketyper även via https://ckm.openehr.org/ckm/

## Förberedelser att göra innan undervisningstillfälle 3 (18 Januari)
1. Skapa användare på Github och i Archetype Designer enligt instruktioner i de två första lathundarna på https://openehr.atlassian.net/wiki/spaces/healthmod/pages/966295553/Snabbstartsguide+f+r+modelleringsverktyg
1. Om du inte redan är inloggad i Archetype Designer (https://tools.openehr.org/designer/) följ lathund 3 (om inloggning)
1. För att riskfritt kunna experimentera och spara, skapa ett eget repository genom att:
    1. Klicka på den gröna knappen "+ New repository"
    1. Välj: Repository type = Local Folder
    1. Hitta på valftitt namn och fyll i under "Repository name"
1. Ladda ner exempelfilerna för kursen från det här GitHub-projektet (i valfritt bibliotek på din dator):
   1. Klicka på https://github.com/modellbibliotek/kurs-openEHR-jan-2021/archive/main.zip och ladda ner filen
   1. Packa upp zip-filen på din dator.
1. I Archetype Designer:
   1. Klicka på det repository som du skapade. Observera att det kan ta en stund (upp till en minut) att öppna det.
   1. Klicka på "Import" längst upp i fönstret. 
   1. Markera filerna från underbiblioteket "local" bland de filer som du packade upp i förra steget och dra-och-släpp dem i rutan med texten "Drop here" i dialogfönstret.    
   1. Klicka på den gröna knappen "Upload all", vänta tills allt laddats upp och klicka då på "Close".
1. Nu kan du öppna mallen "akutmall_undervisningsexempel_2a" eller de ingående arketyperna genom att klicka på dem.

### Info om akutmall_undervisningsexempel_2a (kommer att användas i övning 3b)
Template/mallen akutmall_undervisningsexempel_2a som användes vid andra undervisningstillfället (13 Jan) är en förenklad (inte helt realistisk) delmängd av saker som kan vara intressanta vid akut omhändertagande av vissa skador. Den är utformad för att visa olika användbara egenskaper hos modeller baserade på en kombination av openEHR och Snomed CT.

## Övningar vid undervisningstillfälle 3 (18 Januari)

### 3a. Skapa och terminologibind arketyp för motionslopp
Vi låtsas nu att vi ska hjälpa ett forskningsprojekt att fånga mer detaljerade data kring olyckor vid Vätternrundan som kräver vårdsinsatser, de av Region Östergötlands mottagningar som brukar hantera flest skador från Vätternrundan är med i studien och har gått med på att utöka sitt olycksfomulär. Vi hittar ingen lämplig färdig arketyp utan bestämmer oss för att författa en egen. Men att göra en särskild vätternrunde-arketyp verkar lite väl specifikt så vi beslutar göra en mer generell om händelser vid motionslopp.

1. Starta Archetype Designer i Google Chrome (https://tools.openehr.org/designer) och logga in med ditt personliga konto (som du skapat själv tidigare, se ovan)
1. Inspektera den befintliga arketypen `Problem/Diagnosis` (den öppnas då som en till flik längst upp, till höger om fliken för ditt skapade repository). Använd drop-down-menyn uppe i högra hörnet för att byta språk till svenska. Leta upp och läs beskrivning/metadata (fliken "Details" i högra spalten) för fältet `Extra information` som är av typen "SLOT" - där funderar vi på att senare i templaten stoppa in vår nya motionslopps-arketyp. 
1. Gå tillbaks till fliken för ditt skapade repository och skapa en ny arketyp genom att klicka på den stora gröna knappen "New" och välja "Archetype". 
   * I Rm Type, välj CLUSTER
   * I Concept ange "Motionslopp_NN" där NN är dina initialer (OBS: inga ÅÄÖ eller bindestreck) eller annan unik text (så att vi inte senare krockar med namn i vår gemensamma labbmiljö för formulär).
   * I fältet Version ska inget fyllas i/ändras.
   * I fältet Original Language, välj Swedish (sv) (Det är ok att använda svenska som originalspråk om vi inte tror att den kommer spridas internationellt, vilket vi i detta fall inte tror.)
   * Klicka på knappen Create.(Om inget händer kan det ha smugit sig in något icke tillåtet tecken i namnet. Testa då att ändra namnet och klicka igen.)
1. Skapa ett träd (ungefär) som det i bilden [motionslopp.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/motionslopp.png?raw=true) genom att för varje fält/rad klicka på motsvarande symbol i vänsterkanten och ange namn. 
Ha följande tips i åtanke för att testa olika funktioner i verktyget.
   * Det går att duplicera fält så att alla inställningar följer med, gör det t.ex. för att kopiera mellan fälten `Latitud` och `Longitud`.
   * För värden i `Typ av motion` välj "Internal Coded", tryck sedan den blå knappen "Edit" och skapa en lista med t.ex. de fyra raderna Cykling, Löpning, Skidåkning, Simning.
   * För värden i `Träningsvana` välj "Internal Coded", tryck sedan den blå knappen "Edit" och skapa en lista med t.ex. raderna nedan. (För att spara tid kan du markera och kopiera hela listan nedan, via exempelvis Anteckningar rensa listan från specialtecknen och kopiera igen, och när du står på första tomma fältet i kolumnen "Text" klistra in hela urklippet så skapas alla tre rader, tryck sedan "Save")
    * Nybörjare
    * Motionsidrottare
    * Elitnivå

   * För inställningarna i fältet `Antal tidigare deltaganden i detta lopp` ta bort bocken framför "unbound" under rubriken "Range". Då kommer nya val fram, sätt/behåll 0 som minimumgräns (för att förbjuda negativa värden) och ta bort bocken framför "Max" så att det inte finns någon övre gräns.
   * För fältet `Tid efter start` skulle vi vilja använda datatypen "Duration". Istället för att använda knappen i vänsterkanten kan man välja någon annan datatyp (t.ex. "Any") och genom att klicka i rutan bredvid "Available types" få fram en bläddringslista där bl.a. "Duration" finns.
   * I fält av typen "Quantity" kan man välja att tillåta (flera) olika enheter genom att vid etiketten "Units" trycka på ´+´-knappen. Då kommer det upp en ruta med sökfält för "Category" och "Units" genom att klicka i fältet kommer en bläddringslista upp, men man kan även börja skriva det man söker efter. I Category kan man söka storhet/typ, t.ex "length", och när man valt storhet/typ så kan man klicka i sökfältet "unit" och får då bara upp enheter som passar storheten.
       * För `Sträcka från start` välj att tillåta både meter och kilometer
       * För `Longitud` och för `Latitud` välj "degree (deg)" som enhet (som är av kategorin "Angle, plane")
1. Spara ditt arbete ofta, och åtminstone nu.
1. Terminologibind åtminstone "skidåkning" i fältet `Typ av motion` till Snomed CT (Lämpligt snomedbegrepp: 45033006). *Se beskrivning av hur på t.ex. https://youtu.be/BqUWVpnFXiw om du inte redan sett annan demo.* Den som har tid över kan börja leta i begreppen under [415577004 | idrott |](https://browser.ihtsdotools.org/?perspective=full&conceptId1=415577004&edition=MAIN/SNOMEDCT-SE/2020-11-30&release=&languages=sv,en) i Snomed CT och försöka terminologibinda fler saker.
1. Spara ditt arbete ofta, och åtminstone nu.
       
### 3b. Skapa och justera NN_akutmall_undervisningsexempel_3b
1. Kopiera exempel-mallen från förra undervisningstillfället, "akutmall_undervisningsexempel_2a" genom att ställa pekaren över mallen i listan av mallar och arketyper så att tre prickar dyker upp på raden i listan, tryck på dem så kommer kopieringsmöjligheten upp, se [copy_template.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/copy_template.png?raw=true). Spara då kopian med ett nytt namn i stil med NN_akutmall_undervisningsexempel_3b (där NN är dina initialer eller annan unik text så att vi inte senare krockar med namn i vår gemensamma labbmiljö för formulär. Undvik åäö i filnamn.)
1. Om du tittar i listan över mallar så ser du att namnet i liten text underst på en av mallarna har ändrats till det du valde i förra steget, men namnet i stor fet text på den raden är oförändrat från originalet. Öppna mallen och ändra den översta nodens namn i mallen till det namn du gav kopian, om du tycker det är snyggare så kan du här ersätta understrecken `_` med riktiga mellanslag (men behåll dina initialer för att undvika sammanblandning senare). Spara mallen. Gå tillbaka till (gröna) fliken med listan över arketyper och mallar och kolla om ändringen slagit igenom. 
1. Växla tillbaka till fliken med mallen. Kolla att svenska (Sv) är valt (uppe till höger)
1. Koppla in vår nytillverkade arketyp om motionslopp i mallens fält `Extra information` (som finns under `Problem/Diagnosis`) genom att klicka på fältet Extra information och i listan över kluster-arketyper som då dyker upp i panelen till höger välja din arketyp. Notera att det nu inte går att titta på mallen på engelska och tyska längre, eftersom vår tillagda arketyp bara finns på svenska.
1. I mallens fält `Loppets namn` vill vi lista de olika varianterna på vätternrundan så att det blir smidigt för personalen. Välj "Free text" sedan "Edit values" kopiera hela listan nedan, rensa från specialtecken, och när du står i översta tomma fältet klistra in det urklippta och tryck "Save". 

   * Vätternrundan
   * Halvvättern 150 km
   * Tjejvättern 100 km
   * Vätternrundan 100 km
   * MTB-Vättern
   * Minivättern

1. Se sedan till att "Limit to list" *inte* är förbockat, annars kan man inte skriva in namn på andra motionslopp när man använder mallen. Som "Default Value" välj Vätternrundan. Spara mallen. 
1. I inställningarna för fältet `Tid efter start` ta bort bocken framför "Allow all time units" och välj sedan bort "Years", "Months" och "Weeks".
1. Terminologibind fältet 'Klinisk tolkning', under Andning, till listan med alla barn till snomedbegreppet  85617008 (onormal andningsrytm). Detaljer:
   * I https://browser.ihtsdotools.org/ se till att svenska versionen "Release: Swedish Edition..." är vald välj sedan fliken `Expression Constraint-sökning` och skriv in `<< 85617008 | onormal andningsrytm |` se bilden [snomed_andningsrytm.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/snomed_andningsrytm.png?raw=true).
   * Kopiera ut resultatlistan från sökverktyget och klistra in i ett kalkylark, ta bort kolumnen med termer på engelska, byt plats på de kvarvarande kolumnerna så att sifferkoder står till vänster om de beskrivningar du vill ha. (Vi brukar använda Google Sheets, t.ex. Excel funkar också men man kan då behöva ändra sifferformat för att få tillbaka heltal när Excel automatiskt bakar om stora tal till annan form: Markera kolumnen med koder, högerklicka och välj "Formatera celler", i fliken "Tal" ange Tal som kategori och sätt decimaler till 0, klicka "OK".) 
   * I inställningarna för mallens fält 'Klinisk tolkning' välj "External Coded", 
       * under `terminology` skriv `SNOMED-CT`
       * under `Uri` skriv `http://snomed.info/sct/`
   * Bocka för "Add valueset"
   * Tryck på "Edit valueset"
   * Kopiera från ditt kalkylark ut de två spalterna med kod och text, klistra in dem i den tomma "Edit valueset"-listan (när markören står i det översta tomma fältet i kolumnen code) och tryck sedan "Save"
1. Spara ditt arbete ofta, och åtminstone nu.
1. Vi låtsas att det är 31-Aug-2020 och vi behöver ladda ner och inkludera den uppdaterade svenska översättningen av blodtrycksarketypen i Sofia Janstads "Branch" Rev 8.3 i Clinical Knowledge Manager. Den hade då inte hunnit återföras till huvudversionen ("trunk").
   * Öppna genväg till blodtrycksarketypens revisionshistorik: https://ckm.openehr.org/ckm/archetypes/1013.1.3574/revisionhistory (det tar lite tid innan historiken äär inladdad)
   * Klicka på Sofia Janstads "Branch", raden med Rev 8.3...
   * ...då öppnas en ruta med beskrivning och direkt under den en knapp "Details", tryck på den knappen.
   * I menyn som då dyker upp välj "Export Archetype"
   * Nu öppnas en ny flik för just denna version och tre knappar för export visas, välj "Export ADL"
   * Spara ner filen lokalt på din dator (kom ihåg var)
   * Växla tillbaka till Archetype Designer där vi förut höll på att redigera vår template
   * Tryck på "Import" längst upp och importera Blodtrycksarketypen du nyss laddade ner (på samma sätt som du tidigare importerade arketyper i förberedelserna inför övingstillfället)
   * I mallen välj noden "Puls/Hjärtfrekvens" klicka sedan på Blodtryck i listan över arketyper till vänster, den kommer då importeras  nedanför "Puls/Hjärtfrekvens"-arketypen
1. Släck ut delar av blodtrycksarketypen
    1. Välj `24 timmars blodtrycksmätning` och tryck den gula `0..0`
    1. Under "Ospecificerad händelse", välj fältet "Medelartärtryck", håll inne skift-tangenten på tangentbordet samtidigt som du markerar "kommentar" fyra rader längre ner. Nu ska alla fyra rader vara markerade och ute till höger dyker knappen "Prohibit all" upp. Tryck på den för att släcka ut de fyra raderna i ett svep.
    1. Släck på liknande sätt ut allt utom "ställning" under "state"
    1. Släck på liknande sätt ut allt under "protocol"
1. Akutmottagningen säger att de vill ha inskrivningsmallen på formen ABCDE (Airway, Breathing, Circulation...) som pappers-akutjournalen, [se exempel (låtsaspatienter)](https://drive.google.com/file/d/0BwdHmPbK5e3SWjRsQzUyR243OEk/view?usp=sharing). De behöver också ett sätt att rapportera problem med luftvägar. Målbilden är en template som ser ut ungefär som på bilden [ABCDE.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/ABCDE.png?raw=true)
   1. Få bättre överblick genom att trycka på `+` för att fälla ihop arketyperna under Rubriken vitalparametrar
   1. Ändra namn på rubriken "Vitalparametrar" till "ABCDE"
   1. Lägg in ett nytt exemplar av SECTION-arketypen "Rubrik" (eng. Ad Hoc Heading) längst upp i mallen, direkt under "content" och namnge den "Skada". Dra sedan in den exsisterande Problem/diagnos-grenen under nya "Skada"-rubrikens "items"
   1. Lägg till tre nya exemplar av SECTION-arketypen "Rubrik" under ABCDE och namnge dem
       * A. Fri luftväg (Airway)
       * B. Andning (Breathing)
       * C. Cirkulation
   
   1. Under "items" under "A. Fri luftväg (Airway)" lägg till ett exemplar av arketypen "Problem/Diagnos" och justera den så här:
      * Byt namn på detta exemplar av "Problem/Diagnos" till "Luftväg"
      * Ändra fältet "Occurrences" (under fliken "Constraints") från `0..1` till `0..*` (för att tillåta fler exemplar av noden).
1. Släck ut allt utom `Problem/Diagnos namn` och `Klinisk Beskrivning` i arketypen vi döpte om till "Luftväg".
1. Terminologibind fältet `Problem/Diagnos namn` i arketypen vi döpte om till "Luftväg" 
   1. välj "External Coded", 
       * under `terminology` skriv `SNOMED-CT`
       * under `Uri` skriv `http://snomed.info/sct/`
   * Bocka för "Add valueset"
   * Tryck på "Edit valueset"
   * Kopiera alla koder och termer (samtidigt) ur nedanstående tabell, och klistra in dem i den tomma "Edit valueset"-listan och tryck sedan "Save"

    |SCTID|Term|
    |---|---|
    |70407001|stridor|
    |79688008|andningshinder|
    |217808004|andningshinder orsakad av främmande kropp i matstrupen|
    |427286007|obstruktion av de nedre luftvägarna|
    |68372009|obstruktion av de övre luftvägarna|
    |427562009|blod i övre luftvägarna|
1. Spara ditt arbete ofta, och åtminstone nu.
1. Exportera din mall som en "Operational template" (OPT). Detaljer:
   * Klicka på Export, en ruta kommer upp
   * Klicka på den blåvita "Export"-knappen och välj "Export to OPT"
   * Kom ihåg var du sparar den exporterade filen på din dator, du behöver den i nästa övning

### 3c. Skapa och justera formulär
1. Nu byter vi verktyg. Logga in i https://tools.better.care/studio/ med användarnamn `sfmi` och lösenordet ni fått via epost i kalenderinbjudan (kan även efterfrågas i möteschatten), välj längst ner domänen ehrscape.com.
1. Välj Form Builder
1. Längst ner till vänster finns grå ikoner. Klicka på ikonen för import, den med pil uppåt inuti en ruta.
1. Det dyker nu upp ett import-fönster, dra-och-släpp din Operational Template (OPT), som du exporterade i förra övningen, dit. (Importen kan ta lite tid.)
1. Du bör nu ha fått upp en lista där din mall finns med någonstans, klicka på den.
1. Nu öppnas "editor" för formulär, innehållet från din template ska synas i vänsterspalten, dra in den översta noden (hela trädet följer med) från din template till den stora vita redigeringsytan i mitten av skärmen. Formuläret blir ganska stort med många ramar i ramar.
1. Ta bort den yttersta/översta ramen genom att gå upp till översta (grå) kanten (där ditt mallnamn sannolikt står), det dyker då upp nya ikoner. Klicka på den röda ikonen som ser ut som ett kryss omringat av fyra hörn = "Remove frame". 
1. Välj nu ramen "Skada" (om du har en sådan) och i högerspalten under rubriken "Presentation" ändra från "Container" till "Collapsible title".
1. Välj ramen "Problem/Diagnos" och klicka på röda "Remove frame"
1. Byt plats på "Klinisk Beskrivning" och "Anatomisk plats"
1. Välj "Klinisk Beskrivning", ändra i högerspalten "Display in" till 5 lines.
1. Nu betämmer vi att i detta formulär ska vi inte ta med det detaljerade sättet att ange lokalisation, så välj ramen "Anatomisk lokalisation" och tryck på den röda soptunnan. Notera i vänsterspalten att de datafält vi tog bort nu markerats i svart och finns där för att kunna dra in i andra delar av formuläret oom man skulle vilja.
1. I ramen motionslopp, titta på "Loppets namn" i är vätternrundan redan vald eftersom vi hade satt det som defaut i vår template/mall. Om du vill kan du säga att det idag är dags för Tjejvättern istället och ändra så att det blir default idag istället för Vätternrundan. 
1. I drop-down menyn för "Typ av motion" välj "Cykling" så att det också blit default i formuläret.
1. Nu är det dags att testköra en första gång, välj "preview" ovanför formuläret.
    * Testa att koppla om mellan visningslägena, "Desktop", "Tablet" och "Mobile"
    * Notera att man för "anatomisk plats" kan välja flera alternativ samtidigt
    * Notera att du nu under sträcka från start måste välja meter eller kilometer, default saknas (det kan du åtgärda senare i editor-läget om du vill)
    * Om inte vänsterspalten är öppen, öppna den med `>>` nära övre vänstra hörnet- Inspektera hur data ändras när du gör val i formuläret.
    * Välj "Stridor" under luftväg. Tryck sedan på "+ Add another Luftväg" och i den nya rutan som dyker upp nedanför välj något ytterligare luftvägsbekymmer (detta är önskad funktionalitet).
    * Notera att det även går att lägga till fler exemplar av "Ospecificerad händelse" inuti observationerna "Andning", "Puls/Hjärtfrekvens" och "Blodtryck". Templaten vi gjort tillåter det, men för vårt inskrivningsformulär vill vi bara tillåte en av varje sort, så...
1.  ...avsluta "Preview" genom att växla över till "Editor".
1. Under "Andning" välj ramen "Ospecificerad händelse" och ändra i inställningarna (högerspalten) fältet "max" under "MULTIPLICITY" från 100 till 1. Gör samma sak för "Ospecificerad händelse" under "Puls/Hjärtfrekvens"  och "Blodtryck". Klicka även den röda "remove frame" på alla "Ospecificerad händelse"
1. Testkör igen med "preview"
1. Publicera en första version av ditt formulär genom att klicka på "Publish" överst på skärmen (så att det kan användas i journalsystemet)
1. Nu vill vi ha motionslopp dolt tills man väljer att öppna det med en liten switch.
    * i vänstra kanten, välj "Generics" (liknar legobit)
    * Drag sedan "Boolean" till precis ovanför "motionslopp" och släpp den där och döp om etiketten till "Motionslopp?".
    * Under "Design"-fliken till höger ändra presentation till "toggle switch"
    * Under "Interactions"-fliken till höger, under "When" klicka först på "Select field" och sedan på Motionslopp-switchen du nyss redigerade. i menyn som då dyker upp välj "is" och sedan "true".
    * Under "Interactions"-fliken till höger igen, under "Then" klicka först på "Select field" och sedan på Motionslopp-ramen. I menyn som då dyker upp välj "is shown"
    * Klicka på "Otherwise" och klicka på "Select field" och sedan på Motionslopp-ramen igen. I menyn som då dyker upp välj "is hidden"
    * Det skulle kunna se ut ungefär så här nu: [motionslopp-switch.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/motionslopp-switch.png)
1. Testkör, via Preview, logiken/vilkorsstyrningen du nyss byggde 
1. Snygga till under rubriken "B. Andning (Breathing)"
    * Klicka röda "Remove frame" för "Pulsoximetri"
    * Klicka röda "Remove frame" för den översta "Inandad syrgas" (altså den som hör till pulsoximetri, inte den för andning längre ner)
    * Inom den inre ramen "Andning" gör följande:
        * Välj "Förekomst" vi kan förtdliga saker på formulärnivå utifall vi inte skulle ha möjlihget att ändra i arketyp/template.
            * I fliken "Design" i högra spalten ändra "Presentation" till "button group", slå sedan på switcharna "hide label" och Show in columns. Sätt Number of columns till 2.
            * I fliken "Content" i högra spalten, under "Selection values" ändra "Förekommer" till "Andas"
            * I fliken "Content" i högra spalten, under "Selection values" ändra "Ej möjlig att upptäcka" till "Andning ej upptäckt"
        * Välj "Regelbundenhet" 
            * I fliken "Design" i högra spalten ändra "Presentation" till "button group", slå sedan på switcharna "hide label" och Show in columns. Sätt Number of columns till 2.
1. Överkurs:
    * Koppla med when+then+otherwise-regler:
        * pulsoximetrins "På luft"-checkbox till motsvarande för andning och till "Luft eller syrgas?" i NEWS2.
        * pulsoximetrins "Syrgasflöde" (både värde och enhet) till motsvarande fält för andning
    * Markera andningens hela ram kring "inandad syrgas" som "hidden"
    * Ledtråd till syrgas-delen av denna överkursuppgift: [syrgas-koppling.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/syrgas-koppling.png?raw=true) (spoiler-alert!) Det är givetvis ok om ditt formulär ser annorlunda ut grafiskt.
    
--- Slut på övningar för undervisningstillfälle 3 (18 Januari) ---

## Exempelpatienter (till AQL-exempel m.m. vid senare tillfälle)
|Field|Patient One|Patient Two|Patient Three|Patient Four|
|---|---|---|---|---|
|**Problem/Diagnos**|||||
|Skada|127347009 arbetsskada + 125665001 klämskada (eller 50793006 klämskada på hand?) | 125667009 kontusion (eller 44801007 kontusion på höft?)|443786003 skada under idrottsaktivitet + 281599007 distorsion av ligament i ben (eller 54888009 distorsion av knä) |397996002 skada orsakad av explosion|
|Klinisk beskrivning|The patient held his hand in a door opening at work when a collegue accidentely slammed it.|The patient fell down the stairs at home  and landed on his right hip.|The patient sprained her knee while playing badminton.|The patient was experimenting with a friend when things went out of control and there was an explosion.|
|Anatomisk plats (grovt för att förenkla exemplet)|80768000 vänster arm, struktur|62175007 höger ben, struktur|32153003 vänster ben, struktur|6921000 höger arm, struktur|
|Anatomisk plats (alternativ utan lateralitet)|53120007 övre extremitet, struktur|61685007 nedre extremitet, struktur |61685007 nedre extremitet, struktur|53120007 övre extremitet, struktur|
|Datum och tid för skada|2020-01-23 11:34|2020-01-23 12:34|2020-01-23 13:34|2020-01-23 14:34|
|**Pulsoximetri**|||||
|SpO₂|98%|96%||97%|
|Syrgasflöde||||5 l/min|
|På luft|True|True||False|
|**Andning**|||||
|Frekvens|19|21|14|18|
|Syrgasflöde||||5 l/min|
|På luft|True|True||False|
|**Puls/Hjärtfrekvens**|||||
|Frekvens|72|92|50|112|
|Regelbunden|Regular|Regular|Regular|Irregular|
|Oregelbunden typ||||Regularly Irregular|
|Kropsställning|Reclining|Lying|Reclining|Lying|
|Metod|Automatic, non-invasive|Automatic, non-invasive|Palpation|Automatic, non-invasive|
|Lokalisation|Finger|Finger|Radial Artery - Left|Toe|

Det är inte självklart vilka Snomedbegrepp som vore lämpliga "föräldrabegrepp" till en fältet "Skada" ovan. 417163006 | traumatisk och/eller icke-traumatisk skada | är ett förslag som ändå inte täcker in alla ovanstående exempel. Man får gå högre i hierarkierna.
Sannolikt skulle man behöva använda/göra termonologiurval för akutvård. (Kanske kopplat till akutmotagningarnas RETTS-koder m.m.?)

## Valfria extrasteg senare:
1. Följ lathund 4 `Koppla Archetype Designer till arbetsytan på GitHub` 
1. Om du vill koppla in fler repositories upprepa lathund 4 med olika innehåll i "Repository". CKM-mirror kan t.ex. vara kul att koppla in och utforska, men tar en del tid att ladda in med sina över 500 arketyper.
1. Skicka ett mail till asa.skagerhult@regionostergotland.se och erik.sundvall@regionostergotland.se där du berättar ditt GitHub-användarnamn (men _inte_ ditt lösenord) om du vill kunna spara (inte bara läsa) i repository/arbetsytor som använs i nationellt samarbete.
