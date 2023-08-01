# Volume Functions

  * Version: 1.0.0
  * Release Date: 1 Aug 2023

## Get the Project Code

  * [From Google Drive (links to containing directory)](https://drive.google.com/drive/folders/12u6BbX-fF22aPMLjOU_NiN_I0DUyJTaE?usp=drive_link)
  * [From GitHub](https://github.com/c-d-smith/android-automation/blob/main/projects/volume-functions/Volume_Functions.prj.xml)

## Overview

This project provides an interface for easily getting and setting the various volumes. There are type-specific wrappers for both getting and setting a volume. This eliminates the need to remember the constant that correlates to the volume control you want to get or set.

Tasks that get volume types take no arguments, while tasks that set volume types take only the integer value to which to set it. There are no safeguards around the argument values. If the value is out-of-bounds/extreme or is not an integer, the attempt to set the volume will simply fail.

Maximum volume values vary by device, and some devices combine (as an example) ringer and notification volumes into one. You may have to experiment a bit to determine the maximum allowed value. This is something I'll probably provide an easier way to do in the future.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)
    
## Project Setup

This project does not require any setup, nor does it use any global variables.
