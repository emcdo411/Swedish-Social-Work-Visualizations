### README for GitHub

Create a file named `README.md` in your repository with this content:

```markdown
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
  ```

## How to Run
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/Swedish-Social-Work-Visualizations.git
   ```
2. Open `social_work_visualizations.R` in RStudio.
3. Run the script to generate all visualizations.
4. Outputs will appear in RStudio (Viewer and Plots panes) and save to your working directory.

## Files
- `social_work_visualizations.R`: Main R script
- `social_work_bubble_anim.gif`: Animated output
- `social_work_3d_surface.html`: Interactive 3D plot
- `social_work_correlation_matrix.png`: Correlation matrix

## Future Enhancements
- Integrate real data from Swedish social work reports.
- Add statistical models to quantify policy impacts.
- Expand visualizations with heatmaps or network graphs.

## Acknowledgments
Thanks to my girlfriend for her insights into Swedish social work, and to the R community for powerful visualization tools.
```

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
     git push -u origin main
     ```
   - Replace `yourusername` with your GitHub username.
4. **Verify**: Check your GitHub repo online to ensure all files (script, README, outputs) are uploaded.

This gives you a polished, professional repo to share! Let me know if you need help with Git or want to refine anything further.<img width="959" alt="Screenshot 2025-03-20 182050" src="https://github.com/user-attachments/assets/6d611cc9-af3f-42a1-a263-a9f8b6073ad3" />

### Clean Script for All Advanced Graphs

This script includes all necessary steps, assumes packages are installed, and avoids the pitfalls we encountered (e.g., typos, missing renderers).

```R
# Load required libraries
library(dplyr)      # For data manipulation
library(tidyr)      # For pivot_longer
library(ggplot2)    # For plotting
library(gganimate)  # For animated bubble chart (p3)
library(gifski)     # For GIF rendering
library(plotly)     # For 3D surface plot (p4)
library(GGally)     # For correlation matrix (p5)

# Simulated data for Swedish nationals
nationals_data <- data.frame(
  Year = 2020:2025,
  Trust_Level = c(75, 70, 65, 62, 60, 63),
  Satisfaction_Score = c(7.8, 7.5, 7.2, 7.0, 6.8, 7.0),
  Accessibility_Rating = c(7.0, 6.8, 6.5, 6.3, 6.2, 6.5),
  Workload_Score = c(8.0, 8.2, 8.5, 8.3, 8.1, 7.8),
  Intervention_Success = c(70, 68, 65, 64, 63, 68),
  Disinformation_Impact = c(2.0, 4.5, 5.0, 4.8, 4.0, 3.5)
)

# Simulated data for immigrants
immigrants_data <- data.frame(
  Year = 2020:2025,
  Trust_Level = c(60, 58, 55, 52, 50, 53),
  Satisfaction_Score = c(6.5, 6.3, 6.0, 5.8, 5.7, 5.9),
  Accessibility_Rating = c(5.5, 5.3, 5.0, 4.8, 4.7, 5.0),
  Workload_Score = c(8.5, 8.7, 8.8, 8.6, 8.4, 8.0),
  Intervention_Success = c(60, 58, 55, 54, 53, 58),
  Disinformation_Impact = c(3.0, 5.5, 6.0, 5.8, 5.0, 4.0)
)

# Combine data and add a group identifier
combined_data <- bind_rows(
  nationals_data %>% mutate(Group = "Swedish Nationals"),
  immigrants_data %>% mutate(Group = "Immigrants")
)

# Convert to long format (optional for some plots)
data_long <- combined_data %>%
  pivot_longer(cols = c(Trust_Level, Satisfaction_Score, Accessibility_Rating, 
                        Workload_Score, Intervention_Success, Disinformation_Impact),
               names_to = "Metric", values_to = "Value")

