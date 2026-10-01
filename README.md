Running Race Planner 2027
Power BI dashboard for planning and tracking running races throughout the 2027 season.
The project combines an Excel-based race plan with an interactive Power BI dashboard. It is designed to provide a clear overview of planned races, total race distance, race priorities, the next upcoming event, race spacing, and monthly race distribution.
Dashboard Preview
 
Main Features
- Total race distance
- Number of planned races
- Number of priority A races
- Next upcoming race
- Days remaining until the next race
- Interactive filtering by race priority
- Interactive filtering by race distance
- Detailed race overview
- Conditional formatting for race gaps
- Monthly race distribution
Data Source
The dashboard uses an Excel workbook as its source.
Each row represents one race and contains fields such as:
- Date
- Start time
- Race name
- Location
- Race type
- Distance
- Priority
- Status
- Goal
- Registration status
- Result
- Position
- Days between races
- Race phase
- Gap in weeks
The source file is designed to be updated during the season as new races are added or completed.
Tools Used
- Microsoft Power BI Desktop
- Microsoft Excel
- Power Query
- DAX
DAX Measures
Next Race
Next Race =
VAR NextDate =
    CALCULATE(
        MIN(Preteky_2027[Dátum]),
        FILTER(
            Preteky_2027,
            Preteky_2027[Dátum] >= TODAY()
                && Preteky_2027[Stav] <> "Zrušený"
        )
    )
RETURN
    CALCULATE(
        SELECTEDVALUE(Preteky_2027[Názov pretekov]),
        Preteky_2027[Dátum] = NextDate
    )
Days to Next Race
Days to Next Race =
VAR NextDate =
    CALCULATE(
        MIN(Preteky_2027[Dátum]),
        FILTER(
            Preteky_2027,
            Preteky_2027[Dátum] >= TODAY()
                && Preteky_2027[Stav] <> "Zrušený"
        )
    )
RETURN
    DATEDIFF(
        TODAY(),
        NextDate,
        DAY
    )
Dashboard Design
The dashboard focuses on a clean and compact layout:
- KPI cards at the top
- filters for priority and race distance
- highlighted next-race section
- detailed race table
- monthly race chart
- conditional formatting for race spacing
Race gaps are visually classified to make recovery periods easier to identify.
Project Structure
Running-Race-Planner-2027/
│
├── data/
│   └── Bezecke_preteky_2027_beta_V04.xlsx
│
├── powerbi/
│   └── Running_Race_Planner_2027.pbix
│
├── screenshots/
│   └── dashboard.png
│
├── README.md
└── LICENSE
Project Goal
The goal of this project is to build a practical personal race-planning tool while developing Power BI skills in:
- data preparation
- data modelling
- Power Query
- DAX
- KPI design
- interactive filtering
- conditional formatting
- dashboard layout and visual design
Future Development
Possible future improvements include:
- completed-race statistics
- planned vs. actual results
- personal-best tracking
- additional race categories
- full 12-month calendar view
- improved race timeline
- historical comparison across multiple seasons
Status
The project is currently in development and will continue to evolve as the 2027 race schedule is updated.
