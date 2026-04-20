# 📝 SZABLON HTML — CZĘŚĆ 1c — TABELE HTML I CSS

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT — CO JUŻ WIESZ I CO DODAMY

### Znasz już (z poprzedniego semestru):

```html
<table>
    <thead>
        <tr><th>Nagłówek</th></tr>
    </thead>
    <tbody>
        <tr><td>Dane</td></tr>
    </tbody>
    <tfoot>
        <tr><td>Podsumowanie</td></tr>
    </tfoot>
</table>

colspan="2"   → scal 2 kolumny poziomo
rowspan="3"   → scal 3 wiersze pionowo
```

### Dodajemy teraz — stylowanie CSS:

```css
/* 1. Scalenie obramowań (KLUCZOWE — zawsze!) */
table {
    border-collapse: collapse; /* bez tego: podwójne linie między komórkami */
    width: 100%;
}

/* 2. Obramowanie i padding komórek */
th, td {
    border: 1px solid #ccc;
    padding: 10px 14px;
    text-align: left;
}

/* 3. Kolor nagłówka */
thead th {
    background-color: rgb(78, 205, 196);
    color: white;
}

/* 4. Naprzemienne kolory wierszy — "zebra" */
tbody tr:nth-child(even) {
    background-color: #f0fafa;
}

/* 5. Efekt hover — podświetlenie wiersza */
tbody tr:hover {
    background-color: #d0f0ee;
    cursor: pointer;
}

/* 6. Stopka tabeli */
tfoot td {
    font-weight: bold;
    background-color: #e8f8f7;
}
```

### Dlaczego tabele są ważne w INF.03?

Na egzaminie praktycznym i w przyszłej pracy z PHP/MySQL będziesz pobierać dane z bazy i wyświetlać je w tabeli HTML. Przykład typowego kodu PHP:

```php
// Pętla wyświetlająca rekordy z bazy — dane trafiają w <td>
while ($row = mysqli_fetch_assoc($wynik)) {
    echo "<tr>";
    echo "<td>" . $row['imie'] . "</td>";
    echo "<td>" . $row['nazwisko'] . "</td>";
    echo "<td>" . $row['email'] . "</td>";
    echo "</tr>";
}
```

Żeby ten kod wyglądał dobrze — tabela HTML musi być poprawnie zbudowana i ostylowana. Tego uczymy się teraz.

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 — HTML5 i CSS Część 1c — Tabele</title>
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
            background: linear-gradient(135deg, #4ecdc4 0%, #44a08d 100%);
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
            background: #4ecdc4;
            color: white;
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

        .difficulty-star { color: #ffa500; }

        .task-content {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 6px;
            border-left: 4px solid #4ecdc4;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #e8f8f7;
            border: 1px solid #80cbc4;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #00695c;
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
            border: 2px dashed #4ecdc4;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            min-height: 60px;
            overflow-x: auto; /* tabele mogą być szerokie */
        }

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
        <h1>🟦 Tabele HTML i CSS</h1>
        <p>Część 1c — HTML5 i CSS | INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: SEMANTYCZNA BUDOWA TABELI
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">Pełna struktura tabeli — thead, tbody, tfoot, caption</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę listy uczniów według poniższej specyfikacji. Użyj wszystkich semantycznych sekcji tabeli.</p>
            <div class="code-example">
                <h4>📋 Specyfikacja tabeli:</h4>
                <pre>
caption:   "Lista uczniów klasy 3TI"
thead:     Lp. | Imię i nazwisko | Klasa | Średnia ocen
tbody:     min. 4 wiersze z danymi uczniów
tfoot:     "Liczba uczniów: 4" — scalenie 3 ostatnich kolumn (colspan="3")</pre>
            </div>
            <div class="info-box">💡 <code>&lt;caption&gt;</code> = tytuł tabeli — umieszczaj go jako PIERWSZE dziecko <code>&lt;table&gt;</code><br>
            Czytniki ekranowe ogłaszają caption zanim przeczytają dane — ważne dla dostępności.<br>
            CSS: <code>caption-side: bottom</code> przenosi tytuł pod tabelę.</div>
            <div class="warning-box">⚠️ <code>&lt;tfoot&gt;</code> piszemy w HTML PO <code>&lt;tbody&gt;</code> — ale przeglądarka i tak wyświetli go na dole tabeli.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <style>
                    /* Minimalne style żeby tabela była czytelna */
                    #ex1-area table { border-collapse: collapse; width: 100%; }
                    #ex1-area th, #ex1-area td {
                        border: 1px solid #80cbc4;
                        padding: 8px 12px;
                    }
                    #ex1-area caption {
                        font-weight: bold;
                        color: #00695c;
                        margin-bottom: 8px;
                        font-size: 1.05em;
                    }
                    #ex1-area thead th { background-color: #4ecdc4; color: white; }
                    #ex1-area tfoot td { background-color: #e8f8f7; font-weight: bold; }
                </style>

                <!-- Wstaw tu tabelę: table > caption + thead + tbody + tfoot -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">Atrybut scope — dostępność nagłówków</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę planu zajęć z atrybutem <code>scope</code> na każdym nagłówku. Nagłówki kolumn (dni tygodnia) mają <code>scope="col"</code>, nagłówki wierszy (godziny) mają <code>scope="row"</code>.</p>
            <div class="code-example">
                <h4>📄 Wzorzec użycia scope:</h4>
                <pre>
&lt;thead&gt;
    &lt;tr&gt;
        &lt;th scope="col"&gt;Godzina&lt;/th&gt;
        &lt;th scope="col"&gt;Poniedziałek&lt;/th&gt;
        &lt;th scope="col"&gt;Wtorek&lt;/th&gt;
    &lt;/tr&gt;
