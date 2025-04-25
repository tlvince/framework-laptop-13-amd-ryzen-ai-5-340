# Framework Laptop 13 AMD Ryzen AI 5 340

Device notes and configuration under Linux for the [Framework Laptop 13 AMD Ryzen AI 300 Series](https://frame.work/gb/en/laptop13?tab=specs&slug=laptop13-diy-amd-ai300) AI 5 340 variant, DIY edition.

## Specs

- [AMD Ryzen AI 5 340](https://www.amd.com/en/products/processors/laptop/ryzen/ai-300-series/amd-ryzen-ai-5-340.html) (Krackan Point, Zen 5)
- [SK hynix Platinum P41](https://ssd.skhynix.com/platinum_p41/) 1TB SSD
- [Crucial CT2K16G56C46S5](https://uk.crucial.com/memory/DDR5/CT2K16G56C46S5) 32GB DDR5-5600 SODIMM
- [BOE NE135A1M-NY1 v18.0 (matte)](https://www.panelook.com/NE135A1M-NY1_BOE_13.5_LCM_overview_66744.html) 13.5", 3:2, 2880x1920 256 ppi, 500 nits, eDP1.4, [40 pins](https://github.com/FrameworkComputer/Framework-Laptop-13/tree/57357b797447b55ec7afcaf31b2fe731e7a48144/Display#pinout), [DC-mode dimming](https://github.com/FrameworkComputer/Framework-Laptop-13/tree/57357b797447b55ec7afcaf31b2fe731e7a48144/Mainboard#display-interface) (not PWM)
- 61Wh battery
- RZ717/MT7925 WiFi adapter
- 4x [USB-C Expansion Cards](https://frame.work/gb/en/products/usb-c-expansion-card)
- [Capella CM3218](https://github.com/FrameworkComputer/Framework-Laptop-13/blob/b3872f334810103c758e39a33572b42a5e4d67e0/Webcam/README.md#pinout) ambient light sensor

## Sleep

Slept for 7.68 hours. Used 4.10Wh, an average rate of 0.53W (via [batterylog](https://github.com/lhl/batterylog))

## Battery

Test environment

- 6.14.0 #1-NixOS
- GNOME 47
  - `gnome-shell --no-x11` (XWayland disabled)
  - `gdm3`
  - `gnome-settings-daemon`
  - variable refresh rate
- 40% brightness
- WiFi connected
- Bluetooth disabled
- webcam and microphone disabled (via hardware switches)
- keyboard backlight disabled
- power button LED lowest brightness
- ambient light sensor disabled (`hid_sensor_hub`)
- 4x USB-C expansion cards

```sh
powerstat -d 0 -c -H 1 480
```

### Idle benchmarks

One `foot` terminal running `powerstat`

#### 2025-04-24

| State                                                                                                | C3%    | Power (W) |
| ---------------------------------------------------------------------------------------------------- | ------ | --------- |
| [idle 60Hz (ppd balanced)](./data/nixos-linux-6.14.0-gnome-47-ppd-0.30-vrr-60hz-balanced-idle.txt)   | 99.47% | 4.08      |
| [idle 120Hz (ppd balanced)](./data/nixos-linux-6.14.0-gnome-47-ppd-0.30-vrr-120hz-balanced-idle.txt) | 99.68% | 4.00      |

### Video benchmarks

- One `foot` terminal running `powerstat`
- mpv/Firefox (in Wayland mode with hardware-video acceleration) playing 1080p AV1 video
- both windows evenly split (vertically)
- other baseline settings [as above](#battery)

#### 2025-04-24

| State                                                                                                              | C3%    | Power (W) |
| ------------------------------------------------------------------------------------------------------------------ | ------ | --------- |
| [mpv 60Hz (ppd balanced)](./data/nixos-linux-6.14.0-gnome-47-ppd-0.30-vrr-60hz-balanced-mpv-av1-1080p.txt)         | 93.98% | 5.70      |
| [Firefox 60Hz (ppd balanced)](./data/nixos-linux-6.14.0-gnome-47-ppd-0.30-vrr-60hz-balanced-firefox-av1-1080p.txt) | 79.43% | 7.17      |

### Browsing benchmarks

- One `foot` terminal running `powerstat`
- Firefox, light websites (no videos)
- both windows evenly split (vertically)
- other baseline settings [as above](#battery)

#### 2025-04-24

| State                                                                                                      | C3%    | Power (W) |
| ---------------------------------------------------------------------------------------------------------- | ------ | --------- |
| [Firefox 60Hz (ppd balanced)](./data/nixos-linux-6.14.0-gnome-47-ppd-0.30-vrr-60hz-balanced-firefox.txt)   | 89.35% | 6.75      |
| [Firefox 120Hz (ppd balanced)](./data/nixos-linux-6.14.0-gnome-47-ppd-0.30-vrr-120hz-balanced-firefox.txt) | 83.55% | 7.38      |

## Links

- [tlvince/nixos-config](https://github.com/tlvince/nixos-config)
- [tlvince/framework-laptop-13-amd-7640u](https://github.com/tlvince/framework-laptop-13-amd-7640u)
