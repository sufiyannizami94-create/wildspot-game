# 🐆 WildSpot – Find the Hidden Animal

A premium mobile-first "Find the Animal" game. Players tap where they think the camouflaged animal is hidden in stunning photorealistic scenes.

## 📁 Folder Structure

```
wildspot-game/
├── index.html          ← Main game file
├── README.md           ← This file
└── images/
    ├── level1_cheetah.png
    ├── level2_crocodile.png
    ├── level3_frog.png
    ├── level4_leopard.png
    ├── level5_octopus.png
    ├── level6_viper.png
    ├── level7_stickinsect.png
    ├── level8_arcticfox.png
    └── ... (add more levels here)
```

## ➕ How to Add New Levels

1. Add your new image to the `images/` folder, e.g. `level9_tiger.png`
2. Open `index.html` and find the `LEVELS` array
3. Add a new entry following this template:

```javascript
{
  id: 9,
  name: "Tiger",
  scene: "images/level9_tiger.png",
  desc: "Hidden in bamboo forest",
  difficulty: "Hard",   // Easy / Medium / Hard / Expert
  hx: 45,  // horizontal % position of animal center (0-100)
  hy: 50,  // vertical % position of animal center (0-100)
  radius: 12,  // tap detection radius in % (smaller = harder)
  time: 45,    // seconds allowed
  hint: "Look for orange stripes near the bamboo center",
  funFact: "Tigers are the largest wild cats in the world!"
}
```

## 🎯 Finding the hx / hy Values

Open your image in any photo viewer, hover over the animal's center, and note the X/Y pixel position. Then divide by image width/height and multiply by 100 to get the percentage.

**Example:** Animal center at pixel (640, 480) in a 1280×960 image → hx: 50, hy: 50

## 💰 AdMob Integration

Replace the placeholder ad banner in `index.html` with your real AdMob code:

```html
<!-- Replace this comment with your AdMob banner script -->
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=YOUR_CLIENT_ID"></script>
<ins class="adsbygoogle" style="display:block" data-ad-client="YOUR_CLIENT_ID" data-ad-slot="YOUR_SLOT_ID" data-ad-format="auto"></ins>
```

For interstitial ads, call `showInterstitialAd()` in the `showResult()` function.

## 📱 Publishing to Android (WebView App)

1. Create a new Android project in Android Studio
2. Use a `WebView` activity that loads `file:///android_asset/index.html`
3. Copy the entire `wildspot-game/` folder into `app/src/main/assets/`
4. Add internet permission for ads: `<uses-permission android:name="android.permission.INTERNET"/>`
5. Build APK → Sign → Upload to Google Play

## 🚀 GitHub Workflow for New Levels

```bash
git clone https://github.com/yourusername/wildspot-game
# Add new image to images/
# Edit LEVELS array in index.html
git add .
git commit -m "Add level 9: Tiger"
git push
```
