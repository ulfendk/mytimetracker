# Cloud Sync Setup Guide

This guide will help you configure Google Drive integration for automatic cloud backup of your time tracking data.

## Prerequisites

- A Google account
- Access to Google Cloud Console

## Setup Steps

### 1. Create a Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Click "Select a project" at the top
3. Click "New Project"
4. Enter a project name (e.g., "My Time Tracker")
5. Click "Create"

### 2. Enable Google Drive API

1. In your project, go to "APIs & Services" > "Library"
2. Search for "Google Drive API"
3. Click on "Google Drive API"
4. Click "Enable"

### 3. Create OAuth 2.0 Credentials

1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "OAuth client ID"
3. If prompted, configure the OAuth consent screen:
   - Choose "External" user type
   - Fill in the required fields:
     - App name: "My Time Tracker"
     - User support email: your email
     - Developer contact information: your email
   - Click "Save and Continue"
   - Skip adding scopes (click "Save and Continue")
   - Add test users if needed (your email)
   - Click "Save and Continue"
4. Back to creating OAuth client ID:
   - Application type: "Web application"
   - Name: "My Time Tracker Web Client"
   - Authorized JavaScript origins:
     - Add: `https://ulfendk.github.io` (for GitHub Pages)
     - Add: `http://localhost:8000` (for local testing, if needed)
   - Click "Create"
5. Copy the **Client ID** that is displayed

### 4. Create an API Key

1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "API key"
3. Copy the **API Key** that is generated
4. (Recommended) Click "Restrict Key":
   - Application restrictions: HTTP referrers (web sites)
   - Add referrer: `ulfendk.github.io/*`
   - API restrictions: Select "Restrict key"
   - Select: "Google Drive API"
   - Click "Save"

### 5. Configure the Application

1. Open `index.html` in a text editor
2. Find the `initCloudSync()` method (around line 1030)
3. Update the following lines with your credentials:
   ```javascript
   this.GOOGLE_CLIENT_ID = 'YOUR_CLIENT_ID_HERE';
   this.GOOGLE_API_KEY = 'YOUR_API_KEY_HERE';
   ```
4. Save the file

### 6. Deploy and Test

1. If you're using GitHub Pages, commit and push your changes
2. Wait for deployment to complete
3. Open the application
4. Click the Settings button (⚙️)
5. Enable "Cloud Auto-Save"
6. Click "Sync Now"
7. Sign in with your Google account when prompted
8. Authorize the application to access your Google Drive

## Usage

Once configured:

- Your data will automatically sync to Google Drive whenever you make changes
- A file named `mytimetracker-data.json` will be created in your Google Drive
- The sync status is displayed in the Settings modal
- You can manually trigger a sync by clicking "Sync Now"

## Troubleshooting

### "Cloud sync requires Google API credentials to be configured"

This means the `GOOGLE_CLIENT_ID` or `GOOGLE_API_KEY` is not set in the code. Follow the setup steps above.

### "Sign-in failed"

- Check that your Client ID is correct
- Verify that the application URL is listed in "Authorized JavaScript origins"
- Make sure the OAuth consent screen is properly configured

### "Sync failed"

- Check your internet connection
- Verify that you're signed in to Google
- Check browser console for detailed error messages

## Alternative: Manual Backup

If you prefer not to configure Google API credentials or want to use a different cloud service:

1. Use the "Save Data" button to download your data as JSON
2. Upload the JSON file to your preferred cloud storage (iCloud Drive, Dropbox, OneDrive, etc.)
3. To restore, download the JSON file and use the "Load Data" button

## Security Notes

- Your API key and Client ID are safe to include in the code (they're designed for client-side use)
- OAuth 2.0 ensures secure authentication without storing passwords
- Data is transmitted securely via HTTPS
- Only you can access your time tracking data through your Google account
- You can revoke access anytime from your [Google Account permissions](https://myaccount.google.com/permissions)

## Privacy

- The application only accesses files it creates (`mytimetracker-data.json`)
- No data is sent to any third-party servers except Google Drive
- All processing happens locally in your browser
