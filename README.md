# GPSMapProject — Embedded Linux GPS Navigation System

This project was developed as the **final project for Embedded Systems & Embedded Linux Development Class**. It implements a **GPS-based navigation system** running on an ARM/Linux board. The system loads custom map data (latitude/longitude), constructs a road network, displays live GPS coordinates, and calculates the **shortest path** between a start and end point.

---

## 🚀 Key Features

* Displays **real-time latitude and longitude** while moving.
* Divides the map into blocks and loads only the relevant block for efficiency.
* Implements a **Start/Stop workflow**:
  * **Start Button**: Captures current GPS position, saves it to `/data/map/start.txt`, and marks it on the map.
  * **Stop Button**: Captures end point, finds the shortest route, and marks it on the map.
* Calculates routes using **Floyd–Warshall shortest path algorithm**.
* Supports **power-loss recovery** by saving the start position; when the system reboots, the route can be recalculated automatically.

---

## 📂 Data Files

* **`node.txt`** — Stores all map nodes:
* **`graph.txt`** — Adjacency matrix representing road connectivity (`1 = connected, 0 = not connected`).
* **`start.txt`** — Persists start position for recovery after reboot.

---

## 🧠 How It Works

1. **GPS Reader**: Continuously updates current latitude/longitude.
2. **Start Capture**: Saves starting position in `start.txt`.
3. **End Capture**: Captures end position, finds nearest nodes, and calculates the route.
4. **Routing Algorithm**:
 * Reads nodes from `node.txt`.
 * Reads graph connectivity from `graph.txt`.
 * Maps start/end points to nearest collected nodes.
 * Applies **Floyd–Warshall** to compute the shortest path.
 * Returns the route as a list of nodes (`pathNodes`) to display.


