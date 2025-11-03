# HTML5 - Kompletny Cheatsheet (Ściąga)

Szybka referencja wszystkich ważnych tagów, atrybutów i konceptów HTML5.

---

## 📑 Struktura Dokumentu

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tytuł Strony</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Zawartość -->
    <script src="script.js"></script>
</body>
</html>
```

---

## 📄 Semantyczne Elementy

```html
<header>...</header>       <!-- Nagłówek strony/sekcji -->
<nav>...</nav>             <!-- Nawigacja -->
<main>...</main>           <!-- Główna zawartość -->
<article>...</article>     <!-- Artykuł/post -->
<section>...</section>     <!-- Sekcja -->
<aside>...</aside>         <!-- Sidebar/dodatkowe -->
<footer>...</footer>       <!-- Stopka -->
<figure>...</figure>       <!-- Obrazy/diagramy -->
<figcaption>...</figcaption> <!-- Podpis do figure -->
```

---

## 📝 Tekst i Formatowanie

```html
<!-- Nagłówki -->
<h1>Główny nagłówek</h1>
<h2>Nagłówek 2</h2>
...
<h6>Nagłówek 6</h6>

<!-- Tekst -->
<p>Paragraf</p>
<div>Blok zawartości</div>
<span>Tekst inline</span>

<!-- Formatowanie -->
<strong>Tekst ważny</strong>
<em>Tekst podkreślony</em>
<b>Pogrubienie</b>
<i>Kursywa</i>
<mark>Zaznaczony tekst</mark>
<small>Mały tekst</small>
<del>Usunięty tekst</del>
<ins>Wstawiony tekst</ins>

<!-- Cytaty -->
<blockquote cite="http://example.com">
    Duża cytacja
</blockquote>
<q>Mała cytacja</q>

<!-- Kod -->
<code>kod inline</code>
<pre>
    Wstępnie sformatowany kod
    Z zachowaniem spacji
</pre>

<!-- Specjalne -->
<br>                    <!-- Łamanie linii -->
<hr>                    <!-- Linia pozioma -->
<nbsp>                  <!-- Spacja nieprzełamywalna -->
<wbr>                   <!-- Wskazówka łamania linii -->
```

---

## 🔗 Linki

```html
<!-- Link zwykły -->
<a href="https://example.com">Link</a>

<!-- Link wewnętrzny -->
<a href="/strona.html">Strona</a>
<a href="index.html">Home</a>

<!-- Anchor (skok na stronie) -->
<a href="#sekcja">Skocz do sekcji</a>
<h2 id="sekcja">Sekcja</h2>

<!-- E-mail -->
<a href="mailto:email@example.com">Wyślij e-mail</a>

<!-- Telefon -->
<a href="tel:+48123456789">Zadzwoń</a>

<!-- Atrybuty -->
<a href="..." target="_blank">Otwórz w nowej karcie</a>
<a href="..." download>Pobierz plik</a>
<a href="..." rel="nofollow">SEO tag</a>
```

---

## 🖼️ Multimedia

```html
<!-- Obraz -->
<img src="obraz.jpg" alt="Opis">
<img src="obraz.jpg" alt="Opis" width="300" height="200">
<img src="obraz.jpg" alt="Opis" srcset="obraz2x.jpg 2x">

<!-- SVG -->
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="red" />
</svg>

<!-- Canvas -->
<canvas id="myCanvas" width="200" height="200"></canvas>

<!-- Audio -->
<audio controls>
  <source src="audio.mp3" type="audio/mpeg">
  Przeglądarka nie wspiera audio
</audio>

<!-- Video -->
<video controls width="300" height="200">
  <source src="video.mp4" type="video/mp4">
  Przeglądarka nie wspiera video
</video>

<!-- Picture (Responsywne obrazy) -->
<picture>
  <source srcset="obraz-large.jpg" media="(min-width: 800px)">
  <source srcset="obraz-small.jpg" media="(max-width: 600px)">
  <img src="obraz-default.jpg" alt="Obraz">
</picture>
```

---

## 📋 Listy

```html
<!-- Lista nienumerowana -->
<ul>
    <li>Punkt 1</li>
    <li>Punkt 2</li>
</ul>

<!-- Lista numerowana -->
<ol>
    <li>Pierwszy</li>
    <li>Drugi</li>
</ol>

<!-- Lista definicji -->
<dl>
    <dt>HTML</dt>
    <dd>Język znaczników</dd>
</dl>

<!-- Zagnieżdżone -->
<ul>
    <li>Punkt 1
        <ul>
            <li>Podpunkt 1.1</li>
        </ul>
    </li>
