# Publisering til IIS

## Redigering av toppmenyen

Menytekst, overskrifter, lenker og rekkefølge redigeres i
`lib/content/meny.ts`. Desktop, nettbrett og mobil bruker samme innholdsfil.
Behold formatet `{ label: 'Navn', href: '/side' }` for lenker. Interne lenker
må peke til eksisterende sider. Produktinnhold og sidens URL endres ikke ved
å redigere menyfilen.

## Kundeuttalelser

De delte kundeuttalelsene som vises på forsiden og `/referanser`, redigeres
kun i `lib/content/customerTestimonials.ts`. Begge sidene bruker samme
komponent og datakilde; ikke legg inn egne sitatkopier på enkeltsidene.

## Merkevare og produktnavn

ScanGolf Clubsite HUB er navnet på det samlede løsningsuniverset, med
slagordet «For golfklubber med ambisjoner!». Clubsite CMS, Clubsite Booking,
Scangolf.no, appene og partnerløsningene beholder sine egne produktnavn.
Sørg for at endringer i felles merkevaretekster ikke erstatter navnene på
enkeltproduktene eller endrer eksisterende URL-er.

Kjør kodekontroll og bygg før publisering. En endring i den felles
toppmenyen krever oppdaterte statiske sidefiler for sidene som viser menyen.

## Vanlig publisering

Bygg og kontroller IIS-pakken lokalt:

```powershell
npm run build:iis
```

For dette prosjektet bygges IIS-pakken lokalt og publiseres med WinSCP via
FTPS. Bruk Windows PowerShell 5.1 for publiseringsscriptet:

```powershell
npm run build:iis
& "$env:WINDIR\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -ExecutionPolicy Bypass -File scripts\publish-ftps.ps1 -Preview
```

Kontroller forhåndsvisningen før overføring. Scriptet henter legitimasjon fra
brukerens private `.scangolf`-mappe, sikkerhetskopierer filer som overskrives
på serveren, og sletter ikke eldre serverfiler. Ved avbrudd kan avgrensede
puljer sendes med `-OnlyFiles`; kjør deretter `-Preview` på nytt og bekreft at
det ikke står filer igjen å publisere. Ikke publiser `_old`.

Test de berørte sidene live med Playwright. Commit og push kildekoden etter
bestått kontroll og når dette er avtalt.

## Tilbakeføring

Gjenopprett overskrevne filer fra den aktuelle serverbackupen til samme
relative plassering i webroten med WinSCP. Nye filer har ingen tidligere
versjon å gjenopprette; vurder dem separat ved tilbakeføring. Legitimasjon
skal aldri lagres i prosjektet eller deles.
