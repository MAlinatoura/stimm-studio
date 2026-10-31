# Stimm-Studio

Mobile Aufnahmeseite, um die eigene Stimme für ein [Piper](https://github.com/OHF-Voice/piper1-gpl)-TTS-Modell einzusprechen.

- Läuft komplett im Browser, keine Aufnahme verlässt das Gerät.
- Speichert WAV (22050 Hz, mono, 16 bit) im Browser (IndexedDB).
- Export als ZIP mit `wavs/` und `metadata.csv` (`datei.wav|Text`) für `python3 -m piper.train fit`.
- Satzkorpus: [Piper Recording Studio](https://github.com/rhasspy/piper-recording-studio), Deutsch, MIT-Lizenz.

**Keine Aufnahmen oder trainierten Stimmmodelle in dieses öffentliche Repo hochladen.**

## Nutzung

Online: https://malinatoura.github.io/stimm-studio/

## Lizenz

Code: [MIT](LICENSE) © 2026 Ali Natoura.
Die deutschen Standardsätze werden zur Laufzeit aus dem [Piper Recording Studio](https://github.com/rhasspy/piper-recording-studio) geladen (MIT, © 2023 Michael Hansen) und sind nicht Teil dieses Repos.
