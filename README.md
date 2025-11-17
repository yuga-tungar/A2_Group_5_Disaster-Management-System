Project Title & Objective
Intelligent Flood Emergency Response System for India
Objective: Automatically determine appropriate rescue locations, evaluate flood danger levels, and offer safe evacuation assistance using location-based flood data and AI algorithms. The system provides real-time risk assessments, rescue facility recommendations, and safe navigation routes, empowering users with a mobile-centric framework and SOS interface.
It integrates:
K-Means clustering for unsupervised flood-risk zone formation
Logistic Regression for supervised flood-risk prediction
KDTree + A* for safe routing with risk-aware penalties
Rescue Center Optimization using K-Means clustering
SOS Interface (Gradio) for user interaction and live route planning


Dataset Details
Source: floodriskdatasetindia.csv
About Dataset: The “Flood Risk Prediction Dataset in India” is a detailed, multi-dimensional dataset created to support the development and testing of models that predict flood risk across different Indian regions. It brings together extensive meteorological, geographical, hydrological, socio-economic, and past flood records, providing the key variables needed to understand flood-driving factors and build reliable prediction systems.
Features:
Latitude (Latitude)
 	Type: Float
 	Location’s latitude coordinate.
Longitude (Longitude)
 	Type: Float
 	Location’s longitude coordinate.
Rainfall (mm) (Rainfall_mm)
 	Type: Float
 	Rainfall amounts in millimeters.
Temperature (°C) (Temperature_C)
 	Type: Float
 	Recorded temperature in Celsius.
Humidity (%) (Humidity_pct)
 	Type: Float
 	Humidity percentage at the location.
River Discharge (m³/s) (River_Discharge_m3_s)
 	Type: Float
 	Volume of river water flowing per second.
Water Level (m) (Water_Level_m)
 	Type: Float
 	Measured water level height in meters.
Elevation (m) (Elevation_m)
 	Type: Float
	Elevation above sea level in meters.
Land Cover (Land_Cover)
 	Type: Categorical
 	Land cover classification: Urban, Forest, Agricultural, Water Body etc.
Soil Type (Soil_Type)
 Type: Categorical
 Soil classification: Sandy, Clay, Loam, Silt, Peat.
Population Density (Population_Density)
 	Type: Float
 	People per square kilometer.
Infrastructure (Infrastructure)
 	Type: Binary (0/1)
 	Presence of flood-control infrastructure (1 = present, 0 = absent).
Historical Floods (Historical_Floods)
 	Type: Binary (0/1)
 	Whether the location has a past flood record (1 = yes, 0 = no).
Flood Occurred (Flood_Occurred)
 	Type: Binary (0/1)
	Target variable indicating flood occurrence (1 = flood, 0 = no flood)
Features used: Latitude, Longitude, Water Level (m)
Preparation: Removed rows with missing values and applied StandardScaler to ensure feature scaling for fair clustering and classification.
Data enables both spatial risk mapping and machine learning-based flood prediction.​
Algorithms and Models Used
K-Means Clustering (Unsupervised)
K-Means clustering partitions flood data into natural risk zones using features weighted by their importance (water level and river discharge). The result is five distinct flood risk categories—No Risk, Low Risk, Medium Risk, High Risk, and Severe Risk—each data point being assigned a risk label. This clustering informs targeted rescue planning by demarcating emergency zones.
Logistic Regression (Supervised)
Using the K-Means labels as targets, Logistic Regression classifies locations into flood risk zones based on geographic and hydrological inputs. It is chosen for its speed, multi-class handling capability, and interpretability. The trained classifier predicts flood risk levels for new or user-input locations, supporting timely decisions.
KDTree + A* Geospatial Routing
To provide safe evacuation routes, KDTree indexes spatial coordinates for efficient nearest-neighbor queries. The A* pathfinding algorithm calculates routes considering both great-circle Earth distances and risk penalties linked to flood zone severity. This ensures evacuees avoid high-risk areas unless unavoidable.
Strategic Rescue Center Placement
K-Means clustering also optimizes the location of rescue centers ensuring coverage across risk zones. Rescue centers are spaced apart with enforced minimum distance constraints and situated in safer zones, promoting balanced and efficient emergency support.
SOS Interface (Gradio UI)
An interactive interface facilitates SOS requests, allowing users to input start and end locations and receive flood risk predictions, safe routes, and rescue center contacts. The UI is designed for ease of use during emergencies.
Results and Performance
The system effectively clusters flood-prone regions into meaningful risk zones.
Logistic regression achieved an overall accuracy of about 87% and macro F1-score around 0.86.
Routing algorithms generate safe, user-friendly evacuation paths visualized on interactive maps.
Rescue center placement ensures accessible emergency support distributed across all zones.
How to Run the Project
Install dependencies:
pip install pandas numpy scikit-learn joblib scipy geopy matplotlib gradio
Run data preprocessing and clustering:
python 1_clustering.py
Train the logistic regression model:
python 2_train_model.py
Execute safe route and rescue center modules:
python 3_safe_route.py
Launch the Gradio-based SOS application:
python app.py
Files in the Repository
dataset.csv — Raw flood dataset
flood_clustered.csv — Processed dataset with cluster labels
flood_risk_model.pkl — Trained logistic regression model
risk_map.png — Visualization of risk zones
app.py — Main Gradio UI application
routing.py — A* pathfinding logic
clustering.py — K-Means clustering logic
rescue_center.py — Rescue center placement algorithm
Conclusion and Future Scope
This system presents a comprehensive, AI-driven approach for flood risk prediction and emergency response, integrating clustering, classification, and geospatial routing. Future work could incorporate real-time data inputs, advanced deep learning models, and cloud-based dashboards for wider applicability and enhanced accuracy.

PPT link:
https://www.canva.com/design/DAG42bSvD8c/SAfEDiw5VIWK6stf2D5M1A/edit?utm_content=DAG42bSvD8c&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
