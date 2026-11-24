# Endringslogg

## 2026-10-29 – første versjonerte grunnlag

### Nettsiden før Git-oppsettet

- Statisk produksjonseksport erstattet tidligere utviklingskopier.
- Alle 25 sider ble generert, inkludert løsnings- og nyhetsdetaljer.
- Bildene bruker direkte filer i stedet for Next.js sin serverbaserte optimizer.
- Kontaktskjema uten reell sending ble erstattet med e-post-/telefonkontakt
  etter godkjenning fra prosjekteier.
- IIS-konfigurasjonen håndterer standarddokument, gamle adresser, rene URL-er,
  MIME-typer og en reell 404-feilside.
- Opplastingsregelen er «alt i iis-publisering, unntatt _old».

### Git og dokumentasjon

- Privat repo: `Scangolf/SCANGOLF-Nettside-versjon2026`.
- Kildekode, låsefil og byggeskript versjoneres; genererte filer holdes utenfor Git.
- Den lokale IIS-pakken bevares som release med ZIP og filhasher.
- MkDocs, oppgavemal og vedlikeholdsnotater er lagt til.
- En privat Projects-tavle brukes til videre vedlikehold.
- GitHub Pages er klargjort, men ikke aktivert. Publisering er utsatt i påvente
  av egnet organisasjonsabonnement og ny kontroll av innhold/synlighet.

Prosjekteier har bekreftet at nettsiden er publisert. Dette Git-oppsettet
gjør ingen nye endringer på IIS og inkluderer ingen ny nettleserkontroll.

## 2026-10-29 – offentlig dokumentasjon i separat repo

- Prosjekteier godkjente deretter offentlig dokumentasjon fra et eget repo,
  ikke offentlig nettsidekode.
- `Scangolf/SCANGOLF-Nettside-versjon2026-docs` inneholder bare gjennomgått
  Markdown-dokumentasjon og nødvendig MkDocs-/Pages-oppsett.
- Dokumentasjonskilden ligger på `main`; den ferdige nettsiden publiseres direkte
  fra en lokal MkDocs-bygging til `gh-pages`.
- Dokumentasjonskilden beholdes privat og synkroniseres eksplisitt med et
  avgrenset CLI-skript; det gjøres ingen automatisk kopiering av nettsidekode.
- Nettsidekoden, releasene og Projects-tavlen forblir private.
- Ingen endring gjøres i IIS-pakken eller på webserveren.

## 2026-11-19 – direkte publisering

- Nettsiden publiseres direkte til IIS, testes med Playwright og synkroniseres
  deretter til prosjektets Git-repo.
- Dokumentasjonen bygges lokalt med MkDocs og publiseres direkte til `gh-pages`.

## 2026-11-24 – samlet produksjonsversjon

- Alle akkumulerte nettsideendringer er bygget og publisert til det daværende
  utviklingsdomenet med server-side sikkerhetskopier.
- Versjonen omfatter blant annet GolfBox medlemsinnmelding, partner- og
  produktlogoer, oppdatert nyhetsside, Ski Golfklubb-saken, kontaktskjema med
  SMTP2GO-endepunkt, sitemap og nye redaksjonelle bilder.
- Sluttkontrollen viste 0 deployavvik. Forside, løsninger, nyheter, kontakt,
  GolfBox-siden, sitemap og mobilvisning ble kontrollert live.
- Headless Playwright CLI rapporterte 0 konsollfeil og 0 advarsler.
- Aktiv kildeversjon er commit `0d818c6` med etterfølgende dokumentasjonscommit.

## 2026-11-24 – overgang til clubsite.no

- `https://clubsite.no` er satt som canonical produksjonsdomene i metadata,
  sitemap, IIS-regler, kontaktskjema og aktiv dokumentasjon.
- HTTP, www-adressen og tidligere utviklingsvert omdirigeres permanent til
  produksjonsdomenet med sti og query bevart.
- Alle 38 sitemap-sider svarte 200 etter publisering. Automatisert headless
  kontroll fant ingen gamle domenelenker, brutte bilder eller konsollfeil.

## 2026-11-24 – GKIT-logo på tjenestesiden

- Banneret på `/tjenester` viser Golfklubbenes IT-logoen til høyre på desktop
  og under teksten på mobil.
- Logoen bruker en beskåret WebP-versjon uten gjennomsiktige kanter, med maks
  2 px hvit flate rundt selve logoen.
- Publisert til IIS med server-side sikkerhetskopier; slutt-preview viste 0
  avvik. Headless Playwright bekreftet logo, 2 px kant og 0 konsollfeil på
  desktop og mobil.
