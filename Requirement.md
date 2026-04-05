# Requirements Document

## 1. Application Overview

- **Application Name:** RoadWatch
- **Description:** RoadWatch is an all-in-one road intelligence platform that merges traffic law compliance, road quality monitoring, and emergency response into a single, visually immersive tool. It delivers location-aware insights, citizen reporting capabilities, and instant emergency access — all wrapped in a highly animated, modern interface.

---

## 2. Users & Use Cases

### 2.1 Target Users
- Everyday drivers and commuters
- Concerned citizens and road safety advocates
- Travelers unfamiliar with local traffic regulations
- Anyone involved in or witnessing a road accident

### 2.2 Core Use Cases
- A driver checks local traffic laws and fine schedules before entering a new state or city
- A citizen reports a pothole or damaged road sign and tracks whether it has been addressed
- A road accident victim or bystander instantly locates the nearest trauma centre, ambulance, or police station
- A user monitors public spending on road infrastructure in their area

---

## 3. Page Structure & Feature Description

### 3.1 Overall Structure

```
RoadWatch App
├── Splash / Landing Screen (animated entry)
├── Home Dashboard
│   ├── Module Card: DriveLegal
│   ├── Module Card: RoadWatch (Monitoring)
│   └── Module Card: RoadSOS
├── DriveLegal Module
│   ├── Location Detection Banner
│   ├── National Traffic Laws Panel
│   ├── State Laws Panel
│   ├── Local Enforcement Panel
│   └── Fine Schedule Table
├── RoadWatch Module (Road Monitoring)
│   ├── Road Quality Map View
│   ├── Issue Report Form
│   ├── My Reports Tracker
│   └── Public Spending Dashboard
├── RoadSOS Module
│   ├── Emergency Map (nearby services)
│   ├── Quick-Dial Emergency Contacts
│   └── Accident Checklist
└── Settings / Location Preferences
```

---

### 3.2 Splash / Landing Screen
- Full-screen animated entry with the RoadWatch logo emerging from a road-perspective animation (vanishing point highway effect using CSS/canvas animation)
- Animated tagline cycling through: \"Know the Law. Watch the Road. Get Help Fast.\"
- Auto-transitions to Home Dashboard after 2.5 seconds, or on tap/click
- Background: dark asphalt texture with animated lane markings scrolling upward

---

### 3.3 Home Dashboard
- Sticky top navigation bar with the RoadWatch logo and a live location chip (city + country)
- Three large animated module cards arranged vertically (mobile-first) or in a 3-column grid (desktop):
  - **DriveLegal Card** — icon: gavel/law book, accent color: electric blue, hover animation: card lifts with glow
  - **RoadWatch Card** — icon: road/map pin, accent color: amber/orange, hover animation: road ripple effect
  - **RoadSOS Card** — icon: siren/cross, accent color: red, hover animation: pulsing red ring
- Each card displays a one-line description and an animated entry arrow
- Animated background: subtle moving road grid (parallax scroll effect)
- Bottom status bar: current location, time, and a live \"Road Alert\" ticker (scrolling text of simulated local alerts)

---

### 3.4 DriveLegal Module

#### 3.4.1 Location Detection Banner
- Displays detected country, state, and city with a flag icon and animated location pin drop
- Manual override: user can search or select a different location via a dropdown
- Smooth slide-in animation on load

#### 3.4.2 Traffic Laws Panel (Tabbed Layout)
- Three tabs: **National**, **State**, **Local**
- Each tab contains an accordion list of law categories (e.g., Speed Limits, Seatbelts, Mobile Phone Use, Alcohol Limits, Overtaking Rules)
- Each accordion item expands with a smooth slide-down animation to reveal the rule description
- Law items are color-coded by severity: informational (blue), warning (amber), strict (red)
- Animated icon per category (e.g., speedometer for speed limits, phone icon with cross for mobile use)

#### 3.4.3 Fine Schedule Table
- Displayed below the law panels
- Columns: Violation | Fine Amount (min–max) | Points Deducted | Notes
- Rows animate in sequentially on scroll (staggered fade-up)
- Sortable by fine amount or violation name
- A highlighted \"Most Common Violations\" section at the top with badge indicators

