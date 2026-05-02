## Build
```
mkdir minimal-manifest-twrp
cd minimal-manifest-twrp
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1 -c --depth=1
mkdir .repo/local_manifests
echo '<manifest><project path="device/motorola/fogorow" name="korzenroot/android_device_motorola_fogorow-twrp" remote="github" revision="main"/></manifest>' > .repo/local_manifests/roomservice.xml
repo sync -j$(nproc --all) -c
. build/envsetup.sh
lunch twrp_fogorow-eng
mka clean -j$(nproc --all)
mka vendorbootimage -j$(nproc --all)
fastboot flash vendor_boot out/target/product/fogorow/vendor_boot.img
fastboot reboot recovery
```