# Graph 1: Animated Bubble Chart (p3)
p3 <- ggplot(combined_data, aes(x = Year, y = Trust_Level, size = Satisfaction_Score, color = Group)) +
  geom_point(alpha = 0.7) +
  scale_size(range = c(3, 15)) +
  scale_color_manual(values = c("Swedish Nationals" = "blue", "Immigrants" = "red")) +
  labs(title = "Trust Level vs. Satisfaction (2020-2025)",
       subtitle = "Bubble size = Satisfaction Score",
       x = "Year", y = "Trust Level (%)", size = "Satisfaction Score", color = "Group") +
  theme_minimal() +
  transition_time(Year) +
  shadow_wake(wake_length = 0.1)

anim <- animate(p3, nframes = 100, fps = 10, width = 800, height = 600, renderer = gifski_renderer())
print(anim)  # Display in Viewer pane
anim_save("social_work_bubble_anim.gif", anim)
cat("Bubble chart GIF saved to:", getwd(), "/social_work_bubble_anim.gif\n")

# Graph 2: 3D Surface Plot (p4)
surface_data <- combined_data %>%
  select(Year, Group, Trust_Level) %>%
  pivot_wider(names_from = Group, values_from = Trust_Level) %>%
  as.matrix()

p4 <- plot_ly(z = surface_data[, -1], x = 2020:2025, y = c("Swedish Nationals", "Immigrants"), 
              type = "surface") %>%
  layout(title = "Trust Level Surface Plot (2020-2025)",
         scene = list(xaxis = list(title = "Year"),
                      yaxis = list(title = "Group"),
                      zaxis = list(title = "Trust Level (%)")))

print(p4)  # Display in Viewer pane or browser
htmlwidgets::saveWidget(p4, "social_work_3d_surface.html")
cat("3D surface plot saved to:", getwd(), "/social_work_3d_surface.html\n")

# Graph 3: Paired Correlation Matrix (p5)
p5 <- ggpairs(combined_data, columns = 2:7,  # Trust_Level to Disinformation_Impact
              aes(color = Group, alpha = 0.5),
              upper = list(continuous = "cor"),
              lower = list(continuous = "points"),
              diag = list(continuous = "densityDiag")) +
  labs(title = "Correlation Matrix of Social Work Metrics") +
  theme_minimal()

print(p5)  # Display in Plots pane
ggsave("social_work_correlation_matrix.png", p5, width = 12, height = 12, dpi = 300)
cat("Correlation matrix saved to:", getwd(), "/social_work_correlation_matrix.png\n")
```

### Prerequisites
Before running, ensure these packages are installed:
```R
install.packages(c("dplyr", "tidyr", "ggplot2", "gganimate", "gifski", "plotly", "GGally", "htmlwidgets"))
```
Run this once in RStudio, then you can skip it in future runs.

### Running Instructions
1. **Save as Script**: Save this as `social_work_visualizations.R` in your project folder.
2. **Open in RStudio**: Open the file and run all lines (Ctrl+A, Ctrl+Enter).
3. **Outputs**:
   - `social_work_bubble_anim.gif`: Animated GIF (Viewer pane and file).
   - `social_work_3d_surface.html`: Interactive 3D plot (Viewer pane or browser and file).
   - `social_work_correlation_matrix.png`: Static matrix (Plots pane and file).

---

### Suggested Repository Name
**`Swedish-Social-Work-Visualizations`**  
- Reflects the focus on visualizing Swedish social work data, concise and descriptive.

---
<img width="953" alt="Screenshot 2025-03-20 185247" src="https://github.com/user-attachments/assets/844f7b19-1d2f-4fde-b5a6-8030a93704c4" />
<img width="959" alt="Screenshot 2025-03-20 184235" src="https://github.com/user-attachments/assets/9af57e65-c7cf-40ba-929f-f81caa7fd5d8" />
<img width="959" alt="Screenshot 2025-03-20 183958" src="https://github.com/user-attachments/assets/eb25931b-a144-4e15-b0be-46b4939c71c1" />
<img width="949" alt="Screenshot 2025-03-20 183651" src="https://github.com/user-attachments/assets/9ca6aabf-9642-4990-87af-0b28f60a1110" />






  
