# Arkitektur og filer

## Fra kildekode til IIS

```text
app + components + lib + public
              |
       npm run build:iis
              |
  Next.js produksjonseksport: out
              |
  Fil-, bilde- og lenkekontroll
              |
       iis-publisering
              |
  Manuell kopiering, uten _old
              |
       Windows IIS
```

`next.config.ts` setter `output: 'export'`, `trailingSlash: false` og
`images.unoptimized: true`. Bildene leveres direkte fra statiske filer,
ikke gjennom `/_next/image`.

## Mapper og filer

| Sted | Innhold | I Git? |
|---|---|---|
| `app` | Nettsidene og globale stiler | Ja |
| `components` | Felles toppmeny, bunntekst og komponenter | Ja |
| `lib` | Løsnings- og nyhetsdata | Ja |
| `public` | Bilder og kilden til IIS-konfigurasjon/instruksjoner | Ja |
| `scripts` | Kontroll, pakking og klargjøring | Ja |
| `docs`, `mkdocs.yml` | Denne dokumentasjonen | Ja |
| `package-lock.json` | Låste npm-versjoner | Ja |
| `iis-publisering` | Ferdig opplastingspakke | Nei, bevares som release |
| `iis-publisering/_old` | Lokale sikkerhetskopier | Nei, aldri til serveren |
| `out`, `.next`, `node_modules`, `site` | Genererte filer | Nei |

## Hvorfor både HTML og TXT?

`booking.html` inneholder selve nettsiden. `booking.txt` inneholder offentlige
Next.js-sidedata for navigasjon mellom sider uten en Next.js-server.
Begge er nødvendige i denne eksportmodellen.

Gamle ASP-filer er overflødige i opplastingspakken: URL Rewrite videresender
gamle adresser før ASP-kode trenger å kjøres. Gamle filer og lokale
instruksjoner som ikke skal til IIS, ligger i `_old`.

## IIS-regler

Kilden er `public/web.config`. Byggingen kopierer den til publiseringspakken.
Reglene setter `index.html` som standarddokument, håndterer HTTPS og ikke-www
på produksjonsdomenet, skriver rene adresser til eksisterende HTML-filer,
videresender gamle ASP-adresser og leverer en 404-side med feilstatus.

IIS må ha Static Content, Default Document og URL Rewrite Module 2.
HTTPS krever gyldig sertifikat og korrekt binding. Eventuell fremtidig
reverse proxy må vurderes separat; dagens HTTPS-regel bruker IIS-variabelen
`HTTPS`, ikke proxy-headere.

## Kontakt

Kontaktsiden tilbyr e-post og telefon. Den har ingen skjema-innsending og skal
ikke vise en bekreftelse på at serveren har mottatt en melding.
