# 📝 SZABLON HTML — CZĘŚĆ 4 — POZYCJONOWANIE CSS

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT — ŚCIĄGAWKA PRZED ĆWICZENIAMI

### Co to jest pozycjonowanie CSS?

Właściwość `position` kontroluje **jak element jest umieszczony na stronie** — czy przesuwa się razem z resztą treści, czy "unosi się" ponad nią, czy jest przyklejony do okna przeglądarki.

---

### Wartości `position` — ściągawka:

```css
/* DOMYŚLNE — element w normalnym przepływie strony */
position: static;       /* zachowanie domyślne — top/left/right/bottom nie działają */

/* WZGLĘDNE — element pozostaje w przepływie, ale można go przesunąć */
position: relative;     /* przesuwa się WZGLĘDEM swojego normalnego miejsca */
                        /* inne elementy nadal "widzą" go w oryginalnym miejscu */

/* BEZWZGLĘDNE — element wyciągany z przepływu */
position: absolute;     /* pozycja WZGLĘDEM pierwszego rodzica z position ≠ static */
                        /* jeśli brak takiego rodzica → względem <body> */
                        /* inne elementy go "nie widzą" — jak duch */

/* STAŁE — przyklejone do okna przeglądarki */
position: fixed;        /* zawsze widoczne w tym samym miejscu ekranu */
                        /* nie przesuwa się przy scrollowaniu */

/* PRZYKLEJONE — kombinacja relative i fixed */
position: sticky;       /* zachowuje się jak relative, DOPÓKI nie dotrze do krawędzi */
                        /* wtedy "przykleja się" jak fixed */
```

---

### Właściwości przesunięcia (działają gdy position ≠ static):

```css
top: 20px;      /* 20px od GÓRNEJ krawędzi rodzica (lub okna przy fixed) */
bottom: 20px;   /* 20px od DOLNEJ krawędzi */
left: 20px;     /* 20px od LEWEJ krawędzi */
right: 20px;    /* 20px od PRAWEJ krawędzi */

/* Możesz łączyć top + left, top + right, bottom + left itp. */
```

---

### z-index — kolejność nakładania elementów:

```css
z-index: 1;    /* wyższy = na wierzchu */
z-index: 10;   /* jeszcze wyżej */
z-index: -1;   /* pod normalnym przepływem */

/* z-index działa TYLKO na elementach z position ≠ static */
```

---

### Kluczowy wzorzec: rodzic relative + dziecko absolute

```css
/* RODZIC — tworzy "obszar" dla dziecka */
.rodzic {
    position: relative;  /* ← to sprawia że absolute dziecka liczy się od tego rodzica */
    width: 300px;
    height: 200px;
}

/* DZIECKO — pozycjonuje się wewnątrz rodzica */
.dziecko {
    position: absolute;
    bottom: 10px;   /* 10px od dołu RODZICA */
    right: 10px;    /* 10px od prawej RODZICA */
}
```

```
┌─────────────────────────────┐
│  RODZIC (position: relative)│
│                             │
│                             │
│                   ┌───────┐ │
│                   │DZIECKO│ │ ← bottom:10px, right:10px
│                   └───────┘ │
└─────────────────────────────┘
```

---

### Wizualna ściągawka — kiedy co używać:

