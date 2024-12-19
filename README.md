## Overview

This project collects and analyzes commit data from the GitHub API. It stores the data in an SQLite database, and performs various queries to retrieve key insights, including identifying the top committers, calculating the longest streaks of commits, and generating a heatmap based on commit activity.

## 1. Data Collection
- **Fetches commit data** from the GitHub API.
- **Retrieves the author’s name** and commit date (replacing the default "GitHub" committer name).
- **Handles pagination** by checking for additional pages of commits and fetching them accordingly.

## 2. Data Transformation
- **Converts commit dates** to the proper `datetime` format.
- **Extracts the day of the week** and **hour** from each commit date. These details will be used for building a heatmap later.

## 3. Data Storage
- **Stores the transformed data** in an SQLite database using SQLAlchemy.
- Data is saved in the `commits` table.

## 4. Data Analysis and Querying

### Query 1: Top Committers
- Groups the commits by **committer name**, orders them by **commit count**, and retrieves the **top 5 committers**.

### Query 2: Longest Streaks
- Sorts the data by **committer name** and **commit date**.
- Calculates the difference in days between consecutive commits and assigns a "streak" number whenever there is a break in consecutive commits.

### Query 3: Heatmap Data
- Groups commit data by **day of the week** and **3-hour time blocks**.
- Labels each time block (e.g., 01-03, 04-06) and organizes the data into a matrix with **days of the week** as rows and **3-hour blocks** as columns.
- Generates a **heatmap** that visualizes the commit count across these time intervals.
