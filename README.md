# GalaBizz — Misiunea echipei de Testare & Quality Assurance

> **Document de misiune** · Branch: `testing` · Versiune: 1.0 · Proprietar: QA Lead

---

## 1. Contextul proiectului

**GalaBizz** este o aplicație care prezintă **cele mai profitabile firme din România** și care ajută antreprenorii, investitorii și autoritățile locale să identifice **domeniile insuficient reprezentate** la nivelul unui oraș — punctul de plecare fiind **Galați** — corelând oportunitatea economică cu **specificul forței de muncă locale**. Platforma are capacitatea de a **verifica și de a replica aceeași analiză în alte orașe**, astfel încât concluziile să fie comparabile și reproductibile la nivel național.

### 1.1 Cele trei promisiuni ale proiectului

| # | Promisiune către utilizator | Ce înseamnă concret pentru QA |
|---|---|---|
| **P1** | Clasificare corectă a firmelor după profitabilitate | Acuratețea datelor financiare, a perioadei de raportare, a monedei și a unităților de măsură |
| **P2** | Identificarea domeniilor subreprezentate într-un oraș | Corectitudinea agregărilor, a mapării codurilor CAEN și a pragurilor de semnificație |
| **P3** | Verificarea concluziilor în alte orașe | Consistență multi-oraș, comparabilitate reală, izolare corectă a filtrelor geografice |

Fiecare promisiune este tratată ca un **obiectiv de calitate măsurabil**, nu ca o afirmație de marketing.

---

## 2. Misiunea echipei

> **Misiunea echipei de Testare & QA este să garanteze că fiecare cifră, fiecare clasament și fiecare recomandare afișată în GalaBizz este corectă, trasabilă și reproductibilă — indiferent de orașul analizat — astfel încât deciziile economice luate pe baza platformei să poată fi susținute în fața unui investitor, a unui client sau a unei autorități publice.**

Tradus în responsabilități concrete, echipa:

1. **Apără integritatea datelor.** Niciun indicator financiar nu ajunge în interfață fără a fi validat față de sursa oficială și fără a avea o cale de trasabilitate clară.
2. **Apără corectitudinea analizei.** „Domeniul X este subreprezentat în Galați” este o concluzie derivată; o tratăm ca pe un calcul critic care trebuie demonstrat, nu presupus.
3. **Apără comparabilitatea.** Analiza pentru Galați și analiza pentru un alt oraș trebuie să folosească aceleași reguli, aceleași praguri și aceeași semantică — altfel comparația este invalidă.
4. **Apără încrederea utilizatorului.** Orice eroare vizibilă (un clasament greșit, un total inconsistent, un filtru care „uită” un județ) costă credibilitatea proiectului mai mult decât costă un bug de design.

---

## 3. Principii de lucru

| Principiu | Aplicare practică |
|---|---|
| **Corectitudinea înaintea vitezei** | Pentru date financiare și clasamente, un release se amână mai degrabă decât să livreze cifre incerte |
| **Trasabilitate integrală** | Fiecare valoare afișată poate fi urmărită: sursă → transformare → agregare → API → UI |
| **Testăm ipotezele, nu doar ecranele** | Validăm și logica de business (definiția „profitabil”, pragul de „subreprezentare”), nu doar randarea |
| **Automatizare unde aduce valoare** | Regresie, contracte API și reguli de calitate a datelor = automatizate; exploratorul rămâne uman |
| **Calitatea este a echipei, nu a QA** | QA facilitează standardul; Developer, Data și Product răspund împreună de respectarea lui |
| **Failure is a finding** | Un defect re și documentat este un câștig, nu o vină |

---

## 4. Scop și limite (Scope / Out of scope)

### 4.1 În scop

- **Calitatea datelor** — surse, ingestie, normalizare, deduplicare, prospețime, completitudine.
- **Logica de business** — definiții de profitabilitate, praguri, scoring de oportunitate, mapare CAEN → domeniu.
- **Analiza geografică** — agregări pe oraș/județ, identificarea domeniilor subreprezentate, comparații între orașe.
- **API-uri și contracte** — contract testing între `data-analysis` și `frontend`.
- **Interfața** — funcțional, consistență, accesibilitate, responsivitate, localizare (RO).
- **Non-funcțional** — performanță, disponibilitate, securitate, protecția datelor.
- **Proces** — criterii de intrare/ieșire, quality gates, raportare, managementul defectelor.

### 4.2 În afara scopului (dar monitorizat)

- Modelarea economică propriu-zisă (aparține echipei de data analysis; QA validează **implementarea** și **coerența**, nu oportunitatea strategiei).
- Acuratețea surselor oficiale în sine — QA semnalează discrepanțe, dar nu le poate corecta la sursă.
- Decizii de infrastructură și costuri cloud (consiliate, nu decise de QA).

