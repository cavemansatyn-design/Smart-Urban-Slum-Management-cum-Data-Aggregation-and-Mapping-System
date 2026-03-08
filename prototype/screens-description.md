# NIVAAS Prototype Screen Descriptions

## Slum Dweller Interface

### Screen 1: Home
- **Purpose**: Entry point for slum dwellers
- **Elements**: Large icon buttons for Survey, Welfare, Emergency
- **Navigation**: Bottom nav (Home, Survey, Welfare, Profile)
- **Notes**: Minimal text, icon-first for accessibility

### Screen 2: Survey – Step 1 (Demographics)
- **Purpose**: Collect household demographic data
- **Fields**: Household size, income range, occupation type
- **UX**: Progress bar, simple dropdowns and number inputs

### Screen 3: Survey – Step 2 (Living Conditions)
- **Purpose**: Capture living condition details
- **Fields**: Water source, sanitation, electricity, structure type
- **UX**: Radio buttons, checkboxes

### Screen 4: Survey – Confirmation
- **Purpose**: Review and submit
- **Elements**: Summary of entries, Submit button, Edit option

### Screen 5: Welfare Schemes
- **Purpose**: Show eligible government schemes
- **Elements**: Card list with scheme name, eligibility %, Apply button
- **UX**: Filter by category (housing, health, education)

### Screen 6: Emergency
- **Purpose**: Trigger emergency alert
- **Elements**: Large red Emergency button, confirmation dialog
- **UX**: One-tap with safety confirmation

---

## Citizen Reporting Interface

### Screen 1: Report – Capture
- **Purpose**: Start a new report
- **Elements**: Camera button, "Take Photo" CTA
- **Flow**: Opens device camera

### Screen 2: Report – Location
- **Purpose**: Confirm or adjust location
- **Elements**: Map with draggable pin, address text
- **UX**: Auto-detect GPS, manual adjust option

### Screen 3: Report – Details
- **Purpose**: Add optional description
- **Elements**: Text area, Submit button
- **UX**: Optional field, character limit

### Screen 4: Report – Confirmation
- **Purpose**: Confirm submission
- **Elements**: Success message, reference ID, "Report Another" option

---

## Nodal Officer Dashboard

### Screen 1: Login
- **Purpose**: Authenticate nodal officer
- **Elements**: Email, password, Login button

### Screen 2: Case Queue
- **Purpose**: List of assigned cases
- **Elements**: Table/cards with case ID, location, status, date
- **Filters**: Status, date range, priority
- **Actions**: Open case, bulk assign

### Screen 3: Case Detail
- **Purpose**: Full case view for verification
- **Elements**: Photos, map, report details, notes, status dropdown
- **Actions**: Verify, Dispute, Escalate, Add Note

### Screen 4: Heatmap View
- **Purpose**: Visualize settlement density
- **Elements**: Map with heatmap overlay, layer toggles
- **UX**: Click cluster to see cases

---

## Government Overview Dashboard

### Screen 1: Login
- **Purpose**: Authenticate government user
- **Elements**: Credentials, role-based redirect

### Screen 2: Analytics Overview
- **Purpose**: High-level metrics
- **Elements**: KPI cards (total settlements, new reports, verified), trend chart
- **UX**: Date range selector

### Screen 3: Reports
- **Purpose**: Detailed report list
- **Elements**: Filterable table, export button
- **Columns**: Region, settlement count, status, date

### Screen 4: Heatmap
- **Purpose**: City-wide settlement visualization
- **Elements**: Full map, region selector, legend
- **UX**: Zoom, pan, click for details
