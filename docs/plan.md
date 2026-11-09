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
| [#8 – simulatorprodukter](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/8) | Produktsider for Clubsite Simulator Booking og Clubsite Sim Launcher |
| [#9 – funksjonsskanner](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026/issues/9) | Playwright CLI-skanning av alle Clubsite-funksjoner med skjermbilder |

## Neste runde – innholdsutvidelse etter lansering

### Nye produktsider (issue #8)

To produkter mangler i `lib/solutionsData.ts` og på `/losninger`:

1. **Clubsite Simulator Booking** – dokumentert i drift hos
   [Arendal & Omegn GK](https://arendalgk.no/booking/simulator/kalender):
   kalender med flere simulatorer (Sim 1–3), timeslots 06:00–23:00,
   fargekoder (ledig/ditt valg/opptatt/ikke bekreftet/tid passert),
   brukerkonto med «Min konto», forhåndsbetaling online, verdikort med
   rabattert forhåndskjøp (f.eks. Gull kr 5 400 for kr 3 500), 14 dagers
   bookinghorisont, 60 min økter og protimer i utvalgt simulator.
2. **Clubsite Sim Launcher** – adgang og oppstart av simulatorøkten:
   dørlås åpnes kun i gyldig bookingvindu (matchet på telefonnummer),
   simulatorinnlogging ved ankomst. Funksjonsomfang mot tredjepart
   (Trackman/SolverApp) avklares med produkteier før publisering.

### Playwright-funksjonsskanner (issue #9)

CLI-basert headless skanning av alle Clubsite-funksjoner hos
[Ski Golfklubb](https://skigk.no) med fullside-skjermbilder som
dokumentasjonsbevis og rapport per funksjon: nyheter, bildearkiv,
dokumentarkiv, banemodul, kurs, turneringer, online påmelding med
betaling, blogg, dynamisk kalender, fotoalbum, kontaktlister,
skjemagenerator, restaurant/kafé, enkel nettbutikk, handlekurv,
ordreoversikt, maloppsett og dynamisk elementplassering (drag/drop).
Simulatorfunksjoner verifiseres mot Arendal GK.

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
