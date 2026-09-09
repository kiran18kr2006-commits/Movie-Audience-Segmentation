# Movie Audience Segmentation

<p align="center">
  <strong>Machine Learning Powered Audience Analytics Dashboard</strong>
</p>

<p align="center">
  An interactive React application that uses K-Means clustering to discover meaningful movie-viewer segments from rating behavior.
</p>

<p align="center">

![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge\&logo=react\&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-4-646CFF?style=for-the-badge\&logo=vite\&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge\&logo=javascript\&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?style=for-the-badge\&logo=tailwindcss\&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-K--Means-FF6F00?style=for-the-badge)

</p>

---

## Overview

**Movie Audience Segmentation** is an end-to-end browser-based analytics application that transforms raw movie-rating data into actionable audience segments.

The system analyzes individual viewer behavior, engineers behavioral and genre-preference features, standardizes the feature space, and applies a custom **K-Means clustering algorithm** to identify groups of viewers with similar rating patterns.

The resulting segments are presented through an interactive analytics dashboard containing charts, cluster metrics, viewer-level analysis, segment insights, and downloadable PDF reports.

The project demonstrates the complete journey from:

**Raw Data → Feature Engineering → Machine Learning → Cluster Evaluation → Business Insights → Interactive Visualization**

---

## Demo

> Add your deployed application URL here.

**Live Demo:** `https://your-demo-url.com`

**Repository:** `https://github.com/your-username/movie-audience-segmentation`

### What you can explore

* Audience segment discovery
* Interactive cluster analysis
* Rating behavior analytics
* Genre preference analysis
* Viewer-level exploration
* Cluster performance metrics
* Dynamic K-Means configuration
* PDF report generation

---

## Screenshots

> Replace the placeholders below with screenshots from the deployed application.

### Dashboard

![Dashboard](docs/screenshots/dashboard.png)

The main dashboard provides a high-level view of the dataset, rating behavior, audience distribution, and genre-level insights.

### Audience Segments

![Audience Segments](docs/screenshots/audience-segments.png)

Explore automatically generated audience segments and understand the behavioral characteristics of each cluster.

### Rating Analysis

![Rating Analysis](docs/screenshots/rating-analysis.png)

Analyze rating distributions, viewer activity, movie popularity, and genre-level rating behavior.

### Cluster Performance

![Cluster Performance](docs/screenshots/cluster-performance.png)

Evaluate clustering quality using cluster sizes, inertia, silhouette score, and segment-level statistics.

### Viewer Details

![Viewer Details](docs/screenshots/viewer-details.png)

Inspect individual viewer behavior and understand how viewers contribute to each audience segment.

---

# Key Features

## Audience Segmentation

The application automatically groups viewers according to their rating behavior using K-Means clustering.

Features include:

* K-Means clustering implemented from scratch
* K-Means++ centroid initialization
* Lloyd's optimization algorithm
* Configurable K from 2 to 6
* Deterministic clustering
* Automatic segment classification
* Cluster-level behavioral analysis

---

## Feature Engineering

Raw ratings are transformed into meaningful viewer-level features.

For each viewer, the system calculates:

* Average rating
* Number of ratings
* Rating variance
* Minimum rating
* Maximum rating
* Rating consistency
* Genre-specific average ratings
* Dominant genre preference

This converts individual rating records into a behavioral profile suitable for unsupervised learning.

---

## Feature Standardization

Because the engineered features have different numerical scales, the application applies **Z-score standardization** before clustering.

```text
z = (x - μ) / σ
```

This prevents high-range features such as rating count from disproportionately influencing the clustering algorithm.

---

## Custom K-Means Implementation

Rather than relying on a high-level machine learning library, the project contains its own JavaScript implementation of K-Means.

The implementation includes:

1. K-Means++ initialization
2. Distance calculation
3. Cluster assignment
4. Centroid recalculation
5. Convergence detection
6. Maximum iteration control
7. Inertia calculation

Default configuration:

```text
K = 4
Maximum iterations = 100
Random seed = 42
```

Users can dynamically change the number of clusters and rerun the analysis.

---

# Machine Learning Architecture

```text
                         ┌──────────────────────┐
                         │   Movie Ratings CSV   │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │   Data Ingestion     │
                         │    & Validation      │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Feature Engineering  │
                         │                      │
                         │ • Avg Rating         │
                         │ • Rating Count       │
                         │ • Variance           │
                         │ • Min / Max Rating   │
                         │ • Consistency        │
                         │ • Genre Preferences  │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Feature Standardize  │
                         │      Z-Score         │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    K-Means /         │
                         │    K-Means++         │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Cluster Evaluation   │
                         │                      │
                         │ • Inertia            │
                         │ • Silhouette Score   │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Audience Segments    │
                         │ & Behavioral Insights│
                         └──────────┬───────────┘
                                    │
                                    ▼
                 ┌─────────────────┴─────────────────┐
                 │                                   │
                 ▼                                   ▼
        ┌──────────────────┐               ┌──────────────────┐
        │ Interactive      │               │ PDF Report       │
        │ Dashboard        │               │ Generation       │
        └──────────────────┘               └──────────────────┘
```

