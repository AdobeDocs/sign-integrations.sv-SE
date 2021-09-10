---
title: Snabbstart för Workday
description: En snabb startguide för kunder som vill använda Adobe Sign i sina Workday-miljöer.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 36%

---

# [!DNL Workday] Snabbstart{#workday-quick-start-guide}

[**Kontakta supporten för Adobe Sign**](https://adobe.com/go/adobesign-support-center_se)

## Översikt {#overview}

Det här dokumentet är utformat för att hjälpa [!DNL Workday]-administratörer att förstå hur man anpassar [!DNL Workday]-affärsprocesser så att de innefattar Adobe Sign för att skaffa e-signaturer. Om du vill använda Adobe Sign i [!DNL Workday] måste du känna till hur du skapar och ändrar [!DNL Workday]-objekt, till exempel:

* Business Process Framework
* Installation och konfiguration av innehavare
* Rapportering och [!DNL Workday] Studio-integrering

## Komma åt Adobe Sign i [!DNL Workday] {#access-adobe-sign}

Adobe Sign funktion för elektroniska signaturer är [!UICONTROL Granska dokumentsteg] i Business Process Framework (BPF) och som en Distribuera dokument.

## [!UICONTROL Steget Review Document (Granska dokument)] {#review-document-step}

Adobe Sign för [!DNL Workday] visas via [!UICONTROL steget Granska dokument] som du kan lägga till i någon av de över 400 affärsprocesser som finns i [!DNL Workday], inklusive Erbjudande, Distribuera dokument och uppgifter, Föreslå kompensation med mera.

Du kan läsa [[!DNL Workday] community-artiklarna på [!UICONTROL Granska dokumentsteg]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Det finns en 1:1-relation mellan [!UICONTROL [!UICONTROL Granska dokumentsteg]s] och fakturerbara transaktioner med Adobe Sign. Du kan kombinera flera dokument i ett enda [!UICONTROL steg för Granska dokument] och de presenteras som ett paket för signatur.

**Obs**! Det går endast att referera till ett  ** dynamiskt dokument i ett specifikt  [!UICONTROL steg] för granskning av dokument.

Så här definierar du en funktion [!UICONTROL Granska dokumentsteg]:

1. Infoga ett [!UICONTROL steg för Granska dokument].
1. Ange de grupper (roller) som kan agera på [!UICONTROL steget Granska dokument].

![Affärsprocesstegen](images/insert-review-doc-steptornm-575.png)

Så här konfigurerar du [!UICONTROL steget Granska dokument]:

1. Ange *[!UICONTROL e-signaturintegreringstypen]* som *[!UICONTROL e-signera av Adobe]*.

1. Lägg till rader i signaturrastret.

   * Med signaturrastret anges i vilken ordning som dokumentet dirigeras för signering. Varje rad kan innehålla en eller flera roller, och varje rad representerar ett steg i signeringsprocessen.
   * Varje rollmedlem inom ett visst steg meddelas om att en signeringshändelse väntar.
   * När en person i en roll signerar, är radsteget avslutat och dokumentet flyttas till nästa radsteg.
   * När alla rader har signerats är [!UICONTROL steget Granska dokument] slutfört.

1. Ange vilket dokument som ska signeras. Om detta är ett affärsprocesserbjudande, kan du använda dokumentet från steget ”Generate Document” (Skapa dokument). I annat fall ska du välja ett befintligt dokument eller en rapport.

1. Upprepa steg 3 för de dokument som du behöver.

   ![Konfigurera steg för Review Document (Granska dokument)](images/configure-rd-stepsmaller-575.png)

1. Du kan också lägga till en&quot;omdirigeringsanvändare&quot; för att fånga upp&quot;avböja att signera&quot;-åtgärder. När användare avböjer returnerar [!DNL Workday] dokumenten till en konfigurerad säkerhetsgrupp för granskning.

Välj **[!UICONTROL Affärsprocess]** > **[!UICONTROL Behåll omdirigering]** på menyn för relaterade åtgärder i ett [!UICONTROL steg för Granska dokument]. Välj sedan något av följande:

* **[!UICONTROL Lägg underst]**: Om du vill att medlemmar i en säkerhetsgrupp ska kunna skicka tillbaka ett steg till ett tidigare steg i affärsprocessen. Affärsprocessen startar om från detta steg.
* **[!UICONTROL Gå till nästa steg]**: Att göra det möjligt för medlemmar i säkerhetsgrupper att vidarebefordra ett steg till nästa steg i affärsprocessen.
* **[!UICONTROL Säkerhetsgrupper]**: Om du vill omdirigera steg i affärsprocessflödet. Säkerhetsgrupper som visas när uppmaningen visas väljs i säkerhetsprofilen för affärsprocesser i avsnittet Omdirigering.

## Information om steg i affärsprocess {#business-process-step-notes}

Business Process Framework är kraftfullt; Du måste dock se till att

* Varje affärsprocess måste ha ett slutförandesteg, vilket är idealiskt i slutet av affärsprocessen.

* Ett steg för slutförande anges på menyn för relaterade åtgärder i sökikonen. Detta är bara möjligt när du&quot;visar&quot; affärsprocessen och inte när du&quot;redigerar&quot; den.

* Varje steg i affärsprocessen körs i sekvens.

   Du kan ändra stegordningen genom att ändra ordningsvärdet. Om du till exempel vill infoga ett steg mellan objekten &quot;c&quot; och &quot;d&quot; anger du ett nytt objekt som &quot;ca&quot;.

### Exempel: erbjudande {#example-offer}

Erbjudandet är en underprocess till Job Application Dynamic BP som måste konfigureras för att genomföra offertförfrågan. Det aktiveras när Job Application-läget flyttas till ”Offer” (Erbjudande) eller ”Make Offer” (Gör erbjudande).

I exemplet nedan använder ett [!UICONTROL steg för Granska dokument] ett dynamiskt dokumentsteg för både Nordamerika och Japan.

![[!DNL Workday]Exempel på en affärsprocess i ](images/bp-for-offersmaller-575.png)

Den här affärsprocessen gör följande:

* uppmanar BP:s initierare att föreslå kompensation för kandidaten (steg b).
* Använder ett stegvillkor för att testa om det aktuella landet INTE är Japan.

   Om true körs steget&quot;ba&quot; som använder ett engelskt dokument.

   Om false körs steg &quot;bb&quot; som använder ett japanskt språksdokument.

* Definierar signaturprocessen i [!UICONTROL steget Granska dokument] &quot;bc&quot;.
* Definierar beslutspunkten för att skapa ett erbjudande i det obligatoriska slutförandesteget &quot;d&quot;.

Det dynamiska dokumentet som skapas i steget ”ba” kallas [!UICONTROL Offer Letter] (Erbjudandebrev) och innehåller ett textblock med namnet [!UICONTROL Rapid Offer] (Snabberbjudande). Du kan lägga till flera textblock efter behov, t.ex. rubrik, hälsningsfras, kompensation, aktie, avslut, villkor med mera.

![[!DNL Workday] visa dokumentsida](images/offer-letter-575.png)

Det dynamiska erbjudandebrevet nedan har skapats i [!DNL Workday] RTF-redigeraren. Objekten som markeras i *gray* är [!DNL Workday] förutsatt att de refererar till sammanhangsberoende data.

Objekt inom {{hakparenteser}} är [Adobe-texttaggar](https://adobe.com/go/adobesign_text_tag_guide_se).

![Exempel på dynamiskt formulär](images/script.png)

I [!UICONTROL steget Granska dokument] refereras det dynamiska dokumentet från föregående steg och den sekventiella signeringsprocessen definieras via två signeringsgrupper.

Beteendet nedan dirigerar det dynamiskt genererade dokumentet först till rekryteringshanteraren och sedan till kandidaten.

![[!DNL Workday] signeringsgrupper definieras](images/configure-rd-stepsmaller-575.png)

### Exempel: Distribuera dokument {#example-distribute-documents}

Aktiviteten för massdistribution av dokument eller uppgifter, som introducerades i [!DNL Workday] 30, kan användas för att skicka ett enstaka dokument till en stor grupp (&lt;20K) med enskilda signerare. Detta är begränsat till en signatur per dokument. Distributionen skapas genom att åtgärden [!UICONTROL Skapa Distribuera dokument eller uppgifter] aktiveras från sökfältet.

Exempel: Skicka ett equity choice-formulär till alla chefer med Global Modern Services. Du kan filtrera det ytterligare till enskilda chefer om du vill.

Du kan också komma åt rapporten **View Distribute Documents or Tasks** för att spåra distributionsförloppet.

![](images/create-distributedocumentsortasks.png)

### Exempel: Rapporter {#example-reporting}

[!DNL Workday] har en omfattande rapportstruktur. Kontrollera elementen för *Review Document Event* (Granskningsdokumenthändelse) för att se detaljer i Adobe Sign-processen.

Här nedan visas en enkel rapport som kan köras i alla affärsprocesser som söker efter Adobe Sign-transaktioner och deras status.

![Exempel på en  [!DNL Workday] anpassad rapport](images/review-document-eventsmaller-575.png)

Följande rapport genererades genom att titta på affärsprocesserna Offer (Erbjudande), Onboarding (Komma igång) och Propose Compensation (Föreslå kompensation) inom en implementeringsklient.

Du kan se:

* Dokumenten som skickas ut för signering
* Det associerade affärsprocessteget
* Nästa person som väntar på att signera

![Exempel på en  [!DNL Workday] rapport som använder tre objekt](images/workday-reportsmaller-575.png)

## Signerade dokument {#signed-documents}

Signaturcykeln [!DNL Workday] undertrycker alla e-postmeddelanden från Adobe Sign. Användare informeras om väntande åtgärder i sin [!DNL Workday]-inkorg.

När ett dokument har signerats av alla signaturgrupper distribueras en kopia av det signerade dokumentet till alla medlemmar i signaturgruppen via e-post.

Du kan kontakta din Adobe Sign Success Manager eller [Adobe Sign Support-teamet](https://adobe.com/go/adobesign-support-center) om du vill inaktivera detta beteende.

Inom [!DNL Workday] kan du komma åt de signerade dokumenten på den fullständiga processposten. Du kan hitta:

* Arbetardokument i arbetarprofilen, och
* Kandidatdokument (erbjudandebrev) i kandidatprofilen.

Bilden nedan visar ett signerat offertbrev för kandidaten Chris Foxx.

![Exempel på  [!DNL Workday] erbjudandebrev](images/offer.png)

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

Adobe Sign-kunder bör kontakta sin Customer Success Manager (CSM) för att be om hjälp. Det går även att ringa till Adobes tekniska support på 1-866-318-4100, vänta på produktlistan och sedan ange 4 sedan ange 2 (enligt anvisningarna).

* [Lägg till Adobe-texttaggar i dokument](https://adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
