# SQL Problem Solving

Three query sets written against a modeled healthcare schema (`Patients`, `Encounters`,
`Vitals`, `LabResults`, `PatientMedication`, `Providers`, `Clinics`, `ProviderSchedule`). Each is
written as a multi-stage CTE pipeline and ends in a `CREATE OR ALTER VIEW`, so the output plugs
directly into a BI-ready semantic layer (e.g. a Power BI or Tableau data model).

All queries are T-SQL (SQL Server syntax).

## [`patient_risk_stratification.sql`](patient_risk_stratification.sql)

Scores each patient 0–6 on blood pressure, heart rate, and 90-day ED utilization, then buckets
them into **Low / Moderate / High Risk** for care-management prioritization.

**Techniques:** 7-stage CTE pipeline · window functions (`ROW_NUMBER`) for latest-vitals lookup ·
pivoted vitals via `MAX(CASE ...)` · weighted `CASE` risk scoring

## [`encounter_cycle_times.sql`](encounter_cycle_times.sql)

Validates raw timestamp data, calculates stage-by-stage cycle times (arrival → triage → room →
provider → discharge), then ranks providers and clinics on throughput.

**Techniques:** multi-table joins · data-quality validation via `CASE` · `DATEDIFF` cycle-time
calculations · `RANK()` / `ROW_NUMBER()` for provider and clinic throughput ranking

## [`chronic_meds_compliance.sql`](chronic_meds_compliance.sql)

Flags patients on chronic medications (Metformin, Lisinopril, Atorvastatin) as compliant or
non-compliant based on whether the right lab test was run within the clinically appropriate
window, then rolls compliance rate up by medication.

**Techniques:** deduplication via `ROW_NUMBER()` · drug-specific `CASE` compliance logic ·
compliance-rate calculation with `CAST` + `NULLIF` to guard against divide-by-zero

## Running these queries

These were written against a modeled schema for demonstration purposes. To run them yourself,
create matching tables (`Patients`, `PatientDiagnoses`, `Vitals`, `Encounters`, `EncounterEvents`,
`Providers`, `Clinics`, `ProviderSchedule`, `PatientMedication`, `LabResults`) or adapt the table
and column names to your own environment.
