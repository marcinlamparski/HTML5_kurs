# HTML5 - Struktura Dokumentu i Semantyka

## Wprowadzenie

W tym module nauczysz się budować semantyczną strukturę dokumentów HTML5. Semantyka oznacza **używanie odpowiednich elementów do opisania zawartości**[1][2].

**Czego się nauczysz w tym module:**
- ✅ Semantyczne elementy HTML5
- ✅ Struktura strony internetowej
- ✅ Hierarchia zawartości
- ✅ Accessibility i SEO
- ✅ Praktyczne layouty
- ✅ Best practices

---

## Część 1: Semantyczne Elementy HTML5

### Co to Semantyka?

Semantyka oznacza, że HTML opisuje **znaczenie zawartości**, a nie tylko jej wygląd.

```html
<!-- ❌ ŹLE - Brak semantyki -->
<div class="header">
    <div class="nav"></div>
</div>

<!-- ✅ DOBRZE - Semantyczne -->
<header>
    <nav></nav>
</header>
```

### Główne Elementy Semantyczne

```html
<header>...</header>           <!-- Nagłówek strony/sekcji -->
<nav>...</nav>                 <!-- Nawigacja -->
<main>...</main>               <!-- Główna zawartość (jeden na stronę!) -->
<article>...</article>         <!-- Artykuł, post, wiadomość -->
<section>...</section>         <!-- Sekcja o powiązanej zawartości -->
<aside>...</aside>             <!-- Sidebar, informacje poboczne -->
<footer>...</footer>           <!-- Stopka strony/sekcji -->
```

### Zastosowania

#### `<header>` - Nagłówek

```html
<header>
    <h1>Nazwa Strony</h1>
    <p>Slogan lub opis</p>
</header>

<!-- Nagłówek sekcji -->
<article>
    <header>
        <h2>Tytuł Artykułu</h2>
        <p>Autor: Jan Kowalski</p>
    </header>
</article>
```

#### `<nav>` - Nawigacja

```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">O nas</a></li>
        <li><a href="/contact">Kontakt</a></li>
    </ul>
</nav>
```

#### `<main>` - Główna Zawartość

```html
<body>
    <header>...</header>
    <nav>...</nav>
    
    <main>
        <!-- Główna zawartość strony -->
        <article>...</article>
    </main>
    
    <footer>...</footer>
</body>
```

#### `<article>` - Artykuł

```html
<article>
    <header>
        <h2>Mój Blog Post</h2>
        <p>Opublikowano: 1 stycznia 2024</p>
    </header>
    
    <p>Zawartość artykułu...</p>
    
    <footer>
        <p>Autor: Jan Kowalski</p>
    </footer>
</article>
```

#### `<section>` - Sekcja

```html
<section>
    <h2>Usługi</h2>
    <article>
        <h3>Usługa 1</h3>
        <p>Opis...</p>
    </article>
    <article>
        <h3>Usługa 2</h3>
        <p>Opis...</p>
    </article>
</section>
```

#### `<aside>` - Informacje Poboczne

```html
<body>
    <header>...</header>
    <main>...</main>
    
    <aside>
        <h3>Kategorie</h3>
        <ul>
            <li><a href="#">HTML</a></li>
            <li><a href="#">CSS</a></li>
        </ul>
    </aside>
</body>
```

#### `<footer>` - Stopka

```html
<footer>
    <p>&copy; 2024 Moja Strona. Wszelkie prawa zastrzeżone.</p>
    <ul>
        <li><a href="#">Polityka Prywatności</a></li>
        <li><a href="#">Warunki Użytkownika</a></li>
    </ul>
</footer>
```

---

## Część 2: Struktura Typowej Strony

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moja Strona</title>
</head>
<body>
    <!-- Nagłówek -->
    <header>
        <h1>Moja Strona</h1>
        <p>Witaj na mojej stronie!</p>
    </header>
    
    <!-- Nawigacja -->
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/blog">Blog</a></li>
            <li><a href="/contact">Kontakt</a></li>
        </ul>
    </nav>
    
    <!-- Główna zawartość -->
    <main>
        <article>
            <h2>Mój Pierwszy Post</h2>
            <p>Zawartość...</p>
        </article>
    </main>
    
    <!-- Sidebar -->
    <aside>
        <h3>Ostatnie posty</h3>
        <ul>
            <li><a href="#">Post 1</a></li>
            <li><a href="#">Post 2</a></li>
        </ul>
    </aside>
    
    <!-- Stopka -->
    <footer>
        <p>&copy; 2024 Moja Strona</p>
    </footer>
</body>
</html>
```

---

## Część 3: Zagnieżdżane Sekcje

```html
<body>
    <header>...</header>
    
    <main>
        <section>
            <h2>Sekcja 1</h2>
            <article>
                <h3>Artykuł w Sekcji</h3>
                <p>Zawartość...</p>
            </article>
        </section>
        
        <section>
            <h2>Sekcja 2</h2>
            <section>
                <h3>Podsection</h3>
                <p>Zawartość...</p>
            </section>
        </section>
    </main>
    
    <footer>...</footer>
