# Stimm-Studio

Mobile Aufnahmeseite, um die eigene Stimme für ein [Piper](https://github.com/OHF-Voice/piper1-gpl)-TTS-Modell einzusprechen.

- Läuft komplett im Browser, keine Aufnahme verlässt das Gerät.
- Speichert WAV (22050 Hz, mono, 16 bit) im Browser (IndexedDB).
- Export als ZIP mit `wavs/` und `metadata.csv` (`datei.wav|Text`) für `python3 -m piper.train fit`.
- Satzkorpus: [Piper Recording Studio](https://github.com/rhasspy/piper-recording-studio), Deutsch, MIT-Lizenz.

**Keine Aufnahmen oder trainierten Stimmmodelle in dieses öffentliche Repo hochladen.**
