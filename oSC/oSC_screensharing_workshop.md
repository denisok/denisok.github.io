# Wayland screen sharing status (DEs, apps, flatpak)

Lets test and hack Wayland screen sharing on different apps (Zoom, Teams ...), different DEs (sway, GNOME, KDE),different installation methods (rpms, flatpak).

Come with your laptop with DE you have and lets test how it works for you.

The MVP for the session is to have wiki page where to document correct ways to do it, issues and maybe workarounds. If we can hack any solution for the issues identified or create some sig to hack it in a future - will be awesome.

## How we would have fun?

* Ask around about distros, DEs and etc. What screensharing app are used.
* Ask ppl to open rooms, joing their meetings/apps and try sharing.
* Get results in some way documented (tables, text and etc).
* Document some interesting links, info, use cases, ways to debug and etc.

## Environments

Distros:
| name     | version    |
| -------- | ---------- |
| openSUSE | Leap 15.3  |
| openSUSE | Leap 15.4  |
| openSUSE | Tumbleweed |
| openSUSE | MicroOS    |
|          |            |

DEs:
* sway
* GNOME
* KDE

## meeting/recording software
Apps:
* Zoom
* Jitsi: https://meet.opensuse.org/
* Google Meet https://meet.google.com/
* MSTeams
* OBS
* 

Instalation method:
* rpm
* flatpak

## Test

ability to share:
* full screen
* Xwayland application
* wayland application

## Troubelshooting guides

### sway
`swaymsg -t get_tree` shows window details (shell)
`env XDG_UTILS_DEBUG_LEVEL=10  xdg-mime query default x-scheme-handler/zoommtg`
`dbus-monitor` `d-feet`

## Results

shells:
* xwayland
* xdg-shell

cap modes f/a/t/v:
* full screen: f
* app window: a
* browser tab: t
* obs v4l2 (sharing through camera): v

present mode:
* pipewire
* 

## openSUSE MicroOS on Sway DE

| app      | flatpak  | rpm   |   shell   |  cap mode | present mode |  notes |
| -------- | -------- | ----- | --------- | --------- | ------------ | ------ |
| Zoom     |   yes    |   -   |   -       | -/-/-/v   |              | [x][x] |
| Jitsi    | yes/Chrm |   -   | xwayland  | f/-/t/v   |              | [3][3] |
| Jitsi    | yes/Frfx |   -   | xdg-shell | f/-/-/v   |              | [2][2] |
| Meet     | yes/Chrm |   -   | xwayland  | f/-/t/v   |              | [1][1] |
| Meet     | yes/Frfx |   -   | xdg-shell | f/-/-/v   |              | [2][2] |

with camera sharing in OBS, Meet has a very bad picture transfered (in chrome and firefox), it probably .

[1]: very bad quality in v mode, dialog for app shows screen
[2]: very bad quality in v mode
[3]: good quality in v mode, but it is cut on reciever side

Zoom doesn't really work well on MicroOS. It doesn't work with xdg there: couldn't login, links aren't open with xdg-open.

## openSUSE Tumbleweed on Sway DE

| app      | flatpak  | rpm   |   shell   |  cap mode | present mode |  notes |
| -------- | -------- | ----- | --------- | --------- | ------------ | ------ |
| Zoom     |   yes    |       |           |  / / /    |              | [x][x] |
| Jitsi    |   Chrm   |       |           |  / / /    |              | [x][x] |
| Jitsi    |          | Frfx  |           |  / / /    |              | [x][x] |
| Meet     |   Chrm   |       |           |  / / /    |              | [x][x] |
| Meet     |          | Frfx  |           |  / / /    |              | [x][x] |

## Notes