#### 3.4.4 Compliance Tips
- A horizontally scrollable card strip at the bottom with animated tip cards
- Each card has a short tip, an icon, and a color-coded urgency level

---

### 3.5 RoadWatch Module (Road Quality Monitoring)

#### 3.5.1 Road Quality Map View
- Interactive map centered on user's current location
- Road segments color-coded by quality: green (good), yellow (fair), orange (poor), red (critical)
- Animated pulsing markers for recently reported issues
- Cluster animation when zooming out (markers group and display count)
- Toggle layers: Issue Reports | Public Spending Zones | Road Works

#### 3.5.2 Issue Report Form
- Triggered via a floating action button (FAB) with a \"+\" icon and a ripple animation on press
- Form fields:
  - Issue Type (dropdown with icons): Pothole, Damaged Signage, Broken Barrier, Flooding, Missing Road Markings, Other
  - Severity (slider: 1–5 with animated color shift from green to red)
  - Description (text area, max 300 characters)
  - Location (auto-filled from GPS, with manual pin-drop option on mini-map)
  - Photo Upload (optional, supports up to 3 images)
- Submit button with a loading spinner and a success animation (checkmark draw-on effect)
- Submitted reports appear on the map within the same session with a \"Pending Review\" badge

#### 3.5.3 My Reports Tracker
- List view of all reports submitted by the current user (session-based or account-based)
- Each report card shows: issue type icon, location, date submitted, and a status badge
- Status states: Pending Review → Acknowledged → In Progress → Resolved
- Status badge animates with a color transition when status changes
- Tap a report card to expand details and view any authority response

#### 3.5.4 Public Spending Dashboard
- Displays road infrastructure budget allocation and spending data by region
- Visualizations:
  - Animated donut chart: budget categories (maintenance, new construction, signage, lighting)
  - Animated bar chart: monthly spending over the past 12 months
  - KPI tiles: Total Budget | Spent to Date | Projects Completed | Projects Ongoing
- KPI tiles count up from 0 on load (number counter animation)
- Data source label: \"Simulated public data for prototype purposes\"
- Filter by: Region / Year

---

### 3.6 RoadSOS Module

#### 3.6.1 Emergency Map
- Full-screen map view centered on user's GPS location
- Animated radar sweep effect emanating from user's position on load
- Nearby service markers with distinct icons and colors:
  - Trauma Centres: red cross icon
  - Ambulance Services: orange ambulance icon
  - Vehicle Rescue / Towing: blue tow-truck icon
  - Police Stations: dark blue shield icon
- Each marker pulses gently to draw attention
- Tapping a marker opens a bottom sheet with: name, distance, estimated travel time, address, and a \"Call Now\" button
- \"Call Now\" button triggers a simulated dial action with a phone-ring animation

#### 3.6.2 Quick-Dial Emergency Contacts
- Persistent bottom strip (or side panel on desktop) with large, high-contrast emergency buttons:
  - Ambulance (red)
  - Police (blue)
  - Fire / Rescue (orange)
  - Roadside Assistance (yellow)
- Each button has an animated icon (e.g., siren flash, phone vibrate on hover/press)
- Buttons display the local emergency number based on detected location
- One-tap initiates a simulated call with a confirmation modal to prevent accidental dials

#### 3.6.3 Accident Checklist
- Accessible via a \"What to Do Now\" button on the RoadSOS screen
- Animated step-by-step checklist that reveals one step at a time:
  1. Ensure personal safety — move to a safe location
  2. Call emergency services
  3. Do not move injured persons unless in immediate danger
  4. Document the scene (photos, license plates)
  5. Exchange details with other parties
  6. Notify your insurance provider
- Each step has an icon, a short description, and a \"Done\" tap to advance
- Progress bar at the top animates as steps are completed
- Final step shows a calming confirmation screen: \"You've done the right things. Help is on the way.\"

---

