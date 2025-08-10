```markdown
```
# Manufacturing AMR Dispatch & Production Line Efficiency Analysis

## 📌 Project Overview
This project simulates **AMR (Autonomous Mobile Robot) task dispatch** and **manufacturing work order processing** data.  
It is designed for SQL / Python / Power BI practice, covering:
- AMR task waiting time, travel time, and service time analysis
- Production line OEE, bottleneck identification, and rework rate calculation
- Dashboard design and KPI monitoring

The dataset consists of three CSV files:
1. `amr_tasks.csv` — AMR task records
2. `work_orders.csv` — Work order process records
3. `stations.csv` — Static parameters of workstations

## 📂 Project Structure

```

.
├── data/
│   ├── amr\_tasks.csv      # AMR task records
│   ├── work\_orders.csv    # Work order process records
│   └── stations.csv       # Workstation master data
├── notebooks/             # SQL & Python analysis notebooks
├── dashboard/             # Power BI or Streamlit dashboards
├── src/                   # Data cleaning & KPI calculation scripts
└── README.md


```
## 📊 Data Dictionary

### 1. `amr_tasks.csv` — AMR Task Records
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| task_id | Integer | Unique task ID | 1523 |
| created_at | Datetime | Task creation time (request generated) | 2025-06-05 08:13:24 |
| assigned_at | Datetime | Time task is assigned to an AMR | 2025-06-05 08:13:54 |
| start_move_at | Datetime | AMR starts moving | 2025-06-05 08:14:04 |
| arrived_at | Datetime | AMR arrives at destination | 2025-06-05 08:15:33 |
| start_service_at | Datetime | Start of loading/unloading/docking | 2025-06-05 08:15:38 |
| end_service_at | Datetime | Completion of loading/unloading/docking | 2025-06-05 08:16:35 |
| from_node | String | Task origin node | N03 |
| to_node | String | Task destination node | N14 |
| distance_m | Float | Travel distance in meters | 78.5 |
| robot_id | String | AMR ID | R2 |
| status | String | Task status (`done`/`cancelled`/`failed`) | done |

---

### 2. `work_orders.csv` — Work Order Process Records
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| wo_id | Integer | Work order ID (appears multiple times for different stations) | 100123 |
| line_id | String | Production line ID | L1 |
| station_id | String | Workstation ID (refer to `stations.csv`) | S03 |
| op_seq | Integer | Operation sequence number within this work order | 2 |
| start_ts | Datetime | Process start time | 2025-06-08 08:45:00 |
| end_ts | Datetime | Process end time | 2025-06-08 08:46:25 |
| good_qty | Integer | Quantity of good units produced | 1 |
| scrap_qty | Integer | Quantity of scrapped units | 0 |
| rework_flag | Integer | Rework flag (1 = rework, 0 = normal) | 0 |

---

### 3. `stations.csv` — Workstation Master Data
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| station_id | String | Unique workstation ID | S03 |
| line_id | String | Production line ID | L1 |
| name | String | Workstation name | L1-Station-3 |
| takt_sec | Float | Ideal cycle time in seconds | 78.72 |
| availability | Float | Availability rate (0–1) | 0.882 |
| defect_rate | Float | Average defect rate (0–1) | 0.0155 |
| mtbf_hr | Float | Mean Time Between Failures (hours) | 54.89 |
| mttr_min | Float | Mean Time To Repair (minutes) | 29.1 |

---

## 📈 Practice Ideas

### SQL Exercises
1. Daily AMR task volume
2. Average waiting time (`assigned_at - created_at`)
3. Average cycle time per station
4. Identify bottleneck station (highest average cycle time)
5. Compare OEE between day and night shifts

### Python Exercises
- Use Pandas to calculate KPIs (waiting ratio, utilization, FPY, RTY)
- Visualize trends and heatmaps with Matplotlib / Seaborn
- Build interactive charts with Plotly

---

## 📊 Dashboard Showcase
- **Power BI**: `dashboard/factory_dashboard.pbix` (add screenshots here)
- **Streamlit**: [Live Demo Link](https://your-streamlit-app-link)

---

## 🚀 How to Use
1. Clone the project
```bash
git clone https://github.com/WenRu-Chen/amr-manufacturing-analytics.git
cd amr-manufacturing-analytics
````

2. Install dependencies

```bash
pip install pandas matplotlib seaborn plotly duckdb
```

3. Open a Notebook or Power BI file and load CSV files from `data/` for analysis

---

## 📌 Author

* **CHEN WEN RU / WenRu-Chen**
* Email: [spi890012@gmail.com](mailto:spi890012@gmail.com)

