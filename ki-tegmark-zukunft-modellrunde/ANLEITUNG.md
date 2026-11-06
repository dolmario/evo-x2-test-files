# Selbst nachbauen

Die folgenden Befehle sind portable Beispiele mit relativen Dateinamen und einer lokalen Loopback-Adresse. Sie wurden hier als Text vorbereitet; das Paket installiert nichts und startet keine Modelle. Eigene vorhandene Werkzeugversionen und deren `--help` vor Verwendung prüfen.

## 1. Modellserver
Ein passend lizenziertes GGUF-Modell selbst beziehen und die Herstellerhinweise lesen. Keine Gewichte aus diesem Begleitpaket erwarten. Das Modell muss zur verfügbaren Hardware passen.

```sh
llama-server -m model.gguf --alias test-model --host 127.0.0.1 --port 8089 --ctx-size 65536 --predict 32768 --reasoning-budget 8192 --jinja --chat-template-kwargs '{"enable_thinking":true}'
```

Die Thinking-Option ist modell- und Template-abhängig. Sie ist keine universelle Freigabe für jedes GGUF. Bei Modellen ohne passendes Template nicht behaupten, Thinking sei aktiv. Keine feste Temperatur und keinen Seed hinzufügen, wenn der Test native Standardzufälligkeit verlangt. Den tatsächlich verarbeiteten Request und Serverzustand dokumentieren. Der API-Endpunkt dieses Beispiels ist `http://127.0.0.1:8089/v1`.

## 2. OpenCode
In einer eigenen, neuen Konfiguration einen OpenAI-kompatiblen lokalen Provider auf den obigen Endpunkt und Alias `test-model` binden. Kontext und Ausgabelimit dokumentieren. Nur die erlaubten Wiki-Lese-/SearXNG-Werkzeuge freigeben; Shell, Dateischreiben und Agentendelegation sperren. Keine fremde bestehende Konfiguration überschreiben.

```sh
opencode --version
opencode serve --hostname 127.0.0.1 --port 4096
```

Danach in einem zweiten Terminal eine frische Sitzung mit dem ausgefüllten Prompt starten. Bei OpenCode2 werden in dieser Untersuchung die nativen `run --server`, `--model`, `--agent`, `--thinking` und `--format json` Optionen verwendet. OpenCode1 verwendet teilweise andere Attach-Optionen. Kein Versionswechsel mitten in einer Vergleichszelle. Vor dem eigentlichen Prompt prüfen, dass Wiki und SearXNG verbunden sind.

## 3. Hermes
Ein neues sitzungsbezogenes Hermes-Verzeichnis verwenden. Lokalen OpenAI-kompatiblen Provider konfigurieren: Endpunkt wie oben, Modellalias `test-model`, Kontext65536, Ausgabe32768, unterstützte Thinking-Stufe. Wiki und SearXNG als reine Recherchewerkzeuge konfigurieren. Keine privaten Profile, dauerhaften Erinnerungen oder vorherigen Gespräche übernehmen. Keine automatischen Installationen während des Tests.

```sh
hermes --help
hermes --provider custom -m test-model --reasoning high -t llm-wiki,searxng -z "Den vollständig ausgefüllten Prompt hier einsetzen"
```

`high` ist nur bei einem Modell mit dieser unterstützten Stufe zu verwenden. Nicht unterstützte Stufen sind ein Aufbaufehler, keine Modellantwort.

## 4. Cline
Ein frisches Cline-Profil im lokalen Planmodus anlegen, kompatiblen Provider auf denselben Modellserver binden und nur Recherche-/Lesewerkzeuge erlauben. Native Tool-Fehlerschwelle nicht auf eine eigene strengere Schwelle absenken. Workspace-Regeln müssen die eigene Wiki-Projekt-ID vor der ersten Suche setzen; keine fremde Projekt-ID aus einer anderen Installation übernehmen.

```sh
cline --version
cline --help
cline --plan --thinking high --provider openai-compatible --model test-model --json "Den vollständig ausgefüllten Prompt hier einsetzen"
```

Providerkonfiguration bleibt lokal. Dieses Paket enthält keine Zugangsdaten. Bei Cline das tatsächlich gesendete Ausgabelimit kontrollieren: eine Servergrenze ist nicht dasselbe wie ein explizites `max_tokens` Feld.

## 5. Werkzeuge und Wiederholungen
Eigenen Wiki-Lesedienst und SearXNG gemäß deren Dokumentation einrichten; der mitgelieferte Prompt funktioniert auch ohne Recherche, aber dann als andere Bedingung kennzeichnen. Keine privaten Inhalte oder erwarteten Antworten in den Recherchebestand aufnehmen. Für jede Wiederholung eine neue Sitzung starten, Datum/Faktenrahmen beibehalten, Toolzugang und native Sampling-Defaults erfassen. Vollständige Schlussantwort separat von Denkspur und Sitzungstitel speichern. Keine Antwort wegen ihres Inhalts wiederholen.

Öffentliche Werkzeugquellen:
- llama.cpp: https://github.com/ggml-org/llama.cpp
- OpenCode: https://github.com/anomalyco/opencode
- Hermes: https://github.com/NousResearch/hermes-agent
- Cline: https://github.com/cline/cline
- SearXNG: https://github.com/searxng/searxng
