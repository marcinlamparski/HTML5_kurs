# 📝 SZABLON HTML — CZĘŚĆ 2 — FORMULARZE + BOX MODEL

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT — ŚCIĄGAWKA PRZED ĆWICZENIAMI

Zanim zaczniesz ćwiczenia, przeczytaj to!

### Formularz HTML — szkielet:

```html
<form action="wyslij.php" method="post">

    <!-- Tu umieszczamy pola formularza -->

    <button type="submit">Wyślij</button>
</form>
```

| Atrybut | Do czego służy? | Wartości |
|---------|-----------------|---------|
| `action` | Gdzie wysłać dane | adres URL skryptu |
| `method` | Jak wysłać dane | `get` (widoczne w URL) lub `post` (ukryte) |

### Pola formularza — typy input:

| Typ | Kod | Co wyświetla? |
|-----|-----|---------------|
| Tekst | `<input type="text">` | Zwykłe pole tekstowe |
| Email | `<input type="email">` | Pole z walidacją emaila |
| Hasło | `<input type="password">` | Pole z ukrytymi znakami (\*\*\*) |
| Liczba | `<input type="number">` | Pole liczbowe ze strzałkami |
| Checkbox | `<input type="checkbox">` | Kwadratowy znacznik (wielokrotny wybór) |
| Radio | `<input type="radio">` | Okrągły znacznik (jeden wybór z grupy) |
| Submit | `<input type="submit">` | Przycisk wysyłający formularz |

### Label — etykieta pola:

```html
<!-- Metoda 1: for + id (zalecana — kliknięcie w tekst zaznacza pole) -->
<label for="imie">Imię:</label>
<input type="text" id="imie" name="imie">

<!-- Metoda 2: opakowanie (równoważna) -->
<label>
    Imię: <input type="text" name="imie">
</label>
```

> ⚠️ `for` w label musi być identyczne z `id` w input!

### Select i textarea:

```html
<!-- Lista rozwijana -->
<select name="miasto">
    <option value="waw">Warszawa</option>
    <option value="kra">Kraków</option>
    <option value="wro" selected>Wrocław</option>  <!-- domyślnie wybrany -->
</select>

<!-- Pole wieloliniowe -->
<textarea name="wiadomosc" rows="4" cols="40">
    Domyślna treść...
</textarea>
```

---

### Box Model — co to jest?

Każdy element HTML to prostokąt złożony z 4 warstw:

```
┌─────────────────────────────────────┐
│              MARGIN                 │  ← zewnętrzny odstęp (od innych elementów)
│   ┌─────────────────────────────┐   │
│   │           BORDER            │   │  ← ramka (obramowanie)
│   │   ┌─────────────────────┐   │   │
│   │   │       PADDING       │   │   │  ← wewnętrzny odstęp (od treści do ramki)
│   │   │   ┌─────────────┐   │   │   │
│   │   │   │   CONTENT   │   │   │   │  ← treść (tekst, obraz...)
│   │   │   └─────────────┘   │   │   │
│   │   └─────────────────────┘   │   │
│   └─────────────────────────────┘   │
└─────────────────────────────────────┘
```

### Właściwości Box Model — ściągawka:

