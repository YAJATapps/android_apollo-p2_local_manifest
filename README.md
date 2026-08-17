# android_apollo-p2_local_manifest  

WIP

repo init -u https://github.com/LineageOS/android.git -b lineage-23.2 --git-lfs --depth=1

curl -o .repo/local_manifests/local_manifest.xml -L https://raw.githubusercontent.com/YAJATapps/android_apollo-p2_local_manifest/refs/heads/lineage-23.2/local_manifest.xml --create-dirs

repo sync

cd longan

git lfs pull
