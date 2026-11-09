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

Kjør kodekontroll og bygg før inkrementell publisering. En endring i den
felles toppmenyen krever oppdaterte statiske sidefiler for sidene som viser
menyen; uendrede ressurser skal fortsatt hoppes over.

## Vanlig publisering

Etter at innhold eller kode er endret, kjør én kommando fra prosjektmappen:

```powershell
npm run deploy:iis
```

Kommandoen bygger og kontrollerer den statiske IIS-pakken lokalt før den
kobler til serveren. Hvis byggingen feiler, blir ingenting lastet opp.

Publiseringen sammenligner SHA-256 for pakkefilene med siste vellykkede
publisering og sender bare nye eller endrede filer. Tilfeldig build-ID i
statisk HTML/TXT ignoreres i sammenligningen, slik at en endring på én side
ikke tvinger opplasting av alle sidene. Ressurser og interne skript sendes
før TXT-/HTML-sider, og `web.config` sendes sist. Hvis ingen filer er endret,
kobler publiseringen ikke til serveren og laster ingenting opp.

Før en eksisterende fil overskrives, lastes akkurat den filen ned til:

```text
iis-publisering\_old\serverbackup-<tidspunkt>\
```

Filer som ikke lenger finnes i den lokale pakken slettes ikke automatisk fra
serveren. Dette bevarer gamle, hashede ressurser som kan være i bruk av åpne
nettleserfaner. Kontroller eventuelle foreldreløse sider før manuell rydding.

## Forhåndsvisning av endringer

For å se hvilke filer som ville blitt publisert uten å koble til serveren:

```powershell
.\scripts\publish-ftps.ps1 -Preview
```

For å publisere et avgrenset utvalg fra den ferdigbygde pakken, oppgi relative
filbaner. Manifestet oppdateres da bare for filene som faktisk ble overført:

```powershell
.\scripts\publish-ftps.ps1 -OnlyFiles 'partner-apper/google-workspace.html','assets/images/workspace-non-profits.png'
```

SHA-256-manifestet for siste vellykkede opplasting og publiseringslogger
lagres lokalt utenfor prosjektet:

```text
%USERPROFILE%\.scangolf\cs25-iis-published.json
%USERPROFILE%\.scangolf\logs\
```

Ved første publisering på en ny maskin finnes ikke manifestet ennå. Da
publiseres hele pakken én gang; etter en vellykket opplasting blir videre
publiseringer inkrementelle.

## Tilbakeføring

De overskrevne serverfilene ligger i den lokale sikkerhetskopien nevnt over.
Kopier ønsket fil tilbake til samme relative plassering i webroten via FTPS.
Nye filer har ingen tidligere versjon å gjenopprette; publiser den tidligere
pakken på nytt for å tilbakeføre dem.

Påloggingen leses fra `%USERPROFILE%\.scangolf\cs25-ftp-credentials.ps1`.
Denne private filen skal ikke flyttes inn i prosjektmappen eller deles.
