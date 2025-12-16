# HTML5 - Moduł 8: Formularze - Część 1 (Podstawy)

## Wprowadzenie

Formularze to sposób na zbieranie danych od użytkowników. To jeden z najważniejszych elementów stron internetowych. W tym module nauczysz się tworzyć podstawowe formularze i rozumieć jak działają.

**Czego się nauczysz:**
- ✅ Tag `<form>` i atrybuty
- ✅ Strukturę formularza
- ✅ Atrybuty `action` i `method`
- ✅ Znaczenie `<form>` dla wysyłania danych
- ✅ Pierwsze praktyczne przykłady

---

## Część 1: Podstawy Formu

```html
<form action="/submit" method="POST">
    <!-- Pola -->
    <button type="submit">Wyślij</button>
</form>
```

| Atrybut | Opis |
|---------|------|
| `action` | Określa adres URL, na który będą wysłane dane formularza. Może to być skrypt po stronie serwera (np. PHP, Node.js) lub API |
| `method` | Definiuje sposób wysłania danych. **GET** - dane widoczne w URL (dla danych niezabezpieczonych). **POST** - dane wysyłane w treści żądania (bardziej bezpieczne, dla haseł, danych wrażliwych) |

---

### Dlaczego Wszystkie Pola Zamykają Się w `<form></form>`?

Świetne pytanie! 🤔 Tag `<form>` jest **kluczowy**. Oto dlaczego:

**1. Wysyłanie Danych** 📤
- Tylko pola WEWNĄTRZ `<form>` będą wysłane na serwer
- Bez `<form>` przeglądarka nie wie co wysłać
- Atrybut `action` mówi dokąd wysłać dane

**2. Walidacja HTML5** ✅
- Walidacja (`required`, `minlength`, `pattern`) działa TYLKO w `<form>`
- Przeglądarka sprawdza pola PRZED wysłaniem

**3. Logiczne Grupowanie** 🏗️
- Na jednej stronie może być wiele formularzy
- Każdy `<form>` to osobne wysłanie danych

**4. Przyciski Submit/Reset** 🔘
- Przycisk `type="submit"` wysyła zawartość `<form>`
- Przycisk `type="reset"` czyści pola tego `<form>`

```html
<!-- ❌ ŹLE - Bez <form> -->
<input type="text" name="email">
<button type="submit">Wyślij</button>
<!-- Przycisk nic nie robi! -->

<!-- ✅ DOBRZE - Z <form> -->
<form action="/submit" method="POST">
    <input type="text" name="email">
    <button type="submit">Wyślij</button>
    <!-- Przycisk wysyła dane -->
</form>
```

---

## Część 2: Pola Tekstowe

### Input Type="text"

```html
<input type="text" name="imie" placeholder="Wpisz imię">
```

**Do czego służy:** Podstawowe pole do wpisywania tekstu (imiona, nazwiska, nazwy użytkownika itp.). Przyjmuje dowolny tekst bez ograniczeń.

| Użycie | Opis |
|--------|------|
| Imiona, nazwiska | Zbieranie danych osobowych |
| Nazwy użytkownika | Logowanie i rejestracja |
| Zwykłe dane tekstowe | Każdy tekst, który nie wymaga specjalnego formatu |

---

### Email

```html
<input type="email" name="email" required>
```

**Do czego służy:** Pole specjalistyczne do wpisywania adresów e-mail. Przeglądarka automatycznie sprawdza czy format e-maila jest poprawny (musi zawierać `@` i domenę). Na urządzeniach mobilnych pojawia się klawiatura z znakiem `@`.

| Cechy | Opis |
|-------|------|
| Walidacja formatu | Przeglądarka sprawdza czy e-mail jest prawidłowy |
| Mobilna klawiatura | Na telefonach pojawia się specjalna klawiatura z `@` |
| Wymagane | Zwykle oznacza się jako wymagane (required) |

---

### Password

```html
<input type="password" name="haslo" required>
```

