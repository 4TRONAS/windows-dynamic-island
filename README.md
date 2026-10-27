# windows-dynamic-island
a dynamic island experience for users on windows 
ISLAND — a Dynamic Island for Windows
A floating, always-on-top system monitor in One PowerShell file. Zero install,
zero admin, zero dependencies — it runs on stock Windows 10 / 11
(PowerShell + WPF). Think Rainmeter's Illustro, rebuilt as a live,
bloom-open Dynamic Island.
![collapsed pill](docs/island-pill.png)
![expanded](docs/island.png)
Run it
Copy the `Island` folder anywhere (Desktop is fine).
Double-click `Island.cmd`.
A glass pill appears top-center with your clock, CPU, RAM and network.
> Windows SmartScreen may warn "unknown publisher" on first run — this is an
> unsigned hobby-grade script; choose \\\\\\\*\\\\\\\*More info → Run anyway\\\\\\\*\\\\\\\*. The script
> never touches the network and can be read in full (it \\\\\\\*is\\\\\\\* the app).
Use it
Do this	You get
hover the pill	island blooms open into the full dashboard
tap / double-click	pin it open (or dismiss)
drag anywhere	dock it wherever you like (re-dock via right-click)
click a tile	CPU → Task Manager · NET → adapters · POW → battery settings …
right-click	accents (7 palettes), opacity, always-on-top, hover-open, autostart
`Alt+I`	toggle from the keyboard, anywhere
press `Esc`	collapse
The LIVE feed turns red-amber-green with load, sparklines keep history, and
power users can push their own notifications into the island:
```bat
Island.cmd "Build 214 passed - 41s"
Island.cmd "Deploy to prod? open terminal"
npm test \\\\\\\&\\\\\\\& Island.cmd "tests green" \\\\\\\&\\\\\\\& taskkill /f /im node.exe
terraform apply; Island.cmd "infra drift checked"
```
That last trick is the demo moment: every script, pipeline or build tool on
Earth can talk to your desktop with one line.
Launch at sign-in
Right-click the island → launch at sign-in · toggle. It writes one `HKCU`
run-key entry that starts `Island-silent.vbs` (no console flash). Toggle the
same entry (or Settings → Startup) to remove it.
What's monitored
CPU % (1-min sparkline) · cores · clock · model
Memory % (with GB used/total) · sparkline
Network ↓/↑ throughput · dual sparkline
Storage C: % used · free GB · live read/write · busy %
Power: battery %, charging / AC / desktop, low-battery toast at 20 %
Uptime · resolution · GPU model · internal temperature (where the firmware
exposes it — hidden otherwise, never faked)
Hostname · OS edition + build · LAN IP
Files
File	Purpose
`Island.ps1`	the entire app (UI, animation, data engine)
`Island.cmd`	launcher + notification sender
`Island-silent.vbs`	console-less startup helper
`index.html`	pixel-preview of the widget in any browser (design showcase)
Customise
Position on every boot: `Island.cmd --anchor-x 16 --anchor-y 552`
Settings (accent, opacity, hover-open, topmost) persist to
`%TEMP%\\\\\\\\IslandPS\\\\\\\\settings.json` — delete it to factory-reset.
Colours, pill size, animation speed: the XAML block + `PW/PH/EW/EH` constants
at the top of `Island.ps1`.
