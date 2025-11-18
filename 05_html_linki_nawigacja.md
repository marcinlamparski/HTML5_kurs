# HTML5 - Moduł 5: Linki i Nawigacja

## Wprowadzenie

Linki to serce internetu - łączą strony między sobą. W tym module nauczysz się wszystkiego o tworzeniu linków - od linków zewnętrznych po anchory i nawigację[1][2].

**Czego się nauczysz w tym module:**
- ✅ Tag `<a>` i atrybuty
- ✅ Linki zewnętrzne
- ✅ Linki wewnętrzne
- ✅ Anchory (skoki na stronie)
- ✅ Linki specjalne (mailto, tel)
- ✅ Dostępność linków
- ✅ Nawigacja

---

## Część 1: Podstawy Linku

```html
<a href="https://www.google.com">Kliknij tutaj</a>
```

- `href` - URL do którego prowadzi link
- Tekst między znacznikami to **tekst linku** (widoczny dla użytkownika)

---

## Część 2: Typy Linków

### Link Zewnętrzny

```html
<a href="https://www.example.com">Zewnętrzny link</a>
```

**Dobre praktyki:**
- Zawsze używaj pełnego URL (`https://`)
- Otwórz w nowej karcie dla zewnętrznych: `target="_blank"`

```html
<a href="https://www.example.com" target="_blank">
    Otwórz w nowej karcie
</a>
```

### Link Wewnętrzny

```html
<a href="/o-nas.html">O nas</a>
<a href="index.html">Home</a>
<a href="/blog/post-1.html">Artykuł</a>
```

### Względne URL

```html
<!-- Z tego samego folderu -->
<a href="strona.html">Link</a>

<!-- Z podfolderu -->
<a href="blog/post.html">Link</a>

<!-- Z folderu wyżej -->
<a href="../index.html">Link</a>
```

---

## Część 3: Anchory i Skoki

### Ustawienie Anchor

```html
<h2 id="sekcja-1">Sekcja 1</h2>
<p>Zawartość sekcji 1...</p>

<h2 id="sekcja-2">Sekcja 2</h2>
<p>Zawartość sekcji 2...</p>
```

### Link do Anchor

```html
<!-- Link do anchor na tej stronie -->
<a href="#sekcja-1">Skocz do sekcji 1</a>
<a href="#sekcja-2">Skocz do sekcji 2</a>

<!-- Link do anchor na innej stronie -->
<a href="blog.html#post-1">Link do postu 1</a>
```

### Spis treści

```html
<nav id="toc">
    <h2>Spis Treści</h2>
    <ul>
        <li><a href="#intro">Wprowadzenie</a></li>
        <li><a href="#part1">Część 1</a></li>
        <li><a href="#part2">Część 2</a></li>
        <li><a href="#conclusion">Zakończenie</a></li>
    </ul>
</nav>

<section id="intro">
    <h2>Wprowadzenie</h2>
    <p>...</p>
</section>

<section id="part1">
    <h2>Część 1</h2>
    <p>...</p>
</section>
```

---

## Część 4: Linki Specjalne

### E-mail

```html
<a href="mailto:contact@example.com">Wyślij e-mail</a>

<!-- Z tematem -->
<a href="mailto:contact@example.com?subject=Pytanie">
    Wyślij pytanie
</a>

<!-- Z cc, bcc, body -->
<a href="mailto:contact@example.com?cc=other@example.com&subject=Hello&body=Wiadomość">
    Wyślij e-mail z kopią
</a>
```

### Telefon

```html
<a href="tel:+48123456789">Zadzwoń: +48 123 456 789</a>
```

### SMS

```html
<a href="sms:+48123456789">Wyślij SMS</a>
```

### Pobieranie Pliku

```html
<a href="/files/dokument.pdf" download>Pobierz PDF</a>
<a href="/images/foto.jpg" download="moje-foto.jpg">
    Pobierz zdjęcie
</a>
```

---

## Część 5: Atrybuty Linków