&lt;/thead&gt;
&lt;tbody&gt;
    &lt;tr&gt;
        &lt;th scope="row"&gt;8:00 – 8:45&lt;/th&gt;
        &lt;td&gt;Matematyka&lt;/td&gt;
        &lt;td&gt;Informatyka&lt;/td&gt;
    &lt;/tr&gt;
&lt;/tbody&gt;</pre>
            </div>
            <div class="info-box">💡 scope mówi czytnikowi ekranowemu do której osi należy nagłówek:<br>
            <code>scope="col"</code> → nagłówek dotyczy całej kolumny w dół<br>
            <code>scope="row"</code> → nagłówek dotyczy całego wiersza w prawo<br>
            Na egzaminie INF.03 scope może być wymagany w kryteriach dostępności.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <style>
                    #ex2-area table { border-collapse: collapse; width: 100%; }
                    #ex2-area th, #ex2-area td {
                        border: 1px solid #80cbc4;
                        padding: 8px 12px;
                        text-align: center;
                    }
                    #ex2-area thead th {
                        background-color: #4ecdc4;
                        color: white;
                    }
                    #ex2-area tbody th {
                        background-color: #e8f8f7;
                        color: #00695c;
                        font-size: 0.9em;
                        white-space: nowrap;
                    }
                </style>

                <!-- Plan zajęć: thead z scope="col" dla dni, tbody z scope="row" dla godzin -->
                <!-- Min. 3 dni tygodnia i 4 lekcje -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">colspan i rowspan — scalanie komórek</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę harmonogramu projektu według poniższego wzoru. Wymaga zarówno <code>colspan</code> jak i <code>rowspan</code>.</p>
            <div class="code-example">
                <h4>📐 Wzór tabeli do odtworzenia:</h4>
                <pre>
┌─────────────┬──────────────────────┬────────────┐
│   Zadanie   │       Termin         │  Osoba     │
├─────────────┼──────────┬───────────┤            │
│             │  Start   │   Koniec  │            │
├─────────────┼──────────┼───────────┼────────────┤
│  Frontend   │ 01.01    │  15.01    │  Kowalski  │
├─────────────┤          │           ├────────────┤
│  Backend    │          │           │  Nowak     │
├─────────────┼──────────┴───────────┴────────────┤
│  Razem:     │        2 zadania                  │
└─────────────┴───────────────────────────────────┘</pre>
            </div>
            <div class="warning-box">⚠️ Najczęstszy błąd przy rowspan: gdy komórka zajmuje 2 wiersze — w DRUGIM wierszu NIE piszesz tej komórki ponownie! Przeglądarka automatycznie "rezerwuje" to miejsce.</div>
            <div class="info-box">💡 Trick jak liczyć: zanim napiszesz kod, zaznacz ołówkiem na kartce które komórki się scalają. Sprawdź czy suma komórek w każdym wierszu daje tę samą liczbę kolumn.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <style>
                    #ex3-area table { border-collapse: collapse; }
                    #ex3-area th, #ex3-area td {
                        border: 2px solid #4ecdc4;
                        padding: 10px 16px;
                        text-align: center;
                    }
                    #ex3-area th { background-color: #4ecdc4; color: white; }
                    #ex3-area tfoot td {
                        background-color: #e8f8f7;
                        font-weight: bold;
                    }
                </style>

                <!-- Tabela harmonogramu z colspan i rowspan -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">colgroup i col — style dla całych kolumn</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Użyj elementów <code>&lt;colgroup&gt;</code> i <code>&lt;col&gt;</code> żeby nadać kolumnom tabeli różne szerokości i kolory tła — bez dodawania klas do każdej komórki osobno.</p>
            <div class="code-example">
                <h4>📄 Wzorzec colgroup:</h4>
                <pre>
&lt;table&gt;
    &lt;colgroup&gt;
        &lt;col style="width: 5%; background-color: #e8f8f7;"&gt;  &lt;!-- kolumna Lp. --&gt;
        &lt;col style="width: 35%;"&gt;                            &lt;!-- Imię i nazwisko --&gt;
        &lt;col style="width: 20%;"&gt;                            &lt;!-- Klasa --&gt;
        &lt;col style="width: 20%; background-color: #fff9e6;"&gt; &lt;!-- Ocena --&gt;
        &lt;col style="width: 20%;"&gt;                            &lt;!-- Status --&gt;
    &lt;/colgroup&gt;
    &lt;thead&gt;...&lt;/thead&gt;
    &lt;tbody&gt;...&lt;/tbody&gt;
&lt;/table&gt;</pre>
            </div>
            <div class="info-box">💡 <code>&lt;col&gt;</code> jest elementem pustym (samozamykającym) — nie ma treści wewnątrz.<br>
            Działa głównie dla: <code>width</code>, <code>background-color</code>, <code>visibility</code>.<br>
            Liczba elementów <code>&lt;col&gt;</code> musi odpowiadać liczbie kolumn tabeli.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <style>
                    #ex4-area table { border-collapse: collapse; width: 100%; }
                    #ex4-area th, #ex4-area td {
                        border: 1px solid #80cbc4;
                        padding: 8px 12px;
                    }
                    #ex4-area thead th { background-color: #4ecdc4; color: white; }
                </style>

                <!-- table > colgroup (5 col z różnymi szerokościami) + thead + tbody -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: CSS — STYLOWANIE TABELI
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">border-collapse — scalanie obramowań</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tę samą prostą tabelę dwa razy — raz z <code>border-collapse: separate</code> (domyślne), raz z <code>border-collapse: collapse</code>. Obserwuj jak zmienia się wygląd obramowań i jaka jest różnica w odstępach.</p>
            <div class="code-example">
                <h4>📄 Dwa style do porównania:</h4>
                <pre>
#tabela-separate {
    border-collapse: separate;  /* domyślne — podwójne linie */
    border-spacing: 3px;        /* odstęp między komórkami */
}

