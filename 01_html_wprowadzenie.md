# HTML5 - Moduł 1: Wprowadzenie do HTML5

## Wprowadzenie

HTML (HyperText Markup Language) to język znaczników używany do tworzenia stron internetowych. HTML5 to najnowsza wersja tego języka, wprowadzająca wiele nowych funkcjonalności i semantycznych elementów[1][2].

**Czego się nauczysz w tym module:**
- ✅ Historia HTML i HTML5
- ✅ Co to jest HTML i dlaczego go używać
- ✅ Struktura dokumentu HTML
- ✅ Podstawowe znaczniki
- ✅ Atrybuty tagów
- ✅ Validacja i standardy
- ✅ Najczęstsze błędy

---

## Część 1: Historia HTML

### Od HTML do HTML5

| Wersja | Rok | Najważniejsze Zmiany |
|--------|-----|---------------------|
| HTML | 1993 | Pierwsze specification |
| HTML 2.0 | 1995 | Standardyzacja |
| HTML 3.2 | 1997 | Tabele, applets |
| HTML 4.01 | 1999 | Stylesheets (CSS) |
| XHTML 1.0 | 2000 | XML-based |
| HTML5 | 2014 | Semantyka, API, multimedia |

### HTML5 - Lata Prracy

HTML5 był rozwijany przez **8 lat** (2004-2012) zanim został oficjalnie zatwierdzony w **2014 roku** przez **W3C** (World Wide Web Consortium)[1].

---

## Część 2: Co to Jest HTML?

### Definicja

HTML to **język znaczników** (nie język programowania!), który definiuje **strukturę i zawartość** dokumentów internetowych[1].

**Ważne Rozróżnienie:**

- 📄 **HTML** = Struktura i zawartość
- 🎨 **CSS** = Wygląd (kolory, rozmiary,Layout)
- ⚙️ **JavaScript** = Interaktywność i logika

### Jak Działa HTML?

```
HTML Dokument
    ↓
Przeglądarka Internetowa
    ↓
Interpretuje Znaczniki
    ↓
Wyświetla Stronę
```

Przeglądarka czyta znaczniki HTML i wyświetla je użytkownikowi w czytelnej formie.

---

## Część 3: Struktura Dokumentu HTML5

### Szablon HTML5

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tytuł Strony</title>
</head>
<body>
    <h1>Witaj Świecie!</h1>
    <p>Moja pierwsza strona internetowa.</p>
</body>
</html>
```

### Wyjaśnienie Każdej Części

#### `<!DOCTYPE html>` - Deklaracja Typu
- **Musi** być na początku dokumentu
- Mówi przeglądarce że to dokument HTML5
- Zawsze dokładnie taki sam

#### `<html lang="pl">` - Element Główny
- Opakowuje cały dokument
- `lang="pl"` oznacza że strona jest po polsku
- Pomagnie dostępności i SEO

#### `<head>` - Głowa Dokumentu
- **Nie wyświetla się** na stronie
- Zawiera metadane i konfigurację
- Linki do CSS, JavaScript
- Meta tagi

#### `<body>` - Ciało Dokumentu
- **Wyświetla się** na stronie
- Zawiera całą widoczną zawartość

---

## Część 4: Podstawowe Znaczniki

### Nagłówki

```html
<h1>Nagłówek 1 (GŁÓWNY - jeden na stronę)</h1>
<h2>Nagłówek 2 (Sekcje główne)</h2>
<h3>Nagłówek 3 (Podsekcje)</h3>
<h4>Nagłówek 4</h4>
<h5>Nagłówek 5</h5>
<h6>Nagłówek 6 (najmniejszy)</h6>
```

**Ważne:** Używaj nagłówków hierarchicznie! Nie skipuj poziomów.

### Paragrafy

```html
<p>To jest paragraf. Tekst może być długi.</p>
<p>Każda nowa zawartość to nowy element.</p>
```

### Tekst Specjale

```html
<strong>Tekst ważny (pogrubienie)</strong>
<em>Tekst podkreślony (kursywa)</em>
<b>Pogrubienie (tylko stylistyka)</b>
<i>Kursywa (tylko stylistyka)</i>
<br> <!-- Łamanie linii -->
<hr> <!-- Linia pozioma -->
```

### Linki

```html
<a href="https://www.google.com">Link do Google</a>
<a href="/strona.html">Link wewnętrzny</a>
<a href="#sekcja">Link do sekcji na stronie</a>
```

### Obrazy

```html
<img src="obraz.jpg" alt="Opis obrazu">
<img src="/images/foto.png" alt="Moje zdjęcie" width="300" height="200">
```

### Listy

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
```