</ul>
```

---

## 📊 Tabele

```html
<table>
    <thead>
        <tr>
            <th>Nagłówek 1</th>
            <th>Nagłówek 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Dane 1</td>
            <td>Dane 2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Suma</td>
            <td>100</td>
        </tr>
    </tfoot>
</table>

<!-- Atrybuty -->
<td colspan="2">Łączy 2 kolumny</td>
<td rowspan="3">Łączy 3 wiersze</td>
<table border="1" cellpadding="10" cellspacing="0">
```

---

## 📝 Formularze - Część 1

```html
<!-- Form -->
<form action="/submit.php" method="POST">
    
    <!-- Tekst -->
    <input type="text" name="username" placeholder="Wpisz imię">
    <input type="password" name="password">
    <input type="email" name="email" required>
    <input type="number" name="age" min="18" max="100">
    <input type="date" name="data">
    <input type="time" name="godzina">
    <input type="color" name="kolor">
    <input type="range" name="głośność" min="0" max="100">
    <input type="url" name="strona">
    <input type="tel" name="telefon">
    <input type="search" name="szukaj">
    
    <!-- TextArea -->
    <textarea name="wiadomość" rows="5" cols="50"></textarea>
    
    <!-- Select -->
    <select name="kraj">
        <option value="">Wybierz...</option>
        <option value="pl">Polska</option>
        <option value="de">Niemcy</option>
    </select>
    
    <!-- Label -->
    <label for="email">E-mail:</label>
    <input type="email" id="email" name="email">
    
    <!-- Przycisk -->
    <button type="submit">Wyślij</button>
    <button type="reset">Wyczyść</button>
    <button type="button">Przycisk</button>
    
</form>
```

---

## ✅ Formularze - Część 2

```html
<!-- Checkboxa -->
<input type="checkbox" name="zgoda" id="zgoda">
<label for="zgoda">Zgadzam się</label>

<!-- Radio buttons -->
<input type="radio" name="płeć" value="m"> Mężczyzna
<input type="radio" name="płeć" value="k"> Kobieta

<!-- Fieldset -->
<fieldset>
    <legend>Dane osobowe</legend>
    <label>Imię: <input type="text"></label>
    <label>Nazwisko: <input type="text"></label>
</fieldset>

<!-- Atrybuty Walidacji -->
<input type="email" required>
<input type="text" minlength="3" maxlength="20">
<input type="number" min="0" max="100" step="5">
<input type="text" pattern="[A-Z]{3}">
<input type="email" placeholder="user@example.com">
<input type="text" disabled>
<input type="text" readonly>
<input type="text" autofocus>
<input type="text" autocomplete="off">
```

---

## 🏷️ Atrybuty Globalne

```html
<!-- Identyfikacja -->
<div id="unique-id">...</div>
<p class="klasa1 klasa2">...</p>

<!-- Opisy -->
<div title="Tooltip">...</div>
<a href="..." aria-label="Opis dla czytników">Link</a>

<!-- Edycja -->
<div contenteditable="true">Edytowalny tekst</div>
<div draggable="true">Przeciągalny</div>

<!-- Data Attributes -->
<div data-user-id="123" data-role="admin">...</div>

<!-- Style inline (unikaj!) -->
<p style="color: red; font-size: 16px;">...</p>

<!-- Inne -->
<p hidden>Ukryty tekst</p>
<span lang="en">Angielski tekst</span>
<div dir="rtl">Tekst od prawej do lewej</div>
```

---

## 🌐 Meta Tagi

```html
<!-- Kodowanie -->
<meta charset="UTF-8">

<!-- Viewport (WAŻNE!) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- SEO -->
<meta name="description" content="Opis strony">
<meta name="keywords" content="słowa, kluczowe">
<meta name="author" content="Imię Autora">

<!-- Open Graph (Media społeczne) -->
<meta property="og:title" content="Tytuł">
<meta property="og:description" content="Opis">
<meta property="og:image" content="image.jpg">
<meta property="og:url" content="https://example.com">
<meta property="og:type" content="website">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Tytuł">
<meta name="twitter:description" content="Opis">

<!-- Inne -->
<meta name="theme-color" content="#FF0000">
<meta http-equiv="X-UA-Compatible" content="ie=edge">
<meta http-equiv="refresh" content="30">
```

---

## ♿ Dostępność (WCAG)

```html
<!-- Alt tagi dla obrazów -->
<img src="photo.jpg" alt="Opis dla niewidomych">

<!-- Labels dla form -->
<label for="email">E-mail:</label>
<input id="email" type="email">

<!-- ARIA atrybuty -->
<button aria-label="Zamknij menu">×</button>
<div role="navigation" aria-label="Główna">
    <a href="/">Home</a>
</div>

<!-- Semantyczne HTML -->
<header>, <nav>, <main>, <article>, <footer>

