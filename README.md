# SmartAOSP

## Build

### Preparing and Downloading sources

After you prepare your build environment, you can download android source code from AOSP.
To initialize the android source, you must run this command:

    $ repo init -u https://android.googlesource.com/platform/manifest -b android-8.1.0_r41

After initialize AOSP repositories, add SmartAOSP manifest with following command:

    $ git clone -b 8.1.0 https://github.com/SmartAOSP/platform_manifest .repo/local_manifests

And run this command to download the source code:

    $ repo sync -j5

### Configure build environment and build Nexus 4 (mako/occam)

Run following commands:

    $ . build/envestup.sh
    $ lunch occam-user
    $ make updatepackage

### Sign the build with releasekeys

Place your keys in the /vendor/smart/build/security directory
Run the following command to build the signed package:

    $ release

### Flash the build to your device

Flash the using fastboot with the command:

    $ fastboot -w update signed-occam-img-20180705.zip

