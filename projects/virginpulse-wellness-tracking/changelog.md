# v2.0.4

Fixed a bug in the setup routine that incorrectly referenced an obsolete variable used to set the device's unlock swipe direction. This caused `%SwipeDirection` to be incorrectly set to `%input`, leading to Tasker being unable to unlock the phone.

# v2.0.3

The project has been completely refactored. This includes a name change, as well, though the icon used is still that of VirginPulse. The dependency on AutoTools has been removed, and the only applications necessary now are Tasker and AutoInput.

### Tracking
Card interactions have been updated. In the interest of improved reliability, the tracker will interact with all cards instead of just cards worth points.

Habit tracking has been improved. When a habit is tracked as part of a challenge, the tracker will automatically stop tracking and remove it when the challenge is over. It should be noted that VirginPulse indicates the habit can be removed a full day before the habit can *actually* be removed. Don't worry about this; Tasker will remove it from your list of tracked habits.

Journey taking has been improved and simplified. The path through the logic is more reliable, and I have removed some logic that is no longer needed due to changes in how the VirginPulse app behaves.

Tracking will now also only happen if you have not reached your annual target. Before v2.0.0, tracking would still be done one day after reaching your target. From v2.0.0 onward, the day after reaching your target, Tasker will update the relevant variables and exit without performing tracking.

### Setup
I have implemented a setup routine that can easily be run whenever the user chooses. After you import the project into Tasker, simply open VirginPulse and the setup routine will run. To run it again in the future, simply open Tasker, turn on the setup profile, and then open VirginPulse. In all cases, it is important to remember that opening VirginPulse is the **last step** in running the setup routine.

The setup routine will set default values for all the tracker's variables. The variables are still described in detail below for those users interested in knowing how they're used or for those interested in customizing the default values.

### Technical
The tracker's tasks now also adhere much more closely to the Single Responsibility principle.