#tabela-collapse {
    border-collapse: collapse;  /* linie scalane — profesjonalnie */
}</pre>
            </div>
            <div class="warning-box">⚠️ <code>border-collapse: collapse</code> to standard — używaj ZAWSZE przy stylowaniu tabel.<br>
            Bez niego każda komórka ma własną ramkę i powstają "podwójne linie" między nimi.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <style>
                    .ex5-wrapper {
                        display: flex;
                        gap: 30px;
                        flex-wrap: wrap;
                        align-items: flex-start;
                    }

                    .ex5-wrapper p {
                        font-weight: bold;
                        color: #00695c;
                        margin-bottom: 8px;
                        font-size: 0.9em;
                    }

                    /* Dodaj style dla #tabela-separate i #tabela-collapse */
                    .ex5-tbl th, .ex5-tbl td {
                        border: 2px solid #4ecdc4;
                        padding: 8px 14px;
                    }
                    .ex5-tbl thead th { background-color: #4ecdc4; color: white; }
                </style>

                <div class="ex5-wrapper">
                    <div>
                        <p>border-collapse: separate (domyślne):</p>
                        <table class="ex5-tbl" id="tabela-separate">
                            <!-- 3 wiersze × 3 kolumny danych produktów -->
                        </table>
                    </div>
                    <div>
                        <p>border-collapse: collapse (zalecane ✅):</p>
                        <table class="ex5-tbl" id="tabela-collapse">
                            <!-- Ta sama tabela -->
                        </table>
                    </div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">Kompletne stylowanie — padding, kolory, text-align</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Ostyluj tabelę cennika usług według poniższej specyfikacji kolorystycznej. Wszystkie style piszesz w sekcji <code>&lt;style&gt;</code>.</p>
            <div class="code-example">
                <h4>📋 Specyfikacja stylów:</h4>
                <pre>
table:          border-collapse: collapse, width: 100%
th, td:         padding: 12px 16px, border: 1px solid rgb(180,225,220)
thead th:       background-color: rgb(68, 160, 141), color: white,
                text-align: left, font-size: 0.95em, letter-spacing: 0.5px
tbody td:       color: rgb(50,50,50), font-size: 0.95em
tbody tr:       background-color: white
tfoot td:       background-color: rgb(232, 248, 246),
                font-weight: bold, color: rgb(0, 105, 92)
caption:        text-align: left, font-size: 1.1em, font-weight: bold,
                color: rgb(68,160,141), padding-bottom: 10px</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <style>
                    /* Dodaj tu wszystkie style według specyfikacji */
                </style>

                <table id="tabela-cennik">
                    <caption>Cennik usług serwisowych</caption>
                    <thead>
                        <tr>
                            <th>Usługa</th>
                            <th>Czas realizacji</th>
                            <th>Cena netto</th>
                            <th>Cena brutto</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Naprawa komputera</td>
                            <td>1–2 dni robocze</td>
                            <td>120,00 zł</td>
                            <td>147,60 zł</td>
                        </tr>
                        <tr>
                            <td>Instalacja systemu</td>
                            <td>2–3 godziny</td>
                            <td>80,00 zł</td>
                            <td>98,40 zł</td>
                        </tr>
                        <tr>
                            <td>Usuwanie wirusów</td>
                            <td>1 dzień roboczy</td>
                            <td>90,00 zł</td>
                            <td>110,70 zł</td>
                        </tr>
                        <tr>
                            <td>Konsultacja zdalna</td>
                            <td>30 minut</td>
                            <td>50,00 zł</td>
                            <td>61,50 zł</td>
                        </tr>
                    </tbody>
                    <tfoot>
                        <tr>
                            <td colspan="2">Suma wszystkich usług:</td>
                            <td>340,00 zł</td>
                            <td>418,20 zł</td>
                        </tr>
                    </tfoot>
                </table>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">Naprzemienne kolory wierszy — :nth-child</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Dodaj do tabeli z ćwiczenia 6 efekt "zebry" — naprzemienne kolory wierszy. Parzyste wiersze mają jaśniejsze tło. Użyj selektora <code>:nth-child(even)</code> i <code>:nth-child(odd)</code>.</p>
            <div class="code-example">
                <h4>📄 Selektor :nth-child:</h4>
                <pre>
tbody tr:nth-child(odd)  { background-color: white; }
tbody tr:nth-child(even) { background-color: rgb(232, 248, 246); }

/* Można też podać konkretny numer: */
tbody tr:nth-child(3) { font-weight: bold; }  /* tylko 3. wiersz */

/* Lub wzorzec: co trzeci wiersz zaczynając od 1: */
tbody tr:nth-child(3n+1) { background-color: #fffde7; }</pre>
            </div>
            <div class="info-box">💡 "Zebra" znacznie poprawia czytelność długich tabel z danymi.<br>
            W PHP, gdy wyświetlasz dziesiątki rekordów z bazy danych, zebra jest standardem.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <style>
                    #ex7-tabela {
                        border-collapse: collapse;
                        width: 100%;
                    }

                    #ex7-tabela th, #ex7-tabela td {
                        border: 1px solid #80cbc4;
                        padding: 10px 14px;
                    }

                    #ex7-tabela thead th {
                        background-color: rgb(68, 160, 141);
                        color: white;
                        text-align: left;
                    }

                    /* Dodaj: nth-child(even) i nth-child(odd) na tbody tr */
                </style>

                <table id="ex7-tabela">
                    <thead>
                        <tr>
                            <th>Lp.</th>
                            <th>Produkt</th>
                            <th>Kategoria</th>
                            <th>Cena</th>
                            <th>Stan magazynu</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr><td>1</td><td>Laptop Dell XPS</td><td>Komputery</td><td>3 999 zł</td><td>5 szt.</td></tr>
                        <tr><td>2</td><td>Monitor 27" LG</td><td>Monitory</td><td>1 299 zł</td><td>12 szt.</td></tr>
                        <tr><td>3</td><td>Klawiatura Logitech</td><td>Akcesoria</td><td>349 zł</td><td>28 szt.</td></tr>
                        <tr><td>4</td><td>Mysz bezprzewodowa</td><td>Akcesoria</td><td>189 zł</td><td>34 szt.</td></tr>
                        <tr><td>5</td><td>Dysk SSD 1TB</td><td>Podzespoły</td><td>279 zł</td><td>17 szt.</td></tr>
                        <tr><td>6</td><td>Słuchawki Sony</td><td>Audio</td><td>449 zł</td><td>9 szt.</td></tr>
                        <tr><td>7</td><td>Kamera internetowa</td><td>Akcesoria</td><td>199 zł</td><td>22 szt.</td></tr>
                    </tbody>
                </table>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">Efekt hover na wierszu tabeli</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Dodaj do tabeli z ćwiczenia 7 efekt podświetlenia wiersza po najechaniu myszką. Użyj pseudoklasy <code>:hover</code> na <code>tbody tr</code>. Dodaj też <code>transition</code> żeby zmiana była płynna.</p>
            <div class="code-example">
                <h4>📄 Hover na wierszu:</h4>
                <pre>