---

## 5. Atributele de calitate urmărite

| Atribut | Definiție operațională | Nivel țintă |
|---|---|---|
| **Acuratețe** | Procentul valorilor afișate care coincid cu sursa oficială, în marja de rotunjire declarată | ≥ 99,5% |
| **Completitudine** | Procentul firmelor eligibile incluse în clasament pentru un oraș | ≥ 98% |
| **Prospețime** | Întârzierea maximă între publicarea datelor la sursă și reflectarea în platformă | ≤ perioada de raportare + 5 zile |
| **Consistență** | Aceleași filtre și praguri produc aceleași rezultate pe orice oraș | 100% |
| **Trasabilitate** | Fiecare valoare are sursă și versiune de pipeline identificabile | 100% |
| **Disponibilitate** | Uptime lunar pentru API-ul public | ≥ 99,5% |
| **Performanță** | Timp de răspuns p95 pentru listări/filtre | ≤ 800 ms |
| **Accesibilitate** | Conformitate WCAG 2.1 nivel AA pe fluxurile principale | 0 blocante |

---

## 6. Strategia de testare

### 6.1 Piramida și nivelurile

| Nivel | Acoperire | Responsabil | Automatizare |
|---|---|---|---|
| Testare unitară | Funcții de transformare, normalizări, formule | Developer | 100% |
| Testare de contract | Scheme și semantică API între `data-analysis` și `frontend` | QA + Dev | 100% |
| Testare de integrare | Pipeline de date, baza de date, agregări | QA | 90% |
| Testare E2E | Fluxuri utilizator: căutare firmă, filtrare oraș/domeniu, comparație între orașe | QA | 80% pe fluxurile critice |
| Testare exploratorie | Scenarii reale, date „murdare”, cazuri-limită | QA manual | 0% (prin definiție) |

### 6.2 Tipuri de testare aplicate

- **Funcțională** — pe fiecare story, cu criterii de acceptanță verificabile.
- **De date (data quality testing)** — validări de tip „expectations”: unicitate CUI, format numeric, plaje de valori, integritate referențială CAEN, absența duplicatelor.
- **De regresie** — suită automată rulată la fiecare Pull Request și nightly pe `testing`.
- **De contract și compatibilitate** — modificările de schemă nu pot rupe consumatorii.
- **De performanță și încărcare** — listări mari, filtre combinate, interogări multi-oraș.
- **De securitate** — OWASP Top 10, control al accesului, expunere de date personale.
- **De accesibilitate** — tastatură, contrast, cititoare de ecran.
- **De localizare** — diacritice, formatare numerică și valutară românească (1.234.567,89 lei).
- **Exploratorie și „adversarială”** — încercăm să spargem logica: orașe fără date, firme cu profit negativ, domenii cu 1 singur agent economic, schimbări de cod CAEN.

---

## 7. Testarea calității datelor (Data QA)

Aceasta este componenta definitorie pentru GalaBizz: produsul **este** datele.

### 7.1 Lanțul de validare

```
Sursă oficială → Ingestie → Normalizare → Deduplicare → Mapare CAEN → Agregare
      ↑               ↑            ↑              ↑             ↑           ↑
   validare 1     validare 2   validare 3    validare 4    validare 5  validare 6
```

Pentru fiecare verigă se definesc **reguli explicite, versionate și testate**:

| Verigă | Exemple de reguli de calitate |
|---|---|
| Ingestie | Toate înregistrările din fișierul sursă sunt contorizate; zero pierderi neexplicate |
| Normalizare | CUI valid (modul 11), denumire fără spații multiple, județ/oraș din listă închisă |
| Deduplicare | Un CUI = o firmă = o intrare în clasament |
| Mapare CAEN | Fiecare cod CAEN mapează către exact un domeniu de afișare |
| Agregare | Suma pe oraș = suma pe județ − alte localități; totalurile se reconciliază |
| Publicare | Valorile afișate sunt identice cu cele din stratul agregat, fără rotunjiri ascunse |

### 7.2 Testarea „verificării în alte orașe”

Capacitatea de verificare în alte orașe este un **avantaj competitiv** și, în același timp, o **sursă majoră de risc**. Se testează explicit:

- **Izolarea geografică** — filtrarea pe orașul A nu include firme din orașul B (inclusiv firme cu sediu social diferit de punctul de lucru).
- **Comparabilitate** — aceleași praguri și aceeași definiție a „subreprezentării” se aplică identic în toate orașele.
- **Scalabilitate a analizei** — adăugarea unui oraș nou nu alterează rezultatele orașelor existente (idempotență).
- **Reconciliere națională** — însumarea orașelor analizate rămâne coerentă cu totalul național.
- **Cazuri-limită** — orașe cu volum mic de date, orașe în care un domeniu are un singur jucător (risc de concluzie falsă de „oportunitate”).
- **Transparență** — interfața declară explicit numărul de firme pe care se bazează fiecare concluzie.

