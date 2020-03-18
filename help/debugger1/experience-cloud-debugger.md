---
description: Felsökaren undersöker dina webbsidor och hjälper dig att hitta problem med hur Experience Cloud-lösningarna implementeras
keywords: debugger;experience cloud debugger extension;chrome;extension
seo-description: Teknisk dokumentation för Adobe Experience Cloud Debugger Chrome Extension - Granska dina webbsidor och förstå problem med Experience Cloud-lösningens implementeringar
seo-title: Chrome-tillägg för Adobe Experience Cloud-felsökning
title: Adobe Experience Cloud Debugger Extension
uuid: 42e2c8a2-548a-4a3f-b57d-532535a0e7b9
translation-type: tm+mt
source-git-commit: d7a54ea531ac09ea6bee356e47a1da835b3880e8

---


# Adobe Experience Cloud Debugger Extension{#adobe-experience-cloud-debugger-extension}

Felsökningstillägget för [Adobe Experience Cloud för Chrome](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) undersöker dina webbsidor och hjälper dig att hitta problem med hur era Experience Cloud-lösningar implementeras.

Använd Adobe Experience Cloud Debugger-tillägget med övriga Adobe-aktiveringslösningar för ett arbetsflöde som följande:

1. Använd [Launch](https://docs.adobelaunch.com) eller [DTM](https://experiencecloud.adobe.com/resources/help/en_US/dtm/) för att infoga kod som aktiverar [Adobe Experience Cloud](https://marketing.adobe.com/resources/help/en_US/mcloud/) -lösningar på era sidor.

1. Använd [Adobe Cloud Platform Auditor](https://experiencecloud.adobe.com/resources/help/en_US/auditor/) för att testa implementeringarna.
1. Använd Adobe Experience Cloud Debugger-tillägget för att felsöka problem som hittats av granskare för att undersöka annan information om era implementeringar.

Ovanstående steg utförs inte nödvändigtvis i den ordningen, men det är en vanlig process.

Även om du kan köra felsökaren på en webbsida är alla icke-offentliga data bara tillgängliga i tillägget om du autentiseras i Experience Cloud på någon av dina öppna Chrome-flikar.

## Användningsexempel {#section-9fcd0583ed184943a8f0c2d3c00658e0}

Använd Felsökning för att samla in information som hjälper er att förstå hur era Experience Cloud-lösningar implementeras. Exempel:

* **Experience Platform Launch:** Se vilken egenskap, vilken miljö, vilken version som driftsätts på en sida.
* **Target:** Se vilka aktiviteter du är berättigad till eller inte är berättigad till och varför.