# HTML5 - Moduł 7: Tabele

## Wprowadzenie

Tabele to strukturalny sposób na prezentację danych tabelarycznych. W tym module nauczysz się tworzyć dostępne i dobrze sformatowane tabele[1][2].

**Czego się nauczysz w tym module:**
- ✅ Struktura tabeli
- ✅ Nagłówki i dane
- ✅ Scalanie komórek
- ✅ Grupy wierszy
- ✅ Dostępność tabel
- ✅ Praktyczne przykłady
- ✅ Best practices

---

## Część 1: Podstawowa Struktura

```html
<table>
    <tr>
        <th>Nagłówek 1</th>
        <th>Nagłówek 2</th>
    </tr>
    <tr>
        <td>Dane 1</td>
        <td>Dane 2</td>
    </tr>
    <tr>
        <td>Dane 3</td>
        <td>Dane 4</td>
    </tr>
</table>
```

- `<table>` - kontener tabeli
- `<tr>` - wiersz
- `<th>` - nagłówek (zwykle pogrubiony)
- `<td>` - komórka z danymi

---

## Część 2: Pełna Struktura

```html
<table>
    <thead>
        <tr>
            <th>Imię</th>
            <th>Nazwisko</th>
            <th>Wiek</th>
        </tr>
    </thead>
    
    <tbody>
        <tr>
            <td>Jan</td>
            <td>Kowalski</td>
            <td>25</td>
        </tr>
        <tr>
            <td>Maria</td>
            <td>Nowak</td>
            <td>30</td>
        </tr>
    </tbody>
    
    <tfoot>
        <tr>
            <th>Razem</th>
            <td colspan="2">2 osoby</td>
        </tr>
    </tfoot>
</table>
```

- `<thead>` - nagłówek tabeli
- `<tbody>` - ciało tabeli
- `<tfoot>` - stopka tabeli

---

## Część 3: Scalanie Komórek

### Colspan - Scalanie Kolumn

```html
<table border="1">
    <tr>
        <th>Miesiąc</th>
        <th colspan="2">Sprzedaż</th>
    </tr>
    <tr>
        <td>Styczeń</td>
        <td>1000 zł</td>
        <td>1200 zł</td>
    </tr>
</table>
```

### Rowspan - Scalanie Wierszy

```html
<table border="1">
    <tr>
        <th rowspan="2">Miesiąc</th>
        <th>Wersja A</th>
        <th>Wersja B</th>
    </tr>
    <tr>
        <td>1000 zł</td>
        <td>1200 zł</td>
    </tr>
</table>
```

---

## Część 4: Atrybuty Tabeli

```html
<!-- Obramowanie -->
<table border="1">

<!-- Padding komórek -->
<table cellpadding="10">

<!-- Odstęp między komórkami -->
<table cellspacing="5">

<!-- Kombinacja -->
<table border="1" cellpadding="10" cellspacing="0">
```

---

## Część 5: Praktyczne Przykłady

### Tabela Cenników

```html
<table>
    <thead>
        <tr>
            <th>Plan</th>
            <th>Cena/Miesiąc</th>
            <th>Opis</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Starter</td>
            <td>9.99 zł</td>
            <td>Dla początkujących</td>
        </tr>
        <tr>
            <td>Professional</td>
            <td>29.99 zł</td>
            <td>Dla profesjonalistów</td>
        </tr>
        <tr>
            <td>Enterprise</td>
            <td>99.99 zł</td>
            <td>Dla firm</td>
        </tr>
    </tbody>
</table>
```

### Rozkład Jazdy

```html
<table>
    <thead>
        <tr>
            <th>Godzina</th>
            <th>Malinki</th>
            <th>Piaseczno</th>
            <th>Milanówek</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>6:00</td>
            <td>6:10</td>
            <td>6:20</td>
        </tr>
        <tr>
            <td>7:00</td>
            <td>7:10</td>
            <td>7:20</td>
        </tr>
    </tbody>
</table>
```

### Harmonogram

```html
<table>
    <thead>
        <tr>
            <th>Poniedziałek</th>
            <th>Wtorek</th>
            <th>Środa</th>
            <th>Czwartek</th>
            <th>Piątek</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Matematyka</td>
            <td>Historia</td>
            <td>Polski</td>
            <td>Fizyka</td>
            <td>Informatyka</td>
        </tr>
    </tbody>
</table>
```

---

## Część 6: Dostępność Tabel

### Caption

```html
<table>
    <caption>Sprzedaż produktów 2024</caption>
    <tr>
        <th>Produkt</th>
        <th>Ilość</th>
        <th>Wartość</th>
    </tr>
    <!-- Dane -->
</table>
```

### Scope Attribute

```html
<table>
    <thead>
        <tr>
            <th scope="col">Imię</th>
            <th scope="col">Nazwisko</th>
            <th scope="col">Wiek</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">1</th>
            <td>Jan</td>
            <td>25</td>
        </tr>
    </tbody>
</table>
```

---

## Część 7: Ćwiczenia

### Ćwiczenie 1: Prosta Tabela

Stwórz tabelę z:
- Co najmniej 3 wierszami i 4 kolumnami
- thead, tbody
- Dane sprzedażowe (produkt, ilość, cena)

### Ćwiczenie 2: Scalanie

Utwórz tabelę zawierającą:
- Scalane kolumny (colspan)
- Scalane wiersze (rowspan)
- Przynajmniej 2 scalenia każdego typu

### Ćwiczenie 3: Plan lekcji

Stwórz rozkład zajęć:
- Dni tygodnia jako kolumny
- Godziny jako wiersze
- Nazwy przedmiotów
- Scalania gdzie się pokrywają

### Ćwiczenie 4: Dane Biznesowe

Utwórz tabelę danych biznesowych:
- Caption
- Scope attributes
- thead, tbody, tfoot
- Podsumowanie na dole

---

## Best Practices

✅ Zawsze używaj `<thead>` i `<tbody>`  
✅ Używaj `<th>` dla nagłówków  
✅ Dodaj `<caption>` do tabeli  
✅ Używaj `scope` dla dostępności  
✅ Nie używaj tabel do layoutu!  
✅ Nie scalaj zbyt dużo komórek  
✅ Zawsze waliduj HTML  

---

*Gotowy do Modułu 8? Nauczymy się Formularzy! 🚀*

[Miejce na pliki kl 3](https://www.dropbox.com/request/Xc4w0xXrdPg3PYDKjpUd)
