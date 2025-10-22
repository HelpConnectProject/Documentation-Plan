# Helpconnect projekt terv

## Projektleírás
HelpConnect célja, hogy digitális platformot biztosítson civil szervezetek számára, ahol bemutathatják tevékenységeiket és közzétehetik aktuális eseményeiket. A rendszer lehetővé teszi, hogy például egy szervezet egy jótékonysági ételosztást vagy egyéb eseményt rögzítsen, amelyre a felhasználók online jelentkezhetnek és részt vehetnek.

A platform nem csupán események gyűjtőhelyeként szolgál, hanem átfogó adatbázist kínál a civil szervezetekről is. Minden szervezethez részletes profil tartozik, amely tartalmazza tevékenységi körét, az aktív tagok számát, valamint a felhasználók által adott értékeléseket és visszajelzéseket.

A felhasználói profilok szintén fontos szerepet kapnak: megjelenítik, hogy a felhasználó mely szervezeteknél vett részt önkéntes tevékenységben. Emellett a profilok tartalmazhatják a felhasználó szakmai hátterét is – például ha valaki pszichológus végzettséggel rendelkezik, ezt a rendszer feltünteti, így az ilyen kompetenciát igénylő szervezetek könnyebben kapcsolatba léphetnek vele.

A HelpConnect így egy modern, közösségépítő felületként szolgál, amely támogatja az önkéntesek és civil szervezetek közötti hatékonyabb együttműködést, és hozzájárul a társadalmi felelősségvállalás előmozdításához.

Frontend : Angular;

Backend : Laravel;

Adatbázis : MySql;


## Weboldal kinézetének megtekintése
Github link: https://github.com/HelpConnectProject/Frontend.git

## Funkciók
* Eseményszervezési lehetőség civil szervezetek számára
* Regisztrált civil szervezetek listázása(kis leírás róluk, vélemények, bankszámlaszám, stb)
* Eseményekre való jelentkezés lehetősége önkéntesek számára
* Szűrési feltételek biztosítása az önkénteseknek(pl. 50 órás közösségi szolgálat)
* Legaktívabb önkéntesek megjelenítése a szervezet oldalán
* A civil szervezet oldalán megjelennek a már véget ért események is, ahol arról véleményeket és képeket tud közölni a szervezet és az önkéntes is
* Esemény státusza: Függőben, megtelt, lezárult
* Önkéntes adatlap: név, profilkép, város, érdeklődési körök, tapasztalat/részvételi előzmények, képesítés, végzettség feltüntetése

## Komponensek
### Bejelntkezés nélkül látható komponensek
Amikor a civil szervezet és a felhasználó belép, úgy hogy még nincs bejelentkezve, ezeket fogja látni :

* homeComponent - (Kezdőképernyő, ez jelenik meg ha a felhasználó belép)
Tartalmazza : Weboldal alapvető bemutatása, bejelntkezési menüsáv.

* navbarComponent - Navigációs menüsáv

* loginComponent - Belépés felhasználók és civil szervezetek számára.

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


#### Önkénteseknek

* volunteerProfileComponent - 
A felhasználó saját profilja. Tartalmazza a profilképét, nevét, városát, rövid bemutatkozását, érdeklődési köreit, végzettségét/végzettségeit (szakamai hátterét), tapasztalatát (részvételi előzményeket), megszerzett jelvényeket az önkénteskedései során, értékelések amelyeket a szervezetektől kapott. A felhasználó szerkeztheti a saját adatait. 

* myEventsForUserComponent -
Az önkéntes által követett vagy jelentkezett események listája. Megkülönböztetve: Aktív események.
Lezárult események (itt lehet visszajelzést írni a szervezetről)
Esemény státuszai (Függőben / Megtelt / Lezárult) vizuálisan is megjelennek.
Lehetőség lemondani a részvételt, ha az esemény még nem kezdődött el.

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

## Adatbázis terv

#### 1. users (önkéntes felhasználók)

| Oszlop         | Típus                | Megjegyzés                     |
| -------------- | -------------------- | ------------------------------ |
| id             | INT (PK, AI)         | Felhasználó azonosító          |
| name           | VARCHAR(100)         | Név                            |
| email          | VARCHAR(150), UNIQUE | E-mail                         |
| password       | VARCHAR(255)         | Titkosított jelszó             |
| city           | VARCHAR(100)         | Város                          |
| about          | TEXT                 | Rövid bemutatkozás             |
| interests      | TEXT                 | Érdeklődési körök              |
| qualification  | VARCHAR(255)         | Végzettség(ek)                 |
| experience     | TEXT                 | Tapasztalat, korábbi részvétel |
| profile\_image | VARCHAR(255)         | Profilkép elérési útja         |
| created\_at    | TIMESTAMP            |                                |
| updated\_at    | TIMESTAMP            |                                |

#### 2. organizations

