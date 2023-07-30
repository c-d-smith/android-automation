# Unlock Phone

  * Version: 1.0.0
  * Release Date: 30 Jul 2023

## Get the Project Code

  * [From Google Drive (links to containing directory)](https://drive.google.com/drive/folders/1-luS-ClyG4ifqqj8UldwdHYBH2FUiwR0?usp=drive_link)
  * [From GitHub](https://github.com/c-d-smith/android-automation/blob/main/projects/unlock-phone/Unlock_Phone.prj.xml)

## Overview

This project will wake your phone and unlock your phone. It works with the following lock screen types: PIN, swipe, or no security at all.

It might be able to be modified to unlock using a pattern lock screen, but this will be brittle and will need to be updated each time the user gets a new phone because the coordinates of the dots vary by screen size and resolution. Due to this, I am unwilling to support this lock screen type.

In the past, I have tried to make it work using a password lock screen. However, AutoInput is unable to interact with the on-screen keyboard while the phone is locked, and this is probably a security restriction imposed by Android.

The PIN is stored in a global variable, the value of which is not exported unless you explicitly tell Tasker to save it as part of the export. I have verified this because my own PIN is not part of this project's code.

This project includes an installer that helps you set the few global variables needed for it to function correctly. Therefore, there is never a reason to export the value of any of the global variables and thereby compromise your security.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)
  * [AutoInput](https://play.google.com/store/apps/details?id=com.joaomgcd.autoinput)

In order to use this project, you will need to purchase the full version of each of these apps, if you have not already.

## Project Setup

This project includes an installer, which is controlled by a profile. Simply turn on the profile, save Tasker's state by clicking the checkmark in the upper right, and the installer will run. When setup is complete, the profile turns off. You can re-run the installer at any time by turning the profile back on.

The installer will ask whether you have AutoInput already. If you do not, it will launch the Play store app for you after setup is complete. I do not currently know how to get the Play store to take you directly to AutoInput (without using AutoInput itself), but it's something I plan to do more investigation into and try to solve.

### Variables

  * `%Checkmark`
  * `%Password`
  * `%SetupUnlockPhone`
  * `%SwipeDirection`

#### Checkmark

This variable indicates whether you need to tap a checkmark after entering your PIN. If you do not use a PIN to unlock your phone, you should answer "No" when asked by the installer.

#### Password

This variable stores your PIN. I feel it's important to reiterate that the values of four of the variables used by this project are, by default, **_not_** exported when this project is exported.

When the installer prompts you for your PIN, enter it exactly as you would if you were unlocking your phone. That is to say, enter only digits.

#### SetupUnlockPhone

This variable is used by the installer to determine whehter or not it should run when the profile is turned on. It will never have a value, unless you manually give it one, and it does not require a value.

#### SwipeDirection

This variable indicates the direction you need to swipe to reveal the PIN pad. I learned the hard way that this can vary by phone and/or manufacturer. When prompted, just choose either "Vertical" or "Horizontal".
