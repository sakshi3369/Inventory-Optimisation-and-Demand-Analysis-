
📦 Inventory Optimization & Demand Forecasting
A end-to-end data science project that combines inventory analytics, SQL-based supply chain intelligence, and time series demand forecasting to help businesses reduce costs, prevent stockouts, and optimize reorder strategies.

🗂️ Project Structure
inventory-optimization-demand-forecasting/
│
├── inventory-optimization-demand-forecasting.ipynb   # Core analysis notebook
├── time_series_extension.ipynb                        # Time series forecasting extension
├── README.md
└── data/
    └── Inventory_Dataset.csv                          # Source dataset
    Notebook Link: https://www.kaggle.com/code/sakshichougule/inventory-optimization-demand-forecasting

📌 Problem Statement
Supply chain managers face three persistent challenges:

Overstocking — capital tied up in slow-moving products increases holding costs
Stockouts — unmet demand drives shortage costs and lost revenue
Reactive ordering — reorder decisions based on historical averages instead of forecasts

This project addresses all three by building a data-driven inventory intelligence system from scratch.

📊 Dataset
Source: Inventory Dataset for Complex Supply Chains — Kaggle
ColumnDescriptionproduct_idUnique product identifierdateTransaction / observation datehistorical_demandUnits demanded per periodcurrent_inventoryUnits currently in stockholding_costCost to hold one unit in inventoryordering_costFixed cost per order placedshortage_costCost incurred per unit of unmet demandlead_time_daysDays between order placement and receiptreorder_pointInventory level at which reorder is triggereddemand_variabilityVariability coefficient of demandwarehouse_idWarehouse location identifier

🔬 Analysis Modules
1. 🧹 Data Cleaning & Transformation

Datetime parsing and sorting by product_id × date
Forward-fill for missing values
Feature engineering: total_cost = holding + ordering + shortage

2. 📈 Demand & Cost Analysis

Demand distribution across products and warehouses
Cost driver identification (holding vs ordering vs shortage)
Holding–shortage cost tradeoff visualisation
Cost efficiency score per product (cost per unit demanded)

3. 🏭 Inventory Health Metrics (SQL)
AnalysisKey FindingService LevelAverage 82%; 8% of products fall below 70%Safety StockRequired buffer ranges 46–176 units per productOverstock DetectionSome products carry 390+ units of surplus stockFast vs Slow Movers16% fast-moving, 69% medium, 15% slow-movingLead Time Risk52% of products face high delay risk (>7.5 avg days)Demand Volatility100% of products in moderate volatility segmentInventory TurnoverRanges 7x–21x, average 13.85xWarehouse BalanceLoad spread 19%–21% across 5 warehouses (balanced)
4. 📐 Economic Order Quantity (EOQ)
Classic EOQ model applied per product:
EOQ = √(2 × Annual Demand × Ordering Cost / Holding Cost)
5. ⏰ Time Series Forecasting (Extension Notebook)
StepTechniquePurposeStationarity TestADF TestDetermine ARIMA differencing orderDecompositionSeasonal DecomposeSeparate trend, seasonality, residualForecastingARIMA(1,0,1)30-day portfolio demand forecastForecastingFacebook ProphetPer-product forecasts with seasonalityDynamic Safety StockRolling Std DevAdaptive buffer stock vs static formulaDynamic EOQForecasted DemandForward-looking order quantitiesAnomaly DetectionRolling Z-ScoreFlag demand spikes and drops

📉 Key Results
MetricResultARIMA Forecast MAPE7.70% (Good — under 10%)Demand TrendFlat (~120 units/day) — mature product lifecycleSeasonality StrengthWeak — no seasonal inventory buildup neededAnomalies DetectedFlagged via rolling z-score (±2.5σ threshold)Dynamic vs Static Safety StockAdapts to demand shifts; reduces over-buffering

💼 Business Impact

"We can predict daily inventory demand with ~92% accuracy, enabling smarter purchasing, leaner stock levels, and fewer costly stockouts — without adding warehouse capacity."


Procurement: Replace reactive ordering with 30-day demand forecasts
Finance: Budget inventory spend confidently using stable demand signals
Operations: Use dynamic safety stock to absorb real variability, not guesses
Strategy: Identify fast/slow movers to rationalise SKU portfolio


🛠️ Tech Stack
ToolUsagePython 3Core languagePandas / NumPyData manipulationMatplotlib / SeabornVisualisationSQLite3In-memory SQL analyticsStatsmodelsARIMA, ADF test, decompositionProphet (Meta)Per-product forecastingKaggle NotebooksDevelopment environment