```css
/* PADDING — odstęp wewnętrzny (między treścią a ramką) */
padding: 20px;                    /* 20px z każdej strony */
padding: 10px 20px;               /* góra/dół=10px, lewo/prawo=20px */
padding-top: 10px;                /* tylko góra */
padding-right: 15px;              /* tylko prawo */
padding-bottom: 10px;             /* tylko dół */
padding-left: 15px;               /* tylko lewo */

/* MARGIN — odstęp zewnętrzny (między elementami) */
margin: 20px;                     /* 20px z każdej strony */
margin: 10px auto;                /* góra/dół=10px, wyśrodkowanie poziome */
margin-top: 30px;                 /* tylko góra */
margin: 0 auto;                   /* wyśrodkuj element poziomo */

/* BORDER — ramka */
border: 2px solid #333;           /* grubość, styl, kolor */
border-width: 2px;
border-style: solid;              /* solid, dashed, dotted, none */
border-color: #333333;
border-radius: 8px;               /* zaokrąglenie rogów */

/* ROZMIAR */
width: 300px;                     /* szerokość */
height: 150px;                    /* wysokość */
max-width: 600px;                 /* maksymalna szerokość */
```

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 — HTML5 i CSS Część 2 — Formularze i Box Model</title>
    <style>
        /* ============================================================
           STYLE SZABLONU — nie zmieniaj tej sekcji!
           ============================================================ */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        header.page-header {
            text-align: center;
            color: white;
            margin-bottom: 40px;
        }

        header.page-header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        header.page-header p {
            font-size: 1.1em;
            opacity: 0.9;
        }

        .task {
            background: white;
            border-radius: 10px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.1);
        }

        .task-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .task-number {
            display: inline-block;
            background: #a1c4fd;
            color: #1a3a6b;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            text-align: center;
            line-height: 40px;
            font-weight: bold;
            margin-right: 15px;
            font-size: 1.2em;
            flex-shrink: 0;
        }

        .task-title {
            color: #333;
            font-size: 1.3em;
        }

        .difficulty {
            margin-left: auto;
            font-size: 0.9em;
            color: #888;
            white-space: nowrap;
        }

        .difficulty-star {
            color: #ffa500;
        }

        .task-content {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 6px;
            border-left: 4px solid #a1c4fd;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #e3f2fd;
            border: 1px solid #90caf9;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #0d47a1;
            font-size: 0.95em;
            line-height: 1.5;
        }

        .warning-box {
            background: #fff8e1;
            border: 1px solid #ffe082;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #e65100;
            font-size: 0.95em;
            line-height: 1.5;
        }

        .code-example {
            background: #f3f4f6;
            border: 1px solid #d1d5db;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            font-size: 0.9em;
        }

        .code-example h4 {
            color: #555;
            margin-bottom: 6px;
            font-size: 0.9em;
        }

        .code-example pre {
            color: #333;
            line-height: 1.6;
            white-space: pre-wrap;
        }

        .ex-area {
            background: white;
            border: 2px dashed #a1c4fd;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            min-height: 60px;
        }

        .ex-area-label {
            font-size: 0.8em;
            color: #a1c4fd;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 8px;
        }

        /* Obszar ćwiczeń CSS — style uczniów trafiają tutaj */
        /* (scoped przez id obszaru w ćwiczeniach CSS) */

        footer.page-footer {
            text-align: center;
            color: white;
            margin-top: 40px;
            padding: 20px;
            opacity: 0.9;
        }
    </style>
</head>
<body>

<div class="container">

    <header class="page-header">
        <h1>🔵 Formularze + Box Model</h1>
        <p>Część 2 — HTML5 i CSS | INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: PODSTAWY FORMULARZA
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">Szkielet formularza — &lt;form&gt;</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Utwórz formularz kontaktowy szkoły. Wpisz tag <code>&lt;form&gt;</code> z atrybutami <code>action="wyslij.php"</code> i <code>method="post"</code>. Na razie formularz będzie pusty — dodamy pola w kolejnych ćwiczeniach. Pod formularzem dodaj komentarz który wyjaśnia do czego służy atrybut <code>method</code>.</p>
            <div class="info-box">💡 <strong>method="get"</strong> — dane widoczne w adresie URL (np. wyszukiwarki)<br>
            <strong>method="post"</strong> — dane ukryte, wysyłane w tle (hasła, formularze kontaktowe)</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <!-- Napisz tu formularz z atrybutami action i method -->
                <!-- Na razie pusty, bez pól wewnątrz -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">Pole tekstowe z etykietą — &lt;input&gt; i &lt;label&gt;</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz formularz z dwoma polami: "Imię" i "Nazwisko". Każde pole musi mieć etykietę <code>&lt;label&gt;</code> połączoną z polem przez <code>for</code> i <code>id</code>. Sprawdź czy kliknięcie w tekst etykiety zaznacza pole!</p>
            <div class="code-example">
                <h4>📄 Wzorzec do naśladowania:</h4>
                <pre>
