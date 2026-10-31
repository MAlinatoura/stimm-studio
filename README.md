# Stimm-Studio

Mobile Aufnahmeseite, um die eigene Stimme für ein [Piper](https://github.com/OHF-Voice/piper1-gpl)-TTS-Modell einzusprechen.

- Läuft komplett im Browser, keine Aufnahme verlässt das Gerät.
- Speichert WAV (22050 Hz, mono, 16 bit) im Browser (IndexedDB).
- Export als ZIP mit `wavs/` und `metadata.csv` (`datei.wav|Text`) für `python3 -m piper.train fit`.
- Satzkorpus: [Piper Recording Studio](https://github.com/rhasspy/piper-recording-studio), Deutsch, MIT-Lizenz.

**Keine Aufnahmen oder trainierten Stimmmodelle in dieses öffentliche Repo hochladen.**

## So funktioniert's

1. Seite auf dem Handy öffnen (Chrome oder Safari), beim ersten Aufnehmen das Mikrofon erlauben.
2. Satz lesen → **Aufnehmen** → vorlesen → **Stopp**. Die Seite springt automatisch zum nächsten Satz.
3. Versprecher? Satz neu aufnehmen – die alte Aufnahme wird ersetzt.

### Wo werden die Aufnahmen gespeichert?

- **Nur im Browser auf deinem Gerät** (IndexedDB). Nichts wird hochgeladen – nicht zu GitHub, nicht auf einen Server.
- Du kannst jederzeit aufhören und später weitermachen: Aufnahmen und Position bleiben erhalten.
- Gespeichert ist pro Browser und Gerät. In einem anderen Browser oder auf einem anderen Handy ist die Liste leer.
- **Verloren gehen sie**, wenn du Browserdaten/Website-Daten löschst, im privaten/Inkognito-Modus aufnimmst oder der Browser bei Speichermangel aufräumt. Auf iPhones kann WebKit Website-Daten nach längerer Nichtnutzung löschen.
- Deshalb: **nach jeder Session „Nur neue seit letztem Export“** tippen und die ZIP sichern (Android: *Downloads*, iPhone: *Dateien → Downloads*).

### Wie viel aufnehmen?

| Audio (Anzeige oben rechts) | Ergebnis |
|---|---|
| < 10 min | nur zum Testen |
| ~30 min | erstes brauchbares Modell |
| 60–90 min | guter Zielwert |

Pro Session 20–30 Minuten, immer gleicher Raum, gleicher Abstand (20–30 cm), gleiche Stimmlage.

### Training mit Piper

Alle ZIPs entpacken, `wavs/` zusammenführen, `metadata.csv`-Dateien aneinanderhängen, dann (siehe [piper1-gpl TRAINING.md](https://github.com/OHF-Voice/piper1-gpl/blob/main/docs/TRAINING.md)):

```sh
python3 -m piper.train fit \
  --data.voice_name "meine-stimme" \
  --data.csv_path metadata.csv \
  --data.audio_dir wavs/ \
  --model.sample_rate 22050 \
  --data.espeak_voice de \
  --data.cache_dir cache/ \
  --data.config_path de_DE-meine-stimme-medium.onnx.json \
  --data.batch_size 16 \
  --trainer.max_epochs 2000 \
  --model.warmstart_ckpt <deutscher-medium-checkpoint>.ckpt
```

Checkpoints: [rhasspy/piper-checkpoints](https://huggingface.co/datasets/rhasspy/piper-checkpoints)

## Nutzung

Online: https://malinatoura.github.io/stimm-studio/

## Lizenz

Code: [MIT](LICENSE) © 2026 Ali Natoura.
Die deutschen Standardsätze werden zur Laufzeit aus dem [Piper Recording Studio](https://github.com/rhasspy/piper-recording-studio) geladen (MIT, © 2023 Michael Hansen) und sind nicht Teil dieses Repos.
