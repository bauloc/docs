# Step 1
1. Export **myapp.ipa** from **Xcode**
2. Rename **myapp.ipa** to **myapp.zip**, export it then copy **myapp.app**

# Step 2
1. Create `MyApp` folder
2. In `MyApp` folder, create folder structure
```
+- MyProgram
 +- Applications
 | +- MyProgram.app 

+- DEBIAN 
| +- control 
```

3. Open `control` copy, edit and save with no extension.
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

# Step 2
Remove '.DS_Store' file
find . -name '.DS_Store' -type f -delete

# Step 3