&lt;form action="wyslij.php" method="post"&gt;

    &lt;label for="imie"&gt;Imię:&lt;/label&gt;
    &lt;input type="text" id="imie" name="imie"&gt;

    &lt;!-- Dodaj podobne pole dla Nazwiska --&gt;

&lt;/form&gt;</pre>
            </div>
            <div class="warning-box">⚠️ Atrybut <code>for</code> w &lt;label&gt; musi być IDENTYCZNY z <code>id</code> w &lt;input&gt;!<br>
            Atrybut <code>name</code> to klucz pod którym dane trafiają do serwera — też ważny!</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — 2 pola z etykietami:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <!-- Formularz z polami: Imię i Nazwisko, każde z label -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">Typy pól — email, password, number</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Rozbuduj formularz rejestracji konta. Dodaj trzy pola różnych typów i sprawdź jak reagują na błędne dane:</p>
            <ul style="margin: 8px 0 8px 20px; color: #555; line-height: 1.9;">
                <li>Pole <strong>email</strong> — wpisz tekst bez @ i spróbuj wysłać formularz</li>
                <li>Pole <strong>password</strong> — wpisz hasło i obserwuj gwiazdki</li>
                <li>Pole <strong>number</strong> — dodaj atrybuty <code>min="1"</code> i <code>max="100"</code></li>
            </ul>
            <div class="info-box">💡 Przeglądarka sama sprawdza poprawność email i number — to HTML5!<br>
            Nie potrzebujesz JavaScript do podstawowej walidacji.</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — 3 pola różnych typów:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <!-- Formularz z polami: email, password, number (z min i max) -->
                <!-- Każde pole z label, a na końcu button type="submit" -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">Przyciski i atrybut placeholder</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Do formularza z poniższego kodu dodaj: atrybut <code>placeholder</code> do każdego pola (podpowiedź widoczna gdy pole jest puste), przycisk <code>type="submit"</code> oraz drugi przycisk <code>type="reset"</code> który czyści formularz.</p>
            <div class="code-example">
                <h4>📄 Kod startowy do modyfikacji:</h4>
                <pre>
&lt;form action="logowanie.php" method="post"&gt;

    &lt;label for="login"&gt;Login:&lt;/label&gt;
    &lt;input type="text" id="login" name="login"&gt;

    &lt;label for="haslo"&gt;Hasło:&lt;/label&gt;
    &lt;input type="password" id="haslo" name="haslo"&gt;

    &lt;!-- Dodaj tutaj dwa przyciski: submit i reset --&gt;

&lt;/form&gt;</pre>
            </div>
            <div class="info-box">💡 <code>placeholder="np. jan.kowalski"</code> — szara podpowiedź w polu, znika gdy zaczniesz pisać<br>
            <code>type="reset"</code> — czyści wszystkie pola formularza jednym kliknięciem</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ KOD — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <form action="logowanie.php" method="post">

                    <label for="ex4-login">Login:</label>
                    <input type="text" id="ex4-login" name="login">

                    <label for="ex4-haslo">Hasło:</label>
                    <input type="password" id="ex4-haslo" name="haslo">

                    <!-- Dodaj placeholder do obu pól -->
                    <!-- Dodaj przycisk submit z tekstem "Zaloguj się" -->
                    <!-- Dodaj przycisk reset z tekstem "Wyczyść" -->

                </form>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: WIĘCEJ TYPÓW PÓL
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">Checkboxy — wielokrotny wybór</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz sekcję formularza "Jakie technologie znasz?" z checkboxami. Stwórz co najmniej 5 opcji (HTML, CSS, JavaScript, PHP, Python). Jeden checkbox dodaj z atrybutem <code>checked</code> — żeby był domyślnie zaznaczony.</p>
            <div class="code-example">
                <h4>📄 Wzorzec checkboxa:</h4>
                <pre>
