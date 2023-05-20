---
title: Versionsinformation för Adobe Sign för NetSuite
description: Läs om de nya funktionerna och de förändringar som ingår i den nuvarande versionen av Adobe Sign-integreringen för NetSuite.
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 6317723e-447a-4506-a621-4d967bdd6561
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 0%

---

# Versionsinformation för Adobe Sign för NetSuite

## Uppdatera till paket v4.0.4

4.0.4 är helt anpassad för att använda kontospecifika domäner för all ny trafik.

Adobe Sign-ikonen har uppdaterats till den nya bilden.

## Tidigare versioner

### Adobe Sign för NetSuite 4.0.4

4.0.4 är helt anpassad för att använda kontospecifika domäner för all ny trafik.

Adobe Sign-ikonen har uppdaterats till den nya bilden.

### Adobe Sign för NetSuite 4.0.2

Ändrad till **Adobe Sign** (från *Adobe Document Cloud eSign-tjänster*)\
Nu ser du *Adobe Sign* där du tidigare såg *Adobe eSign-tjänster* som bevis för omprofileringen.

### Adobe Sign för NetSuite 4.0.1

På grund av ett API-regressionsfel som introducerades när NetSuite utförde sin plattformsuppdatering har ett nytt paket (v4.0.1) släppts.

Vi rekommenderar att du uppdaterar till det senaste paketet.

### Adobe Sign för NetSuite 4.0

**Lagt till automatisk etablering av användare via NetSuite**

En ny anpassad inställning har lagts till för v4.0. När detta är aktiverat tilldelas användare som skickar avtal i NetSuite automatiskt ett användarkonto för Adobe Document Cloud eSign-tjänster.

**Certifierad med &#39;Built for NetSuite&#39;**

Den här versionen har certifierats som &quot;Built for NetSuite&quot; och uppfyller alla de senaste metoderna för NetSuite-design.

**Varumärket har ändrats till Adobe Document Cloud eSign-tjänster (från EchoSign)**

Du ser nu Adobe Document Cloud eSign-tjänster (eller Adobe eSign-tjänster i korthet) där du tidigare såg Adobe EchoSign som ett bevis på omprofileringen.

**Implementerat förbättrat skydd med OAuth**

För att förbättra datasäkerheten använder eSign-tjänsterna nu OAuth 2.0 för att autentisera ditt Adobe Document Cloud eSign-tjänstkonto i NetSuite. Med det nya protokollet kan NetSuite kommunicera med eSign-tjänster utan att begära ditt lösenord för eSign-tjänsterna. Eftersom känslig information inte delas direkt mellan programmen är det mindre troligt att ditt konto äventyras. Den här förbättringen påverkar inte implementeringen, men du måste göra en engångskonfiguration för att godkänna NetSuite-paketet för kommunikation med Adobe Document Cloud. Detta görs under installationsprocessen. För kunder som uppgraderar från en tidigare version av paketet - v3.5.9 och tidigare - ersätts den tidigare använda API-nyckeln med en OAuth-token som genereras under auktoriseringsprocessen.

**Migrerade eSign-tjänsterna från SOAP API:er till REST API:er**

För att förbättra effektiviteten, flexibiliteten och bearbetningshastigheten har Adobe Document Cloud eSign-tjänster, och följaktligen v4.0-integreringen för NetSuite, migrerats från SOAP-baserade till REST-baserade API:er.

### Adobe Sign för NetSuite 3.0

**Avancerade deltagarroller - godkännare**

* En eller flera mottagare kan markeras som godkännare i ett avtal
* Godkännare måste granska och godkänna dokumentet
* Godkännare kan också behöva fylla i data i avtalet innan de godkänner

**Förhandsgranska dokument eller dra och släpp formulärfält innan de skickas**

Förhandsgranska avtal eller dra och släpp formulärfält innan du skickar dem för signering

**Skicka påminnelse till aktuell signerare**

Skicka en påminnelse direkt till aktuell signerare

**Avancerade autentiseringsprinciper för signerare**

* **Kunskapsbaserad autentisering:** Svara på frågor för att verifiera signeraridentitet
   * Kräver att signerare bevisar sin identitet genom att svara på frågor från hundratals offentliga och kommersiella databaser
   * Namnet på signaturen hämtas från användarens autentiserade namn och kan inte ändras vid signeringstillfället
   * Drivs av RSA
   * KBA-användningen är begränsad per konto och månad. Kontakta försäljningsavdelningen om du vill ha mer information.

* **Webbidentitet:** Logga in med Facebook, LinkedIn, Google eller någon annan webbtjänst från tredje part innan du signerar.

   * Signeraren kan bara signera efter att ha verifierat sin identitet med en webbtjänst från tredje part.
   * Namnet på signaturen hämtas från användarens webbtjänstprofil och kan inte ändras vid signering
   * Granskningsspår registrerar identitetsverifieringsinformation

* **Engångslösenord**
   * Använd autentiseringsmetoder för interna eller externa signerare eller alla signerare. Externa signerare måste använda ett lösenord eller kunskapsbaserad autentisering medan interna signerare inte gör det

**Ytterligare anpassade inställningar**

* Lägg till signerat PDF som en länk till webbadressen eller som en bilaga på NetSuite
* Lägg till granskningsspår till avtalspost - ett avtal har signerats
* Använd transaktionskontakten som signerare som standard, i stället för kundens e-postadress
* Bevilja avsändare alternativet att markera mottagare som godkännare

**Transaktionsfiler**

Du kan välja filer att bifoga från den aktuella transaktionen med den nya listrutan Transaktionsfiler .

**Adobe PDF-certifiering för alla EchoSign-dokument**

* Alla PDF-filer som skickas eller hämtas från EchoSign är certifierade med ett digitalt Adobe EchoSign-certifikat
* Acrobat eller Reader har en certifiering som garanterar att dokumentet inte har manipulerats för att ge ytterligare förtroende och sinnesro

**Samla in stöddokument**

* Avsändare kan samla in ytterligare stöddokument från signerare under signeringen, till exempel ett körkort, ett affärscertifikat med mera.
* Insamlade dokument blir en del av det signerade avtalets officiella protokoll

**Villkorliga datafält**

* Definiera villkorlig logik för avtalsfält
* Villkor kan baseras på värden för ett eller flera fält i avtalet
* Villkoren kan definieras med dra-och-släpp-gränssnittet eller med texttaggar
* Signeraren visas med lämpliga fält när ett dokument signeras baserat på de!ned-villkoren

**Ytterligare förbättringar av EchoSign-formulärfält**

* Listrutor
* Fältmaskering
* Alternativknappar
* Skapa kortare texttaggar för att bevara dokumentstrukturen
