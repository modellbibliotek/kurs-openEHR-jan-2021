# Övningsmaterial för SFMIs openEHR-kurs (Januari 2021)

Se https://discourse.openehr.org/t/digital-utbildningsserie-om-openehr-nov-2020-jan-2021/1105 och https://www.sfmi.se/ för detaljer om kursen.

Spana gärna in https://discourse.openehr.org/t/openehr-se-borja-lasa-har/391 för mer info om svenskt arketyparbete.

Vi rekommenderar att du använder Google Chrome för Archetype Designer, men vissa andra moderna webbläsare kan också funka. Var beredd på att det tar tid (uppåt en halvminut) att öppna ett repository och flera sekunder att sedan öppna eller spara en enskild arketyp i verktyget.

Kom ihåg att du kan spana in, översätta och ladda ner arketyper även via https://ckm.openehr.org/ckm/

## Förberedelser
1. Skapa användare på Github och i Archetype Designer enligt instruktioner i de två första lathundarna på https://openehr.atlassian.net/wiki/spaces/healthmod/pages/966295553/Snabbstartsguide+f+r+modelleringsverktyg
1. Om du inte redan är inloggad i Archetype Designer följ tredje lathunden (om inloggning)
1. För att riskfritt kunna experimentera och spara, skapa ett eget repository genom att:
    1. Klicka på den gröna knappen "+ New repository"
    1. Välj: Repository type = Local Folder
    1. Hitta på valftitt namn och fyll i under "Repository name"
1. Ladda ner exempelfilerna för kursen från det här GitHub-projektet (i valfritt bibliotek på din dator) genom att:
   1. Klicka på https://github.com/modellbibliotek/kurs-openEHR-jan-2021/archive/main.zip
   1. Packa upp zip-filen på din dator.
1. I Archetype Designer:
   1. Klicka på det repository som du skapade. Observerade att det kan ta en stund att öppna det.
   1. Klicka på "Import" längst upp i fönstret. 
   1. Markera filerna från underbiblioteket "local" som du packade upp i förra steget och dra och släpp dem i rutan med texten "Drop here" i dialogfönstret.    
   1. Klicka på den gröna knappen "Upload all", vänta tills allt laddats upp och klicka då på "Close".
1. Nu kan du öppna mallen "akutmall_undervisningsexempel_2a" eller de ingående arketyperna genom att klicka på dem.

## akutmall_undervisningsexempel_2a
Template/mallen akutmall_undervisningsexempel_2a som användes vid andra undervisningstillfället (13 Jan) är en förenklad (inte helt realistisk) delmängd av saker som kan vara intressanta vid akut omhändertagande av vissa skador. Den är utformad för att visa olika användbara egenskaper hos modeller baserade på en kombination av openEHR och Snomed CT.

## Övningar vid undervisningstillfälle 3 (18 Jan)

### 3a. Skapa och terminologibind arketyp för motionslopp
Vi låtsas nu att vi ska hjälpa ett forskningsprojekt att fånga mer detaljerade data kring olyckor vid Vätternrundan som kräver vårdsinsatser, de av Region Östergötlands mottagningar som brukar hantera flest skador från Vätternrundan är med i studien och har gått med på att utöka sitt olycksfomulär. Vi hittar ingen lämplig färdig arketyp utan bestämmer oss för att författa en egen. Men att göra en särskild vätternrunde-arketyp verkar lite väl specifikt så vi beslutar göra en mer generell om händelser vid motionslopp.

