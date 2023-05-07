# 🛠️ Using the ReVanced CLI

Learn how to use the ReVanced CLI.

## ⚡ Setup (optional) Enable Debugging (Developer Options) 

1. Make sure your device is connected

   ```bash
   adb shell exit
   ```

   If you plan to use the root variant, check if you have root access. Allow on Su prompt 4 shell(Magisk) after execution

   ```bash
   adb shell su -c exit
   ```

2. Copy the ADB device name

   ```bash
   adb devices
   ```

## 🔨 ReVanced CLI Usage (change .jar file names same as downloaded one's)

- ### Show all available options for the ReVanced CLI

  ```bash
  java -jar revanced-cli.jar -h
  ```

- ### List all available patches from supplied patch bundles

  ```bash
  java -jar revanced-cli.jar -b revanced-patches.jar -a input.apk -l
  ```

- ### Use the ReVanced CLI without root permissions

  ```bash
  java -jar revanced-cli.jar -a input.apk -o patched-output.apk -m revanced-integrations.apk -b revanced-patches.jar
  ```

- ### Mount the patched application with root permissions over the installed application

  ```bash
  adb install input.apk # Just make sure the same version is installed
  java -jar revanced-cli.jar -a input.apk -m revanced-integrations.apk -d device-name(adb) -o patched-output.apk -b revanced-patches.jar -e vanced-microg-support --mount
  ```
- ### Example
  ```bash 
  java -jar revanced-cli-2.21.1-all.jar -c -a youtube-18-16-37.apk -m revanced-integrations-0.107.0.apk -o revanced.apk -e vanced-microg-support -b revanced-patches-2.173.0.jar -d b9dl69c7 --mount
  ```

> **Note**:
> Check all options from help menu -h.
> - If you want to exclude patches, you can use the option `-e`. In the case of YouTube(Root), you can exclude
    the `vanced-microg-support` patch from [ReVanced Patches](https://github.com/revanced/revanced-patches) with the
    option `-e vanced-microg-support` when mounting for example.
>
> - Some patches from [ReVanced Patches](https://github.com/revanced/revanced-patches) also might require
    [ReVanced Integrations](https://github.com/revanced/revanced-integrations). Supply them with the option `-m`.
    > The integrations will be merged, if necessary automatically, if supplied.
>
> - If you supplied a device with the option `-d`, the patched application will be automatically installed on the
    device.