---

## Część 5: Atrybuty Tagów

Atrybuty dodają informacje do znaczników.

### Składnia

```html
<tag atrybut="wartość">Zawartość</tag>
```

### Uniwersalne Atrybuty

```html
<!-- ID - Unikalne identyfikatory -->
<h1 id="nagłówek-główny">Moja Strona</h1>

<!-- Class - Klasy (może być wiele) -->
<p class="tekst-główny tekst-ważny">Paragraf</p>

<!-- Title - Tooltip przy najedaniu -->
<a href="#" title="Kliknij mnie">Link</a>

<!-- Data Attributes - Własne dane -->
<div data-user-id="123" data-role="admin">Panel Admin</div>

<!-- Style - Styl inline (unikaj!) -->
<p style="color: red;">Czerwony tekst</p>

<!-- Lang - Język -->
<p lang="en">This is English text</p>
```

### Atrybuty Specyficzne

```html
<!-- href - adres linku -->
<a href="https://example.com">Link</a>

<!-- src - źródło obrazu/skryptu -->
<img src="obraz.jpg">
<script src="skrypt.js"></script>

<!-- alt - alternatywny tekst -->
<img src="obraz.jpg" alt="Opis dla niewidomych">

<!-- disabled - wyłączenie elementu -->
<button disabled>Wyłączony przycisk</button>

<!-- required - pole wymagane -->
<input type="text" required>
```

---

## Część 6: Meta Tagi

Meta tagi zawarte w `<head>` konfigurują stronę.

```html
<!-- Kodowanie znaków -->
<meta charset="UTF-8">

<!-- Viewport dla urządzeń mobilnych (WAŻNE!) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Opis strony (wyświetla się w Google) -->
<meta name="description" content="To jest moja fantastyczna strona">

<!-- Słowa kluczowe -->
<meta name="keywords" content="html, nauka, kurs">

<!-- Autor -->
<meta name="author" content="Jan Kowalski">

<!-- Refresh co 30 sekund -->
<meta http-equiv="refresh" content="30">

<!-- Open Graph - dla mediów społecznych -->
<meta property="og:title" content="Moja Strona">
<meta property="og:image" content="obraz.jpg">
<meta property="og:description" content="Opis">
```

---

## Część 7: Walidacja i Standardy

### Czemu Walidacja?

- ✅ Pewna, że kod jest prawidłowy
- ✅ Lepsza kompatybilność
- ✅ Lepszy SEO
- ✅ Łatwiejsze debugowanie

### Jak Walidować?

1. Idź na https://validator.w3.org/
2. Wklej swoją stronę HTML
3. Kliknij "Validate"
4. Czytaj błędy i je naprawiaj!

### Walidacja Offline

```bash
# Zainstaluj HTML validator
npm install -g html-validator-cli

# Waliduj plik
html-validator index.html
```

---

## Część 8: Najczęstsze Błędy

### Błąd 1: Brakujący DOCTYPE

```html
<!-- ❌ ŹLE -->
<html>
    <head>...</head>
</html>

<!-- ✅ DOBRZE -->
<!DOCTYPE html>
<html>
    <head>...</head>
</html>
```

### Błąd 2: Niezamknięte Tagi

```html
<!-- ❌ ŹLE -->
<p>Paragraf bez zamknięcia

<!-- ✅ DOBRZE -->
<p>Paragraf</p>
```

### Błąd 3: Zły Porządek Atrybutów

```html
<!-- ❌ ŹLE (lub ciężkie do czytania) -->
<img alt="Obraz" src="obraz.jpg" width=300 height=200>

<!-- ✅ DOBRZE -->
<img src="obraz.jpg" alt="Obraz" width="300" height="200">
```

### Błąd 4: Ignorowanie Meta Viewport

```html
<!-- ❌ ŹLE - strona nie będzie responsywna -->
<html>
    <head>
        <title>Moja Strona</title>
    </head>
</html>

<!-- ✅ DOBRZE -->
<html>
    <head>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Moja Strona</title>
    </head>
</html>
```

### Błąd 5: Zagnieżdżanie Linków

