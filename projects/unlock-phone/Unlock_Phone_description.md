```
   Profiles
        Profile: Unlock Phone: Install
        	State: Variable Value  [ %SetupUnlockPhone neq false ]
        
        
        
        Enter Task: Unlock Phone: Install: Main
        
        <Show overview and store whether the user indicated they have AutoInput.>
        A1: Perform Task [
             Name: Unlock Phone: Install: AutoInput
             Priority: %priority
             Return Value Variable: %ai_selection
             Structure Output (JSON, etc): On ]
        
        <Set %SwipeDirection.>
        A2: Perform Task [
             Name: Unlock Phone: Install: Swipe Direction
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Set %Checkmark.>
        A3: Perform Task [
             Name: Unlock Phone: Install: Checkmark
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Set %Password.>
        A4: Perform Task [
             Name: Unlock Phone: Install: PIN
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Open AutoInput, if they don't have it.
        
        Offer to test unlocking the phone, if they do.>
        A5: Perform Task [
             Name: Unlock Phone: Install: Cleanup
             Priority: %priority
             Parameter 1 (%par1): %ai_selection
             Structure Output (JSON, etc): On ]
        
        
    
    Tasks
        Task: Unlock Phone: Install: AutoInput
        
        A1: Text/Image Dialog [
             Title: Setup: Overview
             Text: The next dialogs will help you set the variables needed to enable Tasker to unlock your phone.
             
             If you want to run this installer again, simply re-enable the installer's profile.
             
             IMPORTANT!
             You need to install and purchase AutoInput for this to work! If you do not currently have this Tasker plugin, click "I do NOT have AutoInput" and the Google Play store will open when setup is complete.
             Button 1: I have AutoInput.
             Button 2: I do NOT have AutoInput.
             Close After (Seconds): 30 ]
        
        A2: Return [
             Value: %td_button
             Stop: On ]
        
        
    
        Task: Unlock Phone: Install: Swipe Direction
        
        A1: Text/Image Dialog [
             Title: Swipe Direction
             Text: Which direction do you swipe to unlock your phone?
             Button 1: Vertical
             Button 2: Horizontal 
             Close After (Seconds): 30 ]
        
        A2: Variable Set [
             Name: %SwipeDirection
             To: %td_button
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Unlock Phone: Install: Checkmark
        
        A1: Text/Image Dialog [
             Title: Checkmark
             Text: Do you click a checkmark after entering your PIN?
             
             If you do not use a lock screen or only have to swipe to unlock your phone, choose "No".
             Button 1: Yes
             Button 2: No
             Close After (Seconds): 30 ]
        
        A2: Variable Set [
             Name: %Checkmark
             To: false
             Structure Output (JSON, etc): On ]
        
        A3: If [ %td_button eq Yes ]
        
            A4: Variable Set [
                 Name: %Checkmark
                 To: true
                 Structure Output (JSON, etc): On ]
        
        A5: End If
        
        
    
        Task: Unlock Phone: Install: PIN
        
        A1: Input Dialog [
             Title: PIN
             Text: Please enter the PIN used to unlock your phone. Your PIN is only stored locally. This project does not export any data. (I don't even know if that's possible, and I've never tried.)
             
             If you do not use a PIN, click "Cancel".
             
             NOTE: Clicking "Cancel" will clear the value of the global variable "Password" if one is already set!
             Close After (Seconds): 30
             Input Type: 524289
             Output Variable Name: %pin_value
             Continue Task After Error:On ]
        
        A2: If [ %pin_value Set ]
        
            A3: Variable Set [
                 Name: %Password
                 To: %pin_value
                 Structure Output (JSON, etc): On ]
        
        A4: Else
        
            A5: Variable Clear [
                 Name: %Password ]
        
        A6: End If
        
        
    
        Task: Unlock Phone: Not Used: Phone Lock Status
        
        <<b>Device Locked</b>: The device is locked and asks for authentication in order to use it.<br><br>
        <b>Device Secure</b>: The device is protected (service), regardless of if the protection mechanism is not currently required to use the device.<br><br>
        <b>Keyguard Locked</b>: The device is locked and doesn't ask for authentication in order to use it.<br><br>
        <b>Keyguard Secure</b>: The Lockscreen is enabled (service), regardless of if the device is locked or not.<br><br>
        - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -<br><br>
        The <b>Device/Keyguard Locked</b> represents the current state of the device, and <b>Device/Keyguard Secure</b> represents the general configuration of the device.>
        A1: Anchor
        
        A2: Java Function [
             Return: (KeyguardManager) km
             Class Or Object: CONTEXT
             Function: getSystemService
             {Object} (String)
             Param 1 (String): keyguard ]
        
        <Device Locked>
        A3: Java Function [
             Return: %dvc_locked
             Class Or Object: km
             Function: isDeviceLocked
             {boolean} () ]
        
        <Device Secure>
        A4: Java Function [
             Return: %dvc_secure
             Class Or Object: km
             Function: isDeviceSecure
             {boolean} () ]
        
        <Keyguard Locked>
        A5: Java Function [
             Return: %kg_locked
             Class Or Object: km
             Function: isKeyguardLocked
             {boolean} () ]
        
        <Keyguard Secure>
        A6: Java Function [
             Return: %kg_secure
             Class Or Object: km
             Function: isKeyguardSecure
             {boolean} () ]
        
        A7: Return [
             Value: %dvc_locked
             Stop: On ]
        
        
    
        Task: Unlock Phone: Screen On
        
        A1: AutoInput Screen Off/On [
             Configuration: Screen Off Or On: Turn On
             Timeout (Seconds): 60
             Structure Output (JSON, etc): On ]
            If  [ %SCREEN eq off ]
        
        
    
        Task: Unlock Phone: Install: Cleanup
        
        A1: Variable Set [
             Name: %ai_selection
             To: %par1
             Structure Output (JSON, etc): On ]
        
        A2: If [ %ai_selection ~ *NOT* ]
        
            A3: Launch App [
                 Package/App Name: Play Store ]
        
        A4: Else
        
            A5: Perform Task [
                 Name: Unlock Phone: Install: Test
                 Priority: %priority
                 Structure Output (JSON, etc): On ]
        
        A6: End If
        
        A7: Profile Status [
             Name: Unlock Phone: Install
             Set: Off ]
        
        
    
        Task: Unlock Phone: Screen Off
        
        A1: Turn Off [
             Lock: On ]
        
        
    
        Task: Unlock Phone: Install: Test
        
        A1: Text/Image Dialog [
             Title: Test Unlock 
             Text: Do you want to test unlocking your phone?
             Button 1: Yes
             Button 2: No
             Close After (Seconds): 30 ]
        
        A2: If [ %td_button eq Yes ]
        
            A3: Perform Task [
                 Name: Unlock Phone: Install: Test Unlocking
                 Priority: %priority
                 Structure Output (JSON, etc): On ]
        
        A4: End If
        
        
    
        Task: Unlock Phone: Install: Test Unlocking
        
        A1: Perform Task [
             Name: Unlock Phone: Screen Off
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Wait 4s.>
        A2: Perform Task [
             Name: Wait Functions: Main
             Priority: %priority
             Parameter 2 (%par2): 4
             Structure Output (JSON, etc): On ]
        
        A3: Perform Task [
             Name: Unlock Phone: Main
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Unlock Phone: Main
        
        <If the screen is off, turn it on.>
        A1: Perform Task [
             Name: Unlock Phone: Wake Screen
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Perform a swipe.>
        A2: Perform Task [
             Name: Unlock Phone: Swipe
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Attempt to unlock the phone.>
        A3: Perform Task [
             Name: Unlock Phone: Enter PIN
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Unlock Phone: Enter PIN
        Settings: Abort Existing Task
        
        <We don't actually care about %dvc_locked because %kg_locked is what we actually need. Retaining %dvc_locked in case we need it in the future.>
        A1: Anchor
        
        A2: Java Function [
             Return: (KeyguardManager) km
             Class Or Object: CONTEXT
             Function: getSystemService
             {Object} (String)
             Param 1 (String): keyguard ]
        
        <Device Locked>
        A3: Java Function [
             Return: %dvc_locked
             Class Or Object: km
             Function: isDeviceLocked
             {boolean} () ]
        
        <Keyguard Locked>
        A4: Java Function [
             Return: %kg_locked
             Class Or Object: km
             Function: isKeyguardLocked
             {boolean} () ]
        
        A5: If [ %kg_locked eq true ]
        
            A6: If [ %Password Set ]
        
                <Effectively splits the Password on each digit, creating an array of digits.>
                A7: Variable Search Replace [
                     Variable: %Password
                     Search: \d
                     Store Matches In Array: %digits ]
        
                <Loop through the digits and click each one.>
                A8: For [
                     Variable: %digit
                     Items: %digits()
                     Structure Output (JSON, etc): On ]
        
                    A9: AutoInput Action [
                         Configuration: Type: Id
                         Value: com.android.systemui:id/key%digit
                         Action : Click
                         Timeout (Seconds): 2
                         Continue Task After Error:On ]
        
                    <Wait 200ms.>
                    A10: Perform Task [
                          Name: Wait Functions: Wait
                          Priority: %priority
                          Parameter 1 (%par1): 200
                          Parameter 2 (%par2): 0
                          Structure Output (JSON, etc): On ]
        
                A11: End For
        
                <Click the checkmark, if needed.>
                A12: AutoInput Action [
                      Configuration: Type: Id
                     Value: com.android.systemui:id/key_enter
                     Action : Click
                      Timeout (Seconds): 2
                      Continue Task After Error:On ]
                    If  [ %Checkmark eq true ]
        
            A13: End If
        
            <Wait 1s.>
            A14: Perform Task [
                  Name: Wait Functions: Main
                  Priority: %priority
                  Structure Output (JSON, etc): On ]
        
        A15: End If
        
        
    
        Task: Unlock Phone: Swipe
        
        A1: If [ %SwipeDirection ~ *ertical ]
        
            A2: Perform Task [
                 Name: Swipe Functions: Vertical
                 Priority: %priority
                 Parameter 1 (%par1): 500,2000,1225
                 Parameter 2 (%par2): 25
                 Structure Output (JSON, etc): On ]
        
        A3: Else
        
            A4: Perform Task [
                 Name: Swipe Functions: Horizontal
                 Priority: %priority
                 Parameter 1 (%par1): 200,1500,1500
                 Parameter 2 (%par2): 500
                 Structure Output (JSON, etc): On ]
        
        A5: End If
        
        <Wait 1s.>
        A6: Perform Task [
             Name: Wait Functions: Main
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Unlock Phone: Wake Screen
        
        A1: Variable Set [
             Name: %screen_state
             To: %SCREEN
             Structure Output (JSON, etc): On ]
        
        A2: If [ %screen_state eq off ]
        
            A3: Perform Task [
                 Name: Unlock Phone: Screen On
                 Priority: %priority
                 Structure Output (JSON, etc): On ]
        
            <Wait 4s.>
            A4: Perform Task [
                 Name: Wait Functions: Main
                 Priority: %priority
                 Parameter 2 (%par2): 4
                 Structure Output (JSON, etc): On ]
        
        A5: End If
        
        
    
        Task: Unlock Phone: Install: Main
        
        <Show overview and store whether the user indicated they have AutoInput.>
        A1: Perform Task [
             Name: Unlock Phone: Install: AutoInput
             Priority: %priority
             Return Value Variable: %ai_selection
             Structure Output (JSON, etc): On ]
        
        <Set %SwipeDirection.>
        A2: Perform Task [
             Name: Unlock Phone: Install: Swipe Direction
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Set %Checkmark.>
        A3: Perform Task [
             Name: Unlock Phone: Install: Checkmark
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Set %Password.>
        A4: Perform Task [
             Name: Unlock Phone: Install: PIN
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        <Open AutoInput, if they don't have it.
        
        Offer to test unlocking the phone, if they do.>
        A5: Perform Task [
             Name: Unlock Phone: Install: Cleanup
             Priority: %priority
             Parameter 1 (%par1): %ai_selection
             Structure Output (JSON, etc): On ]
        
       

```
