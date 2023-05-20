---
title: Adobe Sign-integreringar Produktversioner och livscykler
description: Läs mer om Adobe Sign-integreringsversioner och supportlivscykel
audience: External
products: Adobe Sign
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Produktversioner och livscykel {#version}

Adobe Sign versionskonvention och supportlivscykel för integreringstjänster är i linje med andra Adobe-produkter som du kanske känner till.

## Versionsnummer

Paketversionen använder ett tredelat numreringssystem för att identifiera serienumret för den lanserade versionen och den relativa importen av uppgraderingen i form av nytt eller ändrat innehåll.

Versionsnumret följer det här mönstret: N.m.p

Där N = Huvudversion. m = Delversion p = Korrigerad version.

Integreringspaketversionen 23.2.1 visar till exempel följande versionsstatus:

* Huvudversion: 23
* Delversion: 2
* Korrigeringsversion: 1

När teknikerna utvecklar nya &quot;builds&quot; av paketet ökar de versionsnumret i enlighet med vilken typ av uppdateringar av koden som görs.

* Större versionsändringar innebär ett betydande tillägg av funktioner eller en viktig förändring av kärnsystemen.
* Delversionsuppdateringar omfattar mindre funktionsuppdateringar och säkerhetsuppdateringar. Adobe Sign kan behöva en uppgradering till den senaste korrigerade versionen om det finns säkerhetsuppdateringar eller för att åtgärda ett rapporterat objekt.
* Korrigeringsversioner är nästan uteslutande buggkorrigeringar och gränssnittsjusteringar

>[!NOTE]
>
>Alla versioner släpps inte till allmänheten eftersom produkten itererar under utveckling. Det kan alltså finnas betydande hopp i korrigeringsversionen mellan versioner.

Administratörerna måste hålla sin version uppdaterad för att säkerställa att kontot har fullständig åtkomst till alla funktioner och att alla kända säkerhetsproblem har korrigerats. Adobe Sign kan behöva en uppgradering till den senaste korrigerade versionen om det uppstår ett säkerhetsproblem eller för att åtgärda ett allvarligt systemproblem.

## Versionsstöd livscykel

Versionsstödet för livscykeln för en Adobe Sign-integrationsprodukt definieras baserat på huvudversionen av paketet och anger den tidsram som Adobe Sign aktivt stöder den enskilda integreringsversionen.

Adobe Sign stöder den aktuella paketversionen och de två tidigare huvudversionerna (inklusive alla relaterade delversioner och korrigeringsuppdateringar). Huvudversionerna uttrycks enligt följande:

* Aktuell version (N): Den senaste huvudversionen av paketet
* Föregående version (N-1): En huvudversion bakom den senaste versionen
* Senaste version som stöds (N-2): Två huvudversioner bakom den aktuella versionen

Om den aktuella tillgängliga versionen av paketet till exempel är 23.2.1 så gäller följande:

* Aktuell huvudversion (N) är 23
* Tidigare huvudversion (N-1) av detta paket är 22
* Senaste huvudversion som stöds (N-2) av det här paketet är 21
* Alla versioner äldre än 21.0.0 stöds inte

![Versionsdiagram](images/version_chart.png)

## Versionstjänstens livscykel

Versionstjänstens livscykel definierar det fullständiga omfånget för när tjänsten kan användas. Tidslinjen matchar versionsstödet för livscykeln med en 90-dagars respitperiod som gör att kunderna kan slutföra uppgraderingen.

* Under en respitperiod för en version som inte stöds ges endast support för att uppgradera till en nyare version, inte för att behålla en version som inte stöds
* Efter respitperioden slutar versionen att fungera

* Adobe Sign kommer inte att acceptera begäranden från versioner som är avstängda
* När integreringen har uppgraderats till den nuvarande versionen återupptas kommunikationen mellan Adobe Sign och integreringen normalt

![Avstängningsperiod](images/shutdown_period.png)

Kontakta din återförsäljare eller kundsupport om du har några frågor.
