# Campustage 2026 — Automatisiertes Fahren! Sicher durch Zufall?

Ein Workshop-Repository für Schülerinnen und Schüler der 11. Klasse.
Thema: **Wie „sieht" ein selbstfahrendes Auto — und wo versagt diese Wahrnehmung?**

**Milin Patel · Hochschule Kempten, Institut für Fahrerassistenz und vernetzte Mobilität (IFM)**
Lizenz: MIT

---

## Worum es geht

Selbstfahrende Autos erkennen ihre Umgebung mit Kamera und Künstlicher Intelligenz.
In diesem Workshop schauen die Teilnehmenden dieser KI beim Sehen zu — und finden mit
eigenen Händen heraus, wo sie an ihre Grenzen stößt: bei schlechtem Wetter, an einer
zu hoch oder zu niedrig gesetzten Erkennungs­schwelle, oder durch einen gezielten Angriff.

Die Leitfrage: **Eine KI sieht die Straße nicht schlechter als ein Mensch — sie sieht sie anders.**

---

## Schnellstart für Teilnehmende

Das Workshop-Notebook läuft direkt im Browser über Google Colab — ohne Installation.

**➜ [Notebook öffnen: *Der KI-Blick*](https://colab.research.google.com/github/milinpatel07/campustage-2026-sicher-durch-zufall/blob/main/01_Perception_Systems/notebooks/00_workshop_der_ki_blick.ipynb)**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/milinpatel07/campustage-2026-sicher-durch-zufall/blob/main/01_Perception_Systems/notebooks/00_workshop_der_ki_blick.ipynb)

1. Auf den Colab-Button klicken.
2. Mit einem Google-Konto anmelden.
3. Oben im Menü: **Laufzeit → Alle ausführen**. Der erste Start lädt kurz die KI.
4. Danach steuert man alles über Regler und Knöpfe — kein Code nötig.

---

## Das Workshop-Notebook

**`01_Perception_Systems/notebooks/00_workshop_der_ki_blick.ipynb`**

Der rote Faden in vier Schritten:

1. **Du zählst zuerst.** Eine echte Straßenszene — wie viele Menschen erkennst *du*?
2. **Die KI zählt.** Ein Klick, und die KI zeichnet Boxen mit Konfidenzwerten. Stimmt es überein?
3. **Die Grenze entscheidet.** Ein Regler für die Erkennungs­schwelle. Zu hoch — echte Menschen verschwinden. Zu niedrig — die KI „sieht" Dinge, die nicht da sind. Diese Grenze legt ein Mensch fest.
4. **Die Welt ist nicht sauber.** Nebel und Regen lassen die Erkennung einbrechen.

Am Ende steht die Erkenntnis: **Die KI sieht nicht, was du siehst. Sie sieht Zahlen — und Zahlen kann man täuschen.**

---

## Teil einer größeren Sammlung

Dieses Workshop-Notebook ist der Einstieg in ein umfassenderes Forschungs- und Lehrmaterial
zu Sicherheit und Security beim automatisierten Fahren. Wer tiefer einsteigen möchte, findet
in diesem Repository weitere Module — gedacht für Studierende und Interessierte:

| Modul | Inhalt |
|-------|--------|
| `01_Perception_Systems` | Objekterkennung, Fußgängererkennung, Sensorfusion, LiDAR, Datensätze |
| `02_Failure_Analysis` | Fehlerfälle, Out-of-Distribution, Corner Cases, adversariale Angriffe |
| `03_Functional_Safety` | ISO 26262, HARA, FMEA, Verifikation & Validierung |
| `04_SOTIF` | Safety of the Intended Functionality, Szenarioanalyse |
| `05_Cybersecurity` | Automotive Cybersecurity, TARA |
| `06_AI_Safety` | Sicherheit von KI-Komponenten |
| `07_Integration_Deployment` | Integration und Einsatz im Fahrzeug |

---

## Aufbau des Repositories

```
campustage-2026-sicher-durch-zufall/
├── README.md
├── LICENSE
├── requirements.txt
├── 01_Perception_Systems/
│   └── notebooks/
│       ├── 00_workshop_der_ki_blick.ipynb   ← Workshop-Notebook
│       ├── 03_object_detection.ipynb
│       ├── 05_pedestrian_detection.ipynb
│       └── ...
├── 02_Failure_Analysis/
├── 03_Functional_Safety/
├── 04_SOTIF/
├── 05_Cybersecurity/
├── 06_AI_Safety/
└── 07_Integration_Deployment/
```

---

## Technisches

Die Notebooks laufen in Google Colab ohne lokale Installation. Für den lokalen Betrieb:

```
pip install -r requirements.txt
```

Verwendet werden unter anderem `ultralytics` (YOLOv8), `ipywidgets`, `matplotlib` und `Pillow`.

---

## Lizenz

Veröffentlicht unter der MIT-Lizenz. Details in der Datei `LICENSE`.
Bei Verwendung im Unterricht oder in der Lehre ist ein Hinweis auf die Quelle willkommen.

**© 2026 Milin Patel, Hochschule Kempten (IFM)**
