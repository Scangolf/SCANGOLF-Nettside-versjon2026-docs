# Lokal utvikling

## Forutsetninger

- Git og GitHub-tilgang til det private repoet.
- Node.js 24 LTS og npm.
- Python 3.12 eller nyere for MkDocs.
- Nettverk ved installasjon og bygging. `next/font` henter Google-fonter ved
  bygging; de ferdige fontfilene følger med til IIS.

Bruk `npm ci` med den versjonerte låsefilen. Endre ikke avhengigheter som en
del av vanlig publisering uten å kontrollere og dokumentere endringen.

```powershell
git pull --ff-only
npm ci
git switch -c endring/kort-beskrivelse
```

For utvikling kan `npm run dev` startes etter avtale. Den rutinemessige
kontrollen her er CLI-basert og krever ikke en lokal server eller nettleser.

## Bygg og kontroller

```powershell
npm run build:iis
npm exec -- eslint scripts/publish-iis.mjs next.config.ts
```

Produksjonsbygget typekontrollerer prosjektet. Publiseringsskriptet sjekker
eksporterte ruter, HTML- og TXT-filer, lokale henvisninger, bildeformater og
fravær av de identifiserte utviklingsbundlene.

Oppsettet har ikke en full nettlesertest eller full automatisk
sikkerhetsgjennomgang. Se [kvalitetskontrollen](kvalitet.md).

## Lagre endringer

- Endre kildekoden, ikke genererte filer.
- Opprett en pull request med utfylt sjekkliste.
- Kontroller at GitHub Actions har bestått.
- Oppdater dokumentasjon og endringslogg ved atferdsendringer.
- Opprett en release når en godkjent pakke skal publiseres.

## Dokumentasjonsbygg

```powershell
python -m venv .venv-docs
.\.venv-docs\Scripts\python.exe -m pip install -r requirements-docs.txt
.\.venv-docs\Scripts\python.exe -m mkdocs build --strict
```

`site` inneholder det genererte dokumentasjonsnettstedet. Det skal ikke inn i
IIS-pakken. Kjør ikke `mkdocs serve` som del av den avtalte CLI-kontrollen.

## Offentlig dokumentasjon på GitHub Pages

Nettsidekoden forblir privat. Prosjekteier har godkjent offentlig publisering
av dokumentasjonen fra det separate repoet
`Scangolf/SCANGOLF-Nettside-versjon2026-docs`.
Dette fungerer med GitHub Free uten å gjøre nettsidekoden offentlig.

Dokumentasjonskilden vedlikeholdes i `docs` i det private nettsiderepoet.
Etter endringer:

1. Gjennomgå teksten før publisering: den blir offentlig, inkludert Git-historikken.
2. Kjør `mkdocs build --strict` som beskrevet ovenfor.
3. Klon det offentlige dokumentasjonsrepoet til en separat lokal mappe dersom
   det ikke allerede finnes.
4. Kjør synkroniseringsskriptet fra det private nettsideprosjektet:

```powershell
.\scripts\sync-docs.ps1 -Destination 'C:\Dev\SCANGOLF-Nettside-versjon2026-docs'
```

5. Skriptet kopierer bare Markdown-dokumentasjonen, `mkdocs.yml` og
   `requirements-docs.txt`. Det krever en ren arbeidsmappe med riktig remote.
   Det gjør ingen commit, push eller IIS-opplasting.
6. Gå gjennom endringene i dokumentasjonsrepoet og lagre dem i Git.
   Nye commits på `main` bygger og publiserer Pages automatisk.
7. Bekreft Actions-resultatet og HTTP 200 på dokumentasjonsadressen med CLI.

Kopier aldri hele nettsideprosjektet, `.env`, releaser, `_old` eller
IIS-pakken inn i det offentlige repoet. Workflowen i dokumentasjonsrepoet
har ingen tilgang til det private nettstedets kildekode.

Lenker til private oppgaver, releaser og Projects krever fortsatt innlogging
og tilgang; de blir ikke offentlige fordi dokumentasjonen lenker til dem.