| Oszlop          | Típus                | Megjegyzés                |
| --------------- | -------------------- | ------------------------- |
| id              | INT (PK, AI)         | Szervezet azonosító       |
| name            | VARCHAR(150)         | Szervezet neve            |
| email           | VARCHAR(150), UNIQUE | Bejelentkezéshez          |
| password        | VARCHAR(255)         | Jelszó                    |
| description     | TEXT                 | Rövid leírás              |
| logo            | VARCHAR(255)         | Logó képfájl elérési útja |
| category        | VARCHAR(100)         | Tevékenységi kör          |
| phone           | VARCHAR(50)          | Telefonszám               |
| address         | VARCHAR(255)         | Székhely                  |
| bank\_account   | VARCHAR(255)         | Bankszámlaszám            |
| active\_members | INT                  | Aktív tagok száma         |
| avg\_rating     | FLOAT                | Átlagos értékelés         |
| created\_at     | TIMESTAMP            |                           |
| updated\_at     | TIMESTAMP            |                           |

#### 3. events

| Oszlop           | Típus                                   | Megjegyzés        |
| ---------------- | --------------------------------------- | ----------------- |
| id               | INT (PK, AI)                            | Esemény azonosító |
| organization\_id | INT (FK → organizations.id)             | Szervező          |
| title            | VARCHAR(255)                            | Esemény címe      |
| description      | TEXT                                    | Leírás            |
| location         | VARCHAR(255)                            | Helyszín          |
| date             | DATETIME                                | Időpont           |
| status           | ENUM('Függőben', 'Megtelt', 'Lezárult') | Állapot           |
| capacity         | INT                                     | Maximális létszám |
| created\_at      | TIMESTAMP                               |                   |
| updated\_at      | TIMESTAMP                               |                   |

#### 4. event_registrations

| Oszlop         | Típus                                     | Megjegyzés             |
| -------------- | ----------------------------------------- | ---------------------- |
| id             | INT (PK, AI)                              | Regisztráció azonosító |
| user\_id       | INT (FK → users.id)                       | Jelentkező             |
| event\_id      | INT (FK → events.id)                      | Cél esemény            |
| status         | ENUM('Függőben', 'Elfogadva', 'Lemondva') |                        |
| registered\_at | TIMESTAMP                                 | Jelentkezés ideje      |

#### 5. feedbacks

| Oszlop           | Típus                          | Megjegyzés        |
| ---------------- | ------------------------------ | ----------------- |
| id               | INT (PK, AI)                   |                   |
| user\_id         | INT (FK → users.id)            | Ki adta           |
| organization\_id | INT (FK → organizations.id)    | Kire vonatkozik   |
| event\_id        | INT (FK → events.id, NULLABLE) | Opcionális        |
| rating           | INT (1–5)                      | Értékelés         |
| comment          | TEXT                           | Szöveges vélemény |
| image            | VARCHAR(255), NULL             | Kép (opcionális)  |
| created\_at      | TIMESTAMP                      |                   |


## Végpontterv (REST API Endpointok) és CRUD műveltek

#### Autentikáció

| Módszer | URL             | Leírás                           |
| ------- | --------------- | -------------------------------- |
| `POST`  | `/api/register` | Új felhasználó regisztrálása     |
| `POST`  | `/api/login`    | Bejelentkezés (token visszaadás) |
| `POST`  | `/api/logout`   | Kijelentkezés                    |

#### Felhasználók

| Módszer | URL                                  | Leírás                          |
| ------- | ------------------------------------ | ------------------------------- |
| `GET`   | `/api/users/{id}`                    | Felhasználó adatainak lekérése  |
| `PUT`   | `/api/users/{id}`                    | Saját profil szerkesztése       |
| `GET`   | `/api/users/{id}/badges`             | Saját jelvényei                 |
| `GET`   | `/api/users/{id}/events`             | Részvett események              |


#### Civil szervezetek

| Módszer | URL                                     | Leírás                            |
| ------- | --------------------------------------- | --------------------------------- |
| `GET`   | `/api/organizations`                    | Összes szervezet listázása        |
| `GET`   | `/api/organizations/{id}`               | Egy szervezet részletes adatlapja |
| `PUT`   | `/api/organizations/{id}`               | Saját profil szerkesztése         |
| `GET`   | `/api/organizations/{id}/events`        | Az adott szervezet eseményei      |
| `GET`   | `/api/organizations/{id}/volunteers`    | Korábbi önkéntesek listája        |
| `GET`   | `/api/organizations/{id}/feedbacks`     | Visszajelzések lekérése           |


#### Események
| Módszer  | URL                         | Leírás                 |
| -------- | --------------------------- | ---------------------- |
| `GET`    | `/api/events`               | Összes esemény         |
| `GET`    | `/api/events/{id}`          | Egy esemény részletei  |
| `POST`   | `/api/events`               | Új esemény létrehozása |
| `PUT`    | `/api/events/{id}`          | Esemény szerkesztése   |
| `DELETE` | `/api/events/{id}`          | Esemény törlése        |
| `POST`   | `/api/events/{id}/register` | Jelentkezés eseményre  |
| `DELETE` | `/api/events/{id}/cancel`   | Jelentkezés lemondása  |

#### Visszajelzések

| Módszer | URL                                | Leírás                                        |
| ------- | ---------------------------------- | --------------------------------------------- |
| `POST`  | `/api/feedbacks`                   | Új értékelés létrehozása                      |
| `GET`   | `/api/feedbacks/{organization_id}` | Egy szervezethez tartozó értékelések lekérése |
| `GET`   | `/api/feedbacks/event/{event_id}`  | Egy eseményhez tartozó értékelések lekérése   |


