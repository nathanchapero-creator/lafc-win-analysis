# lafc-win-analysis

### What is it?
  * Analysis of Carlos Vela's player tenure at Los Angeles Football Club (LAFC), with a special focus on the 2021 MLS season.

### Why I analyzed it: 
  * As an LAFC and soccer fan, analyzing my favorite player's tenure at the club made perfect sense to allow me to showcase my data analysis skills. During his tenure (2018-2023), Carlos Vela played in over 150 MLS matches, winning multiple titles and a championship. My goal was to asess whether or not Carlos Vela had a measurable correlation with LAFC's success. This includes measurements in win percentage, xGF (expected goals for), xGA (expected goals against), and xGD (expected goal difference).
    
### Tools Used: 
  * Excel, Power Query

### Brief Insight Summary:
  * The 2021 MLS season was marked the most notable outlier season, filled with clear signs of underperformance in both xGF (expected goals for) and xGA (expected goals against). I found that underperformance spiked primarily while Carlos Vela was on the pitch compared to when he was not playing.

## Analysis
### *LAFC's trajectory*
 * LAFC's performance during Carlos Vela's tenure:

<img width="738" height="439" alt="LAFC_Graph#1" src="https://github.com/user-attachments/assets/bbaf3bf4-1620-4848-a665-d07a53ac8f50" />

* **Trend Followers:** LAFC's performance followed expectations during the 2018, 2019, and 2022 seasons.
* **The "COVID" Year:** 2020 was filled with visa, player, and safety issues following the COVID-19 pandemic, with LAFC naturally suffering from inconsistent schedules and disruptions.
* **The Big Anomaly:** 2021 contained the largest underperformance in Vela's LAFC career, with a **0.56 difference**. How much of a role did Carlos Vela's injury-plagued year play?

### **Carlos Vela's 2021 Season**
 * LAFC's 2021 season was marred by poor finishing, unlucky defensive performances, and constant injuries to their star players, such as Carlos Vela.
 * Vela was unable to remain healthy throughout the season, frequently missing matches and rarely able to go the full 90 minutes. He ended the season with just 20 games played, with 5 goals and 5 assists, a far cry from his MVP season just two years earlier (36 goals, 11 assists).

<img width="815" height="502" alt="LAFC_Graph#2" src="https://github.com/user-attachments/assets/3de4e88c-dce4-45c8-a274-b83241205627" />

<img width="646" height="428" alt="LAFC_Graph#3" src="https://github.com/user-attachments/assets/0e645fb1-012b-496a-b4a2-5db25e3ec53e" />










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
  - *GD* - Goal Difference  
  - *xGD* - Expected Goal Difference

  **Created Helper Columns:**
  - *Display_Year* - To display season year
  - *Zero_Line_Helper* - Straight line positioned at "0" on X-axis
  - **

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
    - 🟩 *Green* for ≥ 70 minutes  
    - 🟨 *Yellow* for 31–69 minutes  
    - 🟥 *Red* for ≤ 30 minutes  

  **Other adjustments:**  
  - Reordered columns for clarity (Date and Season first, followed by match stats).  


</details>

