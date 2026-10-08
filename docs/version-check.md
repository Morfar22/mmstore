# MM – Store versionscheck

Serverkonsollen viser installeret version ved opstart og henter versions.json fra main i dette repository. Der tjekkes igen hver 6. time. Der installeres ingen filer automatisk.

## Kommandoer

Kør `mm_version_<ressourcenavn>` i serverkonsollen, fx `mm_version_advanced_k9` eller `mm_version_mm_bridge`, for et manuelt check. Kommandoerne kan ikke bruges af spillere.

I server.cfg kan du slå alle HTTP-versionschecks fra med `set mm_versioncheck 0`. Opstartsversionen vises stadig.

## Udgiv en opdatering

1. Ret `version` i ressourcens fxmanifest.lua til den nye version, fx 95.1.2. Brug major.minor.patch.
2. Byg og test pakken. Ved escrow: upload på det eksisterende Cfx-aktiv, hent og test Cfx-pakken, og gør den tilgængelig for kunderne.
3. Opret en GitHub Release med changelog. For betalte escrow-scripts distribueres den beskyttede pakke via Cfx/Tebex; læg ikke private kilde-ZIP-filer i det offentlige repository.
4. Ret den tilsvarende post i versions.json på main. Opdater `version` og `notes` først når pakken er tilgængelig.
5. Kør konsolkommandoen og verificer beskeden. GitHub raw caching kan give en kort forsinkelse.

Eksempel:

```json
"advanced_k9": {
  "version": "95.1.2",
  "notes": "Rettet køretøjsbure og forbedret tracking."
}
```

versions.json er en opdateringsoversigt. De angivne startversioner henviser til de nye Cfx-klare pakker med versionscheck; filen opdaterer ikke eksisterende kildekode eller opretter automatisk GitHub Releases.

Netværksfejl stopper ikke gameplay. Manglende eller ugyldig metadata logges som en advarsel. Identiske resultater gentages ikke ved hvert periodisk check. Checket sender kun en GET-anmodning til den offentlige versionsfil, uden spillerdata eller tokens, og eksekverer aldrig GitHub-indhold.
