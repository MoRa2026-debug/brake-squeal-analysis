# Brake Squeal Analysis – Signalverarbeitung

Projekt zur Signalanalyse von Bremsenquietschen basierend auf der Masterarbeit:

> **"Entwicklung und Erprobung einer Messmethodik zur Untersuchung der
> Quietschanfälligkeit von KFZ-Scheibenbremsen mittels piezoelektrischer
> Anregung im Bremskolben"**
> M. O. F. Rashell, TU Berlin, 2019

## Inhalt

- 10 synthetische Messdateien (Bremsdruck 1–10 bar)
- Jede CSV enthält: Zeit, externe Kraft, Beschleunigung
- Kritische Quietschfrequenz: **2,6 kHz** (ab ca. 6 bar sichtbar)

## Datenformat

| Spalte | Einheit | Beschreibung |
|--------|---------|--------------|
| `time_s` | s | Zeit |
| `force_N` | N | externe Kraft (Piezoaktor) |
| `accel_m_s2` | m/s² | Beschleunigung (Sensor) |

## Analyse

Die externe Arbeit wird berechnet als:

$$
W_{ext} = \frac{\pi}{\Omega^2} \, \hat{\ddot{z}} \, \hat{f}_{ext} \, \sin(\alpha)
$$

mit Phasenwinkel $\alpha = \phi_z - \phi_{ext}$.

## Verwendung

```bash
pip install -r requirements.txt
python generate_data.py     # erzeugt die CSVs
python analyze.py           # wertet sie aus
