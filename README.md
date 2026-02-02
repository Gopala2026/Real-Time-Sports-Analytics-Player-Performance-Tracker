# Real-Time Sports Analytics — Player Performance Tracker

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.29%2B-red)](https://streamlit.io/)
[![SQLite](https://img.shields.io/badge/SQLite-3-green)](https://www.sqlite.org/)

> **End-to-End Data Analytics Project** for tracking real-time football player and team performance.

---

## Quick Start

```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Configure API key
cp .env.example .env
# Edit .env and add your Football-Data.org API key

# 3. Fetch initial data (optional - can also use dashboard button)
python src/fetch_data.py

# 4. Launch dashboard
streamlit run src/app.py
```

Dashboard opens at: **http://localhost:8501**

---

## Overview

**Real-Time Sports Analytics** is a complete data analytics pipeline that:

- **Fetches** live football data from Football-Data.org API
- **Stores** match and player statistics in SQLite database
- **Analyzes** performance metrics (efficiency, involvement, form)
- **Visualizes** insights through interactive Streamlit dashboard
- **Automates** data updates every 10 minutes

### Business Value

Enables coaches and analysts to:
- Monitor player performance trends in real-time
- Identify declining performance or fatigue indicators
- Compare team and player statistics
- Make data-driven tactical decisions

---

## Project Structure
```
project_3/
├── data/
│   ├── snapshots/          # Raw API responses (JSON)
│   ├── logs/               # Application logs
│   └── sports.db           # SQLite database
├── src/
│   ├── fetch_data.py       # API data fetcher
│   ├── process_data.py     # Data processing & ETL
│   ├── db_utils.py         # Database operations
│   ├── app.py              # Streamlit dashboard
│   └── scheduler.py        # Automated scheduling
├── notebooks/
│   ├── 01_explore_api.ipynb    # API exploration
│   └── 02_data_prep.ipynb      # Data analysis & EDA
├── sql/
│   └── schema.sql          # Database schema
├── reports/
│   └── insights_summary.md # Key findings
├── .env.example            # Environment template
├── requirements.txt        # Dependencies
└── README.md               # This file
```

---

## Installation

### Prerequisites

- **Python 3.8+**
- **pip** package manager
- **Football-Data.org API Key** ([Get free key](https://www.football-data.org/client/register))

### Setup Steps

1. **Clone repository** (if not already done)
   ```bash
   cd project_3
   ```

2. **Create virtual environment** (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment**
   ```bash
   cp .env.example .env
   # Edit .env and set FOOTBALL_API_KEY=your_actual_key
   ```

---

## Usage

### Option 1: Dashboard Only

```bash
streamlit run src/app.py
```

- Use **"Fetch Latest Data"** button in sidebar to get data from API
- Dashboard will display available data from database

### Option 2: Fetch Data First

```bash
# Fetch data once
python src/fetch_data.py

# Then launch dashboard
streamlit run src/app.py
```

### Option 3: Automated Scheduling

```bash
# Start scheduler (fetches every 10 minutes)
python src/scheduler.py

# In another terminal, launch dashboard
streamlit run src/app.py
```

**Advanced scheduler options:**
```bash
# One-time fetch
python src/scheduler.py --once

# Custom interval (30 minutes)
python src/scheduler.py --interval 30
```

---

## Dashboard Features

### Key Sections

| Section | Description |
|---------|-------------|
| **KPI Cards** | Total matches, goals, assists, average efficiency |
| **Top Performers** | Leaderboard of best players by goals/assists |
| **Performance Overview** | Goals vs Assists scatter plot |
| **Team Comparison** | Bar chart of team performance |
| **Trend Analysis** | Performance metrics over time |
| **Workload Analysis** | Minutes played vs efficiency |
| **Insights** | Automated findings and recommendations |

### Interactive Features

- **Sidebar Filters**: Team, player, date range
- **Manual Refresh**: Update data on demand
- **Fetch Data**: Pull latest from API directly
- **Hover Tooltips**: Detailed info on charts
- **Responsive Design**: Works on desktop and mobile
---

## Analytics Metrics

### Calculated KPIs

| Metric | Formula | Purpose |
|--------|---------|---------|
| **Efficiency** | `(goals + assists) / minutes_played` | Measure scoring contribution per minute |
| **Involvement Rate** | `(shots + passes) / minutes_played` | Measure active participation |
| **Form Score** | `rolling_avg(efficiency, 5 matches)` | Track performance trends |

### Data Sources

- **Competitions**: Premier League, Champions League, and more
- **Match Data**: Scores, dates, teams, status
- **Team Data**: Names, standings, statistics
- **Player Data**: Top scorers, assists (free tier limitation)

---

## Technical Stack

| Component | Technology |
|-----------|------------|
| **Language** | Python 3.8+ |
| **API** | Football-Data.org v4 |
| **Database** | SQLite |
| **ORM** | SQLAlchemy |
| **Dashboard** | Streamlit |
| **Visualization** | Plotly, Altair |
| **Data Processing** | Pandas, NumPy |
| **Scheduling** | schedule library |
| **Environment** | python-dotenv |

---

### Jupyter Notebooks

Explore data interactively:
```bash
jupyter notebook notebooks/01_explore_api.ipynb
jupyter notebook notebooks/02_data_prep.ipynb
```

---

## Business Questions Answered

1. **Which players show declining performance?**
   - Track form scores in Trend Analysis section

2. **How does workload affect efficiency?**
   - View Workload Analysis bubble chart

3. **Can we monitor team momentum?**
   - Use Team Comparison and temporal trends

4. **Who are top performers?**
   - See Top Performers leaderboard

---

## Acknowledgments

- **Football-Data.org** for the excellent API
- **Streamlit** for the dashboard framework
- **Plotly** for interactive visualizations

---