&lt;input type="checkbox" id="html" name="technologie" value="html"&gt;
&lt;label for="html"&gt;HTML&lt;/label&gt;</pre>
            </div>
            <div class="info-box">💡 Przy checkboxach label piszemy PO input (konwencja)<br>
            <code>value</code> = wartość wysyłana do serwera gdy pole jest zaznaczone<br>
            <code>checked</code> = domyślnie zaznaczony</div>
            <div class="warning-box">⚠️ Każdy checkbox ma swoje unikalne <code>id</code>, ale wszystkie w grupie mają to samo <code>name</code>!<br>
            Dzięki temu serwer wie, że to jedna grupa odpowiedzi.</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — checkboxy technologii:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <!-- Formularz z nagłówkiem "Jakie technologie znasz?" -->
                <!-- 5 checkboxów, jeden domyślnie zaznaczony (checked) -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">Radio — jeden wybór z grupy</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz pytanie ankietowe "Jak preferujesz uczyć się programowania?" z przyciskami radio. Opcje: "Z książki", "Z tutoriali video", "Z kursów online", "Samodzielnie przez projekty". Sprawdź że można wybrać tylko JEDNĄ opcję.</p>
            <div class="code-example">
                <h4>📄 Wzorzec radio — klucz: ta sama wartość name!</h4>
                <pre>
&lt;input type="radio" id="ksiazka" name="metoda" value="ksiazka"&gt;
&lt;label for="ksiazka"&gt;Z książki&lt;/label&gt;

&lt;input type="radio" id="video" name="metoda" value="video"&gt;
&lt;label for="video"&gt;Z tutoriali video&lt;/label&gt;</pre>
            </div>
            <div class="info-box">💡 Radio vs Checkbox:<br>
            <strong>radio</strong> = wybieram JEDNĄ opcję z grupy (ta sama wartość <code>name</code>)<br>
            <strong>checkbox</strong> = wybieram WIELE opcji (ta sama wartość <code>name</code> dla grupy)</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — pytanie z radio:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <!-- Pytanie ankietowe z 4 opcjami radio -->
                <!-- Wszystkie radio w grupie mają to samo name="metoda" -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">Lista rozwijana — &lt;select&gt; i &lt;option&gt;</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz formularz z listą rozwijaną wyboru województwa (co najmniej 5 województw). Jedno województwo ustaw jako domyślnie wybrany za pomocą atrybutu <code>selected</code>. Dodaj też pierwszą pustą opcję z tekstem "— wybierz województwo —".</p>
            <div class="code-example">
                <h4>📄 Wzorzec select:</h4>
                <pre>
&lt;label for="woj"&gt;Województwo:&lt;/label&gt;
&lt;select id="woj" name="wojewodztwo"&gt;
    &lt;option value=""&gt;— wybierz województwo —&lt;/option&gt;
    &lt;option value="maz"&gt;Mazowieckie&lt;/option&gt;
    &lt;option value="mpl" selected&gt;Małopolskie&lt;/option&gt;
    &lt;option value="wlk"&gt;Wielkopolskie&lt;/option&gt;
&lt;/select&gt;</pre>
            </div>
            <div class="info-box">💡 <code>value</code> w option = wartość wysyłana do serwera (krótka, bez polskich znaków)<br>
            Tekst między tagami option = to co widzi użytkownik (może być po polsku)</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — lista rozwijana województw:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <!-- Select z min. 5 województwami + pusta opcja na początku -->
                <!-- Jedno województwo domyślnie selected -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">Pole wieloliniowe — &lt;textarea&gt;</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Dodaj do formularza pole tekstowe na wiadomość (<code>&lt;textarea&gt;</code>) z atrybutami <code>rows="5"</code> i <code>cols="40"</code>. Następnie dopisz atrybut <code>placeholder</code> z tekstem "Wpisz swoją wiadomość...". Całość powinna wyglądać jak formularz kontaktowy.</p>
            <div class="code-example">
                <h4>📄 Wzorzec textarea:</h4>
                <pre>
