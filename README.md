# lafc-win-analysis
LAFC data analysis project tracking win percentages and trends over 2018-2023 MLS seasons. Further analysis on Carlos Vela's impact on the club's win percentage.

## 📊 Data Sources

This project uses publicly available soccer data. All datasets were accessed manually in September 2025.

- **LAFC Match Logs (2018–2023)**  
  Source: [FBRef](https://fbref.com/)  
  Example URL (2018 season): https://fbref.com/...  
  Description: Match-level results including date, opponent, goals for/against, and outcome.

- **Carlos Vela Match Appearances (2018–2023)**  
  Source: [Transfermarkt](https://www.transfermarkt.us/)  
  Example URL (2018 season): https://www.transfermarkt.us/...  
  Description: Player-level appearances with minutes played, substitutions, and competition.

- **Notes**  
  - Dates were standardized to `YYYY-MM-DD`.  
  - Opponent names were normalized to match across datasets. 
  - Row counts were validated against official season totals.
  - 2020 MLS season was shortened due to COVID (23 matches instead of 34) and included repeat fixtures (LAFC vs LA Galaxy three times).
  - Only MLS regular season + playoff matches included (Vela’s 2024 cameo excluded).  

