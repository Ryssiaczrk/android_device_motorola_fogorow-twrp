## Build
```
mkdir minimal-manifest-twrp
cd minimal-manifest-twrp
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
mkdir .repo/local_manifests
echo '<manifest><project path="device/motorola/fogorow" name="Ryssiaczrk/android_device_motorola_fogorow-twrp" remote="github" revision="main"/></manifest>' > .repo/local_manifests/android_device_motorola_fogorow-twrp.xml
repo sync -j$(nproc --all)
. build/envsetup.sh
lunch twrp_fogorow-eng
mka vendorbootimage -j$(nproc --all)
fastboot flash vendor_boot out/target/product/fogorow/vendor_boot.img
```
