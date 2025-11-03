# HTML5 - Moduł 3: Tekst i Formatowanie

## Wprowadzenie

W tym module nauczysz się pracować z tekstem w HTML5. Nauczysz się różnych tagów do formatowania tekstu i zrozumiesz różnicę między semantycznym formatowaniem a czysto stylizacyjnym[1][2].

**Czego się nauczysz w tym module:**
- ✅ Nagłówki od h1 do h6
- ✅ Paragrafy i podziały tekstu
- ✅ Formatowanie semantyczne
- ✅ Formatowanie czysto stylizacyjne
- ✅ Znaki specjalne
- ✅ Cytaty i kod
- ✅ Best practices dla tekstu

---

## Część 1: Nagłówki (h1-h6)

### Hierarchia Nagłówków

```html
<h1>Główny nagłówek strony</h1>  <!-- Tylko jeden na stronę! -->
<h2>Sekcja główna</h2>
<h3>Podsekcja</h3>
<h4>Podnagłówek</h4>
<h5>Mały nagłówek</h5>
<h6>Najmniejszy nagłówek</h6>
```

### Rola Nagłówków

- **h1** - Główny tytuł strony (SEO!)
- **h2** - Główne sekcje (można wiele)
- **h3-h6** - Podszcje

### Prawidłowa Struktura

```html
<!DOCTYPE html>
<html>
<body>
    <h1>Blog</h1>              <!-- Główny tytuł -->
    
    <section>
        <h2>Artykuł 1</h2>     <!-- Sekcja artykułu -->
        <h3>Podsekcja</h3>     <!-- Podsekcja artykułu -->
        <p>Zawartość...</p>
    </section>
    
    <section>
        <h2>Artykuł 2</h2>     <!-- Druga sekcja -->
        <p>Zawartość...</p>
    </section>
</body>
</html>
```

---

## Część 2: Paragrafy i Podziały

### Paragraf `<p>`

```html
<p>To jest pierwszy paragraf.</p>
<p>To jest drugi paragraf.</p>
```

**Ważne:** Każdy nowy paragraf to nowy `<p>`!

### Div - Blok Zawartości

```html
<div>
    <h2>Sekcja</h2>
    <p>Pierwszy paragraf</p>
    <p>Drugi paragraf</p>
</div>
```

### Span - Tekst Inline

```html
<p>To jest <span>zaznaczony</span> tekst.</p>
```

### Line Break i Horizontal Rule

```html
<p>Linia 1<br>Linia 2</p>  <!-- Łamanie linii -->

<hr>  <!-- Linia pozioma separatora -->
```

---

## Część 3: Formatowanie Semantyczne vs Stylizacyjne

### Semantyczne Formatowanie

**`<strong>` - Tekst ważny**

```html
<p>To jest <strong>bardzo ważny</strong> tekst.</p>
```

- Przeglądarki wyświetlają jako **pogrubienie**
- Czytniki dla niewidomych czytają jako "ważne"

**`<em>` - Tekst podkreślony (emphasis)**

```html
<p>To jest <em>podkreślony</em> tekst.</p>
```

- Przeglądarki wyświetlają jako *kursywę*
- Czytniki dla niewidomych czytają jako "podkreślone"

### Tylko Stylizacja (NIE semantyczne)

**`<b>` - Pogrubienie (bold)**

```html
<p>To jest <b>pogrubione</b> (tylko styl).</p>
```

- Wygląda na pogrubienie
- Ale czytniki dla niewidomych tego nie czytają jako ważne

**`<i>` - Kursywa (italic)**

```html
<p>To jest <i>kursywą</i> (tylko styl).</p>
```

- Wygląda na kursywę
- Ale bez semantyki

### Inne Formatowanie

```html
<mark>Zaznaczony tekst</mark>      <!-- Żółty highlight -->
<small>Mały tekst</small>          <!-- Zmniejszony tekst -->
<del>Usunięty tekst</del>          <!-- Przekreślenie -->
<ins>Wstawiony tekst</ins>         <!-- Podkreślenie -->
<sub>Indeks dolny</sub>            <!-- x<sub>2</sub> -->
<sup>Indeks górny</sup>            <!-- E=mc<sup>2</sup> -->
<time>15 stycznia 2024</time>      <!-- Znacznik czasu -->
```

---

## Część 4: Cytaty i Kod

### Duża Cytacja

```html
<blockquote cite="https://example.com/source">
    <p>To jest duża cytacja, zwykle na całą linię.</p>
    <footer>— Autor</footer>
</blockquote>
```

### Mała Cytacja (Inline)

```html
<p>Jak powiedział <q>to jest cytat</q>, kontynuując myśl.</p>
```

### Kod (Inline)

```html
<p>Aby wypisać tekst, użyj komendy <code>console.log()</code>.</p>
```

### Wstępnie Sformatowany Kod

```html
<pre><code>
function hello() {
    console.log("Hello World");
}
</code></pre>
```

- `<pre>` zachowuje spacje i nowe linie
- `<code>` oznacza kod
- Razem idealne dla prezentacji kodu

---

## Część 5: Znaki Specjalne

HTML ma specjalne znaki dla znaków które mają znaczenie w HTML:

