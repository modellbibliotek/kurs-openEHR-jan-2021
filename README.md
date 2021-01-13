# Övningsmaterial för SFMIs openEHR-kurs (Januari 2021)

Se https://discourse.openehr.org/t/digital-utbildningsserie-om-openehr-nov-2020-jan-2021/1105 och https://www.sfmi.se/ för detaljer om kursen.

Spana gärna in https://discourse.openehr.org/t/openehr-se-borja-lasa-har/391 för mer info om svenskt arketyparbete.

Vi rekommenderar att du använder Google Chrome för Archetype Editor, men vissa andra moderna webbläsare kan också funka. Var beredd på att det tar tid (uppåt en halvminut) att öppna ett repository och flera sekunder att sedan öppna eller spara en enskild arketyp i verktyget.

Kom ihåg att du kan spana in, översätta och ladda ner arketyper även via https://ckm.openehr.org/ckm/

## Förberedelser
1. Skapa användare på Github och i Archetype Designer enligt instruktioner i de två första lathundarna på https://openehr.atlassian.net/wiki/spaces/healthmod/pages/966295553/Snabbstartsguide+f+r+modelleringsverktyg
1. Om du inte redan är inloggad i Archetype Designer följ tredje lathunden (om inloggning)
1. För att riskfritt kunna experimentera och spara, skapa ett eget repository lokalt på servern genom att:
    * Klicka på gröna knappen "+ New repository"
    * Välj: Repository type = Local Folder
    * Hitta på valftitt namn och fyll i under "Repository name"
1. Ladda ner exempelfilerna för kursen från det här GitHub-projektet genom att klicka på https://github.com/modellbibliotek/kurs-openEHR-jan-2021/archive/main.zip
1. Packa (i valfritt bibliotek på in dator) upp zip-filen och gå in i underbiblioteket "local"
1. Klicka på "Import" längst upp i archetype designer. Då visas en dialog som har bl.a. har en ruta med texten "Drop here"; dra dit och släpp av filerna från underbiblioteket "local" som du packade upp i förra steget. Klicka sedan en gröna knappen "Upload all" och när allt sedan laddats upp, klicka då close.
1. Nu kan du öppna akutmall_undervisningsexempel_2a eller de ingående arketyperna

## Valfria extrasteg senare:
1. Följ den fjärde lathunden `Koppla Archetype Designer till arbetsytan på GitHub` 
1. Om du vill koppla in fler repositories upprepa lathund 4 med olika innehåll i "Repository". CKM-mirror kan t.ex. vara kul att koppla in och utforska, men tar en del tid att ladda in med sina över 500 arketyper.
1. Skicka ett mail till asa.skagerhult@regionostergotland.se och erik.sundvall@regionostergotland.se där du berättar ditt GitHub-användarnamn (men _inte_ ditt lösenord) om du vill kunna spara (inte bara läsa) i repository/arbetsytor som använs i nationellt samarbete.

## akutmall_undervisningsexempel_2a
Template/mallen akutmall_undervisningsexempel_2a som användes vid andra undervisningstillfället (13 Jan) är en förenklad (inte helt realistisk) delmängd av saker som kan vara intressanta vid akut omhändertagande av vissa skador. Den är utformad för att visa olika användbara egenskaper hos modeller baserade på en kombination av openEHR och Snomed CT.

## Undervisningstillfälle 3 (18 Jan)

### Skapa och terminologibind arketyp för motionslopp
Vi låtsas nu att vi ska hjälpa ett forskningsprojekt att fånga mer detaljerade data kring olyckor vid Vätternrundan som kräver vårdsinsatser, de av Region Östergötlands mottagningar som brukar hantera flest skador från Vätternrundan har gått med på att utöka sitt olycksfomulär. Vi hittar ingen lämplig färdig arketyp utan bestämmer oss för att författa en egen. Men att göra en särskild vätternrunde-arketyp verkar lite väl specifikt så vi beslutar göra en mer generell om händelser vid motionslopp.

1. Starta Archetype Designer (https://tools.openehr.org/designer) och logga in med ditt personliga konto (som du skapat själv tidigare, se ovan)
1. Inspektera den befintliga arketypen `Problem/Diagnosis`, leta upp och läs beskrivning/metadata för fältet `Specifika detaljer`` som är ett "SLOT" - där funderar vi på att senare i templaten stoppa in vår nya motionslopps-arketyp.
1. Skapa en ny arketyp "Motionslopp_NN" där NN är dina initialer (så att vi inte senare krockar med namn i vår gemensamma labbminlö för formulär). Den ska vara av type CLUSTER och vi kan köra med svenska som originalspråk (om vi inte tror att den kommer spridas internationellt).
1. Skapa ett träd (ungefär) som det i bilden motionslopp.png



### Namn_Ns_akutmall_undervisningsexempel_3a
* Kopiera akutmall_undervisningsexempel_2a
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
