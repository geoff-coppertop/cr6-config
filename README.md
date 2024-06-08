# CR6 klipper settings and macros

This repo provides the settings and macros needed to run a CR-6 SE that uses an SKR pico for the mainboard and an CAN connected ebb36 for the toolhead.

## Important features

* Printer definition

## How to install

The instructions assume that you have a up to data and working moonraker installation. If not start with updating your moonraker first. There are two methods that can be used to install these configs as listed below.

### Add updater section

Open your moonraker.conf and add

```ini
[update_manager cr6-config]
type: git_repo
channel: dev
primary_branch: main
path: ~/printer_data/config/cr6-config
origin: https://github.com/geoff-coppertop/cr6-config.git
managed_services: klipper
```

below the mainsail updater section.

### Manual clone

SSH into your PI and run the following,

```bash
cd ~/printer_data/config/
git clone https://github.com/geoff-coppertop/cr6-config.git
```

Then open your moonraker.conf and add

```ini
[include ~/printer_data/config/cr6-config/moonraker.conf]
```

below the mainsail updater section.

### How to setup

The setup process is completed by simply adding the following,

```ini
[include cr6.cfg]
```

to your printer.cfg file. Be aware the file will show up as read only. This was intended by use.
