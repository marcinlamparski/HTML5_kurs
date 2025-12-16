# HTML5 - Moduł 8 & 9: Formularze (Pełny Przewodnik)

## Wprowadzenie

Formularze to sposób na zbieranie danych od użytkowników. To jeden z najważniejszych elementów stron internetowych. W tych dwóch modułach nauczysz się tworzyć wszystkie typy formularzy[1][2].

**Czego się nauczysz:**
- ✅ Tag `<form>` i atrybuty
- ✅ Pola tekstowe (text, email, password, number, date, itp.)
- ✅ `<textarea>` - wielolinijkowy tekst
- ✅ `<select>` - listy rozwijane
- ✅ Checkboxa i radio buttons
- ✅ Walidacja HTML5
- ✅ Dostępność formularzy
- ✅ Wysyłanie danych

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

## Część 4: Select i Option

```html
<select name="kraj">
    <option value="">Wybierz kraj...</option>
    <option value="pl">Polska</option>
    <option value="de">Niemcy</option>
    <option value="fr">Francja</option>
</select>
```

**Do czego służy:** Rozwijana lista opcji. Zamiast wpisywania tekstu, użytkownik wybiera jedną z predefiniowanych opcji. Oszczędza miejsce na ekranie i zapobiega błędom w pisowni.

| Element | Opis |
|---------|------|
| `<select>` | Kontener listy rozwijane |
| `<option>` | Pojedyncza opcja do wyboru |
| `value` | Wartość wysłana do serwera (może być inna niż tekst wyświetlany) |
| Pusta opcja | Zwykle na początku "Wybierz..." jako hint dla użytkownika |

**Przykład:** Kraj, miasto, kategoria produktu, język, rodzaj konta

---

### Optgroup - Grupowanie Opcji

```html
<select name="kategoria">
    <optgroup label="Warzywa">
        <option value="pomidor">Pomidor</option>
        <option value="kapusta">Kapusta</option>
    </optgroup>
    <optgroup label="Owoce">
        <option value="jablko">Jabłko</option>
        <option value="banan">Banan</option>
    </optgroup>
</select>
```

**Do czego służy:** Grupowanie powiązanych opcji w kategorii. Elementy opcji są wyświetlane wcięte pod nagłówkiem grupy, co ułatwia nawigację w długich listach.

| Element | Opis |
|---------|------|
| `<optgroup>` | Grupa opcji |
| `label` | Nazwa grupy wyświetlana w liście (nie do wyboru) |

---

### Multiple Select - Wielokrotny Wybór

```html
<select name="interesy" multiple>
    <option value="sport">Sport</option>
    <option value="muzyka">Muzyka</option>
    <option value="books">Książki</option>
</select>
```

**Do czego służy:** Pozwala użytkownikowi wybrać wiele opcji jednocześnie. Użytkownik zaznacza interesujące go elementy (Ctrl+click lub Cmd+click na Mac).

| Atrybut | Opis |
|---------|------|
| `multiple` | Pozwala wybrać więcej niż jedną opcję |
| Zaznaczenie | User klika + trzyma Ctrl/Cmd aby wybrać wiele |

**Uwaga:** W formularzu, wartości będą wysyłane jako tablica: `interesy: ["sport", "muzyka"]`

---

## Część 5: Checkboxa

```html
<input type="checkbox" name="zgoda" id="zgoda">
<label for="zgoda">Zgadzam się na warunki</label>

<input type="checkbox" name="newsletter" id="newsletter">
<label for="newsletter">Chcę otrzymywać newsletter</label>
```

**Do czego służy:** Niezależne pola wyboru (można wybrać zero, jeden lub wiele). Idealne dla opcji niezależnych od siebie - każda checkbox ma własny status.

| Cechy | Opis |
|-------|------|
| Niezależne | Wybranie jednego nie wpływa na pozostałe |
| Wiele wyborów | Można wybrać dowolną liczbę opcji |
| Zaznaczenie | Pole jest zaznaczone (checked) lub niezaznaczone |

**Przykład:** Zgoda na regulamin, newsletter, warunki, kategorie zainteresowań

---

### Wiele Checkboxów - Grupowanie

```html
<fieldset>
    <legend>Które języki znasz?</legend>
    
    <input type="checkbox" name="jezyki" value="pl" id="pl">
    <label for="pl">Polski</label>
    
    <input type="checkbox" name="jezyki" value="en" id="en">
    <label for="en">Angielski</label>
    
    <input type="checkbox" name="jezyki" value="de" id="de">
    <label for="de">Niemiecki</label>
</fieldset>
```

