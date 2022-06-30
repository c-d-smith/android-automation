# Volume Control for Work

  * Version: 2.0.0
  * Release Date: 30 Jun 2022

## Get the Project Code
  * [From Google Drive](https://drive.google.com/drive/folders/14aBR7ZexeqVCrS5SLCO61wpb5Kb8eGBp?usp=sharing)
  * [From Github](https://github.com/c-d-smith/android-automation/blob/main/projects/volume-control/Volume_Control.prj.xml)

## Overview

This project will lower the various volume settings on your phone at a set time, and raise them again at a later time. This has been useful for me during work hours.

Alternatively, for third shifters, you can set the project to raise the volumes in the morning and lower them in the evening. This project should work perfectly well just by setting the times correctly. If it does not:
  1. Please let me know.
  2. Until I get it fixed, set the `%...VolumeLow` variables to the higher values, and the `%...VolumeHigh` variables to the lower values.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)

### Permissions

Coming soon.

## Project Setup

This project has an installer that is controlled by profile. The profile triggers any time that it is enabled *and* the variable `%SetupVolumeControl` is set to any value other than `false`. The installer will walk you through setting the start and end times, the high and low volume values for each volume setting, and the calendar|s to use.

*This project assumes you are using Google Calendar. If you are not, you will need to set the calendar variables manually.*

### Project Setup

#### Variables

  * `%AlarmVolumeHigh`
  * `%AlarmVolumeLow`
  * `%EndWorkVol`
  * `%HolidayCalendar`
  * `%MediaVolumeHigh`
  * `%MediaVolumeLow`
  * `%NotificationVolumeHigh`
  * `%NotificationVolumeLow`
  * `%RingerVolumeHigh`
  * `%RingerVolumeLow`
  * `%SetupVolumeControl`
  * `%StartWorkVol`
  * `%SystemVolumeHigh`
  * `%SystemVolumeLow`
  * `%WorkCalendar`

#### `%AlarmVolumeHigh`

  * Default Value: Current Alarm volume setting
  * Possible Values: `0` to `25`

#### `%AlarmVolumeLow`

  * Default Value: Current Alarm volume setting
  * Possible Values: `0` to `25`

#### `%EndWorkVol`

  * Default Value: `16:30`
  * Possible Values: `00:00` to `23:59`

#### `%HolidayCalendar`

  * Default Value: no default
  * Possible Values: varies; string

This is the calendar that contains events that indicate when your employer is closed. This project expects that these are the only events on this calendar. If you don't have a clean calendar that contains only these events, then I recommend using only the `Volume Control: Without Holiday Calendar` profile.

In fact, the only reason I make use of this variable is because people tend to be lazy and will allow repeating meetings to be scheduled on holidays, without removing those events that land on holidays. You could obviate the need for this variable by creating `Out of office` events on your `%WorkCalendar` to stand in for holidays. Since I am also obviously lazy and my employer provides a holiday calendar, I use it.

#### `%MediaVolumeHigh`

  * Default Value: Current Media volume setting
  * Possible Values: `0` to `25`

#### `%MediaVolumeLow`

  * Default Value: Current Media volume setting
  * Possible Values: `0` to `25`

#### `%NotificationVolumeHigh`

  * Default Value: Current Notification volume setting
  * Possible Values: `0` to `25`

#### `%NotificationVolumeLow`

  * Default Value: Current Notification volume setting
  * Possible Values: `0` to `25`

#### `%RingerVolumeHigh

  * Default Value: Current Ringer volume setting
  * Possible Values: `0` to `25`

#### `%RingerVolumeLow`

  * Default Value: Current Ringer volume setting
  * Possible Values: `0` to `25`

#### `%SetupVolumeControl`

  * Default Value: unset
  * Possible Values: `false`, anything else

This controls whether the setup profile will trigger. When this variable is set to `false`, setup will not run. Therefore, by setting this to anything other than `false`, including simply erasing its value, and turning on the setup profile, setup can be run again at any time.

#### `%StartWorkVol`

  * Default Value: `7:00`
  * Possible Values: `00:00` to `23:59`

#### `%SystemVolumeHigh`

  * Default Value: Current System volume setting
  * Possible Values: `0` to `25`

#### `%SystemVolumeLow`

  * Default Value: Current System volume setting
  * Possible Values: `0` to `25`

#### `%WorkCalendar`

  * Default Value: no default
  * Possible Values: varies; string

This is the calendar that contains meeting events, which are really any event where you are marked as `busy`, and your `Out of office` events.
