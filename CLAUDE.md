# Websitebeheer-plugin

Openbare repository met de Claude Code-plugin `website-beheer`, de marketplaces voor het stabiele (`main`) en het
testkanaal (`test`) en de gedeelde controles voor de websites. Hoe dit samenhangt met de dienst Websitebeheer staat in
de README van de dienst, §Plugin en gedeelde controles; lees die eerst. Installeren staat in
`plugins/website-beheer/README.md`.

- De plugin is voor alle klanten en websites: geen namen, adressen, branches of paden van één website in de plugin.
  Wat per website verschilt, komt uit `.website-beheer/config.json` van de websiterepository. Een nieuw veld of een
  andere betekenis van een veld is een nieuwe configuratie-`version`; leg dat vast in de plugin-README.
- De repository is openbaar: geen toegangsgegevens, klantgegevens of interne adressen.
- De plugin spreekt Nederlands met de medewerker; schrijf skills en documentatie in het Nederlands.
- Dezelfde plugin werkt ook in ChatGPT: geen `${CLAUDE_SKILL_DIR}` of andere Claude-variabelen in een skill, geen
  menu's of namen van één app in wat de medewerker te lezen krijgt, en wat een skill leest staat in de map van die
  skill. `reference/werkomgeving.md` is de bron; kopieer het na een wijziging naar `references/` in elke skill.
- `actions/` en `.github/workflows/herstelpunt.yml` draaien bij alle websites via de tag `v1`: alleen wijzigingen
  die met de bestaande configuratie blijven werken; zet `v1` na de merge naar `main` op de nieuwe commit. Een breuk
  wordt `v2`.
- Elke wijziging onder `plugins/website-beheer/` krijgt een hogere `version` in `.claude-plugin/plugin.json`.
- `.claude-plugin/marketplace.json` verschilt per branch (alleen `name`): pas het op `test` niet aan.
- Werk op een eigen branch en voeg via een pull request samen met `test`; `main` (stabiel) alleen op verzoek, met een
  pull request van `test` naar `main` (merge commit). Commitberichten in het Nederlands, gebiedende wijs, met het
  waarom in de body.
