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
- MkDocs, CI, oppgavemal og PR-sjekkliste er lagt til.
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
- Pages bygger ved push til dokumentasjonsrepoets `main` og kan også startes manuelt.
- Den ubrukte Pages-workflowen i det private nettsiderepoet er fjernet.
- Dokumentasjonskilden beholdes privat og synkroniseres eksplisitt med et
  avgrenset CLI-skript; det gjøres ingen automatisk kopiering av nettsidekode.
- Nettsidekoden, releasene og Projects-tavlen forblir private.
- Ingen endring gjøres i IIS-pakken eller på webserveren.