&lt;label for="wiad"&gt;Wiadomość:&lt;/label&gt;
&lt;textarea id="wiad" name="wiadomosc" rows="5" cols="40"
          placeholder="Wpisz swoją wiadomość..."&gt;&lt;/textarea&gt;</pre>
            </div>
            <div class="warning-box">⚠️ textarea NIE jest samozamykający! Musi mieć tag zamykający &lt;/textarea&gt;<br>
            Jeśli wewnątrz tagów wstawisz tekst — pojawi się jako domyślna treść w polu.</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — formularz kontaktowy z textarea:</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <!-- Formularz z polami: Imię, Email, Wiadomość (textarea) + przycisk submit -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: BOX MODEL
         Ćwiczenia 9–12
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">Padding — wewnętrzny odstęp</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej masz trzy elementy div. Dodaj do nich w CSS różne wartości <code>padding</code> i obserwuj jak się powiększają. Użyj kolorowego tła żeby efekt był widoczny.</p>
            <div class="code-example">
                <h4>📄 Skala padding do zastosowania:</h4>
                <pre>
#box-a { padding: 5px;  background-color: #bbdefb; }
#box-b { padding: 20px; background-color: #90caf9; }
#box-c { padding: 40px; background-color: #64b5f6; }</pre>
            </div>
            <div class="info-box">💡 Padding powiększa element OD ŚRODKA — tekst się "odpycha" od krawędzi.<br>
            Sprawdź w F12 → DevTools → najedź na element → zobaczysz kolorowy box model!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS I OBSERWUJESZ — Ćwiczenie 9 ↓↓↓ -->
            <div class="ex-area" id="ex9-area">

                <style>
                    /* Wpisz tu reguły CSS dla #box-a, #box-b, #box-c */

                </style>

                <div id="box-a">Ten div ma padding: 5px</div>
                <div id="box-b">Ten div ma padding: 20px</div>
                <div id="box-c">Ten div ma padding: 40px</div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 9 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">Margin — zewnętrzny odstęp</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej masz trzy bloki. Dodaj im CSS: wszystkim po <code>background-color</code> i <code>padding: 10px</code>, żeby były widoczne. Następnie dodaj różne wartości <code>margin-bottom</code> — odpowiednio 5px, 25px i 50px. Obserwuj odstępy między blokami.</p>
            <div class="info-box">💡 Margin to odstęp NA ZEWNĄTRZ elementu — odpycha inne elementy.<br>
            <strong>Padding</strong> = przestrzeń wewnątrz (jak wyściółka w pudełku)<br>
            <strong>Margin</strong> = przestrzeń na zewnątrz (jak odległość między pudełkami)</div>
            <div class="warning-box">⚠️ Pamiętaj: margin: 0 auto — wyśrodkowuje blok poziomo!<br>
            Ale element musi mieć ustawioną szerokość (width), żeby auto działało.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 10 ↓↓↓ -->
            <div class="ex-area" id="ex10-area">

                <style>
                    /* Dodaj style dla #blok-1, #blok-2, #blok-3 */
                    /* background-color, padding: 10px, różne margin-bottom */

                </style>

                <div id="blok-1">Blok 1 — margin-bottom: 5px</div>
                <div id="blok-2">Blok 2 — margin-bottom: 25px</div>
                <div id="blok-3">Blok 3 — margin-bottom: 50px</div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 10 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">Border — ramka dookoła elementu</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Nadaj czterem elementom poniżej różne style ramek. Eksperymentuj z grubością, stylem linii i kolorem. Czwarty element zaokrąglij narożniki przez <code>border-radius</code>.</p>
            <div class="code-example">
                <h4>📄 Style ramek do wypróbowania:</h4>
                <pre>
