# lafc-win-analysis

### What is it?
  * Analysis of Carlos Vela's time at LAFC, with a special focus on the 2021 MLS season

### Why I analyzed it: 
  * LAFC is my favorite football (AKA soccer) club, so I decided to look into the club's history to derive insights that I hadn't previously noticed. I specifically wanted to analyze Carlo Vela's time, as he is my favorite player and also widely considered the club's most iconic player.

### Tools Used: 
  * Excel, Power Query

### Brief Insight Summary:
  * My analysis found the 2021 MLS season to be a significant outlier, filled with clear signs of underperformance in both xG (expected goals) and xGA (expected goals against). I found that underperformance spiked primarily while Carlos Vela was on the pitch compared to when he was not playing.

### In General Terms:
 * LAFC's 2021 season was marred by poor finishing, unlucky defensive performances, and constant injuries to their star players, such as Carlos Vela. Vela was unable to remain healthy throughout the season, frequently missing matches. LAFC as a whole was never able to retain consistency.


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
| [2018](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/plus/0?saison=2017) |
| [2019](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/plus/0?saison=2018) |
| [2020](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/plus/0?saison=2019) |
| [2021](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/plus/0?saison=2020) |
| [2022](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/plus/0?saison=2021) |
| [2023](https://www.transfermarkt.co.uk/carlos-vela/leistungsdaten/spieler/35773/plus/0?saison=2022) |


- **Notes**  
  - Row counts were validated against official season totals.
  - 2020 MLS season was shortened due to COVID (23 matches instead of 34) and included repeat fixtures (LAFC vs LA Galaxy three times).
  - Only MLS regular season + playoff matches included (Vela’s 2024 cameo excluded).
  - Non-MLS competitions (US Open Cup, CCL, friendlies) were excluded from the cleaned dataset to focus the analysis on MLS results only.
  - 2020 MLS is Back Group Stage games included due to also counting as regular season matches for the MLS Regular Season.

<details>
  <summary>Data Cleaning Notes (LAFC Match Logs)</summary>

  **Removed columns:**  
  *Time*, *Day*, *Poss*, *Attendance*, *Captain*, *Formation*, *Opp Formation*, *Referee*, *Match Report*, and *Notes*.

  **Kept columns:**  
  *Date*, *Comp*, *Round*, *Opponent*, *Venue*, *Result*, *GF*, *GA*, *xG*, and *xGA*.

  **Created columns:**  
  - *Composite_Key* — combination of Date, Matchday, and Season  
  - *Matchday*  
  - *Season*  
  - *GD* (Goal Difference)  
  - *xGD* (Expected Goal Difference)

  **Carlos Vela match data adjustments:**  
  - Only retained *Minutes_Played*  
  - Created a *Composite_Key* (Matchday + Year of Date)  
  - Added *Did_Vela_Play* (binary indicator for match participation)  
  - Joined Vela data to FBRef dataset using a **left join** on *Composite_Key*  

  **Final merged dataset (2018–2023 MLS seasons):**  
  - Applied conditional formatting to the **Result** column  
    - 🟩 *Green* for Wins (W)  
    - ⚪ *Gray* for Draws (D)  
    - 🟥 *Red* for Losses (L)  
  - Applied conditional formatting to **Vela_Minutes_Played**  
    - 🟩 *Green* for ≥ 85 minutes  
    - 🟨 *Yellow* for 65–84 minutes  
    - 🟥 *Red* for ≤ 64 minutes  

  **Other adjustments:**  
  - Reordered columns for clarity (Date and Season first, followed by match stats).  


</details>

