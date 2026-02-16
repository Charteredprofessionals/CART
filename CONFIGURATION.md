# 🔧 Configuration Template
## Quick Reference for API Keys and Settings

---

## 📋 API Keys Configuration

Copy this template and fill in your keys:

```javascript
// ============================================
// YOUR API KEYS - FILL THESE IN
// ============================================

const YOUR_API_KEYS = {
    // DeepSeek (Recommended - Get from: platform.deepseek.com)
    deepseek: 'sk-your-deepseek-key-here',
    
    // Google Gemini (Get from: ai.google.dev)
    gemini: 'your-gemini-key-here',
    
    // Alibaba Qwen (Get from: dashscope.aliyun.com)
    qwen: 'your-qwen-key-here',
    
    // OpenAI (Get from: platform.openai.com)
    openai: 'sk-your-openai-key-here',
    
    // Claude works automatically in claude.ai environment
    // For production, use backend proxy
};
```

---

## 🎯 Google AdSense Configuration

```javascript
// ============================================
// GOOGLE ADSENSE - FILL THESE IN
// ============================================

const ADSENSE_CONFIG = {
    // Publisher ID (Get from: google.com/adsense)
    publisherId: 'ca-pub-1234567890123456',
    
    // Ad Unit Slots (Create in AdSense dashboard)
    slots: {
        topBanner: '1234567890',      // 728x90 banner
        sidebarAd1: '2345678901',     // 300x250 rectangle
        sidebarAd2: '3456789012',     // 300x600 half page
        bottomBanner: '4567890123'    // 728x90 banner
    }
};
```

---

## 🔍 Where to Update in HTML File

### Location 1: Line ~9 (Main AdSense Script)
```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXX"
```
**Replace:** `ca-pub-XXXXXXXXXX`
**With:** Your Publisher ID

---

### Location 2: Line ~855 (DeepSeek API Key)
```javascript
deepseek: {
    headers: {
        'Authorization': 'Bearer YOUR_DEEPSEEK_API_KEY'
    }
}
```
**Replace:** `YOUR_DEEPSEEK_API_KEY`
**With:** Your DeepSeek key (e.g., `sk-abc123...`)

---

### Location 3: Line ~863 (Gemini API Key)
```javascript
gemini: {
    apiKey: 'YOUR_GEMINI_API_KEY'
}
```
**Replace:** `YOUR_GEMINI_API_KEY`
**With:** Your Gemini key

---

### Location 4: Line ~871 (Qwen API Key)
```javascript
qwen: {
    headers: {
        'Authorization': 'Bearer YOUR_QWEN_API_KEY'
    }
}
```
**Replace:** `YOUR_QWEN_API_KEY`
**With:** Your Qwen key

---

### Location 5: Line ~879 (OpenAI API Key)
```javascript
gpt4: {
    headers: {
        'Authorization': 'Bearer YOUR_OPENAI_API_KEY'
    }
}
```
**Replace:** `YOUR_OPENAI_API_KEY`
**With:** Your OpenAI key (e.g., `sk-xyz789...`)

---

### Location 6: Line ~420 (Top Banner Ad)
```html
<ins class="adsbygoogle"
     data-ad-client="ca-pub-XXXXXXXXXX"
     data-ad-slot="YYYYYYYYYY"></ins>
```
**Replace:** 
- `ca-pub-XXXXXXXXXX` → Your Publisher ID
- `YYYYYYYYYY` → Your ad slot ID

---

### Location 7: Line ~450 (Sidebar Ad 1)
```html
<ins class="adsbygoogle"
     data-ad-client="ca-pub-XXXXXXXXXX"
     data-ad-slot="ZZZZZZZZZZ"></ins>
```
**Replace:** 
- `ca-pub-XXXXXXXXXX` → Your Publisher ID
- `ZZZZZZZZZZ` → Your ad slot ID

---

### Location 8: Line ~465 (Sidebar Ad 2)
```html
<ins class="adsbygoogle"
     data-ad-client="ca-pub-XXXXXXXXXX"
     data-ad-slot="AAAAAAAAAA"></ins>
```
**Replace:** 
- `ca-pub-XXXXXXXXXX` → Your Publisher ID
- `AAAAAAAAAA` → Your ad slot ID

---

