# Diagramos

## DFD 0 lygis: Duomenų srauto tarp vartotojų, kursų ir vertinimų apžvalga.

```mermaid
flowchart TD
    A[Studentas] -->|Registracija/Prisijungimas| B[MVS]
    B -->|Anketos valdymas| A
    C[Instruktorius] -->|Kurso kūrimas| B
    B -->|Kurso patalpinimas| C
    D[Administratorius] -->|Ataskaitų generavimas| B
    B -->|Duomenų talpinimas| E[(Duomenų Bazė)]
```

## ER diagrama: Objektai: Studentas, Kursas, Registracija, Vertinimas.

```mermaid
erDiagram
   STUDENTAS ||--o{ REGISTRACIJA : "turi"
   STUDENTAS {
       int id PK
       string vardas
       string el_pastas
       string slaptazodis
   }
   KURSAS ||--o{ REGISTRACIJA : "įtraukia"
   KURSAS {
       int id PK
       string pavadinimas
       string aprasymas
       date pradzios_data
   }
   REGISTRACIJA {
       int studento_id FK
       int kurso_id FK
       date registracijos_data
       string statusas
   }
   KURSAS ||--o{ VERTINIMAS : "turi"
   VERTINIMAS {
       int id PK
       int kurso_id FK
       int studento_id FK
       int ivertis
       string atsiliepimas
       date data
   }
```

## Klasių diagrama: Klasės: Studentas, Instruktorius, Kursas, Viktorina.

```mermaid
classDiagram
    class Studentas {
        id
        name
        el_pastas
        slaptazodis
    }

    class Intruktorius {
        id
        vardas
        mokomas_dalykas
        skirtiUžduotį()
    }

    class Kursas {
        id
        pavadinimas
        aprasymas
        pradzios_data
        pridėtiStudentą()
        skirtiUžduotį()
    }

    class Viktorina {
        id
        ivertinimas
        pateikti()
    }

    Studentas <|-- Intruktorius
    Kursas --> Viktorina : turi
    Studentas --> Kursas : registruojasi
    Studentas --> Viktorina : vykdo

```

## Sekos diagrama: Studentas užsiregistruoja į kursą ir atlieka viktoriną.

```mermaid
  sequenceDiagram
    participant Studentas
    participant Sistema
    participant Kursas
    participant Viktorina

    Studentas->>Sistema: Prisijungia
    Studentas->>Sistema: Pasirenka kursą
    Sistema->>Kursas: Registruojasi studentą
    Studentas->>Sistema: Pasirenka viktoriną
    Sistema->>Viktorina: Pradeda viktoriną
    Studentas->>Viktorina: Atsako į klausimus
    Viktorina->>Sistema: Grąžina rezultatą
    Sistema->>Studentas: Parodo rezultatą
```
