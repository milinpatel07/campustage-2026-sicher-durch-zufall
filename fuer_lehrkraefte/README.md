# Hinweise für Lehrkräfte

Notebooks *Der KI-Blick* und *Sicher durch Zufall? Wie viel Testen reicht?*

---

## Lernziel

**Ein automatisiertes Fahrzeug erkennt keine Person, es berechnet eine Zahl. Ab welcher Zahl eine Erkennung zählt, legen Menschen fest.**

Daraus folgen drei Einsichten, die die Teilnehmenden im Notebook selbst erarbeiten:

1. Jeder Schwellenwert ist ein Zielkonflikt zwischen übersehenen Personen und Fehlalarmen.
2. Schlechte Sicht verschiebt diesen Zielkonflikt. Darauf reagieren Menschen mit Entscheidungen, etwa mit einem begrenzten Einsatzbereich.
3. Zufällige Störungen und gezielte Angriffe sind verschiedene Probleme (Safety und Security).

## Ablauf des Workshop-Notebooks

| Teil | Dauer | Inhalt |
|---|---|---|
| Vorbereitung | 1–2 Min | *Laufzeit → Alle ausführen*, das Modell wird geladen |
| 1 · Bild und Referenz | 3 Min | Bild wählen, Personen zählen (mit Zeitmessung) |
| 2 · Objekterkennung | 3 Min | Erkennungen, verworfene Kandidaten, Frage „Wer hat 0,30 festgelegt?“ |
| 3 · Schwellenwert | 5 Min | Regler, übersehene Personen und Fehlalarme, Arbeitspunkt festlegen, Zielkonflikt |
| 4 · Schlechte Sicht | 4 Min | Einschätzung, Simulation, Auswertung, zweite Entscheidung |
| 5 · Zufall oder Absicht | 4 Min | Zufallsmuster und berechnetes Muster |
| Abschluss | 2 Min | Dieselbe Frage wie in Teil 2, Ergebnis, Fachbegriffe |

Die Frage „Wer hat festgelegt, dass der Schwellenwert 0,30 beträgt?“ wird vor Teil 3 und im Abschluss gestellt.
Das Notebook zeigt beide Antworten nebeneinander.

## Ergebnisse mit dem Beispielbild

Gemessen mit `ultralytics 8.4.216` und `yolov8n.pt`. In Colab können einzelne Werte geringfügig abweichen.

- Im Bild sind vier Personen, eine davon nur halb am linken Bildrand. Viele zählen drei oder vier.
- Beim Schwellenwert 0,30 erkennt das Modell drei Personen. Unter den verworfenen Kandidaten erscheint die vierte Person mit einer Konfidenz von etwa 0,24, daneben Fehldeutungen wie „Krawatte 0,06“ oder „Fahrrad 0,08“.
- Beim Schwellenwert 0,20 werden alle vier Personen erkannt, beim Schwellenwert 0,05 entstehen Fehlalarme.
- Schlechte Sicht (70 % Stärke, Schwellenwert 0,30): Regen kostet eine Person, Nebel und Dunkelheit keine. Bei höherem Schwellenwert ändern sich die Ergebnisse; die Texte im Notebook passen sich an.
- Muster mit 35 % der Personengröße: Das Zufallsmuster senkt die Konfidenz auf etwa 0,76, das berechnete Muster auf etwa 0,12. Wirksam ist das berechnete Muster je nach Person ab etwa 25–35 %.

## Einsatzmöglichkeiten

- **Als Teil einer Veranstaltung** (wie bei den Campustagen): nach einer Einführung in automatisiertes Fahren und gegebenenfalls einer Demonstration mit einem Roboterfahrzeug. Ein Foto aus dessen Kamera kann in Teil 1 hochgeladen werden.
- **Als Unterrichtsstunde (45 Minuten):** 5 Minuten Einstieg, 25 Minuten Notebook, 15 Minuten Nachbesprechung.
- **Zur Vertiefung:** das Notebook *Wie viel Testen reicht?* (etwa 10 Minuten), geeignet als Hausaufgabe oder für eine zweite Stunde.

## Fragen für die Nachbesprechung

- Wer hat den Schwellenwert festgelegt, und wie sollte man ihn begründen?
- Warum gibt es keinen Schwellenwert, der weder Personen übersieht noch Fehlalarme erzeugt?
- Ein Fahrzeug erkennt bei Nebel Personen schlechter. Welche Möglichkeiten gibt es außer einem anderen Schwellenwert?
- Was unterscheidet ein zufälliges Muster von einem berechneten Angriff? Was davon ist Safety, was Security?
- Ein Fahrzeug hat 1.000 Testfahrten ohne Fehler absolviert. Ist es damit sicher?

## Bewusste Vereinfachungen

- Übersehene Personen und Fehlalarme werden in Teil 3 nur über die **Anzahl** mit der eigenen Zählung verglichen, nicht für jede einzelne Person.
- Nebel, Regen und Dunkelheit sind **vereinfacht simuliert**. Echte Bedingungen, etwa Blendung durch Scheinwerfer, sind anspruchsvoller.
- Die **Konfidenz** ist ein Wert des Modells, keine kalibrierte Wahrscheinlichkeit. Vertiefung: `06_AI_Safety/notebooks/04_calibration_reliability.ipynb`.
- Der **gezielte Angriff** ist digital und setzt die genaue Kenntnis des Modells voraus. Physische Angriffe sind in der Forschung gezeigt worden (Eykholt et al., 2018; Thys et al., 2019), aber deutlich schwerer umzusetzen.
- Ein Fahrzeug entscheidet nicht anhand eines einzelnen Bildes. Reale Systeme kombinieren mehrere Sensoren und werten mehrere aufeinanderfolgende Bilder aus.

## Begleitende Erhebung (optional)

Für eine Vorher-nachher-Erhebung, etwa mit Mentimeter, eignet sich die Frage aus dem Notebook in einer konkreteren Formulierung:
*„Wer hat entschieden, wo der Regler steht?“* (Das KI-Modell selbst / Der Zufall / Ein Mensch),
gestellt vor Teil 3 und nach dem Abschluss. Wenige Fragen insgesamt halten die Beteiligung hoch.

## Probleme und Lösungen

| Problem | Lösung |
|---|---|
| Schaltflächen reagieren nicht | Prüfen, ob unter *Vorbereitung* „Bereit“ steht; sonst *Laufzeit → Alle ausführen* |
| Meldung „Es ist ein Fehler aufgetreten“ | Die betreffende Zelle mit ▶ erneut ausführen |
| Eigenes Foto lässt sich nicht hochladen | Mit dem Beispielbild weiterarbeiten |
| Teil 5 zeigt keine Person | Im Bild wird keine Person erkannt; anderes Foto wählen |
| Kein Google-Konto vorhanden | Zu zweit an einem Gerät arbeiten |

---

*English summary: The workshop notebook (German, about 20 to 25 minutes, no coding) lets students set the detection threshold
of a real object detector themselves, test it under simulated poor visibility and compare a random patch with a computed
adversarial patch. Its learning goal: a vehicle does not see a person, it computes a number, and people decide which number counts.
The follow-up notebook covers random testing, the rule of three and systematic edge-case search.*
