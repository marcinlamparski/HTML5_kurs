# HTML5 - Moduł 4: Listy

## Wprowadzenie

Listy to podstawowy element struktury dokumentów HTML. Używamy ich do organizacji informacji - od menu nawigacyjnych po listy zadań. W HTML mamy trzy główne typy list[1][2].

**Czego się nauczysz w tym module:**
- ✅ Listy nienumerowane (`<ul>`)
- ✅ Listy numerowane (`<ol>`)
- ✅ Listy definicji (`<dl>`)
- ✅ Zagnieżdżanie list
- ✅ Best practices
- ✅ Praktyczne zastosowania

---

## Część 1: Listy Nienumerowane

```html
<ul>
    <li>Punkt 1</li>
    <li>Punkt 2</li>
    <li>Punkt 3</li>
</ul>
```

**Wynik:**
- Punkt 1
- Punkt 2
- Punkt 3

### Praktycznie

```html
<h2>Moje Hobby</h2>
<ul>
    <li>Czytanie</li>
    <li>Programowanie</li>
    <li>Gry komputerowe</li>
</ul>
```

---

## Część 2: Listy Numerowane

```html
<ol>
    <li>Pierwszy krok</li>
    <li>Drugi krok</li>
    <li>Trzeci krok</li>
</ol>
```

**Wynik:**
1. Pierwszy krok
2. Drugi krok
3. Trzeci krok

### Atrybuty

```html
<!-- Zaczynaj od 5 -->
<ol start="5">
    <li>Punkt 5</li>
    <li>Punkt 6</li>
</ol>

<!-- Cyfry rzymskie -->
<ol type="I">
    <li>I</li>
    <li>II</li>
</ol>

<!-- Litery -->
<ol type="A">
    <li>A</li>
    <li>B</li>
</ol>

<!-- Odwrotnie -->
<ol reversed>
    <li>Trzeci</li>
    <li>Drugi</li>
    <li>Pierwszy</li>
</ol>
```

---

## Część 3: Listy Definicji

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
</dl>
```

- `<dl>` - Definition List (lista definicji)
- `<dt>` - Definition Term (termin)
- `<dd>` - Definition Description (definicja)

---

## Część 4: Zagnieżdżanie List

```html
<ul>
    <li>Punkt 1
        <ul>
            <li>Podpunkt 1.1</li>
            <li>Podpunkt 1.2</li>
        </ul>
    </li>
    <li>Punkt 2
        <ol>
            <li>Podpunkt 2.1</li>
            <li>Podpunkt 2.2</li>
        </ol>
    </li>
</ul>
```

---

## Część 5: Praktyczne Zastosowania

### Menu Nawigacyjne

```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">O nas</a></li>
        <li><a href="/products">Produkty</a>
            <ul>
                <li><a href="/products/new">Nowe</a></li>
                <li><a href="/products/sale">Promocje</a></li>
            </ul>
        </li>
        <li><a href="/contact">Kontakt</a></li>
    </ul>
</nav>
```

### Instrukcja Krok po Kroku

```html
<h2>Jak Zainstalować Program</h2>
<ol>
    <li>Pobierz instalator ze strony</li>
    <li>Uruchom plik .exe</li>
    <li>Kliknij "Next" w każdym oknie</li>
    <li>Zaakceptuj warunki licencji</li>
    <li>Czekaj na zakończenie instalacji</li>
</ol>
```

### Słownik

```html
<dl>
    <dt>Responsywny Design</dt>
    <dd>Projekt który dostosowuje się do wielkości ekranu</dd>
    
    <dt>SEO</dt>
    <dd>Search Engine Optimization - optymalizacja dla wyszukiwarek</dd>
    
    <dt>API</dt>
    <dd>Application Programming Interface - interfejs komunikacji</dd>
</dl>
```

---

## Część 6: Ćwiczenia

### Ćwiczenie 1: Menu

Stwórz menu nawigacyjne dla strony sklepu internetowego:
- Główne kategorie (co najmniej 3)
- Każda kategoria ma podkategorie
- Wszystkie jako linki

### Ćwiczenie 2: Instrukcja

Utwórz instrukcję 5-10 kroków do zrobienia czegoś:
- Nagłówek
- Listy numerowane
- Paragraf wprowadzenia

### Ćwiczenie 3: Zagnieżdżone

Stwórz strukturę katalogów dysku jako zagnieżdżone listy.

### Ćwiczenie 4: Mieszane

Utwórz stronę zawierającą:
- Listę nienumerowaną
- Listę numerowaną
- Listę zagnieżdżaną
- Listę definicji

---

## Podsumowanie

W tym module nauczyliśmy się:

✅ **Listy nienumerowane** - `<ul>`  
✅ **Listy numerowane** - `<ol>`  
✅ **Listy definicji** - `<dl>`  
✅ **Zagnieżdżanie** - listy wewnątrz list  
✅ **Praktyczne aplikacje** - menu, instrukcje  
✅ **Atrybuty** - start, type, reversed  

---

*Gotowy do Modułu 5? Nauczymy się Linków i Nawigacji! 🚀*