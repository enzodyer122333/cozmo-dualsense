# cozmo-dualsense

Drive an Anki/Digital Dream Labs **Cozmo** robot with a **PS5 DualSense controller** on macOS, using [PyCozmo](https://github.com/zayfod/pycozmo). No phone or Cozmo app needed.

> **Unofficial fan project.** Not affiliated with or endorsed by Digital Dream Labs, Anki, or Sony. Cozmo is a trademark of Digital Dream Labs. DualSense and PS5 are trademarks of Sony Interactive Entertainment.

## Features

- Arcade-style driving with the left stick
- Head tilt on the right stick
- Lift up/down on the shoulder buttons
- One-button reset of head and lift
- `--debug` mode to find the right button and axis numbers for your setup

## Controls

| Input | Action |
|---|---|
| Left stick | Drive (up/down = forward/back, left/right = turn) |
| Right stick up/down | Tilt head |
| R1 / L1 | Raise / lower lift |
| Cross (X) | Reset head and lift to neutral |
| Options | Quit |

## Requirements

- A Cozmo robot
- A DualSense controller paired over Bluetooth
- Python 3.7 or newer
- [`pycozmo`](https://pypi.org/project/pycozmo/) and [`pygame`](https://pypi.org/project/pygame/)

Tested on: MacBook Neo, macOS 26.6

## Setup

```bash
git clone https://github.com/enzodyer122333/cozmo-dualsense.git
cd cozmo-dualsense
python3 -m venv env
source env/bin/activate
pip install pycozmo pygame
```

## Usage

1. Pair the DualSense in **System Settings → Bluetooth** (hold **PS + Create** until the light bar flashes, then connect).
2. Turn Cozmo on and join his Wi-Fi network from the Mac's Wi-Fi menu. His network name is shown on his face when you move his lift up and down.
3. Run:

   ```bash
   source env/bin/activate   # if not already active
   python3 cozmo_dualsense.py
   ```

4. Press **Options** (or Ctrl+C) to quit.

Next time you only need steps 1–3. There's no need to reinstall.

## Troubleshooting

**"No controller found."** Make sure the DualSense is connected in Bluetooth settings before you start the script.

**Sticks or buttons do the wrong thing.** Button and axis numbering can differ between SDL versions. Run:

```bash
python3 cozmo_dualsense.py --debug
```

It prints the raw numbers as you press things. Then edit the mapping constants at the top of `cozmo_dualsense.py`.

**No internet while driving.** Cozmo creates his own Wi-Fi network, so your Mac is offline while connected to it. A USB-C network adapter or a phone hotspot over USB can keep you online.

**Connection drops or Cozmo stops responding.** PyCozmo is still under development and can be unstable. Power-cycle Cozmo, rejoin his Wi-Fi, and run the script again.

## Tuning

At the top of `cozmo_dualsense.py` you can change:

- `MAX_WHEEL_SPEED`: top driving speed in mm/s (Cozmo's hard limit is 200)
- `DEADZONE`: how far a stick must move before it registers
- `HEAD_RATE` and `LIFT_RATE`: how fast the head and lift move

## Credits

- [PyCozmo](https://github.com/zayfod/pycozmo) by zayfod, which does all the talking to the robot
- [pygame](https://www.pygame.org/) for reading the controller

## License

[MIT](LICENSE)
