# Pebble with Continuous Glucose Monitors (CGM) and diabetes monitoring

A collection of notes on CGM software and APIs.
This document / guide does NOT recommend any particular software.

## Pebble Software in the Rebble Store

  * Watchfaces https://apps.rebble.io/en_US/search/watchfaces/1?native=false&query=cgm
  * Apps https://apps.rebble.io/en_US/search/watchapps/1?query=cgm

There a mix of faces/apps.

  * Some work with Dexcom Share service - and work with regular off-the-shelf software - works with Android and iOS
    Requires an internet connection to function
  * Some work with open source data hubs, typically Android only. For example, [Nightscout xDrip+](https://github.com/NightscoutFoundation/xDrip), xDrip, etc.
    Some can be used offline (without internet access) some make use of a custom online server that requires an internet connection

For non-tech-savy users, Dexcom Share is probably the option to check out first.

## Dexcom Share

To use the Dexcom Share API, you need the credentials of the **publisher account** (not follower), and you need to have Dexcom Share enabled. To do this, you **must add a follower**, this can be yourself.

Dexcom Share notes, see (non-Pebble) resources:

  * https://www.dexcom.com/training-videos/setting-up-dexcom-share-and-follow - Setting up Dexcom Share and Follow
  * https://provider.dexcom.com/education-research/cgm-education-use/videos/setting-dexcom-share-and-follow


#### Dexcom Share - Pebble Software Graphs

  * [T1000 CGM watchface](https://apps.rebble.io/en_US/application/6972fd68ae32660009f7c242?section=watchfaces) released 2026
      * https://github.com/andrewchilds/t1000-pebble-cgm
  * https://github.com/mollyjester/peb_dx_chart - not in Rebble store
    https://github.com/mollyjester/peb_dx_chart/releases/tag/v16
  * https://github.com/woernsn/urchin-cgm not in Rebble store, also supports Nightscout server. Very configurable.

#### Dexcom Share - Pebble Software non-Graphs

  * [Rat Scout watchface](https://apps.rebble.io/en_US/application/69924ebeb8c85e00096f4920?section=watchfaces) released 2026
      * https://github.com/mollyjester/rat_scout

#### Dexcom Share - for Developers

  * https://github.com/gagebenne/pydexcom - A simple Python API to interact with Dexcom Share service
  * https://github.com/Calebh101/dexcom - Dexcom for Dart allows you to use Dexcom Share to get your Dexcom CGM data, or anybody else's, to run your application.
    Excellent documentation/overview of the Dexcom Share API and usage
  * https://github.com/makors/dexrs - Rust library for interacting with the Dexcom Share API
  * https://github.com/sedyn/rsdexcom - A Rust library for `esp32` providing an interface to the Dexcom Share service

## LibreLinkUp API

#### LibreLinkUp - Pebble Software non-Graphs

  * Fuzzy Glucose https://apps.rebble.io/en_US/application/6977b6735cd4fc00092489cb
      * https://github.com/Apfelholz/Fuzzy-Glucose

#### LibreLinkUp - for Developers

  * https://gist.github.com/khskekec/6c13ba01b10d3018d816706a32ae8ab2

## Nightscout

Nightscout version of xDrip / xDrip+

#### Nightscout - Pebble Software Graph

  * https://github.com/mortenfyhn/xDrip-Pebble-E NOTE no releases as of 2026-02-17 but apparently updated and working
    See https://github.com/NightscoutFoundation/xDrip/discussions/4167 discussion thread
  * https://github.com/woernsn/urchin-cgm not in Rebble store, also supports Dexcom Share. Very configurable.

#### Nightscout - Pebble Software non-Graphs

  * [Nightscout SuperCGM watchface](https://apps.rebble.io/en_US/application/68c5e8d5474b97000932ae2c?section=watchfaces) released 2026
      * https://github.com/sgitaize/Nightscout-supercgm

## Additional Resources

  * FitBit Glances watch face with some information about CGM APIs https://github.com/Rytiggy/Glance/wiki/How-to-configure-Glance's-settings
