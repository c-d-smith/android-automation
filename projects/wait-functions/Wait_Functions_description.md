   Tasks
        Task: Wait Functions: Wait
        
        <Wait for a number of seconds (%par2) and milliseconds (%par1) as specified by the caller.<br><br>
        
        If no arguments are provided, we wait for 1s. If only one argument is provided, we will use that in combination with the default set for the other.>
        A1: Anchor
        
        <Default to 1s 0ms>
        A2: Multiple Variables Set [
             Names: %milliseconds|%seconds
             Variable Names Splitter: |
             Values: 0|1
             Values Splitter: |
             Structure Output (JSON, etc): On ]
        
        A3: Variable Set [
             Name: %milliseconds
             To: %par1
             Structure Output (JSON, etc): On ]
            If  [ %par1 Set ]
        
        A4: Variable Set [
             Name: %seconds
             To: %par2
             Structure Output (JSON, etc): On ]
            If  [ %par2 Set ]
        
        A5: Wait [
             MS: %milliseconds
             Seconds: %seconds
             Minutes: 0
             Hours: 0
             Days: 0 ]
        
        
    
        Task: Wait Functions: Main
        
        <Some text>
        A1: Anchor
        
        <Dwell time defaults to 1s 0ms, and is passed in as "s|ms". The pipe character separating the two values is important!
        
        The number of loops to perform defaults to 1.
        
        Simple loops of 1s duration can be performed by passing in only the number of loops.>
        A2: Anchor
        
        A3: Variable Set [
             Name: %dwell_time
             To: 1|0
             Structure Output (JSON, etc): On ]
        
        A4: Variable Set [
             Name: %loop_control
             To: 1
             Structure Output (JSON, etc): On ]
        
        A5: Variable Set [
             Name: %dwell_time
             To: %par1
             Structure Output (JSON, etc): On ]
            If  [ %par1 Set ]
        
        A6: Variable Set [
             Name: %loop_control
             To: %par2
             Structure Output (JSON, etc): On ]
            If  [ %par2 Set ]
        
        A7: Multiple Variables Set [
             Names: %seconds|%milliseconds
             Variable Names Splitter: |
             Values: %dwell_time
             Values Splitter: |
             Structure Output (JSON, etc): On ]
        
        A8: Variable Set [
             Name: %idx
             To: 0
             Structure Output (JSON, etc): On ]
        
        <Wait loop.>
        A9: If [ %idx < %loop_control ]
        
            A10: Perform Task [
                  Name: Wait Functions: Wait
                  Priority: %priority
                  Parameter 1 (%par1): %milliseconds
                  Parameter 2 (%par2): %seconds
                  Structure Output (JSON, etc): On ]
        
            A11: Variable Set [
                  Name: %idx
                  To: %idx+1
                  Do Maths: On
                  Max Rounding Digits: 0
                  Structure Output (JSON, etc): On ]
        
            A12: Goto [
                  Type: Action Label
                  Label: Wait loop. ]
        
        A13: End If
        
       
