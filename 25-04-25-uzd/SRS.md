# **Programinės įrangos reikalavimų specifikacija (SRS) mokymosi valdymo sistemai (MVS)**

**Versija:** 1.0  
**Data:** 2025-04-25

## **1. Įvadas**

### **1.1 Tikslas**

Šis dokumentas nustato programinės įrangos reikalavimus mokymosi valdymo sistemai (MVS), skirtai palengvinti mokymąsi internetu. Sistema leis kurti kursus, registruoti studentus, atlikti vertinimus, išduoti sertifikatus ir rengti ataskaitas švietimo įstaigoms. Šis SRS yra pagrindas kūrimo, testavimo ir validavimo procesams.

### **1.2 Dokumento konvencijos**

-   **Paryškintas:** Skyrių pavadinimai, pagrindiniai terminai.
-   _Kursyvas:_ Vietos rezervuotos projektui būdingai informacijai.
-   REQ-[numeris]: Funkciniai reikalavimai (pvz., REQ-1).
-   Prioritetai: Aukštas (A), Vidutinis (V), Žemas (Ž).

### **1.3 Tikslinė auditorija**

Šis dokumentas skirtas:

-   Projektų vadovams: Stebėti eigą ir apimtį.
-   Programinės įrangos kūrėjams: Įgyvendinti sistemos funkcijas.
-   Kokybės užtikrinimo komandoms: Testuoti ir užtikrinti atitiktį reikalavimams.
-   Instruktoriams/Administratoriams: Suprasti sistemos galimybes.
-   Studentams: Suprasti sistemos naudojimo būdus.

Skaitytojams rekomenduojama pradėti nuo įvado, kad suprastų projekto apimtį, tada perskaityti bendrą aprašymą, kad susidarytų kontekstą, o tada pasigilinti į sistemos funkcijas ir išorinės sąsajos reikalavimus, kad susipažintų su išsamiomis specifikacijomis.

### **1.4 Projekto apimtis**

MVS teiks:

-   Kursų valdymą (medžiagos įkėlimas, pažangos stebėjimas).
-   Studentų registraciją ir autentifikavimą.
-   Internetinius vertinimus (viktorinos, užduotys).
-   Sertifikatų išdavimą.
-   Integraciją su trečiųjų šalių įrankiais (mokėjimo šliuzai, el. paštas, vaizdo konferencijos).
-   Komunikacijos įrankius (forumai, pranešimai).

Ji palaikys kelis vartotojo vaidmenis, įskaitant administratorius, instruktorius ir studentus, užtikrindama visapusišką mokymosi patirtį.

### **1.5 Nuorodos**

-   IEEE Std 830-1998: IEEE rekomenduojama programinės įrangos reikalavimų specifikacijų praktika.
-   Bendrojo duomenų apsaugos reglamento (BDAR) atitikties gairės.

## **2. Bendras aprašymas**

### **2.1 Produkto perspektyva**

MVS yra atskira žiniatinklio programa, integruojama su:

-   Mokėjimo šliuzais (pvz., PayPal, Stripe).
-   El. pašto paslaugomis (pvz., SendGrid).
-   Vaizdo konferencijomis (pvz., Zoom, Microsoft Teams).

### **2.2 Produkto funkcijos**

-   Vartotojų autentifikavimas (studentai, instruktoriai, administratoriai).
-   Kursų registracija ir turinio valdymas.
-   Internetiniai vertinimai ir pažymių rašymas.
-   Ataskaitų teikimas ir analizė.
-   Pažangos stebėjimas.
-   Komunikacijos įrankiai (forumai, pranešimai).

### **2.3 Vartotojų klasės ir charakteristikos**

-   Studentai: Registruojasi, baigia kursus, peržiūri pažymius.
-   Instruktoriai: Įkelia turinį, rašo pažymius už užduotis, valdo kursus.
-   Administratoriai: Valdo vartotojus, sistemos nustatymus, atitiktį reikalavimams.

### **2.4 Veikimo aplinka**

-   Serveris: Linux pagrindu sukurtas serveris su Apache/Nginx, PHP ir MySQL/PostgreSQL.
-   Klientas: Šiuolaikinės žiniatinklio naršyklės (Chrome, Firefox, Safari, Edge).
-   Frontend: React.js (adaptyvus dizainas).
-   Backend: Node.js/PHP, PostgreSQL/MySQL.
-   Diegimas: AWS/Google Cloud.

