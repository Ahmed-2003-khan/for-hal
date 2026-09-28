# A Letter For You 💌

Ek single-file love letter webpage — **English / اردو / العربية**, mobile-first,
envelope opening animation aur floating rose petals ke saath.

Koi build step nahi. Koi dependency nahi. Bas `index.html`.

---

## 1. Apne mutabiq edit karein

Sab kuch `index.html` ke **niche wale `<script>`** mein hai.

### Naam badalna
Line ~`const CONFIG = {` dhoondein:

```js
const CONFIG = {
  to:   { en: "my love",       ur: "میری جان",   ar: "يا سَكَنَ قلبي" },
  from: { en: "Yours, always", ur: "تمہارا، ہمیشہ", ar: "لكِ دائمًا" },
  date: { en: "Written for you", ur: "تمہارے نام", ar: "كُتِبت لكِ" }
};
```

- `to`   → greeting mein aayega (`Assalamu Alaikum, {to} —`)
- `from` → letter ke akhir mein signature
- `date` → greeting ke upar chhoti si line

### Letter ka matan badalna
`const CONTENT = {` ke andar har zabaan ka block hai:

| key | kya hai |
|---|---|
| `tapHint` | envelope ke niche "Tap to open" |
| `greeting` | salaam wali line (`{to}` token support karta hai) |
| `before[]` | Quran ki aayat se **pehle** ke paragraphs |
| `verseTr` / `verseRef` | aayat ka tarjuma aur hawala |
| `after[]` | aayat ke **baad** ke paragraphs |
| `promiseIntro` + `promises[]` | wadon ki list |
| `closing` / `ps` | ikhtitami line aur P.S. |
| `loveBtn` / `reseal` / `credit` | buttons aur footer |

Aayat ka Arabic matan HTML mein hai — `class="verse__ar"` dhoond lein.

### Default zabaan badalna
Script mein `const DEFAULT_LANG = "ur";` — ise `"en"` ya `"ar"` kar dein.
(Parhne wala khud koi zabaan chunay to wohi yaad rakhi jati hai.)

### Rang badalna
`:root { ... }` ke andar CSS variables:
`--rose`, `--rose-deep`, `--gold`, `--paper`, `--ink` waghera.

---

## 2. GitHub par publish karein

```bash
git init
git add .
git commit -m "A letter"
git branch -M main
git remote add origin https://github.com/<USERNAME>/<REPO>.git
git push -u origin main
```

Phir GitHub par:

**Settings → Pages → Build and deployment**
- Source: `Deploy from a branch`
- Branch: `main` / `(root)` → **Save**

1–2 minute baad link live ho jaye ga:

```
https://<USERNAME>.github.io/<REPO>/
```

> **Tip:** agar repo ka naam `<USERNAME>.github.io` rakh dein to URL sirf
> `https://<USERNAME>.github.io/` ho jaye ga — bhejne mein ziada khoobsurat lagta hai.

---

## 3. Features

- **3 zabaanein** — English, Urdu (Nastaliq), Arabic (Amiri). Default **Urdu** hai;
  parhne wale ki apni choice `localStorage` mein save ho jati hai.
- **Poora RTL support** — `dir` attribute switch hota hai, alignment aur bullets
  dono mirror ho jate hain.
- **Envelope animation** — sealed envelope, wax seal, flap khulta hai, khat upar
  uthta hai. "Close the letter" se dobara seal ho jata hai.
- **Petals + hearts** — halka canvas engine, tab background mein jaye to khud ruk
  jata hai (battery bachane ke liye).
- **Mobile-first** — `svh` units, safe-area insets (iPhone notch), 46px+ tap
  targets, koi horizontal scroll nahi.
- **Accessible** — keyboard se chalta hai, `prefers-reduced-motion` ka ehtaram
  karta hai, screen-reader labels mojood hain.

---

## 4. Local par dekhna

Sirf `index.html` par double-click kar dein. Ya:

```bash
python -m http.server 8000
# phir kholein http://localhost:8000
```