```
CHCĘ...                                          UŻYJ...
─────────────────────────────────────────────────────────
Nieznacznie przesunąć element                 → relative
Nakleić badge/etykietę na karcie              → absolute (w rodzicu relative)
Zrobić stały pasek nawigacji                  → fixed
Zrobić nagłówek tabeli "przyklejony"          → sticky
Kontrolować kolejność nakładania              → z-index
```

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 — HTML5 i CSS Część 4 — Pozycjonowanie</title>
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
            background: linear-gradient(135deg, #0f9b8e 0%, #00d2ff 100%);
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
            background: #0f9b8e;
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
            border-left: 4px solid #0f9b8e;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #e0f7f4;
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
            border: 2px dashed #0f9b8e;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            min-height: 60px;
            overflow: hidden;
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
        <h1>🟢 Pozycjonowanie CSS</h1>
        <p>Część 4 — HTML5 i CSS | INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: RELATIVE I ABSOLUTE — PODSTAWY
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">position: relative — przesunięcie względne</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz trzy bloki w rzędzie. Dodaj do środkowego bloku <code>position: relative</code> oraz <code>top: -20px</code>. Obserwuj — środkowy blok przesunie się w górę, ale <strong>pozostałe bloki nie zmieniają swojego miejsca</strong>. Miejsce po bloku nadal "istnieje".</p>
            <div class="info-box">💡 position: relative przesuwa element WZGLĘDEM jego normalnego miejsca.<br>
            Pozostałe elementy zachowują się jakby blok był na swoim oryginalnym miejscu — "duch" przestrzeni pozostaje.</div>
            <div class="warning-box">⚠️ top/left/right/bottom działają TYLKO gdy position ≠ static.<br>
            Na elemencie z domyślnym position: static — te właściwości są ignorowane!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <style>
                    #ex1-kontener {
                        display: flex;
                        gap: 10px;
                        background-color: #e0f7f4;
                        padding: 30px 15px;
                        align-items: flex-start;
                    }

                    .ex1-blok {
                        width: 100px;
                        height: 80px;
                        background-color: #0f9b8e;
                        color: white;
                        text-align: center;
                        line-height: 80px;
                        font-weight: bold;
                        border-radius: 4px;
                    }

                    #ex1-srodkowy {
                        background-color: #00695c;
                        /* Dodaj: position: relative; top: -20px; */
                    }
                </style>

                <div id="ex1-kontener">
                    <div class="ex1-blok">Blok 1</div>
                    <div class="ex1-blok" id="ex1-srodkowy">Środek</div>
                    <div class="ex1-blok">Blok 3</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">position: absolute — pozycja bezwzględna względem body</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Dodaj do zielonego bloku <code>position: absolute</code>, <code>top: 10px</code> i <code>right: 10px</code>. Blok powinien "wyskoczyć" do prawego górnego rogu — uwaga, ponieważ żaden rodzic nie ma ustawionego <code>position: relative</code>, element liczy pozycję od <code>&lt;body&gt;</code>!</p>
            <div class="info-box">💡 position: absolute szuka PIERWSZEGO rodzica z position ≠ static.<br>
            Jeśli nie znajdzie — liczy od &lt;body&gt;. Dlatego tak ważne jest ustawianie position: relative na rodzicu!</div>
            <div class="warning-box">⚠️ Element z position: absolute "wyciągany" jest z przepływu — inne elementy go nie widzą i zajmą jego miejsce!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <style>
                    #ex2-obszar {
                        background-color: #e0f7f4;
                        padding: 15px;
                        height: 120px;
                        position: relative; /* ← specjalnie dodane, żeby absolute liczył od tego diva */
                    }

                    #ex2-blok-abs {
                        width: 100px;
                        height: 60px;
                        background-color: #0f9b8e;
                        color: white;
                        text-align: center;
                        line-height: 60px;
                        font-weight: bold;
                        border-radius: 4px;
                        /* Dodaj: position: absolute; top: 10px; right: 10px; */
                    }

                    #ex2-tekst {
                        color: #555;
                        line-height: 1.6;
                    }
                </style>

                <div id="ex2-obszar">
                    <div id="ex2-blok-abs">ABSOLUTE</div>
                    <p id="ex2-tekst">Ten tekst "nie widzi" elementu absolute — zajmuje jego miejsce.
                    Blok zielony unosi się NAD tym tekstem.</p>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">Kluczowy wzorzec: relative na rodzicu + absolute na dziecku</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> To najważniejszy wzorzec w pozycjonowaniu. Ustaw <code>position: relative</code> na <code>#ex3-karta</code> (rodzicu). Następnie ustaw <code>position: absolute</code>, <code>top: 10px</code> i <code>right: 10px</code> na <code>#ex3-badge</code>. Zielona odznaka powinna pojawić się w prawym górnym rogu karty — nie strony!</p>
            <div class="code-example">
                <h4>📄 Wzorzec:</h4>
                <pre>
#ex3-karta {
    position: relative; /* ← "kotwica" dla absolute dziecka */
}

#ex3-badge {
    position: absolute;
    top: 10px;
    right: 10px;
}</pre>
            </div>
            <div class="info-box">💡 Rodzic relative = "obszar zakotwiczenia" dla dzieci absolute.<br>
            Bez relative na rodzicu — dziecko absolute uciekłoby poza kartę!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <style>
                    #ex3-karta {
                        background-color: white;
                        border: 2px solid #80cbc4;
                        border-radius: 8px;
                        padding: 20px;
                        width: 280px;
                        /* Dodaj: position: relative; */
                    }

                    #ex3-karta h3 {
                        color: #00695c;
                        margin-bottom: 8px;
                    }

                    #ex3-karta p {
                        color: #555;
                        font-size: 0.9em;
                    }

                    #ex3-badge {
                        background-color: #0f9b8e;
                        color: white;
                        padding: 4px 10px;
                        border-radius: 12px;
                        font-size: 0.8em;
                        font-weight: bold;
                        /* Dodaj: position: absolute; top: 10px; right: 10px; */
                    }
                </style>

                <div id="ex3-karta">
                    <div id="ex3-badge">NOWOŚĆ</div>
                    <h3>Kurs HTML5 i CSS</h3>
                    <p>Naucz się budować nowoczesne strony internetowe od podstaw.</p>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">Wyśrodkowanie przez absolute — top + left + transform</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Użyj <code>position: absolute</code> żeby wyśrodkować element idealnie pośrodku kontenera — poziomo i pionowo. Technika: <code>top: 50%</code>, <code>left: 50%</code>, <code>transform: translate(-50%, -50%)</code>.</p>
            <div class="code-example">
                <h4>📄 Technika wyśrodkowania przez absolute:</h4>
                <pre>
