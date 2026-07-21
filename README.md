## Build
```
mkdir android
cd android
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1 -c --no-tags --depth=1 --no-clone-bundle --git-lfs
mkdir .repo/local_manifests
cat <<EOF > .repo/local_manifests/roomservice.xml
<manifest>
    <project path="device/motorola/fogorow" name="korzenroot/android_device_motorola_fogorow-twrp" remote="github" revision="main"/>
</manifest>
EOF
repo sync
. build/envsetup.sh
lunch twrp_fogorow-eng
mka clean -j$(nproc --all)
mka vendorbootimage -j$(nproc --all)
```
