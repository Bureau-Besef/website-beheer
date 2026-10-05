# Websitebeheer

Plugin voor Claude waarmee een medewerker zonder technische kennis een website laat aanpassen. De medewerker
beschrijft de wens in gewone taal, bekijkt een voorbeeldversie en geeft zelf akkoord voor publicatie.

De plugin werkt via de dienst Websitebeheer van Bureau Besef, een connector in Claude. Alleen de dienst praat met
GitHub: de medewerker heeft geen GitHub-account, geen clone en geen `git` of `gh` nodig. De dienst kent per
medewerker de websites en de rol (redacteur of publiceerder) en dwingt die af; de plugin bevat de werkwijze.
Alles wat per website verschilt, staat in de websiterepository zelf: `.website-beheer/config.json` en het
afsprakendocument waar `website.document` naar wijst. De plugin leest die via de dienst.

## Onderdelen

| Skill                    | Wat                                                                                  |
|--------------------------|--------------------------------------------------------------------------------------|
| `website-wijzigen`       | Wens uitvoeren, voorbeeldversie (preview) afwachten, zelf bekijken en melden         |
| `website-publiceren`     | Na tevredenheid naar de testsite; na expliciet akkoord van een publiceerder live     |
| `website-herstellen`     | Na een fout terug naar een herstelpunt (eerdere publicatie), via dezelfde route      |
| `website-wens-doorgeven` | Wens buiten de inhoud (functionaliteit, opmaak) als issue voor de technisch beheerder |

`reference/werkomgeving.md` bevat wat de skills delen: de opdrachten van de dienst, website en afspraken kiezen,
wat te doen als de dienst niet werkt, de stand van de wijzigingsronde, het beheergebied, wachten op een omgeving en
de regels voor meldingen.

Het akkoord legt de dienst vast als reactie bij de pull request naar de productiebranch, met de naam van de
publiceerder en diens letterlijke bevestiging, en voegt alleen samen als die pull request nog op de goedgekeurde
commit staat. Collega's uitnodigen gaat met de opdracht `uitnodigen` van de dienst (alleen voor publiceerders).

## Installeren

1. **Connector.** Voeg in Claude bij **Instellingen → Connectors** de connector Websitebeheer toe met het adres dat
   de technisch beheerder geeft, en log in met de uitnodigingslink en een passkey.
2. **Plugin.** Installeer het stabiele kanaal in Claude Code:

   ```text
   /plugin marketplace add Bureau-Besef/website-beheer
   /plugin install website-beheer@website-beheer
   ```

   Of upload de zip van de nieuwste release `plugin-website-beheer-<versie>` in Claude bij **Customize → Plugins →
   Upload plugin**. Voor één sessie zonder installatie: `claude --plugin-dir plugins/website-beheer`.
3. **Updates.** Claude Code zoekt bij deze marketplace niet vanzelf naar updates. Zet dat aan via `/plugin` →
   **Marketplaces** → de marketplace → **Enable auto-update**, of werk bij met `/plugin` → **Installed** →
   **Update now**. Een update werkt na een herstart.

   De Claude-app op dezelfde computer gebruikt de marketplace van Claude Code en ziet een nieuwe versie pas als die
   is bijgewerkt: met auto-update vanzelf, anders met `/plugin` → **Marketplaces** → de marketplace → **Update
   marketplace**. Daarna wordt de knop **Update** bij de plugin in de app actief. Een geüploade zip werkt niet vanzelf
   bij: upload de zip van de nieuwe release.

| Kanaal  | Branch | Marketplace           | Voor wie                                             |
|---------|--------|-----------------------|------------------------------------------------------|
| Stabiel | `main` | `website-beheer`      | Klanten                                              |
| Test    | `test` | `website-beheer-test` | Bureau Besef en websites die nieuwe versies proberen |

Het testkanaal: `/plugin marketplace add Bureau-Besef/website-beheer#test` en
`/plugin install website-beheer@website-beheer-test`.

De plugin werkt in Claude Code, Cowork en de Claude-app, ook op een telefoon. Krijgt de dienst nieuwe opdrachten,
dan onthoudt Claude nog de oude lijst: verbreek de connector en verbind opnieuw, en begin een nieuwe chat.

## Configuratie

De plugin kent configuratie `version` 1; de dienst weigert een andere versie. Velden die de plugin zelf gebruikt:

| Veld                                | Betekenis                                                         |
|-------------------------------------|-------------------------------------------------------------------|
| `website.name`, `website.languages` | Naam en talen; een nieuwe tekst komt in alle talen                |
| `website.document`                  | Pad van het afsprakendocument in de repository                    |
| `environments`                      | Adressen van voorbeeldversie, testsite en live website            |
| `contentPaths`                      | Het beheergebied: alleen deze paden mag een wijzigingsronde raken |

De overige velden (branches, controles, labels, `versionPath`) gebruikt de dienst.

## Data

De plugin stuurt wijzigingen via de dienst naar de GitHub-repository van de website. Toegangsgegevens staan alleen
bij de dienst, nooit in een repository of in de chat.
