Aplicație web care analizează cele mai profitabile firme din județul Galați. Noi suntem echipa de backend: importăm datele financiare publice, le salvăm în baza de date, calculăm indicatorii și le oferim frontend-ului printr-un API REST.

## Echipa backend
| Membru | Rol | Ce face |
|---|---|---|
| Chiracu Andrei | Cod general  Structura proiectului, review la pull request-uri, , CI, deploy; |
| Gorgan Andrei | Baza de date | Schema, migrațiile, calculul indicatorilor și al clasamentelor |, ține legătura cu celelalte departamente
| Filote Marius | API-uri | Endpoint-urile (firme, clasament, căutare, comparare, statistici) și documentația Swagger |
| Dan Elena | Verificarea datelor | Importul datelor din surse publice (ANAF, data.gov.ro), curățarea și validarea lor |
| Chiriac Daria  | Securitate și conturi | Login și înregistrare (JWT), roluri, protecția API-ului |

## Tehnologii
Python, FastAPI, PostgreSQL, SQLAlchemy, pandas, Microsoft SQL Server, MySQL, SQLite, SQL, Database Design, Data Modeling, ETL, Data Warehousing

## Reguli
- Fiecare lucrează pe branch-ul lui și deschide pull request.
- Fiecare scrie teste pentru codul lui.
