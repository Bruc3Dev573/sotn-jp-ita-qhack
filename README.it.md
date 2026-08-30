# Castlevania: Symphony of the Night - JP-ITA QHack v1.3

[English](README.md) | **Italiano**

Patch per la versione giapponese Rev 2 di Castlevania: Symphony of the Night.

Questa patch combina la traduzione italiana v1.0 con le modifiche di QHack v1.3. Il gioco originale non è incluso.

## Stato

I controlli automatici di integrità e i test runtime mirati sono stati superati. Non è stata completata una partita al 201,1%, quindi la release va ancora considerata sperimentale.

Se trovi un crash, un softlock, una stanza difettosa, un problema con i salvataggi o del testo impaginato male, [apri una segnalazione](https://github.com/Bruc3Dev573/sotn-jp-ita-qhack/issues). Indica dispositivo o emulatore, hash della base, patcher utilizzato e punto del gioco in cui si verifica il problema.

## Base richiesta

- Seriale: `SLPM_860.23`
- MD5 Track 1: `5021f600f109703170486dda1f0f86c1`
- MD5 Track 2: `3ea3346af023f84b1413c975d3c530fa`

Applica questa patch alla Track 1 dopo aver applicato la traduzione italiana v1.0.

## File

```text
patches/jp-ita-qhack-v1.3.ppf
patches/jp-ita-qhack-v1.3.sha256
```

Note tecniche: [Come funziona](docs/how-it-works.md) (in inglese).

## Utilizzo

1. Verifica gli MD5 del disco giapponese Rev 2.
2. Applica la traduzione italiana v1.0 alla Track 1.
3. Applica `jp-ita-qhack-v1.3.ppf` alla Track 1 tradotta.
4. Mantieni la Track 2 originale e aggiorna il file CUE con i nomi dei file locali.

Track 1 prevista:

```text
SHA-256 d4d2e2e8eb60147e7efba79e78f9f1fc4383ccd59f280be7a4a39aa646effbbc
```

Checksum della patch:

```text
SHA-256 62ff138defcd11d2b192b16407c3acffa5d33a5fc6b508ac277de2329e7b0853
```

## Modifiche QHack

- gioco a schermo intero senza bande nere sopra e sotto
- tile map espanse
- stanze sotto la botola d'ingresso in entrambi i castelli
- sfondi e cornici dei menu espansi
- uscita dal cancello del castello bloccata per Richter
- Death skip in forma di lupo bloccato
- limite della Cappella Reale corretto
- stanze di caricamento mostrate in bianco sulla mappa
- audio stereo abilitato come impostazione predefinita

## Screenshot

| Gioco a schermo intero | Menu dei file in italiano |
|:---:|:---:|
| ![Gioco a schermo intero](docs/screenshots/fullscreen-gameplay.png) | ![Menu dei file in italiano](docs/screenshots/italian-status.png) |

## Crediti

- [QHack v1.3](https://www.romhacking.net/hacks/3606/) di paul_met
- [Traduzione italiana v1.0](https://www.romhacking.net/translations/1171/) di Gemini

Le condizioni di attribuzione e ridistribuzione del materiale originale del progetto sono descritte in [`NOTICE`](NOTICE).

## Avvertenze

Questa patch è stata realizzata su richiesta. È un progetto non ufficiale e non offre alcuna garanzia. Konami e gli autori citati nei crediti non sono coinvolti. È necessaria una copia personale del gioco.

Se detieni i diritti su materiale utilizzato qui e vuoi richiederne la rimozione, apri una segnalazione. La richiesta verrà esaminata e i file interessati verranno rimossi se necessario.

Questo repository contiene solo la patch e i relativi checksum.
