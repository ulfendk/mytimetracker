# My Time Tracker

A simple, browser-based work time tracking application that requires no backend. All data is stored locally in your browser.

## Features

- 📊 Track multiple work intervals per day
- ⏰ Record break times for each interval
- 📅 View and manage work hours by week
- 🏖️ Mark days off and holidays
- 💾 All data stored in browser (localStorage)
- 📥 Export data as JSON
- 📤 Import previously exported data
- 🧮 Automatic calculation of daily and weekly totals

## Live Demo

The application is automatically deployed to GitHub Pages: [View Live Demo](https://ulfendk.github.io/mytimetracker/)

## Usage

1. Open `index.html` in your web browser or use the live demo
2. Navigate between weeks using the Previous/Next Week buttons
3. For each day, add work intervals by clicking "Add Interval"
4. Set start time, end time, and break duration for each interval
5. Mark days off/holidays using the "Mark as Day Off" button
6. View your weekly summary at the bottom of the page

## Data Management

### Export Data
Click the "Export Data" button to download your time tracking data as a JSON file. This allows you to:
- Back up your data
- Share data between different browsers
- Archive historical records

### Import Data
Click the "Import Data" button and paste your previously exported JSON data to restore it.

### Clear Data
Use the "Clear All Data" button to reset the application (requires confirmation).

## Technical Details

- **No Backend Required**: All functionality runs entirely in the browser
- **Data Storage**: Uses browser's localStorage API
- **Data Format**: JSON
- **Responsive Design**: Works on desktop and mobile devices
- **Deployment**: Automatically deployed to GitHub Pages on PR merge to main branch

## Browser Compatibility

Works in all modern browsers that support:
- HTML5
- CSS3
- ES6 JavaScript
- localStorage API

## License

Open source - feel free to use and modify as needed.