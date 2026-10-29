# SCANGOLF – nettside 2026

Dette er vedlikeholdsdokumentasjonen for <https://cs25.clubsite.no>.
Nettsiden bygges fra React/Next.js til statiske filer som publiseres manuelt
på Windows IIS. Node.js kreves på byggemaskinen, ikke på webserveren.

## Dagens status

- Nettsidekoden, releasene og Projects-tavlen ligger privat.
- Dokumentasjonen publiseres separat på
  [offentlig GitHub Pages](https://scangolf.github.io/SCANGOLF-Nettside-versjon2026-docs/)
  fra [dokumentasjonsrepoet](https://github.com/Scangolf/SCANGOLF-Nettside-versjon2026-docs).
- Prosjekteier har bekreftet publisering av den nye nettsiden 29. oktober 2026.
- Første release bevarer den lokale publiseringspakken slik den forelå etter
  denne bekreftelsen. Det er ikke en nedlasting fra serveren og dokumenterer
  derfor ikke at hver fil på serveren er identisk.
- Endringer i nettsiden skal gå via Git, bygging og sjekklistene nedenfor.
- GitHub Free støtter Pages fra det offentlige dokumentasjonsrepoet.
  Det private nettsiderepoet har ingen Pages-publisering.

## Start her

1. Les [arkitekturen og filoversikten](arkitektur.md).
2. Følg [utviklingsrutinen](utvikling.md) når kildekoden endres.
3. Bruk [publiseringssjekklisten](publisering.md) ved hver opplasting.
4. Registrer arbeid i [planen og Projects-tavlen](plan.md).

## Viktige regler

- Hele innholdet i `iis-publisering` kopieres til IIS, **unntatt `_old`**.
- Genererte TXT-sidedata skal følge med.
- `404.html` er en nødvendig feilside, ikke et tegn på mislykket bygg.
- Ikke rediger ferdigbygde HTML-filer manuelt.
- Ikke lagre hemmeligheter, gamle nettstedskopier eller `_old` i Git.
- Kontroller med CLI. Ikke start nettleser, Playwright eller lokal webserver
  som del av arbeidsrutinen uten en ny, uttrykkelig avtale med prosjekteier.