### 3.7 Settings / Location Preferences
- Default location: auto-detect via browser geolocation API
- Manual location override: country → state → city cascading dropdowns
- Unit preference: metric (km/h, km) or imperial (mph, miles)
- Theme toggle: Dark Mode (default) / Light Mode with animated sun/moon transition
- Language preference (UI language): English (default for prototype)
- Notification preference toggle for road alerts (simulated)

---

## 4. Business Rules & Logic

1. **Location Awareness:** All three modules (DriveLegal, RoadWatch, RoadSOS) must reflect the user's currently selected or detected location. Changing location in Settings updates all modules simultaneously.
2. **DriveLegal Data Hierarchy:** Laws are displayed in order: National → State → Local. Where local rules override national rules, a visual \"Local Override\" badge is shown.
3. **Report Submission:** Each report is assigned a unique ID and timestamped. Reports are stored in the backend and visible on the shared map to all users.
4. **Emergency Number Localization:** Quick-dial numbers must reflect the correct emergency numbers for the detected country (e.g., 911 for USA, 999 for UK, 112 for EU, 100/102/108 for India).
5. **Severity Color Logic (Road Quality Map):** Color coding is derived from the aggregate severity score of all reports in a road segment: avg 1–2 = green, 3 = yellow, 4 = orange, 5 = red.
6. **Accident Checklist State:** Checklist progress is not persisted between sessions; it resets on each new visit to RoadSOS.
7. **Spending Dashboard Data:** For the prototype, spending data is simulated/static but structured to be replaceable with a live API feed.

---

## 5. Exceptions & Edge Cases

| Scenario | Handling |
|---|---|
| Geolocation permission denied | Prompt user to manually select location; default to a placeholder city (e.g., New York, USA) |
| No internet connection | Show a cached/offline banner; disable map and live features gracefully |
| Location not covered by law database | Display national-level laws only; show a notice: \"State/local data not yet available for this region\" |
| No nearby emergency services found | Show message: \"No services found within 50 km. Please call the national emergency number.\" with the number displayed prominently |
| Report submission failure | Show an error toast with a retry button; preserve form data |
| Map fails to load | Show a static fallback list of nearby services with addresses |
| User submits duplicate report for same location | Warn: \"A similar report already exists nearby. Would you like to upvote it instead?\" |

---

## 6. Acceptance Criteria

1. The Splash Screen animation plays correctly and auto-transitions to the Home Dashboard within 2.5 seconds.
2. The Home Dashboard displays all three module cards with correct icons, colors, and hover/tap animations.
3. DriveLegal correctly displays laws filtered by the detected or manually selected location across all three tabs (National, State, Local).
4. The Fine Schedule Table renders all columns, supports sorting, and rows animate in on scroll.
5. The Road Quality Map loads centered on the user's location with color-coded road segments and pulsing issue markers.
6. The Issue Report Form submits successfully, shows a success animation, and the new report appears on the map.
7. My Reports Tracker displays submitted reports with correct status badges.
8. The Public Spending Dashboard renders all three chart types with count-up animations on load.
9. The RoadSOS Emergency Map displays the radar sweep animation and correctly categorized nearby service markers.
10. Quick-Dial buttons display the correct local emergency numbers and trigger a confirmation modal before simulating a call.
11. The Accident Checklist advances step by step with progress bar animation and displays the final confirmation screen.
12. Location change in Settings propagates to all three modules without requiring a page reload.
13. Dark Mode is the default theme; Light Mode toggle works with a smooth animated transition.
14. All animations (card hovers, accordion expand, chart load, map markers, checklist steps) render smoothly without layout shifts.
15. The application is fully functional as a prototype with simulated/static data where live APIs are not connected.

---

## 7. Out of Scope (This Release)

- User authentication, login, or account creation
- Real-time live traffic data integration
- Push notifications or background alerts
- Native mobile app (iOS/Android) packaging
- Multi-language localization beyond English
- Payment or fine payment processing
- Integration with actual government or municipal APIs
- Offline-first PWA capabilities
- Admin panel for reviewing and updating citizen reports
- AI-based road damage detection from uploaded photos