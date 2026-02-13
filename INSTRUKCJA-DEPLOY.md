# 🚀 INSTRUKCJA DEPLOY NA BERECKI.COM

## 📦 Co masz gotowe:

✅ `index.html` - Wersja polska (główna)
✅ `index-en.html` - Wersja angielska  
✅ Pełne SEO (meta tags, Schema.org, Open Graph)
✅ Responsive design
✅ Fraktalne tło z symboliką
✅ Formularz kontaktowy

---

## 🎯 METODA 1: NETLIFY + GITHUB (ZALECANA)

### **KROK 1: Przygotuj pliki w VS Code**

1. **Stwórz folder projektu:**
   ```
   C:\Users\TwojeImie\Documents\berecki-website
   ```

2. **Dodaj pliki:**
   - `index.html` (wersja polska z SEO)
   - `index-en.html` (wersja angielska)
   - `robots.txt` (skopiuj z SEO-FILES-NEEDED.md)
   - `sitemap.xml` (skopiuj z SEO-FILES-NEEDED.md)
   - `_redirects` (dla Netlify routing)

3. **Stwórz plik `_redirects`:**
   ```
   /en /index-en.html 200
   /* /index.html 200
   ```

### **KROK 2: Git + GitHub**

1. **Otwórz Terminal w VS Code** (Ctrl + `)

2. **Inicjalizuj Git:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit - Berecki.com website"
   git branch -M main
   ```

3. **Publish to GitHub:**
   - Kliknij ikonę "Source Control" (lewy panel)
   - Kliknij "Publish to GitHub"
   - Wybierz "Public repository"
   - Nazwa: `berecki-website`

### **KROK 3: Netlify Deploy**

1. **Wejdź na https://app.netlify.com**

2. **Zaloguj się przez GitHub**

3. **"Add new site" → "Import an existing project"**

4. **"Deploy with GitHub"**

5. **Wybierz repo:** `berecki-website`

6. **Build settings:**
   - Build command: *zostaw puste*
   - Publish directory: *zostaw puste* (bo masz HTML w root)
   - Kliknij **"Deploy site"**

7. **Poczekaj 1-2 minuty** ✅ Strona jest live!

### **KROK 4: Podłącz domenę berecki.com**

1. **W Netlify kliknij "Domain settings"**

2. **"Add custom domain"** → wpisz: `berecki.com`

3. **Netlify pokaże Ci DNS settings:**

   ```
   Type: A
   Name: @
   Value: 75.2.60.5

   Type: CNAME
   Name: www
   Value: [twoja-nazwa].netlify.app
   ```

4. **Wejdź do panelu swojej domeny** (nazwa.pl, home.pl, OVH)

5. **Zarządzanie DNS → Dodaj rekordy:**
   - Rekord A: `@` → `75.2.60.5`
   - Rekord CNAME: `www` → `[twoja-nazwa].netlify.app`

6. **Usuń stare rekordy A/CNAME** jeśli istnieją

7. **Zapisz zmiany**

8. **Poczekaj 1-24h na propagację DNS**

9. **Netlify automatycznie doda HTTPS** (certyfikat SSL)

---

## 🔄 JAK AKTUALIZOWAĆ STRONĘ W PRZYSZŁOŚCI

### **Sposób 1: Przez VS Code (najszybszy)**

1. Edytuj `index.html` w VS Code
2. Zapisz (Ctrl + S)
3. Terminal:
   ```bash
   git add .
   git commit -m "Opis zmiany, np: Zmiana CTA button"
   git push
   ```
4. **Netlify automatycznie zaktualizuje** stronę (1-2 min)

### **Sposób 2: Przez GitHub (w przeglądarce)**

1. Wejdź na GitHub → Twoje repo
2. Kliknij plik `index.html`
3. Kliknij ikonę ołówka (Edit)
4. Wprowadź zmiany
5. "Commit changes"
6. Netlify automatycznie wdroży zmiany

---

## ✅ CHECKLIST PRZED URUCHOMIENIEM

- [ ] Wszystkie pliki w folderze projektu
- [ ] Git zainicjalizowany (`git init`)
- [ ] Repo na GitHub utworzone
- [ ] Netlify połączony z GitHub
- [ ] Site wdrożony na Netlify
- [ ] Domena kupiona (berecki.com)
- [ ] DNS skonfigurowany (A record + CNAME)
- [ ] Poczekałeś 24h na propagację DNS
- [ ] HTTPS działa (Netlify auto-konfiguracja)
- [ ] Obie wersje działają:
  - [ ] https://berecki.com (PL)
  - [ ] https://berecki.com/en (EN)

---

## 🛠️ DODATKOWE SEO (OPCJONALNE)

### **1. Google Search Console**

1. Wejdź na https://search.google.com/search-console
2. Dodaj property: `berecki.com`
3. Zweryfikuj przez DNS (dodaj rekord TXT)
4. Prześlij sitemap: `https://berecki.com/sitemap.xml`

### **2. Google Analytics**

1. Utwórz konto: https://analytics.google.com
2. Dodaj property dla berecki.com
3. Skopiuj kod tracking (G-XXXXXXXXXX)
4. Dodaj przed `</head>` w obu plikach HTML:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### **3. Meta Pixel (Facebook)**

Jeśli będziesz robić reklamy na FB:
```html
<!-- Meta Pixel Code -->
<script>
!function(f,b,e,v,n,t,s)
{if(f.fbq)return;n=f.fbq=function(){n.callMethod?
n.callMethod.apply(n,arguments):n.queue.push(arguments)};
if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
n.queue=[];t=b.createElement(e);t.async=!0;
t.src=v;s=b.getElementsByTagName(e)[0];
s.parentNode.insertBefore(t,s)}(window, document,'script',
'https://connect.facebook.net/en_US/fbevents.js');
fbq('init', 'YOUR_PIXEL_ID');
fbq('track', 'PageView');
</script>
```

---

## 📊 MONITORING & PERFORMANCE

### **Sprawdź performance:**
- https://pagespeed.web.dev (wpisz berecki.com)
- Target: 90+ na mobile i desktop

### **Sprawdź SEO:**
- https://www.seobility.net/en/seocheck/ 
- Target: 80+ score

### **Sprawdź DNS propagację:**
- https://dnschecker.org (wpisz berecki.com)

---

## 🆘 TROUBLESHOOTING

### **Problem: Strona nie działa po 24h**
**Rozwiązanie:**
- Sprawdź DNS na https://dnschecker.org
- Upewnij się że A record = `75.2.60.5`
- Sprawdź czy nie ma starych rekordów A/CNAME w panelu domeny

### **Problem: HTTPS nie działa**
**Rozwiązanie:**
- Poczekaj 24h - Netlify auto-konfiguruje SSL
- W Netlify: Domain settings → HTTPS → "Verify DNS configuration"

### **Problem: Wersja /en nie działa**
**Rozwiązanie:**
- Sprawdź czy masz plik `_redirects` w root
- Sprawdź czy `index-en.html` jest w repo na GitHub

### **Problem: Formularz nie wysyła emaili**
**Rozwiązanie:**
- Formularz otwiera klienta email (mailto:)
- Jeśli chcesz backend: użyj Netlify Forms lub EmailJS

---

## 🎯 QUICK START - wszystko w jednym

```bash
# W VS Code Terminal:
cd C:\Users\TwojeImie\Documents\berecki-website

# Git init
git init
git add .
git commit -m "Initial commit"
git branch -M main

# Publish to GitHub (przez UI VS Code)
# lub:
# git remote add origin https://github.com/username/berecki-website.git
# git push -u origin main

# Potem:
# 1. Netlify → Import from GitHub
# 2. Deploy
# 3. Domain settings → Add berecki.com
# 4. Skonfiguruj DNS
# 5. Poczekaj 24h
# ✅ DONE!
```

---

## 📞 POTRZEBUJESZ POMOCY?

Jeśli coś nie działa:
1. Sprawdź czy wszystkie kroki są ✅
2. Przejrzyj Troubleshooting
3. Sprawdź logi w Netlify (Deploy log)

**Najczęstsze błędy:**
- Zapomniany plik `_redirects`
- Źle skonfigurowany DNS (www zamiast @)
- Nie poczekałeś 24h na DNS
- Stare rekordy A/CNAME nie usunięte

---

## 🚀 GOTOWE!

Twoja strona będzie na:
- **https://berecki.com** (PL)
- **https://berecki.com/en** (EN)

Z pełnym SEO, HTTPS, i automatycznym deploy przy każdej zmianie! 🎉
