# Data Analytics Projects — Naveen Gupi

Power BI dashboards and SQL problem-solving work, kept separate from the
[portfolio site repo](https://github.com/naveen-metaflux/portfolio) so this repo can stand on its
own as a browsable/cloneable body of work.

## Structure

```
data-analytics-projects/
├── power-bi/
│   ├── car-sales-dashboard/
│   │   ├── Car_sales.pbix
│   │   ├── README.md
│   │   └── screenshots/
│   └── candy-sales-dashboard/
│       ├── Candy_Sales.pbix
│       ├── README.md
│       └── screenshots/
└── sql/
    ├── patient_risk_stratification.sql
    ├── encounter_cycle_times.sql
    ├── chronic_meds_compliance.sql
    └── README.md
```

## Power BI Dashboards

| Project | Focus | File |
|---|---|---|
| [Car Sales Analytics](power-bi/car-sales-dashboard/) | Automotive retail — revenue, YoY growth, regional & body-style performance | `Car_sales.pbix` |
| [Candy Sales Profitability](power-bi/candy-sales-dashboard/) | CPG — margin analysis layered on top of revenue reporting | `Candy_Sales.pbix` |

Open any `.pbix` file in **Power BI Desktop** (free) to explore the full data model, DAX measures,
and interactive report.

## SQL Problem Solving

Three query sets written against a modeled healthcare schema (patients, encounters, vitals, labs,
medications). See [`sql/README.md`](sql/README.md) for details on each.

## Requirements

- **Power BI Desktop** (free) to open `.pbix` files — [download here](https://www.microsoft.com/en-us/power-platform/products/power-bi/downloads)
- Any SQL Server-compatible client to review/run the `.sql` files (written for T-SQL / SQL Server syntax)
