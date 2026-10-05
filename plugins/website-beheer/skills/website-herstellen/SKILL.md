---
name: website-herstellen
description: Draai een gepubliceerde wijziging terug of zet de website terug naar een eerdere versie. Gebruik wanneer er na een publicatie iets mis is op de live website, of de gebruiker een eerdere versie terug wil.
---

# Herstellen

Herstel is een gewone wijzigingsronde die iets terugzet: voorbeeldversie, testsite, expliciet akkoord, live website.
Gedeelde stappen en regels staan in `${CLAUDE_SKILL_DIR}/../../reference/werkomgeving.md`; lees dat eerst en voer
§1 tot en met §3 uit. Loopt er al een ronde, bespreek dan eerst met de gebruiker wat daarmee moet gebeuren.

1. **Wat ging mis.** Laat de gebruiker beschrijven wat er mis is, op welke pagina's en in welke talen, en sinds
   wanneer.
2. **Herstelpunt kiezen.** Elke publicatie is een herstelpunt; `herstelpunten` geeft ze met datum, nieuwste eerst.
   Zoek het laatste herstelpunt waarop het nog goed was: vergelijk met `lees` en `herstelpunt` de oude versie van de
   betrokken bestanden met de huidige. Noem het de gebruiker als "de versie van <datum>".
3. **Kies de aanpak** en leg die in gewone taal voor:
   - *Alleen wat mis is terugzetten* (voorkeur): `herstel` met het herstelpunt en in `paden` alleen de betrokken
     bestanden of mappen. Andere wijzigingen sinds die versie blijven staan.
   - *Alle inhoud terugzetten*: `herstel` zonder `paden`. Dit draait ook alles terug wat daarna kwam, ook wat nog niet
     gepubliceerd was; zeg dat erbij en vraag of dat de bedoeling is.
   - *Gedeeltelijk anders*: moet maar een stukje van een bestand terug, pas het dan aan met de skill
     `website-wijzigen` vanaf stap 3, met de oude tekst uit `lees` als voorbeeld.

   Geef bij `herstel` als `wens` wat er mis is, in de woorden van de gebruiker.
4. **Verder als een gewone wijziging.** Volg de skill `website-wijzigen` vanaf stap 5 (wachten, zelf bekijken,
   melden) en daarna `website-publiceren`.

Gaat het om iets buiten de inhoud (opmaak, werking van de website), dan kan herstel dat niet terugzetten: geef het
door met de skill `website-wens-doorgeven`, met "Herstel" in de titel en of het haast heeft.

Klaar wanneer de herstelde versie op de voorbeeldversie staat en de gebruiker gevraagd is die te beoordelen, of
wanneer het herstel als wens bij de technisch beheerder ligt en de gebruiker dat weet. Een herstel bij de hosting
buiten de dienst om is een noodmaatregel van de technisch beheerder.
