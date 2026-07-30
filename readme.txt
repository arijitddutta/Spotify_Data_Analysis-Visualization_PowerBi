# 🎵 Spotify Global Top 50 — Power BI Dashboard

## 📊 Project Overview

This project is an interactive **Power BI dashboard** built to analyze Spotify's **Global Top 50 chart data** and uncover patterns in song popularity, artist performance, chart rankings, song characteristics, and trends over time.

The dataset contains daily Spotify Global Top 50 chart records, allowing the analysis to go beyond simple "Top 10 songs" reporting and explore **chart presence, song longevity, artist dominance, popularity, explicit content, track duration, and release trends**.

The primary goal of this project is to transform raw Spotify chart data into a **clean, interactive, and insight-driven business intelligence dashboard**.

---

## 🎯 Project Objectives

The dashboard aims to answer questions such as:

* Which songs dominated the Spotify Global Top 50?
* Which artists had the strongest presence on the chart?
* Which songs reached the #1 position?
* Which artists had the most songs in the Top 50?
* How does Spotify popularity vary across chart positions?
* Do explicit songs perform differently from non-explicit songs?
* How long do songs typically remain in the Global Top 50?
* What is the relationship between release age and chart performance?
* How has chart popularity changed over time?
* Are shorter or longer songs more common among successful tracks?

---

## 🗂️ Dataset

The project uses a Spotify Global Top 50 dataset containing **27,800 records** collected across **556 chart days**.

### Dataset Summary

| Metric              |                            Value |
| ------------------- | -------------------------------: |
| Total Chart Entries |                           27,800 |
| Distinct Songs      |                              794 |
| Distinct Artists    |                              343 |
| Chart Positions     |                             1–50 |
| Chart Period        | May 18, 2023 – November 27, 2024 |

### Main Columns

| Column            | Description                             |
| ----------------- | --------------------------------------- |
| `date`            | Date of the Spotify chart               |
| `position`        | Song's position in the Global Top 50    |
| `song`            | Track name                              |
| `artist`          | Artist name                             |
| `popularity`      | Spotify popularity score                |
| `duration_ms`     | Track duration in milliseconds          |
| `album_type`      | Album, single, or compilation           |
| `total_tracks`    | Number of tracks in the album           |
| `release_date`    | Release date of the album/track         |
| `is_explicit`     | Indicates whether the track is explicit |
| `album_cover_url` | URL of the album artwork                |

---

## 🛠️ Tools & Technologies

* **Power BI Desktop** — Dashboard development and visualization
* **Power Query** — Data cleaning and transformation
* **DAX** — Calculated measures and analytical calculations
* **DAX Studio** — Measure development and testing
* **GitHub** — Project documentation and version control

---

## 🧹 Data Preparation

Before building the dashboard, the dataset was reviewed and prepared for analysis.

The data preparation process included:

* Validating column data types
* Converting date fields to appropriate date formats
* Converting track duration from milliseconds to minutes
* Checking for missing values
* Validating Boolean values in `is_explicit`
* Reviewing categorical fields such as `album_type`
* Creating a dedicated **Date table**
* Establishing relationships between the Date table and the Spotify dataset

The final Power BI model was designed to support both **time-series analysis** and **song/artist-level analysis**.

---

## 🧮 DAX Measures

A dedicated `_Measure` table was created to organize the project's DAX measures.

Some of the key measures include:

### Core Metrics

* Total Chart Entries
* Distinct Songs
* Distinct Artists
* Average Popularity
* Average Position

### Chart Performance

* No.1 Chart Entries
* Distinct No.1 Songs
* Top 10 Entries
* Distinct Top 10 Songs
* Song Chart Appearances
* Song Chart Days
* Artist Chart Entries
* Distinct Songs per Artist

### Song Characteristics

* Average Duration
* Average Tracks per Album
* Explicit Entries
* Non-Explicit Entries
* % Explicit Entries
* Average Popularity of Explicit Songs
* Average Popularity of Non-Explicit Songs

### Time Analysis

* Average Popularity Change vs Previous Day
* Average Position Change vs Previous Day
* 7-Day Moving Average of Popularity
* Average Release Year
* Song Age

These measures allow the dashboard to move from simple descriptive statistics to more meaningful analytical insights.

---

## 📈 Dashboard Features

### 1. Executive Overview

The overview page provides a high-level summary of Spotify's Global Top 50.

Key elements include:

* Total chart entries
* Number of unique songs
* Number of unique artists
* Average popularity
* Average chart position
* Top-performing songs
* Leading artists
* Chart popularity trends

---

### 2. Song & Artist Analysis

This section focuses on identifying the songs and artists that dominate the chart.