```html
<!-- target - gdzie otworzyć -->
<a href="..." target="_blank">Nowa karta</a>
<a href="..." target="_self">Ta karta (domyślnie)</a>

<!-- rel - relacja do dokumentu -->
<a href="..." rel="nofollow">Nie śledzony (SEO)</a>
<a href="..." rel="external">Link zewnętrzny</a>

<!-- title - tooltip -->
<a href="..." title="Przejdź do strony głównej">Home</a>

<!-- type - typ dokumentu -->
<a href="dokument.pdf" type="application/pdf">PDF</a>
```
| Wartość          | Znaczenie                                                  | Zastosowanie                                   |
| ---------------- | ---------------------------------------------------------- | ---------------------------------------------- |
| rel="nofollow"   | Wyszukiwarka nie powinna podążać za tym linkiem            | Linki do reklam, komentarze, untrusted content |
| rel="external"   | Link prowadzi na zewnętrzną stronę                         | Informacja dla skryptów JavaScript             |
| rel="noopener"   | Bezpieczeństwo — nowa karta nie ma dostępu dowindow.opener | Ochrona przytarget="_blank"                    |
| rel="noreferrer" | Nie wysyła informacji o pochodzeniu                        | Prywatność użytkownika                         |
---

## Część 6: Nawigacja

### Proste Menu

```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">O nas</a></li>
        <li><a href="/services">Usługi</a></li>
        <li><a href="/contact">Kontakt</a></li>
    </ul>
</nav>
```

### Menu z Podkategoriami

```html
<nav>
    <ul>
        <li>
            <a href="/products">Produkty</a>
            <ul>
                <li><a href="/products/electronics">Elektronika</a></li>
                <li><a href="/products/clothing">Odzież</a></li>
                <li><a href="/products/books">Książki</a></li>
            </ul>
        </li>
        <li><a href="/contact">Kontakt</a></li>
    </ul>
</nav>
```

### Breadcrumbs

```html
<nav aria-label="Breadcrumb">
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/products">Produkty</a></li>
        <li><a href="/products/electronics">Elektronika</a></li>
        <li aria-current="page">Monitor</li>
    </ul>
</nav>
```

---

## Część 7: Dostępność Linków

### Dobry Tekst Linku

```html
<!-- ❌ ŹLE -->
<a href="/post">Kliknij tutaj</a>

<!-- ✅ DOBRZE -->
<a href="/post">Przeczytaj artykuł o HTML5</a>
```

### Title Attribute

```html
<a href="/blog" title="Przejdź do naszego bloga">Blog</a>
```

### ARIA Labels

```html
<a href="#" aria-label="Facebook">
    <i class="fab fa-facebook"></i>
</a>
```

---

## Część 8: Ćwiczenia

### Ćwiczenie 1: Nawigacja
Cel
Stworzenie pełnofunkcjonalnej nawigacji dla witryny internetowej z hierarchiczną strukturą menu.

Wymagania
Nawigacja powinna zawierać następujące elementy:

Home — link do strony głównej

O nas — link do podstrony

Usługi — kategoria z trzema podkategoriami

Portfolio — kategoria z pięcioma projektami

Kontakt — link do strony kontaktowej

Wskazówki do Implementacji
Zamiast tworzyć proste linki w linii, skorzystaj z elementu semantycznego <nav> oraz struktury zagnieżdżonych list (<ul> i <li>). Zagnieżdżone listy pozwolą na utworzenie menu wielopoziomowego

Stwórz nawigację dla strony ze strukturą:

- Home
- O nas
- Usługi (z 3 podkategoriami)
- Portfolio (z 5 projektami)
- Kontakt
```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li>
            <a href="/uslugi">Usługi</a>
            <ul>
                <li><a href="/uslugi/web">Web Design</a></li>
                <li><a href="/uslugi/seo">SEO</a></li>
                <li><a href="/uslugi/marketing">Marketing</a></li>
            </ul>
        </li>
    </ul>
</nav>
```

### Ćwiczenie 2: Spis Treści
Wszystko tworzymy w jednym pliku, linki do anchor
Utwórz artykuł z:
- Spis treści na górze
- Minimum 5 sekcji
- Każda sekcja ma anchor
- Linki TOC skaczą do sekcji

### Ćwiczenie 3: Formularz Kontaktowy

Stwórz linki do kontaktu:
- E-mail z tematem
- Numer telefonu
- SMS link
- Linki do social media

### Ćwiczenie 4: Mieszane Linki

Utwórz stronę zawierającą:
- Linki wewnętrzne
- Linki zewnętrzne
- Anchory
- Linki specjalne
- Pobieranie pliku

---

## Podsumowanie

W tym module nauczyliśmy się:

✅ **Podstawy linków** - tag `<a>`  
✅ **Linki zewnętrzne i wewnętrzne**  
✅ **Anchory i skoki** - nawigacja na stronie  
✅ **Linki specjalne** - mailto, tel, SMS  
✅ **Atrybuty** - target, rel, title  
✅ **Nawigacja** - menu i breadcrumbs  
✅ **Dostępność** - dobry tekst linku  

---

*Gotowy do Modułu 6? Nauczymy się Multimedia! 🚀*
