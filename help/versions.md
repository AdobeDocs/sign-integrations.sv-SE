---
title: Adobe Sign integrerar produktversioner och livscykeln
description: Läs om Adobe Sign integrations-versionerna och supportlivscykeln
audience: External
products: Adobe Sign
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 30cb79b6856c7b623dc5118b4aa40193bf749220
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 40%

---

# Produktversioner och livscykel {#version}

Adobe Sign versionskonvention och supportlivscykeln för integrerade tjänster passar ihop med andra Adobe-produkter som du kanske känner till.

## Versionsnummer

Paketversionen använder ett tredelat numreringssystem för att identifiera serienumret för den lanserade versionen och den relativa importen av uppgraderingen i form av nytt eller ändrat innehåll.

Versionsnumret följer det här mönstret: N.m.p

där N = Huvudversion; m = Delversion; p = Patched version.

Ett integrationspaket version 23.2.1 indikerar till exempel statusen för en release av:

* Huvudversion: 23
* Delversion: 2
* Lappversion: 1

När teknikerna utvecklar nya&quot;byggen&quot; av paketet ökar de versionsnumret enligt typen av uppdateringar av koden.

* Större versionsändringar innebär ett betydande tillägg av funktioner eller en viktig förändring av de centrala systemen.
* Mindre versionsuppdateringar inkluderar mindre funktionsuppdateringar och säkerhetsuppdateringar. Adobe Sign kan kräva en uppgradering till den senaste patchade versionen om säkerhetsuppdateringar eller för att åtgärda ett rapporterat problem.
* Korrigerade versioner är nästan uteslutande buggkorrigeringar och gränssnittsjusteringar

>[!NOTE]
>
>Alla versioner släpps inte ut till allmänheten eftersom produkten itererar under utvecklingen. Det kan därför finnas betydande hopp i patchversionen mellan releaserna.

Administratörerna måste hålla sin version uppdaterad för att säkerställa att kontot har fullständig åtkomst till alla funktioner och att alla kända säkerhetsproblem har åtgärdats. Adobe Sign kan kräva en uppgradering till den senaste patchade versionen om det uppstår säkerhetsproblem eller om det gäller allvarliga systemproblem.

## Livscykel för versionshantering

Versionsstödens livscykel för en Adobe Sign-integreringsprodukt definieras baserat på den huvudsakliga versionen av paketet och anger den tidsram som Adobe Sign aktivt stöder den enskilda versionen av integreringen.

Adobe Sign har stöd för den aktuella versionen av ett paket och de två föregående huvudversionerna (inklusive alla relaterade mindre uppdateringar och korrigeringsuppdateringar). Huvudversionerna uttrycks enligt följande:

* Aktuell version (N): Den senaste huvudversionen av paketet
* Tidigare version (N-1): En huvudversion bakom den senaste versionen
* Senaste version som stöds (N-2): Två huvudversioner bakom den aktuella versionen

Om den aktuella tillgängliga versionen av paketet till exempel är 23.2.1, ska du:

* Aktuell huvudversion (N) är 23
* Tidigare huvudversion (N-1) av detta paket är 22
* Senaste huvudversion som stöds (N-2) av det här paketet är 21
* Inga versioner som är äldre än 21.0.0 stöds

![Versionsdiagram](images/version_chart.png)

## Versionstjänstens livscykel

Versionstjänstens livscykel definierar det fullständiga omfånget för när tjänsten kan användas. Tidslinjen matchar versionsstödet för livscykeln med en 90-dagars respitperiod som tillåter att kunderna slutför uppgraderingen.

* Under en respitperiod för en version som inte stöds ges endast support för att uppgradera till en nyare version, inte för att behålla en version som inte stöds
* Efter respitperioden upphör versionen att fungera

* Adobe Sign kommer inte att acceptera förfrågningar från versioner som är avstängda
* När integreringen har uppgraderats till den aktuella versionen kommer kommunikationen mellan Adobe Sign och integreringen att återupptas normalt

![Avstängningsperiod](images/shutdown_period.png)

Kontakta din återförsäljare eller kundsupport om du har några frågor.