### **2.5 Apribojimai**

-   Privalo atitikti BDAR.
-   Privalo palaikyti 10 000 vienu metu prisijungusių vartotojų.
-   Adaptyvus dizainas, skirtas suderinamumui su mobiliaisiais įrenginiais.

### **2.6 Vartotojo dokumentacija**

-   Vartotojo vadovai kiekvienam vartotojo vaidmeniui.
-   Internetinė pagalba ir DUK.
-   Vaizdo įrašų pamokos.
-   API vadovai.

### **2.7 Prielaidos ir priklausomybės**

-   Vartotojai turi prieigą prie stabilaus interneto ryšio.
-   Instruktoriai pateikia kursų medžiagą standartiniais formatais.
-   Trečiųjų šalių paslaugos (pvz., mokėjimo šliuzai) yra patikimos ir turi prieinamas API.

## **3. Sistemos funkcijos**

### **3.1 Vartotojo autentifikavimas (Prioritetas: A)**

-   Aprašymas: Saugus prisijungimas/registracija.
-   Funkciniai reikalavimai:
    -   REQ-1: Vartotojai gali registruotis per el. paštą arba SSO (Google/Microsoft).
    -   REQ-2: Slaptažodžio atstatymas el. paštu.
    -   REQ-3: Sistema turi leisti vartotojams užsiregistruoti naudojant el. pašto adresą ir slaptažodį.
    -   REQ-4: Sistema turi išsiųsti patvirtinimo el. laišką po registracijos.
-   Stimulas/Atsako sekos:
    -   Stimulas: Vartotojas pateikia registracijos formą.
    -   Atsakas: Sistema patikrina įvestį ir sukuria vartotojo paskyrą.

### **3.2 Kursų valdymas (Prioritetas: A)**

-   Aprašymas: Kurti, atnaujinti ir tvarkyti kursus.
-   Funkciniai reikalavimai:
    -   REQ-5: Instruktoriai gali įkelti PDF/PPT/Video failus.
    -   REQ-6: Studentai gauna registracijos patvirtinimo el. laiškus.
    -   REQ-7: Instruktoriai gali kurti, redaguoti ir ištrinti kursus.
    -   REQ-8: Instruktoriai gali įkelti kursų medžiagą.
    -   REQ-9: Instruktoriai gali nustatyti registracijos laikotarpius.
-   Stimulas/Atsako sekos:
    -   Stimulas: Instruktorius sukuria naują kursą.
    -   Atsakas: Sistema išsaugo kurso informaciją ir padaro ją prieinamą registracijai.

### **3.3 Vertinimai (Prioritetas: A)**

-   Aprašymas: Automatinis pažymių rašymas ir atsiliepimai.
-   Funkciniai reikalavimai:
    -   REQ-10: Laiko atžvilgiu apribotos viktorinos su klausimais su keliais atsakymų variantais.
    -   REQ-11: Instruktoriai gali atsisiųsti pažymių ataskaitas.
    -   REQ-12: Sistema turi leisti instruktoriams sukurti, redaguoti ir ištrinti vertinimus (pvz., viktorinas, užduotis).
    -   REQ-13: Sistema turi automatiškai įvertinti viktorinas ir užduotis, jei įmanoma.
    -   REQ-14: Sistema turi leisti instruktoriams rankiniu būdu įvertinti užduotis ir pateikti atsiliepimus studentams.
-   Stimulas/Atsako sekos:
    -   Stimulas: Studentas pateikia viktorinos sprendimus.
    -   Atsakas: Sistema įvertina viktoriną ir pateikia rezultatą studentui ir instruktoriui.

### **3.4 Ataskaitų teikimas ir analizė (Prioritetas: V)**

-   Aprašymas: Sistemos naudojimo ir studentų pažangos ataskaitų generavimas.
-   Funkciniai reikalavimai:
    -   REQ-15: Administratoriai gali generuoti ataskaitas apie vartotojų aktyvumą, kursų lankomumą ir pažangą.
    -   REQ-16: Instruktoriai gali generuoti ataskaitas apie studentų pažymius ir vertinimus.
    -   REQ-17: Sistema turi pateikti vizualinę duomenų atvaizdavimą (pvz., grafikus, diagramas).