#ramka-1 { border: 1px solid #333; }
#ramka-2 { border: 3px dashed #e74c3c; }
#ramka-3 { border: 4px dotted #2980b9; }
#ramka-4 { border: 2px solid #27ae60; border-radius: 12px; }</pre>
            </div>
            <div class="info-box">💡 Border zawsze opisujemy trzema wartościami: <strong>grubość styl kolor</strong><br>
            Dostępne style: <code>solid</code> (ciągła), <code>dashed</code> (kreski), <code>dotted</code> (kropki), <code>double</code> (podwójna), <code>none</code> (brak)</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 11 ↓↓↓ -->
            <div class="ex-area" id="ex11-area">

                <style>
                    /* Dodaj style dla #ramka-1 do #ramka-4 */
                    /* Pamiętaj też o padding żeby tekst nie przylegał do ramki! */

                </style>

                <p id="ramka-1">Ramka: solid (linia ciągła)</p>
                <p id="ramka-2">Ramka: dashed (kreski)</p>
                <p id="ramka-3">Ramka: dotted (kropki)</p>
                <p id="ramka-4">Ramka: solid + border-radius (zaokrąglona)</p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 11 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Width i height — rozmiar elementu</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Nadaj poniższym kartom konkretne wymiary. Użyj zarówno jednostek <code>px</code> jak i <code>%</code>. Dodaj <code>max-width</code> do ostatniej karty i zmień szerokość okna przeglądarki żeby zobaczyć efekt.</p>
            <div class="code-example">
                <h4>📄 Wymiary do ustawienia:</h4>
                <pre>
#karta-1 { width: 200px;  height: 100px;  background-color: #bbdefb; }
#karta-2 { width: 50%;    height: 80px;   background-color: #90caf9; }
#karta-3 { max-width: 400px; width: 100%; background-color: #64b5f6; }</pre>
            </div>
            <div class="info-box">💡 <code>px</code> = stała liczba pikseli, zawsze taka sama<br>
            <code>%</code> = procent szerokości elementu nadrzędnego — zmienia się z rozmiarem okna<br>
            <code>max-width</code> = "nie przekraczaj tej szerokości" — przydatne przy responsywności</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 12 ↓↓↓ -->
            <div class="ex-area" id="ex12-area">

                <style>
                    /* Dodaj style dla #karta-1, #karta-2, #karta-3 */
                    /* Każda karta powinna mieć też padding: 10px i margin-bottom: 10px */

                </style>

                <div id="karta-1">Karta 1 — stała szerokość 200px</div>
                <div id="karta-2">Karta 2 — 50% szerokości rodzica</div>
                <div id="karta-3">Karta 3 — max-width: 400px, width: 100%</div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 12 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK D: STYLOWANIE FORMULARZY
         Ćwiczenia 13–15
         ========================================== -->

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Stylowanie pól input</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej jest gotowy formularz bez żadnych stylów. Dodaj CSS który sprawi że pola będą wyglądały jak na nowoczesnej stronie: szerokość 100%, odpowiedni padding, zaokrąglona ramka i ładny kolor obramowania.</p>
            <div class="code-example">
                <h4>📄 Style do dodania (na początek):</h4>
                <pre>
#ex13-area input[type="text"],
#ex13-area input[type="email"] {
    width: 100%;
    padding: 10px 14px;
    border: 2px solid #a1c4fd;
    border-radius: 6px;
    font-size: 16px;
    margin-bottom: 10px;
}</pre>
            </div>
            <div class="info-box">💡 Selektor <code>input[type="text"]</code> wybiera tylko inputy tekstowe — nie ruszamy checkboxów!<br>
            Łączenie selektorów przecinkiem pozwala zastosować te same style do wielu elementów naraz.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 13 ↓↓↓ -->
            <div class="ex-area" id="ex13-area">

                <style>
                    /* Dodaj tu style dla inputów w tym formularzu */
                    /* Użyj selektora #ex13-area input[type="text"] i [type="email"] */

                </style>

                <form action="#" method="post">
                    <label for="ex13-imie">Imię:</label>
                    <input type="text" id="ex13-imie" name="imie" placeholder="Jan">

                    <label for="ex13-email">Email:</label>
                    <input type="email" id="ex13-email" name="email" placeholder="jan@example.com">
                </form>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 13 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Stylowanie przycisku</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wystyluj przycisk Wyślij tak żeby wyglądał profesjonalnie. Użyj: koloru tła, koloru tekstu, paddingu, zaokrąglonych rogów i zmiany kursora. Następnie dodaj efekt <code>:hover</code> który zmienia kolor tła gdy najedziesz myszą.</p>
            <div class="code-example">
                <h4>📄 Bazowy styl przycisku + hover:</h4>
                <pre>
