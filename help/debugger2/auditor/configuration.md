---
title: Referens för konfigurationstest
description: Lär dig hur granskaren testar konfigurationer i Adobe Experience Platform Debugger.
exl-id: 92b07224-57f1-4891-9923-aa079945e6bc
source-git-commit: 2223e29de6876639c5dbffda4954e114dcd32521
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 4%

---

# Referens för konfigurationstest

Den här referensen ger mer information om hur revisionsfunktionen i Adobe Experience Platform Debugger kör konfigurationstester.

>[!NOTE]
>
>Mer information om granskartester i Platform Debugger finns i [översikt över funktioner](./overview.md).

Konfigurationstester söker efter specifika inställningar, värden eller potentiella konflikter i implementeringen. Platform Auditor utvärderar taggarna mot andra regler och rekommenderade metodtips.

| Test | Bredd | Kriterier | Rekommendation |
| --- | --- | --- | --- |
| Advertising Cloud - Konverteringsnamn innehåller endast alfanumeriska tecken | 3 | The `ev_conversion_property_name` parametern får bara innehålla numeriska och decimala värden EXCEPT för `ev_transid` -parameter, som kan innehålla text eller numeriska värden. Sök efter `everesttech.net` pixlar som innehåller en URL-parameter som börjar med  `ev_`. | Kontrollera att egenskapsparametrarna för transaktionen bara innehåller numeriska och decimala värden.<br><br>Varning: Andra värdetyper kan orsaka dataförlust. |
| Advertising Cloud - Konverteringsnamn använder URL-säkra tecken | 3 | Namn på konverteringsegenskaper får inte innehålla ett et-tecken eller frågetecken. | Se till att egenskapsparametrarna för transaktioner inte innehåller ett icke-kodat et-tecken eller frågetecken. Dessa bryter URL-formatet.<br><br>Varning: Egenskapsparametrar som innehåller ett icke-kodat et-tecken eller frågetecken (till exempel:  `ev_formComplete?=1` eller  `ev_formComplete&Submit=1`), kan leda till dataförlust. |
| Advertising Cloud - Transaktions-ID har implementerats korrekt | 1 | Egenskapsnamnet  `ev_transid=` får inte vara tom. | Egenskapsnamnet  `ev_transid=` ska inte lämnas utan ett värde. Om detta lämnas utan ett värde kan transaktionsdata gå förlorade. Tilldela ett värde till `ev_transid=` eller ta bort parametern från pixeln. |
| Analyser - instansierat i DOM | 5 | Adobe Analytics-koden är inte installerad eller kan inte köras. Returnerar 0 när ingen Analytics-kod finns på webbsidan. | Kontrollera att Analytics-taggen implementeras på sidan och inte blockeras av efterföljande skriptaktiviteter.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/analytics/implementation/home.html) |
| Analyser - instansierad en gång | 5 | Adobe Analytics-koden upptäcktes mer än en gång på sidan. . Returnerar 0 när ingen A-analyskod hittas på webbsidan. | Kontrollera att det bara finns en Analytics-tagg på sidan.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/analytics/implementation/home.html) |
| Analytics - Senaste versionen | 3 | Dina sidor kör inte den senaste versionen av kodbiblioteket för Analytics. Kodbibliotek som används av Experience Cloud-teknik uppdateras och ändras ständigt för att dra nytta av prestandaförbättringar och tillhandahålla de senaste funktionerna. Returnerar 0 när ingen Analytics-kod finns på webbsidan. | Installera den senaste versionen av Analytics-biblioteket.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/analytics/implementation/appmeasurement-updates.html) |
| Launch - tredjepartstaggar läses in asynkront efter DOM-klart | 3 | För att skapa en balans mellan en bra användarupplevelse och insamling av korrekta data bör tredjepartstaggar aktiveras vid DOM-förberedd. Detta säkerställer att dessa spårningsskript körs utan att webbplatsfunktionaliteten påverkas. | Lös det här problemet genom att justera alla regler som kör pixlar från tredje part som ska aktiveras på DOM Ready.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html) |
| Experience Cloud ID-tjänst - senaste version | 2 | Dina sidor kör inte den senaste versionen av kodbiblioteket för Visitor ID-tjänsten, visitorAPI.js. Kodbibliotek som används av Experience Cloud-teknik uppdateras och ändras ständigt för att dra nytta av prestandaförbättringar och tillhandahålla de senaste funktionerna. | Installera den senaste versionen av tjänstbiblioteket för Visitor-ID.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/id-service/using/id-service-api/library.html) |
| Launch - Senaste version | 2 | De här sidorna kör inte den senaste versionen av taggkodbiblioteket (Turbine). Kodbibliotek som används av Experience Cloud-teknik uppdateras och ändras ständigt för att dra nytta av prestandaförbättringar och tillhandahålla de senaste funktionerna. | Återskapa och publicera taggbiblioteket.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/experience-platform/tags/get-started/quick-start.html) |
| Mål - senaste version | 2 | Dina sidor kör inte den senaste versionen av kodbiblioteket Target. Kodbibliotek som används av Experience Cloud-teknik uppdateras och ändras ständigt för att dra nytta av prestandaförbättringar och tillhandahålla de senaste funktionerna. | Installera den senaste versionen av målbiblioteket.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/implement-target-for-client-side-web.html) |
| Mål - mboxDefault föregår mboxCreate | 5 | Den korrekta användningen av mboxCreate ser ut ungefär så här:<br><br> `<div class="mboxDefault"><!-Customer content--></div><script>mboxCreate('myMboxName')</script>` | Var noga med att inkludera en  `<div class="mboxDefault"></div>` -tagg innan mboxCreate() anropas. at.js kommer inte att lägga till en åt dig.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/implement-target-for-client-side-web.html) |
| Mål - Giltig DOCTYPE | 5 | En ogiltig DOCTYPE upptäcktes. Inga lådor kommer att utlösas i det här scenariot.  För at.js måste DOCTYPE vara i standardläge, annars fungerar inte Target. | Uppdatera DOCTYPE på sidan.<br><br>[Ytterligare information](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js-implementation/faq-at-js/target-atjs-faq.html) |

{style="table-layout:auto"}
