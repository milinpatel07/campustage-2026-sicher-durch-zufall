# Hinweise für Lehrkräfte und Vortragende

Workshop *Automatisiertes Fahren! Sicher durch Zufall?* · Notebook *Der KI-Blick*

Diese Seite ist für die Menschen gedacht, die den Workshop leiten. Die Schülerinnen und Schüler brauchen sie nicht.

---

## Das Lernziel in einem Satz

**Ein Auto sieht keinen Menschen, es sieht eine Zahl. Ab welcher Zahl etwas als Mensch zählt, entscheiden Menschen.**

In der Evaluation des ersten Durchlaufs (27. Juli 2026, 8 Antworten) hat niemand die Frage
„Wer legt fest, ab wann das Auto etwas als Menschen erkennt?“ mit „Ein Mensch“ beantwortet.
Das Notebook ist deshalb so umgebaut, dass die Teilnehmenden diese Entscheidung selbst treffen und festhalten (Mission 4),
und die Frage im Finale noch einmal aufgegriffen wird.

## Ablauf im Notebook (ca. 25 Minuten)

| Mission | Zeit | Was passiert | Ihr Satz in den Raum |
|---|---|---|---|
| Start | 1–2 Min | Laufzeit → Alle ausführen, KI lädt | Die Ladezeit für eine kurze persönliche Vorstellung nutzen (steht bewusst nicht im Notebook). |
| 1 Bild | 2 Min | Beispielbild oder Roboter-Foto hochladen | „Jetzt schaut die KI durch die Augen unseres Roboters.“ |
| 2 Zähl-Duell | 2 Min | Selbst zählen, mit Stoppuhr | „Wie viele habt ihr? Wer war am schnellsten?“ |
| 3 KI schaut hin | 3 Min | Boxen, Konfidenz, dann *alle Vermutungen* | „Die KI hat den Mann links gesehen. Sie hat ihm nur nicht geglaubt.“ |
| 4 Grenze | 5 Min | Regler, Übersehen/Zu viel, *Entscheidung festhalten*, Dilemma | **„Wer stellt diesen Regler ein? Ihr. Gerade eben. Ein Mensch.“** |
| 5 Wetter | 4 Min | Tipp abgeben, ausprobieren, auswerten | „Wer hat richtig getippt?“ |
| 6 Aufkleber | 5 Min | Zufall gegen Berechnung, Challenge | „Wer schafft den kleinsten Aufkleber?“ |
| 7 Mensch oder KI | 3 Min | Sieben Situationen tippen | Gut auch gemeinsam per Handzeichen |
| Finale | 2 Min | Wer entscheidet? Protokoll, Freigabe | Überleitung zu den Berufen |

Wenn die Zeit knapp wird: Mission 7 gemeinsam mündlich machen, nicht am Gerät.

## Was beim Beispielbild passiert

Die folgenden Werte stammen aus einem Testlauf mit `ultralytics 8.4.216` und `yolov8n.pt`.
In Colab können sie um ein, zwei Prozentpunkte abweichen.

- Auf dem Bild sind **vier Menschen**, einer davon nur halb am linken Bildrand. Die meisten zählen 3 oder 4.
- Bei der Standardgrenze von 30 % findet die KI **drei**. Schalten die Teilnehmenden *alle Vermutungen* ein,
  erscheint der vierte grau gestrichelt mit etwa **24 %**. Dazu tauchen Vermutungen wie „Krawatte 6 %“ oder
  „Handtasche 5 %“ auf. Das sorgt meist für Lacher und ist ein guter Einstieg in Mission 4.
- Senkt man die Grenze auf 20 %, ist der vierte Mensch wieder da.
- Beim Wetter (70 % Stärke, Grenze 30 %) hat im Test **Regen** einen Menschen gekostet; Nebel und Dunkelheit keinen.
  Das Ergebnis hängt von der eingestellten Grenze ab, der Text im Notebook passt sich an.
- Der **zufällige Aufkleber** lässt im Test praktisch nie einen Menschen verschwinden.
  Der **berechnete Aufkleber** (50 Rechenschritte, ca. 6–10 Sekunden ohne GPU) schafft es ab etwa 25–35 % der Körpergröße.

## Verbindung zum Roboter

- **Mission 1:** Das Foto aus der Roboter-Kamera vorher auf ein Gerät übertragen, damit es hochgeladen werden kann
  (oder per Beamer gemeinsam mit einem Gerät).
- **Experiment (nicht getestet):** In Mission 6 lässt sich der berechnete Aufkleber speichern. Ausdrucken und vor die
  Roboter-Kamera halten. Sehr wahrscheinlich wirkt er dort *nicht*, weil er für genau dieses Foto und genau dieses
  Modell berechnet wurde. Gerade das ist ein guter Gesprächsanlass: Warum ist ein Angriff in der echten Welt schwerer?

## Bewusste Vereinfachungen

Damit niemand später etwas Falsches mitnimmt:

