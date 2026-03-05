# Semantyczne tagi HTML5

Tagi semantyczne nadają znaczenie strukturze strony — zamiast używać ogólnych `<div>`, opisujemy **czym jest** dany fragment treści. Ułatwia to czytanie kodu, pozycjonowanie (SEO) i dostępność (WCAG).

---

## 🏗️ Tagi struktury strony

### `<header>` — Nagłówek strony lub sekcji

Zastępuje `<div id="header">`. Zawiera zazwyczaj logo, tytuł strony, hasło reklamowe.

```html
<header>
  <img src="logo.png" alt="Logo firmy">
  <h1>Moja Strona</h1>
  <p>Najlepszy blog o HTML!</p>
</header>
```

---

### `<nav>` — Nawigacja, menu linków

Zastępuje `<div id="menu">`. Przeznaczony dla głównych bloków nawigacyjnych z linkami.

```html
<nav>
  <ul>
    <li><a href="/">Strona główna</a></li>
    <li><a href="/blog">Blog</a></li>
    <li><a href="/kontakt">Kontakt</a></li>
  </ul>
</nav>
```

---

### `<main>` — Główna treść strony

Zastępuje `<div id="content">`. Na jednej stronie może wystąpić **tylko raz**. Zawiera treść unikatową dla danego widoku.

```html
<main>
  <h2>Witaj na moim blogu!</h2>
  <p>Tu znajdziesz artykuły o HTML, CSS i JavaScript.</p>
</main>
```

---

### `<footer>` — Stopka strony lub sekcji

Zastępuje `<div id="footer">`. Zazwyczaj zawiera prawa autorskie, linki do polityki prywatności, dane kontaktowe.

```html
<footer>
  <p>&copy; 2025 Moja Strona. Wszelkie prawa zastrzeżone.</p>
  <a href="/polityka-prywatnosci">Polityka prywatności</a>
</footer>
```

---

### `<section>` — Tematyczna sekcja treści

Zastępuje `<div class="sekcja">`. Grupuje powiązaną tematycznie treść. **Powinna posiadać nagłówek** (`<h2>`, `<h3>` itp.).

```html
<section>
  <h2>Nasze usługi</h2>
  <p>Oferujemy projektowanie stron, aplikacji i sklepów internetowych.</p>
</section>

<section>
  <h2>Opinie klientów</h2>
  <p>"Świetna współpraca!" — Anna K.</p>
</section>
```

---

### `<article>` — Samodzielna, niezależna treść

Zastępuje `<div class="artykul">`. Przeznaczony dla treści, która ma sens **poza kontekstem strony** — wpis blogowy, post, artykuł, komentarz.

```html
<article>
  <h2>Jak używać tagów semantycznych?</h2>
  <p>Opublikowano: <time datetime="2025-06-10">10 czerwca 2025</time></p>
  <p>Tagi semantyczne pomagają wyszukiwarkom i czytelnikom ekranu...</p>
</article>
```

---

### `<aside>` — Treść poboczna

Zastępuje `<div id="sidebar">`. Zawiera treść pośrednio powiązaną z główną treścią — sidebar, reklamy, linki pokrewne, cytaty wyróżnione.

```html
<aside>
  <h3>Polecane artykuły</h3>
  <ul>
    <li><a href="#">Wprowadzenie do CSS Grid</a></li>
    <li><a href="#">Flexbox krok po kroku</a></li>
  </ul>
</aside>
```

---

## 📝 Tagi treści

### `<figure>` i `<figcaption>` — Ilustracja z podpisem

`<figure>` opakowuje ilustrację (zdjęcie, diagram, kod), a `<figcaption>` dodaje do niej podpis. Obydwa tagi działają razem.

```html
<figure>
  <img src="zachod-slonca.jpg" alt="Zachód słońca nad morzem">
  <figcaption>Fot. Jan Kowalski — Bałtyk, sierpień 2024</figcaption>
</figure>
```

---

### `<time>` — Data lub godzina

Wyświetla datę/godzinę w sposób czytelny dla człowieka, a atrybut `datetime` przekazuje maszynowy format dla wyszukiwarek i czytników.

```html
<!-- Data -->
<p>Artykuł opublikowany: <time datetime="2025-09-01">1 września 2025</time></p>

<!-- Godzina -->
<p>Spotkanie o <time datetime="14:30">14:30</time></p>

<!-- Data i godzina -->
<p>Wydarzenie: <time datetime="2025-09-01T14:30">1 września 2025, godz. 14:30</time></p>
```

