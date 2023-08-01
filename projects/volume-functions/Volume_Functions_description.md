    Tasks
        Task: Volume Functions: Set: Ringer
        
        A1: Perform Task [
             Name: Volume Functions: Set: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLR
             Parameter 2 (%par2): %par1
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Get: Alarm
        
        A1: Perform Task [
             Name: Volume Functions: Get: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLA
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Get: Ringer
        
        A1: Perform Task [
             Name: Volume Functions: Get: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLR
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Get: Call
        
        A1: Perform Task [
             Name: Volume Functions: Get: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLC
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Get: System
        
        A1: Perform Task [
             Name: Volume Functions: Get: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLS
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Set: Custom
        
        A1: If [ %par1 eq VOLS ]
        
            A2: System Volume [
                 Level: %par2 ]
        
        A3: Else
            If  [ %par1 eq VOLR ]
        
            A4: Ringer Volume [
                 Level: %par2
                 Display: On ]
        
        A5: Else
            If  [ %par1 eq VOLN ]
        
            A6: Notification Volume [
                 Level: %par2 ]
        
        A7: Else
            If  [ %par1 eq VOLM ]
        
            A8: Media Volume [
                 Level: %par2
                 Display: On ]
        
        A9: Else
            If  [ %par1 eq VOLA ]
        
            A10: Alarm Volume [
                  Level: %par2 ]
        
        A11: End If
        
        
    
        Task: Volume Functions: Get: Custom
        
        <Valid values (type):
        * VOLA (Alarm)
        * VOLC (Call)
        * VOLD (DTMF)
        * VOLM (Media)
        * VOLN (Notification)
        * VOLR (Ringer)
        * VOLS (System)>
        A1: Variable Set [
             Name: %volume_type
             To: %%par1
             Structure Output (JSON, etc): On ]
        
        A2: Return [
             Value: %volume_type
             Stop: On ]
        
        
    
        Task: Volume Functions: Set: Notification
        
        A1: Perform Task [
             Name: Volume Functions: Set: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLN
             Parameter 2 (%par2): %par1
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Set: System
        
        A1: Perform Task [
             Name: Volume Functions: Set: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLS
             Parameter 2 (%par2): %par1
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Set: Media
        
        A1: Perform Task [
             Name: Volume Functions: Set: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLM
             Parameter 2 (%par2): %par1
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Get: Notification
        
        A1: Perform Task [
             Name: Volume Functions: Get: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLN
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Set: Call
        
        A1: Perform Task [
             Name: Volume Functions: Set: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLC
             Parameter 2 (%par2): %par1
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Get: Media
        
        A1: Perform Task [
             Name: Volume Functions: Get: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLM
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Volume Functions: Set: Alarm
        
        A1: Perform Task [
             Name: Volume Functions: Set: Custom
             Priority: %priority
             Parameter 1 (%par1): VOLA
             Parameter 2 (%par2): %par1
             Structure Output (JSON, etc): On ]
        
        
