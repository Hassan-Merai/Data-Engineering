# Data-Engineering
Create a complete data pipeline with cloud functions and cloud schedulers using GCP

---

```markdown
# 🛴 Gans Weather & Flights Data Pipeline

**A serverless, cloud-native data pipeline for mobility intelligence**

Welcome to the data backbone of **Gans**, a company that rents thousands of electric scooters across Berlin, Hamburg, and Munich. This project leverages the power of **Google Cloud Platform (GCP)** to gather, store, and process external data that directly influences business operations — namely **weather conditions** and **incoming flight data**.

Because when it rains, revenue drops. And when tourists land without luggage, scooter demand skyrockets.

## 🚀 Project Goals

- Predict scooter demand fluctuations based on **weather conditions**.
- Detect tourist arrival patterns using **short-haul flight data**.
- Store historical data in **Cloud SQL** for analytics and modeling.
- Automate the entire process with **Cloud Functions** and **Cloud Scheduler**.

## 📦 Features

- 🌦️ **Weather Forecast Collection**  
  Real-time weather data for Berlin, Hamburg, and Munich using the OpenWeatherMap API.

- ✈️ **Flight Arrival Monitoring**  
  Tomorrow’s short-haul flight arrivals from Aerodatabox API, filtered for low-luggage potential.

- 🏙️ **City Metadata Scraping**  
  One-time local scraping of Wikipedia pages to gather static info: population, latitude, longitude.

- ☁️ **Serverless Infrastructure**  
  Cloud Functions automatically fetch data and update Cloud SQL — scheduled via Cloud Scheduler.

- 🧠 **Tourist-Weather-Aware Revenue Insight**  
  With centralized data, Gans can better correlate demand drops with drizzle and plan promotions for peak flight times.

## 🧰 Tech Stack

| Layer             | Tool                     |
|------------------|--------------------------|
| Cloud Provider    | Google Cloud Platform    |
| Data Sources      | OpenWeatherMap API, Aerodatabox API, Wikipedia (scraped) |
| Storage           | Cloud SQL (PostgreSQL)   |
| Automation        | Cloud Functions, Cloud Scheduler |
| Language          | Python 3.9               |

## 🛠️ Setup & Deployment

1. **Clone this repo**
   ```bash
   git clone https://github.com/yourusername/gans-weather-pipeline.git
   cd gans-weather-pipeline
   ```

2. **Create and configure your Cloud SQL instance**
   - PostgreSQL with appropriate schema (see `/Gans.sql`)
   - Whitelist access IPs or use Cloud IAM

3. **Deploy your Cloud Function**
   ```bash
   gcloud functions deploy cities_weather \
     --runtime python39 \
     --trigger-http \
     --allow-unauthenticated \
     --region europe-west1
   ```

4. **Schedule your pipeline**
   - Use **Cloud Scheduler** to trigger your function daily

5. **Secure your credentials**
   - API keys and DB passwords go into a `keys.py` file or environment variables (never push this to GitHub!)

## 🧪 Local Testing

You can simulate function calls locally using:
```bash
python main.py
```
Ensure that you have all dependencies installed:
```bash
pip install -r requirements.txt
```

## 🤓 Lessons Learned

- Cloud Functions are awesome until they loop infinitely at 3 AM
- Cloud Scheduler is your silent, punctual friend
- Serverless ≠ Problem-less (always test locally!)
- Weather affects scooter revenue more than you’d think
- Tourists with no luggage are the real MVPs of scooter usage

## 📬 About the Author

Built with ❤️ by Fred (Hassan Merai) a data scientist during his WBS Coding School capstone project.  
This pipeline isn’t just an academic exercise — it’s designed to impact real-world decisions at **Gans**.

---
