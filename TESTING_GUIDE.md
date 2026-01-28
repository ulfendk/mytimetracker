# Testing Guide for Cloud Sync Feature

## Manual Testing Checklist

This guide helps verify the cloud sync feature works correctly.

## Prerequisites for Full Testing

To fully test the Google Drive integration:
1. Follow the setup in `CLOUD_SYNC_SETUP.md` to configure Google API credentials
2. Deploy the application to a web server or GitHub Pages
3. Have a Google account for testing

## Test Cases

### Test 1: UI Elements Present
**Prerequisites**: None

**Steps**:
1. Open the application
2. Install as PWA (or open in standalone mode)
3. Click the Settings button (⚙️)

**Expected Results**:
- ✅ Settings modal opens
- ✅ "Auto-Update" toggle is visible
- ✅ "Cloud Auto-Save" toggle is visible
- ✅ "Cloud Sync Status" section is hidden by default

### Test 2: Enable Cloud Sync Without Credentials
**Prerequisites**: API credentials NOT configured (default state)

**Steps**:
1. Open Settings
2. Enable the "Cloud Auto-Save" toggle

**Expected Results**:
- ✅ Alert appears explaining Google API credentials are required
- ✅ Instructions provided for manual backup as alternative
- ✅ Toggle automatically switches back to disabled

### Test 3: Cloud Sync Status Visibility
**Prerequisites**: API credentials configured

**Steps**:
1. Open Settings
2. Enable the "Cloud Auto-Save" toggle

**Expected Results**:
- ✅ "Cloud Sync Status" section becomes visible
- ✅ Status shows "Click 'Sync Now' to connect"
- ✅ "Sync Now" button is visible

### Test 4: Google Sign-In
**Prerequisites**: API credentials configured

**Steps**:
1. Enable "Cloud Auto-Save" in Settings
2. Click "Sync Now" button

**Expected Results**:
- ✅ Google sign-in popup appears
- ✅ User can select Google account
- ✅ OAuth consent screen shows requested permissions
- ✅ After authorization, sync status updates to "Connected to Google Drive"

### Test 5: Manual Sync
**Prerequisites**: Signed in to Google

**Steps**:
1. Make a change to time tracking data (add a work entry)
2. Open Settings
3. Click "Sync Now"

**Expected Results**:
- ✅ Status changes to "Syncing..."
- ✅ Status changes to "Synced successfully"
- ✅ Check Google Drive - `mytimetracker-data.json` file exists
- ✅ File contains current time tracking data

### Test 6: Auto-Sync on Data Change
**Prerequisites**: Signed in to Google, Cloud Auto-Save enabled

**Steps**:
1. Add a new work time entry
2. Wait 2-3 seconds
3. Check Settings for sync status

**Expected Results**:
- ✅ Status shows "Syncing..." briefly
- ✅ Status changes to "Synced successfully"
- ✅ Google Drive file is updated with new data

### Test 7: Auto-Sync Debouncing
**Prerequisites**: Signed in to Google, Cloud Auto-Save enabled

**Steps**:
1. Make multiple rapid changes (add several entries quickly)
2. Observe Settings sync status

**Expected Results**:
- ✅ Only one sync occurs (after changes stop)
- ✅ Not syncing after every single change
- ✅ Final sync includes all changes

### Test 8: Sync Across Devices
**Prerequisites**: Signed in to Google on both devices

**Steps**:
1. On Device A: Add time entries
2. Wait for auto-sync to complete
3. On Device B: Open the application
4. On Device B: Use "Load Data" with content from Google Drive file

**Expected Results**:
- ✅ Device B can load data from Google Drive
- ✅ All entries from Device A are visible on Device B

### Test 9: Disable Cloud Sync
**Prerequisites**: Cloud Auto-Save enabled

**Steps**:
1. Open Settings
2. Disable "Cloud Auto-Save" toggle

