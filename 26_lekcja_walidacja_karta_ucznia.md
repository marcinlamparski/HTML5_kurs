# 📄 KARTA PRACY — WALIDACJA HTML I ORGANIZACJA W3C
### Technikum Informatyczne | Klasa 3 | INF.03

**Imię i nazwisko:** ___________________________________  **Data:** _____________

---

## 📖 CZĘŚĆ TEORETYCZNA — PRZECZYTAJ UWAŻNIE

---

### 1. Czym jest W3C?

**W3C** (World Wide Web Consortium) to międzynarodowa organizacja non-profit założona w **1994 roku** przez **Tima Bernersa-Lee** — tego samego człowieka który wynalazł World Wide Web.

Siedziba: Massachusetts Institute of Technology (MIT), USA.

**Czym zajmuje się W3C:**
- tworzy i publikuje **standardy** (specyfikacje) dla technologii webowych
- decyduje jak powinny działać HTML, CSS, XML, SVG i inne technologie
- skupia ponad **400 organizacji** — w tym Microsoft, Google, Apple, Mozilla

**Najważniejsze standardy W3C:**
- **HTML5** — język znaczników stron internetowych
- **CSS3** — arkusze stylów
- **WCAG** — wytyczne dostępności (Web Content Accessibility Guidelines)
- **XML** — język znaczników danych

> 💡 Zapamiętaj na egzamin INF.03: „Zalecenia WCAG opracowała organizacja **W3C**"

---

### 2. Co to jest walidacja HTML?

**Walidacja** to proces sprawdzania czy kod HTML jest zgodny ze standardem W3C.

Walidator sprawdza między innymi:
- czy wszystkie tagi są poprawnie otwarte i zamknięte
- czy tagi są prawidłowo zagnieżdżone
- czy elementy zawierają wymagane atrybuty (np. `alt` na `<img>`)
- czy użyto poprawnego DOCTYPE
- czy atrybuty mają dozwolone wartości

**Dwa rodzaje komunikatów walidatora:**

```
ERROR   → błąd składniowy — KOD JEST NIEPOPRAWNY
          Przykład: niezamknięty tag, brak wymaganego atrybutu

WARNING → ostrzeżenie — kod działa, ale coś warto poprawić
          Przykład: brak atrybutu lang na <html>
```

---

### 3. Jak korzystać z walidatora W3C?

**Adres:** `https://validator.w3.org`

Trzy sposoby walidacji:

```
┌─────────────────────────────────────────────────────┐
│  Validate by URI     │ wpisujesz adres strony online │
├──────────────────────┼──────────────────────────────┤
│  Validate by         │ wklejasz gotowy kod HTML      │
│  File Upload         │ lub wysyłasz plik z dysku     │
├──────────────────────┼──────────────────────────────┤
│  Validate by         │ ← NAJCZĘŚCIEJ UŻYWANE         │
│  Direct Input        │ wklejasz kod bezpośrednio     │
└─────────────────────────────────────────────────────┘
```

**Wynik idealny:**

```
✅  Document checking completed. No errors or warnings to show.
```

---

### 4. Najczęstsze błędy walidacji — tabela

| Błąd | Przykład złego kodu | Poprawny kod |
|------|---------------------|--------------|
| Brak `alt` na obrazku | `<img src="foto.jpg">` | `<img src="foto.jpg" alt="opis">` |
| Niezamknięty tag | `<h1>Tytuł` | `<h1>Tytuł</h1>` |
| Brak `lang` na `<html>` | `<html>` | `<html lang="pl">` |
| Zły element w `<ul>` | `<ul><p>tekst</p></ul>` | `<ul><li>tekst</li></ul>` |
| Zduplikowane `id` | dwa elementy z `id="menu"` | każde `id` musi być unikalne |
| Brak `</td>` lub `</tr>` | niezamknięte komórki tabeli | prawidłowe zamknięcie tagów |
| Tag `<b>` zamiast `<strong>` | `<b>ważny</b>` | `<strong>ważny</strong>` |
| Przestarzały tag | `<center>`, `<font>` | użyj CSS zamiast nich |

---

### 5. Walidacja a egzamin INF.03

Na egzaminie praktycznym INF.03 egzaminator sprawdza m.in.:

