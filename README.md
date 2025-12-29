## Autonomous Multi Drone System 

### How to Run the Code


**Step 1**

cd into the MRS_UAV three_drones system 
```bash
./tmux/start.sh
```
**Step2**

Ctrl+t in the terminal -

```bash
roscd example_multi_uav_coordination  
roslaunch example_multi_uav_coordination multi_uav_coordination.launch
```


When ready, call the service prepared in the bottom terminal window for generating the trajectory:
```bash
rosservice call /$UAV_NAME/multi_uav_coordination/start 3.0
```
uav1
uav2
uav3

### Overview
- Built and tested a **distributed multi-drone coordination system** in simulation (**Gazebo + RViz**) using **Python and ROS**.
- **Goal:** Enable search-and-rescue style coordination **without a ground station** when communication is unreliable.

### Problem
- Typical drone swarms rely on a **ground station** for coordination.
- In dangerous environments like forest-fires and floods, the ground-station link can fail when signals get poor, requiring drones to **share detections and regroup autonomously** in search and rescue missions.

### What I built
- **Area-partitioning search**
  - Split the search region across drones to reduce redundant coverage and improve time to locate the target.
- **Drone-to-drone wireless communication setup**
  - Implemented an **IP-based messaging layer** with ROS nodes in Python.
  - When one drone detects a target, it **broadcasts the target location** so other drones can converge autonomously.
- **Machine Vision-based target localization**
  - Used the drone’s **camera view** to estimate the target’s location and convert it into a shared reference frame.
  - Enabled team-wide convergence by distributing (x, y, z) target coordinates.

### Validation
- Tested end-to-end in simulation: **search → detect → localize → broadcast → converge**
  

### Tools & Technologies
- **Programming:** Python  
- **Robotics Middleware:** ROS (Robot Operating System)  
- **Simulation:** Gazebo  
- **Visualization & Debugging:** RViz  
- **Networking:** IP-based inter-drone communication  
- **Perception:** Camera-based target detection and localization using OpenCV and Image Processing

### Summer Research Symposium
- Poster
  <img width="720" height="541" alt="image" src="https://github.com/user-attachments/assets/3b8b0ed4-a5d6-4334-9cf6-2cc9e8cba4bd" />

More pictures coming soon !


