# Telemedicína – software tester portfolio

Telemedicína je způsob, jak poskytovat zdravotní péči na dálku pomocí digitálních nástrojů. Aplikace v mobilu nebo prohlížeči není jen doplněk, ale často hlavní platforma, přes kterou se pacient spojí s lékařem.
Když v takové aplikaci něco nefunguje, hrozí riziko, že se pacient nedovolá, nedostane recept nebo důležitou informaci včas.

Tento repozitář je **anonymizovaná case study** z reálného projektu, kde jsem pracoval jako **software tester** na telemedicínské platformě (mobilní aplikace + web) více než dva roky.  
Neobsahuje žádný kód ani interní data – zaměřuje se na **způsob uvažování, typy testů a příklady scénářů**.

---

## Stručný přehled

- Doména: **telemedicína / healthcare**
- Platformy: **mobilní aplikace (Android/iOS) + web**
- Typ práce: **manuální testování**, regresní testy, exploratorní testování, end to end testy, smoke testy, integrační testy a další
- Tým: produktový tým ve stylu **Agile/Scrum**
- Prostředí: více trhů ve střední Evropě a Latinské Americe

> Cíl tohoto portfolia: ukázat, jak jsem pracoval jako software tester v oblasti zdravotnictví, telemedicíny.

---

## O produktu – co ta platforma řeší

Testovaný produkt byl **telemedicínský ekosystém**, který propojoval:

- **Pacienty** – přes mobilní aplikaci a web:
  - založení účtu a vyplnění základních zdravotních údajů,
  - vyhledání lékaře nebo služby,
  - objednání online konzultace (chat / hovor / videohovor),
  - příjem lékařských zpráv, příloh a eReceptů.

- **Lékaře a terapeuty** – přes aplikaci pro zdravotníky (mobil + web):
  - přehled požadavků pacientů ve „virtuální ordinaci“,
  - plánování a vedení konzultací,
  - vedení dokumentace,
  - vystavování eReceptů a dalších dokumentů.

- **Další role**:
  - sestry (evidence a příprava pacienta),
  - firmy (benefit telemedicíny pro zaměstnance / klienty),
  - nemocnice a kliniky (specializované moduly, např. onkologie).

Platforma byla nasazena ve více zemích:  
Česko, Slovensko, Maďarsko, Polsko, Srbsko a vybrané státy Latinské Ameriky (Kolumbie, Ekvádor, Mexiko, Peru).  
Tomu odpovídalo i **vícejazyčné UI a různé lokální požadavky**.

### Specializovaný modul – péče o diabetiky

Součástí systému byl i modul pro pacienty s diabetem:

- pacient si doma změří glykémii (např. glukometrem),
- hodnoty zadá do průvodce / dotazníku v aplikaci,
- data se přenesou k ošetřujícímu lékaři do přehledu pacienta,
- lékař může v čase sledovat vývoj a reagovat.

Pokud pacient zadal hodnotu výrazně mimo běžné rozmezí, aplikace ho **ihned upozornila**, že by měl situaci řešit – typický příklad, kde chyba v logice nebo validaci dat může mít přímý dopad na zdraví.

---

## Proč je QA v telemedicíně důležité

Chyba v telemedicíně může znamenat, že se pacient:

- nedovolá lékaři,
- nedostane recept,
- uvidí špatnou informaci o svém zdravotním stavu.

Z pohledu testování to znamená:

- práci s **citlivými zdravotními daty** (GDPR, logy, screenshoty musí být anonymizované),
- důraz na **spolehlivost real-time funkcí** (videohovory, chat, notifikace),
- **více trhů a jazyků** – jiné formáty dat, jiné právní texty, různé typy uživatelů,
- různé **role v systému** (pacient, lékař, sestra, administrátor) a jejich oprávnění.

Tester zde není jen „hledač bugů“, ale i člověk, který pomáhá hlídat, aby aplikace byla pro uživatele srozumitelná a dobře ovladatelná. Jak pro lékaře, tak pro pacienty.

---

## Moje role v týmu

Pracoval jsem v roli **software testera** zaměřeného na manuální testování.  
Zodpovědnosti:

- testování nových funkcí na **mobilu i webu**,
- **regresní testy** před releasy,
- testování hlavních toků pacienta a lékaře,
- **lokalizační testy** (země a jazyky viz výše),
- testování **videohovorů** v různých síťových podmínkách,
- ověřování notifikací (push, e-mail),
- zapisování bugů a komunikace s vývojáři,
- zpětná vazba k použitelnosti a chování aplikace z pohledu běžného uživatele,
- základy testování API pomocí Dev Tools,
- první zkušenost s **automatizací – jednoduchý E2E test registračního flow v Cypressu**.

