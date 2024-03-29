---
title: Testinstallation av Workday
description: Workday-installationsguide för ett provkonto i Adobe Sign
uuid: 0c51f329-b7c1-44a2-88a3-670be7673747
products: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 63ed2d5b-9d82-4f87-97e1-2dde23501e89
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: beafe6c0-262f-4f5b-9315-a023a4eef4a2
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 0%

---

# [!DNL Workday] Testversion{#workday-trial-installation}

## Översikt {#overview}

Det här dokumentet är utformat för att hjälpa dig [!DNL Workday] kan du aktivera ett testkonto hos Adobe Sign och sedan integrera det i [!DNL Workday] klientorganisation. Så här använder du Adobe Sign i [!DNL Workday], du måste veta hur man skapar och ändrar [!DNL Workday] föremål som

* Ramverk för affärsprocesser
* Klientinställning och konfiguration
* Rapportering och [!DNL Workday] Studio-integrering

**Anteckning**: Om du har ett Adobe Sign-konto behöver du inte starta en testversion. Du kan kontakta din Client Success Manager för att begära [!DNL Workday] integration.

De viktigaste stegen för att slutföra integrationen är:

* Aktivera testkontot med Adobe Sign
* Skapa en integreringsnyckel i Adobe Sign
* Installera integreringsnyckeln i [!DNL Workday] Klient

## Aktivera ditt testkonto för Adobe Sign {#activate-sign-trial-account}