1. Starta Archetype Designer (https://tools.openehr.org/designer) och logga in med ditt personliga konto (som du skapat själv tidigare, se ovan)
1. Inspektera den befintliga arketypen `Problem/Diagnosis`, leta upp och läs beskrivning/metadata för fältet `Specifika detaljer` som är av typen "SLOT" - där funderar vi på att senare i templaten stoppa in vår nya motionslopps-arketyp. Använd drop-down-menyn uppe i högra hörnet för att byta språk till svenska.
1. Skapa en ny arketyp "Motionslopp_NN" där NN är dina initialer ellar annan unik text (så att vi inte senare krockar med namn i vår gemensamma labbmiljö för formulär). Den ska vara av typen CLUSTER och vi kan köra med svenska som originalspråk om vi inte tror att den kommer spridas internationellt.
1. Skapa ett träd (ungefär) som det i bilden [motionslopp.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/motionslopp.png?raw=true) med följande tips i åtanke för att testa olika funktioner i verktyget.
   * Det går att duplicera fält så att alla inställningar följer med, gör det t.ex. för att kopiera mellan fälten `Latitud` och `Longitud`.
   * För värden i `Typ av motion` välj "Internal Coded", tryck sedan den blå knappen "Edit" och skapa en lista med t.ex. de fyra raderna Cykling, Löpning, Skidåkning, Simning.
   * För värden i `Träningsvana` välj "Internal Coded", tryck sedan den blå knappen "Edit" och skapa en lista med t.ex. raderna Nybörjare, Motionsidrottare, Elitnivå.
   * För inställningarna i fältet `Deltagit tidigare i detta lopp, antal gånger` ta bort bocken framför "unboud" under rubriken "Range". Då kommer nya val fram, sätt/behåll 0 som minimumgräns (för att förbjuda negativa värden) och ta bort bocken framför "Max" så att det inte finns någon övre gräns.
   * För fältet `Tid efter start` skulle vi vilja använda datatypen "Duration", men den finns inte som knapp i vänsterkanten. Man kan då välja någon annan datatyp (t.ex. "Any") och genom att klicka i rutan bredvid "Available types" få fram en bläddringslista där bl.a. "Duration" finns.
   * I fält av typen "Quantity" kan man välja att tillåta (flera) olika enheter
       * För `Sträcka från start` välj at tillåta både meter och kilometer
       * För `Longitud` och för `Latitud` välj grader (degrees) som enhet
1. Terminologibind åtminstone "skidåkning" i fältet `Typ av motion` till Snomed CT (Lämpligt snomedbegrepp: 45033006). *Se beskrivning av hur på t.ex. https://youtu.be/BqUWVpnFXiw om du inte sett annan demo.*
1. Spara ditt arbete ofta, och åtminstone nu.
       
### 3b. Skapa och justera NN_akutmall_undervisningsexempel_3b
1. Kopiera exempel-mallen från förra undervisningstillfället, "akutmall_undervisningsexempel_2a" genom att ställa pekaren över mallen  i listar av mallar och arketyper så att tre prickar dyker upp på raden i listan, tryck på dem så kommer kopieringsmöjligheten upp, se [copy_template.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/copy_template.png?raw=true). Spara då kopian ett nytt namn i stil med NN_akutmall_undervisningsexempel_3a (där NN är dina initialer eller annan unik text så att vi inte senare krockar med namn i vår gemensamma labbmiljö för formulär)
1. Koppla in vår nytillverkade arketyp om motionslopp i mallens fält `Specifika detaljer` (som finns under `Problem/Diagnosis`) 
1. I mallens fält `Loppets namn` vill vi lista de olika varianterna på vätternrundan så att det blir smidigt för personalen. Välj "Free text" sedan "Edit values" kopiera hela listan nedan och när du tryckt "add" klistra in den och tryck "Save". Se till att "Limit to list" *inte* är förbockat, annars kan man inte skriva in andra motionslopp. Som "Default Value" välj Vätternrundan.
   * Vätternrundan
   * Halvvättern 150 km
   * Tjejvättern 100 km
   * Vätternrundan 100 km
   * MTB-Vättern
   * Minivättern
1. Terminologibind fältet 'Onormalt andningsmönster' till listan med alla barn till snomedbegreppet  85617008 (onormal andningsrytm). Detaljer:
   * I https://browser.ihtsdotools.org/ välj fliken `Expression Constraint-sökning` och skriv in `<< 85617008 | onormal andningsrytm |` se bilden [snomed_andningsrytm.png](https://github.com/modellbibliotek/kurs-openEHR-jan-2021/blob/main/images/snomed_andningsrytm.png?raw=true).
   * Kopiera ut resultatlistan från sökverktyget och klistra in i ett kalkylark, byt plats på kolumner så att sifferkoder står till vänster om de beskrivningar du vill ha
   * I inställningarna för mallens fält 'Onormalt andningsmönster' välj "External Coded", 
       * under `terminology` skriv `SNOMED-CT`
       * under `Uri` skriv `http://snomed.info/sct/`
   * Bocka för "Add valueset"
   * Tryck på "Edit valueset"
   * Kopiera från ditt kalkylark ut de två spalterna med kod och text, och klistra in dem i den tomma "Edit valueset"-listan och tryck sedan "Save"
1. Exportera din mall som en "Operational template" (OPT). Detaljer:
   * Klicka på Export, en ruta kommer upp
   * Klicka på den blå "Export"-knappen och välj "Export to OPT"
   * Kom ihåg var du sparar den exporterade filen på din dator, du behöver den i nästa övning

### 3c. Skapa och justera ett formulär
1. Nu byter vi verktyg. Logga in i https://tools.better.care/studio/ med användarnamn `sfmi` och lösenordet ni fått via epost, välj längst ner domänen ehrscape.com.
1. ...mer info kommer


## Exempelpatienter (till övningar m.m.)
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
