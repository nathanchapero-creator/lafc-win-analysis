# lafc-expected-goals-variance

### What is it?
  * Analysis of Carlos Vela's tenure at Los Angeles Football Club (LAFC), with a special focus on the 2021 MLS season.
  * Does LAFC perform better when Vela plays?
  * Did team performance align with expected metrics?

### Tools Used: 
  * **Power Query** - data cleaning, transformations, joins, and data aggregation.
  * **Excel** - pivot tables, conditional formatting, visualizations.

### Notes:
* Deviations calculated per match (GF − xGF and GA − xGA).
* xGD and GD averaged per match.
* Dataset restricted to MLS regular season and playoff matches.

### Why I analyzed it: 
  * The goal is to assess whether Carlos Vela had a measurable impact on LAFC's success. This includes measurements in win percentage, xGF (expected goals for), xGA (expected goals against), and xGD (expected goal difference).

### Brief Insight Summary:
  * The 2021 MLS season contained the largest underperformance relative to xGD. Once broken down, underperformance was most prevalent while Vela was on the pitch.

## Analysis

### *LAFC's trajectory*
 * LAFC's performance during Carlos Vela's tenure:

<img width="738" height="439" alt="LAFC_Graph#1" src="https://github.com/user-attachments/assets/bbaf3bf4-1620-4848-a665-d07a53ac8f50" />

* **Trend Followers:** LAFC's performance matched underlying metrics during the '18, '19, '22, and '23 seasons.
* **The "COVID" Year:** While both 2020 and 2021 showed significant underperformance relative to expected metrics, the 2020 season was heavily impacted by COVID-19 disruptions, including an uneven schedule and tournament-style formats. To reduce structural noise and isolate on-field performance trends, this analysis focuses primarily on the 2021 season, which more closely resembled a standard MLS campaign.
* **The Big Anomaly:** 2021 marked the biggest underperformance in Vela's LAFC career, with a **-0.56 difference** relative to xGD. How much of a role did Carlos Vela's injury-plagued year play?

### **Carlos Vela's 2021 Season**
 * Poor finishing, unlucky defensive performances, and frequent injuries to key players such as Eduard Atuesta and Eddie Segura marred LAFC's season.
 * Vela was unable to remain healthy throughout the season, frequently missing matches and rarely able to go the full 90 minutes. He ended the season with just 20 games played, with 5 goals and 5 assists, a far cry from his MVP season just two years earlier (36 goals, 11 assists in domestic play).

<img width="730" height="459" alt="LAFC_Graph#2" src="https://github.com/user-attachments/assets/c027b5c9-0bf7-4bc5-a881-8979edfb1877" />

***A Stark Contrast:** 
* With Vela on the pitch, LAFC displayed similar underlying metrics to their 2022 championship season, but GD results demonstrated substantial underperformance.

### The Big Picture:
* LAFC's 2021 Season, broken down by when Vela was on or off the pitch:

<img width="697" height="460" alt="LAFC_Graph#3" src="https://github.com/user-attachments/assets/b708b32a-237e-4080-9e0c-0bd3f8d35850" />

* Without Vela on the pitch, LAFC had an xGF and xGA of **+0.03** and **0.06** per game, respectively, indicating that their attack and defense met expectations.
* With Vela on the pitch, LAFC had an xGF and xGA of **-0.66** and **0.27** respectively, indicating underperformance in both attacking and defending.

### Conclusion
* Vela was plagued by numerous injuries that led to him playing just 59% of LAFC's domestic matches in 2021, compared to 92% of regular-season and playoff matches just two seasons earlier (2019).


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