**Do czego służy:** Pole do wpisywania haseł. Znaki są ukryte (pokazywane jako kropki lub gwiazdki) dla bezpieczeństwa. Nikt patrzący przez ramię nie zobaczy hasła.

| Cechy | Opis |
|-------|------|
| Ukryte znaki | Każda litera wyświetlana jako `●` lub `*` |
| Bezpieczeństwo | Ochrona przed podsłuchiwaniem |
| Zalecenie | Zawsze używaj z `required` |

---

### Number

```html
<input type="number" name="wiek" min="18" max="100">
```

**Do czego służy:** Pole do wpisywania liczb. Przeglądarka waliduje czy wpisana wartość jest liczbą. Na mobilnych urządzeniach pojawia się klawiatura numeryczna.

| Atrybut | Opis |
|---------|------|
| `min` | Minimalna dozwolona wartość (np. wiek minimum 18 lat) |
| `max` | Maksymalna dozwolona wartość (np. maksymalny wiek 100 lat) |
| `step` | Krok zwiększania (np. step="5" - zwiększa co 5) |

**Przykład:** Wiek, ilość produktów, liczba pokojów w domu

---

### Date

```html
<input type="date" name="data">
```

**Do czego służy:** Pole do wyboru daty. Przeglądarka wyświetla picker (kalendarz) gdzie użytkownik może wybrać datę. Data jest przechowywana w formacie YYYY-MM-DD.

| Zastosowanie | Opis |
|--------------|------|
| Data urodzenia | Rejestracja użytkownika |
| Data wylotu | Rezerwacje lot, hoteli |
| Termin ważności | Uprawnienia, certyfikaty |
| Data spotkania | Umówienie terminu wizyty |

---

### Time

```html
<input type="time" name="godzina">
```

**Do czego służy:** Pole do wyboru godziny. Przeglądarka wyświetla selektor czasu (godzina:minuta). Format 24-godzinny.

| Zastosowanie | Opis |
|--------------|------|
| Godzina spotkania | Rezerwacja wizyty o konkretnej godzinie |
| Czas pracy | Zapisanie godzin pracy |
| Przypomnienie | Ustawienie alarmu lub powiadomienia |

---

### Color

```html
<input type="color" name="kolor" value="#FF0000">
```

