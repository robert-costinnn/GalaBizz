# Surse de date brute

Fișierele brute nu se urcă în git (vezi `.gitignore`). Le descarci de la linkurile de mai jos în `date/raw/`.

## Bilanțuri 2025 – Ministerul Finanțelor (data.gov.ro)
Set: https://data.gov.ro/dataset/situatii_financiare_2025

| Fișier | Conținut | Mărime |
|---|---|---|
| [web_uu_an2025.txt](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/eeecc692-d914-4d3b-b7f5-d1a8a9791979/download/web_uu_an2025.txt) | bilanțuri, majoritatea firmelor | ~80 MB |
| [web_bl_bs_sl_an2025.txt](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/3540a9ce-6a4d-4e29-9aa1-ac909fe28ac1/download/web_bl_bs_sl_an2025.txt) | bilanțuri, firme mari și mijlocii | ~9 MB |
| [web_ir_an2025.txt](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/38a8cc80-3470-49a0-9335-7ae020d8239d/download/web_ir_an2025.txt) | firme care raportează IFRS (Petrom, Hidroelectrica etc.) | mic |
| [web_instit_de_credit_an2025.txt](https://data.gov.ro/dataset/e2266fdc-0a6b-43b8-9c9f-7a6943d85b28/resource/2322b065-8e43-4cbd-b825-2f45f3718c3b/download/web_instit_de_credit_an2025.txt) | bănci | mic |

Coloane: `CUI, CAEN, I1…I20`. Cele mai folosite sunt I13 (cifra de afaceri netă), I18 (profit net), I19 (pierdere netă) și I20 (număr mediu de salariați). Explicația tuturor coloanelor e în fișierele `.csv` cu același nume din același set. Pentru bănci, coloanele sunt altele (I22 = profit sau pierdere, I23 = cifra de afaceri).

## Identificare firme (nume, județ, localitate) – Ministerul Finanțelor
Set: https://data.gov.ro/dataset/date_de_identificare_platitori_actualizate_iunie_2026
- [date_identificare_platitori_2026_a_actualizat_iulie.txt](https://data.gov.ro/dataset/74d13a1a-8a0c-4ffe-805c-c9795672df83/resource/d35a8883-b2d3-40a6-be96-2611e744e5b2/download/date_identificare_platitori_2026_a_actualizat_iulie.txt) (~430 MB)
- [date_identificare_platitori_2026_b__actualizat_iulie.txt](https://data.gov.ro/dataset/74d13a1a-8a0c-4ffe-805c-c9795672df83/resource/bd1d0d5d-a433-48f0-92a7-fff30627ed5f/download/date_identificare_platitori_2026_b__actualizat_iulie.txt) (~450 MB)

Separatorul e `^`, iar codificarea e UTF-8. Se leagă de bilanțuri prin `COD_FISCAL` = `CUI`. Coloanele utile sunt `DENUMIRE`, `JUDET`, `LOCALITATE` și `STARE`.

## Populație
- Recensământul 2021, populația pe municipii (Tabel 1.22): https://www.recensamantromania.ro/wp-content/uploads/2023/05/Tabel-1.22.xlsx

## De strâns (forța de muncă)
- INS TEMPO Online: salariul mediu net pe județe (FOM106E), șomaj (SOM101E), salariați pe activități. http://statistici.insse.ro:8077/tempo-online/
- ANOFM: statistici lunare de șomaj pe județe. https://www.anofm.ro/
- DJS Galați: https://galati.insse.ro/

## Observații
- Liberty Galați S.A. (CUI 1639739) nu are bilanț pe 2025 în setul publicat.
- Bilanțurile pe 2025 conțin atât coduri CAEN Rev.2, cât și Rev.3, așa că e mai sigur să compari pe diviziuni (primele 2 cifre).
