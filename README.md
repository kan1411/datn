# UAV-Based Search and Rescue Simulation using NS-3 and Deep Q-Learning (Mo phong kich ban tham gia tim kiem cuu ho của drone su dung ns3 ket hop deep q-learning)

This project simulates a UAV conducting a **Search and Rescue (SAR)** operation in a 3D environment. The drone's movement is controlled using the **Deep Q-Learning** (DQL) algorithm, while **NS-3** is used to simulate wireless communication with a base station over **WiFi 802.11a** using the **UDP** protocol.

##  Main Components

- **Drone (UAV):** Moves in 3D space to locate the target using Deep Q-Learning.
- **Target:** A fixed position in space that the drone must find.
- **Base Station:** Communicates with the drone via UDP, receives periodic updates.
- **Communication:** Simulated using WiFi 802.11a, with support for packet loss/noise.

## 🛠 Requirements

- **NS-3.39 or higher** (tested with NS-3.37)
- **Python 3.8+**
- **PyTorch** (for DQL training)
- **C++ Compiler (e.g. g++)**
- **NetAnim** and **NetSimulyzer** for visualization
- Optional: `matplotlib`, `numpy` for result analysis

## 🔧 Installation & Setup

### 1. NS-3 Installation

Follow instructions from the [official NS-3 website](https://www.nsnam.org/wiki/Installation) or use:

```bash
git clone https://gitlab.com/nsnam/ns-3-dev.git
cd ns-3-dev
./ns3 configure --enable-examples --enable-tests
./ns3 build
```
Install NetAnim and NetSimulyzer if not already available.

### 2. Train Deep Q-Learning Model
```bash
cd sar_project
python deepqlearning.py
```
This will train the model and export q_table_drone_search.txt for use in NS-3.

## 3. Run the NS-3 Simulation
Place the Q-table (q_table_drone_search.txt) in the simulation directory and run:

```bash
cd build
cmake ..
make -j4
./ns3 run scratch/sar_drone_test3.cc  
```
Make sure the .cc file (sar_drone_test3.cc) is placed in scratch/.

## 4. Visualization
Use NetAnim to open the generated drone_animation.xml file.

Use NetSimulyzer to open drone_simulation_log.json and visualize the 3D movement.


📁 File Structure
.
finalproject/
├── NetSimulyzer/
├── ns-allinone-3.37/
│   └── ns-3.37/
│       └── scratch/
│           ├── sar_drone_test2.cc
│           └── sar_drone_test3.cc
└── sar_project/
    └── deepqlearning.py

🔍 Reference
Based on implementation guide from:
[Simulation of UAV-Based Search and Rescue Scenario with NS-3](https://www.projectguideline.com/simulation-of-uav-based-search-and-rescue-scenario-with-ns-3/)
