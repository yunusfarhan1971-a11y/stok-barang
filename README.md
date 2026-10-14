# Aplikasi Stok Barang (Android)

Proyek ini membungkus website Stok Barang menjadi aplikasi Android (APK) memakai Capacitor.
Isi aplikasi ada di `www/index.html`.

## Cara 1 - Tanpa install apa pun (disarankan): bangun APK lewat GitHub

1. Buat akun gratis di https://github.com lalu buat repositori baru (misalnya `stok-barang`).
2. Unggah SEMUA isi folder ini ke repositori itu, termasuk folder `.github`.
   (Di halaman repositori: Add file -> Upload files. Pastikan folder tersembunyi `.github` ikut terunggah.
   Jika tidak ikut, buat manual file `.github/workflows/build-apk.yml` lalu salin isinya.)
3. Buka tab **Actions**. Pilih **Build APK** -> **Run workflow**.
4. Tunggu sekitar 5-10 menit sampai ada tanda centang hijau.
5. Buka hasil build tersebut, lalu unduh **stok-barang-apk** di bagian Artifacts. Di dalamnya ada `app-debug.apk`.
6. Kirim file APK ke HP, buka, lalu izinkan "Instal dari sumber tidak dikenal" jika diminta.

## Cara 2 - Bangun sendiri di komputer

Syarat: Node.js 20, Java JDK 17, dan Android Studio (untuk Android SDK).

    npm install
    npx cap add android
    npx cap sync android
    cd android
    ./gradlew assembleDebug        (Windows: gradlew.bat assembleDebug)

APK ada di `android/app/build/outputs/apk/debug/app-debug.apk`.

## Mengubah nama atau ikon

- Nama aplikasi: ubah `appName` di `capacitor.config.json`.
- ID aplikasi: ubah `appId` (huruf kecil, contoh `com.tokoanda.stok`).
- Ikon: setelah `npx cap add android`, ganti gambar di `android/app/src/main/res/mipmap-*`,
  atau pakai alat `@capacitor/assets`.

## Catatan

- APK "debug" ini cukup untuk dipasang dan dipakai sendiri atau dibagikan langsung.
  Untuk Google Play Store perlu APK/AAB bertanda tangan (release) dan akun developer.
- Data disimpan di dalam aplikasi di HP. Data dari link claude.ai TIDAK ikut pindah.
- Menghapus data aplikasi atau mencopot pemasangan akan menghapus data stok.
