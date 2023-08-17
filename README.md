---

---

# DeepExplorer1
Starbase Ship Project ( Deep Space Explorer Ship )

## About Axis

with using 3 gyroscope, use 3 axis.

- Home position
- Cruise Position
- Current Position

### Details

#### Home Position

for "Home" Button. If push "Home Button", return to (x,y,z) =(0,0,0) on this axis.

#### Cruise Position

If push "Forward" button for cruising to forward,  Home Position is reset to (x,y,z) =(0,0,0).

#### Current Position

If push "Pitch", "Yaw", "Roll" or "Home" buttons, reset to  (x,y,z) =(0,0,0) and ship calculate movement.

### Logic (location from gyroscope and speed)

Starbase Eular Order is Pitch -> Roll -> yaw.

Queue is following.

Each rotations

**Pitch**

$$
\left[\begin{matrix}
\cos(Pitch) & 0 & \sin(Pitch)
\\
0 & 1 & 0
\\
-\sin(Pitch) & 0 & \cos(Pitch)
\end{matrix}\right]
$$

**Yaw**

$$
\left[\begin{matrix}
\cos(Yaw) & -\sin(Yaw) & 0
\\
\sin(Yaw) & \cos(Yaw) & 0
\\
0 & 0 & 1
\end{matrix}\right]
$$

Roll

$$
\left[\begin{matrix}
1 & 0 & 0
\\
0 & \cos(Roll) & -\sin(Roll)
\\
0 & \sin(Roll) & \cos(Roll)
\end{matrix}\right]
$$

Translate


$$
\left[\begin{matrix}
\cos(Pitch) & 0 & \sin(Pitch)
\\
0 & 1 & 0
\\
-\sin(Pitch) & 0 & \cos(Pitch)
\end{matrix}\right]
\left[\begin{matrix}
\cos(Yaw) & -\sin(Yaw) & 0
\\
\sin(Yaw) & \cos(Yaw) & 0
\\
0 & 0 & 1
\end{matrix}\right]
\left[\begin{matrix}
\cos(Yaw) & -\sin(Yaw) & 0
\\
\sin(Yaw) & \cos(Yaw) & 0
\\
0 & 0 & 1
\end{matrix}\right]
\\
=\left[\begin{matrix}
-\cos(Pitch) & \sin(Pitch)\sin(Roll) & \sin(Pitch)\cos(Roll)
\\
0 & \cos(Roll) & -\sin(Pitch)
\\
-\sin(Roll) & cos(Pitch)\sin(Roll) & \cos(Roll)\cos(Pitch)
\end{matrix}\right]
\times
\left[\begin{matrix}
\cos(Yaw) & -\sin(Yaw) & 0
\\
\sin(Yaw) & \cos(Yaw) & 0
\\
0 & 0 & 1
\end{matrix}\right]
\\
=\left[\begin{matrix}
\cos(Pitch)\cos(Yaw)-\sin(Roll)\sin(Pitch)\sin(Yaw) & -\cos(Roll)\sin(Yaw)+\sin(Roll)\sin(Pitch)\cos(Yaw) & \sin(Roll)\cos(Pitch)
\\
\cos(Pitch)\sin(Yaw) & \cos(Pitch)\cos(Yaw) & -sin(Pitch)
\\
-\sin(Roll)\cos(Yaw)+\cos(Roll)\sin(Pitch) & \sin(Roll)\sin(Yaw)+\cos(Roll)\sin(Pitch)\cos(Yaw) & \cos(Roll)\cos(Pitch)
\end{matrix}\right]
$$

For X-Axis movement, calculate is following

$$
\left[\begin{matrix}
1 & 0 & 0
\end{matrix}\right]
\times
\left[\begin{matrix}
\cos(Pitch)\cos(Yaw)-\sin(Roll)\sin(Pitch)\sin(Yaw) & -\cos(Roll)\sin(Yaw)+\sin(Roll)\sin(Pitch)\cos(Yaw) & \sin(Roll)\cos(Pitch)
\\
\cos(Pitch)\sin(Yaw) & \cos(Pitch)\cos(Yaw) & -sin(Pitch)
\\
-\sin(Roll)\cos(Yaw)+\cos(Roll)\sin(Pitch) & \sin(Roll)\sin(Yaw)+\cos(Roll)\sin(Pitch)\cos(Yaw) & \cos(Roll)\cos(Pitch)
\end{matrix}\right]
$$

For Y-Axis movement, calculate is following

$$
\left[\begin{matrix}
0 & 1 & 0
\end{matrix}\right]
\times
\left[\begin{matrix}
\cos(Pitch)\cos(Yaw)-\sin(Roll)\sin(Pitch)\sin(Yaw) & -\cos(Roll)\sin(Yaw)+\sin(Roll)\sin(Pitch)\cos(Yaw) & \sin(Roll)\cos(Pitch)
\\
\cos(Pitch)\sin(Yaw) & \cos(Pitch)\cos(Yaw) & -sin(Pitch)
\\
-\sin(Roll)\cos(Yaw)+\cos(Roll)\sin(Pitch) & \sin(Roll)\sin(Yaw)+\cos(Roll)\sin(Pitch)\cos(Yaw) & \cos(Roll)\cos(Pitch)
\end{matrix}\right]
$$

For Z-Axis movement, calculate is following

$$
\left[\begin{matrix}
0 & 0 & 1
\end{matrix}\right]
\times
\left[\begin{matrix}
\cos(Pitch)\cos(Yaw)-\sin(Roll)\sin(Pitch)\sin(Yaw) & -\cos(Roll)\sin(Yaw)+\sin(Roll)\sin(Pitch)\cos(Yaw) & \sin(Roll)\cos(Pitch)
\\
\cos(Pitch)\sin(Yaw) & \cos(Pitch)\cos(Yaw) & -sin(Pitch)
\\
-\sin(Roll)\cos(Yaw)+\cos(Roll)\sin(Pitch) & \sin(Roll)\sin(Yaw)+\cos(Roll)\sin(Pitch)\cos(Yaw) & \cos(Roll)\cos(Pitch)
\end{matrix}\right]
$$



### Yolol code forTranslate Direction from Euler XYZ to Starbase axis

important: x -> Z Z->-X

```
e=cos :gP f=sin :gP a=cos -:gY b= sin -:gY c=cos :gR d=sin :gR
:sZx=:Xs*e*b :sXx=:Xs*c*a :sYx=:Xs*-d // X(HolizontalDirection)
:sZy=:Ys*(e*d-f*a) :sXy=:Ys*(f*b+e*d*a) :sYy=:Ys*e*c // Y(VerticalDirection)
:sZz=:Zs*(e*a+f*d*b) :sXz=:Zs*(f*d*a-e*b) :sYz=:Zs*f*c // Z(Forward)
:sZ=:sZx+:sZy+:sZz :sX=:sXx+:sXy+:sXz :sY=:sYx+:sYy+:sYz goto1
// gP:GyroPitch gY:GyroYow gR:GyroRoll
// Xs:Holizontal(Right+ Left-) speed by CargoFrameLockSpeedmeter
// Ys:Vertical(Up+ Down-) speed by CargoFrameLockSpeedmeter
// Zs:Forward speed by CargoFrameLockSpeedmeter
// sX (Total Rightward speed) sY (Total Upward speed) sZ (Total forward speed)
```