**Expected Results**:
- ✅ Toggle switches to off
- ✅ "Cloud Sync Status" section disappears
- ✅ Future data changes don't trigger auto-sync

### Test 10: Sign Out
**Prerequisites**: Signed in to Google

**Steps**:
1. Disable "Cloud Auto-Save"
2. Re-enable it
3. Check Google sign-in status

**Expected Results**:
- ✅ User needs to sign in again (if signed out)
- ✅ OR remains signed in if still authenticated

### Test 11: Error Handling - Network Offline
**Prerequisites**: Signed in to Google

**Steps**:
1. Disconnect from internet
2. Make a data change
3. Wait for auto-sync attempt

**Expected Results**:
- ✅ Status shows "Auto-sync failed - will retry" or similar
- ✅ No application crash
- ✅ Data still saved locally
- ✅ When reconnected, next change triggers successful sync

### Test 12: Data Integrity
**Prerequisites**: Signed in to Google

**Steps**:
1. Add time entries with various data (breaks, holidays, etc.)
2. Sync to Google Drive
3. Download the `mytimetracker-data.json` file from Google Drive
4. Verify file contents

**Expected Results**:
- ✅ JSON file is valid
- ✅ Contains all expected data fields (dates, holidays, weeklyExpectedHours)
- ✅ All time entries are present and correct
- ✅ Data can be imported back using "Load Data"

## Browser Compatibility Testing

Test on multiple browsers:
- [ ] Chrome/Edge (Desktop)
- [ ] Firefox (Desktop)
- [ ] Safari (Desktop & iOS)
- [ ] Chrome (Android)

Expected: Feature works consistently across all modern browsers

## Performance Testing

1. Add 100+ time entries
2. Enable cloud sync
3. Make a change

**Expected Results**:
- ✅ Sync completes within reasonable time (< 5 seconds)
- ✅ No UI lag or freezing
- ✅ File size in Google Drive is reasonable (< 1 MB for typical usage)

## Alternative Workflow Testing

### Manual Backup to Other Cloud Services

**Steps**:
1. Click "Save Data" button
2. Upload JSON file to iCloud/Dropbox/OneDrive
3. On different device, download JSON file
4. Click "Load Data" and paste JSON

**Expected Results**:
- ✅ Data successfully transfers between devices
- ✅ Works with any cloud storage service

## Known Limitations

- Google API credentials must be configured by the deployment owner
- Requires internet connection for cloud sync
- One file per Google account (not multi-device conflict resolution)
- Auto-sync has 2-second debounce (intentional design)

## Regression Testing

Verify existing features still work:
- [ ] Add/edit/delete time entries
- [ ] Mark days as holidays
- [ ] View monthly overview
- [ ] Export to Excel
- [ ] Manual Save/Load Data
- [ ] Clear all data
- [ ] Theme toggle
- [ ] PWA installation

All existing features should work unchanged.

## Test Results Template

```
Date Tested: ___________
Tester: ___________
Browser: ___________
Device: ___________

Test 1: [ ] Pass [ ] Fail - Notes: ___________
Test 2: [ ] Pass [ ] Fail - Notes: ___________
Test 3: [ ] Pass [ ] Fail - Notes: ___________
Test 4: [ ] Pass [ ] Fail - Notes: ___________
Test 5: [ ] Pass [ ] Fail - Notes: ___________
Test 6: [ ] Pass [ ] Fail - Notes: ___________
Test 7: [ ] Pass [ ] Fail - Notes: ___________
Test 8: [ ] Pass [ ] Fail - Notes: ___________
Test 9: [ ] Pass [ ] Fail - Notes: ___________
Test 10: [ ] Pass [ ] Fail - Notes: ___________
Test 11: [ ] Pass [ ] Fail - Notes: ___________
Test 12: [ ] Pass [ ] Fail - Notes: ___________

Overall Result: [ ] All tests passed [ ] Some tests failed

Issues Found:
___________________________________________
___________________________________________
```