- „Übersehen“ und „Zu viel erkannt“ in Mission 4 vergleichen nur **Anzahlen** mit der eigenen Zählung,
  nicht, ob jeder Kasten auf dem richtigen Menschen sitzt.
- Nebel, Regen und Dunkelheit sind **am Computer nachgemacht**. Echte Bedingungen sind schwieriger.
- Die Konfidenz ist eine Art Sicherheitswert des Modells, **keine echte Wahrscheinlichkeit**.
  Wie gut solche Werte zur Wirklichkeit passen, behandelt `06_AI_Safety/notebooks/04_calibration_reliability.ipynb`.
- Der Aufkleber-Angriff ist **digital** und kennt das Modell genau. Physische Angriffe sind in der Forschung gezeigt worden
  (zum Beispiel Aufkleber auf Stoppschildern, Eykholt et al., CVPR 2018), aber deutlich schwieriger.

## Profi-Wörter

An passenden Stellen schalten die Teilnehmenden neun Fachbegriffe frei, meist englisch, wie sie in Forschung und Industrie benutzt werden.
Im Finale erscheinen alle gesammelten Begriffe als persönliches Wörterbuch.

| Mission | Profi-Wort | Wird freigeschaltet, wenn … |
|---|---|---|
| 3 | Bounding Box, Confidence | die KI zum ersten Mal hinschaut |
| 4 | False Negative / False Positive | der Regler einen Menschen übersieht / zu viele meldet |
| 4 | Threshold | die Entscheidung festgehalten wird |
| 5 | ODD (Operational Design Domain) | das Wetter ausgewertet wird |
| 6 | Adversarial Attack | ein Aufkleber berechnet wurde |
| 7 | Sensor Fusion | alle sieben Situationen beantwortet sind |
| Finale | Safety & Security | die Abschlussfrage beantwortet ist |

„False Positive“ erscheint nur, wenn jemand den Regler ganz nach links schiebt. Ein guter Anlass, im Raum zu fragen: Wer hat alle neun?

## Wenn etwas hakt

| Problem | Lösung |
|---|---|
| Knöpfe reagieren nicht | Prüfen, ob die Start-Zelle *Bereit* zeigt. Sonst Laufzeit → Alle ausführen. |
| „Hoppla, hier ist etwas schiefgelaufen“ | Die Zelle mit ▶ links neu ausführen. |
| Upload klappt nicht | Beispielbild nehmen, der Ablauf funktioniert genauso. |
| Mission 6 findet keinen Menschen | Bild hat keinen erkannten Menschen, anderes Foto nehmen. Nach Änderung der Grenze *Bild neu laden* drücken. |
| Kein Google-Konto | Zu zweit an einem Gerät arbeiten. |

## Umfrage: Empfehlungen aus dem ersten Durchlauf

- Die Lernfrage **vor und nach** dem Notebook stellen, damit eine Veränderung messbar wird.
- Konkreter formulieren: *„Wer hat entschieden, wo der Regler steht?“* (Die KI / Der Zufall / Ein Mensch)
- Weniger Fragen insgesamt. Die Beteiligung fiel im ersten Durchlauf von 100 % auf 50 %.

---

## Presenter notes (English)

**Core message:** the car does not see a person, it sees a number, and *people* decide which number counts.
In the first run nobody got this (0 of 6). The notebook now makes students set the threshold themselves,
lock it in with a button, and face the trade-off (missed person vs. phantom braking). Say the key line out loud
while they still have the slider in their hands: *„Wer stellt diesen Regler ein? Ihr. Gerade eben. Ein Mensch.“*

**What changed compared to the first version**

- Seven short "missions" with a role frame: students are the development team and decide at the end whether the car may drive.
- Count duel with a stopwatch; the student's own count is then used to show *missed* and *extra* detections live.
- "Show all guesses" reveals that the model *did* see the half-hidden person (about 24 %) and rejected it at the default 30 % limit.
- Weather mission starts with a prediction, uses the student's own threshold, and the evaluation text adapts to the actual result.
- New sticker mission: random patch vs. a computed (gradient-based) patch. "Zufall trifft fast nie. Absicht schon." This answers the title question.
- Mensch-oder-KI quiz to land "not better, not worse: different".
- Nine "Profi-Wörter" (Confidence, Threshold, False Negative, ODD, Adversarial Attack, …) unlock at the moment students experience them; the finale shows their personal glossary.
- Finale: learning check, personal mission log, release decision, then a table linking each mission to real jobs.
- Only two follow-up notebooks are shown; the other 30+ are mentioned as "there for later, e.g. in a Bachelor's or Master's".
- Code cells are collapsed in Colab (forms), all interaction is buttons and sliders, all errors show a friendly message.
- Example image now ships with the `ultralytics` package (no download at runtime), version pinned to 8.4.216.

**Your introduction is live, not written.** The notebook deliberately contains no personal note; use the 1–2 minutes while the model loads to introduce yourself.

**Please check before the next run:** have a native German speaker read the student texts once, and do one full dry run in Colab.
