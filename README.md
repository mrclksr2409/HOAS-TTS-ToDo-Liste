# HOAS TTS ToDo-Liste

Liest die Todo-Liste per TTS vor, sobald Anwesenheit erkannt wird. Nach dem Vorlesen werden alle Einträge als erledigt markiert. Täglich um Mitternacht werden alle erledigten Einträge automatisch gelöscht.

## Automationen

### 1. TTS ToDo-Liste (Blueprint)

Liest alle offenen Todo-Einträge vor und markiert sie anschließend als erledigt.

[![Blueprint importieren](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fraw.githubusercontent.com%2Fmrclksr2409%2FHOAS-TTS-ToDo-Liste%2Fmain%2Ftodo.yaml)

**Konfigurierbare Eingaben:**

| Input | Beschreibung |
|---|---|
| Todo-Liste | Die Todo-Listen Entität |
| Anwesenheitssensor | Binary Sensor der Anwesenheit erkennt |
| Person | Person die zu Hause sein muss |
| Mediaplayer | Mediaplayer auf dem vorgelesen wird |
| TTS Engine | TTS Engine Entität |
| Konversations-Agent | Konversationsagent zur Textaufbereitung |

### 2. ToDo-Liste täglich leeren

Löscht täglich um 00:00 Uhr alle erledigten Einträge. Die Datei `todo_cleanup.yaml` direkt als Automation in Home Assistant importieren.

## Ablauf

```
Anwesenheit erkannt
       ↓
Person zu Hause & offene Todos vorhanden?
       ↓
Todos abrufen → Claude aufbereiten → TTS vorlesen
       ↓
Alle Einträge als "erledigt" markieren
       ↓
       ... (täglich um 00:00)
       ↓
Erledigte Einträge endgültig löschen
```
