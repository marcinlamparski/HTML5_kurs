# HTML5 - Moduły 10-13: Zaawansowane Tematy

## Moduł 10: HTML5 Elementy Zaawansowane

```html
<!-- Details i Summary -->
<details>
    <summary>Kliknij aby rozwinąć</summary>
    Zawartość która się pokazuje/ukrywa
</details>

<!-- Progress Bar -->
<progress value="70" max="100"></progress>

<!-- Meter -->
<meter value="6" min="0" max="10"></meter>

<!-- Time -->
<time datetime="2024-01-15">15 stycznia 2024</time>

<!-- Dialog -->
<dialog id="mydialog">
    <p>Zawartość dialoga</p>
    <button>Zamknij</button>
</dialog>

<!-- Mark -->
<p>To jest <mark>zaznaczony</mark> tekst</p>

<!-- Output -->
<output>Wynik: </output>

<!-- Data Attributes -->
<div data-user-id="123" data-role="admin">Element</div>

<!-- Datalist -->
<input list="browsers">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
</datalist>
```

---

## Moduł 11: Dostępność i SEO

### WCAG Guidelines

```html
<!-- Alt text na obrazach -->
<img src="photo.jpg" alt="Opis dla niewidomych">

<!-- Labels na formularzach -->
<label for="email">E-mail:</label>
<input id="email" type="email">

<!-- Semantic HTML -->
<header>, <nav>, <main>, <article>, <footer>

<!-- ARIA Labels -->
<button aria-label="Zamknij">×</button>

<!-- Skip Links -->
<a href="#main" class="skip-link">Skip to main content</a>

<!-- Kontrast Tekstu -->
<!-- Minimalnie 4.5:1 dla normalnego tekstu -->

<!-- Rozmiar Tekstu -->
<!-- Minimalnie 16px na mobilnych -->

<!-- Focus Visible -->
button:focus {
    outline: 2px solid blue;
}
```

### SEO Optimization

```html
<!-- Meta Tags -->
<meta name="description" content="Krótki opis strony">
<meta name="keywords" content="html, css, javascript">

<!-- Open Graph -->
<meta property="og:title" content="Tytuł">
<meta property="og:image" content="image.jpg">

<!-- Canonical Link -->
<link rel="canonical" href="https://example.com/page">

<!-- Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Nazwa"
}
</script>
```

---

## Moduł 12: Walidacja i Best Practices

### W3C Walidacja

1. Idź na https://validator.w3.org/
2. Upload plik HTML
3. Czytaj raporty
4. Naprawiaj błędy

### Checklist Best Practices

```
✅ DOCTYPE html
✅ <html lang="pl">
✅ Meta charset="UTF-8"
✅ Meta viewport
✅ Semantic HTML
✅ Jeden <h1> na stronę
✅ Hierarchia nagłówków
✅ Alt na obrazach
✅ Labels na formularzach
✅ Brak divów zamiast semantic
✅ Walidny kod
✅ Responsywny design
✅ Performance optimized
✅ Dostępny (WCAG)
✅ Mobile-friendly
```

---

## Moduł 13: Responsive Design i Projekty

### Mobile-First

```html
<!-- Viewport Meta (WAŻNE!) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Responsywne Obrazy -->
<picture>
    <source media="(max-width: 600px)" srcset="small.jpg">
    <source media="(max-width: 1200px)" srcset="medium.jpg">
    <img src="large.jpg" alt="Image">
</picture>

<!-- Srcset -->
<img src="photo.jpg" 
     srcset="small.jpg 480w, medium.jpg 800w, large.jpg 1200w"
     alt="Photo">
```

### Projekt Końcowy

**Zadanie:** Stwórz pełną stronę zawierającą:

1. **Struktura HTML5** (10 pkt)
   - Prawidłowy DOCTYPE
   - Semantic elementy
   - Prawidłowa hierarchia

2. **Zawartość** (20 pkt)
   - Tekst z formatowaniem
   - Listy
   - Co najmniej 3 linki
   - Multimedia (obrazy)

3. **Formularze** (20 pkt)
   - Co najmniej 2 formy
   - Różne typy input
   - Labels i fieldsets
   - Walidacja HTML5

4. **Tabele** (15 pkt)
   - Przynajmniej 1 tabela
   - thead, tbody, tfoot
   - Scalanie komórek

5. **Dostępność** (15 pkt)
   - Alt tagi na wszystkich obrazach
   - WCAG kontrast
   - ARIA labels gdzie potrzeba
   - Skip links

6. **SEO i Meta** (10 pkt)
   - Meta description
   - Open Graph
   - Structured data
   - Canonical link

7. **Walidacja** (10 pkt)
   - Brak błędów w W3C Validatorze
   - Mobile-friendly
   - Responsywny design

**Maksymalnie 100 punktów**

---

## Podsumowanie Całego Kursu

W tych 13 modułach nauczyliśmy się:

✅ **HTML5 Podstawy** - struktura dokumentu  
✅ **Semantic HTML** - znaczenia zawartości  
✅ **Tekst i Formatowanie** - wszystkie tagi tekstowe  
✅ **Listy** - nienumerowane, numerowane, definicji  
✅ **Linki i Nawigacja** - wszystkie typy linków  
✅ **Multimedia** - obrazy, audio, video  
✅ **Tabele** - dane tabelaryczne  
✅ **Formularze** - zbieranie danych  
✅ **Zaawansowane Elementy** - nowe w HTML5  
✅ **Dostępność** - WCAG guidelines  
✅ **SEO** - optymalizacja  
✅ **Walidacja** - W3C standards  
✅ **Responsywny Design** - dla wszystkich urządzeń  

---

## Zasoby Końcowe

### Dokumentacja
- [MDN Web Docs HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [W3C HTML Specification](https://html.spec.whatwg.org/)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

### Narzędzia
- [W3C HTML Validator](https://validator.w3.org/)
- [WAVE Accessibility](https://wave.webaim.org/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)
- [Can I Use](https://caniuse.com/)

### Inspiracja
- [CodePen](https://codepen.io/)
- [Dribbble](https://dribbble.com/)
- [Awwwards](https://www.awwwards.com/)

---

**Gratulacje! Ukończyłeś kurs HTML5! 🎉**

Teraz jesteś gotowy do:
- Egzaminu INF.03.3 ✅
- Nauki CSS i JavaScript
- Tworzenia profesjonalnych stron
- Pracy jako Junior Front-end Developer

Powodzenia! 🚀

---

*Autor: Kompletny kurs HTML5 dla Technikum Informatycznego*  
*Wersja: 1.0*  
*Data: 2025-11-03*