---
name: website-publiceren
description: Breng een goedgekeurde voorbeeldversie naar de testsite en publiceer na expliciet akkoord op de live website. Gebruik wanneer de gebruiker tevreden is met de voorbeeldversie, of vraagt om iets live te zetten of te publiceren.
---

# Naar test en publiceren

Gedeelde stappen en regels staan in `${CLAUDE_SKILL_DIR}/../../reference/werkomgeving.md`; lees dat eerst en voer
§1 tot en met §3 uit. De stand bepaalt waar je begint: *voorbeeldversie* bij deel A, *klaar op test* bij deel B. Bij
*geen ronde* is er niets te publiceren; zeg dat.

## A. Van voorbeeldversie naar testsite

Begin hier als de gebruiker tevreden is met de voorbeeldversie.

1. Controleer met `ronde` dat de controles van `ronde.commit` geslaagd zijn en de voorbeeldversie actueel is. Dat is
   de versie die de gebruiker heeft beoordeeld; is er sindsdien iets gewijzigd, laat de gebruiker dan eerst opnieuw
   kijken.
2. `naar_test` met die `commit`.
3. Wacht met `ronde` tot de testsite actueel is (`werkomgeving.md` §5) en bekijk daar de gewijzigde pagina's.
4. Geef de gebruiker de links op de testsite en vraag: "De aangepaste versie staat klaar op de testwebsite. Wil je
   deze versie nu publiceren?"

Klaar wanneer de testsite de nieuwe versie toont en de vraag gesteld is. Ga pas verder met deel B na een antwoord.

## B. Publiceren

Een verzoek om iets aan te passen of tevredenheid over een voorbeeldversie is geen publicatieakkoord. Ga alleen door
na een ondubbelzinnig "ja, publiceer" dat aantoonbaar slaat op de huidige testversie; vraag bij twijfel opnieuw.

Alleen een publiceerder mag publiceren (de rol staat in `status`). Is de gebruiker redacteur, publiceer dan niet en
meld: "De nieuwe versie staat klaar op de testwebsite. Een publiceerder van jullie kan die in Claude laten
publiceren." Noem de link naar de testsite.

1. **Te publiceren versie.** Vraag `ronde`. De versie is `test.commit`; de controles daarvan moeten geslaagd zijn en de
   testsite actueel. `nietLive` toont wat er live komt: alles daarvan moet door de gebruiker beoordeeld zijn. Staat
   er iets tussen wat de gebruiker niet herkent, vraag het dan na voordat je publiceert.
2. **Publiceren.** `publiceer` met die `commit` en in `akkoord` de bevestiging van de gebruiker, letterlijk. De dienst
   legt het akkoord vast en zet de versie live. Antwoordt de dienst dat hij wacht, vraag het dan na een minuut opnieuw
   met dezelfde gegevens. Weigert de dienst omdat de testversie intussen veranderd is, dan vervalt het akkoord:
   begin opnieuw bij stap 1 en vraag het akkoord opnieuw.
3. **Live controleren.** Wacht met `ronde` tot `live.omgeving` actueel is (`werkomgeving.md` §5) en bekijk de
   gewijzigde pagina's op de live website.
4. **Melden.** Geef de gebruiker de links naar de gewijzigde pagina's op de live website.

Klaar wanneer de live website de nieuwe versie toont, de pagina's kloppen en de gebruiker het resultaat heeft. Meld
een publicatie nooit als geslaagd voordat de live website de juiste versie toont.
