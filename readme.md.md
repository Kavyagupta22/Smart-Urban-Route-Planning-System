# Smart Urban Route Planning System

A lightweight, native Win32 desktop application written in C++ that models an urban road network, simulates real-time traffic conditions, and calculates optimized travel routes using Dijkstra's shortest-path algorithm.

---

## Features

- **Optimal Pathfinding**: Calculates the fastest route between urban locations using Dijkstra's algorithm based on distance, estimated travel time, and live traffic multipliers.
- **Dynamic Traffic Simulation**: Toggle through different realistic traffic scenarios (e.g., peak-hour congestion, major road closures, multi-segment bottlenecks).
- **Interactive Visual Map**: Graphical GDI-rendered canvas showing:
  - **Blue lines**: Active optimized route
  - **Orange lines**: Congested roads (traffic multiplier $\ge 1.7$)
  - **Red dashed lines**: Closed roads
  - **Colored nodes**: Green for origin, purple for destination, white for standard intersections
- **Detailed Road Condition Reports**: Real-time readout of total route distance, estimated travel time, and specific road condition warnings.
- **Native GUI**: Uses standard Windows controls (Comboboxes, Buttons, Static Labels, Edit boxes) with zero external library dependencies.

---

## Tech Stack & Dependencies

- **Language**: C++ (C++11 or higher)
- **GUI Framework**: Native Windows API (`<windows.h>`, Win32 GDI)
- **Standard Libraries**: `<vector>`, `<string>`, `<sstream>`, `<iomanip>`, `<algorithm>`, `<cstdio>`, `<cstring>`
- **Dependencies**: None (Uses standard Windows OS system libraries: `gdi32`, `user32`)

---

## Data Model & Graph Structure

The city network consists of **8 location nodes** and **12 bidirectional road segments**:

### Locations (Nodes)
1. **Central Station** `(70, 100)`
2. **City Hospital** `(210, 60)`
3. **University** `(350, 90)`
4. **Shopping Mall** `(490, 60)`
5. **Airport** `(570, 180)`
6. **Tech Park** `(400, 240)`
7. **Bus Terminal** `(220, 240)`
8. **Old Town** `(70, 260)`

### Road Metrics
Each road segment stores:
- **Base Distance**: Kilometers (`km`)
- **Base Time**: Standard travel time in minutes (`time`)
- **Traffic Multiplier**: Dynamic congestion scaling factor (`traffic`)
- **Status Flag**: Open / Closed boolean (`open`)

---

## Building and Compilation

### Using GCC / MinGW (Command Line)
```bash
g++ -O2 route_planner.cpp -o route_planner.exe -lgdi32 -luser32 -mwindows