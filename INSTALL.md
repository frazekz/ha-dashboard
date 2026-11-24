# How to adapt this dashboard

This public edition is a starting point, not a packaged install. It will not run as a one-click replacement of your current Lovelace UI.

## What you need

- A working Home Assistant instance
- Lovelace in YAML mode (or a dashboard you are willing to include by YAML)
- HACS, then these frontend cards:
  - [button-card](https://github.com/custom-cards/button-card)
  - [card-mod](https://github.com/thomasloven/lovelace-card-mod)
  - [kiosk-mode](https://github.com/NemesisRE/kiosk-mode), if you want a header-less tablet view
- The [Nunito](https://fonts.google.com/specimen/Nunito) font, or change the font family in the theme and templates

## Copy, then edit

1. Copy `themes/example-home.yaml` into your `themes/` folder and reload themes. Select **example_home**.
2. Copy `www/img/` into `config/www/img/` so `/local/img/example-plan.png` resolves, along with the garage stills if you use that view. Replace the plan with a plan of *your* rooms when you have one. Do not drop real camera snapshots into the garage camera placeholder.
3. Copy `button_card_templates/` and `views/*.yaml`. Wire them from your Lovelace YAML the same way `ui-lovelace.yaml` does, or merge the templates into your existing dashboard.
4. If you want the example automations and scripts, copy `packages/` and include them from your configuration with `packages: !include_dir_named packages` (see `configuration.yaml`). Review each file and swap the `_example` entities before you enable it.
5. Use `configuration.yaml` only as a reference for YAML-mode Lovelace, theme include, and the packages include. Do not overwrite a live `configuration.yaml`.

A careful way to apply changes, including a backup and a human yes before anything is written to a live instance, is written in [docs/ai-assisted-workflow.md](docs/ai-assisted-workflow.md).

## Replace every example entity

Search the repo for `_example` and point each id at your own entities. The names below are fictional.

| Placeholder | Typical use |
| --- | --- |
| `light.lounge_example` | Lounge lights |
| `light.kitchen_example` | Kitchen lights |
| `light.studio_example` | Studio lights |
| `light.bedroom_example` | Bedroom lights |
| `light.bath_example` | Bath lights |
| `light.garage_example` | Garage light |
| `cover.terrace_example` | Terrace cover |
| `cover.garage_door_example` | Garage door |
| `weather.home_example` | Local weather |
| `sensor.indoor_temp_example` | Indoor temperature |
| `sensor.air_quality_example` | Air quality (or split PM sensors) |
| `alarm_control_panel.home_example` | Alarm |
| `vacuum.robot_example` | Vacuum robot |
| `input_boolean.night_mode_example` | Day / night palette toggle |
| `input_boolean.good_night_active_example` | Good-night scene helper |
| `script.turn_off_lights_example` | Turn all example lights off |
| `script.covers_up_example` / `script.covers_down_example` | Covers |
| `script.good_night_example` / `script.good_morning_example` | Evening and morning scenes |
| `sensor.lounge_temp_example` (and studio/kitchen/bedroom/bath/terrace) | Room temperatures on Rooms / Climate |
| `sensor.outdoor_temp_example` | Outdoor temperature |
| `climate.lounge_example` (and studio/kitchen/bedroom/bath) | Room climate tiles |
| `binary_sensor.front_door_example` | Front door |
| `binary_sensor.terrace_door_example` | Terrace door |
| `binary_sensor.lounge_window_example` (and kitchen/bedroom/studio) | Windows |
| `binary_sensor.lounge_motion_example` (and studio) | Motion sensors |
| `binary_sensor.back_gate_example` | Gate |
| `binary_sensor.car_present_example` | Car in the garage (example) |
| `/local/img/example-garage-camera.png` | Illustrated camera still on the Garage view (not a `camera.` entity) |
| `sensor.energy_solar_today_example` | Solar production today |
| `sensor.energy_home_today_example` | Home use today |
| `sensor.energy_grid_today_example` | Grid import |
| `sensor.energy_feedin_today_example` | Feed-in |
| `sensor.energy_month_example` / `sensor.energy_year_example` / `sensor.energy_peak_example` | Totals |
| `sensor.energy_self_ratio_example` / `sensor.energy_cost_today_example` | Share and example cost |

The clock, weather line, and “3 lights on” label in the screenshots are static **example data**. Bind them to your time, weather, and light-count sensors if you want them live. The GIFs in the README are also example data.

## What this edition does not include

- A full live house: family or people views, calendars, or a real floor plan
- Live camera feeds (the Security view uses doors, windows, motion and the alarm only; the Garage “camera” is an illustrated still)
- Integrations, add-ons, or hardware lists
- Secrets, `.storage`, backups, or databases
- A plan or 3D model of a real apartment, or a real vehicle

If a card is missing, Home Assistant will show an error on that card only. Install the three frontend cards first, then reload Lovelace. Enable packages only after you have replaced the example entities.
