# Swedish-Social-Work-Visualizations

This repository contains advanced visualizations of simulated data exploring changes in Swedish social work practices, inspired by the 2025 Social Services Act. The project uses R to create three sophisticated graphs: an animated bubble chart, a 3D surface plot, and a paired correlation matrix, analyzing metrics like trust, satisfaction, and workload across Swedish nationals and immigrants from 2020 to 2025.

## Motivation
I developed these visualizations to support my girlfriend, a social worker in Sweden, by illustrating trends and impacts of the new Social Services Act based on her insights from agency meetings. The goal is to provide an engaging, data-driven perspective for social workers, policymakers, and researchers.

## Visualizations

### 1. Animated Bubble Chart
- **File**: `social_work_bubble_anim.gif`
- **Description**: Shows Trust Level (y-axis) over years (x-axis), with bubble size representing Satisfaction Score, animated from 2020 to 2025. Colors distinguish Swedish Nationals (blue) and Immigrants (red).
- **Tools**: `ggplot2`, `gganimate`, `gifski`

### 2. 3D Surface Plot
- **File**: `social_work_3d_surface.html`
- **Description**: An interactive 3D surface of Trust Level across years and groups (Swedish Nationals and Immigrants). Rotate and zoom to explore trends.
- **Tools**: `plotly`

### 3. Paired Correlation Matrix
- **File**: `social_work_correlation_matrix.png`
- **Description**: Displays pairwise relationships between six metrics (Trust Level, Satisfaction Score, Accessibility Rating, Workload Score, Intervention Success, Disinformation Impact), with scatter plots, density plots, and correlations, colored by group.
- **Tools**: `GGally`

## Data
The data is simulated based on trends from the 2025 Social Services Act and related challenges (e.g., disinformation since 2021, workload pressures). Columns include:
- **Year**: 2020–2025
- **Trust_Level**: Percentage (0–100%)
- **Satisfaction_Score**: Score (0–10)
- **Accessibility_Rating**: Score (0–10)
- **Workload_Score**: Score (0–10)
- **Intervention_Success**: Percentage (0–100%)
- **Disinformation_Impact**: Score (0–10)
- **Group**: Swedish Nationals or Immigrants

## Requirements
- **R**: Version 4.3.x or later recommended
- **Packages**: `dplyr`, `tidyr`, `ggplot2`, `gganimate`, `gifski`, `plotly`, `GGally`, `htmlwidgets`
- Install with: 
  ```R
  install.packages(c("dplyr", "tidyr", "ggplot2", "gganimate", "gifski", "plotly", "GGally", "htmlwidgets"))

 How to Run
Clone this repository:
bash

Collapse

Wrap

Copy
git clone https://github.com/yourusername/Swedish-Social-Work-Visualizations.git
Open social_work_visualizations.R in RStudio.
Run the script to generate all visualizations.
Outputs will appear in RStudio (Viewer and Plots panes) and save to your working directory.

Files
social_work_visualizations.R: Main R script
social_work_bubble_anim.gif: Animated output
social_work_3d_surface.html: Interactive 3D plot
social_work_correlation_matrix.png: Correlation matrix
Future Enhancements
Integrate real data from Swedish social work reports.
Add statistical models to quantify policy impacts.
Expand visualizations with heatmaps or network graphs.


---

### Steps to Share on GitHub
1. **Create Repository**:
   - Go to GitHub, click "New Repository," name it `Swedish-Social-Work-Visualizations`, and initialize with a README (you’ll overwrite it).
2. **Add Files Locally**:
   - Save the R script as `social_work_visualizations.R`.
   - Save the README text as `README.md`.
   - Run the script to generate the output files (`social_work_bubble_anim.gif`, `social_work_3d_surface.html`, `social_work_correlation_matrix.png`).
3. **Push to GitHub**:
   - Open a terminal in your project folder and run:
     ```bash
     git init
     git add .
     git commit -m "Initial commit with R script and visualizations"
     git remote add origin https://github.com/yourusername/Swedish-Social-Work-Visualizations.git
     git push -u origin main<img width="959" alt="Screenshot 2025-03-20 182050" src="https://github.com/user-attachments/assets/cadbbd70-183f-4fcb-9218-3a00b08dcd6e" />
<img width="949" alt="Screenshot 2025-03-20 183651" src="https://github.com/user-attachments/assets/dbd4793a-a665-4490-88c2-f5272b797109" />
<img width="959" alt="Screenshot 2025-03-20 183958" src="https://github.com/user-attachments/assets/197b25a5-9a3d-41aa-a1f7-ec362ac02689" />
<img width="959" alt="Screenshot 2025-03-20 184235" src="https://github.com/user-attachments/assets/21dbe4bf-e9c9-43ad-adbf-475c2c23df6e" />
<img width="953" alt="Screenshot 2025-03-20 185247" src="https://github.com/user-attachments/assets/22a08300-6639-427c-9ac5-58830865e4c7" />


  
