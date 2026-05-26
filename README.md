Téma: Školní evidence tříd a studentů
# EduRegistry – Proaktivní školní informační systém nové generace

## Téma
Návrh a dokumentace modulárního, API-driven informačního systému pro chytrou evidenci tříd, studentů, docházky a moderních forem hodnocení.

## Perex
EduRegistry je proaktivní školní informační systém navržený jako alternativa k rigidním a zastaralým monolitům (např. Bakaláři). Na rozdíl od nich data pouze pasivně neeviduje, ale aktivně s nimi pracuje. Systém v reálném čase analyzuje **datové trendy** a dokáže třídního učitele automaticky upozornit na náhlé zhoršení prospěchu nebo skrytý nárůst absence (tzv. Early Warning System). EduRegistry navíc nativně podporuje **formativní hodnocení** a zapojení studenta do procesu výuky skrze sebehodnocení. Díky moderní **API-first architektuře** je systém plně modulární – škola si může rozhraní poskládat na míru jako stavebnici, přičemž uživatelské prostředí pro rodiče a studenty nabízí čistý design inspirovaný moderními fintech aplikacemi.

## Hlavní cíle projektu
1. **Proaktivní přístup k datům:** Detekce varovných trendů v docházce a klasifikaci dříve, než student začne propadat.
2. **Podpora moderní pedagogiky:** Integrace formativního hodnocení a žákovských reflexí přímo do klasifikačního archu.
3. **Modularita a otevřenost (API-First):** Snadná integrace s dalšími školními nástroji a možnost vypínat/zapínat moduly podle potřeb školy.
4. **UX zaměřené na uživatele:** Konec nepřehledných tabulek; responzivní a intuitivní design pro rodiče i učitele.
5. **Absolutní bezpečnost:** Striktní řízení přístupových práv (RBAC) a detailní audit log pro transparentnost změn.

## Cílové skupiny (Uživatelé a role)
* **Administrátor:** Správa systému, správa API klíčů, technické nastavení a reset hesel.
* **Ředitel / Vedení školy:** Sledování agregovaných statistik, porovnávání úspěšnosti tříd, schvalování archivací.
* **Učitel:** Zapisování známek (s možností slovní/formativní vazby), zadávání typů hodnocení, správa docházky.
* **Student:** Prohlížení prospěchu, možnost přidání **vlastní reflexe/sebehodnocení** k testům, přehled absencí.
* **Rodič:** Okamžitý přehled o dění ve škole, omlouvání hodin, sledování vývojových trendů dítěte.

---

## Přehled plánovaných modulů (Scope systému)

### 1. Evidence studentů (Smart Core)
* Osobní údaje (jméno, datum nar., adresa) a foto studenta.
* Řízení přestupů mezi třídami a sledování stavu studia (aktivní, přerušené, ukončené).
* Kontextové propojení na kontakty zákonných zástupců.

### 2. Správa tříd (Modularita)
* Vytváření a archivace tříd, hlídání maximální kapacity.
* Přiřazení třídního učitele a správa vazeb mezi předměty, učiteli a konkrétní třídou.

### 3. Klasifikace a Formativní hodnocení
* Zadávání známek (1–5) s definicí vah a typů hodnocení (test, ústní, projekt...).
* **Modul formativního přístupu:** Možnost kombinovat známky s detailním slovním hodnocením a studentským sebehodnocením.
* Automatický výpočet klasického i váženého průměru.

### 4. Inteligentní docházka
* Evidence přítomnosti/absence po hodinách s nahráváním digitálních omluvenek.
* **Early Warning System:** Automatické upozornění při překročení kritického limitu absence nebo při detekci podezřelých vzorců (např. pravidelné pátky).

### 5. Uživatelé, bezpečnost a API
* Bezpečné přihlašování a správa oprávnění podle rolí (co kdo vidí a může měnit).
* **Audit log:** Transparentní a nezměnitelný zápis o tom, kdo, kdy a co v systému upravil.

### 6. Reporty a prediktivní výstupy
* Generování klasických výpisů prospěchu do PDF.
* Exporty do CSV / Excel pro potřeby školní matriky.
* **Výstup pro rodiče:** Grafický přehled vývoje (trendu) žáka namísto pouhého seznamu známek.