#ex4-kontener {
    position: relative;  /* kotwica */
    height: 200px;
}

#ex4-srodek {
    position: absolute;
    top: 50%;             /* górna krawędź w połowie rodzica */
    left: 50%;            /* lewa krawędź w połowie rodzica */
    transform: translate(-50%, -50%); /* cofnij o połowę własnego rozmiaru */
}</pre>
            </div>
            <div class="info-box">💡 top: 50% + left: 50% ustawia LEWĄ GÓRNĄ krawędź elementu w środku.<br>
            transform: translate(-50%, -50%) przesuwa go o połowę własnej szerokości i wysokości w lewo i górę.<br>
            Efekt: idealny środek. To klasyczna technika sprzed Flexbox!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <style>
                    #ex4-kontener {
                        background-color: #e0f7f4;
                        height: 180px;
                        border: 2px dashed #80cbc4;
                        border-radius: 8px;
                        /* Dodaj: position: relative; */
                    }

                    #ex4-srodek {
                        background-color: #0f9b8e;
                        color: white;
                        padding: 12px 24px;
                        border-radius: 6px;
                        font-weight: bold;
                        font-size: 1.1em;
                        /* Dodaj: position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); */
                    }
                </style>

                <div id="ex4-kontener">
                    <div id="ex4-srodek">Idealny środek!</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: Z-INDEX I NAKŁADANIE
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">z-index — kolejność nakładania elementów</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz trzy nakładające się bloki. Domyślnie ten napisany ostatni w HTML jest na wierzchu. Zmień kolejność przez z-index: nadaj pierwszemu blokowi <code>z-index: 3</code>, drugiemu <code>z-index: 1</code>, trzeciemu <code>z-index: 2</code>. Pierwszy powinien znaleźć się na wierzchu.</p>
            <div class="info-box">💡 Wyższy z-index = element bliżej użytkownika (na wierzchu).<br>
            z-index działa TYLKO na elementach z position ≠ static.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <style>
                    #ex5-obszar {
                        position: relative;
                        height: 160px;
                    }

                    .ex5-blok {
                        position: absolute;
                        width: 120px;
                        height: 120px;
                        border-radius: 8px;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        font-weight: bold;
                        color: white;
                        font-size: 1.1em;
                    }

                    #ex5-b1 {
                        background-color: #0f9b8e;
                        top: 0; left: 0;
                        /* Dodaj: z-index: 3; */
                    }

                    #ex5-b2 {
                        background-color: #00695c;
                        top: 20px; left: 50px;
                        /* Dodaj: z-index: 1; */
                    }

                    #ex5-b3 {
                        background-color: #4db6ac;
                        top: 40px; left: 100px;
                        /* Dodaj: z-index: 2; */
                    }
                </style>

                <div id="ex5-obszar">
                    <div class="ex5-blok" id="ex5-b1">1 (z:3)</div>
                    <div class="ex5-blok" id="ex5-b2">2 (z:1)</div>
                    <div class="ex5-blok" id="ex5-b3">3 (z:2)</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">Badge na karcie produktu — praktyczne zastosowanie</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz kartę produktu z odznakę "PROMOCJA" w lewym górnym rogu. Karta ma <code>position: relative</code>, odznaka <code>position: absolute</code> z <code>top: 0</code> i <code>left: 0</code>. Zwróć uwagę na ujemne wartości — <code>top: -10px</code> wysuwa odznakę poza krawędź karty.</p>
            <div class="code-example">
                <h4>📄 Struktura karty z odznaką:</h4>
                <pre>
&lt;div class="karta-prod"&gt;
    &lt;div class="odznak"&gt;PROMOCJA&lt;/div&gt;
    &lt;h3&gt;Nazwa produktu&lt;/h3&gt;
    &lt;p&gt;Opis...&lt;/p&gt;
    &lt;p class="cena"&gt;199 zł&lt;/p&gt;
&lt;/div&gt;

