# IP-adresser og brug i Danmark

Dette dokument er oprindeligt skrevet af cand.scient Henrik Lund Kramshøj, hlk@zencurity.com i sommeren 2019.

Dokumentet er tiltænkt brug af advokater i retsager i Danmark og indeholder informationer om internet-termer som IP-adresse, router, protokoller m.v. Projektet er foregået i samarbejde med Dan M. Dahl Rahimian fra Advokagruppen.dk

Beskrivelsen tager udgangspunkt i mangeårig og detaljeret baggrundsviden om hvordan internet og it-sikkerhed indenfor samme fungerer.

Alle må komme med input til dette dokument og det er hermed publiceret under en åben licens som tillader deling og videre forarbejdning af dokumentet kommercielt og ikke-kommercielt.

## Forfatterens baggrund

Mit navn er Henrik Lund Kramshøj, uddannet cand.scient fra Datalogisk Institut ved Københavns Universitet (DIKU). Jeg har siden start 1990erne arbejdet med internetteknologier og opnået ekspertviden indenfor netværk og it-sikkerhed.

Jeg er certificeret CISSP siden 2003 og tidligere haft certificeringer som CEH, Juniper  Service Provider Routing and Switching, Specialist (JNCIS-SP) (udløb 2019) m.fl.

Jeg har arbejdet professionelt med it-sikkerhed og netværk siden midt 1990erne.


# Internet

Internet er allestedsnærværende og mange danskere har idag smart phones og andre enheder som benytter internet mange gange dagligt.

Ordets oprindelse findes i internetworking, som er en beskrivelse af den logiske opbygning, kommunikation mellem netværk. Et internet er således et netværk af netværk. Det store verdensomspændende Internet skrives indimellem med stort forbogstav for at skelne mellem et generelt internet og Internet.

Det specielle ved Internet er at ingen entitet ejer dette. Internet kan ses som et løst samarbejde mellem netværksoperatører som på tværs af landegrænser. Ud fra relativt simple kontrakter aftales samarbejde om at overholde visse spilleregler. Primært aftales at der udveksles og videresendes traffik på lige fod, også kaldet netneutralitet. Dette område gennemgås ikke.

Der er derfor ingen enkelt organisation som kontrollerer internet, kan lukke for dele, eller tvinge deltagende netværk til at følge bestemte regler.

På dette Internet benyttes TCP/IP som er forkortelse for IP-protokollerne, som er standarder for pakke-baseret elektronisk kommunikation som deltagende netværk forventes at overholde. Forkortelsen indeholder ligeledes en af de mest benyttede, TCP. Denne protokol benyttes blandt andet til email, browsing og andre formål. På de laveste niveauer, tæt på hardware sendes data som pakker, der kan sammenlignes med postkort. De sendes med modtager og afsender, og overholder et simpelt format.

Der kan læses mere om disse protokoller på eksempelvis Wikipedia: https://en.wikipedia.org/wiki/Internet_protocol_suite


## IP-adresser

Et centralt koncept i Internetkommunikation er at der kommunikeres mellem IP-adresser. Ligesom en telefonsamtale mellem to personer er der oftes kommunikation mellem to computere, ofte kaldes klient og server.

Når klienten skal kommunikere med serveren ved brug af TCP/IP benyttes IP-adresse som endepunktet for kommunikationen.

Konkret er IP-adresser et 32-bit tal, som har en værdi mellem 1 og 4294967296, men som oftest skrives de som oktetter med punktum imellem.

Eksempler på IP-adreser er

* 127.0.0.1 en speciel adresse som findes på alle computere. Det tillader eksempelvis webudvikling på en lokal bærbar computer hvor klient og server er på samme adresse

* 192.168.1.1 en meget brugt privat adresse hos forbrugere. Den lokale router som skaber adgang til internet har denne adresse. Klienter indenfor netværket har derefter adresser som 192.168.1.10, 192.168.1.123.

