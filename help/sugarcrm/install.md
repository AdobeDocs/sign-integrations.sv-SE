---
title: Adobe EchoSign for SugarCRM
description: Installationshandbok för att aktivera Adobe Sign-integrering med SugarCRM
product: Adobe Sign
content-type: reference
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
source-git-commit: 40fe3649aab0499ce8e5fbd1b11308ffbd759a44
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 1%

---


# [!DNL SugarCRM]  Installationshandbok {#sugarcrm-install-guide}

[Kontakta kundtjänst](https://adobe.com/go/adobesign-support-center_se)

Adobe [!DNL EchoSign] för [!DNL SugarCRM] är en ledande lösning för e-signaturer och webbavtal som levererar automatisering av elektroniska signaturer i [!DNL SugarCRM] för e-signaturer och faxsignaturer. Användare kan skicka kontrakt direkt från SugarCRM, visa kontraktshistorik och spara e-signerade kontrakt med associerade konton, kontakter, offerter och mycket mer.
Adobe [!DNL EchoSign] för [!DNL SugarCRM] finns för alla SugarCRM-versioner som stöds, inklusive 6.3-6.7 för on-demand- eller on-demand-lösningar.

Det här dokumentet är en guide för [!DNL SugarCRM]-administratörer som lär sig hur du installerar och konfigurerar plugin-programmet Adobe [!DNL EchoSign] för [!DNL SugarCRM].

## Installera det här plugin-programmet {#install-plugin}

1. Hämta arkivfilen [!DNL EchoSign] för [!DNL SugarCRM] Adobe från [SugarExchange-listan](http://www.sugarexchange.com/product_details.php?product=1123).
1. Logga in på [!DNL SugarCRM] med ditt administratörskonto.
1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Modulinläsare]**.

   ![Bild](images/module-loader.png)

1. Om du vill överföra arkivfilen för plugin-programmet Adobe [!DNL EchoSign] för [!DNL SugarCRM] väljer du **[!UICONTROL Bläddra]**, markerar arkivfilen och väljer sedan **[!UICONTROL Överför]**.
1. När arkivfilen har överförts väljer du **[!UICONTROL Installera]** för att påbörja installationen.
1. Granska villkoren och välj sedan **[!UICONTROL Acceptera]** > **[!UICONTROL Genomför]**.
1. Om plugin-programmet installeras utan problem visar förloppsindikatorn att det lyckades till 100 %.  Om förloppsindikatorn inte når 100 % väljer du **[!UICONTROL Visa logg]** för att se det fel som SugarCRM har råkat ut för.

   ![Bild](images/display-log.png)

1. Efter installationen går du till **[!UICONTROL Administration > Reparera]** och väljer **[!UICONTROL Snabbreparation och Återskapa]**.

>[!NOTE]
>
>Om du installerar plugin-programmet på [!DNL SugarCRM] OnDemand ska du skicka en supportanmälan med [!DNL SugarCRM] för att tillfälligt ta bort begränsningarna för paketkontrollen för OnDemand så att paketet kan installeras. Detta är en del av standardprocessen.

## Uppgradera plugin-programmet {#upgrade-plugin}

Om du uppdaterar plugin-programmet Adobe [!DNL EchoSign] för [!DNL SugarCRM] till en nyare version bör du installera det utan att avinstallera den tidigare versionen.
När du har uppgraderat plugin-programmet går du till **[!UICONTROL Administration]** > **[!UICONTROL Reparera]** och väljer **[!UICONTROL Snabbreparation och Återskapa]**.

**Obs!** Om du avinstallerar ett tidigare plugin-program ska du inte ta bort tabellerna under avinstallationen. Annars kan du förlora [!DNL EchoSign] avtalsdata.

## Konfigurera plugin-programmet {#configure-plugin}

1. Om du redan är kund hos Adobe [!DNL EchoSign] fortsätter du till steg 2.

   Om du inte har ett [!DNL EchoSign]-konto kan du [registrera dig för en kostnadsfri 14-dagars testversion](https://sugarcrmintegration.echosign.com/public/login) och aktivera ditt Adobe [!DNL EchoSign]-konto genom att följa stegen för onlineregistrering.
1. Logga in på [Echo Sign-konto](http://www.echosign.com) och följ dessa steg:
   1. Välj fliken **[!UICONTROL Konto]**.
   1. Välj **[!UICONTROL EchoSign API]** nere till vänster.
   1. Välj **[!UICONTROL Aktivera API-åtkomst]** och hämta API-nyckeln från sidan.

   ![Bild](images/enable-api-access.png)

1. I SugarCRM går du till **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]** och anger API-nyckeln i fältet **[!UICONTROL EchoSign API Key]**.
1. Du kan också konfigurera plugin-programmet med följande inställningar:

   1. Bifoga automatiskt PDF när du skapar ett avtal från en offert: Välj om du vill bifoga en PDF i offerten automatiskt om en [!DNL SugarCRM]-användare skapar ett EchoSign-avtal från offertmodulen.
   1. Hantera mottagarlista: Välj vilka moduler som ska visas i underpanelen Mottagare i modulen [!DNL EchoSign] Avtal. Då läggs även underpanelen [!DNL EchoSign] Avtal till i de modulerna.
   1. Lägg till skicka-knapparna till följande moduler: Välj om du vill att knappen/åtgärden Skapa [!DNL EchoSign] avtal ska inkluderas i offertmodulens primära åtgärder.
   1. Välj **[!UICONTROL Spara]** för att spara dina inställningar.

**Obs!** Adobe  [!DNL EchoSign] för  [!DNL SugarCRM] plugin-programmet kräver  [PHP SOAP-tillägget](http://www.php.net/manual/en/book.soap.php). Om du vill aktivera SOAP-stöd konfigurerar du PHP med enable-soap.

## Hämta avtalsuppdateringar (för [!DNL SugarCRM] version 6.3 eller senare) {#get-agreement-updates}

För version 6.3 och senare kan du använda följande två alternativ för att hämta avtalsuppdateringar. I tidigare versioner av SugarCRM innehåller plugin-programmet som standard bara återkopplingsmetod (alternativ 1).

### Alternativ 1: Ställ in återanropsmetod för att skicka uppdateringar till EchoSign

Om din webbplats är offentlig kan du låta Adobe EchoSign pinga din [!DNL SugarCRM]-instans när en ny händelse inträffar. [!DNL SugarCRM] uppdaterar sedan avtalsstatus, händelser och hämtar det signerade dokumentet (om det signeras) automatiskt och i realtid. (Om du befinner dig bakom en brandvägg måste du vitlista IP-adresserna för [!DNL EchoSign]-servern eller använda metoden för schemalagda jobb för att uppdatera EchoSign-avtal som beskrivs i nästa avsnitt i den här handboken).

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign-inställningar]**.
1. Markera kryssrutan **[!UICONTROL Använd EchoSigns callback-metod]** för att uppdatera händelser och status för avtal.
1. Välj **[!UICONTROL Spara]**.

### Alternativ 2: Konfigurera ett schemalagt jobb för [!DNL SugarCRM] instanser bakom en brandvägg

Plugin-programmet [!DNL EchoSign] för [!DNL SugarCRM] kan också använda ett schemalagt jobb för att fråga [!DNL EchoSign] efter uppdateringar av avtal som är Skickade för signatur. Frågemetoden för schemalagda jobb kan användas om du har en lokal [!DNL SugarCRM]-installation bakom en brandvägg.

Så här konfigurerar du:

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Schemaläggaren]**.
1. Välj **[!UICONTROL Skapa schemaläggare]** på den nedrullningsbara menyn.
1. Ange ett jobbnamn.
1. För jobbfältet väljer du **[!UICONTROL Adobe EchoSign Status Updater]**.
1. Ange att jobbet ska köras så ofta som det behövs. Vi föreslår att det ska köras var 10:e minut, vilket innebär att det kan ta upp till 10 minuter innan [!DNL SugarCRM] uppdateras med den informationen när ett avtal har öppnats, lästs eller undertecknats.

   **Obs!** Om du har många avtal ute för signatur kan systemet bli långsammare om det körs för ofta.

   ![Bild](images/echosign-status-updater.png)

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign-inställningar]**.
1. Avmarkera kryssrutan **[!UICONTROL Använd EchoSigns callback-metod]** för att uppdatera händelser och status för avtal.
1. Välj **[!UICONTROL Spara]**.
Obs! Aktivera Schemaläggaren i [!DNL SugarCRM] för att det här ska fungera.