.karta-prod { position: relative; }
.odznak     { position: absolute; top: -10px; left: -10px; }</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <style>
                    #ex6-obszar {
                        display: flex;
                        gap: 20px;
                        flex-wrap: wrap;
                        padding: 20px;
                    }

                    /* Dodaj style dla .karta-prod i .odznak */
                    .karta-prod {
                        width: 180px;
                        background-color: white;
                        border: 1px solid #80cbc4;
                        border-radius: 8px;
                        padding: 20px 15px 15px;
                        /* Dodaj: position: relative; */
                    }

                    .karta-prod h3 {
                        color: #00695c;
                        font-size: 1em;
                        margin-bottom: 6px;
                    }

                    .karta-prod .cena {
                        color: #0f9b8e;
                        font-weight: bold;
                        margin-top: 8px;
                    }

                    .odznak {
                        background-color: #e53935;
                        color: white;
                        font-size: 0.75em;
                        font-weight: bold;
                        padding: 3px 8px;
                        border-radius: 4px;
                        /* Dodaj: position: absolute; top: -10px; left: -10px; */
                    }
                </style>

                <div id="ex6-obszar">
                    <div class="karta-prod">
                        <div class="odznak">PROMOCJA</div>
                        <h3>Klawiatura mechaniczna</h3>
                        <p style="color:#777; font-size:0.85em;">Cherry MX Red, RGB</p>
                        <p class="cena">249 zł</p>
                    </div>
                    <div class="karta-prod">
                        <div class="odznak">NOWOŚĆ</div>
                        <h3>Mysz bezprzewodowa</h3>
                        <p style="color:#777; font-size:0.85em;">3000 DPI, 72h baterii</p>
                        <p class="cena">129 zł</p>
                    </div>
                    <div class="karta-prod">
                        <h3>Monitor 24"</h3>
                        <p style="color:#777; font-size:0.85em;">Full HD, 144Hz</p>
                        <p class="cena">899 zł</p>
                    </div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">Nakładka (overlay) na obrazku — absolute na całą kartę</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz efekt nakładki — tekst pojawia się na kolorowym tle zakrywającym cały blok. Nakładka ma <code>position: absolute</code> z <code>top: 0</code>, <code>left: 0</code>, <code>width: 100%</code>, <code>height: 100%</code>. Kolor tła nakładki z przezroczystością: <code>rgba(15, 155, 142, 0.85)</code>.</p>
            <div class="code-example">
                <h4>📄 Wzorzec nakładki:</h4>
                <pre>
.baner-wrapper {
    position: relative;      /* kotwica */
    width: 300px;
    height: 150px;
}

