---

---

# DeepExplorer1
Starbase Ship Project ( Deep Space Explorer Ship )

## about

This ship is for NavigationDataLogger.
Max Speed : 140+ m/s
Ranges : over 3000Km

## Ores

need following ores

| Ores            | Value      | Stack        |
| --------------- | ---------- | ------------ |
| Aegisium        | 156,723 kv | 90.7 Stacks  |
| Ajatite         | 594,80 kv  | 34.4 Stacks  |
| Arkanium        | 33,169 kv  | 19.2 Stacks  |
| Bastium         | 213,681 kv | 123.7 Stacks |
| Bastonium Alloy | 409 kv     | 0.2 Stacks   |
| Charodium       | 235,664 kv | 136.4 Stacks |
| Corazium        | 6,597 kv   | 3.8 Stacks   |
| Exorium         | 16,510 kv  | 9.6 Stacks   |
| Glass           | 16,976 kv  | 9.8 Stacks   |
| Ice             | 168,000    | 97.2 Stacks  |
| Karnite         | 25,208 kv  | 14.6 Stacks  |
| Kutonium        | 51,269 kv  | 29.7 Stacks  |
| Lukium          | 44,995 kv  | 56.9 Stacks  |
| Valkite         | 38 kv      | 0.0 Stacks   |
| Vokarium        | 132,866 kv | 76.9 Stacks  |
| Xhalium         | 1,265 kv   | 0.7 Stacks   |
| Ymrium          | 33,131 kv  | 19.2 Stacks  |



## Cost

 Assembly : 443,106cr
 Manufacturing : 1,187,518Cr
 Total : 1,630,624Cr

## Functions

Functions

- AutoCruise

  Forward specified distance ( positive integer / unit:Km )

- AutoTurn

  Turn specified Yaw / Pitch / Roll Angle ( integer /unit:gegree )

- AutoReturn

  Automatically return to HomePosition

- CruiseHead

  Auto turn head to cruise primary angle

- HomeHead

  Auto turn head to HomePosition primary angle

- ThrustCalibration

  If push "Cal" button, thrust Yaw / Pitch /Roll thrusters (both direction) and check angle value with thrust

- Turtle

  Limit Forward Thrust

- Sense

  Limit Yaw / Pitch / Roll Thrust

- AvoidanceSystem

  muti functions : SoundOnly / PitchUpDown / PitchUpDown + reduce speed (VerySlow / Turtle) / Stop

  when pitch up or down or reduce speed, after fly 1Km, resume angle and speed

- Transponder

  Transponder On / Off and display status

- SettingTubs

  easy to change settings. AvoidanceSystem / ThrusterSetting

- GeneratorPowerControl

   3 modes. Stop( with AvoidanceSystem,NavigationLogger, and Lights ) / Eco ( Save power ) / FullPower

- EmagencyStop

  If find something within specified distance, stop automatically.

- ReconstructionMachine

  for endoschelton

- NavigationLogger

  for Capital ship

- MultiDIsplay

- DoorOpenWarning

- GeneratorFullWorkingWard

## HowToUse

#### Home

Push "Home" button. Automatically calculate heading and distance of HomePosition. After fix heading, forward to home position.

#### input numbers

push mumeric keys ( left side of main panel )
Number will display on "Number" progress bar.
If you want to enter minus, push "+/-" key after entering numeric keys
"Clear" key : Clear number
"BS" key : backspace key. delete last letter of number.

#### Auto Cruise

1. push mumeric keys
2. Push function Button  "Fwd"

#### Auto Pitch

1. push mumeric keys
2. Push function Button "Pch"

#### Auto Yaw

1. push mumeric keys
2. Push function Button "Pch"

#### Auto Roll

1. push mumeric keys
2. Push function Button "Rol"
If push "Pitch", "Yaw", "Roll" or "Home" buttons, reset to  (x,y,z) =(0,0,0) and ship calculate movement.

## Logic for Angle and location

Starbase Eular Order is Pitch -> Roll -> yaw.

Detail is in [Angle](Manuals/Angle.md) page



manulas/Angle.md

