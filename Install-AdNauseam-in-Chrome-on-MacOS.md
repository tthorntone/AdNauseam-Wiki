_NOTE: For advanced MacOS users only: additional support for these instructions will not be provided_

If you see the following message: “This extension is not listed in the Chrome Web Store and may have been added without your knowledge”, follow the steps below to use AdNauseam _without enabling Developer Mode_.
 
1. Find the extension-id for AdNauseam by going to chrome://extensions/. In the .crx file for the current release, this is `pbpgknjglhpmcpimfhgpmbmkglpphkof`

1. Save the following somewhere on your machine as `Enable AdNauseam.mobileconfig`:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>PayloadContent</key>
    <array>
      <dict>
        <key>ExtensionInstallAllowlist</key>
        <array>
          <string>pbpgknjglhpmcpimfhgpmbmkglpphkof</string>
        </array>
        <key>PayloadDescription</key>
        <string>Google Chrome Settings</string>
        <key>PayloadDisplayName</key>
        <string>Adds AdNauseam to the Allowlist</string>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadIdentifier</key>
        <string>com.google.chrome.36a05e5d-f42b-41a9-85dd-c8758af3615d</string>
        <key>PayloadType</key>
        <string>com.google.chrome</string>
        <key>PayloadUUID</key>
        <string>78cb0b76-2338-4a29-bd3c-964b63a8c28c</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
      </dict>
    </array>
    <key>PayloadDisplayName</key>
    <string>Enable AdNauseam</string>
    <key>PayloadIdentifier</key>
    <string>com.google.chrome</string>
    <key>PayloadRemovalDisallowed</key>
    <false />
    <key>PayloadScope</key>
    <string>System</string>
    <key>PayloadType</key>
    <string>Configuration</string>
    <key>PayloadUUID</key>
    <string>a0bd4c09-2812-427e-9214-497878ff785a</string>
    <key>PayloadVersion</key>
    <integer>1</integer>
  </dict>
</plist>
```
3. In your favorite text editor, make sure the string in the `ExtensionInstallAllowlist` block matches what you got in step 1, and save.

1. Double click the now-verified `Enable AdNauseam` file-- you should see a `Profile installation` popup telling you to review it in System Preferences.

1. Open System Preferences, and navigate to Profiles. Ensure that the Downloaded -> `Enable AdNauseam` profile is selected.

1. Click `Install...` in the top right, and click `Install` again in the following popup.

1. Restart chrome.

<br/>

Note: you may need to update the extension-id for newer versions of AdNauseam

<br/>

<sup>Thanks to Taylore for this workaround!</sup>