.nakladka {
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background-color: rgba(15, 155, 142, 0.85);
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <style>
                    .ex7-baner-wrapper {
                        width: 320px;
                        height: 150px;
                        background-color: #b2dfdb;
                        background-image: repeating-linear-gradient(
                            45deg,
                            #80cbc4 0px, #80cbc4 10px,
                            #b2dfdb 10px, #b2dfdb 20px
                        );
                        border-radius: 8px;
                        /* Dodaj: position: relative; */
                    }

                    .ex7-nakladka {
                        /* Dodaj: position: absolute; top: 0; left: 0; width: 100%; height: 100%; */
                        background-color: rgba(15, 155, 142, 0.85);
                        display: flex;
                        flex-direction: column;
                        justify-content: center;
                        align-items: center;
                        color: white;
                        border-radius: 8px;
                    }

                    .ex7-nakladka h3 {
                        font-size: 1.3em;
                        margin-bottom: 5px;
                    }

                    .ex7-nakladka p {
                        font-size: 0.9em;
                        opacity: 0.9;
                    }
                </style>

                <div class="ex7-baner-wrapper">
                    <div class="ex7-nakladka">
                        <h3>Technikum IT</h3>
                        <p>Rekrutacja 2025/2026</p>
                    </div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">Tooltip — dymek po najechaniu (hover + absolute)</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz dymek podpowiedzi który pojawia się po najechaniu na przycisk. Dymek ma <code>position: absolute</code>, domyślnie <code>display: none</code>, a po <code>:hover</code> na rodzicu — <code>display: block</code>. Użyj selektora potomka: <code>.tooltip-wrapper:hover .tooltip-tekst</code>.</p>
            <div class="code-example">
                <h4>📄 Wzorzec tooltip:</h4>
                <pre>
.tooltip-wrapper {
    position: relative;
    display: inline-block;
}

.tooltip-tekst {
    position: absolute;
    bottom: 110%;      /* nad przyciskiem */
    left: 50%;
    transform: translateX(-50%);
    display: none;     /* domyślnie ukryty */
    background-color: #333;
    color: white;
    padding: 6px 12px;
    border-radius: 4px;
    white-space: nowrap;
}

.tooltip-wrapper:hover .tooltip-tekst {
    display: block;    /* pojawia się po hover */
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <style>
                    /* Dodaj tu style dla .ex8-tooltip-wrapper, .ex8-tooltip i reguły hover */
                    .ex8-tooltip-wrapper {
                        display: inline-block;
                        margin: 30px;
                        /* Dodaj: position: relative; */
                    }

                    .ex8-btn {
                        background-color: #0f9b8e;
                        color: white;
                        padding: 10px 20px;
                        border: none;
                        border-radius: 6px;
                        cursor: pointer;
                        font-size: 1em;
                    }

                    .ex8-tooltip {
                        background-color: #004d40;
                        color: white;
                        padding: 6px 12px;
                        border-radius: 4px;
                        font-size: 0.85em;
                        white-space: nowrap;
                        display: none; /* domyślnie ukryty */
                        /* Dodaj: position: absolute; bottom: 110%; left: 50%; transform: translateX(-50%); */
                    }

                    /* Dodaj: .ex8-tooltip-wrapper:hover .ex8-tooltip { display: block; } */
                </style>

                <div class="ex8-tooltip-wrapper">
                    <button class="ex8-btn">Najedź na mnie!</button>
                    <div class="ex8-tooltip">To jest dymek podpowiedzi 💬</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: FIXED I STICKY
         Ćwiczenia 9–12
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">position: fixed — pasek nawigacji przyklejony do okna</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>fixed_nav.html</code> stwórz stronę z <strong>stałym paskiem nawigacji</strong> na górze okna. Pasek ma <code>position: fixed</code>, <code>top: 0</code>, <code>width: 100%</code>. Dodaj dużo treści (kilka paragrafów Lorem ipsum) żeby strona była przewijalna — pasek ma zostać na górze podczas scrollowania.</p>
            <div class="code-example">
                <h4>📄 Stały nagłówek:</h4>
                <pre>
#staly-header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    background-color: rgb(15, 155, 142);
    color: white;
    padding: 15px 30px;
    z-index: 100;  /* nad resztą treści */
}

/* WAŻNE: body musi mieć padding-top = wysokość headera! */
body {
    padding-top: 60px;
}</pre>
            </div>
            <div class="info-box">💡 position: fixed liczy pozycję od OKNA PRZEGLĄDARKI — nie od body.<br>
            Zawsze widoczny w tym samym miejscu, niezależnie od przewinięcia strony.<br>
            Zawsze dodaj z-index na fixed elementach — muszą być nad treścią!</div>
            <div class="warning-box">⚠️ Bez padding-top na body — treść schowa się pod stałym headerem!</div>
            <!-- ↓↓↓ ĆWICZENIE W OSOBNYM PLIKU ↓↓↓ -->
            <div class="ex-area" id="ex9-area">
                <p style="color:#888; font-style:italic; text-align:center; padding:10px;">
                    Ćwiczenie wykonaj w osobnym pliku: <strong>fixed_nav.html</strong>
                </p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">position: fixed — przycisk "wróć na górę"</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Do pliku <code>fixed_nav.html</code> z ćwiczenia 9 dodaj przycisk "↑ Góra" przyklejony do dolnego prawego rogu okna. Kliknięcie ma przenosić na górę strony (<code>href="#"</code>). Przycisk ma <code>position: fixed</code>, <code>bottom: 30px</code>, <code>right: 30px</code>.</p>
            <div class="code-example">
                <h4>📄 Przycisk "wróć na górę":</h4>
                <pre>
#btn-gora {
    position: fixed;
    bottom: 30px;
    right: 30px;
    background-color: rgb(15, 155, 142);
    color: white;
    padding: 12px 16px;
    border-radius: 50%;
    text-decoration: none;
    font-size: 1.2em;
    z-index: 100;
    border: none;
    cursor: pointer;
}</pre>
            </div>
            <div class="info-box">💡 Dwa elementy fixed na tej samej stronie — header na górze i przycisk na dole.<br>
            Oba potrzebują z-index żeby być nad treścią.</div>
            <!-- ↓↓↓ ĆWICZENIE W OSOBNYM PLIKU ↓↓↓ -->
            <div class="ex-area" id="ex10-area">
                <p style="color:#888; font-style:italic; text-align:center; padding:10px;">
                    Ćwiczenie wykonaj w pliku: <strong>fixed_nav.html</strong> (kontynuacja ćw. 9)
                </p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">position: sticky — przyklejony nagłówek sekcji</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>sticky.html</code> stwórz długą stronę z trzema sekcjami. Każda sekcja ma nagłówek <code>h2</code> z <code>position: sticky</code> i <code>top: 0</code>. Podczas przewijania nagłówek "przykleja się" do górnej krawędzi okna i pozostaje widoczny dopóki trwa sekcja.</p>
            <div class="code-example">
                <h4>📄 Sticky nagłówek sekcji:</h4>
                <pre>
.sekcja-h2 {
    position: sticky;
    top: 0;               /* przykleja się gdy dotrze do top: 0 */
    background-color: rgb(15, 155, 142);
    color: white;
    padding: 10px 20px;
    z-index: 10;
}

.sekcja {
    min-height: 400px;    /* sekcja musi być długa żeby efekt był widoczny */
    padding: 20px;
}</pre>
            </div>
            <div class="info-box">💡 sticky = relative + fixed w jednym:<br>
            • Zachowuje się jak relative gdy jest widoczny w oknie<br>
            • "Przykleja się" jak fixed gdy dotrze do podanej granicy (top: 0)<br>
            • "Odklejasz się" gdy kolejna sekcja wychodzi poza widok</div>
            <!-- ↓↓↓ ĆWICZENIE W OSOBNYM PLIKU ↓↓↓ -->
            <div class="ex-area" id="ex11-area">
                <p style="color:#888; font-style:italic; text-align:center; padding:10px;">
                    Ćwiczenie wykonaj w osobnym pliku: <strong>sticky.html</strong>
                </p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Porównanie: static, relative, absolute, fixed, sticky</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Uzupełnij tabelę porównawczą wartości position wpisując odpowiednie komentarze do kodu CSS poniżej. Następnie stwórz demonstrację — 5 bloków, każdy z inną wartością position, różnymi kolorami i etykietami pokazującymi nazwę wartości.</p>
            <div class="code-example">
                <h4>📋 Uzupełnij tabelę (powtórzenie materiału):</h4>
                <pre>
