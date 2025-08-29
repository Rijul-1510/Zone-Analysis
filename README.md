# ZONE ANALYSIS 
# Overview 
```bash
This project builds a zone intelligence layer for sales and marketing insights.
By integrating sales data with geospatial analysis, it enables businesses to evaluate performance across cities, subzones, and outlets.
The pipeline supports data-driven decisions for marketing, operations, and supply chain optimization.
```
# Key Features 
``` bash
 - Automated Data Extraction from PostgreSQL using SQLAlchemy.
 - Geospatial Mapping of cities and subzones with geopy + folium.
 - Data Normalization & Scaling using MinMaxScaler.
 - Dimensionality Reduction with PCA for zone-based clustering.
 - Interactive Visualizations: sales heatmaps, performance comparisons.
 - Zone Intelligence Layer: insights for marketing, retention, and discount optimization.
```
# System Architecture 

<img width="954" height="551" alt="diagram-export-8-30-2025-12_22_52-AM" src="https://github.com/user-attachments/assets/6679b071-1ffe-48bb-9b9c-72ee38130226" />

# Installation 
``` bash
git clone <repo_url>
cd <repo_url>
```

# Workflow 
``` bash
1. Data Extraction
   - Fetches sales data from PostgreSQL using SQLAlchemy.
   - Ensures only valid transactions are included (e.g., closed orders).
2. Preprocessing & Feature Engineering
   - Cleans missing/duplicate values.
   - Extracts relevant metrics: total sales, discounts, order counts, retention rates.
3. Feature Scaling
   - Applies MinMaxScaler to normalize features, making them comparable across outlets.
4. Zone Score Calculation
   - A composite Zone Score is created for each subzone.
   - Differenct weights balance sales growth, customer loyalty, and profitability impact.
   - Higher scores indicate stronger business performance.
5. PCA & Pattern Analysis
   - PCA reduces multi-feature zone data into 2–3 dimensions.
   - Helps identify hidden patterns and separates high vs low performing clusters.
6. Visualization
   - Heatmaps → Compare performance metrics across cities/subzones.
   - Folium Maps → Interactive maps for outlet distribution and zone scores.
   - PCA Scatter Plots → Visualize clusters of similar-performing zones.
7. Insights
   - Identify top zones for expansion or marketing push.
   - Detect underperforming zones needing discount or retention strategies.
```
# Results and Performance 
# Zone Score Calculation 
At the top, you see:
  Thresholds for zone classification: [0.00368651 0.0280289]
These thresholds are automatically calculated using PCA to split the zones into Low, Medium, and High performing categories.
  -  ≤ 0.0036 → Low
  -  0.0036 – 0.0280 → Medium
  -  >0.0280 → High

![WhatsApp Image 2025-08-30 at 00 25 47_da59be3f](https://github.com/user-attachments/assets/71c80784-a6ed-45a2-b7b0-2c8c13650d8f)

# Results 
# City specific 
![WhatsApp Image 2025-08-30 at 00 30 10_065b6875](https://github.com/user-attachments/assets/5d81c499-5db5-4cc3-9a9f-125caa76a256)

The map highlights different subzones of Delhi.
Each subzone is marked with a colored point.
The popup shows details like City, Subzone, Zone, and the calculated Zone Score.
Colors represent performance levels:
 - Green → High performing zone
 - Orange → Medium performing zone
 - Red → Low performing zone
This helps quickly see which parts of Delhi are performing well and which need attention.
# Zone specific
![WhatsApp Image 2025-08-30 at 00 28 34_ff165d3d](https://github.com/user-attachments/assets/c4ed0a67-b20d-4679-ba21-ba298241567f)

This map provides a nationwide view of zones and subzones.
Each city/subzone is represented with a point.
Just like in the Delhi map, colors indicate Low, Medium, or High performance.
The visualization gives a comparative view across cities and regions, showing where performance is strong and where gaps exist.

# Insights 
![WhatsApp Image 2025-08-30 at 00 30 59_e65d14a3](https://github.com/user-attachments/assets/55904c32-03f4-41fa-be67-1cc3d8960517)

1. Dinner = Primary Revenue Driver 
   - With the majority of orders coming during dinner, marketing spends, promotions, and delivery fleet allocation should heavily prioritize evening hours.
   - Restaurants can also curate special dinner menus and bundles to maximize average order value (AOV).
2. Lunch = Office-Centric Growth Opportunity 
   - IT hubs and business districts (Hinjewadi, Magarpatta, Kalyani Nagar) show strong lunch demand.
   - Brands should partner with corporate meal plans or subscription-based offers to capture recurring office crowd demand.

![WhatsApp Image 2025-08-30 at 00 31 15_6779918f](https://github.com/user-attachments/assets/1d3724b0-6b97-4b6c-ab16-e478187c4419)

3. Breakfast = Low ROI Segment 
   - Demand is consistently weak across the city.
   - Unless tied to niche categories (e.g., coffee chains, bakeries), heavy investment here may not pay off.
4. Snacks & Late-Night = Niche Differentiator
   - Strong presence in student/nightlife areas (Viman Nagar, Koregaon Park).
   - Brands focusing on quick-serve, fast food, or cloud kitchens can leverage late-night demand with targeted offers.
![WhatsApp Image 2025-08-30 at 00 31 57_eca28e6a](https://github.com/user-attachments/assets/7a74c8ef-0a7d-4ee8-bea3-504bd265d0d1)

5. Zone Powerhouses Drive the Market
   - A handful of zones (Baner, Hinjewadi, Magarpatta, Kalyani Nagar) generate the lion’s share of orders.
   - These zones should be priority clusters for expansion, marketing campaigns, and operational excellence, while low-performing areas may need a lean model (fewer discounts, shared kitchens).

# Future Improvement 
1. Incorporating Customer Segments
   - Enrich zone intelligence by factoring in customer demographics, retention, and loyalty behavior.
   - Business Value: Enables personalized offers (office-goers at lunch vs. families at dinner).
2. Competitor Benchmarking Layer
   - Add competitive density metrics (number of outlets per cuisine per zone).
   - Business Value: Helps identify over-saturated vs. underserved zones for smart expansion.
3. Integration with External Data
   - Use weather APIs, traffic data, and local events to refine demand prediction.
   - Business Value: Helps allocate fleets better (rainy evenings = surge in delivery demand)



