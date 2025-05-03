#Persistent

clickInterval := 120        ; Time between clicks (ms)
loopInterval := 25000       ; Time between cycles (ms)
positions := [[500, 400], [600, 400], [700, 400], [800, 400]]  ; Replace with your coordinates

toggle := false

F8::  ; Press F8 to toggle the auto-clicker
toggle := !toggle
if (toggle) {
    SetTimer, ClickLoop, 0
    TrayTip, AutoClicker, Started, 1
} else {
    SetTimer, ClickLoop, Off
    TrayTip, AutoClicker, Stopped, 1
}
return

ClickLoop:
    for index, pos in positions {
        x := pos[1]
        y := pos[2]
        Click, %x%, %y%
        Sleep, %clickInterval%
    }
    Sleep, %loopInterval%
return
