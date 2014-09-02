For usb bluetooth, first `insmod btusb.ko`

we need `CAP_NET_RAW` to create raw inet socket, so add ourself to `net_raw` group.

**export `NET_RAW` permission**

add

    <permission android:name="android.permission.NET_RAW"
        android:permissionGroup="android.permission-group.SYSTEM_TOOLS"
        android:protectionLevel="signature" />

to `frameworks/base/core/res/AndroidManifest.xml`

**map android's `NET_RAW` permission to linux's `net_raw` group**

add

    <permission name="android.permission.NET_RAW" >
        <group gid="net_raw" />
    </permission>

to `frameworks/base/data/etc/platform.xml`

**use `NET_RAW` permission in bluetooth apk**

add

    <uses-permission android:name="android.permission.NET_RAW" />

to `packages/apps/Bluetooth/AndroidManifest.xml`