tbody tr {
    transition: background-color 0.2s ease;
}

tbody tr:hover {
    background-color: rgb(178, 223, 219);
    cursor: pointer; /* kursor zmienia się na rączkę */
}</pre>
            </div>
            <div class="info-box">💡 W aplikacjach bazodanowych hover + cursor: pointer sugeruje użytkownikowi,<br>
            że może kliknąć wiersz i zobaczyć szczegóły rekordu.<br>
            <code>transition</code> sprawia że zmiana jest płynna a nie gwałtowna.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <style>
                    #ex8-tabela {
                        border-collapse: collapse;
                        width: 100%;
                    }

                    #ex8-tabela th, #ex8-tabela td {
                        border: 1px solid #80cbc4;
                        padding: 10px 14px;
                    }

                    #ex8-tabela thead th {
                        background-color: rgb(68, 160, 141);
                        color: white;
                        text-align: left;
                    }

                    #ex8-tabela tbody tr:nth-child(even) {
                        background-color: rgb(232, 248, 246);
                    }

                    /* Dodaj tu: transition i :hover na tbody tr */
                </style>

                <table id="ex8-tabela">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Imię i nazwisko</th>
                            <th>Email</th>
                            <th>Telefon</th>
                            <th>Miasto</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr><td>1</td><td>Jan Kowalski</td><td>jan@example.com</td><td>600 100 200</td><td>Warszawa</td></tr>
                        <tr><td>2</td><td>Maria Nowak</td><td>maria@example.com</td><td>601 200 300</td><td>Kraków</td></tr>
                        <tr><td>3</td><td>Piotr Wiśniewski</td><td>piotr@example.com</td><td>602 300 400</td><td>Gdańsk</td></tr>
                        <tr><td>4</td><td>Anna Wójcik</td><td>anna@example.com</td><td>603 400 500</td><td>Wrocław</td></tr>
                        <tr><td>5</td><td>Tomasz Lewandowski</td><td>tomek@example.com</td><td>604 500 600</td><td>Poznań</td></tr>
                    </tbody>
                </table>
                <p style="color:#888; font-size:0.85em; margin-top:8px;">
                    ↑ Najedź myszką na wiersz — powinien się podświetlić.
                </p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: ZAAWANSOWANE STYLOWANIE
         Ćwiczenia 9–12
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">Tabela sticky header — nagłówek przyklejony przy scrollowaniu</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz długą tabelę (min. 12 wierszy) owiniętą w kontener z ograniczoną wysokością i <code>overflow-y: scroll</code>. Nagłówek tabeli ma <code>position: sticky; top: 0</code> — zostaje widoczny podczas scrollowania danych.</p>
            <div class="code-example">
                <h4>📄 Wzorzec sticky header:</h4>
                <pre>
.tabela-kontener {
    max-height: 300px;
    overflow-y: scroll;
    border: 1px solid #80cbc4;
    border-radius: 6px;
}

.tabela-kontener table {
    border-collapse: collapse;
    width: 100%;
}

.tabela-kontener thead th {
    position: sticky;
    top: 0;           /* przyklej do górnej krawędzi kontenera */
    z-index: 1;       /* nad treścią tabeli */
    background-color: rgb(68, 160, 141); /* wymagane — inaczej przezroczysty! */
}</pre>
            </div>
            <div class="warning-box">⚠️ Sticky header WYMAGA ustawionego <code>background-color</code> na <code>thead th</code>.<br>
            Bez niego nagłówek jest "przezroczysty" i przez niego przebija się treść wierszy.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 9 ↓↓↓ -->
            <div class="ex-area" id="ex9-area">

                <style>
                    /* Dodaj tu style dla .ex9-kontener i tabeli wewnątrz */
                </style>

                <div class="ex9-kontener">
                    <table id="ex9-tabela">
                        <thead>
                            <tr>
                                <th>Lp.</th>
                                <th>Przedmiot</th>
                                <th>Nauczyciel</th>
                                <th>Sala</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr><td>1</td><td>Matematyka</td><td>mgr Kowalska</td><td>101</td></tr>
                            <tr><td>2</td><td>Informatyka</td><td>mgr Lamparski</td><td>Pracownia 1</td></tr>
                            <tr><td>3</td><td>Język Polski</td><td>mgr Wiśniewska</td><td>203</td></tr>
                            <tr><td>4</td><td>Historia</td><td>mgr Nowak</td><td>301</td></tr>
                            <tr><td>5</td><td>Fizyka</td><td>mgr Wójcik</td><td>115</td></tr>
                            <tr><td>6</td><td>Chemia</td><td>mgr Lewandowska</td><td>Lab 2</td></tr>
                            <tr><td>7</td><td>Biologia</td><td>mgr Zielińska</td><td>Lab 1</td></tr>
                            <tr><td>8</td><td>Angielski</td><td>mgr Brown</td><td>215</td></tr>
                            <tr><td>9</td><td>Wychowanie Fizyczne</td><td>mgr Adamski</td><td>Gym</td></tr>
                            <tr><td>10</td><td>Podstawy Przedsiębiorczości</td><td>mgr Woźniak</td><td>302</td></tr>
                            <tr><td>11</td><td>Religia</td><td>ks. Tomaszewski</td><td>201</td></tr>
                            <tr><td>12</td><td>Sieci komputerowe</td><td>mgr Dąbrowski</td><td>Pracownia 2</td></tr>
                        </tbody>
                    </table>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 9 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">Wyróżnianie komórek wartościami — klasy CSS na td</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę wyników egzaminów. Komórki z ocenami koloruj przez klasy CSS: <code>.ocena-bdb</code> (zielone), <code>.ocena-db</code> (jasnozielone), <code>.ocena-dst</code> (żółte), <code>.ocena-ndst</code> (czerwone). Klasy dodawaj bezpośrednio na <code>&lt;td&gt;</code>.</p>
            <div class="code-example">
                <h4>📄 Klasy dla wartości:</h4>
                <pre>
