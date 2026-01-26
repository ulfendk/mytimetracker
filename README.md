# My Time Tracker

A simple, browser-based work time tracking application that requires no backend. All data is stored locally in your browser.

## Features

- 📊 Track multiple work intervals per day
- ⏰ Record break times for each interval
- 📅 View and manage work hours by week
- 📆 Monthly overview with balance tracking (actual vs expected hours)
- 🏖️ Mark days off and holidays
- 💾 All data stored in browser (localStorage)
- 📥 Save data as JSON
- 📤 Load previously saved data
- 🧮 Automatic calculation of daily and weekly totals
- 📱 **Progressive Web App (PWA) - Install on your phone or desktop**

## Live Demo

The application is automatically deployed to GitHub Pages: [View Live Demo](https://ulfendk.github.io/mytimetracker/)

## Progressive Web App (PWA)

My Time Tracker can be installed as a Progressive Web App on your device for a native app-like experience:

### Installation

**On Desktop (Chrome, Edge, Brave):**
1. Visit the [live demo](https://ulfendk.github.io/mytimetracker/)
2. Click the install icon (⊕) in the address bar or look for "Install My Time Tracker" in the browser menu
3. Click "Install" in the confirmation dialog

**On Mobile (iOS Safari):**
1. Visit the [live demo](https://ulfendk.github.io/mytimetracker/)
2. Tap the Share button (box with arrow pointing up)
3. Scroll down and tap "Add to Home Screen"
4. Tap "Add"

**On Mobile (Android Chrome):**
1. Visit the [live demo](https://ulfendk.github.io/mytimetracker/)
2. Tap the three-dot menu
3. Tap "Add to Home screen" or "Install app"
4. Tap "Install"

### PWA Benefits
- **Offline Access**: Works without internet connection once installed
- **Native Feel**: Runs in standalone mode without browser UI
- **Quick Access**: Launch from home screen or desktop
- **Automatic Updates**: Always get the latest version when online

## Usage

1. Open `index.html` in your web browser or use the live demo
2. Navigate between weeks using the Previous/Next Week buttons
3. For each day, add work intervals by clicking "Add Interval"
4. Set start time, end time, and break duration for each interval
5. Mark days off/holidays using the "Mark as Day Off" button
6. View your weekly summary at the bottom of the page
7. Click "Monthly Overview" to see monthly statistics and balance tracking

## Data Management

### Save Data
Click the "Save Data" button to download your time tracking data as a JSON file. This allows you to:
- Back up your data
- Share data between different browsers
- Archive historical records

### Load Data
Click the "Load Data" button and paste your previously saved JSON data to restore it.

### Clear Data
Use the "Clear All Data" button to reset the application (requires confirmation).

### Monthly Overview
Click the "Monthly Overview" button to view comprehensive monthly statistics:
- **Actual vs Expected Hours**: Compare your actual work hours against expected hours (based on working days × 7.5 hours/day)
- **Balance Tracking**: See if you're ahead or behind on your expected hours
- **Monthly Statistics**: View working days, days off, and average hours per day
- **Daily Breakdown**: Review all work days and holidays for the month
- **Month Navigation**: Browse through different months to review historical data

The monthly overview automatically:
- Excludes weekends from expected hours calculations
- Accounts for marked days off/holidays
- Color-codes the balance (green for positive, red for negative)

## Technical Details

- **No Backend Required**: All functionality runs entirely in the browser
- **Data Storage**: Uses browser's localStorage API
- **Data Format**: JSON
- **Responsive Design**: Works on desktop and mobile devices
- **Progressive Web App**: Installable with offline support via Service Worker
- **Deployment**: Automatically deployed to GitHub Pages on PR merge to main branch

## Browser Compatibility

Works in all modern browsers that support:
- HTML5
- CSS3
- ES6 JavaScript
- localStorage API

## License

Open source - feel free to use and modify as needed.