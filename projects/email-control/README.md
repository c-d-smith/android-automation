# Email Control

  * Version: 2.0.1
  * Release Date: 4 Jun 2022

## Get the Project Code

  * [From Google Drive](https://drive.google.com/drive/folders/1DNNhbqcVKCN2WuldYhv27PoN5DeELkTm?usp=sharing)
  * [From Github](Email_Control.prj.xml)

## Overview

This project enables new email notifications for a single account during select hours and on days where you are not marked "Out of office" on your calendar. Otherwise, email notifications for the selected account are suppressed, but email still syncs.

It has two profiles: one that will also check a calendar for holiday events (indicating your employer is closed), and one that does not. The installer will enable the correct profile based on your input.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)
  * [AutoCalendar](https://play.google.com/store/apps/details?id=com.joaomgcd.autocalendar)
  * [AutoApps](https://play.google.com/store/search?q=autoapps&c=apps)

In order to use this project, you will need to purchase Tasker (about $4 USD). If you want to use the installer, you will also need to purchase a subscription to AutoApps. Currently, the subscription is $1.35 USD per month or $14.29 USD per year. If you're going to use Tasker more extensively, the subscription is worth it because it unlocks all the Tasker plugins.

### Tasker Setup and Permissions

Coming soon.

### AutoCalendar Setup and Permissions

AutoCalendar is currently only capable of being connected to a single account that syncs on your phone. This selection is made when you launch AutoCalendar and can only be changed by uninstalling and reinstalling AutoCalendar. While the plugin is currently in an "alpha" state, it does work correctly. I hope that, whenever João is able to put more effort into it, that he'll make it capable of querying more than one sync'd account's calendars.

The only permission this app requires otherwise is access to your calendars.

## Project Setup

The installer will walk you through setting the hours during which you will receive notifications and selecting your calendar|s. It expects that you're using Google calendars. If you are not, then you will only be able to set the hours using the installer. Note that the installer will default to enabling the profile that uses a holiday calendar. If you do not have a holiday calendar, you will need to disable that profile and enable the other one.

To select the calendar|s, you will need to tap the PROFILES tab, then tap the profile you want to use to expand it. Once expanded, you can tap each of the contexts to edit them, one at a time. Find the variable and back it out, including the `%` sign. Once the input field is cleared, tap the magnifying glass to the right and just above the input field. This will display a list of calendars your phone syncs and you can select the correct calendar from that list. Finally, turn the profile on, and save.

**NOTE**: The calendar variables used in this project are shared with other projects, including [Toggle Vibrate for Meetings](https://github.com/c-d-smith/android-automation/tree/main/projects/toggle-vibrate-for-meetings). If you are using a project that also uses these variables, then choose the `Partial Setup` option in the installer to set only your hours.

### Variables

  * `%EndEmailNotifications`
  * `%HolidayCalendar`
  * `%SetupEmailControl`
  * `%StartEmailNotifications`
  * `%WorkCalendar`

#### `%EndEmailNotifications`

  * Default Value: no default
  * Possible Values: time, in `HH:mm` format

This is the time of day you want to stop receiving email notifications. It needs to be in 24-hour format.

#### `%HolidayCalendar`

  * Default Value: no default
  * Possible Values: varies; string

This is the calendar that contains events that indicate when your employer is closed. This project expects that these are the only events on this calendar. If you don't have a clean calendar that contains only these events, then I recommend using only the `Email Control: Without Holiday Calendar` profile.

In fact, the only reason I make use of this variable is because people tend to be lazy and will allow repeating meetings to be scheduled on holidays, without removing those events that land on holidays. You could obviate the need for this variable by creating `Out of office` events on your `%WorkCalendar` to stand in for holidays. Since I am also obviously lazy and my employer provides a holiday calendar, I use it.

#### `%SetupEmailControl`

  * Default Value: no default
  * Possible Values: `false`, `true`, anything other than `false`

This controls whether the setup profile will trigger. When this variable is set to `false`, setup will not run. Therefore, by setting this to anything other than `false`, including simply erasing its value, and turning on the setup profile, setup can be run again at any time.

#### `%StartEmailNotifications`

  * Default Value: no default
  * Possible Values: time, in `HH:mm` format

This is the time of day you want to start receiving email notifications. It needs to be in 24-hour format.
