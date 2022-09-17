# not-yet-definitive-pebble-guide

not yet definitive pebble smart watch guide


## Resources

  * https://rebble.io/
  * https://github.com/pebble-dev/wiki/wiki

## Building

  * Docker and the Pebble emulator https://github.com/clach04/docker-pebble-dev/wiki
  * Pebble Development Setup https://github.com/andyburris/pebble-setup

### Frameworks

TODO URLs needed

#### On Pebble/Phone

  * plain C with Pebble SDK
  * C + js with Pebble SDK and PebbleKitjs
  * Javascript:
      * Rocky.js
      * Pebble.js
      * Simply.js
  * Companion SDK
  * Python on Pebble https://github.com/hiway/pybble

#### Services/APIs

  * https://github.com/clach04/pypebbleapi - Python client library for Timeline (specifically Rebble Timeline service)

#### Desktop/command line tools

  * https://github.com/clach04/python-pebble-tools process locker
  * https://github.com/clach04/github_action_pebble_build - Pebble GitHub Actions for building
  * https://github.com/clach04/pebble_patch_tts voice dictation patching to remove punctuation
  * https://github.com/clach04/Pebble-App-Config-Page-Backup backup of (most) pebble config URLs
  * reverse enginering:
      * radare2/r2 - https://github.com/radareorg/radare2/issues/20002 https://www.reddit.com/r/pebbledevelopers/comments/uc50kw/reverse_engineeringdecompiling_with_radare2r2/
      * extracting assets
          * PBW files are simply ZIP files, js is easily extractable and can be updated and injected back into the PBW without any other steps (i.e. no checksum, metadata/manifest updates, etc.
  

### SDK notes

  * latest 4.x
  * SDK 3.x - can be used to build PBWs that run on Firmware 4.x
  * SDK 2 - has incompatablities with SDK1
  * SDK 1 - do NOT use

#### Migration and porting notes

  * https://developer.rebble.io/developer.pebble.com/guides/migration/migration-guide-3
      * https://remysharp.com/2015/07/29/notes-on-porting-my-pebble-app-to-sdk-3
      * https://developer.rebble.io/developer.pebble.com/guides/migration/migration-guide-3/index.html#using-the-status-bar (statusbar missing battery after sdk2)
      * Also see https://github.com/rebootsramblings/custom-status-bar-for-pebble