```html
&lt;     <!-- < (mniej niż) -->
&gt;     <!-- > (więcej niż) -->
&amp;    <!-- & (i) -->
&quot;   <!-- " (cudzysłów) -->
&apos;   <!-- ' (apostrof) -->
&nbsp;   <!-- Spacja nie łamana -->
&copy;   <!-- © (copyright) -->
&reg;    <!-- ® (registered) -->
&euro;   <!-- € (euro) -->
&pound;  <!-- £ (funt) -->
```

### Przykłady

```html
<p>1 &lt; 2 &lt; 3</p>           <!-- 1 < 2 < 3 -->
<p>&copy; 2024 Moja Strona</p>   <!-- © 2024 Moja Strona -->
<p>Tom &amp; Jerry</p>           <!-- Tom & Jerry -->
```

---

## Część 6: Praktyczne Przykłady

### Przykład 1: Blog Post

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Mój Blog</title>
</head>
<body>
    <h1>Mój Blog</h1>
    
    <article>
        <header>
            <h2>Mój Pierwszy Post</h2>
            <p><small>Opublikowano: <time>15 stycznia 2024</time></small></p>
        </header>
        
        <p>To jest mój <strong>pierwszy post</strong> na blogu.</p>
        
        <h3>Sekcja 1</h3>
        <p>Zawartość pierwszej sekcji.</p>
        
        <h3>Sekcja 2</h3>
        <p>Jak powiedział <q>HTML jest świetny</q>, przystępuję do nauki.</p>
        
        <h3>Kod</h3>
        <p>Oto prosty kod:</p>
        <pre><code>
&lt;p&gt;Hello World&lt;/p&gt;
        </code></pre>
    </article>
</body>
</html>
```

### Przykład 2: Artykuł Naukowy

```html
<article>
    <h1>Teoria Względności</h1>
    
    <p>Teoria względności <strong>Alberta Einsteina</strong> to...</p>
    
    <section>
        <h2>Wzór Słynny</h2>
        <p>Słynny wzór: E=mc<sup>2</sup></p>
    </section>
    
    <section>
        <h2>Cytacja</h2>
        <blockquote cite="https://en.wikipedia.org/wiki/E=mc2">
            <p>Energia równa się masa razy prędkość światła do kwadratu.</p>
        </blockquote>
    </section>
</article>
```

### Przykład 3: Instrukcja

```html
<h1>Jak Zaparzyć Herbatę</h1>

<h2>Składniki</h2>
<ul>
    <li>Woda</li>
    <li>Torebka herbaty</li>
    <li>Filiżanka</li>
</ul>

<h2>Instrukcja</h2>
<ol>
    <li>Zagrzej wodę do <strong>100°C</strong></li>
    <li>Wlej do filiżanki</li>
    <li><em>Czekaj</em> 3-5 minut</li>
    <li>Wyjmi torebkę</li>
    <li>Ciesz się <mark>świeżą herbatą</mark></li>
</ol>

<p><small>&copy; 2024 Instrukcje</small></p>
```

---

## Część 7: Ćwiczenia

### Ćwiczenie 1: Artykuł z Formatowaniem

Utwórz artykuł (minimum 3 paragrafy) o wybranym temacie zawierający:
- h1 z tytułem artykułu
- Co najmniej 2 h2 podsekcje
- **Strong** tekst (minimum 2 razy)
- *em* tekst (minimum 2 razy)
- Przynajmniej jedną cyację
- Kod (w `<code>`)

**Temat:** Czysty, bez tagów div (oprócz sekcji)

### Ćwiczenie 2: Blog Post

Stwórz prosty blog post zawierający:
- Nagłówek artykułu
- Meta informacje (autor, data)
- Przynajmniej 3 sekcje z h3
- Cytacje lub linki
- Znaki specjalne (©, &)

### Ćwiczenie 3: Prezentacja Kodu

Utwórz stronę z:
- Kilkoma fragmentami kodu
- Każdy kod powinien być w `<pre><code>`
- Wyjaśnieniami co robi kod

### Ćwiczenie 4: Walidacja

Weź swoje rozwiązania z ćwiczeń 1-3 i:
1. Waliduj je na https://validator.w3.org/
2. Popraw wszystkie błędy
3. Sprawdź czy struktura nagłówków jest prawidłowa

---

## Best Practices

✅ **Zawsze** używaj **semantycznego** formatowania (`<strong>`, `<em>`)  
✅ Wykorzystuj `<small>` dla meta informacji  
✅ Nie mieszaj formatowania (nie `<strong><em>`)  
✅ Używaj `<code>` dla kodu inline  
✅ `<pre><code>` dla bloków kodu  
✅ Cytacje powinny mieć atrybut `cite`  
✅ Waliduj HTML zawsze  
✅ Nie nadużywaj znków specjalnych  

---

## Podsumowanie

W tym module nauczyliśmy się:

✅ **Nagłówki** - hierarchia h1-h6  
✅ **Paragrafy** - struktura tekstu  
✅ **Formatowanie** - strong, em, b, i  
✅ **Cytaty** - blockquote i q  
✅ **Kod** - code i pre  
✅ **Znaki Specjalne** - &nbsp;, &copy;, itd.  
✅ **Praktyka** - 4 ćwiczenia  

---

## Zasoby

- [MDN Text Basics](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/HTML_text_fundamentals)
- [Semantic HTML](https://www.w3schools.com/html/html5_semantic_elements.asp)

---

*Gotowy do Modułu 4? Nauczymy się Listy! 🚀*