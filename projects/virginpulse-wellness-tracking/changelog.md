# v2.0.9a

  * Changed how `No, Thanks` is handled when there is an offer to add a habit.

# v2.0.8a

  * Fixed a bug where the name of a habit added as part of a journey was not being stored in a global variable. This created a situation where the habit could not be deleted from the list of tracked habits.

# v2.0.7a

  * Changed how cards are processed.
    * Previously, the main screen was checked to see if there were any cards available with which to interact. This could lead to an infinite loop where a card existed that Tasker did not know how to interact with. This lead to a situation where Tasker would enter the card screen, be unable to interact with the available card, then exit to Home and re-query for available cards.
    * In this release, the cards screen is accessed, then it is queried to check if there are any cards with buttons labeled `GOT IT`, `WILL DO`, or `TRUE`.
    * This means that Tasker will no longer attempt to interact with all the cards. It will only interact with matching cards or with cards that display before them.
    * It also means that Tasker will enter the cards screen one extra time, and then exits back to the Home screen to proceed to journeys.
  * Updated the "Decline Home screen offers" logic to include `Not now` as a valid button.

# v2.0.6a

  * Fixed a bug where the habit delete button coordinates were not being correctly returned after querying for them. This prevented habits added as part of a journey from being deleted as they should have been.
  * Added the ability to interact with the year-end card announcing the start of the new program year.
  * Added a query for the transient dialog that asks the user to rate the application. I got fortunate and had one of these dialogs appear as I was querying for something else.

# v2.0.5a

  * Changed the installer to prevent it from overwriting global variable values, which will protect any customizations the user may have done while still enabling them to use the installer to easily and quickly update their tracked habits.
  * Changed how the project handles deleting a habit added as part of a journey. It now stores the name of the habit in `%HabitToDelete`, rather than trying to dynamically determine this. This will eliminate collisions between a habit added as part of a challenge that cannot yet be deleted and a habit added as part of a journey.
  * Implemented new functionality to handle updated privacy policies. Without this, Tasker cannot progress to the home screen and perform the tracking. Today is the first time I have seen this screen.

# v2.0.4

  * Fixed a bug in the setup routine that incorrectly referenced an obsolete variable used to set the device's unlock swipe direction. This caused `%SwipeDirection` to be incorrectly set to `%input`, leading to Tasker being unable to unlock the phone.

# v2.0.3

The project has been completely refactored. This includes a name change, as well, though the icon used is still that of VirginPulse. The dependency on AutoTools has been removed, and the only applications necessary now are Tasker and AutoInput.

### Tracking
Card interactions have been updated. In the interest of improved reliability, the tracker will interact with all cards instead of just cards worth points.

Habit tracking has been improved. When a habit is tracked as part of a challenge, the tracker will automatically stop tracking and remove it when the challenge is over. It should be noted that VirginPulse indicates the habit can be removed a full day before the habit can *actually* be removed. Don't worry about this; Tasker will remove it from your list of tracked habits.

Journey taking has been improved and simplified. The path through the logic is more reliable, and I have removed some logic that is no longer needed due to changes in how the VirginPulse app behaves.

Tracking will now also only happen if you have not reached your annual target. Before v2.0.0, tracking would still be done one day after reaching your target. From v2.0.0 onward, the day after reaching your target, Tasker will update the relevant variables and exit without performing tracking.

### Setup
I have implemented a setup routine that can easily be run whenever the user chooses. After you import the project into Tasker, simply open VirginPulse and the setup routine will run. To run it again in the future, simply open Tasker, turn on the setup profile, and then open VirginPulse. In all cases, it is important to remember that opening VirginPulse is the **last step** in running the setup routine.

The setup routine will set default values for all the tracker's variables. The variables are still described in detail on the [README](README.md) for those users interested in knowing how they're used or for those interested in customizing the default values.

### Technical
The tracker's tasks now also adhere much more closely to the Single Responsibility principle.
