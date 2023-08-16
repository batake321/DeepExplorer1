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
$$


For X-Axis movement, calculate is following

$$
\left[\begin{matrix}
1 & 0 & 0
\end{matrix}\right]
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
$$