* 192.0.2.1 - 192.0.2.255 er specielle adresser som kan benyttes til dokumentation. Det anbefales at man altid og udelukkende benytter sådanne *documentation prefixes* når man skriver eksempler i generelle dokumenter. Specielt bør man ikke blot tage en adresse tilfældigt da man derved kan komme til at pege på en organisation som idag benytter disse adresser på Internet.

Private og offentlige adresser er to begreber som bruges om IP-adresser. En offentlig IP-adresse kan bruges på Internet, hvor netværksoperatører sørger for at pakker med en offentlig modtageradresse fremsendes i retning af netværksdestinationen.

En pakke vil typisk krydse flere netværk, mindst to, men oftere 3-5 og indimellem op til 10 - uden at der er en øvre grænse.

I de netværk der sendes fra og de netværk der modtages vil man ofte benytte en oversættelse mellem de offentlige IP-adresser og interne - private - adresser. De private adresser benyttes grundet en generel mangel på IP-adresser.

En analogi for offentlige og private IP-adresser kan være telefoncentraler med lokalnumre. Indenfor et hus kan ringes med kort lokalnummer, men skal der ringes ud af huset sker det med vores sædvanlige 8-cifrede telefonnumre.

Det bemærkes at kommunikation på internet udelukkende benytter IP-adresserne til kommunikationen. Protokoller i lag ovenfor som eksempelvis HTTP der benytes til hjemmesider skal derfor have oversat navne til IP-adresser inden kommunikationen kan begynde.

En internet kommunikation kan således opsummeret foregå på følgende måde:

En bruger der vil besøge Folketingets hjemmeside http://www.ft.dk vil forårsage følgende, opsummeret og forsimplet:

1. Indtastningen af adressen **www.ft.dk** i en browser
2. Klientens software beder om adressen bagved navnet www.ft.dk hos en navneserver lokalt, enten på samme computer eller hos internetudbyderen
3. Navneserversoftware vil gennem en rekursiv process finde informationer om andre navneserver i dette hierarki .dk, ft.dk og til sidst vil der blive forspurgt på navnet www.ft.dk
4. Svaret på dette opslag sendes til klienten, www.ft.dk har addressen **152.115.53.69**
5. Web browseren vil åbne en TCP forbindelse mellem egen adresse eksempelvis 192.168.1.22 ud til hjemmesiden på adressen 152.115.53.69. Derved sendes data gennem den lokale router 192.168.1.1
6. Hjemmesiden modtages i et antal IP-pakker og vises på skærmen

Bemærkninger.
Da klienten har en privat adresse som ikke kan benyttes på Internet vil den lokale router erstatte afsenderadressen med sin egen offentlige adresse. Det kunne være 185.129.62.2 Denne process kaldes for Network Adress Translation (NAT) og benyttes af langt de fleste internetudbydere i Danmark.

## IP-adresse opsummeret

