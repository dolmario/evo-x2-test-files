# Methodik und Grenzen

## Aufgezeichnete Bedingungen
OpenCode1.19.0, OpenCode2.1.4, Hermes-Agent und Cline CLI3.0.74 wurden in getrennten Sitzungen verwendet. Die Hermes-Quellrevision beim Paketbau lautet `8f817911723e3ec13e7f47fc022fdcc9e2149354`; eine spätere Revision ersetzt nicht rückwirkend die alten Laufprotokolle. Der lokale Modellserver war llama.cpp, in den gespeicherten Startbefehlen Build b11580. Diese Angaben sind Werkzeugversionen, keine Modellbewertung.

Historische lokale Runden: Thinking angefordert, meist8192Denkbudget und32768Generationsgrenze, modellabhängig65536oder262144Kontext. Einzelne alte Fälle hatten abweichende unterstützte Reasoning-Stufen oder ein kleineres Denkbudget. Die betroffenen technischen Datensätze kennzeichnen das. Frühe120Wörter/Thinking-aus-Probeläufe sind keine gleichwertige Bedingung und nicht Teil der hier zusammengestellten Hauptrunde.

Die späteren datierten Runden ergänzten vor Prompt A die Zeilen:

    Heutiges Datum: 6. November 2026.
    Vergleichsrahmen: Lokaler Test mit Wiki und SearXNG; die Cloud-Antworten wurden getrennt geliefert.

Die ältere Hermes-Korrekturrunde hatte diesen neuen Datumsrahmen noch nicht. Alle Modelloriginale bleiben deshalb ihrer jeweiligen Runde zugeordnet. Zusätzliche Sitzungsanweisungen erklärten die Werkzeuge und die Projektbindung; sie waren keine neuen Fragen. Native Systemprompts und interne Agentenschleifen der Harnesse bleiben verschiedene Bedingungen.

Lokal waren Wiki-Lesen und SearXNG-Suche erlaubt. Cloudantworten wurden separat geliefert. Tatsächlich ausgeführte Toolaufrufe, Toolfehler und Quellenbelege sind verschiedene Dinge. Cline lief im Planmodus mit Lese-/Suchwerkzeugen, ohne Shell-, Schreib-, Ingest- oder Teamwerkzeuge. Ein Cline-Prozess kann mit0enden, obwohl der native Agent intern abgebrochen hat; der native Abschlussstatus wird zusätzlich erfasst. Cline ließ in den aufgezeichneten nativen Anfragen `max_tokens` aus; die Modellkonfiguration und der Server begrenzten auf32768. Diese Auslassung wird nicht durch Umschreiben des API-Mitschnitts verborgen.

Die ersten beiden Hermes-Aufbaukorrekturen installierten automatisch Python-Abhängigkeiten in isolierten Sitzungen. Ein Netzwerkdownload ist aus den vorhandenen Startzeilen nicht separat bewiesen. Danach waren Lazy-Installationen deaktiviert. Globale Harnesskonfigurationen wurden nicht geändert.

## Neu beauftragter Wiederholungstest
Zwei Modelle, drei Harnesse, jeweils drei Wiederholungen: Qwen3.6 normal und AxionQ4, rotierend OpenCode2/Hermes/Cline. Danach drei HauhauCS-Thinking-Fälle sowie je drei OpenCode2-Fälle der beiden Qwen3.8-Varianten. Ein weiteres MiniCPM-Paar ist erst nach vollständig geprüftem Eingang vorgesehen. Noch keine neue Schlussantwort oder Auswertung dieser Serie vorhanden.

Geplant: identischer Prompt A mit Datum, frische Sitzung, gemeinsamer Kontext65536, Thinking8192, Generationsgrenze32768, Wiki/SearXNG, keine explizit gesetzte Temperatur und kein fester Seed. Native Defaults werden im tatsächlichen Request erfasst. Frühere Runden hatten teilweise explizite Temperatur0,3; sie dürfen nicht still als dieselbe Sampling-Bedingung behandelt werden. Je Lauf20Minuten einschließlich Start. Ein Fehler bleibt Ergebnis; maximal ein Ersatz je Modell/Harness-Zelle bei Aufbau-/Deadlinefehlern, nie wegen einer unerwünschten Antwort. Ergebnisse und Varianzen werden erst nach separater Auswertung ergänzt.

## Trennungen bei der Auswertung
Prognose, unwahrscheinlichste Zukunft und eigene hypothetische Wahl getrennt erfassen. Originaltexte nicht korrigieren. Trainingsende nur als Selbstauskunft markieren. Ein durch Rechercheinhalte beeinflusstes Szenario nicht als freie Modellpräferenz darstellen. Ausbleibende Schlussantworten, Startfehler und ausgeschlossene Aufbaupiloten nicht in erfundene Antworten umwandeln. API-Denkspuren und automatische Sitzungstitel sind keine Schlussantworten und gehören nicht in die öffentliche Rohantwortsammlung.