---

## 8. Medii și date de test

| Mediu | Scop | Date |
|---|---|---|
| `local` | Dezvoltare, teste unitare | Fixtures sintetice |
| `staging` | Integrare, E2E, regresie | Snapshot anonimizat + seturi sintetice |
| `production` | Verificare post-deploy (smoke) | Date reale, read-only |

**Reguli privind datele de test:**
- Nu se folosesc date cu caracter personal în medii neproducție; identificatorii se pseudonimizează.
- Seturile de date trebuie să acopere: firme profitabile, firme cu pierdere, firme inactive, CUI invalide, domenii cu un singur agent economic, orașe fără date.
- Fiecare set de date de test este versionat și documentat (ce scenariu acoperă).

---

## 9. Managementul defectelor

### 9.1 Severitate și SLA

| Severitate | Definiție | SLA remediere |
|---|---|---|
| **S1 — Blocant** | Date financiare afișate greșit; clasament invalid; scurgere de date personale | 4 ore (hotfix) |
| **S2 — Critic** | Flux principal indisponibil; concluzie de oportunitate eronată | 1 zi lucrătoare |
| **S3 — Major** | Funcționalitate secundară incorectă; inconsistență vizibilă | 3 zile lucrătoare |
| **S4 — Minor** | Defecte cosmetice, texte, aliniere | Următorul sprint |

### 9.2 Ciclul de viață

`New → Triaged → In progress → Fixed → In retest → Verified → Closed`
(respins: `Rejected`, amânat: `Deferred`, duplicat: `Duplicate`)

Orice defect S1/S2 generează automat: **test de regresie adăugat** + **post-mortem scurt** în maxim 5 zile.

---

## 10. Criterii de calitate (Quality Gates)

### 10.1 Criterii de intrare în testare

- Criteriile de acceptanță sunt scrise și verificabile.
- Build-ul este stabil, mediul `staging` este disponibil cu date la zi.
- Contractul API este publicat și versionat.

### 10.2 Criterii de ieșire (Definition of Done pentru release)

- ✅ Zero defecte S1 și S2 deschise.
- ✅ S3 cunoscute documentate și acceptate explicit de Product.
- ✅ Regresia automată verde pe `testing`.
- ✅ Toate regulile de calitate a datelor trec pe ultimul snapshot.
- ✅ Verificarea multi-oraș trecută pe minimum 2 orașe de referință.
- ✅ Smoke test post-deploy în `production` reușit.

---

## 11. Metrici și KPI

| Metrică | Descriere | Țintă |
|---|---|---|
| **Defect escape rate** | Defecte găsite în producție / total defecte | < 5% |
| **Densitatea defectelor** | Defecte per story | ≤ 0,5 |
| **Acuratețea datelor** | Eșantion verificat față de sursă | ≥ 99,5% |
| **Acoperire automată** | Fluxuri critice acoperite de E2E | ≥ 80% |
| **Flaky rate** | Teste instabile / total teste automate | < 2% |
| **Timp mediu de remediere (MTTR)** | De la raportare la verificare, pe severitate | Conform SLA |
| **Lead time QA** | Timp de la „ready for QA” la semnare | ≤ 2 zile |
| **Uptime API** | Disponibilitate lunară | ≥ 99,5% |
| **Lighthouse** | Performanță / accesibilitate pe paginile cheie | ≥ 90 / ≥ 95 |

Metricile se raportează **săptămânal** și se discută în retrospectiva de sprint.

---

## 12. Structura echipei

| Rol | Responsabilități principale |
|---|---|
| **QA Lead** | Strategie, quality gates, raportare, relația cu Product |
| **Test Automation Engineer** | Framework E2E și de contract, mentenanța suitei, CI |
| **Data QA Engineer** | Reguli de calitate a datelor, reconciliere, validarea pipeline-ului și a agregărilor |
| **Manual / Exploratory Tester** | Scenarii reale, cazuri-limită, testare adversarială, UAT |
| **Performance & Security** | Teste de încărcare, scanări de securitate, verificări OWASP |
| **Accessibility Champion** | Audit WCAG, verificări cu cititor de ecran |

*(În forma actuală, rolurile pot fi cumulate; responsabilitățile rămân explicit atribuite.)*

---

## 13. Unelte