<!-- Skip links -->
<a href="#main" class="skip-link">Skip to content</a>

<!-- Kontrast tekstu -->
<!-- Minimalnie 4.5:1 dla tekstu zwykłego -->

<!-- Rozmiar tekstu -->
<!-- Minimalnie 16px na mobilnych -->
```

---

## 🎯 HTML5 Elementy Zaawansowane

```html
<!-- Szczegóły -->
<details>
    <summary>Kliknij aby rozwinąć</summary>
    Zawartość
</details>

<!-- Postęp -->
<progress value="70" max="100"></progress>

<!-- Pomiar -->
<meter value="6" min="0" max="10"></meter>

<!-- Czas -->
<time datetime="2023-01-15">15 stycznia</time>

<!-- Dialog -->
<dialog id="mydialog">
    <p>Zawartość dialoga</p>
    <button>Zamknij</button>
</dialog>

<!-- Mark -->
<p>To jest <mark>zaznaczony</mark> tekst</p>

<!-- Output -->
<output>Wynik</output>

<!-- Keygen -->
<keygen name="rsa" keytype="RSA">
```

---

## 📱 Responsive Design

```html
<!-- Viewport Meta -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Picture Element -->
<picture>
    <source media="(max-width: 600px)" srcset="small.jpg">
    <source media="(min-width: 601px)" srcset="large.jpg">
    <img src="default.jpg" alt="Image">
</picture>

<!-- Srcset na img -->
<img src="photo.jpg" 
     srcset="photo-small.jpg 480w,
             photo-medium.jpg 800w,
             photo-large.jpg 1200w"
     sizes="(max-width: 600px) 100vw,
            (max-width: 1200px) 50vw,
            33vw"
     alt="Photo">
```

---

## ⚙️ Walidacja

```html
<!-- Required -->
<input type="text" required>

<!-- Type Validation -->
<input type="email"> 
<input type="number">
<input type="date">

<!-- Length -->
<input type="text" minlength="3" maxlength="20">

<!-- Pattern -->
<input type="text" pattern="[0-9]{3}-[0-9]{2}-[0-9]{4}">

<!-- Range -->
<input type="number" min="18" max="65" step="5">

<!-- Custom Validation -->
<input type="text" onchange="validate()">
```

---

## 📌 Atrybuty Form

```html
<!-- Form attributes -->
<form action="/submit" method="POST" enctype="multipart/form-data">
    
    <!-- Input attributes -->
    <input name="username"          <!-- Nazwa pola -->
           type="text"              <!-- Typ -->
           value="default"          <!-- Wartość domyślna -->
           placeholder="Wpisz..."   <!-- Hint -->
           required                 <!-- Obowiązkowe -->
           disabled                 <!-- Wyłączone -->
           readonly                 <!-- Tylko do czytania -->
           autofocus                <!-- Automatyczny focus -->
           autocomplete="off"       <!-- Autouzupełnianie -->
    >
    
</form>
```

---

## 🔍 SEO i Structured Data

```html
<!-- Canonical link -->
<link rel="canonical" href="https://example.com/page">

<!-- Robots -->
<meta name="robots" content="index, follow">

<!-- JSON-LD Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "LocalBusiness",
  "name": "Nazwa Biznesu",
  "description": "Opis"
}
</script>

<!-- Microdata -->
<div itemscope itemtype="https://schema.org/Organization">
  <span itemprop="name">Nazwa</span>
</div>
```

---

## 🚀 Best Practices

✅ Zawsze używaj DOCTYPE  
✅ Definiuj lang na html  
✅ Użyj meta charset  
✅ Stwórz meta viewport  
✅ Semantyczne HTML zamiast div soup  
✅ Labele dla form field  
✅ Alt tagi dla obrazów  
✅ Logiczny order nagłówków  
✅ Waliduj HTML  
✅ Responsywny design  
✅ Testy dostępności  
✅ Komentarze w kodzie  

---

## 🛠️ Narzędzia

- [W3C HTML Validator](https://validator.w3.org/)
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)
- [WAVE - Accessibility](https://wave.webaim.org/)
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [CanIUse](https://caniuse.com/)

---

## 📚 Przydatne Kody

```html
<!-- Hello World -->
<!DOCTYPE html>
<html>
<body>
    <h1>Hello World!</h1>
</body>
</html>

<!-- Całkowity Szablon -->
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Strona</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <nav><!-- Menu --></nav>
    </header>
    
    <main>
        <article>
            <!-- Zawartość -->
        </article>
    </main>
    
    <footer>
        <!-- Stopka -->
    </footer>
    
    <script src="script.js"></script>
</body>
</html>
```

---

*Szybka Referencja - Print i Sharej!* 🎓