position: static   → ??? (domyślne, top/left nie działają)
position: relative → ??? (przesuwa się, ale miejsce zostaje)
position: absolute → ??? (wyciągany z przepływu, liczy od rodzica)
position: fixed    → ??? (liczy od okna, zostaje przy scrollu)
position: sticky   → ??? (relative + fixed, przykleja się)</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 12 ↓↓↓ -->
            <div class="ex-area" id="ex12-area">

                <style>
                    #ex12-demo {
                        position: relative;
                        height: 200px;
                        background-color: #e0f7f4;
                        border: 1px dashed #80cbc4;
                        border-radius: 6px;
                        padding: 10px;
                    }

                    .ex12-blok {
                        display: inline-block;
                        padding: 8px 14px;
                        color: white;
                        font-weight: bold;
                        font-size: 0.85em;
                        border-radius: 4px;
                        margin: 4px;
                    }

                    /* Stwórz 5 bloków z różnymi wartościami position i kolorami */
                    /* Każdy z etykietą np. "static", "relative top:-10px", "absolute" */
                </style>

                <div id="ex12-demo">
                    <!-- Stwórz 5 divów .ex12-blok z różnymi wartościami position -->
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 12 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK D: PRAKTYCZNE UKŁADY + PROJEKT
         Ćwiczenia 13–16
         ========================================== -->

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Karta z absolute — licznik lub ikona w rogu</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz trzy karty informacyjne. Każda karta ma w prawym górnym rogu okrągłą ikonę z cyfrą (jak powiadomienie na telefonie). Ikona jest pozycjonowana przez absolute w rogu karty.</p>
            <div class="code-example">
                <h4>📄 Karta z licznikiem:</h4>
                <pre>
&lt;div class="info-kafel"&gt;
    &lt;span class="licznik"&gt;3&lt;/span&gt;
    &lt;h3&gt;Wiadomości&lt;/h3&gt;
    &lt;p&gt;Masz 3 nowe wiadomości&lt;/p&gt;
&lt;/div&gt;

.info-kafel {
    position: relative;
    padding: 20px;
    border: 1px solid #80cbc4;
    border-radius: 8px;
    width: 180px;
}

.licznik {
    position: absolute;
    top: -10px;
    right: -10px;
    width: 28px; height: 28px;
    background-color: #e53935;
    color: white;
    border-radius: 50%;
    text-align: center;
    line-height: 28px;
    font-size: 0.85em;
    font-weight: bold;
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 13 ↓↓↓ -->
            <div class="ex-area" id="ex13-area">
                <style>
                    #ex13-karty {
                        display: flex;
                        gap: 30px;
                        padding: 20px;
                        flex-wrap: wrap;
                    }
                    /* Dodaj style dla .info-kafel i .licznik */
                </style>
                <div id="ex13-karty">
                    <!-- Stwórz 3 karty .info-kafel z .licznik w rogu -->
                    <!-- Np. Wiadomości (3), Zadania (7), Powiadomienia (1) -->
                </div>
            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 13 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Pasek boczny (sidebar) z fixed — stały panel</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>sidebar_fixed.html</code> stwórz stronę ze stałym bocznym panelem po lewej stronie. Panel ma <code>position: fixed</code>, <code>top: 0</code>, <code>left: 0</code>, stałą szerokość <code>220px</code> i <code>height: 100%</code>. Główna treść strony ma <code>margin-left: 220px</code> żeby nie chować się pod panelem.</p>
            <div class="code-example">
                <h4>📄 Układ z fixed sidebar:</h4>
                <pre>
#panel-boczny {
    position: fixed;
    top: 0; left: 0;
    width: 220px;
    height: 100%;
    background-color: rgb(0, 77, 64);
    padding: 20px;
    overflow-y: auto;   /* scroll jeśli menu długie */
    z-index: 50;
}

#tresc-glowna {
    margin-left: 220px; /* = szerokość panelu */
    padding: 30px;
}</pre>
            </div>
            <!-- ↓↓↓ ĆWICZENIE W OSOBNYM PLIKU ↓↓↓ -->
            <div class="ex-area" id="ex14-area">
                <p style="color:#888; font-style:italic; text-align:center; padding:10px;">
                    Ćwiczenie wykonaj w osobnym pliku: <strong>sidebar_fixed.html</strong>
                </p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Złożenie — relative + absolute + z-index razem</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz sekcję "hero" strony — duży baner z nałożonym tekstem i przyciskiem. Baner (tło) to div z kolorem. Na nim: nakładka z przyciemnioną warstwą (absolute, rgba), a na niej treść tekstowa (też absolute, z wyższym z-index).</p>
            <div class="code-example">
                <h4>📄 Struktura hero z warstwami:</h4>
                <pre>
