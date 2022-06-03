# Toggle Vibrate for Meetings

  * Version: 1.0.0
  * Release Date: 3 Jun 2022

## Get the Project Code

  * [From Google Drive](https://drive.google.com/drive/folders/1uAgHTsr9h_y2N8mRqMN8_ewsVvTnFQcm?usp=sharing)
  * [From Github](Toggle_Vibrate_for_Meetings.prj.xml)

## Overview

This project monitors the selected calendar for events where you are marked as "busy", then puts your phone on vibrate when the meeting starts, and removes your phone from vibrate when the meeting ends. If you have consecutive or overlapping meetings, your phone will remain on vibrate until the last meeting ends. When your phone exits vibrate mode, your volumes are restored to what they were when the phone entered vibrate mode.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)

In order to use this project, you will need to purchase Tasker, if you have not already. Tasker is around $4 USD as of 3 Jun 2022.

### Tasker Setup and Permissions

Coming soon.

## Project Setup

The next version of this project will include a setup routine to help you set it up. Until then, you'll need to manually set the two variables this project uses.

To do this, tap on the:
  * `VARS` tab in Tasker to see this project's variables,
  * `%HolidayCalendar` variable and set that to `Google:TC Holiday Calendar`,
  * `%WorkCalendar` variable and set that to `Google:you@umn.edu`.

Once those are set, your phone will go into vibrate mode for meetings that fall on days the University is not closed and days you are not marked 'Out of office' on your calendar.
