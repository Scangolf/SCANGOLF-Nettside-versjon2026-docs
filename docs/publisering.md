# Publisering og tilbakeføring

## Før bygging

- [ ] Arbeidet er knyttet til en GitHub-oppgave.
- [ ] Kildeendringene er gjennomgått og lagret i Git.
- [ ] CI og dokumentasjonsbygget har bestått for aktuell commit.
- [ ] Endringen og eventuelle begrensninger er dokumentert.

## Bygg pakken

```powershell
npm ci
npm run build:iis
```

- [ ] Bygget er et produksjonsbygg, ikke kopierte utviklingsfiler.
- [ ] Alle forventede sider og deres TXT-sidedata finnes.
- [ ] Filkontrollen har bestått.
- [ ] `_old` inneholder bare lokale sikkerhetskopier og utelatte filer.
- [ ] Alt utenfor `_old` er ment for opplasting.

## Bevar en versjon

```powershell
.\scripts\package-iis.ps1 -Version v2026.10.29
```

Bruk et nytt versjonsnavn for hver nye release. Kommandoen lager en ZIP,
en manifestfil med SHA-256 per fil og en kontrollsum for selve ZIP-filen i
`.releases`. `_old` tas ikke med, og eksisterende filer overskrives ikke.

Last filene opp som vedlegg til en GitHub Release for den eksakte commiten:

```powershell
gh release create v2026.10.29 --repo Scangolf/SCANGOLF-Nettside-versjon2026 --target main --title "Nettside 2026 – første publisering" --generate-notes .releases\SCANGOLF-Nettside-versjon2026-iis-v2026.10.29.zip .releases\SCANGOLF-Nettside-versjon2026-iis-v2026.10.29.manifest.json .releases\SCANGOLF-Nettside-versjon2026-iis-v2026.10.29.zip.sha256
```

Taggen må peke på commiten som faktisk ble brukt. Ikke gjenbruk en tidligere
tagg eller erstatt vedleggene til en allerede publisert release.

## Kopier til IIS

- [ ] Ta backup av dagens serverinnhold og eventuell lokal serverkonfigurasjon.
- [ ] Bekreft at riktig webrot for cs25.clubsite.no er valgt.
- [ ] Avklar eventuelle serverfiler, dokumenter eller andre apper som ikke
  finnes i pakken og ikke skal slettes.
- [ ] Avtal vedlikeholdsvindu ved full utskifting.
- [ ] Kopier **alt innholdet i `iis-publisering`, unntatt `_old`**.
- [ ] Ta med `_next`, bilder, fonter, HTML, TXT-sidedata og `web.config`.
- [ ] Ved løpende oppdatering: last opp ressursfiler og TXT før HTML,
  og `web.config` sist. Bevar eldre ressursfiler mens åpne faner kan bruke dem.
- [ ] Ikke last opp prosjektmappen, `.git`, `.releases`, dokumentasjon,
  `node_modules`, `out` eller `site`.

Ingen workflow i dette repoet endrer IIS-serveren automatisk.

## Kontroller og registrer

Følg [CLI-sjekklisten](kvalitet.md).

- [ ] Registrer dato, commit/tagg, release og hvem som publiserte.
- [ ] Registrer faktiske resultater fra serverkontroll, ikke bare lokalt bygg.
- [ ] Opprett oppgaver for funn; ikke erklær utestet funksjonalitet godkjent.

## Tilbakeføring

1. Stans videre publisering.
2. Velg sist fungerende release eller serverbackup.
3. Kontroller ZIP- og filhasher mot manifestet.
4. Gjenopprett riktig webrot uten å berøre IIS-bindinger eller sertifikater.
5. Kjør CLI-kontrollen igjen og registrer hva som ble tilbakeført.

En kildekode-tag alene er ikke en identisk publiseringspakke: avhengigheter,
byggeverktøy og ressurser kan påvirke et nytt bygg. Bruk releasevedlegget ved
behov for nøyaktig samme filer.