.ocena-bdb  { background-color: #d4edda; color: #155724; font-weight: bold; }
.ocena-db   { background-color: #e8f5e9; color: #2e7d32; }
.ocena-dst  { background-color: #fff9c4; color: #f57f17; }
.ocena-ndst { background-color: #ffebee; color: #b71c1c; font-weight: bold; }

&lt;td class="ocena-bdb"&gt;6&lt;/td&gt;
&lt;td class="ocena-ndst"&gt;1&lt;/td&gt;</pre>
            </div>
            <div class="info-box">💡 W PHP takie klasy dodajesz dynamicznie w pętli:<br>
            <code>$klasa = ($ocena >= 5) ? 'ocena-bdb' : (($ocena >= 3) ? 'ocena-dst' : 'ocena-ndst');</code><br>
            <code>echo "&lt;td class='$klasa'&gt;$ocena&lt;/td&gt;";</code><br>
            To jest właśnie połączenie CSS z logiką programowania!</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 10 ↓↓↓ -->
            <div class="ex-area" id="ex10-area">

                <style>
                    #ex10-tabela { border-collapse: collapse; width: 100%; }
                    #ex10-tabela th, #ex10-tabela td {
                        border: 1px solid #80cbc4;
                        padding: 10px 14px;
                        text-align: center;
                    }
                    #ex10-tabela thead th {
                        background-color: rgb(68, 160, 141);
                        color: white;
                    }
                    #ex10-tabela tbody td:first-child { text-align: left; font-weight: bold; }

                    /* Dodaj tu 4 klasy dla ocen */
                </style>

                <table id="ex10-tabela">
                    <caption>Wyniki egzaminów — klasa 3TI</caption>
                    <thead>
                        <tr>
                            <th scope="col">Uczeń</th>
                            <th scope="col">HTML/CSS</th>
                            <th scope="col">JavaScript</th>
                            <th scope="col">Bazy danych</th>
                            <th scope="col">Sieci</th>
                            <th scope="col">Średnia</th>
                        </tr>
                    </thead>
                    <tbody>
                        <!-- Dodaj klasy .ocena-* na odpowiednich komórkach td -->
                        <tr>
                            <td>Kowalski Jan</td>
                            <td class="ocena-bdb">6</td>
                            <td class="ocena-db">4</td>
                            <td class="ocena-bdb">5</td>
                            <td class="ocena-db">4</td>
                            <td class="ocena-bdb">4.75</td>
                        </tr>
                        <tr>
                            <td>Nowak Maria</td>
                            <td class="ocena-db">4</td>
                            <td class="ocena-dst">3</td>
                            <td class="ocena-db">4</td>
                            <td class="ocena-dst">3</td>
                            <td class="ocena-dst">3.5</td>
                        </tr>
                        <tr>
                            <td>Wiśniewski Piotr</td>
                            <td class="ocena-dst">3</td>
                            <td class="ocena-ndst">1</td>
                            <td class="ocena-dst">3</td>
                            <td class="ocena-db">4</td>
                            <td class="ocena-dst">2.75</td>
                        </tr>
                        <tr>
                            <td>Wójcik Anna</td>
                            <td class="ocena-bdb">6</td>
                            <td class="ocena-bdb">6</td>
                            <td class="ocena-bdb">6</td>
                            <td class="ocena-bdb">5</td>
                            <td class="ocena-bdb">5.75</td>
                        </tr>
                    </tbody>
                </table>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 10 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">Responsywna tabela — overflow-x na wąskich ekranach</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Tabele z wieloma kolumnami "wylewają" się poza ekran telefonu. Owiń tabelę w kontener z <code>overflow-x: auto</code> — na wąskim ekranie pojawi się poziomy pasek przewijania, a tabela nie będzie się kurczyć i łamać.</p>
            <div class="code-example">
                <h4>📄 Wzorzec responsywnej tabeli:</h4>
                <pre>
.tabela-responsywna {
    overflow-x: auto;          /* poziomy scroll gdy brakuje miejsca */
    -webkit-overflow-scrolling: touch; /* płynny scroll na iOS */
}

.tabela-responsywna table {
    border-collapse: collapse;
    min-width: 600px;          /* tabela nigdy nie będzie węższa */
    width: 100%;
}</pre>
            </div>
            <div class="info-box">💡 To jest najprostszy i najskuteczniejszy sposób na responsywne tabele.<br>
            Na komputerze wygląda normalnie, na telefonie pojawia się scroll poziomy.<br>
            Alternatywa: @media query zmieniający tabelę na karty (zaawansowane — patrz Część 5B).</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 11 ↓↓↓ -->
            <div class="ex-area" id="ex11-area">

                <style>
                    /* Dodaj tu style dla .ex11-wrapper i tabeli wewnątrz */
                </style>

                <div class="ex11-wrapper">
                    <table id="ex11-tabela">
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Produkt</th>
                                <th>Producent</th>
                                <th>Kategoria</th>
                                <th>Cena</th>
                                <th>VAT</th>
                                <th>Cena brutto</th>
                                <th>Stan</th>
                                <th>Data dostawy</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr><td>1</td><td>Laptop XPS 15</td><td>Dell</td><td>Komputery</td><td>3999</td><td>23%</td><td>4918,77</td><td>5 szt.</td><td>2025-02-10</td></tr>
                            <tr><td>2</td><td>Monitor U2722D</td><td>Dell</td><td>Monitory</td><td>1299</td><td>23%</td><td>1597,77</td><td>12 szt.</td><td>2025-02-15</td></tr>
                            <tr><td>3</td><td>MX Keys Mini</td><td>Logitech</td><td>Klawiatury</td><td>349</td><td>23%</td><td>429,27</td><td>28 szt.</td><td>2025-03-01</td></tr>
                        </tbody>
                    </table>
                </div>
                <p style="color:#888; font-size:0.85em; margin-top:6px;">
                    Zwęź okno przeglądarki — tabela powinna się przewijać poziomo zamiast łamać.
                </p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 11 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Sortowanie wizualne — strzałki w nagłówkach</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę z nagłówkami które wyglądają jak przyciski sortowania — ze strzałką wskazującą aktywną kolumnę. Samo sortowanie realizuje się przez JavaScript lub PHP — tutaj ćwiczymy tylko wizualny efekt przez CSS i klasy HTML.</p>
            <div class="code-example">
                <h4>📄 Klasy sortowania na th:</h4>
                <pre>
th.sort-asc::after  { content: " ▲"; font-size: 0.8em; opacity: 0.7; }
th.sort-desc::after { content: " ▼"; font-size: 0.8em; opacity: 0.7; }

th.sort-asc, th.sort-desc {
    background-color: rgb(44, 130, 110);  /* ciemniejszy nagłówek = aktywny */
    cursor: pointer;
}

thead th {
    cursor: pointer;
    user-select: none; /* nie zaznacza się przy klikaniu */
}

thead th:hover {
    background-color: rgb(56, 148, 126);
}</pre>
            </div>
            <div class="info-box">💡 W prawdziwej aplikacji kliknięcie th wysyła żądanie do PHP:<br>
            <code>SELECT * FROM produkty ORDER BY cena ASC</code><br>
            PHP zwraca posortowane dane i dodaje klasę <code>sort-asc</code> na odpowiedni nagłówek.<br>
            Tutaj uczymy się jak powinno to wyglądać — logikę dodamy na lekcjach PHP.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 12 ↓↓↓ -->
            <div class="ex-area" id="ex12-area">

                <style>
                    #ex12-tabela { border-collapse: collapse; width: 100%; }
                    #ex12-tabela th, #ex12-tabela td {
                        border: 1px solid #80cbc4;
                        padding: 10px 14px;
                    }
                    #ex12-tabela thead th {
                        background-color: rgb(68, 160, 141);
                        color: white;
                        text-align: left;
                    }
                    #ex12-tabela tbody tr:nth-child(even) { background-color: #e8f8f7; }
                    #ex12-tabela tbody tr:hover { background-color: #b2dfdb; }

                    /* Dodaj tu style dla: sort-asc, sort-desc i hover na th */
                </style>

                <table id="ex12-tabela">
                    <thead>
                        <tr>
                            <!-- Dodaj klasy sort-asc lub sort-desc na wybranych th -->
                            <th>Produkt</th>
                            <th class="sort-asc">Cena</th>  <!-- aktywna kolumna -->
                            <th>Kategoria</th>
                            <th>Stan</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr><td>Klawiatura</td><td>349 zł</td><td>Akcesoria</td><td>28</td></tr>
                        <tr><td>Mysz</td><td>189 zł</td><td>Akcesoria</td><td>34</td></tr>
                        <tr><td>Monitor</td><td>1 299 zł</td><td>Monitory</td><td>12</td></tr>
                        <tr><td>Laptop</td><td>3 999 zł</td><td>Komputery</td><td>5</td></tr>
                        <tr><td>Słuchawki</td><td>449 zł</td><td>Audio</td><td>9</td></tr>
                    </tbody>
                </table>
                <p style="color:#888; font-size:0.85em; margin-top:6px;">
                    Najedź myszką na nagłówki — hover powinien działać.
                    Kolumna "Cena" ma klasę sort-asc — widać strzałkę ▲.
                </p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 12 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK D: TABELE W STYLU BAZODANOWYM + PROJEKT
         Ćwiczenia 13–16
         ========================================== -->

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Tabela CRUD — przyciski akcji w ostatniej kolumnie</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W aplikacjach bazodanowych każdy wiersz tabeli zazwyczaj ma przyciski akcji: Edytuj i Usuń. Stwórz tabelę z danymi i ostatnią kolumną zawierającą dwa przyciski stylowane CSS. Przyciski są na razie dekoracyjne (bez JS/PHP).</p>
            <div class="code-example">
                <h4>📄 Wzorzec przycisków akcji:</h4>
                <pre>
