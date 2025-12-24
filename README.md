
# **🚗 Car Listing Analytics & Price Prediction**

**• Web Scraping • Data Engineering • Data Analysis • Machine Learning • Price Prediction • End-to-End Project**

## **Project Overview**

This project analyzes the Dutch used and new car market using publicly available listings to build an end-to-end analytics and machine-learning workflow. It covers the full lifecycle from data ingestion and processing to visualization and price prediction.

Buying a car often involves uncertainty, as prices vary widely based on factors such as brand, model, age, mileage, engine power, and market conditions. This project addresses that challenge by continuously collecting real-world listings, standardizing key attributes, and transforming them into analytics-ready datasets that support both exploratory insights and predictive modeling.

At its core, the project demonstrates how web-scraped data can be converted into reliable market intelligence. Listings are collected periodically, cleaned, enriched, and curated through layered transformations. The resulting data powers interactive dashboards for market analysis and a machine-learning model that estimates car prices based on selected vehicle characteristics.

The outcome is a practical system that helps buyers, analysts, and enthusiasts better understand pricing dynamics and identify potentially undervalued listings in the Dutch car market.

## **Project Objectives**

The project focuses on:
- Analyzing price patterns across brands, models, and key vehicle characteristics
- Deriving market insights from listing attributes beyond price alone
- Training a machine-learning model to estimate car prices based on selected features
- Presenting results through an interactive dashboard and a lightweight prediction application

The emphasis is on practical insights and clarity, rather than exhaustive modeling or infrastructure complexity.

## **Dataset Overview**

The dataset is collected programmatically from publicly accessible car listings posted by users in the Netherlands. The data describes vehicles offered for sale and includes information such as vehicle characteristics, pricing, seller type, and listing metadata. No personal identifiers are collected, and the project does not attempt to track or profile individual users.

In addition to scraped listing data, selected fields are enriched using the GeoNames API. Location-related attributes are derived from postal codes found in the listings, allowing geographic context to be added in a structured and reproducible way. This enrichment step demonstrates the integration of external APIs into the data pipeline.

Because the data is obtained from the web:
- Some fields may be missing or inconsistently formatted
- Data quality varies between listings
- Listings represent a snapshot in time rather than a complete market view

In addition, web scraping pipelines require ongoing maintenance, as website structures and HTML markup may change over time. Selectors and extraction logic may therefore need periodic updates to ensure continued data quality and completeness.

The dataset is used strictly for educational and analytical purposes.

## **High-Level Architecture**

The project follows a layered analytics architecture, separating data ingestion, processing, analysis, and serving.

Data is collected via web scraping, incrementally stored, transformed into structured datasets, and then used for both analytical exploration and machine-learning inference. Analytics and model predictions are exposed through dedicated tools, prioritizing clear separation of responsibilities and compatibility with open-source and free-tier tooling.

A folder tree is shown below:
```bash
car-listing-analytics/
│
├── data/
│   ├── raw/                    # Raw scraped data (JSONL)
│   ├── bronze/                 # Consolidated raw data (Parquet)
│   ├── silver/                 # Cleaned & normalized data
│   ├── gold/                   # Curated / analytics-ready data
│   └── analytics.duckdb        # DuckDB analytics store
│
├── notebooks/
│   └── eda.ipynb               # Exploratory analysis (read-only)
│
├── src/
│   ├── scraping/
│   │   └── spider.py           # Scrapy spider logic
│   │
│   ├── enrichment/
│   │   ├── geonames.py         # Geo data enrichment
│   │
│   ├── cleaning/
│   │   ├── rules.py            # Cleaning rules (pure functions)
│   │   └── clean.py            # Silver layer creation
│   │
│   ├── transforms/
│   │   ├── features.py         # Feature engineering
│   │   └── aggregations.py     # Gold tables
│   │
│   ├── ml/
│   │   ├── train.py
│   │   ├── evaluate.py
│   │   └── select_best.py
│   │
│   ├── serving/
│   │   └── app.py              # Streamlit UI
│   │
│   └── helpers/
│       └── utils.py            # Helper functions
│
├── models/
│   ├── price_model_v1.joblib
│   └── metadata.json           # Feature schema, metrics
│
├── .gitignore
├── requirements.txt
└── README.md
```

## **Technology Stack**

The project uses a set of complementary tools, each chosen for a specific role. The architecture diagram below illustrates how these components interact across the pipeline.

![Diagram](https://github.com/tmsnobrega/car-listing-analytics/blob/main/img/diagram.png)

## **Results & Insights**

### Exploratory Analysis
Exploratory analysis was conducted to understand the structure and limitations of the data and to identify relevant patterns.

Key observations include:
- Clear price differences between brands and models
- Strong relationships between price, mileage, and vehicle age
- Noticeable variation based on fuel type and drivetrain

These findings informed feature selection for the machine-learning model.

### Dashboard
The Tableau dashboard presents aggregated views of the data and allows interactive exploration of pricing patterns.

It highlights:
- Average prices by brand and model
- Price distributions across key vehicle attributes
- Filters to compare subsets of listings

The dashboard is designed to support insight discovery rather than exhaustive reporting. The dashboard is available at [Tableau Public](add_link_here).

### Machine Learning
A regression model is trained to estimate car prices using a subset of vehicle characteristics.

The model is:
- Trained offline
- Evaluated using standard regression metrics
- Persisted and reused for inference only

Predictions are made available through a Streamlit application, allowing users to explore how different vehicle attributes influence estimated price. The application can be found at [Streamlit Community Cloud](add_link_here).

## **License & Disclaimer**

This project is intended for non-commercial, educational purposes only.
- No ownership of the original data is claimed
- Raw scraped data is not redistributed
- The project does not represent or endorse any marketplace or seller

Any insights or predictions produced by the project should be interpreted as illustrative rather than authoritative.

