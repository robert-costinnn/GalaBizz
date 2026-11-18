# Surse de date

> Document canonic al echipei. Singurul loc unde ținem linkurile și statusul surselor.
> Regula: **o sursă oficială = adevăr**; agregatoarele comerciale = doar cross-check.
> Status: `⬜ de verificat` · `🟡 în lucru` · `✅ link confirmat` · `❌ indisponibil`

Fișierele brute nu se urcă în git (vezi `.gitignore`). Se descarcă în `date/raw/<an>/`.

---

## 1. Bilanțuri — Ministerul Finanțelor (data.gov.ro) ✅

Set: https://data.gov.ro/dataset/situatii_financiare_2025

| Fișier | Conținut | Mărime | Descărcare |
|---|---|---|---|
| `web_uu_an2025.txt` | bilanțuri, majoritatea firmelor | ~80 MB | [link](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/eeecc692-d914-4d3b-b7f5-d1a8a9791979/download/web_uu_an2025.txt) |
| `web_bl_bs_sl_an2025.txt` | bilanțuri, firme mari și mijlocii | ~9 MB | [link](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/3540a9ce-6a4d-4e29-9aa1-ac909fe28ac1/download/web_bl_bs_sl_an2025.txt) |
| `web_ir_an2025.txt` | firme care raportează IFRS (Petrom, Hidroelectrica etc.) | mic | [link](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/38a8cc80-3470-49a0-9335-7ae020d8239d/download/web_ir_an2025.txt) |
| `web_instit_de_credit_an2025.txt` | bănci | mic | [link](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/2322b065-8e43-4cbd-b825-2f45f3718c3b/download/web_instit_de_credit_an2025.txt) |

### Structura

- Coloane: `CUI, CAEN, I1…I20`
- **Coloane esențiale:** `I13` = cifra de afaceri netă · `I18` = profit net · `I19` = pierdere netă · `I20` = număr mediu de salariați
- Explicația tuturor coloanelor: fișierele `.csv` cu același nume, din același set
- **Bănci:** coloane diferite — `I22` = profit sau pierdere, `I23` = cifra de afaceri

### Capcane cunoscute

- ⚠️ **Liberty Galați S.A. (CUI 1639739) nu are bilanț pe 2025** în setul publicat →
  nu apare în topul Galați. Trebuie menționat explicit în raport.
- ⚠️ **Bilanțurile 2025 amestecă CAEN Rev.2 cu Rev.3** → comparațiile sigure se fac pe
  **diviziuni (primele 2 cifre)**, nu pe clase (4 cifre).
- Firmele fără bilanț depus = `null`, nu zero.
- De verificat unitatea (RON vs. mii RON) pe eșantion.

- [ ] Descărcat `web_bl_bs_sl_an2025.txt` (9 MB) ca eșantion
- [ ] Confirmat separatorul și encoding-ul
- [ ] Confirmată unitatea sumelor

---

## 2. Identificare firme (nume, județ, localitate) — MF ✅

Set: https://data.gov.ro/dataset/date_de_identificare_platitori_actualizate_iunie_2026

| Fișier | Mărime |
|---|---|
| [date_identificare_platitori_2026_a_actualizat_iulie.txt](https://data.gov.ro/dataset/74d13a1a-8a0c-4ffe-805c-c9795672df83/resource/d35a8883-b2d3-40a6-be96-2611e744e5b2/download/date_identificare_platitori_2026_a_actualizat_iulie.txt) | ~430 MB |
| [date_identificare_platitori_2026_b__actualizat_iulie.txt](https://data.gov.ro/dataset/74d13a1a-8a0c-4ffe-805c-c9795672df83/resource/bd1d0d5d-a433-48f0-92a7-fff30627ed5f/download/date_identificare_platitori_2026_b__actualizat_iulie.txt) | ~450 MB |

- Separator: `^` · Encoding: UTF-8
- Cheie de legătură cu bilanțurile: `COD_FISCAL` = `CUI`
- Coloane utile: `DENUMIRE`, `JUDET`, `LOCALITATE`, `STARE`

- [ ] Descărcat și verificat separatorul pe primele 5 linii
- [ ] Verificat dacă `STARE` are valori consistente

---

## 3. Forță de muncă — INS TEMPO / ANOFM 🟡

| Indicator | Cod / sursă | Status |
|---|---|---|
| Salariu mediu net pe județe | TEMPO `FOM106E` | 🟡 |
| Șomaj pe județe | TEMPO `SOM101E` | 🟡 |
| Salariați pe activități CAEN | TEMPO (de identificat codul) | ⬜ |
| Statistici lunare șomaj | ANOFM — https://www.anofm.ro/ | ⬜ |
| Date județene Galați | DJS Galați — https://galati.insse.ro/ | ⬜ |

TEMPO Online: http://statistici.insse.ro:8077/tempo-online/

- [ ] Exportate seriile pentru Galați + județele orașelor benchmark
- [ ] Confirmat ultimul an publicat (există decalaj de ~1 an)
- [ ] Confirmat nivelul geografic minim (județ, nu oraș)

---

## 4. Populație ✅

| Sursă | Ce obținem |
|---|---|
| [Recensământ 2021 — Tabel 1.22](https://www.recensamantromania.ro/wp-content/uploads/2023/05/Tabel-1.22.xlsx) | Populația pe municipii — numitorul pentru „la 1.000 locuitori” |

- [ ] Confirmat numitorul folosit (populație stabilă vs. domiciliu)
- [ ] Extrase localitățile benchmark din tabel

---

## 5. Context macro / comparații (opțional) ⬜

| Sursă | Ce obținem |
|---|---|
| Eurostat | comparații regionale NUTS2 |
| BNR | curs valutar (dacă apar sume în EUR) |

---

## 6. Agregatoare comerciale (DOAR cross-check) ⬜

> Nu sunt sursă primară. Se folosesc pentru a verifica 5–10 firme de top manual.

| Site | Utilizare |
|---|---|
| listafirme.ro | cross-check top firme |
| termene.ro | cross-check stare / CAEN |

- [ ] Verificate manual 5 firme din top vs. sursa oficială

---

## 7. Nomenclatoare ⬜

| Nomenclator | Sursă | Status |
|---|---|---|
| CAEN Rev.2 (clase/diviziuni) | INS | ⬜ |
| CAEN Rev.3 | INS | ⬜ |
| Mapare CAEN Rev.2 → Rev.3 | de construit | ⬜ |
| Județe + localități (SIRUTA) | INS | ⬜ |

- [ ] Confirmat dacă datele de bilanț folosesc Rev.2, Rev.3 sau ambele

---

## Cum descărcăm (exemplu)

```bash
mkdir -p date/raw/2025
cd date/raw/2025
curl -O <link_din_tabel>
sha256sum *.txt > SHA256SUMS.txt
```

Fiecare descărcare se notează în jurnalul de mai jos: ce, când, de unde, cât de mare.

---

## Jurnal descărcări & decizii

| Data | Ce | Detaliu |
|---|---|---|
| — | — | — |