</body>
```

---

## Część 4: Figure i Figcaption

Używaj `<figure>` i `<figcaption>` dla obrazów, diagramów, kodów z opisami.

```html
<figure>
    <img src="diagram.jpg" alt="Diagram architekury">
    <figcaption>Rysunek 1: Architektura systemu</figcaption>
</figure>

<figure>
    <code>
        function hello() {
            console.log("Hello World");
        }
    </code>
    <figcaption>Kod funkcji hello()</figcaption>
</figure>
```

---

## Część 5: Hierarchia Nagłówków

### Prawidłowa Hierarchia

```html
<h1>Główny Tytuł Strony</h1>

<section>
    <h2>Sekcja 1</h2>
    <p>Zawartość...</p>
    
    <h3>Podsekcja 1.1</h3>
    <p>Zawartość...</p>
</section>

<section>
    <h2>Sekcja 2</h2>
    <p>Zawartość...</p>
</section>
```

### Złe Praktyki

```html
<!-- ❌ ŹLE - Skipowanie poziomów -->
<h1>Główny Tytuł</h1>
<h3>Pomiń h2!</h3>  <!-- Błąd! -->

<!-- ❌ ŹLE - Wiele h1 -->
<h1>Tytuł 1</h1>
<h1>Tytuł 2</h1>  <!-- Tylko jeden h1 na stronę! -->

<!-- ❌ ŹLE - Brak struktury -->
<h1>Nagłówek</h1>
<h1>Inny</h1>
<h5>Niski poziom</h5>
```

---

## Część 6: Meta Tagi dla Semantyki

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <!-- Kodowanie -->
    <meta charset="UTF-8">
    
    <!-- Viewport -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!-- Opis strony (SEO) -->
    <meta name="description" content="Krótki opis mojej strony">
    
    <!-- Słowa kluczowe -->
    <meta name="keywords" content="html, css, javascript">
    
    <!-- Autor -->
    <meta name="author" content="Jan Kowalski">
    
    <!-- Canonical (zapobiega duplicate content) -->
    <link rel="canonical" href="https://example.com/page">
    
    <!-- Open Graph (media społeczne) -->
    <meta property="og:title" content="Tytuł">
    <meta property="og:description" content="Opis">
    <meta property="og:image" content="image.jpg">
    
    <title>Moja Strona</title>
</head>
</html>
```

---

## Część 7: Ćwiczenia

### Ćwiczenie 1: Poprawianie Semantyki

Masz ten HTML:
```html
<div class="header">
    <h1>Blog</h1>
    <div class="menu">
        <a href="/">Home</a>
        <a href="/blog">Blog</a>
    </div>
</div>

<div class="post">
    <h2>Mój Post</h2>
    <p>Zawartość...</p>
</div>

<div class="sidebar">
    <h3>Kategorie</h3>
    <a href="#">HTML</a>
</div>

<div class="footer">
    <p>Copyright 2024</p>
</div>
```

**Zadanie:** Zamień wszystkie divy na semantyczne elementy HTML5.

### Ćwiczenie 2: Struktura Strony

Stwórz kompletną stronę "Restauracji" z:
1. Nagłówkiem zawierającym nazwę restauracji
2. Nawigacją do: Menu, O nas, Rezerwacja, Kontakt
3. Główną zawartością z artykułem o restauracji
4. Sidebarze z godzinami otwarcia
5. Stopką z copyright i linkami

### Ćwiczenie 3: Blog

Stwórz strukturę bloga zawierającą:
1. Główny nagłówek strony
2. Nawigacja
3. Co najmniej 3 artykuły w sekcjach
4. Sidebar z kategorią
5. Stopka

### Ćwiczenie 4: Validacja Semantyki

Sprawdź swoją stronę:
1. Czy masz tylko jeden `<h1>`?
2. Czy hierarchia nagłówków jest poprawna?
3. Czy używasz `<main>` tylko raz?
4. Czy znaczniki semantyczne są prawidłowo zagnieżdżone?

---

## Podsumowanie

W tym module nauczyliśmy się:

✅ **Semantyka HTML5** - znaczenie zawartości  
✅ **Elementy Strukturalne** - header, nav, main, footer  
✅ **Zagnieżdżanie** - article, section, aside  
✅ **Hierarchia** - h1-h6 prawidłowo  
✅ **Figure i Figcaption** - dla obrazów  
✅ **Meta Tagi** - dla SEO i social media  
✅ **Best Practices** - prawidłowa struktura  

---

## Zasoby Dodatkowe

- [MDN Semantic HTML](https://developer.mozilla.org/en-US/docs/Glossary/Semantic_HTML)
- [W3C HTML Semantics](https://www.w3.org/TR/html-semantics/)
- [HTML5 Outlining Algorithm](https://www.w3.org/TR/html52/sections.html)

---

*Gotowy do Modułu 3? Nauczymy się Tekstu i Formatowania! 🚀*