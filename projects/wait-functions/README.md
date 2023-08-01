# Wait Functions

  * Version: 1.0.0
  * Release Date: 1 Aug 2023

## Get the Project Code

  * [From Google Drive (links to containing directory)](https://drive.google.com/drive/folders/12VYU8gamgsRSPwKECAQrjU7usRjyGkef?usp=sharing)
  * [From GitHub](https://github.com/c-d-smith/android-automation/blob/main/projects/wait-functions/Wait_Functions.prj.xml)

## Overview

This project provides a simple, easy-to-use, and consistent way to make Tasker wait between tasks. It's designed to be used by other projects, has no profiles, and has been organized into a project to keep task lists tidy and organized.

The code in `Wait Functions: Main` is very simple, though the concept behind its execution is a little difficult to explain. I created this as a scalable way to wait a variable number of seconds or milliseconds. You can invoke this task with zero, one, or two arguments:
  * `%par1` This is the number of seconds and millisecons you want to wait in each loop. It is passed as `seconds|milliseconds` and this defaults to `1|0` to wait for one second and zero milliseconds.
  * `%par2` This is the number of times the task should perform the wait using the values from `%par1`. It defaults to `1`.

For example, if you want to wait for five seconds, you can simply call `Wait Functions: Main` and pass in `5` as the value for `%par2`, or you can pass in `5|0` as the value for `%par1`. The former will cause `Wait Functions: Main` to wait five times for one second each time, while the latter will cause it to wait one time for five seconds.

## Apps Required

  * [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm)
    
## Project Setup

This project does not require any setup, nor does it use any global variables.
