# kurs-openEHR-jan-2021

Se https://discourse.openehr.org/t/digital-utbildningsserie-om-openehr-nov-2020-jan-2021/1105 och https://www.sfmi.se/ för detaljer om kursen.

Spana gärna in https://discourse.openehr.org/t/openehr-se-borja-lasa-har/391 för mer info om svenskt arketyparbete.

Vi rekommenderar att du använder Google Chrome för Archetype Editor, men vissa andra moderna webbläsare kan också funka. Var beredd på att det tar tid (uppåt en halvminut) att öppna ett repository och flera sekunder att sedan öppna eller spara en enskild arketyp i verktyget.

Kom ihåg att du kan spana in, översätta och ladda ner arketyper även via https://ckm.openehr.org/ckm/

## akutmall_undervisningsexempel_2a
Template/mallen akutmall_undervisningsexempel_2a är en förenklad (inte helt realtistisk) delmängd av saker som kan vara inressanta vid akut omhändertagande av vissa skador. 
Den är utformad för att visa olika användbara egenskaper hos modeller baserade på en kombination av openEHR och Snomed CT.

## Förberedelser
1. Skapa användare på Github och i Archetype Designer enligt instruktioner i de två första lathundarna på https://openehr.atlassian.net/wiki/spaces/healthmod/pages/966295553/Snabbstartsguide+f+r+modelleringsverktyg
1. Om du inte redan är inloggad i Archetype Designer följ tredje lathunden (om inloggning)
1. För att riskfritt kunna experimentera och spara, skapa ett eget repository lokalt på servern genom att:
    * Klicka på gröna knappen "+ New repository"
    * Välj: Repository type = Local Folder
    * Hitta på valftitt namn och fyll i under "Repository name"
1. Ladda ner exempelfilerna för kursen från det här GitHub-projektet genom att klicka på https://github.com/modellbibliotek/kurs-openEHR-jan-2021/archive/main.zip
1. Packa (i valfritt bibliotek på in dator) upp zip-filen 
1. Klicka på "Import" längst upp i archetype designer. Då visas en dialog som har bl.a. har en ruta med texten "Drop here"; dra dit och släpp av filerna du packade upp i förra steget. Klicka sedan en gröna knappen "Upload all" och när allt sedan laddats upp, klicka då close.
1. Nu kan du öppna akutmall_undervisningsexempel_2a eller de ingående arketyperna

## Valfria extrasteg senare:
1. Följ den fjärde lathunden `Koppla Archetype Designer till arbetsytan på GitHub` 
1. Om du vill koppla in fler repositories upprepa lathund 4 med olika innehåll i "Repository". CKM-mirror kan t.ex. vara kul att koppla in och utforska, men tar en del tid att ladda in med sina över 500 arketyper.
1. Skicka ett mail till asa.skagerhult@regionostergotland.se och erik.sundvall@regionostergotland.se där du berättar ditt GitHub-användarnamn (men _inte_ ditt lösenord) om du vill kunna spara (inte bara läsa) i repository/arbetsytor som använs i nationellt samarbete.
