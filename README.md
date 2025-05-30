# Min kodplugg till Anytone AT-D168UV

## Copyright

© 2019-2024 by SM0RUX Pontus Falk och SM0RGM Stefan Helander

Filerna är tillgängliga under [GPLv3](https://github.com/sm0rux/at-d878uv/blob/master/LICENSE).

## Uppdatering av SM0RGM 

På grund av att Pontus SM0RUX av personliga skäl inte har möjlighet att uppdatera kodpluggen så har han och jag kommit överens om att jag övertar och uppdaterar kodpluggen. Kodpluggen är och förblir därmed "SM0RUX kodplugg" men underhållen av mig. Jag har skapat en fork av kodpluggarna och publicerat under mitt eget Github-konto och ändrat kontaktytorna i dessa filer, så kommentarer, ändringar och liknande lägger du som en issue på min Github eller kontaktar mig.

Även om man försöker vara minutiöst noggrann så kan det smyga sig in fel. Kodpluggen innehåller i denna version runt 600 kanaler. Så hittar du något fel eller har andra synpunkter, lägga gärna en issue eller skicka ett mail. 

Nacka februari 2024
SM0RGM Stefan Helander

## Syfte

Det här är min kodplugg till min Anytone AT-D168UV. Den är inte testad med AT-D168UV då jag inte äger en sådan, så testa och rapportera gärna ev problem helst via en Issue. Jag använder CPS version 1.06 och firmware 1.06. Huvudsyftet med publiceringen av filerna här på GitHub är att förenkla för mig själv när det gäller uppdateringar. Jag har inget emot att dela med mig av filerna så att andra kan nyttja dem under förutsättning att de som återanvänder mina filer följer licensvillkoren i [GPLv3](https://github.com/sm0rux/at-d878uv/blob/master/LICENSE).

Om du vill bidra med något så är du naturligtvis välkommen att göra så antingen genom att skapa en Pull Request (kräver en del kunskap om hur GitHub funkar) eller genom att skapa ett [issue](https://github.com/sm0rgm/at-d168uv/issues).

## Vad ingår i filerna?

Alla repeatrar i Sverige som kan köra DMR eller FM är inkluderade (källa: [sk6ba.se](https://sk6ba.se/repeater/karta/)). Även repeatrar som kör exempelvis C4FM och FM finns med. Repeatrarna är indelade distriksvis. Tyvärr finns det så många repeatrar i sjätte och sjunde distrikten att alla inte får plats i scanning-listan.

DMR-repeatrarna är också indelade i roaming-zoner för att få roamingen att funka på ett smidigt sätt.

## Fungerar kodpluggen till Anytone AT-D868UV också?

Jag har själv ingen 868 att prova med men har laddat ner CPS till 868 och provat att ladda in kodpluggen. 868 saknar ju stöd för bl a roaming så de filerna ger felmeddelande. Därför har jag skapat en LIST-fil som heter 868.LST som kan användas för 868. Det verkar vara mindre skillnader i filformatet men resultatet ser ut att vara en fungerande kodplugg även till 868 (återkoppla gärna med rapport till [mig](mailto:stefan@helander.se) om du lyckas använda filerna till 868).

När du läst in filerna i CPS:en till 868 bör du stega igenom zonerna och scanlistorna en gång (öppna den första och klicka next) så ordnar A-channel och B-channel till sig och ställer sig på kaneler i zonen (efter import står alla på pi-star). I scanlistorna så rättar alla parametrar till sig eftersom de står på 0 efter import. OBS att det bara är på 868 detta handgrepp behövs.

Har du en befintlig kodplugg i din 868 och bara vill uppdatera kanalerna så läser du inte in alla filerna via importlistan utan väljer manuellt vilka filer du vill importera, se nedan om uppdatering.

## Boot logo

Bland filerna i kodpluggen finner du filen SSA.jpg. Det är SSAs logotype som kan användas som startbild. Gör så här:

* I CPS, gå till Tool -> Boot image (när radion är ansluten till datorn)
* Klicka på Open Image och välj filen SSA.jpg
* Logon ska ny synas i bildfönstret, annars är något fel
* Klicka på Write
* Gå till Optional Setting -> Power on -> Power-on interface -> Custom picture
* Spara ändringarna till radion

## Digitala kontaktlistan

Den digitala kontaktlistan innehåller call från SM/LA/OH/OZ för att få ner storleken på den så att den med säkerhet får plats i alla modeller av Anytone. Vill du ha en kontaktlista med fler länder kan du skapa ett konto på [radioid.net](https://radioid.net) och generera kontaklistor med exakt de länder du vill ha med.

## Suffix i repeaternamn

För att indikera typ av repeater eller vilket nätverk den är ansluten mot finns numera en eller flera bokstäver som suffix till repeaterns namn. Om repeatern är ansluten till Brandmeister för DMR eller är en lokal FM-repeater utan anslutning till reflektornätverk finns ingen bokstav angiven. Bokstäverna betyder:

L = Link (simplex)
A = AllstarLink
S = SVXlink
E = EchoLink
H = Hotspot (DMR)
F = FreeDMR / FinDMR
+ = DMR+ / DMR Plus
I = IRLP / ircDDB
P = HAMphone

## APRS ISS

Från och med 2025-05-04 finns en simplexkanal med namnet "APRS ISS" för mottagning av APRS från ISS. APRS-frekvens nr 8 för sändning är satt till 145.825 MHz för att kunna sända APRS via ISS.

Obs! För att sända APRS via ISS måste du ändra digipath till:
ARISS,WIDE2-1

Se denna [artikel av K7KEZ](https://k7kez.com/aprs-settings-for-the-iss-international-space-station/) om hur man kör APRS via ISS.

## Vad du måste göra!

### Vilka filer ska du hämta?

Jag rekommenderar att du hämtar filerna som jag har packat ihop i en [release](https://github.com/sm0rgm/at-d168uv/releases) istället för att hämta mina arbetsfiler!

### När filerna är hämtade... 

CSV-filerna kan du använda om du har en befintlig radio eller kodplugg som du vill uppdatera med kanaler, zoner, scalistor etc. 

Om du snabbt och enkelt vill starta en ny kodplugg eller koda upp en ny radio så finns det en färdig fil med alla inställningar gjorda som heter N0CALL.rdt. Filen N0CALL.rdt är sparad i MODE 0003 Amateur EU, d v s så som radion kommer "out of the box". Har du öppnat TX genom att byta mode kan denna RDT-fil inte användas. 
Starta CPS-programmet och välj Öppna fil och välj N0CALL.rdt. Gå till fliken APRS och ändra Your call från N0CALL till ditt call. Gå till Digital -> Master Id och ändra Master ID till ditt DMR ID respektive Master ID Name till ditt callsign i klartext och namn. Gå sedan till Digital -> Radio ID List och ändra Radio ID och Name till ditt DMR ID respektive callsign och namn. Sedan är det bara att skjuta i kodpluggen i radion (välj COM-port och sedan Write to radio).

OBS! Den kompletta rdt-filen är bara kompatibel med den version av CPS den är gjord med eller senare versioner. Har du en tidigare version av CPS och firmware så behöver du antingen uppdatera radion först eller använda CSV-filerna. Vilken version av CPS/Firmware rdt-filen är gjord för framgår av filen CHANGELOG.md.

Om du istället vill använda mina CSV-filer så behöver du i princip bara ändra DMR-ID i RadioIDList.CSV och APRS-inställningarna i APRS.CSV - sedan är det bara att tuta och köra.

Förmodligen vill du ändra på fler saker, men det överlåter jag till dig att fixa med själv.

### Uppdatera befintlig kodplugg

Om du bara vill uppdatera din radio med kanaler, scanlistor, roaming och zoner men låta resterande inställning vara som de är kan du, istället för att importera hela N0CALL.LST välja att enbart importera filerna för Channel, ScanList, RoamingChannels, RoamingZone, Zone, TalkGroups och ReceiveGroupCallList. 

## SM0RUX/Pontus silent key

Den 9 mars 2025 gick SM0RUX/Pontus silent key efter några års kamp mot cancern. Kodpluggen är och förblir "SM0RUX kodplugg" men underhålls fortsatt av mig, SM0RGM/Stefan. Kodpluggen är gratis att använda men vill du ge ett bidrag så tänk gärna på Cancerfonden tel. 010-199 10 10.

73's de SM0RGM Stefan

2025-05-04
