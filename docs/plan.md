# Plan og sjekklister

Arbeidet styres i den private
[GitHub Projects-tavlen](https://github.com/orgs/Scangolf/projects/2).
Oppgaver skal ha ansvarlig, akseptansekriterier og tilknyttede pull requests.

## Opprettede GitHub-oppgaver

| Oppgave | Formål |
|---|---|
| [#1 – versjonert grunnlag](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/1) | Repo, første release, dokumentasjon og CI |
| [#2 – produksjonskontroll](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/2) | Bekreft aktiv versjon på IIS med CLI |
| [#3 – tilbakeføring](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/3) | Backup og dokumentert gjenoppretting |
| [#4 – vedlikeholdsregler](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/4) | PR-er, lint-baseline og avhengigheter |
| [#5 – innhold og kvalitet](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/5) | Separat avtalt tilgjengelighets- og visuell gjennomgang |
| [#6 – Pages](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/6) | Offentlig dokumentasjon fra separat repo, uten å åpne nettsidekoden |
| [#7 – kontaktløsning](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/7) | Eventuelt fremtidig skjema med faktisk sending |

## Prioritet 1 – bekreft produksjonsgrunnlaget

- [ ] Kontroller produksjonsdomenet med CLI etter opplasting.
- [ ] Sammenlign publiserte filer med release-manifestet ved tilgang til serveren.
- [ ] Dokumenter serverkrav og tilgjengelig backup-/tilbakeføringsrutine.
- [ ] Registrer hvilken release/commit som faktisk ligger på IIS.

## Prioritet 2 – trygg vedlikeholdsrutine

- [ ] Bruk pull requests og bestått CI før publisering.
- [ ] Avklar branch-beskyttelse/regler støttet av organisasjonens abonnement.
- [ ] Vurder tilgjengelighet, mobilmeny og visuell kontroll som separat avtalt arbeid.
- [ ] Etabler rutine for avhengighetsoppdateringer og regresjonskontroll.
- [ ] Gå gjennom eksisterende kildekode-lint og eventuelle kjente avvik.

## Prioritet 3 – dokumentasjon og forbedringer

- [ ] Vedlikehold og kontroller offentlig Pages-dokumentasjon ved dokumentasjonsendringer.
- [ ] Avklar om kontaktsiden skal ha et reelt mottaksendepunkt i fremtiden.
- [ ] Gjennomgå innhold, lenker og rettigheter til bilder/tekster med innholdseier.

## Sjekkliste for hver oppgave

- [ ] Beskriv ønsket resultat og hva som er utenfor omfang.
- [ ] Oppgi akseptansekriterier og relevant kontrollmetode.
- [ ] Avtal eventuelle atferds- eller designendringer før implementering.
- [ ] Gjør kildeendringene i en egen gren.
- [ ] Bygg og kontroller med CLI.
- [ ] Oppdater direkte berørt dokumentasjon.
- [ ] Knytt PR, commit og eventuell release til oppgaven.
- [ ] Registrer resultatet fra produksjonskontrollen når endringen publiseres.

## Statusbruk

- **Todo:** ikke startet.
- **In Progress:** aktivt arbeid.
- **Done:** akseptansekriteriene er kontrollert og resultatet lagret.

En oppgave med ekstern blokkering, som manglende nødvendig tilgang, skal
forbli åpen og beskrive blokkeringen.
