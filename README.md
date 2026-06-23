Hello everyone! My name is Fahad Shaikh. I built this functional Spotify clone to hone my frontend engineering skills.
If you would like to contribute assets, add new audio tracks, or optimize current layout styles, please reach out or open a pull request/issue on GitHub for permission first!

# Spotify UI Clone 🎵
Spotify Clone made by only using HTML, CSS, JS. Spotify is a music streaming platform, where you can listen to your songs anywhere anytime you want! Enjoy

A responsive frontend web application that recreates the core user interface of Spotify, built to sharpen frontend layout design, asset management, and cross-page JavaScript architecture.

![Spotify Clone Main Dashboard](screenshot.png)

---

## 🚀 Features

- **Dynamic Audio Player:** Full playback controls including play, pause, next, previous, and an interactive song progress bar (`index.html`).
- **Sidebar Navigation:** A clean, fully responsive left navigation sidebar linking the Home, About Us, and Library panels consistently.
- **Interactive Showcases:** Built-in interactive features like a responsive profile view and a functional custom frontend rating pop-up window (`About.html`).
- **Resilient Script Architecture:** Optimized background scripts equipped with conditional check blocks to prevent page-freezing errors across multiple views.

---

## 🛠️ Tech Stack

- **Frontend:** HTML5, CSS3, JavaScript (ES6+)
- **Icons & Graphics:** SVG Assets, Ionicons CDN
- **Typography:** Circular Sp Font Family (Spotify Premium Native Vibe)

---
 


## 🧩 Architectural Highlight: Cross-Page Error Prevention

When scaling this music player from a single-page layout to a multi-page site, loading the main audio control script (`script.js`) on the profile page (`About.html`) initially caused a critical execution freeze. The browser would fail to locate DOM elements like `masterPlay` (which only exists on the homepage player dashboard) and throw a fatal `TypeError`.

To resolve this and keep the frontend decoupled and error-free, a conditional execution safety wrapper was implemented:
```javascript
// Safe execution block preventing script crashes on non-player views
if (masterPlay) {
    songItems.forEach((element, i) => {
        element.getElementsByTagName("img")[0].src = songs[i].coverPath;
        element.getElementsByClassName("songName")[0].innerText = songs[i].songName;
    });
    
    // All player-dependent event listeners (play, pause, next) are isolated here

}