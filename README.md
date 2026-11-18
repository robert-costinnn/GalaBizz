# Platformă de analiză a firmelor din Galați --- Frontend

> Platformă web pentru descoperirea, analiza și compararea performanței
> financiare a firmelor din municipiul și județul Galați.

## Cuprins

-   [1. Despre proiect](#1-despre-proiect)
-   [2. Tehnologii](#2-tehnologii)
-   [3. Funcționalități](#3-funcționalități)
-   [4. UI/UX și structură](#4-uiux-și-structură)
-   [5. Structura proiectului](#5-structura-proiectului)
-   [6. Integrarea cu backend-ul](#6-integrarea-cu-backend-ul)
-   [7. Modele de date TypeScript](#7-modele-de-date-typescript)
-   [8. Gestionarea stărilor și a
    datelor](#8-gestionarea-stărilor-și-a-datelor)
-   [9. Instalare și rulare locală](#9-instalare-și-rulare-locală)
-   [10. Deployment](#10-deployment)
-   [11. Securitate și bune practici](#11-securitate-și-bune-practici)
-   [12. Etapele de dezvoltare](#12-etapele-de-dezvoltare)
-   [13. Obiectivul final](#13-obiectivul-final)

------------------------------------------------------------------------

## 1. Despre proiect

Aplicația este o platformă web care permite utilizatorilor să descopere,
să analizeze și să compare cele mai profitabile firme din municipiul
Galați și județul Galați, în funcție de domeniul de activitate și de
indicatorii financiari disponibili.

Scopul platformei este să ofere o imagine de ansamblu asupra mediului de
afaceri local prin statistici, grafice, clasamente și informații
financiare relevante.

Utilizatorii vor putea identifica rapid:

-   Cele mai profitabile firme din Galați.
-   Firmele cu cele mai mari cifre de afaceri.
-   Domeniile de activitate cu cele mai bune rezultate financiare.
-   Evoluția financiară a firmelor de-a lungul anilor.
-   Firmele cu cea mai mare creștere a profitului.
-   Comparații între companii din același domeniu de activitate.

Platforma va fi disponibilă online și va avea o interfață modernă,
intuitivă și responsive.

## 2. Tehnologii

  Tehnologie                Utilizare
  ------------------------- ---------------------------------------
  React                     Construirea interfeței utilizator
  Vite                      Development server și build
  TypeScript                Tipizare statică și siguranța codului
  React Router              Navigare între pagini
  Tailwind CSS              Stilizarea interfeței
  Recharts                  Grafice și vizualizări financiare
  Lucide React              Iconuri
  Axios                     Comunicare cu backend-ul
  React Context / Zustand   Gestionarea stării globale

**Deployment:** Render --- Static Site.

## 3. Funcționalități

### 3.1. Dashboard

Dashboard-ul este pagina principală și punctul central al platformei.

**Statistici generale:**

-   Numărul total de firme analizate.
-   Profitul net cumulat al firmelor.
-   Cifra de afaceri totală.
-   Numărul domeniilor de activitate analizate.
-   Numărul firmelor profitabile.

**Grafice:**

-   Distribuția firmelor în funcție de domeniul de activitate.
-   Evoluția profitului în ultimii ani.
-   Top domenii după profitul cumulat.
-   Comparația dintre cifra de afaceri și profit.

**Clasamente rapide:**

-   Top 5 cele mai profitabile firme.
-   Top 5 firme după cifra de afaceri.
-   Top 5 domenii de activitate.

### 3.2. Lista firmelor

Pagină dedicată tuturor firmelor din baza de date.

**Funcționalități:**

-   Afișarea firmelor într-un tabel.
-   Căutare după numele firmei.
-   Filtrare după domeniul CAEN.
-   Filtrare după localitate.
-   Filtrare după profit.
-   Filtrare după cifra de afaceri.
-   Sortare crescătoare și descrescătoare.
-   Paginare.
-   Accesarea paginii individuale a unei firme.

**Coloane în tabel:**

  Câmp                     Descriere
  ------------------------ ----------------------------
  Numele firmei            Denumirea companiei
  CUI                      Codul unic de identificare
  Domeniul de activitate   Domeniul asociat firmei
  Cifra de afaceri         Valoarea cifrei de afaceri
  Profitul net             Profitul net raportat
  Numărul de angajați      Numărul de angajați
  Anul raportării          Anul raportării financiare

### 3.3. Top firme

Pagină dedicată clasamentelor firmelor din Galați.

Clasamente disponibile:

-   Top firme după profit net.
-   Top firme după cifra de afaceri.
-   Top firme după numărul de angajați.
-   Top firme după creșterea profitului.
-   Top firme după rata profitului.

Utilizatorii vor putea selecta anul pentru care doresc să consulte
clasamentele.

### 3.4. Domenii de activitate

Secțiunea permite analizarea performanței financiare în funcție de
domeniul de activitate.

**Funcționalități:**

-   Listarea domeniilor de activitate.
-   Identificarea celor mai profitabile domenii.
-   Compararea domeniilor după profitul total.
-   Compararea domeniilor după cifra de afaceri.
-   Afișarea numărului de firme din fiecare domeniu.
-   Afișarea profitului mediu per firmă.
-   Evoluția domeniilor în timp.

Domeniile vor putea fi identificate folosind codurile CAEN.

### 3.5. Pagina individuală a unei firme

Fiecare firmă va avea o pagină proprie cu informații detaliate.

**Informații generale:**

-   Denumirea firmei.
-   CUI.
-   Sediul social.
-   Localitatea.
-   Domeniul de activitate.
-   Codul CAEN.
-   Starea firmei, dacă informația este disponibilă.

**Indicatori financiari:**

-   Cifra de afaceri.
-   Profitul net.
-   Numărul de angajați.
-   Rata profitului.
-   Datoriile, dacă datele sunt disponibile.

**Grafice și istoric:**

-   Evoluția cifrei de afaceri.
-   Evoluția profitului net.
-   Evoluția numărului de angajați.
-   Evoluția ratei profitului.
-   Istoricul financiar pentru anii disponibili.

### 3.6. Comparație între firme

Platforma va permite selectarea a două sau mai multe firme pentru
compararea performanțelor financiare.

**Indicatori comparabili:**

-   Profit net.
-   Cifră de afaceri.
-   Număr de angajați.
-   Rata profitului.
-   Evoluția financiară anuală.

Rezultatele vor fi prezentate prin grafice și tabele comparative.

## 4. UI/UX și structură

### Direcție vizuală

-   Design de tip SaaS / Financial Analytics Dashboard.
-   Aspect minimalist și profesional.
-   Paletă cromatică bazată pe albastru închis, alb și accente verzi.
-   Carduri pentru indicatorii financiari.
-   Grafice interactive.
-   Tabele clare și ușor de filtrat.
-   Navigare intuitivă.

### Layout general

**Sidebar:**

-   Dashboard
-   Firme
-   Top firme
-   Domenii de activitate
-   Comparații
-   Despre platformă

**Header:**

-   Logo-ul platformei.
-   Bara de căutare.
-   Selectarea anului financiar.
-   Profil utilizator, dacă va exista autentificare.

**Main Content:**

-   Conținutul paginii active.
-   Carduri statistice.
-   Grafice.
-   Tabele și clasamente.

Interfața trebuie să fie responsive și optimizată pentru desktop,
laptop, tabletă și telefon mobil.

## 5. Structura proiectului

Structura recomandată pentru frontend:

``` text
frontend/
├── public/
│   ├── logo.svg
│   └── favicon.ico
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── common/
│   │   │   ├── Button.tsx
│   │   │   ├── Input.tsx
│   │   │   ├── Select.tsx
│   │   │   └── Loading.tsx
│   │   ├── layout/
│   │   │   ├── Sidebar.tsx
│   │   │   ├── Header.tsx
│   │   │   └── MainLayout.tsx
│   │   ├── dashboard/
│   │   │   ├── StatsCard.tsx
│   │   │   ├── ProfitChart.tsx
│   │   │   └── TopCompanies.tsx
│   │   ├── companies/
│   │   │   ├── CompaniesTable.tsx
│   │   │   ├── CompanyFilters.tsx
│   │   │   └── CompanyCard.tsx
│   │   └── charts/
│   │       ├── RevenueChart.tsx
│   │       └── ComparisonChart.tsx
│   ├── pages/
│   │   ├── Dashboard.tsx
│   │   ├── Companies.tsx
│   │   ├── CompanyDetails.tsx
│   │   ├── Rankings.tsx
│   │   ├── Domains.tsx
│   │   ├── Comparison.tsx
│   │   └── About.tsx
│   ├── services/
│   │   ├── api.ts
│   │   ├── companyService.ts
│   │   └── statisticsService.ts
│   ├── hooks/
│   │   ├── useCompanies.ts
│   │   └── useStatistics.ts
│   ├── types/
│   │   ├── company.ts
│   │   └── statistics.ts
│   ├── utils/
│   │   ├── formatCurrency.ts
│   │   └── formatNumbers.ts
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── .env.example
├── .gitignore
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

## 6. Integrarea cu backend-ul

Frontend-ul va comunica cu backend-ul prin intermediul unui API REST.

URL-ul backend-ului nu va fi hardcodat în componente. Se va utiliza o
variabilă de mediu:

``` env
VITE_API_URL=https://backend-url.com/api
```

### Configurare Axios

``` typescript
import axios from "axios";

const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL,
  headers: {
    "Content-Type": "application/json",
  },
});

export default api;
```

Endpoint-urile vor fi stabilite împreună cu echipa responsabilă de
backend.

### Endpoint-uri propuse

  Metodă   Endpoint                Descriere
  -------- ----------------------- -------------------------------------
  GET      `/companies`            Lista firmelor
  GET      `/companies/:id`        Detalii firmă
  GET      `/companies/top`        Top firme
  GET      `/domains`              Lista domeniilor
  GET      `/statistics`           Statistici generale
  GET      `/statistics/profit`    Statistici privind profitul
  GET      `/statistics/revenue`   Statistici privind cifra de afaceri
  GET      `/companies/compare`    Compararea firmelor

> Endpoint-urile sunt propuneri și trebuie corelate cu implementarea
> efectivă a backend-ului.

## 7. Modele de date TypeScript

Se vor defini interfețe pentru toate entitățile principale.

### Company

``` typescript
export interface Company {
  id: number;
  name: string;
  cui: string;
  address: string;
  city: string;
  caenCode: string;
  domain: string;
  revenue: number;
  netProfit: number;
  employees: number;
  year: number;
}
```

### DashboardStatistics

``` typescript
export interface DashboardStatistics {
  totalCompanies: number;
  totalRevenue: number;
  totalProfit: number;
  profitableCompanies: number;
  totalDomains: number;
}
```

Valorile financiare vor fi afișate în RON, cu formatare corespunzătoare.

## 8. Gestionarea stărilor și a datelor

Aplicația trebuie să gestioneze corect:

-   Încărcarea datelor.
-   Erorile de comunicare cu backend-ul.
-   Lipsa rezultatelor.
-   Filtrele active.
-   Paginarea rezultatelor.
-   Actualizarea datelor la schimbarea anului selectat.

Se recomandă utilizarea unor componente reutilizabile pentru stările:

-   `Loading`
-   `Error`
-   `Empty State`

Datele demonstrative (*mock data*) pot fi utilizate în etapa inițială,
până când backend-ul este disponibil. Acestea trebuie separate clar de
datele reale.

## 9. Instalare și rulare locală

După inițializarea proiectului și instalarea dependențelor:

``` bash
npm install
npm run dev
```

> Comenzile presupun existența scripturilor corespunzătoare în
> `package.json`.

Creați fișierul `.env` pe baza `.env.example` și configurați URL-ul
backend-ului:

``` env
VITE_API_URL=https://backend-url.com/api
```

## 10. Deployment

Aplicația frontend va fi publicată pe Render ca **Static Site**.

  Setare              Valoare
  ------------------- --------------------------------
  Service Type        Static Site
  Root Directory      `frontend`
  Build Command       `npm install && npm run build`
  Publish Directory   `dist`

**Variabilă de mediu:**

``` env
VITE_API_URL=https://backend-url.com/api
```

### Configurarea rutării

Deoarece aplicația utilizează React Router, trebuie configurat un
rewrite pe Render pentru ca rutele interne să funcționeze corect.

  Source   Destination     Action
  -------- --------------- ---------
  `/*`     `/index.html`   Rewrite

Astfel, accesarea directă a unor pagini precum `/companies/123` nu va
genera eroarea 404.

Deployment-ul poate fi conectat la repository-ul GitHub, astfel încât
modificările publicate pe branch-ul principal să declanșeze automat un
nou deployment.

## 11. Securitate și bune practici

-   Utilizarea TypeScript pentru reducerea erorilor.
-   Validarea datelor introduse de utilizatori.
-   Gestionarea corespunzătoare a erorilor API.
-   Nu se vor stoca parole sau chei secrete în frontend.
-   Variabilele Vite cu prefixul `VITE_` sunt publice și nu trebuie să
    conțină secrete.
-   Comunicarea cu backend-ul trebuie realizată prin HTTPS în producție.
-   Componentele trebuie să fie reutilizabile.
-   Codul trebuie organizat modular.
-   Se vor evita duplicările de cod.
-   Interfața trebuie să respecte principiile de accesibilitate.

## 12. Etapele de dezvoltare

### Etapa 1 --- Inițializarea proiectului

-   Configurarea Vite cu React și TypeScript.
-   Instalarea dependențelor.
-   Configurarea Tailwind CSS.
-   Configurarea React Router.
-   Organizarea structurii proiectului.

### Etapa 2 --- Interfața principală

-   Implementarea layout-ului general.
-   Crearea Sidebar-ului.
-   Crearea Header-ului.
-   Implementarea Dashboard-ului.
-   Implementarea componentelor statistice.

### Etapa 3 --- Modulul de firme

-   Implementarea tabelului cu firme.
-   Implementarea căutării.
-   Implementarea filtrelor.
-   Implementarea sortării și paginării.
-   Implementarea paginii individuale a firmei.

### Etapa 4 --- Analiza financiară

-   Implementarea clasamentelor.
-   Implementarea paginii domeniilor de activitate.
-   Implementarea graficelor.
-   Implementarea comparațiilor între firme.

### Etapa 5 --- Integrarea cu backend-ul

-   Configurarea serviciilor API.
-   Conectarea componentelor la backend.
-   Eliminarea datelor demonstrative.
-   Tratarea erorilor și a stărilor de încărcare.

### Etapa 6 --- Testare și deployment

-   Testarea funcționalităților.
-   Testarea responsive.
-   Optimizarea performanței.
-   Configurarea Render.
-   Publicarea aplicației online.

## 13. Obiectivul final

Rezultatul final trebuie să fie o platformă web profesională care
permite explorarea și analiza mediului de afaceri din Galați.

Utilizatorii trebuie să poată identifica rapid cele mai profitabile
firme, să compare companii, să analizeze domenii de activitate și să
urmărească evoluția indicatorilor financiari.

Frontend-ul trebuie să ofere o experiență intuitivă și fluentă, să fie
ușor de extins și să permită integrarea ulterioară a unor
funcționalități noi.

**Principiul principal de dezvoltare:** platforma trebuie construită
modular, astfel încât fiecare secțiune să poată fi dezvoltată și
întreținută independent, fără a afecta restul aplicației.

## 14. Împărțirea responsabilităților în echipa de 4 persoane

Pentru a lucra în paralel și pentru a evita suprapunerea responsabilităților, dezvoltarea frontend-ului poate fi împărțită astfel:

### Nedelcu Laura — Configurarea proiectului, layout și Dashboard

**Responsabilități:**

- Inițializarea proiectului React + Vite + TypeScript.
- Configurarea Tailwind CSS și React Router.
- Organizarea structurii de directoare și a rutelor principale.
- Implementarea layout-ului general: `Sidebar`, `Header` și `MainLayout`.
- Crearea componentelor comune reutilizabile: butoane, input-uri, selectoare, carduri și stări de încărcare.
- Implementarea paginii Dashboard.
- Afișarea statisticilor generale și a graficelor principale.
- Verificarea aspectului responsive al layout-ului.

**Fișiere și zone principale:**

- `src/components/common/`
- `src/components/layout/`
- `src/components/dashboard/`
- `src/pages/Dashboard.tsx`
- `src/App.tsx`, `src/main.tsx`, `src/index.css`

**Rezultat așteptat:** aplicația pornește, navigarea funcționează, există un layout comun, iar Dashboard-ul afișează statistici și grafice folosind date demonstrative.

### Buzila Robert — Modulul Firme

**Responsabilități:**

- Implementarea paginii cu lista tuturor firmelor.
- Crearea tabelului cu informații despre firme: denumire, CUI, domeniu CAEN, cifră de afaceri, profit net și număr de angajați.
- Implementarea căutării după numele firmei.
- Implementarea filtrelor după domeniul CAEN, localitate, profit și cifră de afaceri.
- Implementarea sortării și paginării.
- Implementarea paginii individuale a unei firme.
- Afișarea informațiilor generale și a indicatorilor financiari.
- Realizarea graficelor cu evoluția cifrei de afaceri, profitului și numărului de angajați.

**Fișiere și zone principale:**

- `src/components/companies/`
- `src/pages/Companies.tsx`
- `src/pages/CompanyDetails.tsx`

**Rezultat așteptat:** utilizatorul poate găsi o firmă, poate filtra și sorta lista, poate naviga la profilul firmei și îi poate consulta istoricul financiar disponibil.

### Adrian Dinu — Top firme și Domenii de activitate

**Responsabilități:**

- Implementarea paginii Top firme.
- Crearea clasamentelor după profit net, cifră de afaceri și număr de angajați.
- Adăugarea clasamentelor după creșterea profitului și rata profitului.
- Implementarea selectării anului pentru clasamente.
- Implementarea paginii Domenii de activitate.
- Afișarea domeniilor pe baza codurilor CAEN.
- Compararea domeniilor după profitul total și cifra de afaceri.
- Afișarea numărului de firme și a profitului mediu pentru fiecare domeniu.
- Reprezentarea prin grafice a distribuției și evoluției domeniilor.

**Fișiere și zone principale:**

- `src/pages/Rankings.tsx`
- `src/pages/Domains.tsx`
- Componente dedicate clasamentelor și analizelor pe domenii, în directoare separate dacă este necesar.

**Rezultat așteptat:** utilizatorul poate analiza cele mai performante firme și poate identifica domeniile de activitate cu cele mai bune rezultate.

### Grosu Cornelia — Comparații, Despre platformă și coordonarea integrării API

**Responsabilități:**

- Implementarea paginii de comparație între două sau mai multe firme.
- Afișarea comparativă a profitului, cifrei de afaceri, numărului de angajați și ratei profitului.
- Crearea graficelor și tabelelor comparative.
- Implementarea paginii Despre platformă.
- Configurarea stratului de comunicare cu backend-ul folosind Axios, împreună cu ceilalți membri ai echipei.
- Stabilirea și documentarea contractelor comune pentru endpoint-uri și tipurile TypeScript, în colaborare cu echipa.
- Crearea sau coordonarea serviciilor API și a hook-urilor comune, astfel încât fiecare modul să poată prelua datele necesare.
- Verificarea integrării dintre paginile dezvoltate de ceilalți membri.

**Fișiere și zone principale:**

- `src/pages/Comparison.tsx`
- `src/pages/About.tsx`
- `src/services/`
- `src/hooks/`
- `src/types/` (contractele comune se stabilesc împreună cu toată echipa)

**Rezultat așteptat:** utilizatorul poate compara firme, poate consulta informațiile despre platformă, iar modulele frontend au o modalitate comună și coerentă de a comunica cu backend-ul.

> **Important:** Persoana 4 nu ar trebui să rămână singura responsabilă pentru integrarea tuturor paginilor cu API-ul. Fiecare persoană își conectează modulul la serviciile și tipurile comune, iar persoana 4 ajută la coordonare și rezolvarea problemelor de integrare.

### Reguli de colaborare

- Stabiliți de la început interfețele TypeScript comune (`Company`, statistici, domenii și răspunsuri API), ca toată lumea să lucreze cu aceeași structură a datelor.
- Conveniți asupra endpoint-urilor și parametrilor API înainte de integrarea finală.
- Până când backend-ul este disponibil, fiecare persoană poate folosi date demonstrative, respectând tipurile comune.
- Folosiți branch-uri Git separate pentru fiecare modul și integrați periodic modificările în branch-ul principal.
- Componentele comune și regulile de design trebuie stabilite de la început pentru a păstra o interfață unitară.
- Fiecare persoană testează modulul propriu, iar echipa testează împreună aplicația după integrare.

### Ordine recomandată de lucru

1. **La început:** Persoana 1 configurează proiectul și layout-ul; în paralel, toți membrii stabilesc tipurile de date și contractele API.
2. **Dezvoltare în paralel:** fiecare persoană implementează paginile și componentele alocate, folosind date demonstrative.
3. **Integrare:** fiecare modul este conectat la serviciile API comune și sunt rezolvate diferențele dintre datele demonstrative și răspunsurile backend-ului.
4. **Finalizare:** echipa verifică navigarea, filtrele, graficele, afișarea pe mobil, stările de încărcare și erorile, apoi pregătește deployment-ul.