1.  Hvad er en IP-adresse. En IP-adresse er et nummer som bruges som afsender og modtager på IP-pakker, data der sendes over Internet. Det skrives oftest med punktum eksempelvis som 192.0.2.1. Al kommunikation på internet er mellem IP-adresse. Navne oversættes til IP-adresser med navnesystemet (Domain Name System (DNS).


2.  Hvad kan udledes af en IP-adresse. IP-adresser registreres centralt og tildeles til brugere af internetudbydere. Dette sker via 5 Regional Internet Registries (RIRs). Ud fra en IP-adresse kan man i Whois databaser slå op hvilket netværk der har lov til at benytte denne. NB: Der foregår ofte afsendelse af data med forfalskede afsenderadresser, eksempelvis ifb DDoS angreb.
  De data der kan slås op i Whois systemet indeholder bl.a: netværksnavnet, kontaktinformationer på organisationen, herunder hjemmehørende land.

3.  Vil man kunne se hvilket elektronisk udstyr, hvilken person eller hvor dette geografisk har befundet sig.
Mange data om computere og internet er flygtige, og det vil sjældent være muligt efterfølgende at finde informationerne og udtale konkrete konklusioner. Hvis man under en efterforskning straks slår op vil det være muligt med nogen usikkerhed at sige hvilken vej gennem netværk der er benyttet.
Hvis man har rådata vil man indimellem kunne udtale mere konkret hvilken type operativsystem eller producent der formentlig er benyttet.

4.  Hvad vil man reelt kunne udlede af programmer som opsnapper IP-adresser i P2P netværk. I torrentsammenhæng virker protokollerne ved at klienterne fortæller at de tilbyder data - filer - til netværket. Disse informationer skal andre klienter modtage og det vil derfor være en indikation at der er en torrentklient som er villig til at udsende de data.
Såfremt man kun opsamler trackinginformationen vil det ikke være givet at data findes, kun ved en opsamling af data - download - eller dele af data vil det være muligt at konkludere hvilke data der var tilgængelige.


5.  Hvad ville ske, hvis en person som har et P2P program på computeren og enten bevidst/ubevidst logger på en internetforbindelse
Hvis man har et P2P program installeret og forbinder til et netværk vil programmet begynde at kommunikere med delingsnetværket. Dette sker på samme måde som emailprogrammer der med mellemrum checker for ny post, programmer der spørger efter opdateringer, hjemmesider der forbinder til servere i baggrunden, chatfunktioner som melder sig online osv.

6.  Hvordan foregår delingen i et P2P netværk?. Peer-to-peer er et begreb man benytter om kommunikation mellem klienter, hvor disse også fungerer som servere. Et peer-to-peer program kan således kommunikere med et andet af samme type, og både sende og modtage data. Metoden er mere effektiv end centraliseret server arkitektur, idet en central server med data kun kan understøtte et vist antal klienter, hvor en peer-to-peer arkitektur skalerer med antallet af klienter der tilbyder data.

En af de mest populære teknologier indenfor peer-to-peer er BitTorrent som benytter en tracker struktur. Denne tracker er en server som assisterer klienterne i at finde hinanden og de ønskede data. Klienter som vil downloade vil således først kommunikere deres eksistens til trackeren, og der få viden om andre klienter - hvorefter kommunikationen og data går direkte mellem klienterne.

Kilder
https://en.wikipedia.org/wiki/Peer-to-peer
https://en.wikipedia.org/wiki/BitTorrent
https://en.wikipedia.org/wiki/BitTorrent_tracker

7.  Hvad er Swarmsize, se kolonne P i vedlagte pdf bilag 7.

Swarm er et begreb der bruges om de peers der indgår i delingen af en bestemt torrent, en eller flere filer. Hvis der således er 10 klienter som har dele af data, eller er ved at hente data, vil swarm size være 10. NB: processen med deling af data via torrent er meget dynamisk og dette tal vil derfor være behæftet med en vis usikkerhed.


## Wifi-forbindelse

De fleste private i Danmark har idag håndholdte enheder og bærbare computere der forbinder til Internet via trådløse teknologier, populært kaldet Wi-Fi. Denne forbindelse etableres gennem en trådløs router som udleveres af internetudbydere, uden mulighed for at udskifte denne.

Sikkerheden på trådløse netværk hos private er typisk en af følgende

* Ingen sikkerhed, åbent trådløst netværk. Dette ses også hos mange konferencecentre, barer, cafeer m.fl. Det er ikke i Danmark ulovligt at have et åbent netværk som andre kan benytte.
* WEP En ældre krypteringsstandard som betragtes som værende usikker. Den kan brydes i praksis på sekunder og anbefales derfor ikke.
* WPA og WPA2 Personal. Krypteringsmetoder hvor der benyttes et kodeord til det trådløse netværk. Koden er ofte tildelt af internetudbyderen, men kan ændres og bliver det ofte for at lette adgangen til netværket for familie og venner. Det anbefales at benytte den opdaterede WPA version 2.

Hos virksomheder vil en mere avanceret WPA Enterprise benyttes som giver individuel autentificering.


1.  Hvordan er mulighederne for at bryde et kodeord for en WIFI forbindelse med WPA2?
Sikkerheden afhænger primært af kodeordets styrke, så et kortere kodeord vil være nemmere at knække. De kodeord som genereres af internetudbydere er idag ofte omkring 10 tegn, men kun bogstaver og tal - for at undgå en større supportbyrde. De kodeord som indtastes af privatpersoner må antages at være af ringere kvalitet.

Samtidig skiftes WPA kodeord yderst sjældent og der vil derfor typisk være adgang i længere tid, måneder til år, såfremt et kodeord gættes.

Der findes værktøjer som benytter grafikkort til at forsøge at knække WPA koder, og disse vil



2.  Er du bekendt med nogle sikkerhedsbrister for WPA2?

Der har været akademiske problemer i WPA2, men det mest praktiske angreb er til teknologien Wi-Fi Protected Setup (WPS) som benyttes til at lette adgang for brugerne til netværket. Teknologien blev introduceret omkring 2006 og er idag stadig aktiv mange steder, grundet manglende opdatering af software på hjemmeroutere.

Denne teknologi har haft alvorlige sikkerhedsbrister som gør at WPA koden til netværket kunne findes på 4-10 timer såfremt denne teknologi er aktiveret. Idag indeholder routersoftware ofte tiltag der forsinker angrebet, men det er stadig muligt - idet antallet af forsøg på tilkobling *kun er ca. 11.000 forsøg*

Et værktøj til at udnytte dette hedder Reaver og kan benyttes af enhver med meget lidt træning.

Eksempel artikel
https://www.pwnieexpress.com/blog/wps-cracking-with-reaver

3.  Hvordan vil en privatperson kunne beskytte sig fuldstændig mod uautoriseret adgang til ens WIFI forbindelse?
En privatperson vil have svært ved at beskytte imod uautoriseret adgang, idet beskyttelsen ofte vil kræve højere vidensniveau og kontinuerlig overvågning.

Samtidig benyttes trådløse netværk ofte af andre, herunder gæster.

Koden til netværket er ofte angivet under routeren, så blot kort tid vil give mulighed for at aflæse denne.

Koder er samtidig gemt på enheder som kan være udsat for hacking. Mange koder som internetbrugere er ligeledes lækket på Internet i store databaser.


4.  Hvor langt væk vil du vurdere en standard router vil kunne tilgås fra?
Jeg vil vurdere at en standard router ville kunne nås fra en afstand af mindst 50-100m med en god retningsbestemt antenne.

De fysiske forhold gør at dette er behæftet med stor usikkerhed. I et villaområdet med enkeltfamilienhuse vil det kunne være over 100m, mens etageejendomme med mange trådløse netværk gør det besværligere at kommunikere med et af disse over større afstand.

I en etageejendom vil det derfor ofte være nemmere at få signal fra en genbo som kan ses fra altanen, end to etager over eller under.

Kilder til mere information:
https://en.wikipedia.org/wiki/Wi-Fi

## Hacking af internetadgang

Andre måder at få tilgang til IP-adresse på

1.  Vil du beskrive hvad Malware er, herunder hvordan man kan få dem?
2.  Vil du beskrive hvad et router angreb er?
3.  Vil du beskrive om der findes andre måder, at kunne få adgang til at benytte IP-adressen? (Malware og router angreb)
4.  Hvor sandsygt vil du sige det er, at almindelige private har computere, som er inficerede af Malware?
5.  Findes der nogen statistikker på hvor mange computere som enten er eller potentielt kan være inficeret af malware eller lignende?


Derudover er vi åbne for, at du giver eventuelle andre tekniske inputs eller hvis du hellere skulle have lyst til at være med som vidne gennem telefonen.

Jeg har vedlagt nogle af de tekniske udtalelser som modparten har sendt.
Hvis du har nogle bemærkninger til dem må du endelig sige til.

Nok engang tak for hjælpen både af mig og forbrugerne!