---

### `<mark>` — Wyróżnienie tekstu

Działa jak **marker** na tekście — podświetla fragment uznany za szczególnie istotny w danym kontekście (np. wyniki wyszukiwania).

```html
<p>
  W dokumencie znaleziono frazę: 
  „Użyj tagu <mark>semantycznego</mark>, aby opisać znaczenie treści."
</p>

<!-- Przykład wyników wyszukiwania -->
<p>Wyniki dla „<mark>HTML5</mark>": znaleziono 42 artykuły.</p>
```

---

### `<details>` i `<summary>` — Rozwijana sekcja (bez JS!)

`<details>` tworzy natywny element rozwijany. `<summary>` to klikalny nagłówek widoczny zawsze — reszta treści jest ukryta do rozwinięcia. Nie wymaga JavaScript!

```html
<!-- FAQ -->
<details>
  <summary>Czym są tagi semantyczne?</summary>
  <p>
    Tagi semantyczne to elementy HTML, które opisują znaczenie zawartej w nich treści,
    a nie tylko jej wygląd. Przykłady: <code>&lt;article&gt;</code>, 
    <code>&lt;nav&gt;</code>, <code>&lt;footer&gt;</code>.
  </p>
</details>

<!-- Spoiler -->
<details>
  <summary>⚠️ Uwaga: spoiler do filmu!</summary>
  <p>Okazuje się, że mordercą był ogrodnik...</p>
</details>

<!-- Domyślnie otwarte (atrybut open) -->
<details open>
  <summary>Wskazówka dla początkujących</summary>
  <p>Zawsze waliduj swój HTML na stronie validator.w3.org!</p>
</details>
```

---

## 🗺️ Przykład kompletnej struktury strony

Poniżej pełna strona używająca wszystkich omówionych tagów:

```html
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <title>Blog o HTML5</title>
</head>
<body>

  <header>
    <h1>Blog o HTML5</h1>
    <nav>
      <a href="/">Główna</a> |
      <a href="/artykuly">Artykuły</a> |
      <a href="/kontakt">Kontakt</a>
    </nav>
  </header>

  <main>
    <article>
      <h2>Dlaczego warto używać semantycznego HTML?</h2>
      <p>Opublikowano: <time datetime="2025-06-15">15 czerwca 2025</time></p>

      <figure>
        <img src="html5.png" alt="Logo HTML5">
        <figcaption>Logo standardu HTML5 — wprowadzonego w 2014 roku.</figcaption>
      </figure>

      <p>
        Stosowanie tagów semantycznych to <mark>podstawa dobrego kodu</mark>.
        Pomaga robotom wyszukiwarek i czytnikom ekranu zrozumieć strukturę strony.
      </p>

      <details>
        <summary>Czy tagi semantyczne wpływają na SEO?</summary>
        <p>Tak! Wyszukiwarki takie jak Google lepiej indeksują strony
        z poprawną semantyką HTML.</p>
      </details>
    </article>

    <section>
      <h2>Powiązane tematy</h2>
      <p>Dowiedz się więcej o CSS, dostępności i standardach W3C.</p>
    </section>
  </main>

  <aside>
    <h3>Popularne artykuły</h3>
    <ul>
      <li><a href="#">CSS Grid w 10 minut</a></li>
      <li><a href="#">Flexbox dla początkujących</a></li>
    </ul>
  </aside>

  <footer>
    <p>&copy; 2025 Blog o HTML5</p>
  </footer>

</body>
</html>
```

---

## 📊 Szybkie porównanie: tag semantyczny vs. div

| Tag semantyczny | Stary odpowiednik `<div>` | Znaczenie |
|---|---|---|
| `<header>` | `<div id="header">` | Nagłówek strony/sekcji |
| `<nav>` | `<div id="menu">` | Nawigacja/menu |
| `<main>` | `<div id="content">` | Główna treść (1×) |
| `<footer>` | `<div id="footer">` | Stopka |
| `<section>` | `<div class="sekcja">` | Sekcja tematyczna |
| `<article>` | `<div class="artykul">` | Samodzielna treść |
| `<aside>` | `<div id="sidebar">` | Treść poboczna |
| `<figure>` | `<div class="grafika">` | Ilustracja z podpisem |
| `<time>` | `<span>` | Data/godzina |
| `<mark>` | `<span class="highlight">` | Wyróżnienie tekstu |
| `<details>` | `<div>` + JavaScript | Rozwijana sekcja |
