# XCODE SETTINGS
1. Enable Bitcode
2. Add **-fembed-bitcode** flag to **Other C flags** and **Other linker flags**
3. Add **BUILD_LIBRARY_FOR_DISTRIBUTION = YES**

# EXPORT FRAMEWORK
https://stackoverflow.com/a/29650369

# SAMPLE CODE
`lipo -info ISPORTSDK`

`lipo -remove arm64 ISPORTSDK -o ISPORTSDK`

`lipo -create -output "ISPORTSDK" "ISPORTSDK.framework/ISPORTSDK" "sim-ISPORTSDK.framework/ISPORTSDK"`