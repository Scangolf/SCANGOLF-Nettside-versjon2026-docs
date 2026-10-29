# Kvalitetskontroll

## Hva kontrolleres automatisk?

`npm run build:iis` bygger og typekontrollerer prosjektet og kontrollerer:

- Eksporterte sider og tilsvarende TXT-navigasjonsdata.
- Interne henvisninger i HTML og ressursadresser i CSS.
- At bilder ikke krever `/_next/image`.
- PNG-, JPEG- og WebP-signaturer.
- Identifiserte utviklings- og HMR-markører.
- E-post-/telefonkontakt i stedet for det inaktive kontaktskjemaet.

GitHub Actions bygger dessuten MkDocs med `--strict` og lagrer byggepakker som
private workflow-artefakter. Dette er ikke automatisk publisering til IIS.

## Manuell CLI-kontroll etter opplasting

Kjør fra PowerShell. `curl.exe` brukes eksplisitt for å unngå aliaser.

```powershell
curl.exe -I https://cs25.clubsite.no/
curl.exe -I https://cs25.clubsite.no/booking
curl.exe -I https://cs25.clubsite.no/losninger
curl.exe -I https://cs25.clubsite.no/losninger/clubsite-ai-assistent
curl.exe -I https://cs25.clubsite.no/nyheter
curl.exe -I https://cs25.clubsite.no/nyheter/har-fatt-ny-hjelper-pa-hjemmesiden
curl.exe -I https://cs25.clubsite.no/booking.txt
curl.exe -I https://cs25.clubsite.no/assets/images/cs.png
curl.exe -I https://cs25.clubsite.no/default.asp
curl.exe -I "http://cs25.clubsite.no/booking?test=1"
curl.exe -I https://cs25.clubsite.no/ikke-en-ekte-side
```

Forventninger:

- [ ] Eksisterende sider, bilder og sidedata gir 200.
- [ ] Gamle ASP-adresser gir 301 til riktig ny adresse.
- [ ] HTTP gir HTTPS med sti og query bevart.
- [ ] Forsiden omdirigerer ikke til seg selv.
- [ ] Ugyldig adresse gir HTTP 404, ikke 200 med en feilside.
- [ ] Representative CSS-, JavaScript- og fontadresser fra HTML-en gir 200.

## Hva er ikke dokumentert av en HTTP-kontroll?

Status 200 eller en gyldig bildefil beviser ikke riktig utseende, fungerende
mobilmeny eller god tilgjengelighet. Visuell kontroll og interaksjonstesting
må avtales separat. Ingen nettleser eller Playwright skal startes automatisk
i denne arbeidsrutinen.

## Historisk grunnlag 29. oktober 2026

Før Git-oppsettet ble følgende lokale resultater registrert:

- 25 genererte nettsider og 1 061 lokale henvisninger kontrollert ved bygging.
- 67 lokale IIS Express HTTP-kontroller uten rapportert feil.
- En tidligere integrert Playwright-gjennomgang rapporterte 25 sider med
  status 200, 143 bildeelementer uten rapportert bildefeil, ingen rapporterte
  JavaScript-feil og ingen mislykkede forespørsler.

Den historiske Playwright-kontrollen var **ikke Playwright CLI**. Det ble ikke
lagret skjermbilder av alle sidene. Disse resultatene er ikke nye tester av
det publiserte domenet og dokumenterer ikke at alle sider er visuelt riktige.
