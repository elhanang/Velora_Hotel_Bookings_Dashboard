# 🏨 Velora Luxury Hotel — Booking Analytics Dashboard

![Velora Dashboard](/images/Velora_Luxury_Hotel_Bookings_Dashboard.png)
*Velora Luxury Hotel Dashboard*

[Download the ready to use file.](Velora_Luxury_Hotel_Dashboard.pbix)
The file is fully self-contained.

## 📌 The Brief

The CEO of Velora Luxury Hotel needs to know what's going on in the 
business. Not in a spreadsheet. Not in a report that takes an hour to 
read. In a single view, updated and interactive, that answers the most 
important questions about bookings, revenue, cancellations, and guest 
behaviour at a glance.

That's what this dashboard delivers.

---

## 📊 The Data

The dataset contains hotel reservation records with the following fields:
Booking ID, Booking Date, Booking Channel, Loyalty Level, Status, Stay 
Date, Number of Nights, Room Rate, Revenue, How Far Away, How Far Away 
Bucket, Day Name, and Day of Week.

Several columns were engineered inside Power Query before any visualization began.

**Number of Nights** was calculated from check-in and check-out dates.
**Day Name and Day of Week** were derived from the Stay Date to enable 
weekday vs. weekend analysis.
**How Far Away** was calculated by subtracting the Booking Date from the 
Stay Date to find how many days ahead each reservation was made.
**How Far Away Bucket** was built using a conditional column in Power Query, 
grouping the noisy day counts into four buckets: Before a Week, Before 2 
Weeks, Before 4 Weeks, and More Than 4 Weeks.

---

## ❓ Numbers That Matter

| Metric | Value |
|---|---|
| Booking Count | 5K |
| Cancellation Rate | 28.7% |
| Total Revenue | $1M |
| Total Room Nights | 9K |
| Average Room Rate | $147.9 |
| Date Range | 6 Sep 2024 — 31 Oct 2024 |

---

## 🖥️ What the Dashboard Shows

**How Many Stays Per Day?**
A daily stay trend line tracking occupancy from September through October, 
revealing a sharp peak around 29 September before gradually declining 
toward the end of October.

**Weekdays or Weekends?**
A bar chart comparing booking volume across all seven days of the week. 
Thursday and Friday lead, with Sunday recording the lowest volume, giving 
the hotel clear direction on which days drive the most demand.

**Who Stays With Us?**
A horizontal bar chart breaking down bookings by loyalty tier. Non-members 
dominate at 1,940 bookings, followed by Essential (983), Preferred (517), 
Select (372), Premier (421), Elite (348), and Iconic (194). The gap between 
non-members and loyalty members is significant and points to an opportunity 
to convert first-time guests into program participants.

**How Far Ahead Do They Book?**
A bar chart showing booking lead time distribution. The majority of guests 
book less than a week in advance, with volume dropping as lead time increases. 
Only a small segment books more than four weeks out.

**Loyalty Level × Booking Channel Matrix**
A conditional formatting matrix cross-tabulating loyalty tier against booking 
channel (App, At the Hotel, Connect, GDS, Other, Phone, Velora direct). 
Non-members book most heavily through At the Hotel (842) and App (385). 
Essential members show strong GDS activity (207) and Velora direct (260), 
pointing to different acquisition strategies working across different segments.

**One Night or More? / Loyal or Not?**
Two donut charts on the left sidebar give the CEO an immediate read on 
stay length (single vs. multi-night) and loyalty split (members vs. 
non-members), with roughly equal splits visible across both.

---

## 🧮 DAX Measures

```dax
Booking Count = COUNTROWS(bookings)

Total Revenue = SUM(bookings[Revenue])

Total Room Nights = SUM(bookings[Number of nights])

Avg. Room Rate = DIVIDE([Total Revenue], [Total Room Nights])

Cancellation Count = 
    CALCULATE([Booking Count], bookings[Status] = "Cancelled")

Cancellation Pct = DIVIDE([Cancellation Count], [Booking Count])

Single Night Booking Count = 
    CALCULATE([Booking Count], bookings[Number of nights] = 1)

Multi Night Booking Count = 
    CALCULATE([Booking Count], bookings[Number of nights] > 1)

Loyal Customer Booking Count = 
    CALCULATE([Booking Count], bookings[Loyalty Level] <> "0.Non-member")

Not Loyal Customer Booking Count = 
    CALCULATE([Booking Count], bookings[Loyalty Level] = "0.Non-member")
```

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Power BI Desktop | Report design, visuals, and interactivity |
| Power Query | Data preparation and column engineering |
| DAX | Custom KPI measures and calculated fields |
| Conditional Formatting | Loyalty × channel matrix heat map |
| Power BI Themes | Custom dark gold color scheme matching Velora branding |

---

## 🧠 What I Learned Building This

Working with booking data taught me that the most valuable insights are 
rarely in the totals. The loyalty matrix revealed that different customer 
segments use completely different booking channels, which means a single 
channel strategy would miss most of the audience. The lead time distribution 
showed that last-minute bookings dominate, which has direct implications 
for how the hotel should manage dynamic pricing and room availability.

The Power Query work on this project was also more involved than most. 
Engineering the How Far Away Bucket column using conditional logic before 
the data even reached the model made the final visualizations cleaner and 
more meaningful than they would have been with raw day counts.

---

## ✅ Conclusion

This dashboard gives Velora's leadership a fast, honest read on the 
business. The 28.7% cancellation rate is the most pressing number on 
the page and warrants deeper investigation into which channels and 
loyalty tiers are cancelling most. The dominance of non-members across 
all booking channels points to an underperforming loyalty program that 
represents one of the clearest growth levers available to the business.

---

## 📁 Data Source

[Velora Luxury Hotel reservation data.](data\reservations-1.xlsx)

---
[Quick insights](https://app.powerbi.com//groups/me/insights/c60ac0a7-9336-4a02-892c-41401e53ec02?insightsSource=Desktop)

---

## 👤 Author

**El-hanan Garba** — Data Analyst & BI Professional

[![Portfolio](https://img.shields.io/badge/Portfolio-1a472a?style=for-the-badge&logo=githubpages&logoColor=white)](https://elhanang.github.io/El-hananGarba.github.io/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/el-hanan-garba)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/elhanang)