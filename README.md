# not-yet-definitive-pebble-guide

not yet definitive pebble smart watch guide

  * [Resources](#resources)
    + [Documentation](#documentation)
    + [Communities](#communities)
    + [Archives](#archives)
  * [Android Apps](#android-apps)
  * [Building](#building)
    + [Local](#local)
    + [Under CI / GitHub Actions](#under-ci---github-actions)
    + [CloudPebble](#cloudpebble)
    + [Frameworks](#frameworks)
      - [Libraries](#libraries)
      - [On Pebble/Phone](#on-pebble-phone)
      - [Services/APIs](#services-apis)
      - [Desktop/command line tools](#desktop-command-line-tools)
        * [Third Party Tools](#third-party-tools)
    + [Hacking tools](#hacking-tools)
  * [Dev notes](#dev-notes)
    + [Tips](#tips)
      - [Pebble Debug Logs](#pebble-debug-logs)
      - [Hung Pebble emulator](#hung-pebble-emulator)
    + [SDK notes](#sdk-notes)
      - [SDK Presentations](#sdk-presentations)
      - [Migration and porting notes](#migration-and-porting-notes)
    + [Learning C with Pebble](#learning-c-with-pebble)
  * [Rebble Services Notes](#rebble-services-notes)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>


## Resources

  * https://rebble.io/
  * https://github.com/pebble-dev/wiki/wiki

### Documentation

[Notes on PebbleOS on device settings](./settings.md)

### Communities

  * Discord
  * Reddit (users and dev)
  * https://forum.rebble.io/

### Archives

  * https://github.com/clach04/PebbleArchive
  * https://github.com/clach04/Pebble-App-Config-Page-Backup

## Android Apps

 1. Original Pebble app, and Rebble modified/tweaked one
 2. [microPebble](https://github.com/matejdro/microPebble)
 3. [CoreDevices mobileapp](https://github.com/coredevices/mobileapp) https://play.google.com/store/apps/details?id=coredevices.coreapp
 4. [gadgetbridge](https://gadgetbridge.org/internals/specifics/pebble/) - NOTE there is supposed to be a fork that has network access for config

Cobble currently not suitable

## Building

### Local

  * Docker and the Pebble emulator https://github.com/clach04/docker-pebble-dev/wiki
  * Pebble Development Setup https://github.com/andyburris/pebble-setup
  * Rebble Help SDK FAQ https://help.rebble.io/sdk/

### Under CI / GitHub Actions

So far only GitHub Actions available

  * see https://github.com/kristofwillen/Pebble-NMBS for docker based build under GitHub actions
  * https://github.com/clach04/github_action_pebble_build - Pebble GitHub Actions for building
      * See a demo at https://github.com/clach04/pebble_watchface_framework

### CloudPebble

Requires the most work and not recommended:

  * Self hosted (with limitations) https://github.com/gfunkmonk/cloudpebble-composed WARNING not considered safe to expose publicly (from original author in Discord https://discord.com/channels/221364737269694464/407270816997441547/1014688058685259817)

### Frameworks

TODO URLs needed

#### Libraries

  * https://github.com/LeFauve/pebble_memory_tools


#### On Pebble/Phone

  * plain C with Pebble SDK
  * C + js with Pebble SDK and PebbleKitjs
  * Javascript:
      * Rocky.js
      * Pebble.js
      * Simply.js
  * Companion SDK
  * Python on Pebble https://github.com/hiway/pybble
  * UI mocking / preview
      * https://github.com/gregoiresage/pebble-image-viewer https://apps.rebble.io/en_US/application/53bdb1291c6da72083000044?query=Image&section=watchapps
      * Preview App by Tack Mobile https://apps.rebble.io/en_US/application/56240ecbbdf1bfb3cb00009e?query=Image&section=watchapps

#### Services/APIs

  * https://github.com/clach04/pypebbleapi - Python client library for Timeline (specifically Rebble Timeline service)

#### Desktop/command line tools

Note that there are improvements and fixes for existing tools; you may have to find them. For example, see unmerged PRs:


  * https://github.com/pebble-dev/pebble-tool/pulls - for example, allow logging to be ran from Windows
  * https://github.com/pebble/clay/pulls - working pebble clay config in the emulator on a modern desktop browser
  * See https://github.com/pebble-dev/clay/branches in 2025-12 there was some new activity along with releases https://www.npmjs.com/package/@rebble/clay

##### Third Party Tools

  * https://github.com/clach04/python-pebble-tools process locker
  * https://github.com/clach04/pebble_patch_tts voice dictation patching to remove punctuation, relies on rockgarden
  * https://github.com/clach04/Pebble-App-Config-Page-Backup backup of (most) pebble config URLs
  * reverse engineering:
      * radare2/r2 - https://github.com/radareorg/radare2/issues/20002 https://www.reddit.com/r/pebbledevelopers/comments/uc50kw/reverse_engineeringdecompiling_with_radare2r2/
      * extracting assets
          * PBW files are simply ZIP files, js is easily extractable and can be updated and injected back into the PBW without any other steps (i.e. no checksum, metadata/manifest updates, etc.

### Hacking tools

  * https://github.com/pebble-dev/legacy-firmware-patcher/tree/rbl1-rc2
  * https://github.com/southwolf/pbw-tools
  * https://github.com/clach04/rockgarden patch and hack watchfaces and apps - working fork of https://github.com/cpfair/rockgarden
      * For example, with use with https://github.com/clach04/pebble_patch_tts
  * https://github.com/cpfair/sand - Remix Pebble apps
  * https://github.com/sethasaurus/pebble-pyrite
  * [7z](https://www.7-zip.org/) and a [text](https://scintilla.org/SciTE.html) [editor](https://www.vim.org/)
      * Most config/internet access can be modified/fixed/hacked via:
         1. Extract the javascript from PBW using any zip extractor
         2. edit javascript
         3. rezip up the PBW
      * A typical use case is to change the settings page or modify [weather lookup](https://github.com/clach04/pebble-forecaswatch2-fcsw2-fcw2/blob/6ae4f1f7cde3a32144d20821fb1a425b89122864/src/pkjs/weather/openweathermap.js#L26).

## Dev notes

### Tips

#### Pebble Debug Logs

Once Developer mode is enabled in the Pebble App on the phone:

    pebble logs --phone IP_ADDRESS

Will display all logs, from C code and js code.

This works under Windows, not just Unix-like platforms:

    python2 -m pip install -e git+https://github.com/clach04/pebble-tool.git@windows_py27#egg=pebble-tool

#### Hung Pebble emulator

If Pebble emulator is hung

1. Issue `pebble kill`
2. Manually stop/kill any remaining pebble (emulator) processes
3. Issue `pebble wipe`

### SDK notes

  * latest 4.x
  * SDK 3.x - can be used to build PBWs that run on Firmware 4.x
  * SDK 2 - has incompatablities with SDK1
  * SDK 1 - do NOT use

#### SDK Presentations

  * https://m.youtube.com/watch?v=8tOhdUXcSkw&pp=0gcJCdgAo7VqN5tD covers memory
      * https://www.slideshare.net/slideshow/pebble-dev-retreat2014size/40376128

#### Migration and porting notes

  * https://developer.rebble.io/developer.pebble.com/guides/migration/migration-guide-3
      * https://remysharp.com/2015/07/29/notes-on-porting-my-pebble-app-to-sdk-3
      * https://developer.rebble.io/developer.pebble.com/guides/migration/migration-guide-3/index.html#using-the-status-bar (statusbar missing battery after sdk2)
      * Also see https://github.com/rebootsramblings/custom-status-bar-for-pebble

### Learning C with Pebble

  * https://pebble.gitbooks.io/learning-c-with-pebble/content/
      * https://github.com/clach04/PebbleArchive/blob/mine/learning-c-with-pebble%20final.pdf
  * Solutions https://github.com/learning-c-with-pebble

## Rebble Services Notes

  * https://github.com/pebble-dev/rebble-boot/blob/master/boot/stage2.py#L182 - weather bootstrap URL
  * Rebble App Store
      * https://apps.rebble.io/en_US/watchapps
      * https://apps.rebble.io/en_US/watchfaces
      * Sample dev link for app, allows PBW download from web browser https://apps.rebble.io/en_US/application/55123f98e28a6598dd00008e?dev_settings=tru&section=watchapps

