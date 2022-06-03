# v2.0.0

Implemented an installer that fires when the setup profile is turned on and the value of `%SetupToggleVibrate` is set to anything **other than** `false`. The installer dialogs make clear that the installer only works with Google calendars, and provides instructions for configuring the profile contexts for other calendars.

With the addition of the installer, this project now also requires [AutoCalendar](https://play.google.com/store/apps/details?id=com.joaomgcd.autocalendar).

I renamed the main profile to indicate that it also uses a holiday calendar, and I added a profile that does not use a holiday calendar. The installer will intelligently enable the appropriate profile, depending upon the user's input.