Analysis includes:

* Most frequently appearing songs
* Artists with the highest chart presence
* Songs with the best average positions
* Most frequent Top 10 songs
* Artists with multiple songs in the Top 50
* Song longevity in the chart

---

### 3. Trend & Deep-Dive Analysis

The analytical section explores relationships between song characteristics and chart performance.

Potential analysis includes:

* Popularity trends over time
* 7-day moving average
* Explicit vs non-explicit performance
* Song duration analysis
* Release year analysis
* Older vs newer songs
* Album vs single performance
* Chart position distribution

---

## 🔍 Key Analytical Concepts

One of the important aspects of this project is distinguishing between **chart entries** and **unique songs**.

For example, a song appearing in the Global Top 50 for 100 different days creates:

> **100 chart entries**

but represents:

> **1 unique song**

This distinction is important when measuring:

* Song longevity
* Artist dominance
* Chart presence
* Number of unique songs reaching the Top 10
* Number of unique songs reaching #1

This approach helps avoid misleading conclusions from repeated daily chart records.

---

## 📊 Example Insights

The dashboard is designed to uncover insights such as:

* Which artists consistently maintain a presence in the Global Top 50?
* Which songs have the longest chart lifespan?
* How concentrated is the #1 position among songs and artists?
* Does higher Spotify popularity correspond to better chart positions?
* What percentage of chart entries are explicit?
* Are explicit tracks more or less popular on average?
* What type of releases dominate the chart?
* How quickly do newly released songs enter the Global Top 50?
* How does the average chart position change over time?

---

## 🏗️ Power BI Data Model

The model consists primarily of:

```text
              ┌───────────────┐
              │     Date      │
              │───────────────│
              │ Date          │
              │ Year          │
              │ Month         │
              │ Month Name    │
              │ Day           │
              └───────┬───────┘
                      │
                      │ 1 : *
                      │
              ┌───────▼──────────┐
              │  Top-50-World    │
              │──────────────────│
              │ date             │
              │ position         │
              │ song             │
              │ artist           │
              │ popularity       │
              │ duration_ms      │
              │ album_type       │
              │ release_date     │
              │ is_explicit      │
              └──────────────────┘

              ┌───────────────┐
              │    _Measure   │
              │───────────────│
              │ DAX Measures  │
              └───────────────┘
```

The `_Measure` table is used to keep analytical measures separate from the raw dataset and improve model organization.

---

## 🚀 Project Workflow

The project follows the following workflow:

```text
Raw Spotify Dataset
        ↓
Data Inspection
        ↓
Power Query Cleaning
        ↓
Data Type Validation
        ↓
Date Table Creation
        ↓
Data Model & Relationships
        ↓
DAX Measures
        ↓
Interactive Visualizations
        ↓
Dashboard Design
        ↓
Insight Generation
```

---

## 📁 Repository Structure

A suggested repository structure:

```text
Spotify-PowerBI-Dashboard/
│
├── README.md
│
├── Dataset/
│   └── spotify-top-50-world.csv
│
├── PowerBI/
│   └── Spotify_Global_Top50.pbix
│
├── DAX/
│   └── Spotify_Measures.dax
│
└── Screenshots/
    ├── dashboard-overview.png
    ├── song-analysis.png
    └── trends-analysis.png
```

---

## 🎨 Dashboard Design Philosophy

The dashboard focuses on:

* Clean visual hierarchy
* Minimal visual clutter
* Consistent formatting
* Interactive slicers
* Meaningful KPIs
* Clear analytical storytelling
* Easy navigation between report pages

The objective is not simply to display data, but to make the dashboard answer meaningful questions quickly.

---

## 💡 Future Improvements

Potential future enhancements include:

* Artist drill-through pages
* Song-level drill-through analysis
* Dynamic Top N analysis
* More advanced time-intelligence measures
* Ranking movement analysis
* Tooltip pages
* Bookmark-based navigation
* Advanced DAX calculations
* Spotify album artwork integration
* Additional audio features such as danceability, energy, valence, and acousticness

---

## 📌 Learning Outcomes

This project helped strengthen practical skills in:

* Power BI dashboard development
* Power Query data transformation
* Data modeling
* Relationship design
* DAX measure creation
* Time-series analysis
* KPI development
* Interactive visualization
* Data storytelling
* Analytical thinking

---

## 👨‍💻 Author

**Arijit Dutta**

Aspiring Data Analyst | Power BI | SQL | Excel | Python

This project was created as part of my hands-on learning and portfolio development in **Data Analytics and Business Intelligence**.

---

## ⭐ Feedback

Suggestions and feedback are welcome.

If you find this project useful, consider giving the repository a ⭐.
