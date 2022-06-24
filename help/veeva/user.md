---
title: Användarhandbok för Veva Vault
description: Användarhandbok för Veva Vault-kunder om hur du använder Adobe Sign-integrering med Veva
products: Adobe Sign
content-type: reference
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 39a43637-af3f-432e-a784-8f472aa86df5
source-git-commit: c164692d78608c436d136caef44b19fe8d37b9d8
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 2%

---

# Adobe Acrobat Sign för [!DNL Veeva Vault]: Användarhandbok {#veeva-vault-user-guide}

[**Kontakta Adobe Acrobat Sign Support**](https://adobe.com/go/adobesign-support-center_se)

Det här dokumentet är utformat för att hjälpa dig [!DNL Veeva Vault] kan du lära dig använda Adobe Acrobat Sign för [!DNL Veeva Vault] integration för att skicka ett avtal.

## Översikt {#overview}

Adobe Acrobat Sign-integrering med [!DNL Veeva Vault] underlättar processen för att erhålla en signatur eller ett godkännande för all dokumentation som kräver juridiska signaturer eller granskningsbar dokumentbearbetning.

Den övergripande processen att skicka dokument för signering påminner om att skicka ett e-postmeddelande, så det är enkelt att använda för de flesta användare.

Adobe Acrobat Sign-integrering med [!DNL Veeva Vault] effektiviserar och snabbar upp arbetsflödena för dokument och signaturer. Genom att använda arbetsflödet för integrering kan du

* Spara tid och resurser på snigelmejl, övernattning och fax.
* Skicka kontrakt för e-signering eller godkännande från [!DNL Veeva Vault], få åtkomst till kontraktshistorik i realtid och visa sparade kontrakt.
* Spåra erbjudandena i realtid i hela organisationen och få uppdateringar när avtal visas, signeras, avbryts eller avvisas.
* eSign på över 20 språk och stöd för faxtjänster på 50+ platser runt hela jorden.
* Skapa återanvändbara avtalsmallar för sändningsalternativ.

## Skicka ett avtal med Adobe Acrobat Sign för [!DNL Veeva Vault] {#send-sign-vault-agreement}

Så här skickar du ett avtal med Adobe Acrobat Sign för Veva:

1. Gå till [[!DNL Veeva Vault] inloggningssida](https://login.veevavault.com/) och ange ditt användarnamn och lösenord. Den öppnar startsidan för ditt valv, som visas nedan.

   ![](images/vault-home.png)

1. Välj **[!UICONTROL Bibliotek]** och sedan välja **[!UICONTROL Skapa]** från det övre högra hörnet.

   ![](images/create-library.png)

1. Välj **[!UICONTROL Överför och fortsätt]**.

1. Ladda upp alla dokument från den lokala enheten.

1. I dialogrutan som visas väljer du **[!UICONTROL Text]** som *[!UICONTROL Kliniska]* och välj sedan en **[!UICONTROL Undertyp]** och **[!UICONTROL Klassificering]**, om så krävs.


   ![](images/choose-document-type.png)

1. Stäng dialogrutan genom att välja **[!UICONTROL OK]**.

1. Välj **[!UICONTROL Nästa]**.

1. I fönstret som visas fyller du i alla obligatoriska fält i metadataavsnittet och väljer **[!UICONTROL Spara]**.

   ![](images/metadata-details.png)

1. Ett testdokument skapas i **[!UICONTROL Utkast]** status, se nedan.

   ![](images/document-draft.png)

1. I det övre högra hörnet väljer du ![kugghjulsikon](images/icon-gear.png) och väljer **[!UICONTROL Starta granskning]**.

   ![](images/start-review.png)

1. Välj **[!UICONTROL Granskare]** och **[!UICONTROL Granska förfallodatum]**.

1. Välj **[!UICONTROL Start]**. Dokumentstatus ändras till [!UICONTROL GRANSKAS].

   ![](images/in-review.png)

1. Slutför den tilldelade uppgiften för granskarnas räkning. När du är klar ändras dokumentstatusen till [!UICONTROL GRANSKAD].

   ![](images/reviewed-status.png)

1. Välj ![kugghjulsikon](images/icon-gear.png) och väljer **[!UICONTROL Adobe Sign]**.

   ![](images/select-adobe-sign.png)

1. Om UMG-funktionen (Användare i flera grupper) är aktiverad på Adobe Acrobat Sign-kontot och avsändaren tillhör flera grupper visas en dialogruta så som visas nedan. Markera gruppen i dialogrutan och välj sedan **[!UICONTROL Nästa]**.

   ![](images/umg-dialog.png)

1. I iFrame-fönstret som öppnas i Vault anger du mottagarens e-postadress och väljer **[!UICONTROL Nästa]**.

   ![](images/iframe.png)

   **Obs!** Om det inte finns något Adobe Acrobat Sign-användarkonto för avsändarens e-post visas ett meddelande i iFrame-fönstret, enligt nedan. Användaren får också ett e-postmeddelande med instruktioner om hur kontot aktiveras.

   ![](images/iFrame-registration-message.png)

   ![](images/iFrame-confirm-email.png)

   Om *Etablera Sign-användare automatiskt* är inaktiverad, Adobe Acrobat Sign-användargenerering misslyckas och i iFrame-fönstret visas ett meddelande där användaren uppmanas att kontakta sin Adobe Acrobat Sign-kontoadministratör. Kontoadministratören för Adobe Acrobat Sign kan vidta en av följande åtgärder:

   * Aktivera *Etablera Sign-användare automatiskt* för kontot.
   * Skapa användaren i Adobe Acrobat Sign innan du använder VEVA Vault Adobe Acrobat Sign Integration.

   ![](images/iFrame-contact-administrator.png)

1. När dokumentet har bearbetats drar och släpper du signaturfälten från den högra panelen och väljer **[!UICONTROL Skicka]**.

   ![](images/add-signature-fields.png)

1. Dokumentet skickas till mottagarna för signering. När mottagaren tar emot dokumentets e-postadress ändras dokumentstatusen från [!UICONTROL Granskad] till [!UICONTROL Signering i Adobe].

   ![](images/in-adobe-signing.png)

1. När alla signaturer har samlats in och slutförts i Adobe Acrobat Sign ändras dokumentstatusen i Vault till [!UICONTROL Approved].

1. Välj **[!UICONTROL Dokumentfiler]** och expandera **[!UICONTROL Återgivningar]** i Vault. En återgivning med namnet Adobe Sign-återgivning skapas automatiskt när dokumentet har statusen Godkänd.

   ![](images/document-files.png)

1. Hämta Adobe Sign-återgivningen för att validera mottagarens signatur.

   ![](images/verify-signature.png)

## Avbryta ett avtal med Adobe Acrobat Sign för [!DNL Veeva Vault] {#cancel-sign-vault-agreement}

1. Gå till [[!DNL Veeva Vault] inloggningssida](https://login.veevavault.com/) och ange ditt användarnamn och lösenord. Den öppnar startsidan för ditt valv, som visas nedan.

   ![](images/vault-home.png)

1. Välj **[!UICONTROL Bibliotek]** och sedan markera dokumentet. Dokumentstatus kan vara: [!UICONTROL I Adobe Sign Draft], [!UICONTROL Redigera i Adobe Sign]eller [!UICONTROL Signering i Adobe].

   ![](images/document-adobe-sign-authoring.png)

1. Välj **[!UICONTROL Avbryt Adobe Sign]**.

   ![](images/cancel-document.png)

1. Det utlöser webbåtgärden och läser in iFrame-fönstret i [!UICONTROL valv].

   ![](images/cancelled-document.png)

1. Dokumentstatusen ändras automatiskt till [!UICONTROL Granska].

   ![](images/cancel-reviewed.png)

När dokumentstatusen har ändrats till Granska kan du skicka ut det för signering igen.