Så här lägger du till EchoSign-avtal i andra [!DNL SugarCRM]-moduler:

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Studio]**.
1. Välj modulen för att lägga till [!DNL EchoSign] avtal i det vänstra kolumnmappträdet.
1. Välj **[!UICONTROL Relationer]** **[!UICONTROL Lägg till relationer]**.
1. I listrutan väljer du Skriv som **[!UICONTROL Ett till Många]** och Modul som **[!UICONTROL EchoSign-avtal]**.
1. Välj **[!UICONTROL Spara och distribuera]**.

   ![Bild](images/save-and-deploy.png)

   [!DNL EchoSign] Avtal visas nu i modulen och avtal kan skapas och spåras där.

   ![Bild](images/echosign-agreements.png)

**Andra konfigurationssteg**

* **Dölja  [!DNL EchoSign] moduler**: Du kan dölja modulerna  [!DNL EchoSign] Mottagare och  [!DNL EchoSign] Händelser genom att gå till flikar och underpaneler i modulen Administration&quot; Visningsmodul och flytta dem till den dolda kolumnen.
* **Inaktiverar packageScan**: Om du har aktiverat packageScan på ditt eget system måste du inaktivera det under installationen. Om du använder [!DNL SugarCRM] On-Demand kontaktar du supporten för [!DNL SugarCRM] för att inaktivera packageScan åt dig.

