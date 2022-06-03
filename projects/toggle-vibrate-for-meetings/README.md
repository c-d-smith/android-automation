# Toggle Vibrate for Meetings

  * Version: 2.0.1
  * Release Date: 3 Jun 2022

## Get the Project Code

  * [From Google Drive](https://drive.google.com/drive/folders/1uAgHTsr9h_y2N8mRqMN8_ewsVvTnFQcm?usp=sharing)
  * [From Github](Toggle_Vibrate_for_Meetings.prj.xml)
  * [Changelog](changelog.md)

## Overview

This project monitors the selected calendar for events where you are marked as "busy", then puts your phone on vibrate when the meeting starts, and removes your phone from vibrate when the meeting ends. If you have consecutive or overlapping meetings, your phone will remain on vibrate until the last meeting ends. When your phone exits vibrate mode, your volumes are restored to what they were when the phone entered vibrate mode.

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

The installer will walk you through selecting your calendar|s. It expects that you're using Google calendars. If you are not, then you will not be able to use the installer.

Instead, you will need to tap the `PROFILES` tab, then tap the profile you want to use to expand it. Once expanded, you can tap each of the contexts to edit them, one at a time. Find the variable and back it out, including the `%` sign. Once the input field is cleared, tap the magnifying glass to the right and just above the input field. This will display a list of calendars your phone syncs and you can select the correct calendar from that list. Finally, turn the profile on, and save.

### Variables

  * `%HolidayCalendar`
  * `%SetupToggleVibrate`
  * `%WorkCalendar`

#### `%HolidayCalendar`

Default Value: no default
Possible Values: varies; string

This is the calendar that contains events that indicate when your employer is closed. This project expects that these are the only events on this calendar. If you don't have a clean calendar that contains only these events, then I recommend using only the `Toggle Vibrate: Without Holiday Calendar` profile.

In fact, the only reason I make use of this variable is because people tend to be lazy and will allow repeating meetings to be scheduled on holidays, without removing those events that land on holidays. You could obviate the need for this variable by creating `Out of office` events on your `%WorkCalendar` to stand in for holidays. Since I am also obviously lazy and my employer provides a holiday calendar, I use it.

#### `%SetupToggleVibrate`

Default Value: no default
Possible Values: `false`, `true`, anything other than `false`

This controls whether the setup profile will trigger. When this variable is set to `false`, setup will not run. Therefore, by setting this to anything other than `false`, including simply erasing its value, and turning on the setup profile, setup can be run again at any time.

#### `%WorkCalendar`

Default Value: no default
Possible Values: varies; string

This is the calendar that contains meeting events, which are really any event where you are marked as `busy`, and your `Out of office` events.
