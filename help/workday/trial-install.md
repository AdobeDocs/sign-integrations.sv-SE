---
title: Provinstallation av Workday
description: Installationshandbok för ett Workday-testkonto i Adobe Sign
uuid: 0c51f329-b7c1-44a2-88a3-670be7673747
products: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 63ed2d5b-9d82-4f87-97e1-2dde23501e89
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: beafe6c0-262f-4f5b-9315-a023a4eef4a2
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 39%

---

# [!DNL Workday] Testinstallation{#workday-trial-installation}

## Översikt {#overview}

Det här dokumentet är utformat för att hjälpa [!DNL Workday]-kunder att lära sig hur man aktiverar ett testkonto hos Adobe Sign och sedan integrerar det i [!DNL Workday]-klienten. Om du vill använda Adobe Sign i [!DNL Workday] måste du känna till hur du skapar och ändrar [!DNL Workday]-objekt som:

* Affärsprocessram
* Installation och konfiguration av klientorganisation
* Integration med Reporting och [!DNL Workday] Studio

**Obs**! Om du har ett Adobe Sign-konto behöver du inte starta en testversion. Du kan kontakta din Client Success Manager för att begära [!DNL Workday]-integrering.

De åtgärder du måste utföra för att slutföra integreringen är:

* Aktivera ditt testkonto med Adobe Sign
* Generera en integreringsnyckel i Adobe Sign
* Installera integreringsnyckeln i [!DNL Workday]-klienten

## Aktivera ditt testkonto för Adobe Sign {#activate-sign-trial-account}