## Avinstallera plugin-programmet {#uninstall-plugin}

1. Logga in på [!DNL SugarCRM] med ditt administratörskonto.
1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Modulinläsare]**.
1. Välj **[!UICONTROL Avinstallera]** bredvid [!UICONTROL EchoSign för SugarCRM-plugin].
1. Välj **[!UICONTROL Genomför]** för att påbörja avinstallationen. Du kan också välja att ta bort de databastabeller som har skapats för plugin-programmet.

   ![Bild](images/uninstall-plugin.png)

   Om plugin-programmet avinstalleras utan problem visar förloppsindikatorn att det lyckades till 100 %. Om förloppsindikatorn inte når 100 % väljer du [!UICONTROL Visa logg] för att se det fel som SugarCRM har råkat ut för.

   ![Bild](images/uninstall-display-log.png)

## Använd Adobe [!DNL EchoSign] för [!DNL SugarCRM] {#use-echosign-for-sugarcrm}

Du kan skapa ett Adobe [!DNL EchoSign]-avtal som är associerat med ett konto, en kontakt, en offert eller andra [!DNL SugarCRM]-moduler. Du kan bifoga filer, ange mottagare och skicka för signering. Adobe [!DNL EchoSign] uppdaterar [!DNL SugarCRM] med den aktuella statusen för avtalet och lagrar det signerade kontraktet i [!DNL SugarCRM] när det har slutförts.

### Skapa och redigera ett Adobe [!DNL EchoSign]-avtal {#create-edit-agreements}

Du kan skapa avtal med hjälp av modulen [!DNL EchoSign] Avtal eller med hjälp av moduler som har konfigurerats av en [!DNL SugarCRM]-administratör.

1. Välj **[!UICONTROL Skapa EchoSign-avtal]** på fliken [!UICONTROL Åtgärder] på fliken [!UICONTROL EchoSign-avtal].
1. I huvudavsnittet i [!DNL EchoSign]-avtalet anger du följande information eller väljer mellan olika avtalsalternativ:

   1. **[!UICONTROL Namn:]** Ange ett namn för avtalet.
   1. **[!UICONTROL Typ av signatur:]** Välj typ av signatur som accepteras för dokumentet. Alternativen är e-signatur och faxsignatur.
   1. **[!UICONTROL Jag måste också signera det här avtalet:]** Ange om avsändaren också måste signera avtalet.
   1. **[!UICONTROL Signaturordning:]** Om det föregående alternativet Jag måste signera det här avtalet är markerat väljer du också i vilken ordning som avsändaren och mottagarna ska signera.
   1. **[!UICONTROL Påminn mottagare om att signera:]** Välj hur ofta påminnelser en mottagare ska signera ett dokument. Alternativen är Daily eller Weekly.
   1. **[!UICONTROL Dagar till signeringsdeadline:]** Ange antalet dagar innan avtalet måste signeras.
   1. **[!UICONTROL Förhandsgranska, placera signaturer eller lägg till formfält:]**  Välj det här alternativet om du vill förhandsgranska avtalet innan det skickas eller dra och släpp signaturfält, initialfält eller andra formulärfält till avtalet innan det skickas till mottagare. När du har förhandsgranskat dokumentet eller dragit fälten som du vill ha till dokumentet, måste du komma ihåg att välja knappen Skicka för att skicka avtalet till mottagaren.
   1. **[!UICONTROL Värdsignering för den första signeraren:]** Ange om avsändaren vill vara värd för avtalssigneringen personligen.
      * **[!UICONTROL Meddelande:]** Inkludera ett meddelande till mottagaren.
      * **[!UICONTROL Konto, säljprojekt, offert:]** Välj eller ändra konto, säljprojekt eller offert som är associerad med det här avtalet.
      * **[!UICONTROL Språk:]** Ange på vilket språk signeringssidan och e-postmeddelanden ska visas för mottagarna.

      ![Bild](images/create-agreements.png)