---

## Jak testuju – přístup a typy testů

Při práci na projektu jsem používal hlavně tyto typy testů:

### Funkční testy

Ověření, že funkce dělá to, co má. Například v částech aplikace zaměřené na:

- registraci a přihlášení,
- objednání konzultace,
- videohovor,
- vystavení eReceptu,
- vyplnění a uložení dotazníků (např. diabetologický modul).

### Integrační testy „přes UI“

Kontrola, že spolu správně fungují:

- mobil / web aplikace,
- backend API,
- notifikační systém,
- video platforma.

Typický příklad:  
pacient objedná konzultaci a projde přes platební bránu → lékař vidí termín ve svém kalendáři → přijde notifikace do aplikace a e-mailu → proběhne videohovor → lékař vystaví lékařskou zprávu a eRecept.

### Regresní a smoke testy

Před releasem:

- rychlé **smoke testy** – základní flow pacienta a lékaře,
- rozsáhlejší **regresní sada** – hlavní scénáře napříč moduly.

### Exploratorní testování

Cílené „proklikaní“ aplikace bez detailního scénáře:

- kombinace kroků, které nejsou v happy path,
- testování toho, co by reálný uživatel mohl udělat „nelogicky“,
- hledání edge cases (přepnutí sítě během hovoru, více přihlášených zařízení, přerušení zadávání dotazníku apod.).

### Negativní scénáře

Záměrné zadávání špatných / nekompletních dat:

- neplatné e-maily, slabá hesla,
- extrémní hodnoty v dotaznících (např. glykémie mimo rozumné meze),
- přihlášení špatným heslem,
- neplatné PSČ, rodné číslo a další údaje,
- nahrávání dokumentů v nesprávném formátu.

---

## Ukázkové scénáře, které jsem testoval

Níže několik typických scénářů (anonymizovaně):

### 1️⃣ Pacient se registruje a objedná se k lékaři

- založení účtu, potvrzení e-mailu,
- vyplnění základních údajů,
- výběr služby / lékaře,
- nastavení času konzultace,
- kontrola, že se konzultace zobrazí mezi nadcházejícími,
- že dorazí upozornění (push / e-mail),
- otestování průběhu videohovoru.

### 2️⃣ Základní lékařské workflow

- přihlášení do lékařské části,
- zobrazení seznamu konzultací,
- přijetí pacienta,
- spuštění a ukončení videohovoru,
- zápis zprávy a případného eReceptu,
- kontrola, že pacient vše najde ve své historii.

### 3️⃣ Diabetologický modul – zadání glykémie pacientem

- pacient zadá hodnotu glykémie do dotazníku,
- aplikace spočítá, zda je hodnota v normě,
- při výrazně mimořádné hodnotě zobrazí **okamžité upozornění**,
- lékař v rozhraní vidí nové hodnoty u konkrétního pacienta,
- může sledovat trend v čase.

### 4️⃣ Multi-device a notifikace

- pacient je přihlášen na mobilu a desktopu,
- dojde ke změně času konzultace,
- kontrola notifikací,
- ověření, že po kliknutí se otevře správná obrazovka,
- že nedochází k nečekanému odhlášení.

### 5️⃣ Slabé připojení během videohovoru

- zahájení hovoru na stabilní Wi-Fi,
- přechod na mobilní data,
- krátké i delší výpadky spojení,
- sledování kvality obrazu a zvuku,
- chování aplikace (reconnecting, chybové hlášky, možnost obnovit hovor).

---

## Příklady chyb, které jsem pomáhal řešit

- **Validace vstupů při registraci**  
  Pole pro kontaktní údaje nebo identifikátor pacienta přijme zjevně neplatný vstup, místo aby uživatele zastavilo a zobrazilo jasnou chybovou hlášku.

- **Lokalizace a layout po přepnutí jazyka**  
  V některých jazykových verzích (delší texty) se rozbije rozložení obrazovek – tlačítka „přetékají“, text se nevejde nebo zakrývá jiné prvky.

- **Časové zóny a plánování konzultací**  
  Pacient a lékař v různých zemích vidí u stejné konzultace odlišný čas, protože se špatně přepočítává časové pásmo.

