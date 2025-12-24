# Boston-Housing-Quality-Violation-Analytics-PCA-Based-Interactive-Visualization

# CS424 Project

## Group name
### Brick By Brick

## Team Members
Omar Khan - okhan39@uic.edu \
Manan Patel - mpate360@uic.edu \
Andrea Piras - apiras2@uic.edu 

## Data Description:
For our project we picked two datasets from the City of Boston’s open data portal: RentSmart and the Boston Building Inventory. The RentSmart dataset compiles property violation and complaint data from BOS:311 and the City of Boston’s Inspectional Services Division, covering 2016 to the present. It contains about 366,000 rows and 13 attributes. The attributes include date and type of violation, detailed descriptions of complaints, property information such as address, neighborhood, parcel ID, property type, year built, and geographic coordinates for mapping. The Boston Building Inventory dataset was put together by the city to keep track of its buildings, and it lists close to 99,000 properties with 107 attributes. Some of these attributes are year built, number of floors, square footage, property type, and different structural or energy features. There is also info about past renovations. We picked these two datasets because they go hand in hand. RentSmart shows complaints and issues that people are reporting while the Boston Building Inventory describes the physical characteristics of the buildings. City officials and researchers might use this data to study questions about housing quality, whether rent is affordable, and how different neighborhoods develop over time. For our project, combining the two lets us explore whether building characteristics like age or size are linked to more complaints and how building features connect to rental conditions across Boston.

## Questions

1) How do violation counts evolve over time, and which neighborhoods show the highest or changing concentrations?
 
2) Building Inventory: How is building size and height distributed across the city, and how has that distribution shifted by construction era (i.e., are newer buildings taller/bigger)?
   
3) How do building properties relate to violations?

4) How do building location, age, and year remodeled relate to intensity of retrofit recommendations?
   
5) Question: How does the demographic composition vary across the city and over time?

## Overview

This project creates an interactive web-based system for exploring building and violation patterns in Boston through a 2D embedding. We combined the RentSmart complaint data with the Boston Building Inventory and built a feature set that includes building attributes, neighborhood context, time information, and text from complaint descriptions. After constructing these features, we used PCA to project everything into two dimensions so that similarities between buildings and complaints are easier to see. The interface is built around a brushable PCA scatterplot, which is tied to a bar chart, a time-based view, and a neighborhood map of Boston. Selecting points in the embedding automatically updates the other views, letting users follow how a group behaves across different parts of the data. With this setup, patterns start to stand out. Certain neighborhoods cluster together, some violation types show clear trends over time, and specific building traits become easier to interpret in the context of complaints.

# Live Demo: 
https://andreapiras00.github.io/andreapiras00.github.io-cs424/

## Task 1: Creating embeddings and projections 

# Files generated and saved:

embeddings.csv – full high-dimensional feature vectors (one row per record)
embeddings_2d.csv – full PCA projection
embeddings_2d_sampled.csv – 5,000-point sample used in the web interface (for performance)

# Task 1.2 – Project embeddings to 2D

Method chosen: PCA
Parameters:n_neighbors=15, min_dist=0.1, n_components=2, metric='euclidean'
Rationale: PCA preserves both local structure (similar violations stay close) and global structure (major categories separate). We also tried using UMAP, which however produced worse clusters compared to the PCA embedding.
embeddings_2d.csv:
<img width="1147" height="392" alt="image" src="https://github.com/user-attachments/assets/50349cda-b2cb-4088-8337-287c44770c3f" />

## Task 2: Building the standalone embedding-focused HTML page

# The standalone page index.html contains coordinated views:

1) Main Embedding Scatterplot (top-left) – PCA 2D projection, brushable & lasso selection, colored by violation_type.
2) Violation Type Bar Chart (bottom) – Distribution of selected points by type.
3) Temporal Multi-Line Chart (top-right) – Time series trends (e.g., by month/year) for selected vs. all violations.
4) Spatial Map View (bottom-right) – Point map of Boston neighborhoods (using GeoJSON), showing violation density and highlighting selections.
5) Attribute Detail Panel – Table or charts showing key numerics (e.g., year_built distribution) for selected points.

All views are fully linked bidirectionally:

1) Brushing/lasso in embedding updates other views (e.g., filters map to selected clusters).
2) elections in bar chart, timeline, or map highlight/filter points in the embedding scatterplot.

Reused from previous assignments: temporal line chart and point map (multi-view) and barchart (single-view), adapted for linkage.

## Task 3: Using previous visualizations (reuse & linking)

# Definition: 
Dense vectors capturing similarity of Boston buildings via structural, temporal, energy, and demographic traits.

# Goal: 
2D embedding of Boston buildings based on age, size, and structural attributes. Similar buildings cluster together, revealing neighborhood-level patterns.

# Embadding Interface
![newlinked (1)](https://github.com/user-attachments/assets/7e9a4373-5c19-4965-82ef-42581bb94884)


In the above figure, 
Linked View 1 is Violation Timeline for the selected embedding cluster with the Point Map of violations.
Linked View 2 is the Bar Chart showing the number of violations per neighborhood, filtered by the selected embedding cluster.

# Insights and Findings:
Finding 1) High-violation clusters in Dorchester, East Boston, and Roxbury, indicating strong concentration of housing issues.

Finding 2) Seasonal patterns are clear: buildings in these clusters experience sharp spikes in housing violations.

Finding 3) Newer and larger buildings form separate clusters with much lower violation frequency.


## Task 4: Web deployment
**Hosting steps performed:**
1) Repository name set to `[andreapiras00.github.io-cs424](https://github.com/andreapiras00/andreapiras00.github.io-cs424)`
2) All files are pushed in main branch in the root folder.

**Public URL (tested and working on multiple devices):**
https://andreapiras00.github.io/andreapiras00.github.io-cs424/
