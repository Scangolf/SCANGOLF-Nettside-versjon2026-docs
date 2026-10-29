# SCANGOLF – offentlig nettsidedokumentasjon

Dokumentasjon: <https://scangolf.github.io/SCANGOLF-Nettside-versjon2026-docs/>

Dette offentlige repoet inneholder bare gjennomgått Markdown-dokumentasjon,
MkDocs-oppsett og GitHub Actions for dokumentasjonsnettstedet.
Det inneholder ikke nettsidens kildekode, IIS-pakke, releaser, miljøfiler,
tilgangsnøkler eller lokale sikkerhetskopier.

Nettsidekoden og arbeidsplanen ligger i et separat privat repo.
Lenker til private ressurser i dokumentasjonen krever tilgang.

## Vedlikehold

Dokumentasjonskilden vedlikeholdes i `docs` i det private nettsideprosjektet.
Bruk prosjektets `scripts\sync-docs.ps1` til å kopiere gjennomgåtte endringer
hit. Synkronisering skjer eksplisitt og kopierer ikke nettsideprosjektet.

Kjør CLI-bygg før commit:

```powershell
python -m venv .venv-docs
.\.venv-docs\Scripts\python.exe -m pip install -r requirements-docs.txt
.\.venv-docs\Scripts\python.exe -m mkdocs build --strict
```

Push til `main` bygger og publiserer GitHub Pages automatisk.
Workflowen kan også startes manuelt. Ingen av disse handlingene endrer
nettsiden på IIS eller har tilgang til det private kildekoderepoet.
