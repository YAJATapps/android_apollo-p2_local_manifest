# android_apollo-p2_local_manifest (LineageOS 24 / Android 17)

Local manifest and build instructions for building LineageOS 24 (Android 17) for the Orange Pi Zero 2W (`apollo-p2` / Allwinner H618).

---

## 1. Initialize LineageOS 24.0 Source

```bash
repo init -u https://github.com/LineageOS/android.git -b lineage-24.0 --git-lfs --depth=1
```

---

## 2. Add Local Manifest

```bash
curl -o .repo/local_manifests/local_manifest.xml -L https://raw.githubusercontent.com/YAJATapps/android_apollo-p2_local_manifest/refs/heads/lineage-24/local_manifest.xml --create-dirs
```

---

## 3. Sync Repositories

```bash
repo sync
```

---

## 4. Build Kernel & Bootloader (Longan)

The Allwinner kernel (Linux 6.18) and bootloader must be compiled in `longan` before lunching the Android build:

```bash
cd longan
git lfs pull
./build.sh autoconfig -i h618 -o android -b p2 -n default -k linux-6.18 -a arm64
./build.sh
cd ..
```

---

## 5. Apply Device Patches

Run the automated patching script to apply necessary platform fixes:

```bash
./device/allwinner/apollo-p2/patches.sh
```

---

## 6. Build Android

```bash
source build/envsetup.sh
lunch lineage_apollo_p2-cp2a-userdebug
m
```

---

## 7. Pack Firmware Image

Pack the final image into Allwinner format (PhoenixCard / LiveSuit flashable):

```bash
pack
```

The output image is generated at:
`longan/out/h618_android17_p2_uart0.img`

