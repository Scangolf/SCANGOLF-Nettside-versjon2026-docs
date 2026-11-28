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

Publisering skjer med PowerShell Remoting via WinRM HTTPS til
`remote.clubsite.no` med godkjent legitimasjon. Kontroller først at IIS-siten
`CLUBSITE-HOME`, app-poolen og den fysiske mappen stemmer. Sammenlign
pakkefilene med serveren, sikkerhetskopier filer som skal overskrives, og
verifiser filene etter overføring. Ikke publiser `_old` eller slett filer på
serveren som ikke finnes i pakken. Kontroller spesielt endringer i
`web.config` før den eventuelt erstattes.

Test berørte sider på det publiserte nettstedet før kildeendringene committes.
Push utføres bare etter egen beskjed.

`npm run deploy:iis` og `scripts/publish-ftps.ps1` er eldre FTPS-oppsett,
ikke WinRM-rutinen, og skal ikke brukes til denne publiseringen. Prosjektet
har foreløpig ikke et eget WinRM-publiseringsscript.

## Tilbakeføring

Gjenopprett overskrevne filer fra den aktuelle serverbackupen til samme
relative plassering i webroten. Nye filer har ingen tidligere versjon å
gjenopprette; vurder dem separat ved tilbakeføring. Legitimasjon skal aldri
lagres i prosjektet eller deles.
