# HTML5 - Moduł 9: Formularze - Część 2 (Zaawansowane)

## Wprowadzenie

W drugiej części nauczysz się zaawansowanych pól formularzy, takich jak listy rozwijane, checkboxy, radio buttons, i walidacji HTML5. Pozwoli to na tworzenie bardziej złożonych i bezpiecznych formularzy.

**Czego się nauczysz:**
- ✅ `<select>` - listy rozwijane
- ✅ Checkboxa i radio buttons
- ✅ `<fieldset>` i `<legend>` - organizacja pól
- ✅ `<label>` - dostępność
- ✅ Walidacja HTML5
- ✅ Atrybuty zaawansowane

---

## Część 1: Select i Option

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

## Część 2: Checkboxa

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

## Część 3: Radio Buttons

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

## Część 4: Label i Dostępność

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

## Część 5: Fieldset i Legend

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

## Część 6: Walidacja HTML5

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

## Część 7: Atrybuty Input

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

## Część 8: Praktyczne Formu

### Formularz Kontaktowy - Zaawansowany

```html
<form action="/contact" method="POST">
    <h2>Kontakt</h2>
    
    <fieldset>
        <legend>Dane Osobowe</legend>
        
        <label for="name">Imię i Nazwisko:</label>
        <input id="name" type="text" name="name" required minlength="3" maxlength="50">
        
        <label for="email">E-mail:</label>
        <input id="email" type="email" name="email" required>
        
        <label for="phone">Telefon:</label>
        <input id="phone" type="tel" name="phone">
    </fieldset>
    
    <fieldset>
        <legend>Wiadomość</legend>
        
        <label for="subject">Temat:</label>
        <select id="subject" name="subject" required>
            <option value="">-- Wybierz temat --</option>
            <option value="support">Wsparcie techniczne</option>
            <option value="feedback">Opinia</option>
            <option value="other">Inne</option>
        </select>
        
        <label for="message">Wiadomość:</label>
        <textarea id="message" name="message" rows="5" required minlength="10" maxlength="500"></textarea>
    </fieldset>
    
    <fieldset>
        <legend>Preferencje</legend>
        
        <input type="checkbox" id="newsletter" name="newsletter">
        <label for="newsletter">Chcę otrzymywać newsletter</label>
        
        <input type="checkbox" id="gdpr" name="gdpr" required>
        <label for="gdpr">Wyrażam zgodę na przetwarzanie danych</label>
    </fieldset>
    
    <button type="submit">Wyślij</button>
    <button type="reset">Wyczyść</button>
</form>
```

---

### Formularz Rejestracji - Pełny Przykład

```html
<form action="/register" method="POST">
    <h2>Rejestracja</h2>
    
    <fieldset>
        <legend>Dane Osobowe</legend>
        
        <label for="name">Imię i Nazwisko:</label>
        <input id="name" type="text" name="name" required>
        
        <label for="birthdate">Data urodzenia:</label>
        <input id="birthdate" type="date" name="birthdate" required>
        
        <label for="gender">Płeć:</label>
        <input type="radio" name="gender" value="m" id="m">
        <label for="m">Mężczyzna</label>
        
        <input type="radio" name="gender" value="k" id="k">
        <label for="k">Kobieta</label>
        
        <input type="radio" name="gender" value="other" id="other">
        <label for="other">Inna</label>
    </fieldset>
    
    <fieldset>
        <legend>Konto</legend>
        
        <label for="email">E-mail:</label>
        <input id="email" type="email" name="email" required>
        
        <label for="username">Nazwa użytkownika:</label>
        <input id="username" type="text" name="username" required minlength="3" maxlength="20">
        
        <label for="password">Hasło:</label>
        <input id="password" type="password" name="password" required minlength="8">
    </fieldset>
    
    <fieldset>
        <legend>Interesy</legend>
        
        <input type="checkbox" name="interests" value="sport" id="sport">
        <label for="sport">Sport</label>
        
        <input type="checkbox" name="interests" value="muzyka" id="music">
        <label for="music">Muzyka</label>
        
        <input type="checkbox" name="interests" value="film" id="film">
        <label for="film">Film</label>
    </fieldset>
    
    <input type="checkbox" id="terms" name="terms" required>
    <label for="terms">Akceptuję regulamin</label>
    
    <button type="submit">Zarejestruj</button>
</form>
```

---

---

## 📋 ZADANIA PRAKTYCZNE - Część 2

### Zadanie 1: Formularz z Select 🎯
**Cel:** Praktyka z listami rozwijającymi

Utwórz formularz zawierający:
- Imię (text)
- Kraj (select z opcjami: Polska, Niemcy, Francja, Wielka Brytania)
- Typ konta (select: Premium, Standard, Darmowe)
- Przycisk Wyślij

Listę países wysyłaj na `/submit` metodą POST.

**Wskazówka:** Pamiętaj dodać jedną pustą opcję na początek!

```html
<!-- Tutaj wpisz swój kod -->
```

---

### Zadanie 2: Checkboxa - Zgody 📋
**Cel:** Praktyka z niezależnymi polami wyboru

Utwórz formularz rejestracji z:
- Imię i nazwisko (text, required)
- E-mail (email, required)
- Cztery niezależne checkboxa:
  - Zgadzam się na regulamin (wymagana)
  - Zgadzam się na politykę prywatności (wymagana)
  - Chcę newsletter
  - Komunikaty SMS
- Przyciski: Zarejestruj + Wyczyść

**Wskazówka:** Każda checkbox powinna mieć własne `name`!

---

### Zadanie 3: Radio Buttons - Wybór Jednego 📻
**Cel:** Praktyka z mutualnie wykluczającymi opcjami

