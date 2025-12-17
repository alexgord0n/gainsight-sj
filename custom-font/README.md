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

Go to: **Theme → Code Snippets → Global Head Snippet**

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

}

/* Alternative Application */
* {
  font-family: 'Brown LL Sub', sans-serif;
}

</style>
```

---

## 3. Publish Your Theme
After adding the snippet:
1. Click **Save**  
2. Visit a course page to confirm fonts load correctly
3. Check inspector **under Computed**

---

## 4. Best Practices

- **Use `.woff2`** for optimal performance  
- **Place your `<style>` block at the top** of Global Head Snippet
- **Test multiple Skilljar pages**, as different page types load CSS differently  
- **Use `font-display: swap`** to avoid invisible text during loading  

---

# Additional Notes on Other Font Formats (TTF, OTF, WOFF)

While `.woff2` is the recommended format for Skilljar due to performance and compatibility, other formats do work. Below is guidance for using them.

---

## Supported Web Font Formats

### **1. WOFF2 (Recommended)**
- Best performance  
- Smallest file size  
- Ideal for Skilljar learner environments  

```css
src: url('font.woff2') format('woff2');
```

---

### **2. WOFF (Optional Fallback)**
A good fallback format, though larger than WOFF2.

```css
src: url('font.woff') format('woff');
```

---

### **3. TTF (TrueType)**
Supported but not recommended due to large file sizes.

```css
src: url('font.ttf') format('truetype');
```

---

### **4. OTF (OpenType)**
Similar to TTF—large file sizes and includes advanced typography features not typically needed in Skilljar.

```css
src: url('font.otf') format('opentype');
```

---

## Example: Multiple Font Formats

```css
@font-face {
  font-family: 'My Custom Font';
  src: 
    url('font.woff2') format('woff2'),
    url('font.woff') format('woff'),
    url('font.ttf') format('truetype'),
    url('font.otf') format('opentype');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

---