&lt;div id="hero-baner"&gt;            &lt;!-- relative --&gt;
    &lt;div class="przyciemnienie"&gt;&lt;/div&gt;  &lt;!-- absolute, z-index:1 --&gt;
    &lt;div class="hero-tresc"&gt;             &lt;!-- absolute, z-index:2 --&gt;
        &lt;h1&gt;Tytuł&lt;/h1&gt;
        &lt;a href="#"&gt;Czytaj więcej&lt;/a&gt;
    &lt;/div&gt;
&lt;/div&gt;</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 15 ↓↓↓ -->
            <div class="ex-area" id="ex15-area">
                <style>
                    #ex15-hero {
                        width: 100%;
                        height: 220px;
                        background: linear-gradient(135deg, #004d40, #00acc1);
                        /* Dodaj: position: relative; */
                        border-radius: 8px;
                        overflow: hidden;
                    }
                    /* Dodaj style dla .ex15-przyciemnienie i .ex15-tresc */
                </style>
                <div id="ex15-hero">
                    <!-- Stwórz: div.ex15-przyciemnienie (z-index:1) i div.ex15-tresc (z-index:2) -->
                    <!-- W treści: h2 + paragraf + link/przycisk -->
                </div>
            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 15 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 16 — PROJEKT KOŃCOWY -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">16</div>
            <div class="task-title">🏆 PROJEKT KOŃCOWY — Zadanie w stylu egzaminu INF.03</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>pozycjonowanie_projekt.html</code> z osobnym <code>styl.css</code> wykonaj stronę według poniższej specyfikacji.</p>

            <div class="code-example">
                <h4>📐 Diagram układu:</h4>
                <pre>
┌─────────────────────────────────────────────────────┐
│  STAŁY HEADER (position: fixed, top: 0, z-index:100)│
│  logo po lewej       |  nawigacja po prawej          │
└─────────────────────────────────────────────────────┘
                                          ↕ scroll
┌─────────────────────────────────────────────────────┐
│  SEKCJA HERO (position: relative, height: 300px)    │
│  ┌────────────────────────────────────────────────┐ │
│  │ NAKŁADKA (absolute, rgba tło, z-index: 1)      │ │
│  └────────────────────────────────────────────────┘ │
│  ┌────────────────────────────────────────────────┐ │
│  │ TREŚĆ HERO (absolute, środek, z-index: 2)      │ │
│  │ h1 + paragraf + przycisk                       │ │
│  └────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────┤
│  SEKCJA KART (3 karty obok siebie — Flexbox)        │
│  Każda karta ma BADGE (absolute) w rogu             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐          │
│  │[BADGE]   │  │[BADGE]   │  │          │          │
│  │  Karta 1 │  │  Karta 2 │  │  Karta 3 │          │
│  └──────────┘  └──────────┘  └──────────┘          │
├─────────────────────────────────────────────────────┤
│  FOOTER                                             │
└─────────────────────────────────────────────────────┘
         ↗ PRZYCISK "↑" (fixed, bottom:30px, right:30px)