| Categorie | Unelte propuse |
|---|---|
| E2E / UI | Playwright (Chromium, Firefox, WebKit) |
| API / contract | Postman + Newman, Pact sau schema-based contract testing |
| Calitatea datelor | `pytest` + Great Expectations / dbt tests |
| Performanță | k6 |
| Securitate | OWASP ZAP, `npm audit` / `pip-audit` |
| Accesibilitate | axe-core, audit manual cu tastatură și cititor de ecran |
| CI/CD | GitHub Actions (PR checks + nightly pe `testing`) |
| Calitate cod | SonarQube (coverage, code smells) |
| Observabilitate | Grafana / dashboard de calitate, alerte pe S1 |
| Management | GitHub Issues (defecte) + Projects (board QA) |

---

## 14. Conformitate și etică

- **GDPR** — GalaBizz prelucrează date despre firme, dar și date de contact care pot fi personale (administratori, reprezentanți). QA verifică explicit că astfel de câmpuri nu sunt expuse nejustificat și că sunt minimizate.
- **Surse și citare** — fiecare cifră afișată indică sursa și perioada de raportare.
- **Disclaimer de acuratețe** — interfața informează că rezultatele au caracter informativ și se bazează pe date publice raportate.
- **Fără concluzii absolute** — recomandările de tip „domeniu oportun” sunt prezentate cu grad de încredere și volumul de date pe care se bazează.

---

## 15. Riscuri principale și mitigare

| Risc | Impact | Mitigare |
|---|---|---|
| Surse oficiale cu întârzieri sau format modificat | Date învechite / pipeline rupt | Monitorizare a ingestiei + alertă pe scădere bruscă a volumului |
| Definiții inconsistente ale „profitabilității” între ecrane | Clasamente contradictorii | Definiție unică, versionată, testată la nivel de contract |
| Duplicare de firme (aceeași entitate, CUI-uri diferite istorice) | Clasament umflat | Reguli de deduplicare + verificare manuală pe eșantion |
| Concluzie de „oportunitate” bazată pe prea puține date | Recomandare înșelătoare | Prag minim de volum + afișarea gradului de încredere |
| Extinderea la orașe noi rupe analiza existentă | Regresie funcțională | Test de idempotență la fiecare oraș adăugat |
| Date personale expuse accidental | Risc legal | Scanări automate + teste de acces + review de privacy |

---

## 16. Plan inițial (primul ciclu)

1. **Săptămâna 1** — Inventar de riscuri, definirea atributelor de calitate, baseline de metrici.
2. **Săptămâna 2** — Reguli de calitate a datelor pe sursele existente; primul raport de acuratețe.
3. **Săptămâna 3** — Suită E2E pe fluxurile critice (căutare firmă, clasament, filtru oraș/domeniu).
4. **Săptămâna 4** — Test de contract `data-analysis` ↔ `frontend`; primul test multi-oraș (Galați + 1 oraș de control).
5. **Săptămâna 5** — Performanță și accesibilitate; definitivarea quality gates în CI.

---

## 17. Colaborare cu celelalte echipe

| Echipa | Interfața cu QA |
|---|---|
| `data-analysis` | Contracte de date, reguli de calitate, reconciliere, trasabilitate |
| `frontend` | Contracte API, E2E, accesibilitate, consistență vizuală |
| `testing` (acest branch) | Suita de testare, rapoarte, indicatori, documentație de proces |
| Product | Criterii de acceptanță, prioritizarea defectelor, acceptarea riscurilor |

---

## 18. Ipoteze deschise

Aceste elemente trebuie confirmate cu Product / `data-analysis` înainte de a fi transformate în teste formale:

- Definiția exactă a „celei mai profitabile firme” (profit net? marjă? profit absolut pe an fiscal?).
- Pragurile numerice care definesc un domeniu „subreprezentat”.
- Lista surselor oficiale de date și frecvența de actualizare.
- Setul de orașe de referință pentru validarea multi-oraș.
- Nivelul de detaliu acceptat pentru datele de contact (implicații GDPR).

---

## 19. Glosar

| Termen | Definiție |
|---|---|
| **CAEN** | Clasificarea activităților din economia națională — standardul de mapare a firmelor pe domenii |
| **CUI** | Codul unic de identificare al firmei |
| **Domeniu subreprezentat** | Sector economic cu prezență redusă (număr de firme / profit agregat) raportat la potențialul forței de muncă locale |
| **Quality gate** | Condiție obligatorie care trebuie îndeplinită pentru promovarea unui build |
| **Trasabilitate** | Capacitatea de a urmări o valoare afișată până la sursa și transformările ei |
| **Snapshot** | Copie consistentă a datelor la un moment dat, folosită pentru testare |

---

*Document viu — se actualizează la fiecare modificare a definirii proiectului sau a strategiei de testare.*
