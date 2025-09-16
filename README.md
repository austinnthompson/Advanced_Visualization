# Advanced Visualization Notebook

## Executive Summary

This Jupyter Notebook showcases data exploration and visualization capabilities using Python packages to analyze the ACLED (Armed Conflict Location & Event Data Project) dataset augmented with U.S. Combatant Command (COCOM) information. The dataset, spanning December 18, 2019, to February 15, 2020, includes conflict events with details like event types, locations, dates, and fatalities. The notebook leverages key Python packages (`pandas`, `matplotlib`, `folium`) to perform data manipulation, temporal analysis, and geospatial visualization.

### Python Packages and Capabilities

#### 1. **Pandas** (`pandas`)
   - **Purpose**: Data manipulation and exploration.
   - **Capabilities Demonstrated**:
     - **Data Loading**: Reads the dataset from `data/ACLED_event_data_with_COCOM.csv` into a DataFrame using `pd.read_csv()`.
     - **Data Inspection**: Displays the first five rows (`df_event.head()`) and provides a summary of data types and non-null counts (`df_event.info()`).
     - **Data Transformation**: Converts the `event_date` column to datetime format using `pd.to_datetime()` for temporal analysis.
     - **Data Sorting and Filtering**: Sorts the DataFrame by `event_date` (`sort_values()`) and filters for USCENTCOM events on specific dates (January 7-8, 2020) using boolean masks.
     - **Aggregation**: Computes the mean of latitude and longitude for map centering (`df_event['latitude'].mean()`, `df_event['longitude'].mean()`).

#### 2. **Matplotlib** (`matplotlib`)
   - **Purpose**: Visualization of temporal patterns.
   - **Capabilities Demonstrated**:
     - **Plotting**: Generates a plot (likely a line or bar chart) to analyze temporal trends in the dataset, as indicated by the example section "Analyze Temporal Patterns."
     - **Customization**: Includes a legend (`matplotlib.legend.Legend`) for enhanced plot readability, suggesting visualization of event counts or fatalities over time.

#### 3. **Folium** (`folium`)
   - **Purpose**: Interactive geospatial visualization.
   - **Capabilities Demonstrated**:
     - **Map Creation**: Initializes an interactive map centered on the mean coordinates of filtered events using `folium.Map(location=..., zoom_start=5, tiles='CartoDB positron')`.
     - **Marker Clustering**: Uses `folium.plugins.MarkerCluster` to group closely located events, improving map performance and readability for large datasets.
     - **Custom Markers**: Adds markers for each USCENTCOM event with `folium.Marker`, including:
       - **Popups**: Detailed HTML popups (`folium.Popup`) displaying event details (date, event type, sub-event type, country, location, coordinates, fatalities).
       - **Tooltips**: Hover text showing the event type (`tooltip=row['event_type']`).
       - **Icons**: Red markers with a white info-sign icon (`folium.Icon(color='red', icon='info-sign')`).
     - **Minimap Plugin**: Incorporates `folium.plugins.MiniMap` for navigation context, with customizable settings (e.g., `toggle_display=True`, `zoomLevelOffset=-5`).
     - **Map Rendering**: Displays the map inline in the notebook, with an option to save as HTML (`m.save('centcom_events_jan7_8.html')`).
