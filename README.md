# 🚖 OLA Ride Booking Analytics Dashboard

An end-to-end data analytics project that analyzes OLA ride booking data using **SQL** (data cleaning & querying), **Excel** (data preprocessing & pivot analysis), and **Power BI** (interactive dashboard & visualization) to uncover insights on bookings, revenue, cancellations, and customer/driver behavior.

---

## 📌 Project Overview

Ride-hailing platforms generate massive volumes of trip data every day. This project simulates a real-world business analytics workflow — taking raw OLA booking data, cleaning and transforming it, running analytical SQL queries to answer key business questions, and finally building an interactive Power BI dashboard for stakeholders to monitor performance at a glance.

**Goal:** Help business/operations teams understand ride trends, revenue performance, cancellation patterns, and customer/vehicle insights to support data-driven decision-making.

---

## 🎯 Objectives

- Track overall booking volume and revenue trends over time
- Identify peak booking hours/days and demand patterns
- Analyze ride cancellations (by customer vs. by driver) and their root causes
- Evaluate vehicle type performance (Mini, Sedan, Auto, Bike, Prime, etc.)
- Understand customer ratings vs. driver ratings
- Segment revenue by payment method
- Provide a single interactive dashboard for quick decision-making

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Excel** | Initial data cleaning, exploration, and pivot table analysis |
| **SQL (MySQL/SQL Server)** | Data cleaning, transformation, and business-question queries |
| **Power BI** | Data modeling (DAX) and interactive dashboard/visualization |

---

## 📂 Project Structure

```
OLA-Dashboard/
│
├── data/
│   └── ola_bookings_raw.csv          # Raw dataset
│
├── excel/
│   └── OLA_Data_Cleaning.xlsx        # Data cleaning & pivot analysis
│
├── sql/
│   └── ola_queries.sql               # SQL scripts for business questions
│
├── powerbi/
│   └── OLA_Dashboard.pbix            # Power BI dashboard file
│
├── images/
│   └── dashboard_preview.png         # Dashboard screenshots
│
└── README.md
```

---

## 🧹 Data Cleaning & Preparation

- Removed duplicate and null records
- Standardized date/time formats for booking and pickup timestamps
- Created new calculated columns (e.g., booking status, trip duration, revenue per km)
- Handled inconsistent categorical values (vehicle types, payment methods)
- Used Excel Pivot Tables for a first pass at exploratory analysis before moving to SQL

---

## 🗃️ SQL Analysis

Key business questions answered using SQL:

1. What is the total number of successful vs. cancelled bookings?
2. What is the overall revenue generated, and how does it trend by day/month?
3. Which vehicle type generates the highest revenue and booking volume?
4. What are the top reasons for ride cancellations (customer-side vs. driver-side)?
5. What is the average customer rating and driver rating by vehicle type?
6. Which payment method is most preferred by customers?
7. What are the peak hours/days for ride bookings?

> Example query:
```sql
SELECT 
    Vehicle_Type,
    COUNT(Booking_ID) AS Total_Bookings,
    SUM(Booking_Value) AS Total_Revenue,
    AVG(Driver_Ratings) AS Avg_Driver_Rating
FROM ola_bookings
WHERE Booking_Status = 'Success'
GROUP BY Vehicle_Type
ORDER BY Total_Revenue DESC;
```

Full query set available in [`sql/ola_queries.sql`](./sql/ola_queries.sql).

---

## 📊 Power BI Dashboard

The dashboard consists of multiple pages/views:

1. **Overall Summary** – Total bookings, total revenue, cancellation rate, success rate (KPI cards)
2. **Vehicle Type Analysis** – Revenue and booking volume by vehicle category
3. **Cancellation Analysis** – Breakdown of cancellations by customer vs. driver and reasons
4. **Ratings Analysis** – Customer and driver rating distribution
5. **Revenue Analysis** – Revenue trends by date, payment method, and distance

### Key DAX Measures
```
Total Revenue = SUM(ola_bookings[Booking_Value])

Cancellation Rate = 
DIVIDE(
    CALCULATE(COUNTROWS(ola_bookings), ola_bookings[Booking_Status] = "Cancelled"),
    COUNTROWS(ola_bookings)
)

Avg Ride Distance = AVERAGE(ola_bookings[Ride_Distance])
```

### Dashboard Preview
> Add your exported dashboard screenshots to the `images/` folder and reference them below:

```
![Dashboard Preview](images/dashboard_preview.png)
```

---

## 📈 Key Insights

*(Update this section with your actual findings once analysis is complete)*

- Majority of cancellations occur due to **[driver/customer]**-side reasons
- **[Vehicle type]** generates the highest revenue share
- Peak booking hours are between **[X AM/PM – Y PM]**
- **[Payment method]** is the most preferred mode of payment
- Average customer rating is **X.X**, while average driver rating is **X.X**

---

## 🚀 How to Use This Project

1. Clone or download this repository
2. Open `excel/OLA_Data_Cleaning.xlsx` to review the raw data cleaning steps
3. Run the scripts in `sql/ola_queries.sql` against your database to reproduce the analysis
4. Open `powerbi/OLA_Dashboard.pbix` in Power BI Desktop to explore the interactive dashboard
5. Use the filters/slicers in the dashboard to explore bookings by date, vehicle type, and status

---

## 📌 Future Improvements

- Automate data refresh using Power BI Service / scheduled SQL ETL
- Add predictive analytics (e.g., cancellation likelihood, demand forecasting)
- Integrate real-time data via API instead of static CSV

---

## 🙋‍♂️ Author

**[Your Name]**
📧 [your.email@example.com]
🔗 [LinkedIn](https://linkedin.com/in/yourprofile) | [Portfolio](https://yourportfolio.com)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
