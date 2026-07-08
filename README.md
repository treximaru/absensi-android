# 📱 Absensi Android

Aplikasi Android WebView untuk **Absensi Mapel Harian**. Akses langsung ke `https://absen.berkahsablon.com/` dari HP Android.

> **🌐 Web App:** [Absensi Mapel Harian](https://github.com/treximaru/absensi-mapel-harian) — source code PHP backend

---

## ✨ Fitur

- **WebView** loading `absen.berkahsablon.com`
- **Progress bar** saat loading halaman
- **Back button** navigasi di dalam WebView
- **File upload** support (input file)
- **External links** otomatis buka di browser
- **JavaScript & DOM Storage** aktif
- **Fullscreen mode** (tanpa status bar)
- **Auto-print** untuk fitur Print/PDF

---

## 📋 Spesifikasi

| Item | Detail |
|------|--------|
| Package | `com.berkahsablon.absensi` |
| Min SDK | Android 7.0 (API 24) |
| Target SDK | Android 14 (API 34) |
| URL | `https://absen.berkahsablon.com/` |
| Size | ~2.7 MB |

---

## 📥 Download

### Latest Release

Download APK terbaru dari [Releases](https://github.com/treximaru/absensi-android/releases)

### Install

1. Download file `.apk`
2. Buka file di Android
3. Izinkan install dari sumber tidak dikenal (jika diminta)
4. Install

---

## 🛠️ Build dari Source

### Requirements

- Java 17
- Android SDK (build-tools 34.0.0, platform android-34)
- Gradle 8.2

### Build

```bash
git clone https://github.com/treximaru/absensi-android.git
cd absensi-android
chmod +x gradlew
./gradlew assembleDebug
```

APK akan ada di: `app/build/outputs/apk/debug/app-debug.apk`

### Sign APK

```bash
# Generate keystore
keytool -genkeypair -v \
  -keystore release.jks \
  -alias absensi -keyalg RSA -keysize 2048 -validity 10000 \
  -storepass <password> -keypass <password> \
  -dname 'CN=Berkah Sablon, OU=IT, O=Berkah Sablon, L=Banjarnegara, ST=Jawa Tengah, C=ID'

# Sign
jarsigner -keystore release.jks -storepass <password> \
  app/build/outputs/apk/debug/app-debug.apk absensi
```

---

## 📁 Struktur Project

```
absensi-android/
├── app/
│   ├── build.gradle              # App dependencies
│   └── src/main/
│       ├── AndroidManifest.xml   # Manifest (permission, activity)
│       ├── java/com/berkahsablon/absensi/
│       │   └── MainActivity.java # WebView activity
│       └── res/
│           ├── layout/           # Layout XML
│           ├── values/           # Strings, colors, themes
│           └── mipmap-*/         # App icons
├── build.gradle                  # Root build config
├── settings.gradle
├── gradle/wrapper/
└── gradlew
```

---

## 🔧 Konfigurasi

### Ganti URL

Edit `MainActivity.java`:

```java
private static final String BASE_URL = "https://absen.berkahsablon.com/";
```

### Ganti Icon

Ganti file PNG di `app/src/main/res/mipmap-*/ic_launcher.png`:

| Density | Ukuran |
|---------|--------|
| mdpi | 48×48 px |
| hdpi | 72×72 px |
| xhdpi | 96×96 px |
| xxhdpi | 144×144 px |

### Ganti Warna Theme

Edit `app/src/main/res/values/themes.xml`:

```xml
<item name="android:statusBarColor">@color/primary_dark</item>
```

---

## 🔗 Link Terkait

| Repository | Keterangan |
|------------|-----------|
| [absensi-mapel-harian](https://github.com/treximaru/absensi-mapel-harian) | Web app (PHP + MariaDB) |
| **absensi-android** | Android WebView app (repo ini) |

---

## 📄 Lisensi

MIT License