### Location 9: Line ~485 (Bottom Banner Ad)
```html
<ins class="adsbygoogle"
     data-ad-client="ca-pub-XXXXXXXXXX"
     data-ad-slot="BBBBBBBBBB"></ins>
```
**Replace:** 
- `ca-pub-XXXXXXXXXX` → Your Publisher ID
- `BBBBBBBBBB` → Your ad slot ID

---

## 🎛️ Optional Customizations

### Change Default AI Model
Line ~390 in `<select>` element:

```html
<!-- Current default: DeepSeek -->
<option value="deepseek" selected>DeepSeek-V3 (Best Value) 💰</option>

<!-- To change default to Claude: -->
<option value="claude" selected>Claude Sonnet 4 (Best Quality)</option>
```

### Change Color Scheme
Line ~21 (Background gradient):

```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Alternative: Blue gradient */
background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);

/* Alternative: Green gradient */
background: linear-gradient(135deg, #56ab2f 0%, #a8e063 100%);
```

### Adjust PDF Margins
Line ~230 (`@media print` section):

```css
@page {
    margin: 20mm;  /* Change to 15mm, 25mm, etc. */
}
```

---

## ✅ Verification Checklist

After configuration, test these:

**AI Models:**
- [ ] DeepSeek responds correctly
- [ ] Gemini responds correctly
- [ ] Error handling works (try with wrong key)
- [ ] Model switching works smoothly

**AdSense:**
- [ ] Ads display on desktop
- [ ] Ads display on mobile (320x100)
- [ ] No console errors
- [ ] Ad labels ("Advertisement") visible

**PDF Export:**
- [ ] Print button works
- [ ] Save PDF button works
- [ ] Header/footer appear in PDF
- [ ] Ads hidden in PDF

**General:**
- [ ] Mobile responsive
- [ ] Quick query buttons work
- [ ] Clear conversation works
- [ ] Legal disclaimer visible

---

## 🚨 Security Reminder

### For Development/Testing:
✅ API keys in frontend (current setup)

### For Production:
❌ **Never expose API keys in frontend!**

**Use backend proxy:**
```javascript
// Frontend (ca2013-assistant.html)
const response = await fetch('/api/chat', {
    method: 'POST',
    body: JSON.stringify({ message: query, model: selectedModel })
});

// Backend (e.g., Node.js server.js)
app.post('/api/chat', async (req, res) => {
    const apiKey = process.env.DEEPSEEK_API_KEY; // Secure!
    // Forward to LLM provider...
});
```

---

## 📊 Cost Tracking

Set up cost alerts:

**DeepSeek:**
- Login to platform.deepseek.com
- Go to Billing → Set alerts
- Recommended: Alert at $10, $50, $100

**Gemini:**
- Login to console.cloud.google.com
- Billing → Budget alerts
- Recommended: Alert at $5, $20, $50

**Monitor weekly** in first month to understand usage patterns.

---

## 🎯 Performance Optimization

### If experiencing slow responses:

1. **Switch to faster model:**
   - Gemini 2.0 Flash (fastest)
   - DeepSeek-Turbo (fast + cheap)

2. **Reduce max_tokens:**
   - Current: 2000 tokens
   - Try: 1500 tokens
   - Edit at line ~905

3. **Enable caching:**
   - Store frequent queries
   - Add to localStorage
   - Serve from cache first

### If ads not loading:

1. **Check AdSense approval status**
2. **Wait 24-48 hours after approval**
3. **Clear browser cache**
4. **Try incognito mode**
5. **Check browser console for errors**

---

## 📞 Support Resources

**API Issues:**
- DeepSeek: [platform.deepseek.com/docs](https://platform.deepseek.com/docs)
- Gemini: [ai.google.dev/docs](https://ai.google.dev/docs)
- OpenAI: [platform.openai.com/docs](https://platform.openai.com/docs)

**AdSense Issues:**
- Help: [support.google.com/adsense](https://support.google.com/adsense)
- Forum: AdSense Community

**General Questions:**
- Check: `final-build-docs.md`
- Or: `llm-provider-guide.md`

---

## 🎉 You're All Set!

After filling in the configuration:
1. Save the HTML file
2. Open in browser to test
3. Try a few queries
4. Verify PDF export
5. Check ads display
6. Deploy to hosting

**Happy Building!** 🚀