1. I avsnittet [!UICONTROL Säkerhetsalternativ] i [!UICONTROL EchoSign-avtal] anger du följande information:

   a) **[!UICONTROL Lösenord krävs för signering:]** Ange om ett lösenord måste anges innan en mottagare kan signera ett dokument.
b) **[!UICONTROL Lösenord krävs för att öppna:]** Ange om ett lösenord måste anges innan en mottagare kan öppna ett PDF i avtalet eller det signerade avtalet
c) **[!UICONTROL Lösenord:]** Ange lösenordet som ska användas för att signera eller öppna ett dokument.
d) **[!UICONTROL Bekräfta lösenord:]** Bekräfta lösenordet som ska användas för att signera eller öppna ett dokument.

1. Ange följande information i avsnittet Annan i [!DNL EchoSign]-avtalet:

   a) **[!UICONTROL Användare:]** Ange en [!DNL SugarCRM]-användare. Standardvärdet är den användare som för närvarande är inloggad på systemet.
b) **[!UICONTROL Team:]** Om du vill ändra det primära teamet anger du namnet på det nya primära teamet. Om du vill tilldela fler team till posten klickar du på **[!UICONTROL Välj]** och väljer ett team i grupplistan, eller välj **[!UICONTROL Lägg till i]** för att lägga till teamfält och ange teamnamnen. Mer information finns i&quot;Tilldela poster till användare och team&quot; i [!DNL SugarCRM]-programguiden.

1. Välj **[!UICONTROL Spara]**.

### [!DNL EchoSign] avtalsdetaljvy {#agreement-detail-view}

När ett [!DNL EchoSign]-avtal har sparats innehåller avtalets detaljvy följande underpaneler:

* **[!UICONTROL Mottagare:]** Alla kontakter i den här underpanelen får de dokument som anges i underpanelen Dokument. Du måste lägga till en eller flera mottagare innan du skickar avtalet.
* **[!UICONTROL Dokument:]** Överför ett nytt dokument eller välj ett dokument som redan har överförts  [!DNL SugarCRM] till för att skickas för signatur.
* **[!UICONTROL Händelser:]** Alla åtgärder som rör avtalet, till exempel när avtalet skickades för signering, visades eller signerades, visas i den här underpanelen.
Om du vill redigera ett [!DNL EchoSign]-avtal väljer du knappen [!UICONTROL Redigera] på [!UICONTROL avtalets detaljvy].

![Bild](images/agreement-detail-view.png)

**Obs!** När ett avtal har skickats för signering tas knappen   Redigera bort från detaljvyn för att bevara händelseregistreringen. Du kan dock aktivera knappen Redigera. Om du vill göra det går du till [!UICONTROL Admin] > [!UICONTROL Adobe EchoSign Settings] och avmarkerar alternativet *[!UICONTROL När ett avtal har skickats ut för signatur inaktiverar du möjligheten att redigera eller ta bort]*.

### Lägg till ett dokument i ett [!DNL EchoSign]-avtal {#add-document}

[!DNL SugarCRM] kan användare överföra ett nytt dokument eller välja ett dokument som redan har överförts till  [!DNL SugarCRM] genom att använda underpanelen Dokument i en EchoSign-avtalspost.
Om du vill överföra ett dokument väljer du **[!UICONTROL Överför dokument]** på underpanelen [!UICONTROL Dokument].

I avsnittet&quot;Dokumentmodul&quot; i [!DNL SugarCRM]-programguiden finns mer information om de enskilda fälten i det formuläret.

Om du vill markera ett dokument klickar du på **[!UICONTROL Välj]** på underpanelen Dokument. Mer information om hur du hanterar relaterad information i underpaneler finns i&quot;Visa och hantera postinformation&quot; i [!DNL SugarCRM]-programguiden.

![Bild](images/add-document-to-agreement.png)

### Ange en mottagare för ett [!DNL EchoSign]-avtal {#specify-recipient}