#ex14-area button {
    background-color: #1565c0;
    color: white;
    padding: 12px 30px;
    border: none;
    border-radius: 6px;
    font-size: 16px;
    cursor: pointer;
}

#ex14-area button:hover {
    background-color: #0d47a1;   /* ciemniejszy przy najechaniu */
}</pre>
            </div>
            <div class="info-box">💡 <code>cursor: pointer</code> — zamienia kursor w "rączkę" jak przy linkach<br>
            <code>border: none</code> — usuwa domyślną ramkę przeglądarki z przycisku<br>
            <code>:hover</code> — pseudo-klasa, aktywuje się gdy mysz jest nad elementem</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 14 ↓↓↓ -->
            <div class="ex-area" id="ex14-area">

                <style>
                    /* Dodaj style dla przycisku i efekt :hover */

                </style>

                <button type="button">Wyślij formularz</button>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 14 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Łączenie formularzy i Box Model</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Nadaj formularzowi poniżej "ramkę karty" — tło białe, zaokrąglone narogi, cień i padding. Wystyluj też etykiety aby były pogrubione i wyświetlały się w osobnej linii (każda nad swoim polem).</p>
            <div class="code-example">
                <h4>📄 Styl "karty" formularza:</h4>
                <pre>
#ex15-area form {
    background-color: white;
    border: 1px solid #c5d8fd;
    border-radius: 10px;
    padding: 25px;
    max-width: 400px;
}

#ex15-area label {
    display: block;      /* każda etykieta w osobnej linii */
    font-weight: bold;
    margin-bottom: 5px;
    color: #333;
}</pre>
            </div>
            <div class="info-box">💡 <code>display: block</code> na etykiecie sprawi że będzie zajmować całą linię.<br>
            Domyślnie label jest <code>inline</code> — siedzi obok inputa w tej samej linii.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 15 ↓↓↓ -->
            <div class="ex-area" id="ex15-area">

                <style>
                    /* Dodaj styl "karty" dla formularza i styl dla label */
                    /* Dodaj też margin-bottom między polami dla czytelności */

                </style>

                <form action="#" method="post">
                    <label for="ex15-imie">Imię:</label>
                    <input type="text" id="ex15-imie" name="imie" placeholder="Jan">

                    <label for="ex15-email">E-mail:</label>
                    <input type="email" id="ex15-email" name="email" placeholder="jan@example.com">

                    <label for="ex15-temat">Temat:</label>
                    <input type="text" id="ex15-temat" name="temat" placeholder="W sprawie...">

                    <button type="submit">Wyślij</button>
                </form>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 15 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK E: PROJEKT KOŃCOWY
         Ćwiczenie 16
         ========================================== -->

    <!-- ĆWICZENIE 16 — PROJEKT KOŃCOWY -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">16</div>
            <div class="task-title">🏆 PROJEKT KOŃCOWY — Formularz rejestracji</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>formularz_rejestracji.html</code> stwórz kompletny, wystylowany formularz rejestracji na szkolny kurs programowania. Formularz powinien być estetyczny — wyobraź sobie że to prawdziwa strona szkoły.</p>

            <div style="background: #e3f2fd; border: 2px solid #a1c4fd; border-radius: 8px; padding: 20px; margin: 10px 0;">
                <h3 style="color: #1565c0; margin-bottom: 12px;">📋 Wymagania projektu:</h3>
                <ul style="margin-left: 20px; color: #555; line-height: 2;">
                    <li>✅ Poprawny szkielet HTML5 z lang="pl"</li>
                    <li>✅ Formularz z <code>action</code> i <code>method="post"</code></li>
                    <li>✅ Pole tekstowe — imię i nazwisko (z label i placeholder)</li>
                    <li>✅ Pole email — adres e-mail uczestnika</li>
                    <li>✅ Pole number — wiek (min="15" max="25")</li>
                    <li>✅ Select — wybór poziomu: Początkujący / Średniozaawansowany / Zaawansowany</li>
                    <li>✅ Minimum 3 checkboxy — jakie technologie uczestnik już zna</li>
                    <li>✅ Textarea — "Dlaczego chcesz wziąć udział w kursie?" (rows="4")</li>
                    <li>✅ Przycisk submit i reset</li>
                    <li>✅ Każde pole ma etykietę label połączoną przez for/id</li>
                    <li>✅ CSS: formularz w "kartce" (białe tło, border, padding, border-radius)</li>
                    <li>✅ CSS: inputy mają padding, border i border-radius</li>
                    <li>✅ CSS: przycisk submit ma kolor tła i efekt :hover</li>
                </ul>
            </div>

            <div class="warning-box">⚠️ Projekt tworzysz w NOWYM pliku <code>formularz_rejestracji.html</code>!<br>
            Napisz cały szkielet HTML od nowa — to dobry trening przed egzaminem.</div>

            <div class="info-box">💡 Nie musisz mieć prawdziwego action= — możesz wpisać action="#"<br>
            Ważna jest poprawna <strong>struktura</strong> formularza i <strong>wygląd</strong> — to sprawdzane na INF.03!</div>
        </div>
    </div>

    <footer class="page-footer">
        <p>HTML5 i CSS — Część 2 | Formularze + Box Model | INF.03</p>
        <p style="margin-top: 10px; font-size: 0.9em;">📋 Formularze | 📦 Box Model | 🎨 Stylowanie</p>
    </footer>