- czy strona ma poprawny `<!DOCTYPE html>`
- czy `<html>` ma atrybut `lang`
- czy wszystkie obrazki mają atrybut `alt`
- czy tagi są prawidłowo zagnieżdżone i zamknięte
- czy kod przechodzi walidację W3C

> ⚠️ Dobra praktyka: **zawsze sprawdzaj plik przed zapisaniem na egzaminie!**
> Jeden niezamknięty tag może kosztować Cię punkty.

---

## ✏️ ZADANIE 1 — Walidacja własnego pliku

Otwórz `https://validator.w3.org` → zakładka **„Validate by Direct Input"**.

Wklej kod HTML z jednego ze swoich poprzednich ćwiczeń i zapisz wynik:

**Liczba błędów (errors):** _______

**Liczba ostrzeżeń (warnings):** _______

**Trzy pierwsze błędy które znalazł walidator:**

1. ___________________________________________________________________

2. ___________________________________________________________________

3. ___________________________________________________________________

**Po poprawkach — ponowna walidacja:**

Liczba błędów po poprawkach: _______

---

## ✏️ ZADANIE 2 — Znajdź i popraw błędy

Poniższy kod HTML zawiera **błędy**. Znajdź je wszystkie, zaznacz i popraw.
Następnie wklej poprawiony kod do walidatora — cel to wynik „No errors or warnings".

```html
<!DOCTYPE html>
<html>
<head>
    <title>Szkoła TechPlus</title>
</head>
<body>

    <h1>Witamy w TechPlus
    
    <nav>
        <a href="#">Strona główna</a>
        <a href="#">O szkole</a>
    </nav>

    <section>
        <h2>O naszej szkole</h2>
        <p>Kształcimy techników informatyków 
           od <strong>2005 roku</p>
        <img src="szkola.jpg">
    </section>

    <ul>
        <p>Kierunki kształcenia:</p>
        <li>Technik informatyk</li>
        <li>Technik programista</li>
    </ul>

    <table>
        <tr>
            <th>Przedmiot</th>
            <th>Nauczyciel</th>
        <tr>
            <td>HTML i CSS</td>
            <td>mgr Kowalski</td>
        </tr>
    </table>

    <footer>© 2025 TechPlus</footer>

</body>
</html>
```

**Tabela znalezionych błędów:**

| Nr | Linia (orientacyjnie) | Opis błędu | Poprawka |
|----|----------------------|------------|----------|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |
| 7 | | | |
| 8 | | | |
| 9 | | | |
| 10 | | | |
| 11 | | | |
| 12 | | | |
| 13 | | | |

**Wynik walidacji po poprawkach:** ________________________________

---

## ✏️ ZADANIE 3 — Pytania egzaminacyjne (odpowiedz ustnie lub pisemnie)

1. Jak nazywa się organizacja która opracowała zalecenia WCAG?

   ___________________________________________________________________

2. Co oznacza komunikat walidatora: *„Element img is missing required attribute alt"*?

   ___________________________________________________________________

3. Wymień dwie różnice między błędem (error) a ostrzeżeniem (warning) w walidatorze.

   ___________________________________________________________________

4. Dlaczego przeglądarka może wyświetlić stronę pomimo błędów w kodzie HTML?

   ___________________________________________________________________

5. Jak powinien wyglądać prawidłowy wynik walidacji strony?

   ___________________________________________________________________

---

## 📌 ŚCIĄGAWKA — NA ŚCIANĘ LUB DO ZESZYTU

```
WALIDACJA HTML — CHECKLISTA PRZED ZAPISANIEM PLIKU NA EGZAMINIE:

  ✅  <!DOCTYPE html> na początku pliku
  ✅  <html lang="pl"> — z atrybutem języka
  ✅  <meta charset="UTF-8"> w sekcji head
  ✅  <title> z treścią w sekcji head
  ✅  Wszystkie tagi zamknięte (h1, p, strong, em...)
  ✅  Każdy <img> ma atrybut alt=""
  ✅  Brak zduplikowanych id na stronie
  ✅  <ul> i <ol> zawierają tylko <li> (nie <p>, nie <div>)
  ✅  Tagi semantyczne zamiast <div> (header, nav, main, footer...)
  ✅  Walidator: "No errors or warnings to show" ✅
```