1. I underpanelen [!UICONTROL Mottagare] i ett [!DNL EchoSign]-avtal väljer du **[!UICONTROL Lägg till mottagare]**.
1. Ange följande information:
a) [!UICONTROL Mottagare:] Välj typ av mottagare i listrutan. Skriv in mottagarens namn eller e-postadress i textfältet. [!DNL SugarCRM] söker efter namnet när du skriver och erbjuder en lista med val. Välj ett namn om en träff hittas. Du kan också välja en pilikon för att välja ett namn i ett popup-fönster. Om du vill radera namnet från fältet väljer du ikonen **[!UICONTROL X]**.
b) [!UICONTROL Roll:] Välj en roll i listrutan. Alternativen är Signer och CC och Godkännare. En godkännare behöver inte signera dokumentet.
1. Välj Spara.

![Bild](images/add-recipient-to-agreement.png)

### Skicka avtal för signering {#send-for-signature}

När avtal är klara att skickas för signering väljer du **[!UICONTROL Send for Signature]** i listrutan längst upp till vänster på sidan. Mottagarna får sedan ett e-postmeddelande med information om de dokument som väntar på att signeras. När mottagarna har signerat dokumentet får avsändaren ett e-postmeddelande.
Om alternativet [!UICONTROL Värdsignering för första signeraren] är markerat kan du välja **[!UICONTROL Send for Signature]** så att signeraren kan signera dokumentet med avsändaren närvarande.

![Bild](images/send-for-signature.png)

En **[!UICONTROL värdsignering för aktuell signerare]**-länk visas också bredvid fältet [!UICONTROL Värdsignering för första signeraren], som kan nås tills dokumentet har signerats. Du kan använda den här länken för att lagra avtalssignaturer för flera signerare eller för att öppna popup-fönstret igen om det stängs av misstag.
Om [!UICONTROL alternativet Förhandsgranska, placera signatur eller lägg till formfält] är markerat väljer du **[!UICONTROL Send for Signature]** så att avsändaren kan förhandsgranska dokumentet eller dra fält till dokumentet innan det skickas. Du måste välja **[!UICONTROL Skicka]** i det fönstret för att skicka avtalet till mottagaren.

Figur 5: Välj Send for Signature för att skicka ett dokument till en mottagare för en signatur.

### Skicka från en offertpost {#send-from-quote-record}

Adobe [!DNL EchoSign] har en direkt integrering med citattecken i [!DNL SugarCRM] så att offertens PDF automatiskt genereras och bifogas till avtalsposten.
När du visar en offert väljer du **[!UICONTROL Skapa EchoSign-avtal]** för att generera offerten och automatiskt bifoga den till avtalet. Det nya avtalet kopplar automatiskt alla relaterade säljprojekt, konton eller offerter.

![Bild](images/create-echosign-agreement.png)

Om du vill inaktivera den automatiska bifogningen av offerten PDF till avtalet går du till **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]** och avmarkerar kryssrutan *[!UICONTROL Bifoga PDF automatiskt när du skapar ett avtal från en offert]*.

### Avbryta ett avtal {#cancel-agreement}

Du kan avbryta ett [!DNL EchoSign]-avtal efter att det har skickats för en signatur om alla mottagare ännu inte har signerat dokumentet. En [!UICONTROL Avbryt avtal]-knapp visas i detaljvyn för ett avtal när ett dokument har skickats för signatur. Välj **[!UICONTROL Avbryt avtal]** om du vill avbryta avtalet.

![Bild](images/cancel-agreement.png)

Obs! Om ett [!DNL EchoSign]-avtal skickas för signatur och posten tas bort, måste du avbryta avtalet innan du tar bort det.

### Spåra signaturer {#track-signatures}

Underpanelen [!UICONTROL Händelser] i ett [!DNL EchoSign]-avtal spårar status för avtal som skickas för signatur. Om du vill visa de senaste uppdateringarna för ett [!DNL EchoSign]-avtal väljer du **[!UICONTROL Uppdatera status]**. Knappen [!UICONTROL Uppdateringsstatus] är bara tillgänglig efter att ett avtal har skickats för signatur.

![Bild](images/update-cancel-status.png)

När ett avtal har skickats ut för en signatur väljer du **[!UICONTROL Uppdatera status]** för att hämta den senaste statusen.

![Bild](images/events-subpanel.png)

### Skicka påminnelser {#send-reminders}

Om du vill skicka en påminnelse till den aktuella signeraren när avtalet har skickats väljer du **[!UICONTROL Skicka påminnelse]**. Det skickar omedelbart en e-postpåminnelse till den aktuella signeraren om avtalet som väntar på signatur.

![Bild](images/send-reminder.png)
