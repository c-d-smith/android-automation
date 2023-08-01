    Tasks
        Task: Swipe Functions: Vertical
        
        <Coordinates are passed as a comma delimited string using this pattern: X,Y1,Y2.<br><br>
        
        Y1 doesn't need to be smaller than Y2. If Y1 is larger, Tasker will swipe up; else it will swipe down.>
        A1: Variable Set [
             Name: %coords
             To: %par1
             Structure Output (JSON, etc): On ]
        
        A2: Variable Split [
             Name: %coords
             Splitter: ,
             Delete Base: On ]
        
        A3: Variable Set [
             Name: %duration
             To: %par2
             Structure Output (JSON, etc): On ]
        
        A4: Variable Set [
             Name: %coord1
             To: %coords(1),%coords(2)
             Structure Output (JSON, etc): On ]
        
        A5: Variable Set [
             Name: %coord2
             To: %coords(1),%coords(3)
             Structure Output (JSON, etc): On ]
        
        A6: AutoInput Gestures [
             Configuration: Gesture Type: Swipe
             Manage Accessibility Service: Unchanged
             Start Point: %coord1
             End Point: %coord2
             Duration: %duration
             Timeout (Seconds): 1
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Swipe Functions: Horizontal
        
        <Coordinates are passed as a comma delimited string using this pattern: X1,X2,Y.<br><br>
        
        X1 doesn't need to be smaller than X2. If X1 is larger, Tasker will swipe left; else it will swipe right.>
        A1: Variable Set [
             Name: %coords
             To: %par1
             Structure Output (JSON, etc): On ]
        
        A2: Variable Split [
             Name: %coords
             Splitter: ,
             Delete Base: On ]
        
        A3: Variable Set [
             Name: %duration
             To: %par2
             Structure Output (JSON, etc): On ]
        
        A4: Variable Set [
             Name: %coord1
             To: %coords(1),%coords(3)
             Structure Output (JSON, etc): On ]
        
        A5: Variable Set [
             Name: %coord2
             To: %coords(2),%coords(3)
             Structure Output (JSON, etc): On ]
        
        A6: AutoInput Gestures [
             Configuration: Gesture Type: Swipe
             Start Point: %coord1
             End Point: %coord2
             Duration: %duration
             Timeout (Seconds): 0
             Structure Output (JSON, etc): On ]
        
        
    
        Task: Swipe Functions: Clear Single App
        
        <Wait 1s.>
        A1: Perform Task [
             Name: Wait Functions: Main
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        A2: Show Recents
        
        <Wait 1s.>
        A3: Perform Task [
             Name: Wait Functions: Main
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        A4: Perform Task [
             Name: Swipe Functions: Vertical
             Priority: %priority
             Parameter 1 (%par1): 500,1200,800
             Parameter 2 (%par2): 25
             Structure Output (JSON, etc): On ]
        
        <Wait 1s.>
        A5: Perform Task [
             Name: Wait Functions: Main
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        A6: AutoInput Action [
             Configuration: Type: Point
             Value: 700,1625
             Action : Click
             Timeout (Seconds): 0
             Structure Output (JSON, etc): On ]
        
        <Wait 1s.>
        A7: Perform Task [
             Name: Wait Functions: Main
             Priority: %priority
             Structure Output (JSON, etc): On ]
        
        
