---
name: website-wens-doorgeven
description: Leg een wens voor nieuwe functionaliteit of een andere opmaak vast als issue voor de technisch beheerder. Gebruik wanneer de gebruiker iets wil wat meer is dan tekst, foto's, berichten of menu aanpassen (een formulier, een nieuw soort pagina, een koppeling, een andere vormgeving), of wanneer een andere skill naar het beheergebied verwijst.
---

# Wens doorgeven aan de technisch beheerder

Een wens buiten het beheergebied (`werkomgeving.md` §4) voert de plugin niet zelf uit: die wordt met de opdracht `wens`
een goed omschreven issue, dat de technisch beheerder beoordeelt en bouwt. Gedeelde stappen en regels staan in
`${CLAUDE_SKILL_DIR}/../../reference/werkomgeving.md`; lees dat eerst en voer §1 en §2 uit.

1. **Splitsen.** Valt een deel van de wens binnen het beheergebied (een tekst, een foto), voer dat deel dan uit met de
   skill `website-wijzigen` en geef hier alleen de rest door. Zeg de gebruiker welk deel waar heen gaat.
2. **Doorvragen.** Een issue is goed omschreven als de beheerder het kan bouwen zonder terug te vragen. Vraag, één
   vraag per keer en alleen wat nog ontbreekt:
   - wat de bezoeker van de website moet kunnen doen of zien;
   - waarom: welk doel of welk probleem van het bedrijf dit oplost;
   - waar op de website (welke pagina's, alle talen of niet);
   - voorbeelden: een andere website, een schets of een foto;
   - wat er gebeurt met gegevens die bezoekers invullen, en wie die ontvangt;
   - of er haast bij is, en waarom.

   Verzin geen bedrijfsgegevens; wat de gebruiker niet weet, wordt een open vraag in het issue.
3. **Doorgeven.** `wens` met als `titel` een korte omschrijving in gewone taal en als `beschrijving` deze opbouw:

   ```markdown
   ## Wens
   <de wens in de woorden van de gebruiker, letterlijk geciteerd>

   ## Doel
   ## Wat de bezoeker merkt
   ## Waar
   <pagina's met links naar de live site, talen>
   ## Voorbeelden
   ## Gegevens van bezoekers
   ## Open vragen
   ```

   Laat een kop weg als er niets onder komt, behalve *Open vragen*. De dienst zet er zelf bij wie de wens doorgaf. Neem een bijlage van de gebruiker op als link of
   beschrijving; toegangsgegevens en persoonsgegevens van klanten horen niet in een issue.
4. **Melden.** Zeg de gebruiker in één of twee zinnen dat de wens bij de technisch beheerder ligt, met het nummer dat de
   dienst teruggeeft (de link werkt alleen voor de beheerder), en dat de beheerder contact opneemt als er vragen zijn.

Klaar wanneer de dienst de wens heeft aangenomen en de gebruiker het nummer heeft.
