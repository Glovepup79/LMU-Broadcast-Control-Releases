> **Latest:** v0.1.4 • See releases for changelog

# LMU Broadcast Control

LMU Broadcast Control is a WPF application designed for managing live timing, overlays, and broadcast controls in Le Mans Ultimate. It provides race directors and broadcasters with information on the session and quick-access tools for controlling what viewers see.

## Auto-Update

- On startup, the app checks GitHub for new releases.
- If an update is available, a banner appears on the Home screen.
- Click the banner to view release notes, download, and install — with SHA256 checksum verification.
- Installation is blocked if Le Mans Ultimate is running.

## Requirements

- Windows 10 or later.
- [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/en-us/download/dotnet/8.0/runtime) (the installer will prompt you if it's missing).
- Le Mans Ultimate installed and running locally.

## Timing Grid

- Position – driver current overall position (positional change highlighted).
- Class - driver current position in class.
- Driver Name – active driver's name.
- Team Name – the racing team associated with the driver.
- Class – car's category (e.g., Hypercar, LMP2, GT3).
- PEN/DQ – shows penalties or disqualifications (DT = Drive-Through, SG = Stop-Go, TIME = time penalty).
- Car – Car manufacturer badge.
- Best Lap – driver's fastest lap time.
- Last Lap – most recent lap time.
- S1 – sector 1 time.
- S2 – sector 2 time.
- S3 – sector 3 time.
- PB – highlights a driver's personal best sector (green). Personal best lap highlighted in Best and Last columns.
- SB – highlights the overall session best sector (purple). Class best lap highlighted in Best column.
- Sectors slower than personal best are highlighted in orange.
- Yellow flag highlighting – class bar flashes yellow when a car is slow on track, with linger and formation lap suppression.
- Energy – virtual energy or fuel remaining as a colored progress bar.
    - VE classes show virtual energy from the strategy endpoint.
    - Non-VE classes (LMP2, etc.) show fuel from standings.
    - Color-coded: green (75%+), light green (50–75%), yellow (25–50%), orange (10–25%), red (<10%).
- GAP – time difference to the overall leader.
    - In practice/qualifying: shows the gap to the fastest lap.
    - In a race session: shows the live time gap to the race leader.
- INT – time difference to the car ahead.
    - In practice/qualifying: shows the gap on fastest lap times.
    - In a race session: shows the live interval to the car directly in front.
    - Close driver highlighting:
        - Door-to-Door: ≤ 0.30s gap (red wash highlight)
        - Critical: ≤ 0.50s gap (amber wash highlight)
    - Trend arrows updated each lap: ▲ Closing, ▼ Opening, ▬ Stable.
- Status – driver state: Exiting Pits, In Pits, Pit Lane, Garage, Out Lap, FIN, DNF, DQ.

## Overlay Controls

- Hide in game panels (middle mouse button in LMU).
- Refresh Overlay.
- Session Info – show or hide the session information overlay.
- Full Course Yellow – toggle the Code80 flag.
- Safety Car – toggle the Safety Car flag.
- Tower (Standings Tower) – show or hide the live standings tower.
    - Switch between classes, driver & team names, and data fields (gap, interval, stops, positions, energy, tyres).
- Driver Information.
- Qualifying Information.
- On-board driver box and HUD.
- Set starting order and display starting grid.

## Camera Controls

- Clickable driver row to change focus (single click).
- Camera family buttons: Nose, Bonnet, Trackside, TV, and Onboard.
    - With an incident selected, clicking a camera button focuses on that driver and switches camera.
    - Without a selection, switches camera family only.

## Broadcast Control

- Session tabs (Practice / Qualifying / Race) with auto-switching on session change.
- Incident type filters: toggle Yellow Flags, Contacts, and Overtakes independently.
- Overtake detection during race sessions (with pit stop and yellow flag filtering, 10-second cooldown per car pair).
- Incident type row highlighting (yellow for Yellow Flag, red for Contact, blue for Overtake).
- Unviewed incident indicator (blue left border, clears on click).
- Slow car detection with automatic replay switching.
- Contact detection between cars.
- Manufacturer logos and driver/vehicle info for incidents.
- CSV export for slow car and contact incidents.
- Replay pre-roll and auto-return to live.

## Beta Overlay

- Standalone overlay served via embedded HTTP server — independent of in-game overlays.
- Open from the Home screen; copy the URL into an OBS Browser Source.
- Standings tower with class colours, PIT/OUT/PEN/DQ badges, gap and interval columns.
- Adaptive tower width based on name lengths with stability.
- Driver info banner for the focused driver.
- Qualifying info panel with live lap timer, position, and real-time sector colour indicators (green = personal best, purple = class best, orange = slower).
- Session results page — WEC-style classification table with pagination and class filtering.
- Mid-race results — live classification table during race sessions.
- Championship standings — load championship data from CSV, displayed as a WEC-style table with position, class bar, manufacturer logo, car number, driver, vehicle, and points. Supports multiple classes per CSV with per-class filtering.
- 1-second fade transitions for all overlay elements.
- Staggered slide-in animation for results rows.
- Track map overlay with class-coloured car dots and focused car highlighting.
- Starting grid carousel: WEC-style overlay with configurable auto-cycle interval.
- Tower field selector: Interval, Gap, Stops, Pos +/-, Energy with auto-cycle support, configurable interval, and per-field rotation checkboxes. Settings persist per PC.
- Toggle between driver name and team name.
- Penalty badges show specific type (DT, SG, TIME).

## Connect to a Remote PC

- Ensure the following ports are open on the remote PC:
    - 6397 (REST API)
    - 6398 (WebSocket)
- From the Home screen, enter the IP address and port for each PC (supports up to two PCs).
- Click the connection status indicator to connect, then open any feature window from that PC's panel.