</pre>
            </div>

            <div style="background: #e0f7f4; border: 2px solid #80cbc4; border-radius: 8px; padding: 20px; margin: 10px 0;">
                <h3 style="color: #00695c; margin-bottom: 14px;">📋 Specyfikacja (jak na egzaminie INF.03):</h3>

                <p style="color:#00695c; font-weight:bold; margin-bottom:8px;">Stały header (position: fixed):</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li><code>position: fixed</code>, <code>top: 0</code>, <code>left: 0</code>, <code>width: 100%</code>, <code>z-index: 100</code></li>
                    <li>Kolor tła: <code>rgb(0, 77, 64)</code>, kolor tekstu: biały, padding: 0 30px, wysokość: 60px</li>
                    <li>Układ przez Flexbox: <code>justify-content: space-between</code>, <code>align-items: center</code></li>
                    <li>Body: <code>padding-top: 60px</code> (żeby treść nie chowała się pod headerem)</li>
                </ul>

                <p style="color:#00695c; font-weight:bold; margin-bottom:8px;">Sekcja hero (position: relative):</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li><code>position: relative</code>, <code>height: 300px</code>, kolor tła: <code>rgb(15, 155, 142)</code></li>
                    <li>Nakładka: <code>position: absolute</code>, top/left: 0, width/height: 100%, <code>background-color: rgba(0, 0, 0, 0.45)</code>, <code>z-index: 1</code></li>
                    <li>Treść hero: <code>position: absolute</code>, top: 50%, left: 50%, <code>transform: translate(-50%, -50%)</code>, <code>z-index: 2</code>, kolor tekstu: biały, text-align: center</li>
                    <li>W treści hero: <code>&lt;h1&gt;</code> z nazwą szkoły + <code>&lt;p&gt;</code> z hasłem</li>
                </ul>

                <p style="color:#00695c; font-weight:bold; margin-bottom:8px;">Sekcja kart:</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li>Kontener kart: Flexbox, <code>gap: 20px</code>, <code>padding: 40px 30px</code>, kolor tła: <code>rgb(232, 245, 243)</code></li>
                    <li>3 karty: <code>flex: 1</code>, <code>position: relative</code>, kolor tła: biały, <code>border: 1px solid rgb(128, 203, 196)</code>, border-radius: 8px, padding: 25px 20px 20px</li>
                    <li>Badge na pierwszych dwóch kartach: <code>position: absolute</code>, <code>top: -12px</code>, <code>right: -12px</code>, kolor tła: <code>rgb(229, 57, 53)</code>, kolor tekstu: biały, border-radius: 50%, width/height: 32px, line-height: 32px, text-align: center, font-weight: bold</li>
                </ul>

                <p style="color:#00695c; font-weight:bold; margin-bottom:8px;">Przycisk "wróć na górę" i footer:</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0;">
                    <li>Przycisk: <code>position: fixed</code>, <code>bottom: 30px</code>, <code>right: 30px</code>, <code>z-index: 100</code>, kolor tła: <code>rgb(0, 77, 64)</code>, kolor tekstu: biały, border-radius: 50%, width/height: 48px, text-align: center, line-height: 48px, text-decoration: none, font-size: 1.3em</li>
                    <li>Footer: kolor tła <code>rgb(0, 77, 64)</code>, kolor tekstu: biały, padding: 20px, text-align: center, tekst stopki: "© 2025 Technikum Informatyczne" + Twój PESEL pogrubionym</li>
                </ul>
            </div>

            <div class="warning-box">⚠️ CSS piszesz w OSOBNYM pliku <code>styl.css</code> dołączonym przez <code>&lt;link&gt;</code>!<br>
            Pamiętaj o <code>padding-top: 60px</code> na body — bez tego treść schowa się pod stałym headerem.</div>
            <div class="info-box">💡 Sprawdź projekt przez przewinięcie strony — header i przycisk "↑" muszą być stale widoczne.<br>
            Nad kartami: czy badge wystaje poza krawędź karty? (top: -12px, right: -12px)</div>
        </div>
    </div>

    <footer class="page-footer">
        <p>HTML5 i CSS — Część 4 | Pozycjonowanie CSS | INF.03</p>
        <p style="margin-top: 10px; font-size: 0.9em;">
            📌 relative | 🎯 absolute | 📌 fixed | 🔗 sticky | 🗂 z-index
        </p>
    </footer>

</div>
</body>
</html>
```

---

## 📋 LISTA ĆWICZEŃ

### Blok A — Relative i Absolute: podstawy (ćwiczenia 1–4)
| Nr | Temat | Właściwości |
|----|-------|-------------|
| 1 | position: relative — przesunięcie bez zmiany przepływu | position: relative, top |
| 2 | position: absolute — pozycja od rodzica | position: absolute, top, right |
| 3 | Kluczowy wzorzec: relative rodzic + absolute dziecko | badge na karcie |
| 4 | Wyśrodkowanie przez absolute | top: 50%, left: 50%, transform |

### Blok B — Z-index i nakładanie (ćwiczenia 5–8)
| Nr | Temat | Właściwości |
|----|-------|-------------|
| 5 | z-index — kolejność elementów | z-index: 1/2/3 |
| 6 | Badge "PROMOCJA" na karcie produktu | absolute w rogu karty |
| 7 | Nakładka (overlay) na banerze | absolute + rgba |
| 8 | Tooltip po najechaniu (hover + absolute) | :hover, display: none/block |

### Blok C — Fixed i Sticky (ćwiczenia 9–12)
| Nr | Temat | Plik |
|----|-------|------|
| 9 | Stały pasek nawigacji | fixed_nav.html |
| 10 | Przycisk "wróć na górę" | fixed_nav.html (cd.) |
| 11 | Przyklejony nagłówek sekcji | sticky.html |
| 12 | Porównanie wszystkich wartości position | w szablonie |

### Blok D — Praktyczne układy + Projekt (ćwiczenia 13–16)
| Nr | Temat | Zakres |
|----|-------|--------|
| 13 | Karta z licznikiem w rogu (badge) | absolute w rogu |
| 14 | Stały panel boczny | sidebar_fixed.html |
| 15 | Sekcja hero — warstwy: nakładka + treść | relative + 2× absolute + z-index |
| 16 | 🏆 Projekt egzaminacyjny | pozycjonowanie_projekt.html + styl.css |

Miejsce na wysłania pracy:

kl3 TIe Jastrzębie https://www.dropbox.com/request/yvi40xoNLJ0Q1kf1NtNV