Utwórz formularz zamówienia z:
- Wybór porcji (radio):
  - Mała (300g)
  - Średnia (500g)
  - Duża (800g)
- Wybór sosu (radio):
  - Pomidorowy
  - Krem
  - Pesto
- Typ dostawy (radio):
  - Odbór osobisty
  - Dostawa 0-2 godziny
  - Dostawa 2-4 godziny
- Przycisk: Zamów

**Pamiętaj:** Aby radio buttons pracowały razem, muszą mieć tę SAMĄ wartość `name`!

---

### Zadanie 4: Zaawansowana Walidacja ✅
**Cel:** Stosowanie atrybutów walidacji

Utwórz formularz z takimi polami:
- Imię (text, required, minlength=2, maxlength=30)
- Wiek (number, required, min=18, max=100)
- Hasło (password, required, minlength=8)
- Kod pocztowy (text, pattern="[0-9]{2}-[0-9]{3}")
- Numer PESEL (text, pattern="[0-9]{11}")
- Przycisk: Wyślij

Każde pole powinno być walidowane PRZED wysłaniem!

---

### Zadanie 5: Fieldset i Legend - Organizacja 🏗️
**Cel:** Grupowanie i organizowanie pól

Utwórz formularz z trzema sekcjami (fieldset + legend):

**Sekcja 1: Dane Osobowe**
- Imię
- Nazwisko
- Data urodzenia

**Sekcja 2: Adres**
- Ulica
- Numer domu
- Kod pocztowy
- Miasto

**Sekcja 3: Kontakt**
- E-mail
- Telefon
- WWW

Każda sekcja powinna mieć swoją `<legend>`!

---

### Zadanie 6: Kompleksowy Formularz - Ankieta 📊
**Cel:** Połączyć wszystko w jednym formularzu

Utwórz formularz ankiety zawierający:

```html
<fieldset>
  <legend>Dane osobowe</legend>
  - Imię i nazwisko (text, required)
  - E-mail (email, required)
  - Telefon (tel)
</fieldset>

<fieldset>
  <legend>Jakość serwisu</legend>
  - Ocena (radio 1-5)
  - Czy polecisz? (radio: Tak/Nie)
</fieldset>

<fieldset>
  <legend>Zainteresowania</legend>
  - Checkboxa: Produkty, Usługi, Artykuły, Inne
  (można wybrać wiele!)
</fieldset>

<fieldset>
  <legend>Kategoria produktu</legend>
  - Select z 5+ opcjami z groupowaniem (optgroup)
</fieldset>

<fieldset>
  <legend>Komentarz</legend>
  - Textarea (min 10, max 500 znaków)
  - Zgoda RODO (checkbox, required)
</fieldset>

Przyciski: Wyślij + Wyczyść
```

---

### Zadanie 7: Select Multiple - Wielokrotny Wybór 🎪
**Cel:** Praktyka z wyborem wielu opcji

Utwórz formularz z:
- Imię (text)
- Języki które znasz (select multiple):
  - Polski
  - Angielski
  - Niemiecki
  - Francuski
  - Hiszpański
  - Chiński
- Przycisk: Wyślij

**Wskazówka:** User zaznacza opcje z Ctrl+click (Cmd+click na Mac)

---

### Zadanie 8: Praktyka - Formularz Sklepu 🛒
**Cel:** Realny przykład z e-commerce

Utwórz formularz checkout sklepu internetowego zawierający:

```html
SEKCJA: Dane Dostawy
- Imię i Nazwisko
- E-mail
- Telefon
- Ulica i numer
- Kod pocztowy
- Miasto
- Kraj (select)

SEKCJA: Typ Dostawy
- Opcje wysyłki (radio):
  - List polecony (5 zł)
  - Kurier (15 zł)
  - Paczkomat (8 zł)

SEKCJA: Dane Faktury
- Nazwa firmy
- NIP
- Checkbox: Taka sama jak dostawa

SEKCJA: Zgody
- Checkbox: Regulamin
- Checkbox: Polityka prywatności
- Checkbox: Newsletter

Przyciski: Zamów + Anuluj
```

---

### Zadanie 9: Wyzwanie - Formularz Filmu 🎬
**Cel:** Zaawansowana praktyka

Utwórz formularz do dodawania recenzji filmu:

```html
SEKCJA: Informacje o Filmie
- Tytuł (text, required, max=100)
- Rok (number, min=1900, max=2025)
- Reżyser (text)
- Gatunek (select: Akcja, Dramat, Komedia, Horror, Thriller)

SEKCJA: Twoja Recenzja
- Ocena (radio 1-10 lub range)
- Czy polecasz? (radio: Tak/Nie)
- Recenzja tekstowa (textarea, min=20)

SEKCJA: Znaczniki
- Checkboxa: Nie dla dzieci, Ciekawy, Nudny, Śmieszny, Straszny
- Select multiple: Aktorzy poleceni

SEKCJA: Zgody
- Checkbox: Wyrażam zgodę na publikację
```

---

## 🎓 Podsumowanie Części 2

W tej części nauczyłeś się:
- ✅ List rozwijanych (`<select>`, `<option>`, `<optgroup>`)
- ✅ Checkboxów i radio buttons
- ✅ Organizacji pól (`<fieldset>`, `<legend>`)
- ✅ Dostępności (`<label>`)
- ✅ Walidacji HTML5
- ✅ Zaawansowanych atrybutów

**Gratulacje!** 🎉 Teraz znasz wszystko co potrzebne do tworzenia profesjonalnych formularzy HTML!

**Następny krok:** Nauka CSS do stylizacji formularzy lub JavaScript do zaawansowanej walidacji.