**Do czego służy:** Grupowanie kilku checkbox'ów o tej samej nazwie (`name`). Wszystkie zaznaczone opcje będą wysłane jako tablica wartości.

| Element | Opis |
|---------|------|
| `<fieldset>` | Kontener grupujący powiązane pola |
| `<legend>` | Tytuł grupy pól |
| Wspólna `name` | Wszystkie checkbox'y z tą samą nazwą są wysyłane razem |

**W PHP/Node.js otrzymamy:** `jezyki: ["pl", "en"]` (tylko zaznaczone)

---

## Część 6: Radio Buttons

```html
<input type="radio" name="płeć" value="m" id="m">
<label for="m">Mężczyzna</label>

<input type="radio" name="płeć" value="k" id="k">
<label for="k">Kobieta</label>
```

**Do czego służy:** Wzajemnie się wykluczające opcje - użytkownik może wybrać TYLKO jedną. Wszystkie radio buttons z tą samą `name` tworzą grupę.

| Różnica od Checkbox | Opis |
|-------------------|------|
| Checkbox | Wiele wyborów |
| Radio | Tylko jeden wybór |
| Semantyka | Radio buttons to "albo-albo" |

**Przykład:** Płeć (Mężczyzna/Kobieta), Sposób wysyłki (List/Kurier/Paczkomat), Typ konta (Standard/Premium)

---

## Część 7: Label i Dostępność

```html
<!-- ✅ DOBRZE - Label związany z input -->
<label for="email">E-mail:</label>
<input id="email" type="email" name="email">

<!-- ❌ ŹLE - Label bez związku -->
<label>E-mail:</label>
<input type="email" name="email">
```

**Do czego służy:** Tag `<label>` ma kilka ważnych funkcji:

| Funkcja | Opis |
|---------|------|
| Opis pola | Wyjaśnia co należy wpisać w pole |
| Dostępność | Czytniki ekranu wiedzą co wyjaśnia label |
| Klikowalność | Użytkownik może kliknąć na label aby fokusować pole |
| Mobilna ergonomia | Na telefonie większy obszar do kliknięcia |

**Prawidłowe połączenie:**
- `id` w input musi być identyczne z `for` w label
- Lub label zawiera input wewnątrz: `<label>Email: <input></label>`

---

## Część 8: Fieldset i Legend

```html
<fieldset>
    <legend>Dane Osobowe</legend>
    
    <label for="imie">Imię:</label>
    <input id="imie" type="text" name="imie">
    
    <label for="nazwisko">Nazwisko:</label>
    <input id="nazwisko" type="text" name="nazwisko">
</fieldset>

<fieldset>
    <legend>Adres</legend>
    
    <label for="ulica">Ulica:</label>
    <input id="ulica" type="text" name="ulica">
</fieldset>
```

**Do czego służy:** Organizowanie powiązanych pól w logiczne grupy. Poprawia czytanie formularza, szczególnie dla czytników ekranu.

| Element | Opis |
|---------|------|
| `<fieldset>` | Wizualny i logiczny kontener dla powiązanych pól |
| `<legend>` | Tytuł grupy pól - wyświetlany jako ramka wokół grupy |
| Semantyka | Wskazuje że pola w group'ie są powiązane tematycznie |

**Korzyści:**
- Czytelny formularz
- Lepsza dostępność
- Możliwość stylizacji grupy CSS
- Jasna struktura dla osób słabowidzących

---

## Część 9: Walidacja HTML5

```html
<!-- Required -->
<input type="email" required>

<!-- Min/Max length -->
<input type="text" minlength="3" maxlength="20">

<!-- Min/Max value -->
<input type="number" min="18" max="100">

<!-- Step -->
<input type="number" step="5">

<!-- Pattern -->
<input type="text" pattern="[A-Z]{3}" title="Trzy wielkie litery">

<!-- Placeholder -->
<input type="email" placeholder="user@example.com">
```

**Do czego służy:** Walidacja HTML5 sprawdza czy dane wprowadzone przez użytkownika spełniają określone wymagania PRZED wysłaniem do serwera.

