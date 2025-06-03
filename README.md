# Interactive Data Visualization Dashboard for TB Using D3

## 1. Project Objective
Create an interactive dashboard visualizing Tuberculosis (TB) relationships across multiple dimensions (geography, time, and type) using D3.js. The goal is to uncover patterns, provide insightful analysis, and facilitate exploration through dynamic visualizations.

---

## 2. Dataset Details
The dataset `updated_tb_dataset.csv` contains:
- **latitude & longitude**: Geographic coordinates for plotting  
- **year**: Year of the recorded event  
- **country**: Country name  
- **Relationship Type & Path**: Descriptive relationship information  
- **TB Cause**: Primary causes of TB spread  
- **People Affected & Deaths**: Impact metrics  
- **Deaths Due to Cause Treatment Available**: Treatment availability details  

---

## 3. Visualizations

### 3.1. Force-Directed Graph (`Forced.html`)
- **Purpose**: Visualize relationships between TB causes and affected countries.  
- **Data Prep**: Group by country and TB cause; aggregate “People Affected.”  
- **Nodes**:
  - Blue = countries  
  - Green = TB causes  
  - Size ∝ “People Affected”  
- **Edges**:
  - Thickness ∝ number of people affected on that link  
- **Interactivity**:
  - Hover for tooltips (country, cause, affected count)  
  - Click to zoom and show details in a side panel  
  - Filters: year, country, cause  
- **D3 Features**:
  - `d3.forceSimulation` for layout  
  - `d3.zoom` for pan/zoom  
  - Dynamic tooltips and side panel  

---

### 3.2. Geographic Map Chart (`Map.html`)
- **Purpose**: Show geographic distribution of TB cases on a world map.  
- **Integration**: Leaflet.js for base map + D3.js for overlays.  
- **Markers**:
  - Circles or pins at lat/long  
  - Color-coded by TB cause; adjustable opacity  
- **Interactivity & Filters**:
  - Dropdowns: filter by region or cause  
  - Year-range slider for time filtering  
  - Death-count threshold slider  
- **Legend**: Dynamic legend to toggle TB causes  
- **D3 Features**:
  - `d3.csv` to load/preprocess data  
  - Custom SVG markers; hover tooltips  

---

### 3.3. Hierarchical Tree Map (`Treemap.html`)
- **Purpose**: Visualize TB treatment availability vs. deaths.  
- **Hierarchy**:
  1. Treatment availability (“Yes”, “No”, “Limited”)  
  2. Year  
  - Rectangle size ∝ number of deaths  
- **Breadcrumb Navigation**: Drill down by treatment or year; breadcrumb trail back to root  
- **Color Coding**:
  - “Yes” = bright green  
  - “No” = bright red  
  - “Limited” = bright blue (lighter shade)  
- **Filters**:
  - Dropdown: select country  
  - Checkboxes: choose treatment types  
  - Year-range slider  
- **D3 Features**:
  - `d3.hierarchy`, `d3.treemap`  
  - Tooltips on hover  

---

### 3.4. Timeline Visualization (`tl.html`)
- **Purpose**: Animate TB case evolution over time.  
- **Core**: Line graph (X = year; Y = metric) for each country  
- **Metrics**: Toggle between “People Affected” and “Deaths”  
- **Animation**:
  - Play/pause or slider to step through years  
- **Tooltip**: Hover to see year, country, metric value  
- **Filters**:
  - Dropdown: select countries  
  - Year-range slider  
- **D3 Features**:
  - `d3.line`, `d3.scaleLinear`, `d3.axis`  
  - Transitions for smooth animations  

---

### 3.5. Sunburst Chart (`sun.html`)
- **Purpose**: Show hierarchical relationships between TB causes and treatment availability.  
- **Hierarchy**:
  1. Root (all TB data)  
  2. TB causes  
  3. Treatment availability (“Yes”, “No”, “Limited”)  
  - Segment size ∝ People Affected  
- **Interactivity**:
  - Zoom/pan to explore levels  
  - Hover for tooltips (cause, treatment, people affected)  
  - Segment highlighting on hover/click  
- **Color Coding**:
  - Root = white  
  - TB causes = distinct colors  
  - Treatment levels = lighter shade of parent color  
- **Filter**: Country dropdown updates chart in real time; global view if none selected  
- **D3 Features**:
  - `d3.hierarchy`, `d3.partition`  
  - `d3.arc` for segments  
  - `d3.zoom`, `d3.select`, `d3.on` for interactivity  

---

## 4. Installation & Usage
```bash
# 1. Clone the repository
git clone https://github.com/yourusername/tb-d3-dashboard.git
cd tb-d3-dashboard

# 2. Serve files locally (D3/Leaflet require a local server)
# Using Python 3:
python -m http.server 8000

# 3. Open a browser and navigate to:
# Force-Directed Graph:
http://localhost:8000/Forced.html
# Geographic Map Chart:
http://localhost:8000/Map.html
# Tree Map:
http://localhost:8000/Treemap.html
# Timeline Visualization:
http://localhost:8000/tl.html
# Sunburst Chart:
http://localhost:8000/sun.html


##5. Project Structure
tb-d3-dashboard/
├── data/
│   └── updated_tb_dataset.csv
├── Forced.html
├── Map.html
├── Treemap.html
├── tl.html
├── sun.html
├── README.md
└── assets/            # (Optional) CSS/JS libraries or images

##6. Dependencies
D3.js (v6+)

Leaflet.js (v1.7+) (only for Map visualization)

A modern web browser (Chrome, Firefox, Edge)

##7. Contributing
# 1. Fork this repository.
# 2. Create a new branch:
git checkout -b feature/your-feature
# 3. Make changes and commit:
git commit -m "Add feature"
# 4. Push to branch:
git push origin feature/your-feature
# 5. Open a Pull Request with your changes.