### **3.5 Komunikacijos įrankiai (Prioritetas: V)**

-   Aprašymas: Vartotojų bendravimo ir bendradarbiavimo galimybės.
-   Funkciniai reikalavimai:
    -   REQ-18: Sistema turi turėti forumą, kuriame vartotojai galėtų diskutuoti apie kursų temas.
    -   REQ-19: Sistema turi leisti vartotojams siųsti asmenines žinutes kitiems vartotojams.
    -   REQ-20: Sistema turi palaikyti pranešimų siuntimą (pvz., apie naujas užduotis, artėjančius terminus).

## **4. Išorinės sąsajos reikalavimai**

### **4.1 Vartotojo sąsajos**

-   Prietaisų skydelis su vaidmenimis pagrįstais rodiniais (studentas/instruktorius/administratorius).
-   Adaptyvus dizainas mobiliesiems įrenginiams.
-   Prieinama sąsaja, atitinkanti WCAG 2.1 standartus.

### **4.2 Programinės įrangos sąsajos**

-   Mokėjimo šliuzas: Stripe API/PayPal API.
-   El. pašto paslauga: SendGrid integracija.
-   Vaizdo konferencijos įrankiai: Zoom API, Microsoft Teams API.
-   RESTful API, skirtos integracijai su išorinėmis sistemomis.

### **4.3 Komunikacijos sąsajos**

-   HTTPS, RESTful API.

## **5. Kiti nefunkciniai reikalavimai**

### **5.1 Veikimas**

-   Privalo aptarnauti 10 000 vienu metu prisijungusių vartotojų su <2 s atsako laiku.

### **5.2 Saugumas**

-   Šifravimas nuo galo iki galo (SSL/TLS).
-   BDAR atitinkantis duomenų saugojimas.
-   Duomenų šifravimas perduodant ir ramybės būsenoje.
-   Vaidmenimis pagrįsta prieigos kontrolė.
-   Reguliarūs saugumo auditai.
-   Reguliarus duomenų atsarginis kopijavimas, kad būtų išvengta duomenų praradimo.
-   Parengtas nelaimių atkūrimo planas.

### **5.3 Programinės įrangos kokybė**

-   Prieinamumas: 99,9 % veikimo laikas.
-   Naudojamumas: Intuityvi vartotojo sąsaja su minimalia mokymosi kreive.
-   Patikimumas: Sistemos veikimo laikas 99,9%.
-   Palaikymas: Modulinis kodo pagrindas, skirtas lengviems atnaujinimams ir priežiūrai.

## **6. Kiti reikalavimai**

-   Teisinis: BDAR atitiktis ES vartotojams.
-   Internacionalizavimas: Anglų, ispanų, prancūzų kalbų palaikymas.
-   Atitiktis vietiniams švietimo reglamentams ir standartams.
-   Kelių kalbų palaikymas.

**Priedas A: Žodynėlis**

-   MVS: Mokymosi valdymo sistema
-   SSO: Vienkartinis prisijungimas
-   BDAR: Bendrasis duomenų apsaugos reglamentas
-   WCAG: Žiniatinklio turinio prieinamumo gairės
-   API: Aplikacijos programavimo sąsaja

**Priedas B: Analizės modeliai**

-   DFD 0 lygis: Duomenų srauto tarp vartotojų, kursų ir vertinimų apžvalga.
-   ER diagrama: Objektai: Studentas, Kursas, Registracija, Vertinimas.
-   Klasių diagrama: Klasės: Vartotojas, Instruktorius, Kursas, Viktorina.
-   Sekos diagrama: Studentas užsiregistruoja į kursą ir atlieka viktoriną.

**Priedas C: Problemų sąrašas**

-   TBD: Užbaigti mokėjimo šliuzo pasirinkimą (Stripe prieš PayPal).
-   TBD: Debesų prieglobos paslaugų teikėjas (AWS prieš Google Cloud).
-   Integracijos iššūkiai su trečiųjų šalių įrankiais.
-   Duomenų privatumo užtikrinimas įvairiuose regionuose.