</div>
</body>
</html>
```

---

## 📋 LISTA ĆWICZEŃ

### Blok A — Podstawy formularza (ćwiczenia 1–4)

| Nr | Temat | Tagi / atrybuty |
|----|-------|-----------------|
| 1 | Szkielet formularza | form action, method |
| 2 | Pole tekstowe z etykietą | input type="text", label for, id, name |
| 3 | Typy pól: email, password, number | type, min, max |
| 4 | Przyciski i placeholder | type="submit", type="reset", placeholder |

### Blok B — Więcej typów pól (ćwiczenia 5–8)

| Nr | Temat | Tagi / atrybuty |
|----|-------|-----------------|
| 5 | Checkboxy | type="checkbox", checked, value |
| 6 | Radio | type="radio", name (grupowanie) |
| 7 | Lista rozwijana | select, option, selected |
| 8 | Pole wieloliniowe | textarea, rows, cols |

### Blok C — Box Model (ćwiczenia 9–12)

| Nr | Temat | Właściwości CSS |
|----|-------|-----------------|
| 9 | Padding | padding, padding-top/right/bottom/left |
| 10 | Margin | margin, margin-bottom, margin: auto |
| 11 | Border | border, border-style, border-radius |
| 12 | Width i height | width, height, max-width, jednostki px i % |

### Blok D — Stylowanie formularzy (ćwiczenia 13–15)

| Nr | Temat | Właściwości CSS |
|----|-------|-----------------|
| 13 | Stylowanie inputów | input[type="text"], width, padding, border |
| 14 | Stylowanie przycisku | background-color, cursor, :hover |
| 15 | Formularz jako karta | background-color, border-radius, display: block |

### Blok E — Projekt (ćwiczenie 16)

| Nr | Temat | Zakres |
|----|-------|--------|
| 16 | 🏆 Formularz rejestracji | Wszystko z bloków A–D w nowym pliku |

Link do wysłania plików ćwiczeń (tylko plik HTML):

Klasa 3 TIe Jastrzębie Zdrój: https://www.dropbox.com/request/0YvpR9U7kG5AyN9UzRI9

Klasa 4 TIe Jastrzębie Zdrój: https://www.dropbox.com/request/BvcS23qHZY2s4uk3K1R6

UWAGA Brak wysłania efektów pracy w terminie wyznaczonym przez nauczyciela to ocena ndst!
