# android_apollo-p2_local_manifest  

repo init -u https://github.com/omnirom/android.git -b android-12.1 --depth=1

curl -o .repo/local_manifests/local_manifest.xml -L https://raw.githubusercontent.com/YAJATapps/android_apollo-p2_local_manifest/refs/heads/omni-12.1/local_manifest.xml --create-dirs

repo sync

cd longan

git lfs pull