---

# Application Architecture

```text
src/
│
├── components/
│   ├── ChartCard.jsx
│   ├── ClusterVisualization.jsx
│   ├── Header.jsx
│   ├── RatingBehaviorMatrix.jsx
│   ├── ReportButton.jsx
│   ├── SegmentCard.jsx
│   ├── Sidebar.jsx
│   ├── StatCard.jsx
│   ├── ViewerDetails.jsx
│   └── ViewerTable.jsx
│
├── ml/
│   ├── clustering.js
│   ├── kmeans.js
│   └── preprocessing.js
│
├── pages/
│   ├── AudienceSegments.jsx
│   ├── ClusterPerformance.jsx
│   ├── Dashboard.jsx
│   └── RatingAnalysis.jsx
│
├── services/
│   └── dataset.js
│
├── utils/
│   ├── colors.js
│   ├── reportGenerator.js
│   └── segmentInsights.js
│
├── App.jsx
├── index.css
└── main.jsx
```

The architecture separates:

* UI components
* Machine learning logic
* Dataset processing
* Application pages
* Visualization utilities
* Report generation

This keeps the ML pipeline independent from the presentation layer and makes the project easier to extend.

---

# Dataset

The included dataset contains:

| Metric             | Value |
| ------------------ | ----: |
| Rating records     | 6,083 |
| Viewers            |   252 |
| Movies             |    36 |
| Genres             |     6 |
| Rating scale       |   1–5 |
| Average rating     |  3.49 |
| Median rating      |     4 |
| Most common rating |     4 |

### Genres

* Action
* Comedy
* Drama
* Sci-Fi
* Romance
* Thriller

---

# Audience Segmentation Pipeline

## 1. Data Ingestion

The application loads:

```text
public/data/movie_ratings.csv
```

Expected schema:

```csv
user_id,movie_id,movie_title,genre,rating
```

The ingestion layer validates records and removes duplicate user-movie combinations.

---

## 2. Viewer Profile Construction

Individual ratings are aggregated into viewer-level behavioral profiles.

Example conceptual representation:

```text
Viewer
 ├── Average Rating
 ├── Rating Count
 ├── Rating Variance
 ├── Rating Range
 ├── Consistency
 ├── Action Preference
 ├── Comedy Preference
 ├── Drama Preference
 ├── Sci-Fi Preference
 ├── Romance Preference
 └── Thriller Preference
```

---

## 3. Standardization

All numerical features are normalized using Z-score standardization.

This ensures that features such as:

```text
Rating Count
```

do not dominate features such as:

```text
Average Rating
```

during Euclidean-distance calculations.

---

## 4. Clustering

K-Means groups viewers according to their standardized behavioral profiles.

Conceptually:

```text
Viewer Features
       |
       ▼
Initial Centroids
       |
       ▼
Assign Viewers
       |
       ▼
Recalculate Centroids
       |
       ▼
Repeat Until Convergence
       |
       ▼
Final Audience Segments
```

---

# Cluster Evaluation

The application uses two primary metrics.

### Inertia

Measures the total squared distance between viewers and their assigned centroids.

```text
Lower inertia
      ↓
Tighter clusters
```

Inertia is particularly useful for comparing different K values using an elbow-style analysis.

### Silhouette Score

Measures how well each viewer fits within its assigned cluster compared with neighboring clusters.

The general interpretation is:

```text
Closer to +1  → Better-separated clusters
Around 0      → Overlapping clusters
Below 0       → Potentially poor assignments
```

---

# Audience Insights

After clustering, the application calculates cluster-level behavioral statistics and generates descriptive audience profiles.

Possible segment characteristics include:

### Highly Engaged Viewers

Viewers with high rating activity and strong interaction with the movie catalog.

### Selective High-Rating Viewers

Viewers who rate fewer movies but tend to give relatively high ratings.

### Genre-Focused Viewers

Viewers whose rating behavior is strongly concentrated around particular genres.

### Critical Rating Viewers

Viewers who tend to assign lower or more conservative ratings.

The segment names are derived from the observed cluster characteristics rather than being manually assigned to individual viewers.

---

# Dashboard

The dashboard brings the machine learning results together into a single analytics experience.

### Key metrics

* Total viewers
* Total movies
* Total ratings
* Overall average rating

### Visual analytics

* Rating distribution
* Genre rating comparison
* Audience segment distribution
* Segment rating behavior
* Viewer activity
* Cluster statistics

This allows users to move from high-level business metrics to individual viewer analysis.

---

# Report Generation

The application includes browser-based PDF report generation.

Generated reports can include:

* Dataset overview
* Audience segmentation results
* Cluster configuration
* Segment statistics
* Genre analysis
* Clustering metrics
* Audience insights
* Visualization snapshots

This turns the analytical output into a shareable business report without requiring server-side processing.

