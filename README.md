# 🎬 Netflix dbt Project

An end-to-end **dbt (data build tool)** project that transforms raw Netflix/MovieLens-style data into clean, tested, and well-documented analytics-ready models on **Snowflake**.

## 📌 Overview

This project follows a layered dbt architecture:

```
Raw Sources → Staging Models → Dimension/Fact Models → Mart Models
```

- **Staging (`src_*`)** — cleans and standardizes raw source data
- **Dimensions (`dim_*`)** — movies, users, genome tags
- **Facts (`fct_*`)** — ratings (incremental) and genome relevance scores
- **Marts (`mart_*`)** — business-ready aggregated tables
- **Snapshots** — tracks slowly changing user tag history over time
- **Tests** — data quality checks (not_null, unique, custom relevance score test)

## 🛠️ Tech Stack

- [dbt-core](https://www.getdbt.com/) — data transformation
- Snowflake — data warehouse
- dbt-utils package
- Python (virtual environment)

## 📁 Project Structure

```
netflix/
├── models/
│   ├── staging/     # Cleaned raw sources
│   ├── dim/          # Dimension tables
│   ├── fct/           # Fact tables
│   ├── mart/         # Business-facing mart models
│   └── sources.yml   # Source table definitions
├── snapshots/         # SCD tracking (user tags)
├── tests/             # Custom data tests
├── macros/            # Reusable Jinja macros
├── seeds/             # Static CSV reference data
└── dbt_project.yml    # Project configuration
```

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/your-username/netflix-dbt-project.git
cd netflix-dbt-project/netflix
```

### 2. Set up a virtual environment
```bash
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # macOS/Linux
```

### 3. Install dbt
```bash
pip install dbt-snowflake
```

### 4. Configure your profile
Create a `profiles.yml` in your `~/.dbt/` folder (this file is **not** committed to the repo for security) with your Snowflake connection details.

### 5. Install dbt packages
```bash
dbt deps
```

### 6. Run the models
```bash
dbt run
```

### 7. Run tests
```bash
dbt test
```

### 8. Generate documentation
```bash
dbt docs generate
dbt docs serve
```

## 🧪 Data Quality

This project includes:
- `not_null` and `unique` tests on key columns
- Referential integrity tests between fact and dimension tables
- A custom test ensuring genome relevance scores are always positive

## 📄 License

This project is licensed under the MIT License.
