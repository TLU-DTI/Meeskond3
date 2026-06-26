# SciFilter-Project_

SciFilter Phase 2
 
## Meie prototüübi leiate aadressilt: https://scifilter-project-afan.onrender.com

## Screenshots

### Dashboard
![SciFilter Dashboard](images/SciFilter_dashboard.png)

### Login
![SciFilter Login](images/SciFilter_login.png)

### Registration
![SciFilter Registration](images/SciFilter_register.png)

## Projekti autorid: Kati Põld, Risto Ridal, Andre Priks, Daniel Malkov, Riho Nelk

## Klient: Dr. Abiodun Afolayan Ogunyemi

## Projekti kirjeldus: 

SciFilter on teaduspublikatsioonide kvaliteedi hindamise ja sõelumise tööriist, mis aitab kasutajatel hinnata teadusallikate usaldusväärsust ning kvaliteeti. Süsteem kasutab publikatsioonide metaandmeid ja registripõhist klassifitseerimist, et toetada teaduspõhist otsustamist ning kirjanduse sõelumist. Käesoleva projekti eesmärk oli täiustada olemasolevat SciFilter süsteemi, parandada kasutajakogemust ning prototüüpida uusi töövooge, mis vähendavad käsitööd ja muudavad süsteemi kasutamise mugavamaks.

## Projekti taust: 

Projekt valmis Tallinna Ülikooli Digitehnoloogiate instituudi Tarkvaraarenduse (IFI6240.DT) suveprojekti raames.
Arendustöö keskendus kasutajakesksele disainile, sidusrühmade kaasamisele ning olemasoleva SciFilter süsteemi laiendamisele. 
Projekt oli seotud ka õppeainetega Sissejuhatus infosüsteemidesse (IFI6068.DT) ja Interaktsioonidisaini alused (IFI6207.DT), mille käigus valmisid lahenduse analüüs, dokumentatsioon ning kasutajaliidese disain.
Õppeaine Sissejuhatus infosüsteemidesse raames viidi läbi probleemi analüüs, sidusrühmade ja kasutajate vajaduste kaardistamine, nõuete kogumine ning infosüsteemi dokumentatsiooni koostamine. Samuti kirjeldati süsteemi eesmärke, kasutusstsenaariume ja funktsionaalseid nõudeid.
Õppeaine Interaktsioonidisain raames teostati kasutajauuringud, koostati persoonad ja kasutajalood, loodi informatsiooni arhitektuur ning valmisid nii madala kui ka kõrge detailsusega kasutajaliidese prototüübid. Lisaks viidi läbi kasutatavuse testimine ja disainilahenduste hindamine.
Õppeaine Tarkvaraarenduse projekt raames realiseeriti kavandatud lahendus meeskonnatööna. Arendus põhines eelnevates ainetes valminud analüüsil, nõuetel ja prototüüpidel ning hõlmas süsteemi funktsionaalsuste implementeerimist, testimist ja dokumenteerimist.
SciFilter projekti eesmärk oli täiustada olemasolevat teaduspublikatsioonide sõelumise tööriista, parandada kasutajakogemust ning prototüüpida uusi funktsionaalsusi ja töövooge teadusallikate kvaliteedi hindamise toetamiseks.

## Kasutatud tehnoloogiad ja nende versioonid: 

Git -	versioon 2.39.5 -	Versioonihaldus

GitHub	- Veebiplatvorm	- Koodihoidla ja koostöö

Render	- Pilveteenus	- Rakenduse majutus

OpenAlex API	- V1 -	Teaduspublikatsioonide metaandmete otsimine

Crossref API	- V1	- DOI põhine metaandmete pärimine

CSS	 - CSS3 -	Kasutajaliidese kujundus

JavaScript 	- ES6 -	Rakenduse loogika

Node.js -	22.19	- JavaScripti käituskeskkond serveris

Express.js	- 4.22.2 -	Veebirakendus ja API

HTML	- HTML5	- Kasutajaliidese struktuur

PostgreSQL	- 18 -	Andmebaas

## Paigaldamine ja arenduskeskkonna seadistamine

### Eeldused

Enne projekti käivitamist peavad olema paigaldatud:

Git

Node.js (LTS versioon soovitatav)

npm

PostgreSQL




### Projekti allalaadimine

git clone https://github.com/rrtlu/SciFilter-Project_

cd SciFilter-Project_/Main/project_Root

npm install


.env faili loomine
Loo projekti kausta Main/project_Root fail nimega .env.

Näidis:
SESSION_SECRET=your_32_byte_secure_hex_string_here
JWT_SECRET=your_other_32_byte_secure_hex_string_here
DATABASE_URL=postgresql://postgres:password@localhost:5432/scifilter

Väärtused asendada enda seadistustele vastavatega.
_SECRET tokenite jaoks saab terminalis kasutada järgneval real olevat käsklust, et saada vajalikud väärtused
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"

Lisa referentsandmebaasi csv fail kausta:
Main/reference_Data/
Kui referentsandmebaas puudub, ei pruugi kvaliteedihindamise funktsioonid töötada.

PostgreSQL andmebaasi loomine
Logi PostgreSQL-i sisse:
psql -U postgres
Loo andmebaas:
CREATE DATABASE scifilter;
Ühenda andmebaasiga:
\c scifilter

Tabelite loomine
Käivita projektiga kaasasolev SQL-skript:
psql -U postgres -d scifilter -f database/schema.sql
Või kopeeri ja käivita järgmine SQL-kood:
--

CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(255) NOT NULL UNIQUE,
    institution VARCHAR(150),
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL
);

Andmebaasi ühenduse seadistamine
Lisa loodud andmebaasi ühendus .env faili:
DATABASE_URL=postgresql://postgres:password@localhost:5432/scifilter

Rakenduse käivitamine
Arenduskeskkonnas:
kaustas Main/
node server.js
või kaustas Main/project_Root/
npm start

Kontrollimine
Kui rakendus käivitub edukalt, peaks see olema kättesaadav aadressil:
http://localhost:5110

Kiire kokkuvõte
Pärast projekti allalaadimist tuleb:
1.	Paigaldada sõltuvused käsuga:
npm install
2.	Luua ja täita .env fail.
3.	Lisada referentsandmebaasi csv fail kausta:
Main/reference_Data/
4.	Luua PostgreSQL andmebaas.
5.	Käivitada tabelite loomise SQL-skript.
6.	Lisada andmebaasi ühendusstring .env faili.
7.	Käivitada rakendus:
node server.js
Seejärel peaks süsteem olema kasutamiseks valmis.

## Viide litsentsile
Projekt kasutab MIT litsentsi. Litsentsi täielik tekst on leitav failist LICENSE. 
