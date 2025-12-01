---
title: "Gym Occupancy Tracking with Selenium"
excerpt: "Automated scraping of live gym occupancy by section and overall capacity, aggregated over a year to study usage patterns."
categories: ["Web Scraping", "Data Analysis"]
tags: ["Python", "Selenium", "Pandas", "Scheduling", "Visualization"]
layout: single
classes: wide
---

## Overview
This project automates the collection of live occupancy numbers from my gym's website, which estimates people present using nearby Bluetooth devices. Selenium navigates the site, captures the overall facility count plus section-level counts, and saves the readings to a structured dataset. After a year of continuous collection, the data now supports analysis of peak times, day-of-week trends, and congestion by area.

---

## Tools & Technologies
- **Python**
- **Selenium**
- **Pandas**
- **Matplotlib / Plotly**
- **Cron / Scheduled Jobs**

---

## Data Collection Workflow
- Selenium script authenticates and loads the occupancy dashboard.
- Scrapes timestamped counts for the whole gym and each section.
- Runs on a schedule (cron) to capture regular snapshots throughout the day.
- Writes raw records to disk, with lightweight validation to catch missing or duplicate pulls.

Captured fields include:
- `timestamp_utc`
- `location` (overall or section name)
- `occupancy_count` (integer)
- `source_url` for traceability

---

## Aggregation & Analysis
- Normalize raw pulls into long-format tables keyed by `timestamp` and `location`.
- Resample to hourly and daily summaries to smooth noisy readings.
- Build comparisons across sections (e.g., weights vs. cardio) to find congestion patterns.
- Visualize distributions and weekly seasonality to inform optimal workout times.

---

## Reliability & Ethics
- Respectful scraping: low-frequency requests and only my own authenticated session.
- Basic retry logic to handle transient site changes or network hiccups.
- Local logging for failed pulls to keep the time series continuous.

---

## Current Status
- Year-long dataset collected and cleaned for exploratory analysis.
- Early plots highlight consistent rush windows; deeper statistical summaries are in progress.
- Preparing a reproducible notebook to share the workflow end-to-end.

---

## Future Improvements
- Add alerts for live occupancy thresholds (e.g., text when the weight room is below a set level).
- Experiment with anomaly detection to flag irregular spikes.
- Containerize the scraper for portable deployment (Docker + scheduled task).

---

## Summary
Automated Selenium scraping captures the gym's live occupancy (overall and by section) and rolls it into a year-long time series. With scheduled pulls, validation, and exploratory visualizations, the project is evolving toward a shareable toolkit for planning less-crowded gym visits.
