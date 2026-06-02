# Katalog požadavků softwarového projektu – EduRegistry

Tento dokument obsahuje detailní specifikaci funkčních a nefunkčních požadavků pro proaktivní školní informační systém **EduRegistry**. Požadavky jsou rozděleny podle modulů a opatřeny prioritou (Must = kritický, Should = důležitý, Could = volitelný/bonusový).

---

## 1. Funkční požadavky (Functional Requirements - FR)
Funkční požadavky definují, co systém dělá, jaké nabízí funkce a jak reaguje na vstupy od uživatelů.

### Modul 1: Evidence studentů (Smart Core)
| ID | Uživatel (Role) | Popis požadavku (Funkce) | Priorita |
| :--- | :--- | :--- | :--- |
| **FR-1.1** | Administrátor / Učitel | Systém umožní kompletní správu (CRUD) osobních údajů studenta (jméno, datum narození, adresa). | Must |
| **FR-1.2** | Administrátor | Systém umožní nahrát a zobrazit profilovou fotografii studenta. | Should |
| **FR-1.3** | Administrátor / Učitel | Systém umožní evidovat a měnit stav studia (aktivní, přerušené, ukončené). | Must |
| **FR-1.4** | Učitel / Vedení | Systém uchová historii přestupů studenta mezi jednotlivými třídami. | Should |
| **FR-1.5** | Učitel / Rodič | Systém zajistí kontextové propojení profilu studenta s kontaktními údaji jeho zákonných zástupců. | Must |

### Modul 2: Správa tříd (Modularita)
| ID | Uživatel (Role) | Popis požadavku (Funkce) | Priorita |
| :--- | :--- | :--- | :--- |
| **FR-2.1** | Administrátor / Vedení | Systém umožní vytváření nových tříd a archivaci starých tříd na konci školního roku. | Must |
| **FR-2.2** | Administrátor | Systém umožní přiřadit ke každé třídě jednoho třídního učitele. | Must |
| **FR-2.3** | Administrátor | Systém umožní konfigurovat vazby mezi předměty, vyučujícími učiteli a konkrétní třídou. | Must |
| **FR-2.4** | Učitel / Administrátor | Systém automaticky zkontroluje a zamezí překročení maximální kapacity třídy při zápisu nového studenta. | Should |

### Modul 3: Klasifikace a Formativní hodnocení
| ID | Uživatel (Role) | Popis požadavku (Funkce) | Priorita |
| :--- | :--- | :--- | :--- |
| **FR-3.1** | Učitel | Systém umožní zadávat známky (1–5) a definovat jejich váhu (např. 1 až 10). | Must |
| **FR-3.2** | Učitel | Systém umožní vybrat typ hodnocení (test, ústní zkoušení, projekt, aktivita). | Must |
| **FR-3.3** | Učitel | **[Formativní modul]** Systém umožní učiteli přidat ke známce (nebo místo ní) detailní slovní zpětnou vazbu. | Must |
| **FR-3.4** | Student | **[Formativní modul]** Systém umožní studentovi vložit k zadané známce/testu vlastní sebehodnocení a reflexi. | Should |
| **FR-3.5** | Systém | Systém automaticky počítá průběžný vážený i aritmetický průměr studenta v daném předmětu. | Must |

### Modul 4: Inteligentní docházka (Early Warning)
| ID | Uživatel (Role) | Popis požadavku (Funkce) | Priorita |
| :--- | :--- | :--- | :--- |
| **FR-4.1** | Učitel | Systém umožní evidovat přítomnost, absenci nebo pozdní příchod studenta na každé vyučovací hodině. | Must |
| **FR-4.2** | Rodič / Student | Systém umožní nahrát fotografii nebo sken lékařského potvrzení (omlouvenky) přímo přes mobilní rozhraní. | Should |
| **FR-4.3** | Systém | **[Early Warning]** Systém automaticky upozorní studenta i rodiče v rozhraní, pokud absence v předmětu překročí 15 %. | Must |
| **FR-4.4** | Systém | **[Early Warning]** Systém upozorní třídního učitele na podezřelé vzorce chování (např. opakovaná absence v pátečních hodinách). | Could |

