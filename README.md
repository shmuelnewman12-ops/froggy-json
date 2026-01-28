# YouTube Channel Verifier - Persistent Edition

A beautiful, fully client-side web app for reviewing YouTube channels with **persistent progress tracking**. Each session picks up exactly where you left off.

## 🎯 How It Works

### The Smart Way
1. **Upload your JSON once** - The app stores it in browser memory
2. **Review at your own pace** - Work on 10 channels, 100 channels, or just 5 at a time
3. **Close and come back** - Every decision is saved immediately
4. **Pick up where you left off** - Next session starts at the next unreviewed channel
5. **Download your updated JSON** - Get your original data with added `verification_decision` field

### What Gets Saved

Your original JSON gets enhanced with two new fields:

```json
[
  {
    "artist": "Taylor Swift",
    "channel_title": "Taylor Swift",
    "subscribers": "@TaylorSwift",
    "url": "https://youtube.com/@TaylorSwift",
    "verification_decision": "good",           // ← Added by you
    "verification_timestamp": "2026-01-27T..." // ← Auto-added
  }
]
```

**Possible decisions:**
- `"good"` - Good match ✅
- `"bad"` - Not a match ❌
- `"review_later"` - Need to review again 🤔
- `"pending"` - Not reviewed yet (default)

## ✨ Features

### Core Features
- 🎨 **YouTube-inspired UI** - Professional dark theme
- 🖼️ **Channel thumbnails** - Visual confirmation with fallbacks
- 💾 **Auto-save everything** - Every decision saves immediately
- 🔄 **Resume sessions** - Always picks up where you left off
- ⌨️ **Keyboard shortcuts** - 1=Good, 2=Bad, 3=Review, 4=Skip
- 📊 **Real-time stats** - See progress at a glance
- 📥 **Export options** - JSON or CSV download

### Smart Progress Tracking
- **Live progress bar** - Visual indicator of completion
- **Smart navigation** - Automatically finds next unreviewed channel
- **Comprehensive stats**:
  - ✓ Good matches
  - ✗ Bad matches  
  - ? Review later
  - ⏳ Pending (not yet reviewed)

### Data Persistence
- All data stored in browser localStorage
- Survives browser restarts
- No server needed
- 100% private - data never leaves your browser

## 🚀 Deployment

### Netlify Drop (30 seconds)
1. Go to [drop.netlify.com](https://drop.netlify.com)
2. Drag `yt-verifier-final.html` onto the page
3. Get instant live URL
4. Done!

### GitHub Pages
1. Create a repo
2. Upload `yt-verifier-final.html` as `index.html`
3. Enable Pages in Settings
4. Access at `https://yourusername.github.io/repo-name`

### Vercel
```bash
npm i -g vercel
vercel
# Follow prompts
```

## 📋 Usage Guide

### Starting Fresh
1. Open the app
2. Upload your JSON file (drag & drop or click)
3. Start reviewing!

### Continuing Work
1. Open the app
2. Automatically loads your previous session
3. Shows next unreviewed channel
4. Keep going!

### Exporting Results
When done (or anytime):
1. Click **"Download Updated JSON"**
   - Gets your original data + all decisions
   - Ready to import into other tools
2. Or click **"Download as CSV"**
   - Open in Excel/Sheets
   - Easy filtering and analysis

### JSON Format

**Input (your original file):**
```json
[
  {
    "artist": "Artist Name",
    "channel_title": "Channel Title",
    "subscribers": "@handle",
    "url": "https://youtube.com/@handle"
  }
]
```

**Output (after reviewing):**
```json
[
  {
    "artist": "Artist Name",
    "channel_title": "Channel Title",
    "subscribers": "@handle",
    "url": "https://youtube.com/@handle",
    "verification_decision": "good",
    "verification_timestamp": "2026-01-27T15:30:45.123Z"
  }
]
```

## 🎮 Keyboard Shortcuts

- **1** → Mark as Good Match ✅
- **2** → Mark as Bad Match ❌
- **3** → Review Later 🤔
- **4** → Skip (no decision)

## 📊 Progress Tracking

### Top Bar
- **Progress bar** - Visual % complete
- **Current count** - "45 / 100"
- **Live stats** - ✓ Good, ✗ Bad, ? Review

### Stats Panel
Shows real-time breakdown:
- **Good** - Confirmed matches
- **Bad** - Rejected channels
- **Review** - Flagged for later
- **Pending** - Not yet reviewed

## 🔧 Advanced Features

### Resume Anywhere
The app is smart about finding work:
1. First, checks from your last position forward
2. If all reviewed ahead, loops back to beginning
3. Finds first unreviewed channel
4. Shows completion screen when all done

### Data Management

**To reset and start over:**
```javascript
// In browser console:
localStorage.clear();
location.reload();
```

**Or** just click "Load New File" button

### Export Formats

**JSON (recommended):**
- Complete data with timestamps
- Re-importable
- Machine-readable

**CSV:**
- Excel/Sheets compatible
- Easy filtering
- Human-readable

## 📱 Mobile / APK Wrapper

### Option 1: PWA (Recommended)
- Add to home screen directly from browser
- Works offline
- No APK needed
- Native app feel

### Option 2: WebView Wrapper
Use your Netlify/Vercel URL with:
- **Android Studio** - Full control
- **AppsGeyser** - Free, easy
- **Webintoapp** - Quick builds

## 🔐 Privacy & Data

- **100% client-side** - No server, no tracking
- **localStorage only** - Data stays in browser
- **No cookies** - Clean and private
- **No analytics** - Just you and your data

## 🐛 Troubleshooting

**Q: My progress disappeared**
- Check if localStorage was cleared
- Use same browser (Chrome, Firefox, etc.)
- Download JSON regularly as backup

**Q: Can I use on multiple devices?**
- Download JSON from device 1
- Upload to device 2
- Continue seamlessly!

**Q: What if I accidentally mark wrong?**
- Just hit the same channel again when it loops
- Or download JSON and edit manually
- Then re-upload

**Q: Thumbnails not loading?**
- YouTube blocks most thumbnail embedding
- App uses smart fallbacks (generated avatars)
- Click "Open on YouTube" to see real channel

## 🎯 Workflow Example

**Day 1:**
- Upload 500 channels
- Review 100 (✓50, ✗30, ?20)
- Close browser

**Day 2:**
- Open app
- Starts at channel #101
- Review 150 more
- Close browser

**Day 3:**
- Finish remaining 250
- Download updated JSON
- Import into your database/spreadsheet

## 💡 Pro Tips

1. **Work in batches** - Do 20-50 at a time to stay focused
2. **Use keyboard** - Way faster than clicking
3. **Download often** - Regular backups = peace of mind
4. **Review flag** - Use for uncertain ones, revisit later
5. **Stats guide you** - Watch the pending count drop!

## 📄 Technical Details

- **Framework:** Vanilla JavaScript (no dependencies)
- **Storage:** Browser localStorage API
- **Styling:** Custom CSS with YouTube theme
- **Fonts:** Syne + JetBrains Mono (Google Fonts)
- **Size:** ~50KB single file
- **Browser:** Any modern browser (Chrome, Firefox, Safari, Edge)

## 🎨 Customization

All colors are CSS variables - easy to customize:

```css
:root {
    --yt-red: #FF0000;      /* Primary accent */
    --yt-dark: #0F0F0F;     /* Main background */
    --success: #00D856;     /* Good decisions */
    --danger: #FF4444;      /* Bad decisions */
    --warning: #FFA500;     /* Review later */
}
```

## 📜 License

MIT - Use however you want!

---

**Built for efficient, persistent YouTube channel verification** 🎬
