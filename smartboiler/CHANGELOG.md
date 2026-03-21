<!-- https://developers.home-assistant.io/docs/add-ons/presentation#keeping-a-changelog -->

## 2.0.0

**Complete architectural rewrite — no breaking config migration needed (all config moves to web UI wizard).**

### What's new
- **Rolling histogram predictor** replaces the LSTM network — works from week 1, no GPU required, adapts to routine changes automatically
- **Greedy day-ahead scheduler** with standby-loss-adjusted cost minimisation
- **Day-ahead spot electricity prices** via free energy-charts.info API (CZ/SK/AT/DE/PL/HU/FR/IT/ES)
- **HDO ripple-control auto-learning** — detects blocking pattern from relay `unavailable` state; explicit schedule also supported
- **Web UI setup wizard** — all configuration via browser, no YAML editing
- **4-level water temperature estimation** — NTC probe → power feedback → thermal model → last known value
- **Newton's law thermal model** for boiler cooling curve estimation without internal sensor
- **Legionella protection** — 65 °C full heat cycle every 21 days, persisted across restarts
- **PV surplus scheduling** with battery-priority allocation (`battery_first` / `boiler_first` / `sell_first`)
- **Calendar event modes** via HA Calendar entity (`#off`, `#boost`, `#min`, `heat water at N`)
- **Flask dashboard** on port 8099 via HA ingress — shows temperature trajectory, 24h plan, histogram, spot prices, HDO schedule
- **Persistent state** in `/data/` directory (survives restarts and updates)

### Removed
- InfluxDB dependency (replaced by HA native history API)
- LSTM / TensorFlow / Keras / HDF5 dependencies
- Google Calendar direct API token (replaced by HA Calendar entity)
- Solax Cloud API / `fotovoltaics.py` (replaced by generic PV entity input)
- NMap device tracker requirement (person entities now used directly)
- AccuWeather API dependency
- Hardcoded 2-device-tracker limit (now accepts any number via `person_entity_ids`)
- Manual `config.yaml` options (all moved to web UI wizard)

---

## 1.5.4

- Stability fixes for controller loop
- Improved ESPHome sensor compatibility

## 1.5.0

- Added PV surplus scheduling support
- HDO schedule parsing improvements

## 1.0

Initial release — LSTM-based hot water consumption prediction with InfluxDB data source, Google Calendar integration, and Solax PV support.