```html
<!-- ❌ ŹLE -->
<a href="https://example.com">
    Tekst
    <a href="https://inne.com">Link wewnątrz linku</a>
</a>

<!-- ✅ DOBRZE -->
<a href="https://example.com">Link 1</a>
<a href="https://inne.com">Link 2</a>
```

---

## Część 9: HTML5 vs HTML4

### Co Nowego w HTML5?

```html
<!-- Semantyczne elementy (NOWE) -->
<header>, <nav>, <article>, <section>, <aside>, <footer>

<!-- Multimedia (NOWE) -->
<audio>, <video>, <canvas>

<!-- Formularze (ULEPSZONE) -->
<input type="email">
<input type="date">
<input type="range">

<!-- Globalne Atrybuty (NOWE) -->
<div contenteditable="true">Edytowalny tekst</div>
<div draggable="true">Przeciągalny element</div>

<!-- Data Attributes (NOWE) -->
<div data-user-id="123"></div>
```

---

## Część 10: Praktyczne Przykłady

### Przykład 1: Prosta Strona

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moja Pierwsza Strona</title>
</head>
<body>
    <h1>Witaj na Mojej Stronie!</h1>
    <p>To jest moja pierwsza strona HTML.</p>
    <p>Jest to bardzo proste.</p>
    
    <h2>Co to HTML?</h2>
    <p>HTML to język do tworzenia stron internetowych.</p>
    
    <h2>Linki</h2>
    <ul>
        <li><a href="https://www.google.com">Google</a></li>
        <li><a href="https://www.w3schools.com">W3Schools</a></li>
    </ul>
</body>
</html>
```

### Przykład 2: Strona z Obrazami

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Galeria</title>
</head>
<body>
    <h1>Moja Galeria Zdjęć</h1>
    
    <h2>Zdjęcie 1</h2>
    <img src="zdjecie1.jpg" alt="Krajobraz">
    <p>Piękne zdjęcie krajobrazu.</p>
    
    <h2>Zdjęcie 2</h2>
    <img src="zdjecie2.jpg" alt="Morze">
    <p>Zdjęcie morza.</p>
</body>
</html>
```

---

## Część 11: Ćwiczenia

### Ćwiczenie 1: Moja Pierwsza Strona

Utwórz plik `index.html` zawierający:
1. DOCTYPE html
2. Nagłówek `<h1>` z Twoim imieniem
3. Paragraf o sobie (przynajmniej 2 zdania)
4. Listę Twoich hobby (5 pozycji)
5. Link do Twojej ulubionej strony

**Wskazówka:** Użyj tagu `<ul>` dla listy i `<a>` dla linku.

### Ćwiczenie 2: Validacja

Sprawdź czy Twój `index.html` z Ćwiczenia 1 jest validny:
1. Idź na https://validator.w3.org/
2. Upload swój plik
3. Popraw wszystkie błędy

### Ćwiczenie 3: Tagi i Atrybuty

Utwórz HTML zawierający:
1. Tytuł strony w `<title>`
2. Meta tag viewport
3. Nagłówek z `id="main-header"`
4. Paragraf z `class="highlight"`
5. Link z atrybutem `title="Tooltip"`
6. Obraz z atrybutem `alt`

### Ćwiczenie 4: Rzeczywista Strona

Stwórz prostą stronę cv zawierającą:
1. Nagłówek ze Twoim imieniem
2. Sekcje: O mnie, Doświadczenie, Umiejętności
3. Listy punktów
4. Linki do profili (LinkedIn, GitHub, etc.)

---

## Podsumowanie

W tym module nauczyliśmy się:

✅ **Historia HTML** - od HTML do HTML5  
✅ **Co to HTML** - język znaczników dla internetu  
✅ **Struktura** - DOCTYPE, head, body  
✅ **Podstawowe Tagi** - h1-h6, p, a, img, listy  
✅ **Atrybuty** - id, class, title, data-*  
✅ **Meta Tagi** - charset, viewport, og:*  
✅ **Walidacja** - W3C Validator  
✅ **Błędy** - co unikać  

---

## Zasoby Dodatkowe

- [MDN HTML Introduction](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)
- [W3Schools HTML Tutorial](https://www.w3schools.com/html/)
- [HTML5 Standard](https://html.spec.whatwg.org/)
- [W3C Validator](https://validator.w3.org/)

---

*Jesteś gotowy do Modułu 2? Nauczymy się Semantyki i Struktury HTML5! 🚀*