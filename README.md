# SCANGOLF – offentlig nettsidedokumentasjon

Dokumentasjon: <https://scangolf.github.io/SCANGOLF-Nettside-versjon2026-docs/>

Dette offentlige repoet inneholder bare gjennomgått Markdown-dokumentasjon,
MkDocs-oppsett og nødvendig dokumentasjonskonfigurasjon.
Det inneholder ikke nettsidens kildekode, IIS-pakke, releaser, miljøfiler,
tilgangsnøkler eller lokale sikkerhetskopier.

Nettsidekoden og arbeidsplanen ligger i et separat privat repo.
Lenker til private ressurser i dokumentasjonen krever tilgang.

## Vedlikehold

Dokumentasjonskilden vedlikeholdes i `docs` i det private nettsideprosjektet.
Bruk prosjektets `scripts\sync-docs.ps1` til å kopiere gjennomgåtte endringer
hit. Synkronisering skjer eksplisitt og kopierer ikke nettsideprosjektet.

Bygg og publiser dokumentasjonen lokalt fra dette repoet:

```powershell
python -m venv .venv-docs
.\.venv-docs\Scripts\python.exe -m pip install -r requirements-docs.txt
.\.venv-docs\Scripts\python.exe -m mkdocs build --strict
.\.venv-docs\Scripts\python.exe -m mkdocs gh-deploy --force
```

Kommandoen publiserer den ferdigbygde dokumentasjonen direkte til `gh-pages`.
Kontroller deretter dokumentasjonsadressen i nettleser eller med CLI.
Nettsiden på IIS publiseres separat fra det private prosjektet.
