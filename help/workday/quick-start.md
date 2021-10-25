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
source-git-commit: 5ac9dc27dcdb6cab19281e6aafd4ea0524cc01d6
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 30%

---

# [!DNL Workday] Snabbstart{#workday-quick-start-guide}

[**Kontakta supporten för Adobe Sign**](https://www.adobe.com/go/adobesign-support-center)

## Översikt {#overview}

Det här dokumentet har utformats för att [!DNL Workday] administratörer förstår hur man anpassar [!DNL Workday] Affärsprocesser som innefattar Adobe Sign för att skaffa e-signaturer. Så här använder du Adobe Sign inom [!DNL Workday]måste du veta hur man skapar och ändrar [!DNL Workday] objekt som:

* [!UICONTROL Business Process Framework]
* Installation och konfiguration av innehavare
* Rapportering och [!DNL Workday] Studio-integrering

## Komma åt Adobe Sign i [!DNL Workday] {#access-adobe-sign}

[!UICONTROL Adobe Sign funktioner för elektroniska signaturer] är upplevd som [!UICONTROL Granska dokumentsteg] åtgärd inom [!UICONTROL Business Process Framework (BPF)] och som en Distribuera dokument.

## [!UICONTROL Steget Review Document (Granska dokument)] {#review-document-step}

Adobe Sign för [!DNL Workday] exponeras via [!UICONTROL Granska dokumentsteg] som du kan lägga till i över 400 affärsprocesser inom [!DNL Workday], inklusive [!UICONTROL Erbjudande], [!UICONTROL Distribuera dokument och uppgifter], [!UICONTROL Föreslå kompensation]med mera.

Du kan läsa [[!DNL Workday] community-artiklar på [!UICONTROL Granska dokumentsteg]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

Det finns en 1:1-relation mellan [!UICONTROL [!UICONTROL Granska dokumentsteg]s] och fakturerbara transaktioner med Adobe Sign. Du kan kombinera flera dokument i en enda [!UICONTROL Granska dokumentsteg] och de presenteras som ett enda paket för signering.

**Anteckning**: Endast en *Dynamisk* -dokument kan refereras inom ett specifikt [!UICONTROL Granska dokumentsteg].

Definiera en funktion [!UICONTROL Granska dokumentsteg]:

1. Infoga en [!UICONTROL Granska dokumentsteg].
1. Ange vilka grupper (roller) som kan agera på [!UICONTROL Granska dokumentsteg].

![Affärsprocesstegen](images/insert-review-doc-steptornm-575.png)

Så här konfigurerar du [!UICONTROL Granska dokumentsteg]:

1. Ange *[!UICONTROL Typ av e-signaturintegrering]* as *[!UICONTROL eSign av Adobe]*.

1. Lägg till rader i signaturrastret.

   * Med signaturrastret anges i vilken ordning som dokumentet dirigeras för signering. Varje rad kan innehålla en eller flera roller, och varje rad representerar ett steg i signeringsprocessen.
   * Varje rollmedlem inom ett visst steg meddelas om att en signeringshändelse väntar.
   * När en person i en roll signerar, är radsteget avslutat och dokumentet flyttas till nästa radsteg.
   * När alla rader har signerats [!UICONTROL Granska dokumentsteg] är klar.

1. Ange vilket dokument som ska signeras. Om dokumentet är ett [!UICONTROL Erbjudande - BP]kan du använda det från ett genereringsdokumentsteg. I annat fall ska du välja ett befintligt dokument eller en rapport.

1. Upprepa steg 3 för de dokument som du behöver.

   ![Konfigurera steg för Review Document (Granska dokument)](images/configure-rd-stepsmaller-575.png)

1. Du kan också lägga till en&quot;omdirigeringsanvändare&quot; för att fånga upp&quot;avböja att signera&quot;-åtgärder. När användare avböjer [!DNL Workday] skickar om dokumenten till en konfigurerad säkerhetsgrupp för granskning.

På menyn för relaterade åtgärder i en [!UICONTROL Granska dokumentsteg], markera **[!UICONTROL Affärsprocess]** > **[!UICONTROL Underhåll omdirigering]**. Välj sedan något av följande:

* **[!UICONTROL Lägg underst]**: Om du vill att medlemmar i en säkerhetsgrupp ska kunna skicka tillbaka ett steg till ett tidigare steg i affärsprocessen. Affärsprocessen startar om från detta steg.
* **[!UICONTROL Flytta till nästa steg]**: Att göra det möjligt för medlemmar i säkerhetsgrupper att vidarebefordra ett steg till nästa steg i affärsprocessen.
* **[!UICONTROL Säkerhetsgrupper]**: Om du vill omdirigera steg i affärsprocessflödet. Säkerhetsgrupper som visas när uppmaningen visas väljs i säkerhetsprofilen för affärsprocesser i avsnittet Omdirigering.

## Information om steg i affärsprocess {#business-process-step-notes}

[!UICONTROL Business Process Framework] är kraftfull, Du måste dock se till att

* Varje affärsprocess måste ha ett slutförandesteg, vilket är idealiskt i slutet av affärsprocessen.

* Ett slutförandesteg anges på menyn för relaterade åtgärder i sökikonen. Detta är bara möjligt när du&quot;visar&quot; affärsprocessen och inte när du&quot;redigerar&quot; den.

* Varje steg i affärsprocessen körs i sekvens.

   Du kan ändra stegordningen genom att ändra ordningsvärdet. Om du till exempel vill infoga ett steg mellan objekten &quot;c&quot; och &quot;d&quot; anger du ett nytt objekt som &quot;ca&quot;.

### Exempel: erbjudande {#example-offer}

Erbjudandet är en underprocess till [!UICONTROL Job Application Dynamic BP] som måste vara konfigurerade för att köra offert-BP. Den utlöses när tillståndet för jobbprogrammet flyttas till[!UICONTROL Erbjudande]&quot; eller &quot;[!UICONTROL Erbjudande]&quot;.

I exemplet nedan har en [!UICONTROL Granska dokumentsteg] använder ett dynamiskt dokumentsteg för både Nordamerika och Japan.

![[!DNL Workday]Exempel på en affärsprocess i ](images/bp-for-offersmaller-575.png)

Den här affärsprocessen gör följande:

* uppmanar BP:s initierare att föreslå kompensation för kandidaten (steg b).
* Använder ett stegvillkor för att testa om det aktuella landet INTE är Japan.

   Om true körs steget&quot;ba&quot; som använder ett engelskt dokument.

   Om false körs steg &quot;bb&quot; som använder ett japanskt språksdokument.

* Definierar signaturprocessen i [!UICONTROL Granska dokumentsteg] &quot;bc&quot;.
* Definierar beslutspunkten för att skapa ett erbjudande i det obligatoriska slutförandesteget &quot;d&quot;.

Det dynamiska dokumentet som skapas i steget ”ba” kallas [!UICONTROL Offer Letter] (Erbjudandebrev) och innehåller ett textblock med namnet [!UICONTROL Rapid Offer] (Snabberbjudande). Du kan lägga till flera textblock efter behov, t.ex. rubrik, hälsningsfras, kompensation, aktie, avslut, villkor med mera.

![[!DNL Workday] visa dokumentsida](images/offer-letter-575.png)

Det dynamiska erbjudandebrevet nedan har skapats i [!DNL Workday] textredigerare. Objekten markerade i *grå* är [!DNL Workday] tillhandahåller objekt som refererar till sammanhangsberoende data.

Objekt inom {{hakparenteser}} är [Adobe-texttaggar](https://adobe.com/go/adobesign_text_tag_guide_se).

![Exempel på dynamiskt formulär](images/script.png)

Inom [!UICONTROL Granska dokumentsteg], refereras det dynamiska dokumentet från föregående steg och definierar den sekventiella signeringsprocessen via två signeringsgrupper.

Beteendet som visas nedan dirigerar det dynamiskt genererade dokumentet först till rekryteringshanteraren och sedan till kandidaten.

![[!DNL Workday] signeringsgrupper definieras](images/configure-rd-stepsmaller-575.png)

### Exempel: Distribuera dokument {#example-distribute-documents}

Introducerades i [!DNL Workday] 30 kan aktiviteten för massdistribution av dokument eller uppgifter användas för att skicka ett dokument till en stor grupp (&lt;20 kB) med enskilda signerare. Detta är begränsat till en signatur per dokument. Skapande av en distribution görs med hjälp av[!UICONTROL Skapa distribuera dokument eller uppgifter]’ åtgärd från sökfältet.

Exempel: Skicka ett urvalsformulär för medarbetares eget kapital till alla chefer med [!UICONTROL Globala moderna tjänster]. Du kan filtrera det ytterligare till enskilda chefer om du vill.

Du kan även komma åt **Visa Distribuera dokument eller uppgifter** rapportera hur distributionen fortskrider.

![](images/create-distributedocumentsortasks.png)

### Exempel: Rapporter {#example-reporting}

[!DNL Workday] har en omfattande rapportstruktur. Kontrollera elementen för *Review Document Event* (Granskningsdokumenthändelse) för att se detaljer i Adobe Sign-processen.

Här nedan visas en enkel rapport som kan köras i alla affärsprocesser som söker efter Adobe Sign-transaktioner och deras status.

![Exempel på en [!DNL Workday] Anpassad rapport](images/review-document-eventsmaller-575.png)

Följande rapport genererades genom att titta på affärsprocesserna Offer (Erbjudande), Onboarding (Komma igång) och Propose Compensation (Föreslå kompensation) inom en implementeringsklient.

Du kan se:

* Dokumenten som skickas ut för signering
* Det associerade affärsprocessteget
* Nästa person som väntar på att signera

![Exempel på en [!DNL Workday] Rapportera med tre objekt](images/workday-reportsmaller-575.png)

## Signerade dokument {#signed-documents}

The [!DNL Workday] signaturcykeln inaktiverar alla e-postmeddelanden från Adobe Sign. Användare informeras om väntande åtgärder inom sina [!DNL Workday] inkorgen.

När ett dokument har signerats av alla signaturgrupper distribueras en kopia av det signerade dokumentet till alla medlemmar i signaturgruppen via e-post.

Du kan kontakta din [!UICONTROL Adobe Sign Success Manager] eller [Adobe Sign supportteam](https://adobe.com/go/adobesign-support-center).

Inom [!DNL Workday], kan du komma åt de signerade dokumenten i den fullständiga processposten. Du kan hitta:

* Arbetardokument i arbetarprofilen, och
* Kandidatdokument (erbjudandebrev) i kandidatprofilen.

Bilden nedan visar ett signerat offertbrev för kandidaten Chris Foxx.

![Exempel [!DNL Workday] erbjudandebrev](images/offer.png)

## Support {#support}

### [!DNL Workday] support {#workday-support}

[!DNL Workday] är integreringsägaren och bör vara den första kontaktpunkten för eventuella frågor om omfattningen av integreringen, funktioner eller problem med det dagliga integreringsarbetet.

The [!DNL Workday] har flera bra artiklar om hur du felsöker integreringen och skapar dokument:

* [Felsöka e-signeringsintegreringar](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [Steg för granskning av dokument](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [Skapa dynamiska dokument](https://community.workday.com/node/176443)
* [Tips angående konfiguration för att skapa dokument](https://community.workday.com/node/183242)

### Adobe Sign support {#adobe-sign-support}

Adobe Sign är integreringspartnern och ska kontaktas om integreringen inte kan hämta signaturer eller om meddelanden med väntande signeringar misslyckas.

Adobe Sign-kunder bör kontakta sin Customer Success Manager för att få hjälp. Alternativt kan [!UICONTROL Adobe tekniska support] kan nås via telefon: 1-866-318-4100, vänta på produktlistan och ange sedan: 4 och sedan 2 (enligt uppmaningen).

* [Lägg till Adobe-texttaggar i dokument](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
