# 🚘 Urban Parking Dynamic Pricing Solution

**Leveraging Live Demand, Congestion, and Competition for Smarter Parking**

## 📚 Overview

Parking in cities is a constantly shifting challenge. Traditional fixed pricing often causes empty lots or overcrowding. This project delivers a **Dynamic Parking Pricing Engine** that adapts prices in real time using live data (occupancy, traffic, queues, and nearby competitors), simulates user flow, and reroutes vehicles when lots are full.

---

## 🥅 Project Goals

- Develop **three dynamic pricing strategies**: simple linear, demand-driven, and location-aware competitive models.
- Emulate **real-time price updates** as parking demand fluctuates.
- Integrate **rerouting logic** to guide drivers to available lots when one is full.
- Present pricing and rerouting visually with Bokeh charts.

---

## 🧰 Tools & Libraries

- **Python**
- **Pandas** (for data wrangling)
- **NumPy** (for calculations)
- **Bokeh** (for interactive charts)
- **Pathway** (for streaming and simulation)

---

## 🗂️ Data Description

The dataset mimics real-world parking sensor feeds and contains:

- **Lot ID**: Unique code for each parking area
- **Capacity**: Total parking spots
- **Occupancy**: Number of vehicles currently parked
- **Queue Length**: Vehicles waiting for entry
- **Vehicle Type**: (car, bike, truck, cycle)
- **Nearby Traffic**: Encoded congestion level
- **Special Day**: Flag for holidays/weekends
- **Timestamp**: Combined date and time
- **Latitude & Longitude**: For distance-based logic (Model 3)

---

## 🧪 Data Preparation & Feature Creation

- **Timestamp Generation**: Merge date and time columns
- **Occupancy Rate**: Calculate as `occupancy / capacity`
- **Queue Scaling**: Normalize queue values
- **Categorical Encoding**: Convert traffic and special day to numbers
- **Vehicle Weighting**: Assign impact factors to vehicle types
- **Distance Matrix**: Use Haversine formula for proximity

---

## 🧩 Pricing Algorithms

### 1️⃣ Linear Model (Occupancy-Based)
- Price rises in direct proportion to occupancy
- Formula: `price = base_price + α × (occupancy / capacity)`

### 2️⃣ Demand-Weighted Model
- Price reflects a combined score (occupancy, queue, traffic, special day, vehicle type)
- Formula: `price = base_price × (1 + λ × normalized_demand_score)`

### 3️⃣ Geo-Competitive Model with Rerouting
- Adjusts price based on nearby lots (within 1 km) and reroutes if full
- Uses geospatial logic to find alternatives

---

## ⏳ Streaming Simulation

- Data is processed in chronological order
- Each entry updates lot status and recalculates price
- Rerouting is activated if a lot is full and cheaper options are close
- Bokeh charts display the evolving results

---

## 📈 Visualization

- All plots are created with **Bokeh** inside the notebook
- Includes time series for price trends and competitor comparisons

---

## 📦 Installation

Install the required Python packages:

```bash
pip install pandas numpy bokeh pathway
```

---

## 🙏 Credits

Created for the Summer Analytics Course 2025 at **IIT Guwahati**.

Thanks to:
- **Pathway** for streaming tools
- **OpenStreetMap** for geospatial data
- **Bokeh** for visualization