### Modul 5: Uživatelé, bezpečnost a API
| ID | Uživatel (Role) | Popis požadavku (Funkce) | Priorita |
| :--- | :--- | :--- | :--- |
| **FR-5.1** | Všichni | Systém vyžaduje bezpečné přihlášení pomocí unikátního loginu a zahashovaného hesla. | Must |
| **FR-5.2** | Systém | Systém striktně řídí přístupová práva na základě rolí (RBAC) – např. student nesmí vidět známky ostatních žáků. | Must |
| **FR-5.3** | Administrátor | Systém umožní bezpečný reset hesla uživatele a vygenerování jednorázového přihlašovacího odkazu. | Must |
| **FR-5.4** | Systém | **[Audit log]** Systém nezměnitelně loguje každou změnu známky nebo docházky (kdo, kdy, co změnil a původní hodnotu). | Must |
| **FR-5.5** | Vývojář / Třetí strany | **[API-First]** Systém poskytuje zabezpečené REST API rozhraní pro možnost připojení externích školních modulů. | Should |

### Modul 6: Reporty a prediktivní výstupy
| ID | Uživatel (Role) | Popis požadavku (Funkce) | Priorita |
| :--- | :--- | :--- | :--- |
| **FR-6.1** | Učitel / Vedení | Systém umožní vygenerovat a stáhnout oficiální pololetní/výroční výpis prospěchu a docházky do formátu PDF. | Must |
| **FR-6.2** | Vedení / Administrátor | Systém umožní exportovat kompletní data pro školní matriku do formátu CSV / Excel. | Must |
| **FR-6.3** | Rodič / Student | **[Trend reporting]** Systém namísto pouhého seznamu známek vygeneruje grafický vizuální přehled vývoje (trendu) prospěchu studenta v čase. | Should |

---

## 2. Nefunkční požadavky (Non-functional Requirements - NFR)
Nefunkční požadavky definují technické vlastnosti, limity, kvalitu a standardy celého systému.

### Bezpečnost a ochrana dat (Security)
* **NFR-1.1:** Veškerá síťová komunikace mezi uživatelem a serverem musí být šifrována pomocí protokolu HTTPS (TLS 1.3).
* **NFR-1.2:** Uživatelská hesla musí být v databázi bezpečně uložena za použití silného kryptografického saltu a algoritmu (např. bcrypt nebo Argon2).
* **NFR-1.3:** Systém musí splňovat legislativní požadavky GDPR, jelikož pracuje s citlivými osobními údaji nezletilých.

### Výkon a dostupnost (Performance & Availability)
* **NFR-2.1:** Odezva systému (načtení profilu studenta nebo zapsání známky) nesmí při běžném zatížení překročit 1.5 sekundy.
* **NFR-2.2:** Systém musí být navržen tak, aby zvládl nárazové zatížení na konci klasifikačního období (generování stovek PDF reportů naráz).
* **NFR-2.3:** Dostupnost systému (Uptime) musí být minimálně 99.5 % v průběhu školního roku (mimo plánované technické odstávky o prázdninách).

### Použitelnost a kompatibilita (UX & Compatibility)
* **NFR-3.1:** Uživatelské rozhraní (UI) pro role Student a Rodič musí být plně responzivní a optimalizované pro zobrazení na mobilních telefonech (Mobile-First přístup).
* **NFR-3.2:** Webová aplikace musí být plně kompatibilní se všemi moderními webovými prohlížeči (Google Chrome, Apple Safari, Mozilla Firefox, Microsoft Edge).
* **NFR-3.3:** Systém musí mít intuitivní ovládání – učitel musí být schopen zapsat známku nebo absenci na maximálně 3 kliknutí od přihlášení.