Om du vill ha en 30-dagars testversion av Adobe Sign måste du fylla i det här [registreringsformuläret](https://land.echosign.com/esign-trial-workday-registration.html).

**Obs**! Vi rekommenderar starkt att du använder en giltig e-postadress för att skapa testversionen och inte ett tillfälligt e-postmeddelande. Du måste ha åtkomst till den här e-postadressen för att kunna verifiera kontot, så adressen måste vara giltig.

![Formulär för testbegäran](images/trial-land.png)

Inom en arbetsdag tillhandahåller en Adobe Sign-specialist ditt konto (i Adobe Sign) för [!DNL Workday]. När du är klar får du ett bekräftelsemeddelande via e-post enligt nedan.

![Välkomstmeddelandet från Adobe Sign](images/welcome-email-2020.png)

Följ instruktionerna i e-postmeddelandet för att initiera ditt konto och komma åt din Adobe Sign [!UICONTROL hemsida].

![Adobe Sign Dashboard](images/classic-home.png)

## Generera en integreringsnyckel {#generate-an-integration-key}

För nya installationer måste du generera en integreringsnyckel i Adobe Sign och sedan ange den i [!DNL Workday]. Med den här nyckeln autentiseras Adobe Sign- och [!DNL Workday]-miljöerna så att de litar på varandra och delar innehåll.

Så här skapar du en integreringsnyckel i Adobe Sign:

1. Logga in som administratör i Adobe Sign.
1. Navigera till **[!UICONTROL **Konto]** > **[!UICONTROL Personliga inställningar]** > **[!UICONTROL Åtkomsttoken**]**.
1. Klicka på **plusikonen** till höger i fönstret.

   Gränssnittet [!UICONTROL Skapa integreringsnyckel] öppnas.

   ![Bild på hur man navigerar till sidan Åtkomsttoken](images/navigate-to-group-accesstokens.png)

1. Ge nyckeln ett intuitivt namn, till exempel [!DNL Workday].

   Integreringsnyckeln måste ha följande element aktiverade:

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_read
   * library_read

   ![Panelen Skapa integreringsnyckel](images/create-integration-key-575.png)

1. Klicka på **[!UICONTROL Spara]**.

   På sidan [!UICONTROL Åtkomsttoken] visas de nycklar som är avsedda för ditt konto.

1. Klicka på nyckeldefinitionen som skapades för [!DNL Workday].

   Länken [!UICONTROL Integreringsnyckel] visas ovanför definitionen.

1. Klicka på länken **[!UICONTROL Integreringsnyckel.]**

   Integreringsnyckeln visas.

   ![Länken Integreringsnyckel](images/integration-key.png)

1. Kopiera nyckeln och spara den på ett säkert ställe för nästa steg.
1. Klicka på **[!UICONTROL OK]**.

   ![Panelen Integreringsnyckel](images/copy-the-key-575.png)

## Konfigurera klientorganisationen [!DNL Workday] {#configuring-the-workday-tenant}

### Installera integrationsnyckeln {#install-the-integration-key}

Genom att installera integreringsnyckeln i [!DNL Workday]-klienten upprättas en förtroenderelation med Adobe Sign. När relationen är på plats kan alla affärsprocesser ha ett [!UICONTROL steg för granskningsdokument] tillagt som aktiverar signeringsprocessen.

**Obs**! Adobe Sign heter&quot;Adobe Document Cloud&quot; i hela  [!DNL Workday] miljön.

Så här installerar du integreringsnyckeln:

1. Logga in på [!DNL Workday] som kontoadministratör.
1. Sök efter och öppna sidan **[!UICONTROL Redigera klientinställning - Affärsprocesser]**.

1. Ange information för följande fyra fält:

   * **[!UICONTROL Adobe Document Cloud-erkännande]**: En fast textbekräftelse av integreringen.

   * **[!UICONTROL Adobe Document Cloud API-nyckel]**: Där integreringsnyckeln är installerad

   * **[!UICONTROL Adobe Document Cloud avsändares e-postadress]**: E-postadressen till gruppnivåadministratören i Adobe Sign

   * **[!UICONTROL Ta bort dokument som väntar på e-signatur när dokumentet har avbrutits]**: En valfri konfiguration som tar bort dokument från signaturcykeln om ett dokument avbryts i  [!DNL Workday].

   ![Fälten för integreringsnyckeln i Adobe Sign](images/bp-filled-torn2-575.png)

1. Slutför sedan installationen:

   1. Klistra in integreringsnyckelen i fältet [!UICONTROL API-integreringsnyckel för Adobe Sign.]
   1. Skriv e-postadressen för Adobe Sign-administratören i fältet [!UICONTROL Avsändares e-postadress för Adobe Document Cloud.]
   1. Klicka på **[!UICONTROL OK]**.

   ![Fälten för integreringsnyckeln och e-postadressen för nyckelhållaren](images/bp-filled-small.png)

Adobe Sign-funktioner kan nu läggas till i alla affärsprocesser genom att lägga till ett [!UICONTROL steg för Granska dokument] och konfigurera det så att det använder **[!UICONTROL eSign av Adobe]** som e-signaturtyp.

### Konfigurera steget Granska dokument {#configure-the-review-document-step}

Dokumentet för steget Granska dokument kan vara ett statiskt dokument. Ett dokument som genererats av ett genererat dokumentsteg inom samma affärsprocess. eller en formaterad rapport som skapats med [!DNL Workday] Report Designer. Alla dessa kan kompletteras med [Adobe-texttaggar](https://adobe.com/go/adobesign_text_tag_guide_se) för att kontrollera utseendet och placeringen av specifika komponenter för Adobe Sign. Dokumentkällan måste anges i definitionen för affärsprocessen. Det går inte att överföra ett ad hoc-dokument när affärsprocessen körs.

Unikt för att använda Adobe Sign med ett steg för att granska dokument är möjligheten att ha serialiserade signerargrupper. Med signerargrupper kan du ange rollbaserade grupper som signerar i ordning. Adobe Sign stöder inte parallella signeringsgrupper.

Om du behöver hjälp med att konfigurera steget Granska dokument kan du läsa [Snabbstartsguiden](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}.

## Support {#support}

### [!DNL Workday] support {#workday-support}

[!DNL Workday] är integreringsägaren och bör vara den första kontaktpunkten för eventuella frågor om omfattningen av integreringen, funktioner eller problem med det dagliga integreringsarbetet.

[!DNL Workday]-communityn har flera bra artiklar om hur du felsöker integreringen och skapar dokument:

* [Felsöka e-signeringsintegreringar](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Steg för granskning av dokument](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Skapa dynamiska dokument](https://community.workday.com/node/176443)

* [Tips angående konfiguration för att skapa dokument](https://community.workday.com/node/183242)

### Adobe Sign support {#adobe-sign-support}

Adobe Sign är integreringspartnern och ska kontaktas om integreringen inte kan hämta signaturer eller om meddelanden med väntande signeringar misslyckas.

Adobe Sign-kunder bör kontakta sin Customer Success Manager (CSM) för att be om hjälp. Du kan även kontakta Adobe tekniska support via telefon: 1-866-318-4100; vänta på produktlistan och ange sedan: 4 och sedan 2 (enligt uppmaningen).

* [Lägg till Adobe-texttaggar i dokument](https://adobe.com/go/adobesign_text_tag_guide)

* [Granska dokumentkonfiguration och exempel](https://experienceleague.adobe.com/docs/dc-sign-integrations/using/workday/quick-start.html)

[**Kontakta supporten för Adobe Sign**](https://adobe.com/go/adobesign-support-center_se)
