---
title: Versionsinformation om Adobe Sign för NetSuite
description: Läs om de nya funktionerna och ändringarna som ingår i den aktuella versionen av Adobe Sign-integreringen för NetSuite.
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 6317723e-447a-4506-a621-4d967bdd6561
source-git-commit: f8d0bc748872e675dc1c638eb4050efe9e3147ef
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 5%

---

# Versionsinformation om Adobe Sign för NetSuite

## Uppdatering till paketet v4.0.4

4.0.4 är helt anpassat för att använda kontospecifika domäner för all nygenererad trafik.

Adobe Sign-ikonen har uppdaterats till den nya bilden.

## Tidigare versioner

### Adobe Sign för NetSuite 4.0.4

4.0.4 är helt anpassat för att använda kontospecifika domäner för all nygenererad trafik.

Adobe Sign-ikonen har uppdaterats till den nya bilden.

### Adobe Sign för NetSuite 4.0.2

Ommärkt till **Adobe Sign** (från *Adobe Document Cloud eSign-tjänster*)\
Du ser nu *Adobe Sign* där du tidigare såg *Adobe eSign-tjänster* som ett bevis på den nya varumärkningen.

### Adobe Sign för NetSuite 4.0.1

På grund av ett API-regressionsfel som introducerades när NetSuite utförde sin plattformsuppdatering har ett nytt paket (v4.0.1) släppts.

Kunder uppmanas att uppdatera till det senaste paketet.

### Adobe Sign för NetSuite 4.0

**Tillagd automatisk etablering av användare via NetSuite**

En ny anpassad inställning har lagts till för v4.0. När det här alternativet är aktiverat kommer användare som skickar avtal i NetSuite automatiskt att tilldelas ett Adobe Document Cloud-användarkonto för eSign-tjänster.

**Certifierad med&quot;Built for NetSuite&quot;**

Den här versionen klarade certifieringen&quot;Built for NetSuite&quot; och uppfyller alla de senaste metodstrategierna för NetSuite-design.

**Ommärkt till Adobe Document Cloud eSign-tjänster (från EchoSign)**

Nu kan du se Adobe Document Cloud eSign-tjänster (eller Adobe eSign-tjänster för kort tid) där du tidigare såg Adobe EchoSign som ett bevis på varumärkesändringen.

**Implementerad förbättrad säkerhet med OAuth**

För att förbättra datasäkerheten använder nu eSign-tjänsterna OAuth 2.0 för att autentisera ditt Adobe Document Cloud eSign-konto inom NetSuite. Med det nya protokollet kan NetSuite kommunicera med eSign-tjänster utan att begära ditt lösenord för eSign-tjänsterna. Eftersom känslig information inte delas direkt mellan programmen är det mindre troligt att ditt konto utsätts för risker. Den här förbättringen påverkar inte implementeringen, men du måste göra en engångskonfiguration för att godkänna att ditt NetSuite-paket kommunicerar med Adobe Document Cloud. Detta görs under installationen. För kunder som uppgraderar från en tidigare version av paketet - v3.5.9 och tidigare - ersätts den API-nyckel som tidigare använts av en OAuth-token som genererats under auktoriseringsprocessen.

**Migrerade eSign-tjänsterna från SOAP API:er till REST API:er**

För att öka effektiviteten, flexibiliteten och bearbetningshastigheten har Adobe Document Cloud eSign-tjänsterna, och följaktligen även v4.0-integreringen för NetSuite, migrerats från SOAP-baserade till REST-baserade API:er.

### Adobe Sign för NetSuite 3.0

**Avancerade deltagarroller - godkännare**

* En eller flera mottagare kan markeras som godkännare i ett avtal
* Godkännare måste granska och godkänna dokumentet
* Godkännare kan också behöva fylla i data i avtalet innan de godkänner det

**Förhandsgranska dokument eller dra och släpp formulärfält innan de skickas**

Förhandsgranska avtal eller dra och släpp formulärfält innan de skickas för signering

**Skicka påminnelse till aktuell signerare**

Skicka påminnelse direkt till den aktuella signeraren

**Avancerade autentiseringsprinciper för signerare**

* **Kunskapsbaserad autentisering:** Besvara frågor för att verifiera signeraridentitet
   * Kräver att signerare bevisar sin identitet genom att svara på frågor som hämtats från hundratals offentliga och kommersiella databaser
   * Namnet på underskriften hämtas från användarens autentiserade namn och kan inte ändras vid tidpunkten för undertecknandet
   * Powered by RSA
   * KBA-användningen är begränsad per konto och månad. Kontakta försäljningen för mer information.

* **Webbidentitet:** Logga in med Facebook, LinkedIn, Google eller någon annan tredjepartstjänst innan du signerar.

   * Signerare kan bara signera efter att ha verifierat sin identitet med hjälp av en webbtjänst från tredje part.
   * Namn på signatur hämtas från användarens webbtjänstpro!le och kan inte ändras vid tidpunkten för signering
   * Granskningsspårning samlar in identitetsverifieringsinformation

* **Engångslösenord**
   * Använd autentiseringsmetoder för interna eller externa signerare eller alla signerare. Externa signerare måste använda ett lösenord eller använda kunskapsbaserad autentisering medan interna signerare inte gör det

**Ytterligare anpassade inställningar**

* Lägg till signerat PDF som en länk till URL-adressen eller som bilaga i NetSuite
* Lägg till granskningsspår i avtalsposten ett$er-avtal har signerats
* Använd transaktionskontakten som signerare i stället för som kundens e-postadress
* Bevilja avsändare möjligheten att markera mottagare som godkännare

**Transaktionsfiler**

Du kan välja filer som ska bifogas från den aktuella transaktionen med den nya listrutan Transaktionsfiler.

**Adobe PDF-certifiering för alla EchoSign-dokument**

* Alla PDF-filer som skickas eller hämtas från EchoSign är certifierade med ett digitalt Adobe EchoSign-certifikat
* Acrobat eller Reader visar en certifiering som garanterar att dokumentet inte har manipulerats för att öka tillit och sinnesro

**Samla in stöttande dokument**

* Avsändare kan samla in ytterligare stöddokument från signerare vid signering, t.ex. ett körkort, ett affärscertifikat med mera.
* Insamlade dokument blir en del av det undertecknade avtalets officiella register

**Villkorliga datafält**

* Definiera villkorlig logik för avtalsfält
* Villkoren kan baseras på värden för ett eller flera fält i avtalet
* Villkoren kan definieras genom dra-och-släpp-gränssnittet för formulärredigering eller via texttaggar
* Undertecknaren visas med rätt fält när ett dokument signeras baserat på de!end-villkor

**Förbättringar med ytterligare EchoSign-formulärfält**

* Listrutor
* Fältmaskering
* Alternativknappar
* Skapa kortare texttaggar för att bibehålla dokumentstrukturen
