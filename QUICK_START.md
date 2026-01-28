# Quick Start: Using Cloud Auto-Save

## What is Cloud Auto-Save?

Cloud Auto-Save automatically backs up your time tracking data to Google Drive whenever you make changes. This provides:
- ✅ Automatic backups without manual downloads
- ✅ Access your data from multiple devices
- ✅ Peace of mind - your data is safely stored in the cloud

## Quick Start (3 Steps)

### For Repository Owners/Developers

1. **Set Up Google API Credentials**
   - Follow the detailed guide in [CLOUD_SYNC_SETUP.md](CLOUD_SYNC_SETUP.md)
   - You'll need to create a Google Cloud project and get credentials
   - This is a one-time setup

2. **Configure the Application**
   - Edit `index.html` 
   - Add your Google Client ID and API Key to the `initCloudSync()` method
   - Deploy your changes

3. **Enable and Use**
   - Install the app as a PWA
   - Go to Settings (⚙️ icon)
   - Enable "Cloud Auto-Save"
   - Click "Sync Now" to connect
   - Your data will now automatically backup!

### For End Users (When Not Configured)

If the repository owner hasn't configured Google API credentials, you can still backup to cloud storage:

1. **Manual Backup**
   - Click "Save Data" button to download your data as JSON
   - Upload the JSON file to your preferred cloud service:
     - Google Drive
     - Apple iCloud
     - Dropbox
     - OneDrive
     - Any other cloud storage

2. **Restore on Another Device**
   - Download the JSON file from your cloud storage
   - Click "Load Data" button
   - Paste the JSON content
   - Your data is restored!

## How It Works

```
[You make changes] 
    ↓
[2-second delay (debounce)]
    ↓
[Auto-sync to Google Drive]
    ↓
[Status: "Synced successfully"]
```

## Status Indicators

In the Settings modal, you'll see:

- **"Not configured"** - API credentials need to be set up
- **"Click 'Sync Now' to connect"** - Ready to connect to Google Drive
- **"Syncing..."** - Currently uploading data
- **"Synced successfully"** - Data backed up! ✅
- **"Auto-sync failed - will retry"** - Temporary issue, will try again
- **"Connected to Google Drive"** - Signed in and ready

## Tips

- **Install as PWA**: Settings button is visible in PWA mode
- **Check Status**: Open Settings to see last sync status
- **Manual Sync**: Click "Sync Now" anytime to force a backup
- **Disable Anytime**: Toggle off "Cloud Auto-Save" to stop automatic backups
- **Your Data is Safe**: Only you can access your Google Drive files

## Troubleshooting

**"Cloud sync requires Google API credentials to be configured"**
- Ask the repository owner to configure Google API credentials
- OR use the manual Save/Load Data buttons

**"Sign-in failed"**
- Check your internet connection
- Make sure you're using the deployed URL (not local file://)
- Verify API credentials are correctly configured

**"Sync failed"**
- Check your internet connection
- Try signing out and signing in again
- Check browser console for detailed error messages

## Privacy & Security

- 🔒 OAuth 2.0 secure authentication
- 🔒 Data encrypted in transit (HTTPS)
- 🔒 Only you can access your data
- 🔒 Revoke access anytime at [Google Account Permissions](https://myaccount.google.com/permissions)
- 🔒 No third-party data collection

## Alternative: Using iCloud Drive (iOS/macOS)

For Apple users who prefer iCloud:

1. Click "Save Data" to download JSON
2. Save to iCloud Drive folder
3. On other Apple devices, access from iCloud Drive
4. Use "Load Data" to restore

Works great with the iOS PWA!

## Need Help?

- 📖 Read the full setup guide: [CLOUD_SYNC_SETUP.md](CLOUD_SYNC_SETUP.md)
- 🔍 Check the testing guide: [TESTING_GUIDE.md](TESTING_GUIDE.md)
- 🔐 Review security details: [SECURITY_SUMMARY.md](SECURITY_SUMMARY.md)

---

**Remember**: Cloud Auto-Save is optional. The app works perfectly fine with just local storage and manual backups!
