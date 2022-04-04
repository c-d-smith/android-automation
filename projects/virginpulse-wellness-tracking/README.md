# VirginPulse Wellness Tracking

## Get the Project Code
  * [From Google Drive](https://drive.google.com/file/d/1gW8MtD0_2n0GCcD1W-nDaTtWzmPZ2GDx/view?usp=sharing)
  * [From Github](VirginPulse_Tracking.prj.xml)

## Overview

This project can track your "Healthy Habits", do your Cards, and do your Journeys daily at the time you choose. It is highly configurable and you choose what is automated. Tracking will continue until you earn at least the number of points you selected as your target for the year, and will resume automatically on 1 September.

Once tracking has been completed, VirginPulse will be left open on your device to enable you to confirm tracking was successful and to easily manually complete it in case there was an error.

### Habit Tracking

All habits are supported, except `Get a Workout`. This is because `Get a Workout` is too open-ended and the amount of work required to automate tracking this habit would almost certainly be exorbitant. Most habits are `Yes/No` or 'simple' habits, and Tasker will always choose `Yes`. The habit `Track your mood` presents you with a choice of six 'mood faces' and Tasker will always choose the happy face.

Some habits use a number-picker, while a few ask you to enter a number. The values entered for these habits are all randomized, and you choose the range of values. If you choose the same value for each end of the range, then that is the number that will always be used.

Tasker can track up to four habits automatically, and the habits you want it to track need to be at the top of the list. This project is not coded to scroll down the list to look for habits to track. I did have it set up this way for a while, but it created too much unpredictability and I removed it. Place your Tasker-tracked habits at the top of the list, followed by any other habits, such as those tracked using a fitness tracker or those you will manually track.

#### Special Notes

  # Tracking the habit `Track your weight` provides a once-per-month boost of 25 points. Otherwise, habits are worth 1 point per day for each of three habits, plus one point per day for tracking three habits.
  # Since there is no benefit to tracking more than three habits per day, I recommend configuring Tasker to track only three habits in addition to any habits that are tracked using a fitness tracker.
  # If you need to add a habit to complete a Challenge, then either update the automatically tracked habits list to include that habit (and keep it near the top of the list) or move it to at least the fourth position on the list and track it manually.

### Cards

Tasker will do two cards for you each day. It will only do cards that have `GOT IT`, `WILL DO`, or `TRUE/FALSE` buttons, and it will ignore the rest. You can manually interact with announcement or challenge cards, if you choose. If you choose to ignore them, that's entirely fine, too.

While tracking cards, Tasker will return to the Home screen after each card it tracks. This simplifies tracking cards because this interface is maddeningly difficult to query reliably. I found that speed and reliability were each improved by returning to the Home screen after tracking each card.

### Journeys

Tasker will do your journey for you each day. When a journey completes, Tasker will choose a new journey to start the next day. It will not automatically start a pregnancy-related journey, but it will automatically take each step, if you start it. Otherwise, Tasker will prefer journeys you have never taken and, if there are no uncompleted journeys, it will restart the first journey that you have already completed.

If a journey requires you to add a habit, Tasker will add the habit to complete the step and it will immediately return to the Habits screen and delete the new habit. It does this to ensure it will be able to continue tracking your habits without trouble.

### Limitations

#### Number-picker Based Habits

It is possible that tracking using a number-picker may not be perfectly precise. This affects time-based habits, such as `Get some sleep` or `Yoga`, and the number-based habit `Stress Levels`. This is due to the difference in the screen resolution of your device as compared to the screen resolution of my device (where the tasks were created). I am working to account for this and to improve reliability. Overall, it really shouldn't matter because some input will be recorded and that is, in the end, the goal.

#### Journeys

If there are no uncompleted journeys, then Tasker will end up repeating the same journey over and over. There is no easy way to get Tasker to move down the list of journeys and select a different already completed journey each time.

#### Achievement Announcements

I recommend disabling "Achievement Announcements" in your personal preferences because these will interfere with Tasker's wellness tracking. I have not coded this project to handle those announcements because they are too infrequent and unpredictable.

#### Rate in the App Store

In addition, the app will periodically ask you to rate it in the app store. I believe Tasker will gracefully handle these, but it is possible it will not. I have not been able to code to handle these because these overlays disappear when you change which app is active. In order to code for these, I have to be able to have Tasker query for them, but they're never there when I try to have Tasker retrieve their information.

#### Project Setup

There are currently no user interfaces to make setting this project up easier. I was working on this and I thought I was nearly done with it. Unfortunately, I discovered that they don't scale very well when the screen resolution of the device displaying them is different from the screen resolution of the device on which the interfaces were created. I am working to figure out how to overcome this.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)
  * [AutoInput](https://play.google.com/store/apps/details?id=com.joaomgcd.autoinput)
  * [AutoTools](https://play.google.com/store/apps/details?id=com.joaomgcd.autotools)

In order to use this project, you will need to purchase the full version of each of these apps, if you have not already. They are not expensive; in aggregate, less than $8 USD as of 4 April 2022.

### Tasker Setup and Permissions

Coming soon.

### AutoInput Setup and Permissions

Coming soon.

### AutoTools Setup and Permissions

Coming soon.

### Special Notes

Certain other apps may be unhappy that you have installed AutoInput, especially mobile banking apps because they may view automated click programs as a security vulnerability.

I really cannot understand why because the touch interactions that AutoInput generates are, from what I can see, exactly the same as actual touch interactions. If an attacker has enough control over your device to write Tasker projects to automate logging into your mobile banking app, then they have enough control over your device to log into your mobile banking app without the use of Tasker and AutoInput.

It is possible that cloning the mobile banking app into the Work Profile will alleviate this problem.

## Project Setup

### Tasker Setup

#### Variables

  * `%Checkmark`
  * `%Password`
  * `%SwipeDirection`

#### Overview

Tasker needs to be able to unlock your device. To do this, Tasker will need to know whether you tap a checkmark after entering your PIN, your PIN, and the direction you swipe to reveal the keypad.

This means your device will need to be unlocked using a PIN. If your device is not currently set to unlock using a PIN, you will need to change this. If you are not comfortable making this change, you could still use this project provided you ensure your device is unlocked daily at the time you select tracking to be completed.

With respect to data security, Tasker can be configured to automatically back up your projects, including variables. However, none of my projects are otherwise coded to exfiltrate your data or settings. I have no reason to make this happen, especially because I use these projects personally.

I created a task to make setting these variables easier: `General: Setup: Unlock`. On the `TASKS` tab, find this task and tap it to open it for editing. The first three actions in the task are where you will set the specifics for your device. After you have updated the actions as needed, then tap the play button in the lower left corner. Finally, tap the back arrow in the upper left corner to return to the `TASKS` tab.

### Project Setup

#### Variables

  * `%AnnualTarget`
  * `%AppRunTime`
  * `%DebugEnd`
  * `%DebugFlash`
  * `%DebugNotify`
  * `%DebugSay`
  * `%DoCards`
  * `%DoHabits`
  * `%DoJourney`
  * `%FoundHabits`
  * `%Habits`
  * `%MindfulHoursDefault`
  * `%MindfulHoursMax`
  * `%MindfulHoursMin`
  * `%MindfulMinutesDefault`
  * `%MindfulMinutesMax`
  * `%MindfulMinutesMin`
  * `%ReachedTarget`
  * `%SleepHoursDefault`
  * `%SleepHoursMax`
  * `%SleepHoursMin`
  * `%SleepMinutesDefault`
  * `%SleepMinutesMax`
  * `%SleepMinutesMin`
  * `%StepsMax`
  * `%StepsMin`
  * `%StressDefault`
  * `%StressMax`
  * `%StressMin`
  * `%StretchingHoursDefault`
  * `%StretchingHoursMax`
  * `%StretchingHoursMin`
  * `%StretchingMinutesDefault`
  * `%StretchingMinutesMax`
  * `%StretchingMinutesMin`
  * `%WeightMax`
  * `%WeightMin`
  * `%YogaHoursDefault`
  * `%YogaHoursMax`
  * `%YogaHoursMin`
  * `%YogaMinutesDefault`
  * `%YogaMinutesMax`
  * `%YogaMinutesMin`

#### Overview

That is pretty long list of variables, but most of them are habit-related and, as such, only need to be set if you are tracking the relevant habit. **You do not need to manually set all these variables.** *So don't let the list overwhelm you!*

I created a task to set all these variables to what I consider safe default values. If you want to use that and move on, find the task `VP: Controller: App: Setup: Defaults: Easy`, tap it to open it, and then tap the play button in the lower left corner.

When you do this, VirginPulse will open, Tasker will navigate to your list of habits, read them, and set the first three to be automatically tracked. VirginPulse will then close and you will return to Tasker. **It is important not to touch anything until after you are returned to Tasker!** On the other hand, if something does go wrong, nothing is broken; just re-run the task and Tasker will attempt setup again.

If you would rather DIY setting the values for the variables you actually need, please run the task `VP: Controller: App: Setup: Defaults: UI`. This sets the variables that represent the default values presented in the VirginPulse user interface for some habits. Of course, you can also set those variables yourself, as well.

Following is an explanation of what each variable is for, what its possible values are, and how to set them. 

##### `%AnnualTarget`

Default Value: `10000`
Possible Values: Any integer

This is the number of points you want to earn each year before tracking automatically stops. This needs to be entered as an integer, and without any punctuation. If you are setting this up for your spouse or partner, then you would most likely enter `2500` since anything over that doesn't matter, anyway. For yourself, you'll probably choose `5000`, `7500`, or `10000`.

If you don't want tracking to stop ever, simply enter some ridiculously large integer, such as `999999`. As long as it's an integer, it can be whatever you choose. Be aware that a negative integer will result in automatic wellness tracking occurring exactly once each year.

##### `%AppRunTime`

Default Value: `12:00`
Possible Values: Any time, in hh:mm format

This is the time of day you want tracking to occur. This is entered using 24-hour clock notation. If you want tracking to occur at `9:15 AM`, then you would set this to `9:15`; whereas if you wanted tracking to occur at `3:59 PM`, then you would set this to `15:59`.

For those who are not familiar with 24-hour notation, hours after Noon are represented as `12+X` where `X` is the afternoon hour. So, `1:00 PM` would be `13`. Midnight is represented as `00` - NOT `24`.

##### `%DebugEnd`

Default Value: `false`
Possible Values: `true`, `false`

This is used simply to make Tasker say `Exit` when tracking is complete.

##### `%DebugFlash`

Default Value: `false`
Possible Values: `true`, `false`

This is used to make Tasker flash a message (typically at the bottom of the screen) to indicate what it is doing. This is mostly used in situations where looping activity is possible, such as when trying to verify that a given page in VirginPulse has loaded.

This can slow the task that is running to provide time to flash the message, and [so far] not all messages will flash. I have not been able to find a reason why some messages are not flashed, especially since they all use the same flashing mechanism.

##### `%DebugNotify`

Default Value: `false`
Possible Values: `true`, `false`

This is used to make Tasker create a notification in your tray. Generally, this is used when a task is invoked and the only useful information provided is the name of the invoked task.

This has minimal to no effect on the speed at which Tasker attempts looping activity and, as such, it can generate upwards of one hundred notifications.

##### `%DebugSay`

Default Value: `false`
Possible Values: `true`, `false`

This is used to make Tasker say the name of the task that has been invoked.

This imposes considerable delay in proceeding through the tracking tasks, and can mask the source of trouble on a device with lower RAM and/or a slower CPU. This is useful when trying to determine whether it is an issue of Tasker needing to wait for the VirginPulse UI to update versus poorly constructed logic.

##### `%DoCards`

Default Value: `true`
Possible Values: `true`, `false`

Set this to `true` to have Tasker automatically do your cards. If you want to exempt them from automation, set this to `false` or leave it unset.

##### `%DoHabits`

Default Value: `true`
Possible Values: `true`, `false`

Set this to `true` to have Tasker automatically track your habits. If you want to exempt them from automation, set this to `false` or leave it unset.

##### `%DoJourney`

Default Value: `true`
Possible Values: `true`, `false`

This is used to control whether Tasker will automatically do your journey. If you want to exempt this from automation, set this to `false` or leave it unset.

##### `%FoundHabits`

Default Value: unset
Possible Values: varies; array

This is used by the easy setup routine mentioned earlier. It will be populated with the habits Tasker found in VirginPulse. *You do not need to do anything with this variable.* **Ever.**

##### `%Habits`

Default Value: unset
Possible Values: varies; array

This is the master list of habits that Tasker tracks for you. To set this, tap the plus sign button in the lower right corner. Name the variable `%HabitsX`, where `X` is a number greater than zero (0). Once created, tap the variable name and type in the name of the habit *as it appears in VirginPulse*. **Capitalization and spaces matter.**

If you are adding a habit that is not currently on your list, *add the habit to your list first*! The name of the habit can be different once it is on your list of tracked habits. (Yes, this annoys me, but what can you do?)

For example, if Tasker is going to track the habits `Start With Oats`, `Get some sleep`, and `Track your weight` for you, then you will end up with a variable list that looks like this:
  * `%Habits`
  * `%Habits1`: `Start With Oats`
  * `%Habits2`: `Get some sleep`
  * `%Habits3`: `Track your weight`

##### `%MindfulHoursDefault`

Default Value: `0`
Possible Values: `0` to `??`

This is the default value displayed in VirginPulse for the habit `Mindful Moment`. It represents the number of hours you spent engaged in this activity. Generally speaking, zero is the best value for this variable.

##### `%MindfulHoursMax`

Default Value: `0`
Possible Values: `0` to `??`

This is used for randomizing the hours spent on the habit `Mindful Moment`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%MindfulHoursMin` will remove randomization.

##### `%MindfulHoursMin`

Default Value: `0`
Possible Values: `0` to `??`

This is used for randomizing the hours spent on the habit `Mindful Moment`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%MindfulHoursMax` will remove randomization.

##### `%MindfulMinutesDefault`

Default Value: `30`
Possible Values: `0` to `59`

This is the default value displayed in VirginPulse for the habit `Mindful Moment`. It represents the number of minutes you spent engaged in this activity. Generally speaking, 30 is the best value for this variable because it results in the least travel required to reach all the possible values.

##### `%MindfulMinutesMax`

Default Value: `59`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Mindful Moment`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%MindfulMinutesMin` will remove randomization.

##### `%MindfulMinutesMin`

Default Value: `0`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Mindful Moment`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%MindfulMinutesMax` will remove randomization.

##### `%ReachedTarget`

Default Value: `false`
Possible Values: `true`, `false`

This is used to track whether you have reached your annual points target. When this is set to `true`, Tasker will not perform wellness tracking for you. This is reset to `false` on 1 September. Otherwise, Tasker checks the number of points you have accumulated each time it does wellness tracking and updates this to `true` when your annual points target has been reached or exceeded. *You do not need to do anything with this variable.* **Ever.**

##### `%SleepHoursDefault`

Default Value: `7`
Possible Values: `0` to `??`

This is the default value displayed in VirginPulse for the habit `Get some sleep`. It represents the number of hours you spent engaged in this activity. Generally speaking, seven is the best value for this variable.

##### `%SleepHoursMax`

Default Value: `8`
Possible Values: `0` to `23`

This is used for randomizing the hours spent on the habit `Get some sleep`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%SleepHoursMin` will remove randomization.

##### `%SleepHoursMin`

Default Value: `7`
Possible Values: `0` to `23`

This is used for randomizing the hours spent on the habit `Get some sleep`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%SleepHoursMax` will remove randomization.

##### `%SleepMinutesDefault`

Default Value: `30`
Possible Values: `0` to `59`

The default value displayed in VirginPulse for the habit `Get some sleep` is actually zero. It represents the number of minutes you spent engaged in this activity. Generally speaking, 30 is the best value for this variable because it results in the least travel required to reach all the possible values.

##### `%SleepMinutesMax`

Default Value: `59`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Get some sleep`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%SleepMinutesMin` will remove randomization.

##### `%SleepMinutesMin`

Default Value: `0`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Get some sleep`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%SleepMinutesMax` will remove randomization.

##### `%StepsMax`

Default Value: `8729`
Possible Values: `0` to `??`

This is used for randomizing the value for the habit `Steps`, and it represents the upper bound of the number of steps you take each day. This is habit is completed simply by typing in the number of steps you took; as such, the default value is entirely arbitrary and it is the value set by the easy setup routine mentioned earlier.

Setting this equal to, or less than, the value of `%StepsMin` will remove randomiation.

##### `%StepsMin`

Default Value: `1952`
Possible Values: `0` to `??`

This is used for randomizing the value for the habit `Steps`, and it represents the lower bound of the number of steps you take each day. This is habit is completed simply by typing in the number of steps you took; as such, the default value is entirely arbitrary and it is the value set by the easy setup routine mentioned earlier.

Setting this equal to, or greater than, the value of `%StepsMax` will remove randomiation.

##### `%StressDefault`

Default Value: `3`
Possible Values: `1` to `5`

This is the default value displayed in VirginPulse for the habit `Stress Levels`. It represents your stress level on a scale of one to five. Generally speaking, three is the best value for this variable because it requires the least travel to reach all possible values.

##### `%StressMax`

Default Value: `5`
Possible Values: `1` to `5`

This is used for randomizing your estimated stress level in the habit `Stress Levels`, and it represents the upper bound of the range. Setting this equal to, or less than, `%StressMin` will remove randomization.

##### `%StressMin`

Default Value: `1`

Possible Values: `1` to `5`

This is used for randomizing your estimated stress level in the habit `Stress Levels`, and it represents the lower bound of the range. Setting this equal to, or greater than, `%StressMax` will remove randomization.

##### `%StretchingHoursDefault`

Default Value: `0`
Possible Values: `0` to `??`

This is the default value displayed in VirginPulse for the habit `Minutes of Stretching`. It represents the number of hours you spent engaged in this activity. Generally speaking, zero is the best value for this variable.

##### `%StretchingHoursMax`

Default Value: `0`
Possible Values: `0` to `??`

This is used for randomizing the hours spent on the habit `Minutes of Stretching`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%StretchingHoursMin` will remove randomization.

##### `%StretchingHoursMin`

Default Value: `0`
Possible Values: `0` to `??`

This is used for randomizing the hours spent on the habit `Minutes of Stretching`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%StretchingHoursMax` will remove randomization.

##### `%StretchingMinutesDefault`

Default Value: `30`
Possible Values: `0` to `59`

This is the default value displayed in VirginPulse for the habit `Minutes of Stretching`. It represents the number of minutes you spent engaged in this activity. Generally speaking, 30 is the best value for this variable because it results in the least travel required to reach all the possible values.

##### `%StretchingMinutesMax`

Default Value: `59`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Minutes of Stretching`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%StretchingMinutesMin` will remove randomization.

##### `%StretchingMinutesMin`

Default Value: `0`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Minutes of Stretching`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%StretchingMinutesMax` will remove randomization.

##### `%WeightMax`

Default Value: `160`
Possible Values: `0` to `??`

This is used for randomizing the value for the habit `Track your weight`, and it represents the upper bound of your weight. This is habit is completed simply by typing in your weight; as such, the default value is entirely arbitrary and it is the value set by the easy setup routine mentioned earlier.

Setting this equal to, or less than, the value of `%WeightMin` will remove randomiation.

##### `%WeightMin`

Default Value: `150`
Possible Values: `0` to `??`

This is used for randomizing the value for the habit `Track your weight`, and it represents the lower bound of your weight. This is habit is completed simply by typing in your weight; as such, the default value is entirely arbitrary and it is the value set by the easy setup routine mentioned earlier.

Setting this equal to, or greater than, the value of `%WeightMax` will remove randomiation.

##### `%YogaHoursDefault`

Default Value: `0`
Possible Values: `0` to `??`

This is the default value displayed in VirginPulse for the habit `Yoga`. It represents the number of hours you spent engaged in this activity. Generally speaking, zero is the best value for this variable.

##### `%YogaHoursMax`

Default Value: `1`
Possible Values: `0` to `??`

This is used for randomizing the hours spent on the habit `Yoga`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%YogaHoursMin` will remove randomization.

##### `%YogaHoursMin`

Default Value: `0`
Possible Values: `0` to `??`

This is used for randomizing the hours spent on the habit `Yoga`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%YogaHoursMax` will remove randomization.

##### `%YogaMinutesDefault`

Default Value: `30`
Possible Values: `0` to `59`

This is the default value displayed in VirginPulse for the habit `Yoga`. It represents the number of minutes you spent engaged in this activity. Generally speaking, 30 is the best value for this variable because it results in the least travel required to reach all the possible values.

##### `%YogaMinutesMax`

Default Value: `59`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Yoga`, and it represents the upper bound of the range of values. Setting this equal to, or less than, `%YogaMinutesMin` will remove randomization.

##### `%YogaMinutesMin`

Default Value: `0`
Possible Values: `0` to `59`

This is used for randomizing the minutes spent on the habit `Yoga`, and it represents the lower bound of the range of values. Setting this equal to, or greater than, `%YogaMinutesMax` will remove randomization.
