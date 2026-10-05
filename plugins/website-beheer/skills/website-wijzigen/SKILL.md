---
name: website-wijzigen
description: Pas de website aan en laat een voorbeeldversie zien. Gebruik wanneer de gebruiker iets op de website wil veranderen, toevoegen of weghalen (tekst, foto, bericht, pagina), of een voorbeeldversie wil bijstellen.
---

# Website wijzigen tot voorbeeldversie

Van wens tot een voorbeeldversie (preview) die de gebruiker kan bekijken. Gedeelde stappen en regels staan in
`${CLAUDE_SKILL_DIR}/../../reference/werkomgeving.md`; lees dat eerst.

1. **Werkomgeving.** Voer §1 tot en met §3 van `werkomgeving.md` uit. Bij stand *voorbeeldversie* is dit een
   vervolgwijziging in de lopende ronde. Bij *klaar op test*: vraag of de nieuwe wens kan wachten tot de vorige is
   gepubliceerd; ga pas door als de gebruiker daarover beslist heeft.
2. **Wens.** Vraag alleen door wat nodig is om de wijziging goed uit te voeren: welke pagina, welke tekst, welke taal.
   Ontbreekt een gegeven als een prijs, adres of openingstijd, vraag het; verzin het niet.
3. **Lezen.** Zoek met `bestanden` en `lees` de bestanden die de wijziging raakt, met `ronde: true` als er een ronde
   loopt (anders zie je de testsite en mis je de eerdere wijzigingen van deze ronde).
4. **Wijzigen.** Pas alleen bestanden onder `contentPaths` aan (een publiceerder ook de CSS onder `stylePaths`), volgens de afspraken, `CLAUDE.md` en `README.md`.
   Een nieuwe of gewijzigde tekst komt in alle talen uit de instellingen; vertaal wat de gebruiker niet zelf
   aanlevert. Een nieuwe afbeelding: verklein die tot de grootte waarop de site hem toont en zet breedte en hoogte in
   de inhoud gelijk aan het bestand.

   Stuur alles wat bij elkaar hoort in één `wijzig`, met per bestand de volledige nieuwe inhoud (`tekst`, `base64` of
   `verwijderen`) en een `bericht` in de gebiedende wijs ("Vervang de openingstijden"). Begint er een nieuwe ronde,
   geef dan ook `titel` en `wens` (de wens in de woorden van de gebruiker).
5. **Wachten.** Wacht met `ronde` tot de controles van de nieuwe commit geslaagd zijn en de voorbeeldversie actueel is
   (`werkomgeving.md` §5). Mislukken de controles, lees dan de inhoud opnieuw na, los het op binnen de wens met een
   nieuwe `wijzig`, of meld wat de technisch beheerder moet doen (met de link `ronde.github`).
6. **Zelf bekijken.** Open op de voorbeeldversie elke gewijzigde pagina in elke taal waarin je iets veranderde en
   controleer dat de nieuwe tekst of afbeelding er staat en de links werken. Kun je de pagina in een browser bekijken,
   doe dat dan op desktop- en mobiele breedte.
7. **Melden.** Geef de gebruiker de links naar de gewijzigde pagina's op de voorbeeldversie, een korte samenvatting,
   eventuele aandachtspunten (vertalingen) en vraag: tevreden, of iets aanpassen?

Wil de gebruiker de wijziging niet meer, stop de ronde dan met `sluit_ronde` en een korte reden.

Klaar wanneer de voorbeeldversie de laatste commit toont, de controles geslaagd zijn en de gebruiker de links heeft.
Een "ja, zo is het goed" is akkoord met de voorbeeldversie, nog geen publicatieakkoord: daarvoor is de skill
`website-publiceren`.
