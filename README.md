# Open Tickets Dashboard in the OTRS/Znuny System

Author: Flavio Ribeiro Córdula [![LinkedIn](https://img.shields.io/badge/LinkedIn--blue?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/cordulaflavio)

---

## 1. Introduction

This project, initiated before my involvement, was developed to monitor and analyze the flow of tickets in UFPB's OTRS (now Znuny) system.

My contributions included:

- Creation of the `fato_atendimento_historico` table, consolidating essential support data.
- Development of a functional dashboard in Metabase, aimed at the Information Technology Superintendence (STI) managers.
- Dimensional data modeling, with fact and dimension tables supporting consistent analysis and visualization.
- Generation of **materialized views**, used as the data source for Metabase dashboards.

The main objective of this project is to provide a practical and accessible tool for STI managers — including department heads and the superintendent — to monitor the volume, distribution, and status of tickets submitted by the UFPB academic community.

The dashboard offers visualizations such as:

- Volume of tickets by status over time.
- Tickets grouped by queue, service, time, and date.
- SLA compliance monitoring.
- Ranking of users with the highest number of tickets.

In addition to improving management, the project promotes **internal transparency**, enhances **resource allocation**, and supports the **prioritization of critical demands**.

## 2. Reach

- Reaches **90+ STI staff members**, including IT technicians and analysts.
- Used by **all IT managers** and the **STI superintendent**.
- Some views are also used by **institutional managers from other departments**.

## 3. Production Timeline

- In production since **2020**.
- As of 2025, it is being phased out due to the integration of the OTRS system into **GitLab**, which now automatically receives tickets as *issues*.
- Ticket monitoring and analysis will migrate to a new dashboard based on data extracted from GitLab.

> See also: [GitLab Analytics Project](https://github.com/cordulaflavio/gitlab-analytics) *(example link)*

## 4. Technologies Used

- **Pentaho Data Integration (PDI)**: For developing ETL processes that feed the analytical database.
- **SQL (MySQL and PostgreSQL)**: For building fact and dimension tables, data modeling, and view creation.
- **CRON**: For scheduling periodic data updates.
- **Metabase**: For building dashboards with controlled access and interactive visualizations.

## 5. Project Architecture

The solution is part of a **departmental Data Warehouse architecture**, composed of multiple thematic **Data Marts**. This project refers to the **`dm_otrs` data mart**, which centralizes and delivers analytical information regarding OTRS/Znuny tickets.

The overall process follows an **ETL approach**, with data extraction from production, transformation, and loading into an analytical structure modeled as a star schema.

### 5.1. Process Steps

1. **Extraction (E)**:
   - Data extracted directly from the OTRS/Znuny production database (MySQL).
   - Use of SQL queries in Pentaho for both full and incremental loads.

2. **Transformation (T)**:
   - Creation of surrogate keys.
   - Date handling, data normalization, and standardization of fields.
   - Calculation of indicators such as handling time and SLA delay.

3. **Loading (L)**:
   - Transformed data is loaded into a PostgreSQL database.
   - Data organized into **fact and dimension tables** under the `dm_otrs` data mart.
   - Creation of **materialized views** to optimize Metabase queries.

### 5.2. Data Modeling

- **Dimension Tables**:
  - `dim_sla` — Service Level Agreements.
  - `dim_service` — Types of services related to tickets.
  - `dim_queue` — Support queues.
  - `dim_users` — Requesters and agents.
  - `dim_ticket_state` — Ticket states.

- **Fact Table**:
  - `fato_atendimento_historico` — Stores events related to ticket handling, linking all dimensions and recording metrics like duration, SLA, and status.

### 5.3. Pentaho Transformations

Below is one of the transformations developed in Pentaho Data Integration (PDI), responsible for populating the `fato_chamado_atendimento` fact table:

![Pentaho Transformation - fato_chamado_atendimento](https://github.com/cordulaflavio/OTRS-Data-Analytics/blob/main/images/Pentaho-03-fato_chamado_atendimento.png)

Other PDI screenshots are available in the [`images/`](images/) folder of the project.

## 6. Dashboard

> ⚠️ All data shown in the images below has been anonymized. There is no exposure of sensitive information or user identification. Data security and privacy were ensured throughout the process.

![STI Dashboard](https://github.com/cordulaflavio/OTRS-Data-Analytics/blob/main/images/Dashboard-OTRS-STI.png?raw=true)
