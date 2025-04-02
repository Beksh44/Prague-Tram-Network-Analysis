### Prague Tram Network Analysis

This project explores the structure of Prague’s public transport network by analyzing data from **tram routes**. The dataset is based on General Transit Feed Specification (GTFS) and focuses on stops and connections between them.

We work with a pre-processed dataset `d.csv`(official dataset from PID) that includes pairs of consecutively visited tram stops, their times, and other metadata.

---

### 📁 Dataset Overview

Each row represents a direct connection between two stops of a tram line. Key columns include:

- `stop_from`, `stop_to`: IDs of the two consecutive stops  
- `stop_from_name`, `stop_to_name`: Human-readable names of the stops  
- `depart_from`, `arrive_to`: Scheduled time of departure and arrival  
- `route_type`: Identifies the type of transport (3 = tram)  
- `is_night`: Whether it’s a night route  
- `mon`, `tue`, ..., `sun`: Indicators of which day(s) the route is active

The times may exceed 24 hours (e.g. `25:00:00`), which required correction using modulo 24.

---

### 🧹 Data Preprocessing

- Time columns (`depart_from`, `arrive_to`) were converted from strings into numerical time representations.  
- Values over 24 hours were wrapped using `modulo 24` to represent them in daily time format.  
- Only **tram lines** (`route_type == 3`) were included in this analysis.

---

### 🌐 Network Construction

The network was modeled using `NetworkX`, where:

- **Nodes** are stops
- **Edges** represent direct travel between stops
- **Edge weights** are based on the number of trips that connect those stops in a typical week

---

### 📊 Visualization

A complete graph of Prague tram routes was visualized. Nodes were plotted based on their geographic coordinates using the data from `stops.txt` (latitude and longitude). This helps understand the structure and connectivity of the tram system across the city.

---

### 📈 Centrality Analysis

Several centrality measures were calculated to identify the most important stops:

- **Degree centrality**
- **Betweenness centrality**
- **Closeness centrality**

Each measure was visualized.
---

### ❓ Some custom Questions Explored

- What are the most overloaded stops??
- how does traffic activity vary throughout the day and what are the peak hours?
- What proportion of traffic occurs during night versus day?

Each question was addressed using custom visualizations and graph metrics.

---

### 🗺️ Bonus: Geographic Analysis

Using the `stops.txt` file, each stop’s **latitude and longitude** was used for spatial plotting. This enabled geographic layout of the network and enhanced readability of visualizations.

---

### ✅ Summary

This project involved building and analyzing a directed weighted graph of Prague’s tram network. Using NetworkX and visual tools, we identified key nodes, explored traffic patterns, and visualized the structure of public transportation in the city.

