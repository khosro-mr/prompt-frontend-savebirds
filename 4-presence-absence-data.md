<h1 align="center">SaveBirds.app Presence-Absence Data Page</h1>

# 1. Overview
Create the Presence-Absence Data page for SaveBirds.app using Vue 3 and Bootstrap 5. This page allows users to select a specific bird species and time range to visualize where that species has been observed across North America.

# 2. Design Requirements

## 2.1. Layout Structure
The Presence-Absence Data page should consist of three main sections:
- **Explanation Section**: Title and descriptive text explaining the feature
- **Form and Results Section**: User input controls and resulting map display
- **Bird Image Recovery Panel**: Dynamic bird image search results

## 2.2. Visual Reference
![Presence-Absence Data Page Design](images/3-Presence-Absence-Data.png)

# 3. Component Specifications

## 3.1. Explanation Section
- **Title**:
  - Text: "Presence-Absence Data"
  - Font: Large, bold, prominent (display-5 class)
  - Position: Top of the content area, left-aligned

- **Descriptive Text**:
  - Content: Explanation of the Presence-Absence Data feature
  - Format: Justified text with an ordered list explaining the output:
    1. A map of routes where the selected bird species has been seen in the selected year interval
    2. An Excel file with presence-absence data for the species in the year interval
  - Font: Clean, readable font consistent with the rest of the site
  - Position: Below the title

## 3.2. Form Inputs and Results Section
- **Layout**:
  - Two-column layout on large screens (col-lg-6)
  - Form on the left, results/map on the right
  - Full width on smaller screens (stacked)

- **Form Controls**:
  - **Start Year Dropdown**:
    - Label: "Start year:"
    - Options: Range from 1966 to the current year
    - Default: 1966
    - Note: Include special handling for 2020 (COVID-19 — No data)
    - Styling: Bootstrap form-select with custom padding
  
  - **End Year Dropdown**:
    - Label: "End year:"
    - Options: Synchronized with Start year (equal to or greater than selected start year)
    - Default: Current year
    - Note: Same special handling for 2020
    - Styling: Bootstrap form-select with custom padding
  
  - **Species Name Dropdown**:
    - Label: "Species name:"
    - Component: Use v-select component for searchable dropdown
    - Options: Comprehensive list of North American bird species
    - Default: None (requires user selection)
  
  - **AOU Display**:
    - Label: "AOU:"
    - Content: Automatically display the AOU code corresponding to the selected species
    - Visibility: Only shown when a species is selected
    - Styling: Bold label with indented value
  
  - **Submit Button**:
    - Text: "Click"
    - Icon: Bookmark check icon (Bootstrap Icons)
    - Color: Bootstrap primary (btn-primary)
    - Position: Below the form controls
    - Action: Trigger form submission and data retrieval

- **Results Display**:
  - **Status Indicators**:
    - Error State (status === 0): Red alert with error message
    - Processing State (status === 2): Blue info alert with "please wait" message
    - Success State (status === 1): Display map image and download button
  
  - **Map Display**:
    - Content: Map showing routes where the selected species has been observed
    - Source: Dynamic based on API response
    - Style: Responsive (max-width: 100%) with margin below
    - Custom class: "custom-image-result-styles"
  
  - **Download Button**:
    - Text: "Download results"
    - Color: Green (btn-success)
    - Action: Link to download ZIP file containing map and Excel data
    - Only visible when results are available

## 3.3. Bird Image Recovery Panel
- **Implementation**:
  - Use an iframe embedding Bing image search results
  - Search query: Dynamically set to the selected bird species name
  - Size: Full width of container, 700px height
  - Border: Simple border class
  - Position: Right column on large screens, below form on smaller screens

## 3.4. Specific Implementation Code for Bird Image Recovery Panel
```vue
<div class="col-lg-6">
  <iframe
    :src="'https://www.bing.com/images/search?q='+name"
    style="width: 100%; height: 700px"
    class="border">
  </iframe>
</div>
```

# 4. Data Requirements

## 4.1. Species List for Dropdown
- Comprehensive list of North American bird species
- Each entry should include:
  - Species common name (e.g., "Bald Eagle")
  - Corresponding AOU code (e.g., 3520)
- Implement as a searchable dropdown using v-select component
- Data structure:
  - options: Array of species names
  - aou: Object mapping species names to AOU codes

## 4.2. Form Data Handling
- Implement v-model bindings for all form inputs:
  - startYear: Selected start year
  - endYear: Selected end year
  - name: Selected species name
- Derive AOU code from the selected species name
- Handle form submission with @submit.prevent directive
- Implement appropriate validation before submission

# 5. Responsive Behavior
- **Desktop View**:
  - Two-column layout with form on left, image search on right
  - Balanced spacing between elements
  - Full-width map result below form inputs

- **Mobile View**:
  - Single-column layout with sections stacked vertically
  - Form inputs should be properly sized for mobile viewing
  - Bird image search panel should appear below form
  - All interactive elements sized appropriately for touch input

# 6. Implementation Notes
- Create as a Vue component in `views/PresenceAbsenceView.vue`
- Use Bootstrap 5 grid system for responsive layout
- Implement form controls using Vue's v-model for data binding
- Use v-select component for the searchable species dropdown
- Handle the three possible states of the form:
  - Initial/Error (status === 0)
  - Success with results (status === 1)
  - Processing (status === 2)
- Since this is a frontend-only implementation, mock the API responses with static examples
- Implement proper error handling for form submission

# 7. Component Data Structure
```javascript
data() {
  return {
    fixStartYear: 1966,
    rangeFixed: 55, // Adjust based on current year
    range: 55,      // Dynamically calculated based on startYear
    helper: 0,      // Used for end year calculation
    startYear: 1966,
    endYear: 2022,  // Update to current year
    name: "",       // Selected species name
    options: [],    // Will be populated with species list
    aou: {},        // Will be populated with species:AOU mapping
    status: 0,      // 0: initial/error, 1: success, 2: processing
    failed: "Please select a species name.",
    wait: "Processing your request, please wait...",
    is_default: false,
    png: "",
    zip: "",
    baseURL: "" // Base URL for API calls
  }
}
```

# 8. Code Structure
- Use semantic HTML5 elements (`<section>`, `<form>`, etc.)
- Implement as a single-file component with template, script, and style sections
- Style using Bootstrap classes with minimal custom CSS
- For any custom styles, use scoped CSS to avoid conflicts
- Include appropriate error handling and loading states