&lt;td class="akcje"&gt;
    &lt;button class="btn-edytuj"&gt;✏️ Edytuj&lt;/button&gt;
    &lt;button class="btn-usun"&gt;🗑️ Usuń&lt;/button&gt;
&lt;/td&gt;

.akcje { white-space: nowrap; }

.btn-edytuj {
    background-color: rgb(68, 160, 141);
    color: white;
    border: none;
    padding: 5px 12px;
    border-radius: 4px;
    cursor: pointer;
    font-size: 0.85em;
    margin-right: 5px;
}

.btn-usun {
    background-color: rgb(229, 57, 53);
    color: white;
    border: none;
    padding: 5px 12px;
    border-radius: 4px;
    cursor: pointer;
    font-size: 0.85em;
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 13 ↓↓↓ -->
            <div class="ex-area" id="ex13-area">

                <style>
                    /* Dodaj style dla tabeli i przycisków akcji */
                </style>

                <!-- Tabela: ID | Imię | Nazwisko | Email | Rola | [Edytuj][Usuń] -->
                <!-- Min. 4 wiersze z różnymi rolami: Admin, Użytkownik, Moderator -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 13 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Tabela z paginacją — wizualna nawigacja stron</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę z danymi i pod nią wizualną paginację (numery stron). Paginacja to przyciski lub linki "Poprzednia | 1 | 2 | 3 | Następna". Na razie to tylko HTML+CSS bez PHP — ale taki układ zobaczysz w każdym projekcie bazodanowym.</p>
            <div class="code-example">
                <h4>📄 Wzorzec paginacji:</h4>
                <pre>
&lt;nav class="paginacja" aria-label="Nawigacja stron"&gt;
    &lt;a href="#" class="str-btn"&gt;« Poprzednia&lt;/a&gt;
    &lt;a href="#" class="str-btn"&gt;1&lt;/a&gt;
    &lt;a href="#" class="str-btn aktywna"&gt;2&lt;/a&gt;  &lt;!-- aktywna strona --&gt;
    &lt;a href="#" class="str-btn"&gt;3&lt;/a&gt;
    &lt;a href="#" class="str-btn"&gt;Następna »&lt;/a&gt;
&lt;/nav&gt;

.paginacja { display: flex; gap: 5px; margin-top: 15px; }
.str-btn { padding: 7px 13px; border: 1px solid #80cbc4;
           border-radius: 4px; text-decoration: none; color: #00695c; }
.str-btn.aktywna { background-color: rgb(68,160,141); color: white; }
.str-btn:hover   { background-color: #e8f8f7; }</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 14 ↓↓↓ -->
            <div class="ex-area" id="ex14-area">

                <style>
                    /* Dodaj style dla tabeli i paginacji */
                </style>

                <!-- Tabela z 5 wierszami danych (jakichkolwiek) -->
                <!-- Pod tabelą: nav.paginacja z przyciskami stron -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 14 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Tabela statystyczna z paskami postępu w CSS</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz tabelę wyników sprzedaży gdzie jedna kolumna zamiast liczby pokazuje wizualny pasek postępu. Pasek jest zbudowany z dwóch zagnieżdżonych <code>&lt;div&gt;</code> wewnątrz <code>&lt;td&gt;</code>.</p>
            <div class="code-example">
                <h4>📄 Pasek postępu w komórce:</h4>
                <pre>
&lt;td&gt;
    &lt;div class="pasek-tlo"&gt;
        &lt;div class="pasek-wypelnienie" style="width: 75%"&gt;75%&lt;/div&gt;
    &lt;/div&gt;
&lt;/td&gt;

.pasek-tlo {
    background-color: #e0e0e0;
    border-radius: 4px;
    height: 20px;
    width: 150px;
    overflow: hidden;
}

.pasek-wypelnienie {
    background-color: rgb(68, 160, 141);
    height: 100%;
    border-radius: 4px;
    color: white;
    font-size: 0.75em;
    display: flex;
    align-items: center;
    justify-content: center;
}</pre>
            </div>
            <div class="info-box">💡 Szerokość paska ustawiasz przez <code>style="width: XX%"</code> — to będzie generowane dynamicznie przez PHP:<br>
            <code>$procent = round($sprzedaz / $cel * 100);</code><br>
            <code>echo "&lt;div class='pasek-wypelnienie' style='width:{$procent}%'&gt;";</code></div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 15 ↓↓↓ -->
            <div class="ex-area" id="ex15-area">

                <style>
                    /* Dodaj style dla tabeli, .pasek-tlo, .pasek-wypelnienie */
                </style>

                <!-- Tabela: Handlowiec | Region | Wynik sprzedaży | Realizacja celu [pasek] -->
                <!-- Min. 5 wierszy z różnymi procentami (np. 90%, 45%, 100%, 60%, 78%) -->
                <!-- Pasek powyżej 80% — kolor zielony; poniżej 50% — czerwony (dodaj klasę!) -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 15 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 16 — PROJEKT KOŃCOWY -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">16</div>
            <div class="task-title">🏆 PROJEKT KOŃCOWY — Panel administracyjny w stylu INF.03</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>panel.html</code> z osobnym <code>styl.css</code> stwórz panel administracyjny z tabelą bazy danych. To symulacja strony którą będziesz budować przy pracy z PHP i MySQL.</p>

            <div class="code-example">
                <h4>📐 Diagram układu:</h4>
                <pre>
┌─────────────────────────────────────────────────────┐
│  header — "Panel administracyjny" + nav (Flexbox)   │
│  tło: rgb(44, 130, 110)   tekst biały               │
├─────────────────────────────────────────────────────┤
│  section.pasek-narzedzi                             │
│  [+ Dodaj użytkownika]  [🔍 Szukaj: ________]       │
│  tło: rgb(232, 248, 246)                            │
├─────────────────────────────────────────────────────┤
│  div.tabela-wrapper (overflow-x: auto)               │
│  caption: "Użytkownicy systemu (25 rekordów)"        │
│  ┌────┬────────────┬───────────┬───────┬───────────┐ │
│  │ ID │ Imię i naz.│ Email     │ Rola  │  Akcje    │ │  ← thead sticky
│  ├────┼────────────┼───────────┼───────┼───────────┤ │
│  │  1 │ Jan Kow... │ jan@...   │ Admin │ [✏️][🗑️]  │ │  ← zebra + hover
│  │  2 │ Maria N... │ maria@... │ User  │ [✏️][🗑️]  │ │
│  │ .. │ ...        │ ...       │ ...   │ [✏️][🗑️]  │ │
│  ├────┴────────────┴───────────┼───────┴───────────┤ │
│  │       Łącznie: 5 rekordów   │  3 Admin / 2 User │ │  ← tfoot
│  └─────────────────────────────┴───────────────────┘ │
├─────────────────────────────────────────────────────┤
│  nav.paginacja  « 1 [2] 3 4 5 »                     │
├─────────────────────────────────────────────────────┤
│  footer  © 2025                                     │
└─────────────────────────────────────────────────────┘</pre>
            </div>

            <div style="background:#e8f8f7; border:2px solid #80cbc4; border-radius:8px; padding:20px; margin:10px 0;">
                <h3 style="color:#00695c; margin-bottom:14px;">📋 Wymagania projektu:</h3>
                <ul style="margin-left:20px; color:#555; line-height:2.2;">
                    <li>✅ Pliki: <code>panel.html</code> + <code>styl.css</code> (CSS wyłącznie w osobnym pliku)</li>
                    <li>✅ Header z Flexbox: <code>justify-content:space-between</code>, tło <code>rgb(44,130,110)</code></li>
                    <li>✅ Tabela z: <code>caption</code>, <code>thead</code> (sticky), <code>tbody</code> (min. 5 wierszy), <code>tfoot</code></li>
                    <li>✅ Nagłówki z atrybutem <code>scope="col"</code></li>
                    <li>✅ Kolumna "Rola" — komórki Admin mają klasę <code>.rola-admin</code>, User ma klasę <code>.rola-user</code> z różnymi kolorami</li>
                    <li>✅ Zebra (<code>:nth-child(even)</code>) + hover z <code>transition</code></li>
                    <li>✅ Kolumna Akcje z przyciskami Edytuj (zielony) i Usuń (czerwony)</li>
                    <li>✅ Tfoot z colspan — podsumowanie liczby rekordów</li>
                    <li>✅ Paginacja pod tabelą (<code>&lt;nav&gt;</code> z linkami, jedna strona aktywna)</li>
                    <li>✅ Tabela owinięta w <code>div.tabela-wrapper</code> z <code>overflow-x:auto</code></li>
                </ul>
            </div>

            <div class="warning-box">⚠️ Cały CSS w pliku <code>styl.css</code> — nie używaj atrybutu <code>style=""</code> w HTML, chyba że do szerokości paska postępu.<br>
            Pamiętaj o <code>background-color</code> na <code>thead th</code> przy sticky — bez tego nagłówek jest przezroczysty.</div>
            <div class="info-box">💡 Ten projekt to szablon HTML który uzupełnisz danymi z bazy MySQL na lekcjach PHP.<br>
            Wiersze tabeli będziesz generować w pętli <code>while()</code> zamiast pisać na stałe.<br>
            Im lepiej zbudujesz strukturę teraz — tym łatwiej będzie z PHP!</div>
        </div>
    </div>

    <footer class="page-footer">
        <p>HTML5 i CSS — Część 1c | Tabele | INF.03</p>
        <p style="margin-top:10px; font-size:0.9em;">
            📊 border-collapse | 🦓 :nth-child | 🖱️ :hover | 📌 sticky | 📱 overflow-x
        </p>
    </footer>

</div>
</body>
</html>
```

---

## 📋 LISTA ĆWICZEŃ

### Blok A — Semantyczna budowa tabeli (ćwiczenia 1–4)
| Nr | Temat | Tagi / atrybuty |
|----|-------|-----------------|
| 1 | caption, thead, tbody, tfoot, colspan w tfoot | pełna struktura semantyczna |
| 2 | scope="col" i scope="row" — dostępność | th z scope na planie zajęć |
| 3 | colspan + rowspan razem | harmonogram projektu z scaleniami |
| 4 | colgroup + col — style dla całych kolumn | szerokości i tła kolumn |

### Blok B — CSS: stylowanie tabeli (ćwiczenia 5–8)
| Nr | Temat | Właściwości CSS |
|----|-------|-----------------|
| 5 | border-collapse: separate vs collapse | porównanie — dlaczego collapse jest standardem |
| 6 | Kompletne stylowanie — padding, kolory, text-align | specyfikacja RGB jak na egzaminie |
| 7 | :nth-child(even/odd) — zebra | naprzemienne kolory wierszy |
| 8 | :hover + transition na wierszu | podświetlanie wierszy |

### Blok C — Zaawansowane stylowanie (ćwiczenia 9–12)
| Nr | Temat | Technika |
|----|-------|----------|
| 9 | Sticky header — nagłówek przy scrollowaniu | position: sticky, overflow-y: scroll |
| 10 | Kolorowanie komórek wg wartości | klasy .ocena-* na td |
| 11 | Responsywna tabela — scroll poziomy | overflow-x: auto |
| 12 | Wizualne sortowanie — strzałki w nagłówkach | ::after, klasy sort-asc/sort-desc |

### Blok D — Tabele w stylu bazodanowym + projekt (ćwiczenia 13–16)
| Nr | Temat | Zakres |
|----|-------|--------|
| 13 | Kolumna akcji — przyciski Edytuj i Usuń | CRUD interface |
| 14 | Paginacja pod tabelą | nav z przyciskami stron |
| 15 | Pasek postępu w komórce tabeli | div zagnieżdżony w td, width % |
| 16 | 🏆 Panel administracyjny | panel.html + styl.css — wszystkie techniki |


Wykonane ćwiczenia wysłać:

3TIe JAS https://www.dropbox.com/request/npji3p1oyxueoai4cwew