- **Ukončení videohovoru a soukromí**  
  Chyby kolem ukončení hovoru – například session není správně uzavřená a aplikace nedá uživateli jasně najevo, že přenos byl opravdu ukončen.

- **Notifikace a navigace z upozornění**  
  Upozornění na změnu termínu nebo novou zprávu sice dorazí, ale po kliknutí nevede na správné místo v aplikaci, nebo se konzultace vůbec nenačte.

U každé chyby jsem dbal na:

- jednoznačný název,
- přesné kroky k reprodukci,
- popis očekávaného vs. skutečného chování,
- přiložené screenshoty / video,
- uvedení prostředí (zařízení, OS, verze aplikace).

---

## Regresní testování a práce s riziky

Před releasy jsem procházel sadu hlavních scénářů:

- registrace / přihlášení,
- objednání a průběh konzultace (pacient i lékař),
- notifikace (nová konzultace, změna termínu),
- historie konzultací a dokumentů,
- vybrané scénáře z diabetologického modulu,
- základní nastavení a profil.

---

## Co si z telemedicíny odnáším a kam se posouvám dál

### Co jsem si odnesl

Z pohledu QA:

- jistotu v **manuálním testování** komplexní aplikace (mobil + web),
- zkušenost s **real-time funkcemi** (videohovory, chat),
- praxi v **multi-device / multi-browser / multi-language** prostředí,
- návyk psát **srozumitelné bug reporty**,
- cit pro **edge cases**, které odhalují slabá místa aplikace.
- základní znalosti **automatizovaného testování** v Cypress.

---

## Základy automatizace (Cypress)

Moje hlavní práce v telemedicíně byla manuální, ale postupně jsem se začal zajímat i o automatizaci.  
V rámci webové části aplikace jsem si v Cypressu vyzkoušel jednoduchý end-to-end test registračního flow.

- cílem bylo **projít celý scénář nového pacienta** – výběr země a jazyka, přechod na přihlášení, založení nové registrace,
- generoval jsem **unikátní e-mail** pro každé spuštění testu,
- pracoval jsem se selektory, assertions a základní strukturou Cypress testů.

Níže je **zkrácený, anonymizovaný příklad** (fiktivní URL, texty i selektory):

```js
// Jednoduchý E2E test – registrace pacienta (ukázkový příklad)

function generateRandomNumber() {
  return Math.floor(10000000 + Math.random() * 90000000).toString();
}

function generateUniqueEmail() {
  const prefix = 'testuser+';
  const suffix = '@example.com';
  const randomNumber = generateRandomNumber();
  return `${prefix}${randomNumber}${suffix}`;
}

describe('Registration flow – web telemedicine app', () => {
  it('allows user to select region, language and start registration', () => {
    // 1) návštěva webu
    cy.visit('https://rc.example-telemed-app.com/');

    // 2) výběr země a jazyka (fiktivní selektory)
    cy.get('[data-testid="region-select"]').click();
    cy.contains('[role="option"]', 'Slovensko').click();

    cy.get('[data-testid="language-select"]').click();
    cy.contains('[role="option"]', 'Slovenčina').click();

    cy.contains('Pokračovať').click();
    cy.url().should('include', '/prihlasit');

    // 3) přechod na registraci
    cy.contains('Nová registrácia').click();
    cy.url().should('include', '/registrace');

    // 4) zadání telefonu (zkráceno)
    cy.get('[data-testid="phone-prefix"]').click();
    cy.contains('+421').click();
    cy.get('[data-testid="phone-number"]').clear().type('777000004');
    cy.contains(/pokračovať/i).click();

    // 5) zadání kódu (syntetické hodnoty)
    cy.get('[data-testid="code-input-1"]').type('0');
    cy.get('[data-testid="code-input-2"]').type('0');
    cy.get('[data-testid="code-input-3"]').type('0');
    cy.get('[data-testid="code-input-4"]').type('0');
    cy.contains(/pokračovať/i).click();

    // 6) vyplnění e-mailu – unikátní adresa pro každý běh
    const uniqueEmail = generateUniqueEmail();

    cy.get('[data-testid="email"]').type(uniqueEmail);
    cy.get('[data-testid="email-confirm"]').type(uniqueEmail);

    // jednoduchá kontrola
    cy.get('[data-testid="email"]').should('have.value', uniqueEmail);
    cy.get('[data-testid="email-confirm"]').should('have.value', uniqueEmail);
  });
});
```


## Kontakt
LinkedIn: https://www.linkedin.com/in/jirisilbersky
