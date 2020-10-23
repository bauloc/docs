# Requirement
```brew install dpkg```

# Step 1: Build IPA
1. Export `myapp.ipa` from `Xcode`
2. Rename `myapp.ipa` to `myapp.zip`, export it then copy `myapp.app`

# Step 2: Build Folder
1. Create `MyApp` folder
2. In `MyApp` folder, create folder structure
```
+- MyProgram
 +- Applications
 | +- MyProgram.app 

+- DEBIAN 
| +- control 
```

3. Open `control` file, copy edit and save with no extension.
```
Package: com.ios.MyApp
Name: MyApp
Version: 1.0
Architecture: iphoneos-arm
Description: This is a demo for building applications in Xcode and deploying through Cydia
Maintainer: bauloc
Author: bauloc
Section: Apps

```
Note: `control` must have new line at end of file.

4. Replace `MyProgram.app` with `myapp.app` copy at **Step 1**

# Step 3: Remove DS_Store file
In terminal cd to `MyApp` folder
```find . -name '.DS_Store' -type f -delete```

# Step 4: Build .deb file
In terminal cd to `MyApp` folder

```dpkg-deb -Zgzip -b MyApp```

# Step 5: Install .deb file
- Use `Filza` and `Airdrop` to install `MyApp.deb` file
- **uicache** if need