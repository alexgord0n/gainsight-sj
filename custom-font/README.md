# Adding Custom Web Fonts (Brown LL Sub) to Skilljar

This guide explains how to upload custom font files to Skilljar and apply them globally using a custom `<style>` snippet. Using Skilljar’s built‑in file uploader ensures fonts are hosted on Skilljar’s S3 and load reliably across all course pages.

---

## 1. Upload Your Font Files to Skilljar

Skilljar doesn’t allow file uploads directly in the theme editor, but any **Rich Text Editor (RTE)** in the dashboard can upload files.

### Steps
1. Open **any page with a Rich Text field** such as:
   - Course → Edit → Description  
   - Lesson text fields  
2. Click **Insert Link → Next to Link URL → Upload**  
3. Select your `.woff2` font file  
4. Skilljar will upload it to S3 and generate a **public URL**  
5. Copy that URL for use in your CSS

Repeat this for each font style:
- Light (300)  
- Regular (400)  
- Bold (700)  
- Italic (400 italic)

---

## 2. Add Fonts to the Global Snippet

Go to: **Theme → Advanced → Global Snippets**

Paste the following `<style>` block, replacing the placeholder URLs with your real S3 links.

```html
<style>
/* ===========================
   Brown LL Sub — Custom Fonts
   =========================== */

/* Brown LL Sub Regular */
@font-face {
  font-family: 'Brown LL Sub';
  src: url('YOUR-S3-REGULAR.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}

/* Brown LL Sub Light */
@font-face {
  font-family: 'Brown LL Sub';
  src: url('YOUR-S3-LIGHT.woff2') format('woff2');
  font-weight: 300;
  font-style: normal;
  font-display: swap;
}

/* Brown LL Sub Bold */
@font-face {
  font-family: 'Brown LL Sub';
  src: url('YOUR-S3-BOLD.woff2') format('woff2');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}

/* Brown LL Sub Italic */
@font-face {
  font-family: 'Brown LL Sub';
  src: url('YOUR-S3-ITALIC.woff2') format('woff2');
  font-weight: 400;
  font-style: italic;
  font-display: swap;
}

/* Apply the font globally */
h1, h2, h3, h4, h5, h6,
div, p, span, button, a,
input, select, option, textarea {
  font-family: 'Brown LL Sub', sans-serif;
}
</style>
```

---

## 3. Publish Your Theme
After adding the snippet:
1. Click **Save**  
2. Click **Publish Theme**  
3. Visit a course page to confirm fonts load correctly  

---

## 4. Best Practices

- **Use `.woff2`** for optimal performance  
- **Place your `<style>` block at the top** of Global Snippets  
- **Test multiple Skilljar pages**, as different page types load CSS differently  
- **Use `font-display: swap`** to avoid invisible text during loading  

---

## 5. Need Help?

This README can be extended with:
- A screenshot version  
- A detailed theme‑editor walkthrough  
- A glossary of common Skilljar customization patterns  

Just ask if you'd like additional sections.
