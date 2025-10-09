# Helpconnect projekt terv

## Projektleírás
HelpConnect célja, hogy digitális platformot biztosítson civil szervezetek számára, ahol bemutathatják tevékenységeiket és közzétehetik aktuális eseményeiket. A rendszer lehetővé teszi, hogy például egy szervezet egy jótékonysági ételosztást vagy egyéb eseményt rögzítsen, amelyre a felhasználók online jelentkezhetnek és részt vehetnek.

A platform nem csupán események gyűjtőhelyeként szolgál, hanem átfogó adatbázist kínál a civil szervezetekről is. Minden szervezethez részletes profil tartozik, amely tartalmazza tevékenységi körét, az aktív tagok számát, valamint a felhasználók által adott értékeléseket és visszajelzéseket.

A felhasználói profilok szintén fontos szerepet kapnak: megjelenítik, hogy a felhasználó mely szervezeteknél vett részt önkéntes tevékenységben, valamint különböző jelvényekkel (badge-ekkel) ismerik el az aktivitását. Emellett a profilok tartalmazhatják a felhasználó szakmai hátterét is – például ha valaki pszichológus végzettséggel rendelkezik, ezt a rendszer feltünteti, így az ilyen kompetenciát igénylő szervezetek könnyebben kapcsolatba léphetnek vele.

A HelpConnect így egy modern, közösségépítő felületként szolgál, amely támogatja az önkéntesek és civil szervezetek közötti hatékonyabb együttműködést, és hozzájárul a társadalmi felelősségvállalás előmozdításához.

## Funkciók
* Eseményszervezési lehetőség civil szervezetek számára
* Regisztrált civil szervezetek listázása(kis leírás róluk, vélemények,        egyszerű fórum, bankszámlaszám, stb)
* Eseményekre való jelentkezés lehetősége önkéntesek számára
* Szűrési feltételek biztosítása az önkénteseknek(pl. 50 órás közösségi szolgálat)
* Önkéntes jelvények(melyeket az eseményeken való részvétel után kaphat a felhasználó)
* Legaktívabb önkéntesek megjelenítése a szervezet oldalán
* A civil szervezet oldalán megjelennek a már véget ért események is, ahol arról véleményeket és képeket tud közölni a szervezet és az önkéntes is
* Emlékeztetőt kapnának email-ben az önkéntesek a közelgő eseményről
* Esemény státusza: Függőben, megtelt, lezárult
* Önkéntes adatlap: név, profilkép, város, érdeklődési körök, tapasztalat/részvételi előzmények, képesítés, végzettség feltüntetése

## Komponensek
### Bejelntkezés nélkül látható komponensek
Amikor a civil szervezet és a felhasználó belép, úgy hogy még nincs bejelentkezve, ezeket fogja látni :

* homeComponent - (Kezdőképernyő, ez jelenik meg ha a felhasználó belép)
Tartalmazza : Weboldal alapvető bemutatása, bejelntkezési menüsáv.

* userLoginComponent - felhasználóknak.
A felhasználó bejelntkezik a weboldalra. Ez csak a felhasználóra (önkéntesre) vonatkozik.

* organizationLoginComponent -
A civil szervezet bejelentkezik a weboldalra. Ez csak a szervezetre vonatkozik.

* eventsComponent -
Megszervezett események összegyűjtve.
Láthatja a felhasználó is, és a civil szervezet is. Ez itt csak összegyűjti az eseményeket, aztán ha a felhasználó kiválaszt egy konkrét eseményt akkor -> eventDetailsComponent

* eventDetailsComponent -
Egy konkrét esemény részletes oldala.
Tartalmazza: Leírás, időpont, helyszín, kapcsolattartó.
Résztvevők száma / limit.
Szervező neve + link a szervezet profiljára.
Jelentkezés gomb (ha van még hely).
Ha nem vagy bejelentkezve, akkor nem tudsz jelentkezni az eseményre. Ha be vagy jelentkezve, akkor tudsz rá jelentkezni önkéntesként (tehát felhasználóként).

* organizationListComponent - 
A civil szervezetek listája. Innen fog majd az adott szervezet konkrét adatlapjára vezetni ->

* organizationDetailsComponent -
Egy civil szervezet adatlapja, amit az önkéntes megtekinthet :
Logó, leírás, elérhetőségek, bankszámlaszám.
Tevékenységi kör, célok.
Aktív események listája.
Lezárult események, és vélemények.
Értékelések és kommentek más önkéntesektől.
„Érdekel” gomb (értesítések új eseményekről).
Megjelenített statisztikák: aktív tagok száma, átlagos értékelés.

* contactUsComponent - 
Ügyfélszolgálatunk. Hibák, fennakadások esetén.

* forumsComponent
A különböző szervezetek fórumai(bejelentkezés nélkül lehet látni, de írni nem lehet)



### Bejelentkezéssel látható komponensek

#### Civil szervezeteknek

* createEventComponent - 
A szervezetnek itt tud létrehozni eseményeket.

* myEventsForOrganizationComponent -
Saját már lezárult és aktív eseményeinek listája. Itt szerkeszteni is tudja a
még szervezés alatt álló eseményeit. Egyszerűbb statisztikák megjelenítése.

* volunteerListComponent - 
A már korábban valamilyen eseményen résztvett önkéntesek listája, aktivitási
adatokkal feltöltve.

* volunteerFeedbackComponent – az esemény után a szervezet értékelheti az önkéntes munkáját (pl. aktivitás, megbízhatóság, együttműködés). Csilagokkal tudja majd értékelni az önkéntes 
munkáját.

* organizationProfileComponent – a szervezet adatlapjának megtekintése és szerkesztése (leírás, logó, bankszámlaszám, elérhetőségek, kategória stb.).

* organizationNotificationsComponent – rendszerértesítések kezelése (új jelentkezés, visszajelzés, eseményemlékeztetők). Ha pl. a felhasználók jelentkeznek egy eseményre, itt 
ebben az értesítésiközpontban lesznek összegyűjtve.

#### Önkénteseknek

* volunteerProfileComponent - 
A felhasználó saját profilja. Tartalmazza a profilképét, nevét, városát, rövid bemutatkozását, érdeklődési köreit, végzettségét/végzettségeit (szkamai hátterét), tapasztalatát (részvételi előzményeket), megszerzett jelvényeket az önkénteskedései során, értékelések amelyeket a szervezetektől kapott. A felhasználó szerkeztheti a saját adatait. 

* myEventsForUserComponent -
Az önkéntes által követett vagy jelentkezett események listája. Megkülönböztetve: Aktív események.
Lezárult események (itt lehet visszajelzést írni a szervezetről)
Esemény státuszai (Függőben / Megtelt / Lezárult) vizuálisan is megjelennek.
Lehetőség lemondani a részvételt, ha az esemény még nem kezdődött el.

* volunteerNotificationsComponent -
Rendszerértesítések a felhasználó számára. Emlékeztető közelgő eseményről.
Szervezet visszajelzése az önkéntes munkáról.
Új ajánlott esemény vagy szervezet megjelenése.

* volunteerFeedbackComponent -
Az önkéntes visszajelzést adhat egy lezárult eseményről vagy szervezetről.
Lehetőségek:
1–5 csillagos értékelés
Szöveges vélemény megadása
Képfeltöltés (pl. eseményfotó)
A visszajelzés megjelenik a szervezet oldalán.

* forumInteractionComponent -
Az önkéntes bejelentkezés után hozzászólhat a fórumhoz.
Lehetőség:
Kommentelés, kérdésfeltevés szervezetekhez.
Saját kommentek törlése.






