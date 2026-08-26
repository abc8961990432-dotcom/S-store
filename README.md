# S Store — Android App (Flutter)

एक secure digital storage app जिसमें फाइलें (photo, video, PDF, document, audio) पूरी तरह
**offline** save और देखी/चलाई जा सकती हैं, और internet मिलते ही अपने आप Firebase पर backup हो जाती हैं।

## Features
- Google, Facebook और Email/Password से Login
- Photo/Video/PDF/Document/Audio — कोई भी file बिना internet upload और view
- Folders: Personal, Work, Study
- Rename, Delete, Search
- Dark Mode
- नए फोन में login करके पुरानी files वापस पाना (Firebase Cloud Backup)

## Setup करने के स्टेप्स

1. **Flutter install करें**: https://docs.flutter.dev/get-started/install
2. यह प्रोजेक्ट फोल्डर अपने कंप्यूटर पर खोलें, फिर:
   ```
   flutter pub get
   ```
3. **Firebase प्रोजेक्ट बनाएं**: https://console.firebase.google.com
   - Android app add करें (package name अपनी पसंद का रखें, जैसे `com.yourname.sstore`)
   - `google-services.json` डाउनलोड करके `android/app/` फोल्डर में डालें
   - Firebase Console में: Authentication → Sign-in method → Google, Facebook, Email/Password सब **Enable** करें
   - Firebase Storage और Firestore भी enable करें
4. **Facebook Login के लिए**: https://developers.facebook.com पर App बनाकर App ID `android/app/src/main/res/values/strings.xml` में डालें (Facebook SDK docs अनुसार)
5. Run करें:
   ```
   flutter run
   ```
6. Play Store पर publish करने के लिए:
   ```
   flutter build appbundle
   ```
   बना हुआ `.aab` फाइल Google Play Console में अपलोड करें।

## Project Structure
```
lib/
  main.dart                  - App entry, theme, providers
  services/
    auth_service.dart        - Google/Facebook/Email login
    storage_service.dart     - Offline-first file save + cloud backup
    theme_service.dart       - Dark mode
  models/
    file_item.dart           - File data model
  screens/
    login_screen.dart
    home_screen.dart         - Folders, grid, upload, search
    file_viewer_screen.dart  - Offline photo/video/document viewer
```

## ज़रूरी नोट
यह production-ready base code है, पर चलाने के लिए ऊपर बताए Firebase setup स्टेप्स पूरे करने ज़रूरी हैं
(`google-services.json` डाले बिना app build नहीं होगा)।