| Atrybut | Opis |
|---------|------|
| `required` | Pole jest obowiązkowe - nie można wysłać formularza bez wypełnienia |
| `minlength` | Minimalna liczba znaków (np. hasło min 8 znaków) |
| `maxlength` | Maksymalna liczba znaków (np. kod pocztowy max 6 cyfr) |
| `min` | Minimalna wartość dla liczb i dat |
| `max` | Maksymalna wartość dla liczb i dat |
| `step` | Przyrost wartości (np. cena co 0.50 zł) |
| `pattern` | Wyrażenie regularne - format który musi być spełniony |
| `placeholder` | Pomocniczy tekst wskazujący co wpisać |

**Przykłady walidacji:**
- Numer PESEL: `pattern="[0-9]{11}"` - dokładnie 11 cyfr
- Kod pocztowy: `pattern="[0-9]{2}-[0-9]{3}"` - format XX-XXX
- Liczba dodatnia: `min="1"`
- Data w przeszłości: `max="2024-12-16"`

---

## Część 10: Atrybuty Input

```html
<input type="text"
    name="username"           <!-- Nazwa pola do wysłania -->
    value="default"           <!-- Wartość domyślna wyświetlana na początek -->
    placeholder="..."         <!-- Hint - podpowiedź co wpisać -->
    required                  <!-- Pole obowiązkowe -->
    disabled                  <!-- Pole wyłączone - użytkownik nie może edytować -->
    readonly                  <!-- Tylko do czytania - nie można zmienić, ale wysyła się -->
    autofocus                 <!-- Automatyczne fokusowanie pola na załadowaniu strony -->
    autocomplete="off"        <!-- Wyłączenie autouzupełniania (przydatne dla haseł) -->
    maxlength="50"            <!-- Maksymalna liczba znaków do wpisania -->
    pattern="..."             <!-- Wyrażenie regularne - walidacja formatu -->
>
```

| Atrybut | Opis |
|---------|------|
| `name` | Identyfikator pola wysyłany w formularzu do serwera |
| `value` | Wartość domyślna pokazana na starcie |
| `placeholder` | Tekst wskazówki widoczny gdy pole jest puste |
| `required` | Pole musi być wypełnione |
| `disabled` | Pole nieaktywne - szare, nie da się edytować |
| `readonly` | Pole tylko do czytania - można zobaczyć ale nie zmienić |
| `autofocus` | Pole automatycznie fokusuje się przy załadowaniu (tylko jedno!) |
| `autocomplete` | "on" lub "off" - czy przeglądarka ma sugerować wartości |
| `maxlength` | Maksymalna liczba znaków |
| `pattern` | Format walidacji (np. tylko liczby, format daty itp.) |

---

## Część 11: Przyciski

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
| `type="reset"` | Zeruje wszystkie pola formularza do stanu początkowego | Czyszczenie formularza, powrót do началу |
| `type="button"` | Zwykły przycisk - nie wysyła formularza, wymaga JavaScript | Akcje dodatkowe, obliczenia, ukrywanie/pokazywanie pól |

**Dobra praktyka:** Zawsze używaj `type="submit"` dla wysyłania i `type="reset"` do czyszczenia. Przyciski zwykłe rzadko są potrzebne w formularzu.

---

## Część 12: Praktyczne Formu

### Formularz Kontaktowy

```html
<form action="/contact" method="POST">
    <h2>Kontakt</h2>
    
    <!-- Imię - wymagane, główny tekst -->
    <label for="name">Imię:</label>
    <input id="name" type="text" name="name" required>
    
    <!-- Email - wymagany, walidacja formatu email -->
    <label for="email">E-mail:</label>
    <input id="email" type="email" name="email" required>
    
    <!-- Temat - wymagany, opis wiadomości -->
    <label for="subject">Temat:</label>
    <input id="subject" type="text" name="subject" required>
    
    <!-- Wiadomość - wiele linii tekstu, wymagana -->
    <label for="message">Wiadomość:</label>
    <textarea id="message" name="message" rows="5" required></textarea>
    
    <!-- Zgoda na newsletter - opcjonalna -->
    <input type="checkbox" id="newsletter" name="newsletter">
    <label for="newsletter">Zapisz się na newsletter</label>
    
    <!-- Przyciski: wysyłanie i czyszczenie -->
    <button type="submit">Wyślij</button>
    <button type="reset">Wyczyść</button>
</form>
```

**Elementy:**
- `name` - imię osoby kontaktowej
- `email` - adres do odpowiedzi
- `subject` - temat wiadomości
- `message` - tekst wiadomości (textarea dla dłuższych tekstów)
- `newsletter` - czy chce newsletter'a
