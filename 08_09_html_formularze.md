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

- `action` - gdzie wysłać dane
- `method` - GET lub POST

---

## Część 2: Pola Tekstowe

### Input Type="text"

```html
<input type="text" name="imie" placeholder="Wpisz imię">
```

### Email

```html
<input type="email" name="email" required>
```

### Password

```html
<input type="password" name="haslo" required>
```

### Number

```html
<input type="number" name="wiek" min="18" max="100">
```

### Date

```html
<input type="date" name="data">
```

### Time

```html
<input type="time" name="godzina">
```

### Color

```html
<input type="color" name="kolor" value="#FF0000">
```

### Range

```html
<input type="range" name="volume" min="0" max="100" value="50">
```

### URL

```html
<input type="url" name="strona">
```

### Tel

```html
<input type="tel" name="telefon">
```

### Search

```html
<input type="search" name="szukaj">
```

---

## Część 3: Textarea

```html
<textarea name="wiadomosc" rows="5" cols="40"></textarea>

<!-- Lepiej z CSS -->
<textarea name="wiadomosc" rows="5"></textarea>
```

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

### Optgroup

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

### Multiple Select

```html
<select name="interesy" multiple>
    <option value="sport">Sport</option>
    <option value="muzyka">Muzyka</option>
    <option value="books">Książki</option>
</select>
```

---

## Część 5: Checkboxa

```html
<input type="checkbox" name="zgoda" id="zgoda">
<label for="zgoda">Zgadzam się na warunki</label>

<input type="checkbox" name="newsletter" id="newsletter">
<label for="newsletter">Chcę otrzymywać newsletter</label>
```

### Wiele Checkboxów

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

---

## Część 6: Radio Buttons

```html
<input type="radio" name="płeć" value="m" id="m">
<label for="m">Mężczyzna</label>

<input type="radio" name="płeć" value="k" id="k">
<label for="k">Kobieta</label>
```

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

---

## Część 10: Atrybuty Input

```html
<input type="text"
    name="username"           <!-- Nazwa pola -->
    value="default"           <!-- Wartość domyślna -->
    placeholder="..."         <!-- Hint -->
    required                  <!-- Obowiązkowe -->
    disabled                  <!-- Wyłączone -->
    readonly                  <!-- Tylko do czytania -->
    autofocus                 <!-- Automatyczny focus -->
    autocomplete="off"        <!-- Brak autouzupełniania -->
    maxlength="50"            <!-- Max liczba znaków -->
    pattern="..."             <!-- Regex pattern -->
>
```

---

## Część 11: Przyciski

```html
<!-- Submit -->
<button type="submit">Wyślij</button>

<!-- Reset -->
<button type="reset">Wyczyść</button>

<!-- Zwykły -->
<button type="button">Kliknij mnie</button>
```

---

## Część 12: Praktyczne Formu

### Formularz Kontaktowy

```html
<form action="/contact" method="POST">
    <h2>Kontakt</h2>
    
    <label for="name">Imię:</label>
    <input id="name" type="text" name="name" required>
    
    <label for="email">E-mail:</label>
    <input id="email" type="email" name="email" required>
    
    <label for="subject">Temat:</label>
    <input id="subject" type="text" name="subject" required>
    
    <label for="message">Wiadomość:</label>
    <textarea id="message" name="message" rows="5" required></textarea>
    
    <input type="checkbox" id="newsletter" name="newsletter">
    <label for="newsletter">Zapisz się na newsletter</label>
    
    <button type="submit">Wyślij</button>
    <button type="reset">Wyczyść</button>
</form>
```

### Formularz Rejestracji

```html
<form action="/register" method="POST">
    <h2>Rejestracja</h2>
    
    <fieldset>
        <legend>Dane Osobowe</legend>
        
        <label for="fname">Imię:</label>
        <input id="fname" type="text" name="fname" required>
        
        <label for="lname">Nazwisko:</label>
        <input id="lname" type="text" name="lname" required>
    </fieldset>
    
    <fieldset>
        <legend>Konto</legend>
        
        <label for="email">E-mail:</label>
        <input id="email" type="email" name="email" required>
        
        <label for="password">Hasło:</label>
        <input id="password" type="password" name="password" minlength="8" required>
        
        <label for="password2">Powtórz hasło:</label>
        <input id="password2" type="password" name="password2" minlength="8" required>
    </fieldset>
    
    <fieldset>
        <legend>Preferencje</legend>
        
        <input type="radio" name="language" value="pl" id="pl" checked>
        <label for="pl">Polski</label>
        
        <input type="radio" name="language" value="en" id="en">
        <label for="en">Angielski</label>
        
        <input type="checkbox" name="terms" id="terms" required>
        <label for="terms">Zgadzam się na warunki użytkownika</label>
    </fieldset>
    
    <button type="submit">Zarejestruj się</button>
</form>
```

---

## Część 13: Ćwiczenia

### Ćwiczenie 1: Prosty Formularz

Stwórz formularz z:
- Imię, Nazwisko
- E-mail
- Telefon
- Przycisk Wyślij

### Ćwiczenie 2: Formularz z Walidacją

Rozszerz Ćwiczenie 1 o:
- Required na wszystkich polach
- Email type z walidacją
- Pattern dla telefonu
- Min/Max length dla imienia

### Ćwiczenie 3: Ankieta

Stwórz ankietę zawierającą:
- Select z opcjami
- Checkboxa (wiele możliwości)
- Radio buttons
- Textarea
- Fieldset i Legend

### Ćwiczenie 4: Rejestracja

Utwórz formularz rejestracji:
- Dane osobowe (fieldset)
- Dane konta (fieldset)
- Hasła z min 8 znakami
- Zgoda na warunki (checkbox)
- Język (radio buttons)

---

## Best Practices

✅ Zawsze używaj `<label>` z `for` atrybutem  
✅ Grupuj pola w `<fieldset>` z `<legend>`  
✅ Używaj `<placeholder>` dla hintu  
✅ Walidacja HTML5 zawsze  
✅ Descriptive field names  
✅ Clear submit button text  
✅ Accessibility first  

---

*Gotowy do Modułów 10-13? Zaawansowane tematy! 🚀*