Om du vill ha en 30-dagars testversion av Adobe Sign måste du fylla i det här [registreringsformulär](https://land.echosign.com/esign-trial-workday-registration.html).

**Anteckning**: Vi rekommenderar starkt att du använder en giltig funktionell e-postadress för att skapa testversionen och inte ett tillfälligt e-postmeddelande. Du måste öppna det här e-postmeddelandet för att verifiera kontot, så adressen måste vara giltig.

![Formulär för begäran om testversion](images/trial-land.png)

Inom en arbetsdag tillhandahåller en Adobe Sign-specialist ditt konto (i Adobe Sign) för [!DNL Workday]. När det är klart får du ett bekräftelsemeddelande enligt beskrivningen nedan.

![Välkomstmeddelandet från Adobe Sign](images/welcome-email-2020.png)

Så här initierar du ditt konto och får åtkomst till ditt Adobe Sign [!UICONTROL Startsida] följer du instruktionerna i e-postmeddelandet .

![Adobe Sign-kontrollpanelen](images/classic-home.png)

## Generera en integreringsnyckel {#generate-an-integration-key}

För nya installationer måste du generera en integreringsnyckel i Adobe Sign och sedan ange den i [!DNL Workday]. Denna nyckel autentiserar Adobe Sign och [!DNL Workday] miljöer där man kan lita på varandra och dela innehåll.

Så här skapar du en integreringsnyckel i Adobe Sign:

1. Logga in som administratör i Adobe Sign.
1. Gå till **[!UICONTROL **Konto]** > **[!UICONTROL Personliga inställningar]** > **[!UICONTROL Åtkomsttoken**]**.
1. Klicka på **cirkelformad plusikon** på höger sida av fönstret.

   Det öppnar [!UICONTROL Skapa integreringsnyckel] gränssnitt.

   ![Bild av navigeringen till sidan Åtkomsttoken](images/navigate-to-group-accesstokens.png)

1. Ge nyckeln ett intuitivt namn, till exempel [!DNL Workday].

   Integreringsnyckeln måste ha följande element aktiverade:

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_read
   * library_read

   ![Panelen Skapa integreringsnyckel](images/create-integration-key-575.png)

1. Klicka **[!UICONTROL Spara]**.

   Den [!UICONTROL Åtkomsttoken] visas de tangenter som är utformade för ditt konto.

1. Klicka på nyckeldefinitionen som skapats för [!DNL Workday].

   Den [!UICONTROL Integreringsnyckel] länken visas överst i definitionen.

1. Klicka på **[!UICONTROL Integreringsnyckel]** länk.

   Integreringsnyckeln visas.

   ![Länken Integreringsnyckel](images/integration-key.png)

1. Kopiera nyckeln och spara den på ett säkert ställe inför nästa steg.
1. Klicka **[!UICONTROL OK]**.

   ![Panelen Integreringsnyckel](images/copy-the-key-575.png)

## Konfigurera [!DNL Workday] klientorganisation {#configuring-the-workday-tenant}

### Installera integreringsnyckeln {#install-the-integration-key}

Installera integreringsnyckeln i [!DNL Workday] klientorganisationen upprättar den betrodda relationen med Adobe Sign. När relationen är etablerad kan alla affärsprocesser ha en [!UICONTROL Steg för granskning av dokument] som aktiverar signeringsprocessen.

**Anteckning**: Adobe Sign varumärkesmarkeras som &quot;Adobe Document Cloud&quot; i hela [!DNL Workday] miljön.

Så här installerar du integreringsnyckeln:

1. Logga in på [!DNL Workday] som kontoadministratör.
1. Sök efter och öppna **[!UICONTROL Redigera klientinställning - Affärsprocesser]** sidan.

1. Ange information för följande fyra fält:

   * **[!UICONTROL Adobe Document Cloud-bekräftelse]**: En fast textbekräftelse av integreringen.

   * **[!UICONTROL API-nyckel för Adobe Document Cloud]**: Där integreringsnyckeln är installerad

   * **[!UICONTROL E-postadress för Adobe Document Cloud-avsändare]**: E-postadressen till gruppnivåadministratören i Adobe Sign

   * **[!UICONTROL Ta bort dokument som väntar på e-signatur när dokumentet avbryts]**: En valfri konfiguration som tar bort dokument från signaturcykeln om ett dokument avbryts i [!DNL Workday].

   ![Fälten för Adobe Sign-integreringsnyckeln](images/bp-filled-torn2-575.png)

1. Slutför sedan installationen:

   1. Klistra in integreringsnyckeln i [!UICONTROL Integreringsnyckel för Adobe Sign API] fält.
   1. Ange e-postadressen till Adobe Sign-administratören i [!UICONTROL E-postadress för Adobe Document Cloud-avsändare] fält.
   1. Klicka **[!UICONTROL OK]**.

   ![Fälten för integrationsnyckel och e-postfältet för nyckelinnehavaren](images/bp-filled-small.png)

Adobe Sign-funktioner kan nu läggas till i alla affärsprocesser genom att lägga till en [!UICONTROL Steg för granskning av dokument] och konfigurera den för användning **[!UICONTROL eSign by Adobe]** som e-signaturtypen.

### Konfigurera steget Granska dokument {#configure-the-review-document-step}

Dokumentet för steget Granska dokument kan vara ett statiskt dokument; ett dokument som genereras av steget Generera dokument inom samma affärsprocess, eller en formaterad rapport som skapats med [!DNL Workday] Rapportdesignern. Alla dessa fall kan utökas med [Adobe-texttaggar](https://adobe.com/go/adobesign_text_tag_guide) för att styra utseendet och placeringen av Adobe Signing-specifika komponenter. Dokumentkällan måste anges i affärsprocessdefinitionen. Det går inte att överföra ett ad hoc-dokument medan affärsprocessen körs.

Det enda sättet att använda Adobe Sign med steget Granska dokument är möjligheten att ha serialiserade signerargrupper. Med signerargrupper kan du ange rollbaserade grupper som loggar in efter varandra. Adobe Sign stöder inte parallella signeringsgrupper.

Om du behöver hjälp med att konfigurera steget Granska dokument läser du i [Snabbstartsguide](https://adobe.com//go/adobesign_workday_quick_start){target="_blank"}.

## Support {#support}

### [!DNL Workday] bära {#workday-support}

[!DNL Workday] är integreringsägaren och bör vara din första kontaktpunkt för frågor om omfattningen av integreringen, funktionsförfrågningar eller problem med den dagliga funktionen i integreringen.

Den [!DNL Workday] användarforumet har flera bra artiklar om hur man felsöker integreringen och genererar dokument:

* [Felsöka e-signaturintegreringar](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Steg för granskning av dokument](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Skapa dynamiska dokument](https://community.workday.com/node/176443)

* [Tips angående konfiguration för att skapa dokument](https://community.workday.com/node/183242)

### Stöd för Adobe Sign {#adobe-sign-support}

Adobe Sign är integrationspartnern och bör kontaktas om integreringen inte kan hämta signaturer eller om meddelanden om väntande signaturer misslyckas.

Adobe Sign-kunder bör kontakta sin Customer Success Manager (CSM) för support. Du kan även nå Adobe tekniska support via telefon: 1-866-318-4100; Vänta på produktlistan och ange sedan: 4 och sedan 2 (enligt anvisning).

* [Lägga till Adobe-texttaggar i dokument](https://adobe.com/go/adobesign_text_tag_guide)

* [Granska dokumentkonfiguration och exempel](https://www.adobe.com//go/adobesign_workday_quick_start){target="_blank"}

[**Kontakta Adobe Sign Support**](https://www.adobe.com/go/adobesign-support-center)
