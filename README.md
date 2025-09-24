# lafc-win-analysis
LAFC data analysis project tracking win percentages and trends over 2018-2023 MLS seasons. Further analysis on Carlos Vela's impact on the club's win percentage.

## 📊 Data Sources

This project uses publicly available soccer data. All datasets were accessed manually in September 2025.

- **LAFC Match Logs (2018–2023)**  
Source: [FBRef](https://fbref.com/)  
Description: Match-level results including date, opponent, goals for/against, and outcome.

| Season |
|--------|
| [2018](https://fbref.com/en/squads/81d817a3/2018/Los-Angeles-FC-Stats) |
| [2019](https://fbref.com/en/squads/81d817a3/2019/Los-Angeles-FC-Stats) |
| [2020](https://fbref.com/en/squads/81d817a3/2020/Los-Angeles-FC-Stats) |
| [2021](https://fbref.com/en/squads/81d817a3/2021/Los-Angeles-FC-Stats) |
| [2022](https://fbref.com/en/squads/81d817a3/2022/Los-Angeles-FC-Stats) |
| [2023](https://fbref.com/en/squads/81d817a3/2023/Los-Angeles-FC-Stats) |

- **Carlos Vela Match Logs (2018–2023)**  
Source: [Transfermarkt](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773)  
Description: Player-level match logs including date, opponent, competition, and minutes played.

| Season |
|--------|
| [2018](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/saison/2017#gesamt) |
| [2019](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/saison/2018#gesamt) |
| [2020](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/saison/2019#gesamt) |
| [2021](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/saison/2020#gesamt) |
| [2022](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/saison/2021#gesamt) |
| [2023](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/saison/2022#gesamt) |


- **Notes**  
  - Dates were standardized to `YYYY-MM-DD`.  
  - Opponent names were normalized to match across datasets. 
  - Row counts were validated against official season totals.
  - 2020 MLS season was shortened due to COVID (23 matches instead of 34) and included repeat fixtures (LAFC vs LA Galaxy three times).
  - Only MLS regular season + playoff matches included (Vela’s 2024 cameo excluded).
  - Non-MLS competitions (US Open Cup, CCL, friendlies) were excluded from the cleaned dataset to focus the analysis on MLS results only.  

