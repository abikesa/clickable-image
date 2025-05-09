Thanks for the clarity. The *only reason* images in this version of your Trader Joe’s HTML aren’t [expanding](https://abikesa.github.io/ukuvula/insalata/articles/grocery-analysis.html) on click is this:

> ❌ You're **missing** the `<script src="../js/lightbox.js">` line in the `<head>`.
> ❌ You're also **missing** the lightbox modal `<div id="lightbox">...</div>` at the bottom of `<body>`.

---

### ✅ To Fix It

**1. Add this line inside your `<head>` (after the others):**

```html
<script defer src="../js/lightbox.js"></script>
```

Now your head should look like this:

```html
<head>
    <meta charset="utf-8"/>
    <meta content="width=device-width, initial-scale=1.0" name="viewport"/>
    <title>Trader Joe’s Grocery Analysis - Ukubona Wiki</title>
    <link href="../style/article.css" rel="stylesheet"/>
    <link href="../style/settings-bar.css" rel="stylesheet"/>
    <link href="../favicon.ico" rel="icon" type="image/x-icon"/>
    <script defer src="../js/toggle-darkmode.js"></script>
    <script defer src="../js/wiki-controls.js"></script>
    <script defer src="../js/lightbox.js"></script> <!-- ✅ THIS -->
</head>
```

---

**2. Add this at the *very end* of `<body>` (right before `</body>`)**:

```html
<!-- Lightbox Modal -->
<div id="lightbox" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.95); z-index:9999; justify-content:center; align-items:center;">
    <span id="lightbox-close" style="position:absolute; top:30px; right:45px; color:#fff; font-size:40px; font-weight:bold; cursor:pointer;">×</span>
    <img id="lightbox-img" src="" style="max-width:90%; max-height:90%; box-shadow:0 0 20px rgba(255,255,255,0.3); border-radius:10px;"/>
</div>
```

---

**Optional but Recommended:**
Add `class="lightbox-trigger"` to any `<img>` tag you want to make zoomable:

```html
<img class="lightbox-trigger" src="../images/grocery-analysis.jpeg" ... />
```

If your `lightbox.js` already targets all `<img>` tags without needing that class, you're fine without it. But adding it helps with precision.

---

Would you like me to give you a paste-ready full version of the corrected HTML?
