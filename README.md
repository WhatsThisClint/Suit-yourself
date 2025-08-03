# **Site Suitability Analyzer**

A web-based GIS tool designed for non-experts to easily upload, visualize, analyze, and classify location-based data without requiring specialized software. This tool streamlines the site suitability assessment process by providing an interactive map interface, powerful analysis tools, and simple data I/O, all within a single web page.

## **Table of Contents**

* [Core Features](https://www.google.com/search?q=%23core-features)  
* [How It Works: The Workflow](https://www.google.com/search?q=%23how-it-works-the-workflow)  
* [Data Requirements](https://www.google.com/search?q=%23data-requirements)  
  * [Input File Format](https://www.google.com/search?q=%23input-file-format)  
  * [Special Columns](https://www.google.com/search?q=%23special-columns)  
* [Getting Started](https://www.google.com/search?q=%23getting-started)  
* [Using the Tool: A Detailed Guide](https://www.google.com/search?q=%23using-the-tool-a-detailed-guide)  
  * [1\. Uploading Location Data](https://www.google.com/search?q=%231-uploading-location-data)  
  * [2\. Configuring Fields & Plotting](https://www.google.com/search?q=%232-configuring-fields--plotting)  
  * [3\. The Interactive Map](https://www.google.com/search?q=%233-the-interactive-map)  
  * [4\. Classifying Sites (The Details Panel)](https://www.google.com/search?q=%234-classifying-sites-the-details-panel)  
  * [5\. Filtering and Navigation](https://www.google.com/search?q=%235-filtering-and-navigation)  
  * [6\. Adding Context with Vector Layers](https://www.google.com/search?q=%236-adding-context-with-vector-layers)  
  * [7\. Analysis Tools](https://www.google.com/search?q=%237-analysis-tools)  
  * [8\. Exporting Your Work](https://www.google.com/search?q=%238-exporting-your-work)  
* [Technologies Used](https://www.google.com/search?q=%23technologies-used)  
* [Contributing](https://www.google.com/search?q=%23contributing)  
* [License](https://www.google.com/search?q=%23license)

## **Core Features**

* **Easy Data Import:** Upload site data directly from .xlsx or .csv files.  
* **Interactive Mapping:** Plots all locations on a dynamic Leaflet map with street, satellite, and topographic base layers.  
* **RAG Status Classification:** Manually classify each site as **Green** (Good), **Amber** (Moderate), or **Red** (Bad) to track suitability.  
* **Dynamic Details Panel:** Click any point on the map to view its full data, add justification comments, and update its status.  
* **Custom Field Configuration:** Choose which data columns from your input file are displayed in the details panel.  
* **Efficient Navigation:**  
  * Filter points on the map by their classification status.  
  * Quickly jump between points of a specific category (e.g., "Next Amber").  
  * Use the "Go to Next Unchecked" button to systematically work through unvalidated sites.  
* **External Layer Support:** Overlay your own .geojson files (e.g., rivers, administrative boundaries, infrastructure) for spatial context.  
* **Spatial Analysis:**  
  * **Distance Calculation:** Automatically calculate the distance from each of your points to the nearest feature in an overlayed GeoJSON layer (e.g., distance to nearest stream).  
  * **Automated Validation:** Use the calculated distances to automatically classify sites based on user-defined thresholds.  
* **AI-Powered Analysis:** (Advanced) Capture the current map view and send it to a multimodal AI for a descriptive analysis of the geography and topography.  
* **Data Export:** Export the fully analyzed data, including new status and comments, back to a .csv file for reporting or re-use.  
* **No Installation Required:** Runs entirely in your web browser.

## **How It Works: The Workflow**

The tool is designed to guide a resource person through a logical and efficient site assessment workflow.

1. **Start with Your Data:** You begin with an Excel or CSV file containing a list of potential sites. The only mandatory columns are for latitude and longitude. You can have any number of other columns with relevant site information.  
2. **Upload and Configure:** The user uploads this file into the application. The tool immediately prompts them to configure which data fields they want to see in the details panel. This keeps the interface clean and focused on relevant information.  
3. **Visualize:** The sites are plotted as points on the interactive map. Unclassified points are blue by default.  
4. **Add Context (Optional):** The user can overlay additional map layers from GeoJSON files. For instance, they could add a layer of rivers to see how close each site is to a water source.  
5. **Analyze and Classify:** The user clicks on a point to open the details panel. Here they can:  
   * Review all the data associated with that site.  
   * Use the **Green**, **Amber**, and **Red** buttons to assign a suitability status. The point's color on the map changes instantly.  
   * Write a justification for their decision in a comment field.  
6. **Automate (Optional):** If a context layer (like rivers) has been added, the user can run the **Distance Calculation** tool. This adds a new data column to every site, showing its distance to the nearest river. The tool can then use these distances to automatically classify sites (e.g., sites \<100m are Green, 100-500m are Amber, \>500m are Red).  
7. **Systematic Review:** The user can filter the map to show only "Amber" sites, for example. They can then use the navigation buttons to jump from one amber site to the next, reviewing each one systematically.  
8. **Export for Delivery:** Once the analysis is complete, the user exports the results as a new CSV file. This file contains all the original data plus the new validation\_status and User\_Comment columns.  
9. **Collaboration:** This exported file can be sent to a client or colleague. They can load it back into the same tool to see the final classifications, read the justifications, and navigate through the assessed sites.

## **Data Requirements**

### **Input File Format**

* Your location data must be in a Microsoft Excel (.xlsx) or Comma-Separated Values (.csv) file.  
* The file must contain columns for latitude and longitude. The tool is smart enough to find them if they are named any of the following (case-insensitive):  
  * **Latitude:** latitude, lat, y, ycenter  
  * **Longitude:** longitude, long, lon, lng, x, xcenter

### **Special Columns**

The tool automatically recognizes and uses these columns if they exist in your input file. If they don't exist, they will be created for you during analysis.

* validation\_status: This column stores the RAG status. On import, the tool will read existing statuses. Valid values are Green, Amber, Red, Unvalidated, Not Required. Any other value will default to Unvalidated.  
* User\_Comment: This column is for storing text justifications. It is created as an editable field in the details panel.  
* distance\_to\_stream\_m: This column is added automatically when you run the Distance Calculation tool.

## **Getting Started**

No installation is needed\!

1. Download the Stable.html file.  
2. Open the file in any modern web browser (like Chrome, Firefox, or Edge).  
3. You're ready to go\!

## **Using the Tool: A Detailed Guide**

### **1\. Uploading Location Data**

* Click the **"Select Location File"** box on the left-hand panel.  
* Choose your .xlsx or .csv file.  
* The tool will read the file and prepare the data.

### **2\. Configuring Fields & Plotting**

* After a successful upload, a dialog will ask if you want to configure the display fields.  
* **Yes, Configure:** A modal will appear showing all columns from your file. You can check/uncheck boxes to control which fields appear in the details panel and which of those are editable.  
* **No, Plot Now:** The tool will plot the points immediately using the default configuration.  
* You can also re-configure fields at any time using the **"Fields"** button (\<i data-lucide="settings-2"\>\</i\>) in the "Analysis Tools" section.

### **3\. The Interactive Map**

* **Pan and Zoom:** Use your mouse to drag and scroll to navigate the map.  
* **Base Layers:** Switch between Street, Satellite, and Topographic views using the layer control in the top-right corner.  
* **Markers:** Each point from your file is a marker. The color represents its status. A number badge appears on markers that represent multiple data records at the exact same coordinate.

### **4\. Classifying Sites (The Details Panel)**

* **Open:** Click any marker on the map to open its details panel on the right.  
* **Review Data:** Scroll through the panel to see all the configured data for that point.  
* **Change Status:** Use the **Green**, **Amber**, **Red**, or **Not Required** buttons at the bottom of the panel to set the site's status. The marker color on the map will update instantly.  
* **Add Justification:** Type your notes into any field marked as editable (like User\_Comment). The data is saved as you type.

### **5\. Filtering and Navigation**

* **Stats Panel (Left):** The summary panel on the left shows a count for each status category. Click on any category (e.g., "Green") to filter the map and show only those points. Click "Total Points" to see all points again.  
* **Navigate by Category (Right):** When you are filtering by a category (e.g., viewing only "Red" sites), Previous and Next arrow buttons will appear in the details panel, allowing you to cycle through all sites in that category.  
* **Navigate Unchecked (Right):** The **"Go to Next Unchecked"** button is your primary tool for a systematic first-pass review. Clicking it will automatically find the next Unvalidated point and zoom to it.

### **6\. Adding Context with Vector Layers**

* Click the **"Add GeoJSON Layer(s)"** button.  
* Select one or more .geojson files.  
* The layers will be added to the map and will appear in the layer control (top-right).  
* **Style Layers:** Click the paint palette icon (\<i data-lucide="palette"\>\</i\>) next to a layer's name in the control to change its color and opacity.

### **7\. Analysis Tools**

* **Distance Calculation:**  
  1. First, ensure you have both your sites plotted and a GeoJSON layer loaded.  
  2. Click the **"Distance"** button (\<i data-lucide="ruler"\>\</i\>). If you have multiple GeoJSON layers, it will ask you to select one.  
  3. The tool will calculate the distance from each site to the nearest feature in the selected layer and add it to the data.  
  4. A dialog will then ask if you want to automatically set the RAG status based on these distances. If you agree, you can set the distance thresholds for Green and Amber.  
* **AI Analyze:**  
  * Click the **"AI Analyze"** button (\<i data-lucide="brain-circuit"\>\</i\>).  
  * This captures an image of the current map view and sends it to an AI for a high-level textual analysis of the geography. Useful for generating descriptive reports.  
* **Dashboard:**  
  * Click the **"Dashboard"** button (\<i data-lucide="pie-chart"\>\</i\>) to open a full-screen analytics view.  
  * Here you can generate charts (Bar, Pie, Doughnut) to explore your data, grouping by different columns to find insights.

### **8\. Exporting Your Work**

* When you are finished with your analysis, click the **"Export to CSV"** button (\<i data-lucide="download"\>\</i\>).  
* A .csv file named site\_suitability\_report.csv will be downloaded. This file includes all original data plus the final validation\_status and any User\_Comment you added.

## **Technologies Used**

* **HTML5**  
* **Tailwind CSS:** For modern, utility-first styling.  
* **JavaScript (ES6+):** For all application logic.  
* **Leaflet.js:** For the interactive map.  
* **Turf.js:** For geospatial analysis (distance calculations).  
* **PapaParse:** For robust CSV file parsing.  
* **SheetJS (xlsx):** For reading Excel files.  
* **Lucide Icons:** For a clean and consistent icon set.  
* **Chart.js:** For the analytics dashboard.

## **Contributing**

Contributions are welcome\! If you have suggestions for improvements or find a bug, please open an issue or submit a pull request.

## **License**

This project is licensed under the MIT License. See the LICENSE file for details.
