# 🌳 Assessing Heat Risk and Shade in Berlin Playgrounds
### Urban Technology Master Project | Ali Hussnain

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/Berlin-Playground-Heat-Analysis/blob/main/Berlin_Heat_Risk.ipynb)

## 📌 Project Overview
This project addresses a critical urban problem in Berlin: the vulnerability of children to extreme heat in public spaces. By integrating geospatial data on playground locations, street tree canopy, and thermal comfort indices (PET), this study identifies playgrounds where the risk is highest and shade is most needed.

## 🛠️ Technical Workflow
* **Coordinate Reference System (CRS):** All data was transformed from EPSG:4326 to **EPSG:25833 (ETRS89 / UTM zone 33N)** to ensure accurate metric measurements for buffers and canopy areas.
* **Spatial Analysis:** Created 50-meter buffers around 1,879 playground polygons.
* **Canopy Estimation:** Used tree crown diameters (`kronedurch`) to calculate the percentage of shaded area within each playground buffer.
* **Risk Modeling:** Developed a weighted Multi-Criteria Analysis (MCA):
    * **60% Weight:** Heat Stress (PET Index at 14:00).
    * **40% Weight:** Shade Deficit ($1 - \text{Canopy Percentage}$).

## 📊 Data Sources
Due to GitHub file size limits (>500 MB), raw datasets are not included in this repository. Please download them from the official **Berlin Open Data Portal**:
* **Street Trees:** [Baumbestand Berlin - Straßenbäume](https://drive.google.com/file/d/1jE3q-Ng7HFfBy-D3sdnfJ0fLUPpi2rs0/view?usp=sharing).
* **Heat Index:** [Physiologisch Äquivalente Temperatur (PET) um 14:00 Uhr](https://drive.google.com/file/d/1nk6nH8Cj2U4QNfdipV1TbaZkvVgItQ6X/view?usp=sharing).
* **Playgrounds:** [Spielplätze Berlin](https://drive.google.com/file/d/1aupzzbIPAYuRMoXouygcHOEWyCy5RL1-/view?usp=sharing).


## 📈 Key Results
The analysis produced a "Priority Action List" for city planners. Highlights include:
* **High Priority Zones:** Playgrounds with a risk index exceeding 0.75 require urgent intervention.
* **District Disparity:** Districts like Marzahn-Hellersdorf and Spandau show significantly higher average heat risks compared to more shaded districts.
* **Extreme Cases:** Individual playgrounds were identified with risk indices as high as 0.97 due to a total lack of tree canopy in high-heat zones.

## 🚀 How to Run
1. Click the **"Open in Colab"** badge at the top of this page.
2. Mount your Google Drive or upload the raw `.json` files to the Colab sidebar.
3. Update the file paths in the second cell of the notebook.
4. Run all cells to generate the interactive map and statistical graphs.

## 📁 Repository Structure
* `Berlin_Heat_Risk.ipynb`: The primary Python notebook containing all analysis and visualization code.
* `requirements.txt`: List of necessary Python libraries (Geopandas, Folium, etc.).
* `graphs/`: Folder containing exported high-resolution PNGs of the results.


# 📈 Project Visualizations

This folder contains the graphical results of the Berlin Playground Heat & Shade analysis. These charts were generated using `matplotlib` and `seaborn` within the project notebook.

### 1. Risk Index Distribution
* **File:** `risk_histogram.png`
* **Interpretation:** Displays how many playgrounds fall into specific risk categories. The "tail" on the right represents the most vulnerable sites.

### 2. Priority Classification
* **File:** `priority_bar_chart.png`
* **Interpretation:** A summary of playgrounds categorized by action priority (High, Medium, Low) based on the 0.75 and 0.50 thresholds.

### 3. District-Level Analysis
* **File:** `district_comparison.png`
* **Interpretation:** Comparison of the mean risk index across all Berlin districts. Higher bars in darker colors indicate districts requiring systemic intervention.

### 4. Heat vs. Shade Correlation
* **File:** `heat_vs_shade_scatter.png`
* **Interpretation:** Visualizes the trade-off between thermal comfort (PET) and green infrastructure (Canopy %). The "Critical Zone" is the bottom-right quadrant.
