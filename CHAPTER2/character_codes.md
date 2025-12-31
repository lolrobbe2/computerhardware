# Extended ASCII & Unicode — Terminology and Clarifications

---

## Terminology Check: “Extended ASCII”
**“Extended ASCII”** is **vague and non-standard**.  
In practice, it usually refers to **8-bit encodings** that **preserve ASCII in 0–127** and use **128–255** for additional characters.

The most common families are **ISO/IEC 8859** encodings.

---

## ISO/IEC 8859 Family (Latin Encodings)

### ISO-8859-1 (Latin-1)
- Extends **7-bit ASCII (0–127)** to **8 bits (0–255)**
- **0–127** → identical to ASCII
- **160–255** → printable characters:
  - Western European letters with diacritics: `á ä ç ñ ø ß`
  - Additional punctuation and symbols
- **128–159** → **control codes** (not printable)

---

### Windows-1252
- Often **mistaken for Latin-1**
- Differs by redefining **128–159** as printable glyphs:
  - Smart quotes
  - En/em dashes
  - Later additions like the **€** symbol
- Many “Latin-1” web pages were actually **Windows-1252**
- This mismatch caused **mojibake** (文字化け)
  - *moji* = character
  - *bakeru* = to change
  - Meaning: “garbled characters”
  - Dutch term: **rommeltekst**

---

### Other Latin Encodings
- **Latin-2 (ISO-8859-2)** → Central/Eastern Europe
- **Latin-3 / Latin-4 / Latin-5** → regional variants
- **ISO-8859-15 (Latin-9)**:
  - Modifies Latin-1
  - Adds: `€ Š š Ž ž Œ œ Ÿ`
  - Removes a few rarely used symbols

---

## Unicode Overview

### What Unicode Is
**Unicode** is a **universal character repertoire** that assigns every character a **stable code point**, independent of:
- Font
- Platform
- Encoding

**Code point range**:
- `U+0000` → `U+10FFFF`

---

### Planes & Blocks
- **17 planes** total
  - **Plane 0** → Basic Multilingual Plane (BMP)
  - **Planes 1–16** → Supplementary planes
- Characters are grouped into **blocks** by script, symbol type, or function

---

### Character Properties
Each Unicode code point has **normative metadata**, including:
- General category (letter, number, symbol, control, etc.)
- Case mappings
- Numeric value
- Combining class
- Line-breaking behavior
- Bidirectional (bidi) class

These properties drive:
- Text rendering
- Searching
- Sorting
- Case-folding
- Cursor movement and layout

---

## Relationship to ASCII
- Unicode preserves ASCII perfectly:
  - **U+0000–U+007F** map **1:1** with ASCII
- **UTF-8** keeps ASCII bytes unchanged
- This guarantees backward compatibility with legacy systems

---

## Key Takeaway
- ASCII → fixed 7-bit baseline
- “Extended ASCII” → informal umbrella term
- ISO-8859 & Windows-1252 → incompatible 8-bit encodings
- Unicode → the only correct long-term solution
