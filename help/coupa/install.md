---
title: Installationshandbok för Coupa
description: Installationsguide för att aktivera Adobe Sign-integrering med Coupa BSM Suite
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 12c91be5-afec-4918-a8fc-ceb33bedf98b
source-git-commit: 623307e86f1b32edfbfa59dbd636ff74a6d09b62
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 7%

---

# [!DNL Coupa] Installationshandbok{#coupa-installation-guide}

[**Kontakta supporten för Adobe Sign**](https://adobe.com/go/adobesign-support-center_se)

## Översikt {#overview}

I det här dokumentet beskrivs hur du konfigurerar ditt Adobe Sign-konto för att integrera [!DNL Coupa BSM Suite]-instansen för att hämta signaturer.

Förutsättningar:

* Prenumeration på Adobe Sign Enterprise, [Adobe Sign Developer Edition](https://www.adobe.com/sign/developer-form.html) eller [Adobe Sign Enterprise Trial](https://www.adobe.com/sign/business.html)
* Adobe Sign administratörsåtkomst
* [!DNL Coupa BSM Suite] Standard eller Advanced-instans

De steg som krävs för att slutföra integreringen är:

* Konfigurera en Adobe Sign-grupp för användning med [!DNL Coupa BSM Suite]
* Anslut [!DNL Coupa BSM Suite] till Adobe Sign
* Skapa en Adobe Sign-webkrok för att meddela din [!DNL Coupa BSM Suite]-instans

## Konfigurera Adobe Sign Group för [!DNL Coupa BSM Suite] {#configure-adobe-sign-for-coupa}

För att få en dedikerad användning av Adobe Sign för [!DNL Coupa] inom en organisation måste administratörer skapa en Adobe Sign-grupp specifikt för [!DNL Coupa BSM Suite]-användning. Den här Adobe Sign-gruppen bör ha ett enda gruppadministratörskonto som fungerar som tjänstkonto. Eftersom det här tjänstkontot används för alla signaturbegäranden ska det hållas anonymt, till exempel `Legal@xyz.com`, `Purchasing@xyz.com` eller `CoupaCLM@xyz.com`, i stället för personligt, till exempel `Bob.Smith@xyz.com`.

### Skapa en grupp och en användare i Adobe Sign {#create-sign-user-group}

Så här skapar du en användare i Adobe Sign:

1. Logga in på Adobe Sign som kontoadministratör.
1. Navigera till **[!UICONTROL Konto]** > **[!UICONTROL Användare]**.
1. Om du vill skapa en ny användare klickar du på ikonen ![plus-ikonen](images/icon_plus.png) .
1. Ange den nya användarinformationen i dialogrutan som öppnas:

   1. Ange en funktionell e-postadress som du kan komma åt.

      * Den här användaren upprättar och underhåller OAuth-relationen.
      * E-postadressen måste vara en faktisk adress för verifiering.
   1. Ange lämpliga värden för [!UICONTROL Förnamn] och [!UICONTROL Efternamn].
   1. I fältet [!UICONTROL Primär grupp] väljer du **[!UICONTROL Skapa en ny grupp för den här användaren]**.
   1. I fältet [!UICONTROL Nytt gruppnamn] anger du ett intuitivt gruppnamn som *[!DNL Coupa BSM Suite]*.

   ![Panelen Skapa en användare](images/create-user.png)

1. Välj **[!UICONTROL Spara]**.

   När du har sparat informationen visar sidan [!UICONTROL Användare] den nya användaren med statusen [!UICONTROL CREATED].

   ![En vy över den nya skapade användaren](images/post-user-creation.png)

   Statusen [!UICONTROL CREATED] anger att användaren ännu inte har verifierat sin e-postadress.

1. Så här verifierar du e-postadressen:
   1. Logga in på den nya användarens e-postadress.
   2. Hitta e-postmeddelandet&quot;Välkommen till Adobe Sign&quot;. Kontrollera skräppostmapparna om det behövs.
   3. Klicka där det står **[!UICONTROL Klicka här för att ange ditt lösenord]**
   4. Ange lösenordet.

   När du har verifierat e-postadressen ändras användarens status från [!UICONTROL CREATED] till [!UICONTROL ACTIVE].

   ![Bild av den nya aktiverade användaren](images/active-user.png)

### Definiera den autentiserade användaren {#define-authenticating-user}

När du har skapat en grupp och en användare i den gruppen måste du göra användaren till en gruppadministratör.

Så här befordrar du den nya användaren i gruppen [!DNL Coupa BSM Suite]:

1. Navigera till sidan [!UICONTROL Användare] (om du inte redan är där).
2. Dubbelklicka på användaren.

   En [!UICONTROL Redigera]-sida öppnas för användarbehörighet.

3. Under avsnittet Gruppmedlemskap väljer du alternativen **[!UICONTROL Gruppadministratör]** och **[!UICONTROL Kan skicka]**.
4. Avmarkera alternativen **[!UICONTROL Användaren är kontoadministratör]** och **[!UICONTROL Användaren kan signera dokument]**.
5. Klicka på **[!UICONTROL Spara]**.

   ![Bild av användarinställningar](images/user-settings.png)

## Konfigurera [!DNL Coupa BSM Suite]-instansen {#configure-coupa}

För att slutföra anslutningen mellan [!DNL Coupa BSM Suite ]-instansen och Adobe Sign måste en betrodd relation upprättas mellan tjänsterna.

Så här konfigurerar du [!DNL Coupa BSM Suite]:

1. Anslut din [!DNL Coupa BSM Suite]-instans till ditt Adobe Sign-tjänstkonto som du skapade ovan.
1. Skapa en Adobe Sign-webonlineinstans för att meddela din Coupa BSM Suite-instans om uppdateringar av avtal.

Mer information om hur du ansluter [!DNL Coupa BSM Suite] och hur du skapar och registrerar webkrok finns i [Adobe Sign Coupa BSM Suite-supportdokumentation](https://success.coupa.com/Support/Docs/Power_Apps/CLM_Standard/Signing_and_Approvals/Enable_E-Signatures_Through_Adobe_Sign_and_DocuSign){target=&quot;_blank&quot;}.

## Skapa [!DNL Webhook] i Adobe Sign {#create-webhook}

Coupa CLM-integreringen använder webkrokmeddelanden från Adobe Sign för att skicka uppdateringar om avtalets status. Det är viktigt att du slutför webbokroskonfigurationen, annars är avtalen som skickats för signering ofullständiga eller så levereras inte de signerade avtalen tillbaka till Coupa CLM.

Så här skapar du webkrok i Adobe Sign:

1. Logga in på Adobe Sign med den gruppadministratör som har skapats ovan, till exempel `coupaclm@MyDomain.com`.

1. Navigera till **Grupper** > **Webhooks**.

   ![Bild av användarinställningar](images/webhook-login.png)

1. Om du vill skapa en ny anslutning väljer du ikonen ![plus](images/icon_plus.png) .

1. I dialogrutan Skapa som öppnas fyller du i de obligatoriska fälten.

   **Obs!** Du måste hämta URL:en för webkrokhanteraren från Coupa.

   ![Bild av användarinställningar](images/webhook-create.png)

1. Välj obligatoriska meddelandeparametrar.

1. Välj **Spara**.

## Support {#support}

### [!DNL Coupa BSM Suite] support {#coupa-support}

[!DNL Coupa BSM Suite ] är integrationsägaren och bör vara den första kontaktpunkten för frågor om omfattningen av integreringen, förslag till funktioner eller problem med integreringens dagliga funktion.

Kontakta [Coupa Support](https://success.coupa.com/Support/Welcome_to_Coupa_Support){target=&quot;_blank&quot;} om du har frågor.

### Adobe Sign support {#adobe-sign-support}

Adobe Sign är integreringspartnern och bör kontaktas om integreringen misslyckas med att erhålla signaturer eller om meddelanden om väntande signaturer misslyckas.

Om du behöver hjälp med att använda eller konfigurera Adobe Sign kan du kontakta din Customer Success Manager (CSM) eller kontakta [Adobe Sign support](https://adobe.com/go/adobesign-support-center).

Adobe Sign administratörer kan också öppna biljetter och få support via hjälpen (?) i det övre högra hörnet på Adobe Sign-portalen.

![Bild på Adobe Sign portal - hjälp](images/sign-portal-help.png)