---

# Technology Stack

| Category             | Technology        |
| -------------------- | ----------------- |
| UI                   | React 18          |
| Build Tool           | Vite              |
| Styling              | Tailwind CSS      |
| Language             | JavaScript        |
| Data Parsing         | PapaParse         |
| Charts               | Recharts          |
| Machine Learning     | Custom JavaScript |
| Clustering           | K-Means           |
| PDF Generation       | jsPDF             |
| Visualization Export | html2canvas       |

---

# Why This Project Is Interesting

This project goes beyond simply displaying charts.

It demonstrates how raw behavioral data can be converted into an interpretable machine learning product:

```text
Data
 ↓
Cleaning
 ↓
Feature Engineering
 ↓
Standardization
 ↓
Unsupervised Learning
 ↓
Model Evaluation
 ↓
Audience Interpretation
 ↓
Interactive Visualization
 ↓
Business Report
```

The application therefore combines **data science, machine learning, frontend engineering, visualization, and product-oriented analytics** in a single project.

---

# Performance & Design Decisions

### Client-Side Machine Learning

The clustering pipeline runs directly in the browser.

Advantages:

* No backend required
* No ML API dependency
* Simple deployment
* Immediate interaction
* User data remains within the application

### Deterministic Clustering

A fixed random seed is used to make clustering results reproducible.

### Dynamic Genre Detection

Genre features are generated from the dataset rather than being hard-coded to a fixed number of genres.

### Separation of Concerns

Machine learning, data processing, UI components, visualization, and report generation are separated into dedicated modules.

---

# Getting Started

## Prerequisites

* Node.js
* npm

## Installation

```bash
git clone https://github.com/your-username/movie-audience-segmentation.git

cd movie-audience-segmentation

npm install
```

## Development

```bash
npm run dev
```

Then open the local URL displayed by Vite.

## Production Build

```bash
npm run build
```

## Preview Production Build

```bash
npm run preview
```

---

# Project Highlights

### Machine Learning

* Implemented K-Means clustering from scratch in JavaScript
* Implemented K-Means++ initialization
* Built a complete feature-engineering pipeline
* Applied Z-score standardization
* Implemented inertia and silhouette-score evaluation
* Supported dynamic cluster configuration

### Data Analytics

* Converted raw rating events into viewer-level behavioral profiles
* Built genre preference features
* Generated cluster-level statistics
* Created automated audience segment descriptions
* Added viewer-level analytical exploration

### Frontend Engineering

* Built a multi-page React analytics dashboard
* Created reusable visualization components
* Implemented interactive cluster exploration
* Added dynamic data-driven UI
* Added client-side PDF report generation

### Product Thinking

* Transformed an ML model into an interactive analytics product
* Presented technical clustering output as understandable audience segments
* Added business-oriented segment insights
* Designed the application around exploration and decision-making rather than raw model output

---

# Resume-Ready Project Description

### Short Version

**Movie Audience Segmentation | React, JavaScript, K-Means, Recharts**

> Built an interactive machine-learning dashboard that segments 252 movie viewers using behavioral and genre-preference features derived from 6,083 ratings. Implemented K-Means/K-Means++ clustering from scratch, Z-score standardization, inertia and silhouette evaluation, interactive visualizations, automated audience insights, and PDF report generation entirely in the browser.

### Resume Bullet Points

* Developed a browser-based audience segmentation platform using **React and custom K-Means clustering**, transforming 6,083 movie ratings into behavioral profiles for 252 viewers.
* Engineered viewer-level features including rating frequency, average rating, variance, consistency, and genre preferences, followed by **Z-score standardization** for clustering.
* Implemented **K-Means++ initialization, Lloyd's algorithm, inertia, and silhouette scoring from scratch in JavaScript**, with dynamic K selection from 2–6 clusters.
* Built an interactive analytics dashboard using **Recharts and Tailwind CSS** for exploring audience segments, rating behavior, genre preferences, and viewer-level insights.
* Added automated audience-segment interpretation and **client-side PDF report generation**, converting unsupervised ML results into business-readable analytics.

---

# Future Improvements

Potential extensions include:

* Automatic optimal-K selection
* Elbow curve visualization
* PCA-based cluster visualization
* t-SNE visualization
* DBSCAN comparison
* Hierarchical clustering
* Movie recommendation engine
* Time-based rating analysis
* Viewer similarity search
* CSV export for segmented viewers
* Larger dataset support using Web Workers
* Persistent user-uploaded datasets
* Model comparison dashboard

---

# License

Add your preferred open-source license before publishing.

For example:

```text
MIT License
```

---

# Author

**Your Name**

If this project is part of your portfolio, consider adding:

* LinkedIn
* GitHub
* Portfolio
* Email

---

<p align="center">
  Built with React, JavaScript, Machine Learning, and Data Visualization.
</p>
# Movie-Audience-Segmentation
End-to-end movie audience analytics platform that transforms viewer ratings into actionable audience segments using machine learning.
