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

Pitch
A = 
\begin{matrix} 
a & b \\ 
c & d 
\end{matrix}


Yaw



Roll

A=\left[\begin{matrix} a & b \\ c & d \end{matrix}\right]

