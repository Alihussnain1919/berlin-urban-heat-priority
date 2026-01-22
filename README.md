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
* **Playgrounds:** [Spielplätze Berlin](https://daten.berlin.de/datensaetze/spielpl%C3%A4tze-berlin).
* **Street Trees:** [Baumbestand Berlin - Straßenbäume](https://daten.berlin.de/datensaetze/baumbestand-berlin-stra%C3%9Fenb%C3%A4ume).
* **Heat Index:** [Physiologisch Äquivalente Temperatur (PET) um 14:00 Uhr](https://pkk.berlin.de/).

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
* `Presentation.pdf`: The final Master Project presentation slides.
* `graphs/`: Folder containing exported high-resolution PNGs of the results.
