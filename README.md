# Rom-Builder
Build android roms in docker with Ubuntu 20.04 via ci environments (by [Sohil876](https://github.com/Sohil876))
Forked from [Bauh-Yeoj](https://github.com/Bauh-Yeoj/aosp-building)
Thanks to [Cirrus CI](https://cirrus-ci.com/) for their awesome service!

**Humble request to all not to abuse this system. Happy building!!!**

## Steps:
( Read the Cirrus CI [docs](https://cirrus-ci.org/guide/quick-start/) for guide on setting up ci and anything cirrusci related, definetly read their quickstart and writing tasks documentation before proceeding! Only `rom-builder` related things are documented here. )

1. Fork this repo
2. There are two main config files, `.cirrus.yml` and `rb.conf` files.
3. Also do **NOT** comment out or remove the info_dump script in `.cirrus.yml` file, it performs some important tasks!.
4. Add your telegram bot token in in cirrus ci as described in Cirrus Ci docs (Writing tasks), then change the value of `BOT_TOKEN` in `.cirrus.yml` file to the generated variable.
5. `RCLONE_CONFIG_FILE` in  `.cirrus.yml` should be the contents of `~/.config/rclone/rclone.conf` file, encrypted in ci like you did for `BOT_TOKEN` , this is used for upload/download of everything by default so is mandatory, else comment out ccache scripts and use cirrusci upload for zip file upload. If you need help in creating config file for rclone see [rclone website](https://rclone.org) (also make aure your app is published and not in testing in gdrive api settings else gdrive wont allow the app acess)
6. Change settings in `rb.conf` file according to your rom/device/needs, you can configure almost everything relevant to rom-builder from there.
7. You can enable upload of zip files straight to cirrus instead of using rclone by uncommenting `build_zip_artifacts` block in `.cirrus.yml` file, max file size for free users is 1GB per task.
8.  After setting everything up properly, push any commit to repo and build will be triggered, you can re run builds and cancel them with cirrus ci website
