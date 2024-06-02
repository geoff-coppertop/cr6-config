# CR6 klipper settings and macros

This repo provides the settings and macros needed to run a CR-6 SE with a BTT SKR CR6 board using a dual extruder.

## Important features

* Printer definition
* Macros to run the probe

## How to install

The instructions assume that you have a up to data and working moonraker installation. If not start with updating your moonraker first. There are two methods that can be used to install these configs as listed below.

### Add updater section

Open your moonraker.conf and add

```ini
[update_manager cr6-config]
type: git_repo
channel: dev
primary_branch: master
path: ~/cr6-config
origin: https://github.com/geoff-coppertop/cr6-config.git
managed_services: klipper
```

below the mainsail updater section.

### Manual clone

SSH into your PI and run the following,

```bash
cd ~
git clone https://github.com/geoff-coppertop/cr6-config.git
ln -sf ~/cr6-config/cr66.cfg ~/printer_data/config/cr6.cfg
```

Then link the prepared moonraker update file,

```bash
ln -sf ~/cr6-config/cr6-moonraker-update.conf ~/printer_data/config/cr6-moonraker-update.conf
```

Then open your moonraker.conf and add

```ini
[include cr6-moonraker-update.conf]
```

below the mainsail updater section.

### How to setup

The setup process is completed by simply adding the following,

```ini
[include cr6.cfg]
```

to your printer.cfg file. Be aware the file will show up as read only. This was intended by use.
