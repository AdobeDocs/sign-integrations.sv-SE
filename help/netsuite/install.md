---
title: Adobe Sign för NetSuite - Handbok för installation och anpassning (v4.0.4)
description: 'Adobe Sign för NetSuite - Handbok för installation och anpassning '
product: Adobe Sign
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
source-git-commit: 924813403d8e13f816347dd548a68a16d78d866e
workflow-type: tm+mt
source-wordcount: '4952'
ht-degree: 0%

---


# Adobe Sign för NetSuite - installations- och anpassningsguide (v4.0.4){#install-customize-netsuite}

## Översikt {#overview}

Adobe Sign för NetSuite är en komplett e-signaturintegrering med NetSuite. Du kan använda integreringen med Adobe Sign för Netsuite för att skicka avtal som kontrakt, offerter och andra dokument som kräver elektroniska signaturer till mottagare direkt från NetSuite. Du kan skapa och skicka Adobe Sign-avtal från kundposter, lead, offerter och andra NetSuite-poster. Adobe Sign uppdaterar NetSuite med aktuell status för avtal och lagrar avtalen med tillhörande NetSuite-poster när de är helt genomförda. Du kan visa historiken för alla avtal som skickas från NetSuite inifrån produkten.

Mer information finns i [versionsinformationen för Adobe Sign för NetSuite](https://experienceleague.corp.adobe.com/docs/sign-integrations/using/netsuite/release-notes.html?lang=en).

## Installera paketet och konfigurera OAuth {#install}

Endast en NetSuite-administratör kan installera eller uppdatera paketet. För att konfigurera OAuth måste NetSuite-administratören ha administratörsåtkomst till Adobe Sign. Innan du installerar paketet på ditt Production-konto bör du installera och testa det på ett NetSuite Sandbox-konto.

Mer information om testning finns i [Skapa ett Adobe Sign-avtal](#createagreement).

>[!CAUTION]
>
>Kunder som uppgraderar till v4.0.4 bör INTE ta bort sin befintliga API-nyckel.
>
>Mer information om hur API-nyckeln används finns i [Ange anpassade inställningar](#configure).

### Installera paketet för första gången

1. Gå till **Customization > SuiteBundler > Search &amp; Install Bundles**.

1. På sidan *Sök- och installationspaket* anger du **Adobe Sign** som nyckelord och väljer **Sök**.

1. Välj **Adobe Sign** paketnamn.

   ![Sök efter paketet](images/search-for-the-bundle.png)

1. På sidan *Paketinformation* väljer du **Installera**.
1. På sidan *Preview Bundle Install* väljer du **Install Bundle**.

   (Du behöver inte ändra något av standardvärdena på sidan)

   ![Installera paketet](images/bundle-details-install.png)

1. I dialogrutan Install väljer du **OK** för att fortsätta.

   Under installationsprocessen visas paketets status som *Väntande*.

   ![Installera paket](images/installing-bundles.png)

1. Om du vill visa en uppdaterad status väljer du **Uppdatera**.

   När paketinstallationen är klar visas *Adobe Sign för NetSuite* på sidan *Installed Bundles*.

   ![Installerade paket](images/installed-bundles.png)

1. Om du redan är ett Adobe Sign-kundkonto följer du stegen för att [konfigurera OAuth efter installation eller uppgradering](#oauth).

   Om du inte har något Adobe Sign-konto kan du [registrera dig för ett Enterprise trial](https://esign.adobe.com/adobe-sign-netsuite-trial-registration.html)-konto för att testa systemet. Aktivera ditt Adobe Sign-konto genom att följa stegen för onlineregistrering.

## Konfigurera OAuth efter installation eller uppgradering {#oauth}

Adobe Sign använder OAuth 2.0 för att autentisera ditt Adobe Sign-konto i NetSuite.

Det här protokollet tillåter att ditt installerade NetSuite-paket kommunicerar med Adobe Sign utan att behöva ange ditt lösenord. Eftersom känslig information inte delas direkt mellan programmen är det mindre troligt att ditt konto utsätts för risker.

Den här autentiseringen påverkar inte implementeringen, men du måste göra en engångskonfiguration efter att du har installerat eller uppgraderat paketet på ditt Production- eller Sandbox-konto.

NetSuite-administratören som konfigurerar OAuth måste också ha en administratörsbehörighet på kontonivå för Adobe Sign.

1. Gå till listsidan *Adobe Sign Config* i NetSuite.

1. Sök efter **Adobe Sign Config** (en anpassad posttyp) med sökfältet i rubriken.

1. På sidan Sökresultat väljer du **Visa** för posten *Adobe Sign Config*.

   ![Sök efter Adobe Sign](images/search-for-adobesignconfig.png)

1. På sidan med konfigurationslistan i Adobe Sign väljer du **Visa** för posten *Använda OAuth för att komma åt Adobe Sign API:er*.

   ![Konfigurationslista för Adobe Sign](images/adobe-sign-configlist.png)

1. På sidan Adobe Sign Config väljer du **Logga in med Adobe Sign**

   ![Logga in ](images/log-in-with-adobesign.png)

1. På inloggningssidan för Adobe Sign som visas anger du dina inloggningsuppgifter och väljer **Logga in**.

   ![autentisera till Adobe Sign](images/8-authenticate-toadobesign-2020.png)

1. På sidan Bekräfta åtkomst (för OAuth) som visas väljer du **Tillåt åtkomst**

   ![Tillåt åtkomst](images/confirm-access.png)

1. När auktoriseringen är klar omdirigeras du tillbaka till Adobe Sign Config-sidan i NetSuite, som visas nedan.

   ![OAuth lyckades](images/successful-oauth.png)

   >[!NOTE]
   >
   >Om du konfigurerar OAuth i ditt Sandbox-konto kommer du att få felmeddelandet&quot;Could not determine customer compid&quot; när auktoriseringen är klar.
   >
   >
   >För att fortsätta måste du ändra kontodomändelen av URL:en (system.netsuite.com) i webbläsaren så att den pekar tillbaka till NetSuite-sandlådan på följande sätt:
   >
   >
   >Ändra:
   >
   >
   >system.netsuite.com/app/site/hosting/scriptlet.nl?script=745&amp;deploy=1&amp;web_access_point=https://echosign.com
   >
   >
   >Till:
   >
   >
   >system.**sandbox.**netsuite.com/app/site/hosting/scriptlet.nl?script=745&amp;deploy=1&amp;web_access_point=https://echosign.com

## Uppdatera paketet (befintliga användare)

NetSuite-uppdateringar släpps regelbundet av Adobe. Befintliga användare av integreringen med Adobe Sign för NetSuite kan uppdatera till det senaste paketet.

>[!CAUTION]
>
>Kunder som uppgraderar till en nyare version bör INTE ta bort sin befintliga API-nyckel.
>
>Mer information om hur API-nyckeln används finns i [Ange anpassade inställningar](#configure).

### Förutsättningar {#prerequisites}


Den tid som krävs för att uppdatera till v4.0.4-paketet beror på antalet avtal som för närvarande har statusen Skickat för signatur. Vanligtvis tar det 7 till 10 minuter att uppdatera 100 avtal. Notera antalet poster som beräknar uppdateringstiden.

Så här avgör du antalet avtal som skickats ut för signering:

1. Navigera till **Anpassning > Listor, Poster och Filer > Posttyper** och leta sedan reda på *Adobe Sign-avtal.*

   Du kan också söka efter Adobe Sign-avtal i sökfältet.

1. För Adobe Sign-avtalsposten väljer du **Sök**.

   ![Sök efter posttyper](images/search-adobe-signagreements.png)

1. I listrutan **Status** väljer du **Skickat för signatur** och sedan **Skicka**.

   ![Skicka ut för underskrift](images/submit-search-foragreements.png)

   Notera antalet poster som beräknar uppdateringstiden.

   ![Notera numret](images/search-results.png)

### Uppdatera paketet {#updating-the-bundle}

1. Gå till **Customization > SuiteBundler > Search &amp; Install > List** och leta reda på ditt aktuella paket, som visas nedan.

   >[!NOTE]
   >
   >Om det finns en ny version av paketet visas ett utropstecken till höger om *Versionsnumret* för det aktuella paketet.

1. Välj **Uppdatera** i listrutan Åtgärd.

   ![Uppdatera åtgärd](images/update-action.png)

1. På sidan Preview Bundle Update väljer du **Update Bundle** utan att ändra något av de standardvärden som visas på sidan.

   Under installationen visas paketets status som *Väntande*.

   ![Uppdatering](images/preveiw-bundles-update.png) av förhandsgranskningspaket.

   >[!NOTE]
   >
   >När du uppdaterar paketet kan du få ett varningsmeddelande enligt nedan. Om du inte har anpassat dina NetSuite e-signaturposter kan du fortsätta. Om du är osäker bör du installera paketet på ett Sandbox-konto för att testa det innan du uppdaterar paketet på ett produktionskonto.
   ![Felmeddelande](images/netsuite-error.png)

1. Om du vill visa en uppdaterad status väljer du **Uppdatera**.

   ![Installera uppgraderingen](images/installing-upgrade.png)

   >[!NOTE]
   >
   >Om uppdateringen verkar ta lång tid på grund av att du har ett stort antal *Skickat för signatur*-avtal, kan du kontrollera **körningsloggen**-fliken för *Adobe Sign Bundle Installation*-skriptet för att avgöra uppdateringens förlopp. (Se [Bestämma uppdateringens förlopp](#determineprogress)för mer information.)

   När paketuppdateringen är klar visas *Adobe Sign för NetSuite* på sidan *Installed Bundles*.

   ![Installerat paket](images/4-installed-bundles.png)

## Konfigurera paketet {#configure}

### Ange egna inställningar  {#set-custom-preferences}

Du kan använda anpassade inställningar för att ange hur avtal ska skapas och lagras i NetSuite. Dessutom gör inställningen *Automatisk etablering av användare i Adobe Sign* att du kan ange om NetSuite-användare ska tilldelas automatiskt i Sign-tjänster när de skickar avtal från NetSuite.

1. Navigera till **Inställningar > Företag > Allmänna inställningar**.
1. Bläddra nedåt på sidan och välj sedan underfliken **Egna inställningar**.

   ![Anpassade inställningar](images/custom-preferences.png)

1. Aktivera och konfigurera dina Adobe Sign-inställningar efter behov:

   * **Ange EchoSign API-nyckel för ditt konto**: Lägg inte till eller redigera något värde i det här fältet.
   * **Använd överordnad postkontakt som signerare**: Om det här alternativet är aktiverat används den överordnade postens kontaktperson som första signerare när avtal skapas. Avsändaren kan enkelt ta bort eller redigera standardsigneraren eller lägga till ytterligare signerare i avtalet innan den skickas.
   * **Använd trans. Kontakta som signerare om det finns**: Den här inställningen är endast giltig om inställningen *Använd överordnad postkontakt som signerare* också är aktiverad. Om det här alternativet är aktiverat används den primära transaktionskontakten som första signerare när ett avtal genereras från en transaktionspost (t.ex. offert). (Se [Transaktionsposter](#transrecords)för mer information.) Om det inte finns någon primär transaktionskontakt, eller om det skickas från NetSuite-objektsposten (t.ex. kundpost, partnerpost), kommer standardmottagaren att vara den primära kontakten för kundens e-post. Avsändaren kan enkelt ta bort eller redigera standardsigneraren eller lägga till ytterligare signerare i avtalet innan den skickas.
   * **Tillåt markering av mottagare som godkännare**: Om det här alternativet är aktiverat kan avsändare markera mottagare som godkännare. Mottagare som har markerats som godkännare kan granska och godkänna avtal, men de behöver inte signera dem. Godkännare kan behöva ange data i fält under godkännandeprocessen.
   * **ID för** önskad avtalsmapp: Används för att ange mappen där de slutgiltiga signerade avtalen ska lagras. Om du inte anger ett värde för det här fältet sparas slutsignerade avtal i samma mapp som originaldokumentfilen som standard. Mappens ID måste vara ett nummer.
   * **Koppla transaktion-PDF** automatiskt: Om det här alternativet är aktiverat bifogas Transaktions-PDF:er automatiskt till avtal när nya avtal skapas från transaktionsposter.
   * **Lägg till signerad PDF som (bifogad fil eller länk)**: Om  ** Lista väljs i listrutan läggs den signerade PDF-filen automatiskt till som en länk till filen. Om *Bifogad fil* väljs i listrutan lagras den signerade PDF-filen i NetSuite som en bilaga i avtalsposten.
   * **Inkludera granskningsspår i PDF med avtal**: Om det här alternativet är aktiverat bifogas PDF-dokument för granskningsspår till avtalsposter när avtalen har signerats.
   * **Identitetsverifieringsmetod gäller för**: Om du aktiverar någon av metoderna för identitetsverifiering bestämmer du vem som får använda ID-verifieringsmetoden. Alternativen är *Alla signerare, Endast externa signerare, *eller *Endast interna signerare*.

   **Metoder för identitetsverifiering** {#identity-verification-methods}

   Du kan välja aktiverade metoder för identitetsverifiering när du skapar ett avtal. Om fler än en metod för identitetsverifiering är aktiverad här, visas alternativet **Verifiera signeraridentitet** på Adobe Sign-avtalssidan.

   * **Aktivera lösenord som krävs för att signera**: Kräv att signerare anger ett engångslösenord som du anger.

   * **Aktivera kunskapsbaserad autentisering**: Kräv att signerare anger namn, adress och eventuellt de fyra sista siffrorna i sitt SSN och svara sedan på en lista med frågor som verifierar den information de lämnat. Finns endast i USA.

   * **Aktivera autentisering** av webbidentitet: Kräv att signerare verifierar sin identitet genom att logga in på någon av följande webbplatser: Facebook, Google, LinkedIn, Microsoft Live, Twitter eller Yahoo!.

   * **Automatisk etablering av användare i Adobe Sign**: Om det här alternativet är aktiverat kommer användare som skickar avtal i NetSuite automatiskt att tilldelas ett Adobe Sign-användarkonto.


1. Välj **Spara** för att spara dina inställningar.

## Konfigurera automatiska statusuppdateringar {#asu}

Med Adobe Sign integreringspaket kan du automatiskt få uppdateringar i NetSuite om status för avtal som har skickats från NetSuite. När den här funktionen är aktiverad återspeglar NetSuite alltid avtalsstatus. Du kan aktivera automatiska statusuppdateringar enligt följande:

1. Navigera till **Inställningar > Företag > Aktivera funktioner.**
1. Välj underfliken **SuiteCloud**.
1. Aktivera följande alternativ:

   * Aktivera alternativet **Egna poster** i SuiteBuilder-avsnittet.

   * I SuiteScript-avsnittet aktiverar du alternativen **Client SuiteScript** och **Server SuiteScript** och accepterar användarvillkoren för båda.

1. Välj **Spara**.

   Alternativen ställs in enligt bilden.

   ![Aktivera funktioner i SuiteCloud](images/enable-suitecloudfeatures.png)

## Objekt och posttyper {#objects}

Adobe Sign integreringspaket visar redan Adobe Sign Agreement-objektet med många vanliga NetSuite-objekt, inklusive: Kund-, offert-, lead-, säljprojekt- och partnerposter. Du kan även använda Adobe Sign-paketet med andra posttyper, inklusive egna poster.

Avtalsfliken kan visas med två typer av NetSuite-poster: Enhet- och transaktionsposter. Vi antar vanligtvis att en transaktionspost är en post (t.ex. offert) som kan konverteras till ett PDF-dokument. En enhetspost kan inte konverteras till en PDF.

## Transaktionsposter {#transrecords}

Om avtalet skapas från en transaktionspost är det första dokumentet i avtalsposten PDF-versionen av posten som det kom från och den första mottagaren är postens e-postadress. Om du inte vill att det första dokumentet ska vara en PDF-version av posten det kommer från går du till **Inställningar > Företag > Allmänna inställningar > Underfliken Anpassade inställningar** och inaktiverar alternativet **Bifoga transaktion-PDF**. Mer information finns i [Ange egna inställningar](#configure).

Under Anpassade inställningar kan du även aktivera alternativet **Använd transaktion. Inställningen Kontakta första signeraren** om du vill att den primära transaktionskontakten ska läggas till automatiskt som första signerare. När den är associerad med en transaktionspost visas knapparna **Avtal** och **Send for Signature**.

![Citat](images/quote.png)

## Enhetsposter {#entity-records}

Om avtalet skapas från en enhetspost är den första mottagaren e-postadressen från posten. När den är associerad med en enhetspost visas bara fliken Avtal.

## Anpassa paketet {#customize}

Att anpassa paketet innehåller följande:

* Distribuera skripten för underfliken Avtal och Send for Signature-knappen för lämpliga posttyper.
* Ange rollbehörigheter för dina Adobe Sign-posttyper.
* Ändra behörigheter för att bevilja åtkomst till underfliken *Avtal* och knappen *Send for Signature*.

![Skript](images/scripts.png)

### Konfigurera Adobe Sign-avtal för ytterligare posttyper  {#configuring-adobe-sign-agreements-for-additional-record-types}

Så här distribuerar du underfliken *Avtal* och knappen *Send for Signature* för lämpliga posttyper:

1. Navigera till **Anpassning > Skript > Skript.**

1. På listsidan *Skript* som visas letar du reda på skriptet som du behöver distribuera och väljer sedan **Visa**.

   * Om du vill lägga till *Send for Signature*-knappen väljer du **Adobe Sign Estimattningsknapp**-skript.

   * Om du vill lägga till fliken *Avtal* väljer du **Adobe Sign Agreement Loader**-skript.

1. Välj **Distribuera skript** på skriptsidan.

   ![Distribuera skript](images/deploly-script.png)

1. Gör följande på sidan Skriptdistribution:

   * Välj posttyp i listan *Gäller för*.
   * Du kan också ange ett skriptdistributions-ID.

      Mer information finns i avsnittet *Creating a Custom Script Deployment ID* i hjälpcentret för NetSuite. Om du inte anger något ID genereras ett.

   * Markera kryssrutan **Distribuerad**.

   ![Skriptdistribution](images/execute-as-admin.png)

   * Ange *Status* till **Släppt**.

      Du behöver inte ange en *händelsetyp* eller *loggnivå*.

   * I listrutan *Kör som roll* väljer du **Kör som administratör**.

   * Med underfliken **Målgrupp** aktiv (aktiv som standard) väljer du de specifika roller eller användare som du vill ge åtkomst till. Om du vill ge åtkomst till alla roller och användare aktiverar du respektive **Välj alla** alternativ.

   * Välj **Spara**. När ändringsbekräftelsen visas väljer du **Gå tillbaka**.


1. Välj **Lista** högst upp på sidan Skriptdistribution för att komma tillbaka till listsidan *Skript*.
1. Upprepa steg 2 och 3 ovan för det andra skriptet.

## Ange rollbehörigheter för Adobe Sign-posttyper  {#setting-role-permissions-for-adobe-sign-record-types}

De flesta NetSuite-roller bör ha behörighet att använda Adobe Sign utan ytterligare anpassningar. Du kan dock behöva bevilja behörigheter för ytterligare anpassade roller som har skapats.

1. Navigera till **Anpassning > Listor, Poster och filer > Posttyper**.

   ![SiteBuilder - anpassade poster](images/sitebuilder-customrecords.png)

   >[!NOTE]
   >
   >Om du inte kan se *Posttyper* går du till **Inställningar > Företag > Aktivera funktioner > fliken Creative Cloud** och aktiverar alternativet *Anpassade poster*.

1. På sidan *Posttyper* väljer du **Adobe Sign Agreement** för att välja det

   ![Avtalsposttyper](images/search-adobe-signagreementsforedit.png)

1. På sidan *Anpassad posttyp* väljer du **Använd behörighetslista** i listrutan *Åtkomsttyp*.

   ![Anpassad posttyp](images/custom-record-type.png)

   >[!NOTE]
   >
   >Posttypen *Adobe Sign Agreement* är den enda Adobe Sign-posttypen som krävde åtkomsttypen *Använder behörighetslista*.
   >
   >
   >I steg 6 finns instruktioner om hur du ställer in åtkomsttypen för andra posttyper i Adobe Sign.

1. Välj underfliken **Behörigheter**.

   Listan över roller och behörigheter visas.

   ![Roller och behörigheter](images/roles-and-permissions.png)

1. Ange behörigheter enligt följande för de ytterligare anpassade roller som läggs till posttypen&quot;Adobe Sign Agreement&quot;.

   >[!NOTE]
   >
   >Mer information finns i avsnittet *[Konfigurera en behörighetslista för en anpassad posttyp](https://system.netsuite.com/app/help/helpcenter.nl?fid=section_N2879931.html)* i hjälpcentret för NetSuite

   1. Välj rollen i listan *Roll*.
   1. Ange *Nivå* till **Fullständig**
   1. Ange *standardformulär* till **EchoSign-avtalsformulär**
   1. markera kryssrutan *Begränsa formulär*
   1. välj **Lägg till** för att spara ändringarna för rollraden

   ![Ange behörigheter](images/set-permissions.png)

   Den nya raden visas enligt nedan:

   ![Ange behörigheter för typ av avtalspost](images/set-permissions-foragreementrecordtype.png)

   Upprepa steg a till och med e ovan för alla andra anpassade roller.

   * Välj **Spara** på sidan *Anpassad posttyp* när behörigheter för alla roller har angetts.

   Sidan *Kundposttyp* visas igen.

1. Upprepa steg 1 till 3 ovan för att ställa in *åtkomsttypen* för alla andra Adobe Sign-posttyper till

   **Ingen behörighet krävs.** Detta gäller följande posttyper:

   * Adobe Sign Config
   * Adobe Sign-dokument
   * Adobe Sign Event
   * Adobe Sign
   * Adobe Sign-skriptfel
   * Adobe Sign Signerat avtal
   * Adobe Sign Signer

### Bevilja åtkomst till fliken Avtal och knappen Send for Signature  {#granting-access-to-the-agreement-tab-and-send-for-signature-button}

Adobe Sign integreringspaket visar redan Adobe Sign Agreement-objektet med många vanliga NetSuite-objekt (Kund, Uppskattning [Citat], Lead osv.). Underfliken *Avtal* aktiveras automatiskt för följande typer av objekt: Kund, lead, säljprojekt, partner, potentiell kund, offert och leverantörsfaktura.

Knappen *Send for Signature* aktiveras automatiskt **endast för offertobjektet**.

NetSuite-administratörer kan utöka möjligheten att skapa avtal till ytterligare CRM-objekt genom att ändra behörigheter för att lägga till knappen *Avtal*, *Send for Signature* eller båda till dessa objekt.

#### Ändra behörigheter för att bevilja åtkomst till knappen Send for Signature  {#modifying-permissions-to-grant-access-to-the-send-for-signature-button}

1. Navigera till **Anpassning > Skript > Skript**.

   Listsidan *Skript* visas.

   * Om det behövs använder du filtren för att hitta Adobe Sign-skripten

1. På sidan *Skript* letar du reda på skriptet *Adobe Sign Estimat Button* (styr *Send for Signature*-knappen) och väljer sedan **Visa**.

   ![Visa Adobe Sign Estimates-knapp](images/view-adobe-sign-estimatesbutton.png)

1. Gör följande på sidan *Skript*:

   * välj underfliken **Distributioner**

   * Under &quot;*Gäller för*&quot; väljer du länken för den entitet som du vill ändra

      * **Quotein** this example

   ![välj fliken Distribution](images/click-the-deploymentssub-tab.png)

   * välj knappen **Redigera** på sidan *Skriptdistribution*

   ![Redigera skriptdistribution](images/edit-script-deployment.png)

   * När underfliken **Målgrupp** är aktiv väljer du de specifika roller eller användare som du vill ge åtkomst till.

      * Om du vill ge åtkomst till alla roller och användare aktiverar du respektive **Välj alla** alternativ
   * välj **Spara**

   ![Välj de specifika rollerna](images/save-script-deployment-quote.png)

#### Ändra behörigheter för att bevilja åtkomst till avtalsfliken  {#modifying-permissions-to-grant-access-to-the-agreements-tab}

1. Navigera till **Anpassning > Skript > Skript**
1. På sidan *Skript* letar du reda på skriptet *Adobe Sign Agreement Loader* (styr fliken *Avtal*)

   * välj **Visa**

1. Gör följande på sidan *Skript*:

   1. välj underfliken **Distributioner**
   1. Under &quot;*Gäller för*&quot; väljer du länken för entiteten som du vill ändra åtkomsten till
   1. På sidan *Skriptdistribution *väljer du knappen **Redigera**

   1. Med underfliken **Målgrupp** aktiv (den är aktiv som standard) väljer du de specifika roller eller användare som du vill ge åtkomst till. Om du vill ge åtkomst till alla roller och användare aktiverar du respektive **Välj alla** alternativ

   1. välj **Spara**

## Använda paketet Adobe Sign för NetSuite

För att kunna skicka avtal från NetSuite och få uppdateringar för dessa avtal måste användarna ha samma inloggnings-ID (e-postadress) i NetSuite och i Adobe Sign.

### Skapa ett Adobe Sign-avtal

När du har installerat ett nytt paket i en sandlåda eller ett produktionskonto bör du testa paketet genom att skapa ett nytt avtal. Du kan skapa Adobe Sign-avtal från en enhetspost, från en transaktionspost eller som ett fristående avtal.

>[!NOTE]
>
>Processen för att skapa ett avtal varierar något beroende på hur det skapas. Den allmänna processen är att ange alternativ för avtalet, lägga till ett eller flera avtalsdokument och ange mottagarna. Processen som beskrivs nedan förutsätter att du skapar avtalet från en kundpost.

1. Välj eller skapa en kundpost som du vill skicka ett avtal från, eller välj en annan NetSuite-posttyp som har fliken Avtal aktiverad.

1. Välj underfliken **Avtal** i posten.
1. välj **Nytt avtal**.

   ![Nytt avtal](images/new-agreement.png)

1. På sidan *Adobe Sign Agreement* väljer du **Redigera**.

   ![Redigera nytt avtal](images/edit-new-agreement.png)

1. Ange alternativen för ditt avtal enligt följande:

   * **Avtalsnamn** — Ange ett namn för avtalet.
   * **Meddelande**-Ange ett anpassat meddelande för mottagaren.
   * **Typ av signatur** — Välj typ av signatur som accepteras för dokumentet. Alternativen är *e-signatur* och *Fax-signatur*.

   * **Jag måste också signera det här avtalet** — Aktivera det här alternativet för att ange att avsändaren också måste signera avtalet.
   * **Signaturordning**- Om alternativet  *Jag måste signera det här* avtalet är aktiverat väljer du i vilken ordning som avsändaren och mottagarna ska signera. Alternativen är&quot;Jag signerar, sedan mottagare signerar&quot;,&quot;Mottagare signerar, sedan signerar&quot; och&quot;Ingen&quot;.

   * **Förhandsgranska dokument- eller positionssignaturer (eller formulärfält)** — Aktivera det här alternativet om du vill tillåta avsändare att förhandsgranska avtalet och tillåta dem att lägga till fält (dra och släpp signatur, initialfält och andra formulärfält) i avtalet innan det skickas till mottagarna.
   * **Bekräfta signeraridentitet** — Aktivera det här alternativet och välj sedan ett av följande alternativ för identitetsverifiering

      * Det här alternativet visas bara när fler än en av de tre verifieringsmetoderna för signeraridentitet som anges nedan har aktiverats i Anpassade inställningar. (Mer information finns i [Ange egna inställningar](#customize).) Om endast en inställning är aktiverad visas inte alternativet **Verifiera signeraridentitet**.

   **Metoder för identitetsverifiering**

   * **Lösenord krävs för att signera** — Kräv att signerare anger ett engångslösenord som du anger.
   * **Kunskapsbaserad autentisering** — Kräv att signerare anger namn, adress och eventuellt de fyra sista siffrorna i sitt SSN och svara sedan på en lista med frågor som verifierar den information de lämnat. Finns endast i USA.
   * **Webbidentitetsautentisering**  - Kräv att signerare verifierar sin identitet genom att logga in på någon av följande webbplatser: Facebook, Google, LinkedIn, Twitter, Yahoo! eller Microsoft Live.
   * **Lösenord krävs för att visa PDF**  - Aktivera det här alternativet om du vill att en mottagare ska ange ett lösenord innan ett PDF-dokument av avtalet eller det signerade avtalet öppnas. Den PDF-fil som skickas till alla krypteras och det här lösenordet krävs för att öppna den. Tappa inte bort ditt lösenord eftersom det inte kan återställas. Om du skulle förlora lösenordet måste du ta bort transaktionen och börja om.
   * **Lösenord/Bekräfta lösenord** — Om  *Lösenordet som krävs för att visa* PDF-alternativet är aktiverat anger du lösenordet som ska användas för att visa avtalet.
   * **Påminn mottagare att signera** — Ange om och hur ofta påminnelser skickas till mottagare. Alternativen är *Aldrig*, *Dagligen* eller *Veckovis*.
   * **Språk:** Ange på vilket språk signeringssidan och e-postmeddelanden ska visas för mottagarna.
   * **Värdsignering för den första signeraren**  - Aktivera det här alternativet om du vill tillåta avsändarens personliga signering för den första signeraren.
   * **Dagar till signeringsdeadline** — Ange ett heltal för att ange signeringsdeadline för avtalet (dagens datum + antal dagar).
   * **Överordnad post** — Du kan också välja en överordnad post för att länka den till avtalet.

   ![Konfigurera avtal](images/configure-agreement-2.png)

1. Välj fliken **Dokument**.

   ![Fliken Dokument](images/documents-tab.png)

1. Bifoga ett befintligt dokument från filskåpet med listrutan *Adobe Sign-dokument* på underfliken **Dokument** och välj sedan *Bifoga*.

   Du kan också klicka på **Nytt Adobe Sign-dokument** för att komma åt sidan *Adobe Sign-dokument* och sedan skriva namnet på ett dokument i NetSuite-arkivet, välja filer från din transaktionspost (om det är tillämpligt) eller bifoga ett nytt dokument.

   Du kan lägga till flera dokument i ett avtal.

1. Välj **Underfliken Mottagare** och ange mottagare genom att antingen välja från kontaktlistan eller skriva en e-postadress.

   ![Lägg till mottagare](images/add-recipients.png)

   Var och en av dina mottagare kan markeras som signerare eller CC. Om den anpassade inställningen *Tillåt markering av mottagare som godkännare* är aktiverad, kan mottagare även markeras som godkännare. Mer information finns i [Ange egna inställningar](#customize).

   * **Signerare** måste signera avtalet.
   * **Godkännare** måste godkänna, men inte signera avtalet, och kan också behöva lägga till data i ett avtal.
   * **CC-** mottagare meddelas om avtalsuppdateringar och när avtalet har signerats och slutförts. CC-mottagare är inte part i signatur- eller godkännandeprocessen.

      Om den anpassade inställningen *Använd överordnad postkontakt som signerare* är aktiverad fristående eller tillsammans med *Använd trans. Kontakt som signerare*-inställning. Den första mottagaren är standardinställd, men kan ändras.

1. Välj **Lägg till** efter varje mottagares inmatning.

1. Välj **Spara** för att spara avtalet.

### Skicka avtal för signering

När avtalet är klart att skickas väljer du knappen **Send for Signature**.

* Om alternativet *Förhandsgranska dokument- eller positionssignaturer* är aktiverat klickar du på **Send for Signature**. Förhandsgranska dokumentet i det fönster som öppnas eller dra formulärfälten till dokumentet innan det skickas. Välj **Skicka** för att skicka avtalet till mottagaren.

* Om alternativet *Värdsignering för första signeraren* är aktiverat klickar du på **Send for Signature**. I det fönster som öppnas tillåter du att signeraren signerar dokumentet med avsändaren närvarande.

   En *värdsignering för aktuell signerare*-länk visas också bredvid fältet *Värdsignering för första signeraren*, som kan nås tills dokumentet har signerats. Använd den här länken för att lagra avtalssignaturer för flera signerare eller för att öppna popup-fönstret igen om det stängs av misstag.

När avtalet har skickats får mottagarna ett e-postmeddelande som informerar dem om de dokument som väntar på att de ska signera.

När mottagarna har signerat dokumentet får avsändaren ett e-postmeddelande om att dokumentet har signerats.

#### Skicka från en offert

Adobe Sign har en direkt integrering med offerter i NetSuite så att en PDF-fil av offerten automatiskt genereras och bifogas till avtalsposten.

När du visar en offert väljer du **Send for Signature**. Den genererar och visar offerten som är kopplad till avtalet. Du kan också lägga till knappen *Send for Signature* till andra transaktionsposttyper. Se [Objekt och posttyper](#objects)för mer information.

![Citat - Send for Signature](images/quote-send-forsignature.png)

### Spåra status och skicka påminnelser

När du har skickat ett avtal:

* Dokumentstatusen ändras till *Skickat för signatur* i avsnittet Avtalsinformation
* Knappen *Send for Signature* ska ersättas med följande tre knappar:

   * **Uppdateringsstatus** — Välj den här knappen om du vill uppdatera statusen manuellt om statusuppdateringar inte har konfigurerats. Mer information finns i [Konfigurera automatiska statusuppdateringar](#asu)för mer information.
   * **Skicka påminnelse** — Välj den här knappen om du vill skicka en påminnelse till den aktuella signeraren.
   * **Avbryt avtal** — Klicka på den här knappen om du vill avbryta ett avtal. Ett avtal kan avbrytas efter att det har skickats för en signatur om alla mottagare ännu inte har signerat.

![Skickat för signatur](images/out-for-signature.png)

En ny underflik i *Händelser* visas i avtalsposten där du kan spåra avtalets status.

Du kan se en historik över avtalshändelser, som innehåller information om när avtalet skickades, visades och signerades.

![Signerade avtalshändelser](images/agreement-events.png)

När avtalet har signerats:

* Dess status ändras till *Signerad*.
* Du kan länka tillbaka till den överordnade posten för det här avtalet med hjälp av länken.
* Du kan använda nedladdningslänkarna under Signerat dokument och Granskningsspår för att komma åt dessa dokument.
* Ytterligare en underflik i *Signerat dokument* visar miniatyrer av det signerade dokumentet.

![Signerat avtal](images/signed-agreement.png)

>[!NOTE]
>
>När ett avtal har skickats för signering kan du inte redigera posten. Detta är för att bevara händelseregistret.

## Avinstallera paketet

Följ stegen i hjälpen för NetSuite för att avinstallera paketet. Mer information finns i avsnittet *[Avinstallera ett paket](https://docs.oracle.com/cloud/latest/netsuitecs_gs/NSBDL/NSBDL.pdf)* i hjälpcentret för NetSuite.

När du avinstallerar paketet tas de osignerade avtalen bort. De signerade avtalen och deras motsvarande gransknings-PDF-filer påverkas inte.

Avinstallera INTE paketet om du behöver behålla dina osignerade avtal.

## Felsökning

### Kontrollera uppdateringens förlopp

Om uppdateringen verkar ta längre tid än så kan du kontrollera uppdateringens förlopp på underfliken Körningslogg för Adobe Sign Bundle Installation-skriptet enligt följande:

1. Navigera till **Anpassning > Skript > Skript**.
1. På sidan *Skript* letar du reda på skriptet *Adobe Sign Bundle Installation* och väljer sedan **Redigera**.
1. På sidan *Skript* väljer du underfliken **Körningslogg**.
1. Välj **Uppdatera**.

   Körningsloggen uppdateras med aktuell status. Kolumnen *Detaljer* visar status för uppdateringar av dina avtal.

   ![Uppdateringsförlopp](images/refresh-progress.png)

### Lös problem med åtkomsttoken

Du kan stöta på ett meddelande om att den angivna åtkomsttoken är ogiltig eller har upphört att gälla vid interaktion med avtal.

Detta kan bero på följande:

* NetSuite/Adobe Sign-administratören som konfigurerade OAuth har återkallat åtkomsttoken
* Åtkomsttoken har upphört att gälla eftersom inga avtal har skickats från NetSuite under de senaste 60 dagarna
* NetSuite-/Adobe Sign-administratören har inte slutfört den ursprungliga OAuth-konfigurationen

Åtgärda problemet genom att köra OAuth-konfigurationsprocessen igen. Mer information finns i [Konfigurera OAuth efter installation eller uppgradering](#oauth).

![Ogiltig token](images/invalid-token.png)

### Åtgärda problem med dokumentstatus {#resolvestatus}

Om [automatiska statusuppdateringar](#asu) har konfigurerats men avtalsstatusen inte uppdateras efter att avtalen har skickats kan du prova följande:

1. Kontrollera körningsloggen för distributionen av *Adobe Sign External Update*-skriptet för att se om du tar emot samtal från Adobe Sign på följande sätt:

   1. Navigera till **Anpassning > Skript > Skriptdistributioner**
   1. På sidan *Skriptdistributioner* letar du reda på skriptet *Adobe Sign External Update* och väljer sedan **Redigera**
      1. På sidan *Skriptdistribution* väljer du underfliken **Körningslogg**.
      * Du bör se en *Uppdaterad avtalspost*-post för varje avtals-ID


1. Kontrollera om det finns några fel i distributionsloggen för *Adobe Sign Update Agreements*-skriptet:

   1. Navigera till **Anpassning > Skript > Skriptdistributioner**.
   1. På sidan *Skriptdistributioner* letar du reda på skriptet *Adobe Sign Update Agreements* med statusen &quot;Scheduled&quot; och väljer sedan **Redigera**.
   1. På sidan *Skriptdistribution* väljer du underfliken **Körningslogg**.
   1. Under *Skriv* väljer du **Fel** för att filtrera resultaten.

1. Slutligen kontrollerar du om det finns fel i körningsloggen för *Adobe Sign Manager*-skriptet genom att följa instruktionerna i steg 2 ovan.

### Åtgärda MIME-typfel  {#resolving-mime-type-errors}

Om du får ett MIME-typfel när du skickar ett avtal kan det bero på att namnet i fältet Filnamn inte matchar filnamnet och tillägget för den överförda filen. Om du lämnar fältet Filnamn tomt fylls automatiskt filnamnet och filnamnstillägget i.

### Visa skriptloggar {#viewing-script-logs}

Du kan också visa loggarna för distributionskörning för skript som inte är relaterade till dokumentstatusproblem. Mer information finns i [Lösa problem med dokumentstatus](#resolvestatus).

1. Navigera till **Anpassning > Skript > Skript**.

   Listsidan *Skript* visas. Använd vid behov filtren för att hitta rätt skript.

1. Välj **Visa** för motsvarande skript.

1. Markera underfliken **Körningslogg** på sidan för att visa skriptloggen.

## Support {#support}

Gå till [Adobe Sign supportportal](https://adobe.com/go/adobesign-support-center_se) för att få tillgång till Frågor och svar, dokumentation, kunskapsbasartiklar eller kontakta Adobe Support.