**Do czego służy:** Pole do wyboru koloru. Przeglądarka wyświetla color picker (paletę kolorów). Wartość jest przechowywana w formacie heksadecymalnym (#RRGGBB).

| Zastosowanie | Opis |
|--------------|------|
| Motyw strony | Pozwól użytkownikowi wybrać ulubiony kolor |
| Personalizacja | Zmiana koloru logo, tła, interfejsu |
| Dane o produktach | Wybór koloru towaru |

---

### Range

```html
<input type="range" name="volume" min="0" max="100" value="50">
```

**Do czego służy:** Pole do wyboru wartości za pomocą suwaka. Użytkownik przesuwając suwak wybiera wartość z zakresu min-max. Powszechnie używane do regulacji głośności, jasności czy powiększenia.

| Atrybut | Opis |
|---------|------|
| `min` | Minimalna wartość zakresu |
| `max` | Maksymalna wartość zakresu |
| `value` | Wartość początkowa suwaka |
| `step` | Krok zwiększania przy każdym ruchu |

**Przykład:** Głośność, jasność ekranu, filtrowanie ceny produktów

---

### URL

```html
<input type="url" name="strona">
```

**Do czego służy:** Pole do wpisywania adresów internetowych (URL). Przeglądarka sprawdza czy format URL jest prawidłowy (musi zawierać `http://` lub `https://`). Na mobilnych urządzeniach pojawia się klawiatura z możliwością szybkiego wpisania `.com`.

| Walidacja | Opis |
|-----------|------|
| Format | Sprawdzenie czy URL zaczyna się od `http://` lub `https://` |
| Domena | Sprawdzenie czy zawiera domenę (np. example.com) |

---

### Tel

```html
<input type="tel" name="telefon">
```

**Do czego służy:** Pole do wpisywania numerów telefonu. Na mobilnych urządzeniach pojawia się klawiatura numeryczna. Przeglądarka nie waliduje formatu (bo jest wiele formatów międzynarodowych), ale wspomaga wpisywanie.

| Zastosowanie | Opis |
|--------------|------|
| Kontakt do klienta | Zbieranie numeru telefonu |
| Pomoc techniczna | Callback do obsługi klienta |
| Weryfikacja | Wysłanie kodu SMS |

---

### Search

```html
<input type="search" name="szukaj">
```

**Do czego służy:** Pole do wpisywania zapytań wyszukiwania. Funkcjonalnie jest bardzo podobne do `type="text"`, ale semantycznie wskazuje że pole służy do wyszukiwania. Na niektórych przegląrkach ma przycisk `×` do szybkiego wyczyszczenia.

| Zastosowanie | Opis |
|--------------|------|
| Wyszukiwarka | Szukanie produktów w sklepie |
| Artykuły | Szukanie artykułu na blogu |
| Filtry | Wyszukiwanie w bazie danych |

---

## Część 3: Textarea

```html
<textarea name="wiadomosc" rows="5" cols="40"></textarea>

<!-- Lepiej z CSS -->
<textarea name="wiadomosc" rows="5"></textarea>
```

**Do czego służy:** Wielolinijkowe pole tekstowe dla dłuższych tekstów. W przeciwieństwie do `<input type="text">`, `<textarea>` może zawierać wiele linii tekstu i przechowywać znacznie większą ilość danych.

| Atrybut | Opis |
|---------|------|
| `rows` | Liczba widocznych linii w polu |
| `cols` | Liczba widocznych znaków w jednej linii (UWAGA: lepiej stosować CSS) |
| Tekst między tagami | Domyślna zawartość pola |

**Przykład:** Opinie, komentarze, wiadomości, opis produktu, uwagi, pytania do obsługi

---

## Część 4: Przyciski

```html
<!-- Submit - wysyła formularz -->
<button type="submit">Wyślij</button>

<!-- Reset - zeruje wszystkie pola -->
<button type="reset">Wyczyść</button>

<!-- Zwykły przycisk - do JavaScript -->
<button type="button">Kliknij mnie</button>
```

| Typ Przycisku | Opis | Zastosowanie |
|--------------|------|--------------|
| `type="submit"` | Wysyła formularz na serwer | Wysłanie danych, zatwierdzenie formularza |
| `type="reset"` | Zeruje wszystkie pola formularza do stanu początkowego | Czyszczenie formularza, powrót do początku |
| `type="button"` | Zwykły przycisk - nie wysyła formularza, wymaga JavaScript | Akcje dodatkowe, obliczenia, ukrywanie/pokazywanie pól |

**Dobra praktyka:** Zawsze używaj `type="submit"` dla wysyłania i `type="reset"` do czyszczenia. Przyciski zwykłe rzadko są potrzebne w formularzu.

---

## Część 5: Praktyczny Przykład - Formularz Logowania

```html
<form action="/login" method="POST">
    <h2>Logowanie</h2>
    
    <label for="username">Nazwa użytkownika:</label>
    <input id="username" type="text" name="username" required placeholder="Wpisz nazwę">
    
    <label for="password">Hasło:</label>
    <input id="password" type="password" name="password" required placeholder="Wpisz hasło">
    
    <button type="submit">Zaloguj</button>
    <button type="reset">Wyczyść</button>
</form>
```

**Elementy:**
- `username` - nazwa użytkownika (type="text")
- `password` - hasło ukryte (type="password")
- Oba pola wymagane (required)
- Dwa przyciski: wysyłanie i czyszczenie

---

---

## 📋 ZADANIA PRAKTYCZNE - Część 1

### Zadanie 1: Pierwszy Formularz 🎯
**Cel:** Stworzyć prosty formularz rejestracji

Utwórz formularz zawierający:
- Pole tekstowe dla imienia
- Pole email
- Pole password
- Przycisk "Zarejestruj"
- Przycisk "Wyczyść"

Formularz powinien wysyłać dane na `/register` metodą POST.

**Wskazówka:** Pamiętaj aby otworzyć i zamknąć tag `<form>` i dodać atrybut `action` oraz `method`.

```html
<!-- Tutaj wpisz swój kod -->
```

---

### Zadanie 2: Formularz Zgłoszenia 📝
**Cel:** Stworzyć formularz do zbierania informacji o zgłoszeniu

Utwórz formularz z polami:
- Imię i nazwisko (type="text")
- Wiek (type="number", min=18, max=120)
- Data zgłoszenia (type="date")
- Godzina spotkania (type="time")
- Przycisk wysyłania

Formularz wysyła na `/report` metodą POST.

---

### Zadanie 3: Formularz Ankiety 📊
**Cel:** Praktyka z różnymi typami pól

Utwórz formularz ankiety zawierający:
- Imię (type="text")
- E-mail (type="email")
- Osobista strona (type="url")
- Numer telefonu (type="tel")
- Przedział wiekowy (type="number")
- Wiadomość (textarea, 5 linii)
- Przyciski: Wyślij + Wyczyść

Wysyłanie na `/survey` metodą POST.

---

### Zadanie 4: Porównanie GET vs POST ⚖️
**Cel:** Zrozumienie różnicy między GET a POST

Utwórz DWA formularze:

**Formularz 1 - Wyszukiwarka (GET):**
```html
<form action="/search" method="GET">
    <input type="search" name="q" placeholder="Szukaj...">
    <button type="submit">Szukaj</button>
</form>
```

**Formularz 2 - Logowanie (POST):**
```html
<form action="/login" method="POST">
    <input type="text" name="username" placeholder="Login">
    <input type="password" name="password" placeholder="Hasło">
    <button type="submit">Zaloguj</button>
</form>
```

**Pytanie:** Dlaczego wyszukiwarka używa GET a logowanie POST?

**Odpowiedź:** 
- GET - dane są w URL (wyszukiwanie można udostępnić)
- POST - dane ukryte (hasło nie powinno być w URL)

---

### Zadanie 5: Formularz bez `<form>` ❌
**Cel:** Zrozumienie znaczenia tagu `<form>`

Utwórz plik HTML z tym kodem:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Test formularza</title>
</head>
<body>
    <h2>Formularz BEZ <form></h2>
    
    <label>E-mail:</label>
    <input type="email" name="email">
    
    <label>Wiadomość:</label>
    <textarea name="message"></textarea>
    
    <button type="submit">Wyślij</button>
</body>
</html>
```

**Obserwacja:**
- Otwórz plik w przeglądarce
- Kliknij przycisk "Wyślij"
- Co się dzieje? **Nic!** Przycisk nie działa

Teraz dodaj tag `<form>` i powtórz.

---

### Zadanie 6: Praktyka - Formularz Rezerwacji 🏨
**Cel:** Połączyć wiedzę z kilku pól

Utwórz formularz hotelowy z:
- Imię i nazwisko
- E-mail
- Telefon
- Data przyjazdu (date)
- Data wyjazdu (date)
- Liczba gości (number)
- Typ pokoju (text lub wyczekaj na select)
- Notatki (textarea)
- Przyciski: Zarezerwuj + Wyczyść

**Bonus:** Dodaj walidację (required na wszystkie pola)

---

## 🎓 Podsumowanie Części 1

W tej części nauczyłeś się:
- ✅ Struktury tagu `<form>`
- ✅ Atrybutów `action` i `method`
- ✅ Różnych typów pól input
- ✅ Tagu `<textarea>`
- ✅ Przycisków submit i reset
- ✅ Praktycznego stosowania formularzy

**Następnie:** W Części 2 nauczysz się zaawansowanych pól (select, checkbox, radio) i walidacji!

