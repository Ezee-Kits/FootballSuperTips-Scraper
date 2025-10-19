# ⚽ FootballSuperTips Scraper

## 📘 Overview
**FootballSuperTips Scraper** is an automated Python project created by **Ezee Kits** that collects football prediction data from [FootballSuperTips.com](https://www.footballsuper.tips).  
The script scrapes **1X2**, **Over/Under 2.5**, and **Both Teams To Score (BTS)** predictions, merges them into one unified dataset, and saves the final output as a clean CSV file for analysis or model building.

---

## ⚙️ Features
- Automatically scrapes **daily football predictions** from FootballSuperTips.  
- Extracts **Home/Draw/Away percentages**, **Over/Under 2.5 stats**, and **BTS/OTS predictions**.  
- Merges all three prediction datasets into a **single, structured CSV file**.  
- **Removes duplicates** using a custom cleaning function.  
- Designed to run **daily** and save each day's data in a separate folder.  
- Uses helper functions from a modular `func.py` file for better organization.

---

## 🧠 How It Works
1. Generates a new folder for each day using `save_daily_csv()`.  
2. Fetches data from three FootballSuperTips URLs:
   - `todays-free-football-super-tips` → 1X2 predictions  
   - `todays-over-under-football-super-tips` → Over/Under 2.5 predictions  
   - `todays-both-teams-to-score-football-super-tips` → BTS/OTS predictions  
3. Parses HTML using **BeautifulSoup** to extract:
   - Date and Time  
   - Home and Away Teams  
   - Home, Draw, and Away Percentages  
   - Over 2.5 and Under 2.5 Percentages  
   - BTS (Both Teams to Score) and OTS (One Team to Score) Percentages  
4. Converts the data into **pandas DataFrames**, merges them on team names, and saves the combined dataset to a CSV file.  
5. Removes duplicate rows using `drop_duplicate()` to ensure data integrity.  

---

## 🧩 Tech Stack
- **Python 3.x**
- **Requests** – For fetching FootballSuperTips pages  
- **BeautifulSoup4** – For parsing HTML data  
- **pandas** – For merging and organizing data  
- **Custom Functions (func.py)** – For file management and data cleaning  
  - `save_daily_csv()`  
  - `drop_duplicate()`  
  - `match_day_date()`  

---

## 🧰 Setup Instructions
Follow these steps to set up and run the scraper:

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/footballsupertips-scraper.git
cd footballsupertips-scraper
```

### 2. Install Dependencies
```bash
pip install requests beautifulsoup4 pandas
```

### 3. Make Sure `func.py` Is Available
This script depends on custom helper functions located in `func.py`.  
Ensure that `func.py` contains the following functions:
- `save_daily_csv()`  
- `drop_duplicate()`  
- `match_day_date()`

### 4. Run the Script
```bash
python footballsupertips_scraper.py
```

---

## 💻 Usage Example
```python
from footballsupertips_scraper import footballsupertips_func

# Fetch and save today's predictions
footballsupertips_func()
```

---

## 📂 Example Output (footballsupertips.csv)
| DATE | TIME | HOME TEAM | AWAY TEAM | HOME PER | DRAW PER | AWAY PER | UNDER 2.5 | OVER 2.5 | BTS | OTS | NAME |
|------|------|------------|------------|-----------|-----------|-----------|-------------|-------------|------|------|------|
| 19.10.2025 | 14:00 | Liverpool | Brighton | 63 | 21 | 16 | 48 | 52 | 58 | 42 | FST |
| 19.10.2025 | 18:30 | Real Madrid | Valencia | 70 | 18 | 12 | 44 | 56 | 61 | 39 | FST |

---

## 🎯 Example Use Case
- **Data Aggregation:** Combine FootballSuperTips data with other prediction sources (like Betclan or Forebet) to build a stronger **data-driven betting model**.  
- **Machine Learning:** Use the clean CSV data as input for training prediction or confidence models.  
- **Automation:** Schedule it to run daily with `cron` or `Task Scheduler` to build a historical dataset of football predictions.  

---

## 👨‍💻 Author
**Ezee Kits**  
- GitHub: [@Ezee-Kits](https://github.com/Ezee-Kits)  
- YouTube: [Ezee Kits](https://www.youtube.com/@Ezee_Kits)

---

## 📜 License
This project is licensed under the **MIT License**.  
You are free to use, modify, and distribute the code, provided proper credit is given to the author.

---

## 🚀 Future Improvements
- Add support for scraping **tomorrow’s predictions**.  
- Include **error handling** for unavailable pages or network issues.  
- Integrate **multi-threading** for faster data collection.  
- Export results to **databases** (e.g., SQLite, PostgreSQL).  
