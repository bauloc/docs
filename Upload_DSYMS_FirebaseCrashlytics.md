Only and simple way to upload DSYMS files to Firebase Crashlytics. (June 1 - 2020)

# Download appDsyms archive from App Store

1.1 Login: https://appstoreconnect.apple.com

1.2 Go to: MyApps -> Choose your app -> Activity (top left) -> Select version you want to get crashes -> Includes Symbols: press -> Download dSYM.

# Open terminal, drag and drop 3 files on terminal on this order:

2.1 drag an drop: "upload-symbols" which can be found in /project/Pods/FirebaseCrashlytics/upload-symbols

2.2 write "-gsp"

2.3 drag an drop: "GoogleService-Info.plist" which can be found in /project/GoogleService-Info.plist

2.4 write "-p ios"

2.5 drag an drop: "appDsyms" folder which usually is in Download folder /Users/username/Downloads/appDsyms

2.6 Press Enter

# In terminal the complete command should include -gsp and -p ios, full command looks like this: 
``` 
2.1 -gsp 2.3 -p ios 2.5
```
``` 
/project/Pods/FirebaseCrashlytics/upload-symbols -gsp /project/GoogleService-Info.plist -p ios /Users/username/Downloads/appDsyms
```
