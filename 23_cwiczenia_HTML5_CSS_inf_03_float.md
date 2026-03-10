# 📝 SZABLON HTML — CZĘŚĆ 2b — CSS FLOAT

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT — ŚCIĄGAWKA PRZED ĆWICZENIAMI

### Co to jest float?

**Float** to właściwość CSS która "wyciąga" element z normalnego przepływu strony i przesuwa go do lewej lub prawej krawędzi swojego kontenera. Inne elementy "opływają" go z pozostałych stron.

```
BEZ FLOAT:            Z float: left:
┌──────────┐          ┌─────┐
│  Blok A  │          │  A  │ Tekst tekst tekst
└──────────┘          │float│ tekst tekst tekst
┌──────────┐          └─────┘ tekst tekst tekst
│  Blok B  │
└──────────┘
```

Float był przez lata głównym sposobem na **układanie kolumn** na stronie.

---

### Właściwości float — ściągawka:

```css
/* Główna właściwość */
float: left;    /* element przesuwa się do LEWEJ */
float: right;   /* element przesuwa się do PRAWEJ */
float: none;    /* wyłącza float (domyślny) */

/* Czyszczenie floatów */
clear: left;    /* element NIE opływa elementów z float: left */
clear: right;   /* element NIE opływa elementów z float: right */
clear: both;    /* element NIE opływa żadnych floatów — NAJCZĘSTSZY! */

/* Technika clearfix — zapobiega "zawaleniu" kontenera */
.kontener::after {
    content: "";
    display: table;
    clear: both;
}
```

---

### Klasyczny układ dwukolumnowy z float:

```css
/* Lewa kolumna */
.sidebar {
    float: left;
    width: 25%;
}

/* Prawa kolumna */
.tresc {
    float: left;
    width: 75%;
}

/* Stopka — musi "wyczyścić" float, żeby była pod kolumnami */
footer {
    clear: both;
}
```

---

### Wizualna ściągawka — jak działa clear: both:

```
BEZ clear: both:           Z clear: both:

[sidebar][tresc  ]         [sidebar][tresc  ]
[stopka znajduje           [                ]
się tutaj → obok!]         [stopka pod spodem]
```

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 — HTML5 i CSS Część 2b — Float</title>
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
            background: linear-gradient(135deg, #f7971e 0%, #ffd200 100%);
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
            background: #ffd200;
            color: #7a5700;
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
            border-left: 4px solid #ffd200;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #fff9e6;
            border: 1px solid #ffd200;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #7a5700;
            font-size: 0.95em;
            line-height: 1.5;
        }

        .warning-box {
            background: #fff0e0;
            border: 1px solid #ff9800;
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
            border: 2px dashed #ffd200;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            min-height: 60px;
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
        <h1>🟡 CSS Float</h1>
        <p>Część 2b — HTML5 i CSS | INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: PODSTAWY FLOAT
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">float: left — element przesuwa się do lewej</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz pomarańczowy blok i tekst pod spodem. Dodaj do bloku <code>float: left</code> — i obserwuj jak tekst "opływa" blok z prawej strony. Bez float blok zajmuje całą linię i tekst jest pod nim.</p>
            <div class="info-box">💡 float: left przesuwa element do LEWEJ krawędzi kontenera.<br>
            Elementy które są po nim w HTML opływają go z prawej strony.</div>
            <div class="warning-box">⚠️ Float "wyciąga" element z normalnego przepływu strony.<br>
            Inne blokowe elementy zachowują się jakby go nie było!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <style>
                    #ex1-blok {
                        width: 120px;
                        height: 80px;
                        background-color: #f7971e;
                        color: white;
                        font-weight: bold;
                        text-align: center;
                        line-height: 80px;
                        margin-right: 15px;
                        /* Dodaj tu: float: left; */
                    }

                    #ex1-area p.ex1-tekst {
                        color: #555;
                        line-height: 1.7;
                    }
                </style>

                <div id="ex1-blok">float: left</div>
                <p class="ex1-tekst">Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor.</p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">float: right — element przesuwa się do prawej</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Tym razem użyj <code>float: right</code> na żółtym bloku. Tekst powinien opływać go z lewej strony. Porównaj efekt z poprzednim ćwiczeniem.</p>
            <div class="info-box">💡 float: right przesuwa element do PRAWEJ krawędzi.<br>
            Tekst opływa go z lewej — jak "wywołana" ramka w gazecie lub podpis do zdjęcia.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <style>
                    #ex2-blok {
                        width: 140px;
                        height: 90px;
                        background-color: #ffd200;
                        color: #7a5700;
                        font-weight: bold;
                        text-align: center;
                        line-height: 90px;
                        margin-left: 15px;
                        /* Dodaj tu: float: right; */
                    }

                    #ex2-area p.ex2-tekst {
                        color: #555;
                        line-height: 1.7;
                    }
                </style>

                <div id="ex2-blok">float: right</div>
                <p class="ex2-tekst">Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor.</p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">clear: both — zatrzymanie opływania</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz floatujący blok i dwa paragrafy tekstu. Dodaj <code>clear: both</code> do <strong>drugiego</strong> paragrafu — powinien on przestać opływać blok i znaleźć się pod nim. Pierwszy paragraf nadal opływa.</p>
            <div class="code-example">
                <h4>📄 Do dodania:</h4>
                <pre>
#ex3-drugi {
    clear: both;
}</pre>
            </div>
            <div class="info-box">💡 clear: both mówi elementowi: "idź POD wszystkie floaty, nie opływaj ich".<br>
            To podstawowy sposób na "wyjście" z obszaru opływania.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <style>
                    #ex3-box {
                        float: left;
                        width: 100px;
                        height: 100px;
                        background-color: #f7971e;
                        margin-right: 15px;
                        color: white;
                        text-align: center;
                        line-height: 100px;
                        font-weight: bold;
                    }

                    #ex3-area p {
                        color: #555;
                        line-height: 1.6;
                        margin-bottom: 8px;
                    }

                    /* Dodaj tu regułę dla #ex3-drugi */
                </style>

                <div id="ex3-box">FLOAT</div>
                <p id="ex3-pierwszy">Pierwszy paragraf opływa blok po prawej stronie.
                Ten tekst jest blisko floatu.</p>
                <p id="ex3-drugi">Drugi paragraf — po dodaniu clear: both powinien
                znaleźć się POD floatem, nie obok niego.</p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">Problem zawalającego się kontenera</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Kontener z żółtą ramką powinien otaczać oba floatujące bloki. Ale "zawala się" — jego wysokość wynosi 0! Napraw to dodając do kontenera <code>overflow: hidden</code>. Ramka powinna pojawić się wokół obu bloków.</p>
            <div class="info-box">💡 To klasyczna pułapka float: rodzic "nie widzi" dzieci z float i kurczy się do 0px.<br>
            <strong>Rozwiązanie:</strong> <code>overflow: hidden</code> na kontenerze — zmusza go do "zauważenia" floatów.<br>
            Alternatywa: pseudo-element ::after z clear: both (clearfix).</div>
            <div class="warning-box">⚠️ To jeden z najczęstszych błędów przy float! Zapamiętaj overflow: hidden jako fix.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <style>
                    #ex4-kontener {
                        border: 3px solid #f7971e;
                        padding: 10px;
                        /* Dodaj tu: overflow: hidden; */
                    }

                    .ex4-blok {
                        float: left;
                        width: 120px;
                        height: 80px;
                        background-color: #ffd200;
                        margin-right: 10px;
                        text-align: center;
                        line-height: 80px;
                        font-weight: bold;
                        color: #7a5700;
                    }
                </style>

                <div id="ex4-kontener">
                    <div class="ex4-blok">Blok A</div>
                    <div class="ex4-blok">Blok B</div>
                </div>
                <p style="color:#999; font-size:0.9em; margin-top:5px;">
                    Tekst pod kontenerem (bez fix: pojawi się wewnątrz ramki zamiast pod nią)
                </p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: KOLUMNY Z FLOAT
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">Dwie kolumny równej szerokości</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz dwie kolumny obok siebie — każda szerokości 50%. Obu kolumnom dodaj <code>float: left</code> i <code>width: 50%</code>. Pod kolumnami dodaj element z <code>clear: both</code> żeby treść po nich była pod spodem.</p>
            <div class="code-example">
                <h4>📄 Wzorzec:</h4>
                <pre>
.kolumna-pol {
    float: left;
    width: 50%;
    padding: 15px;
}

.clearfix {
    clear: both;
}</pre>
            </div>
            <div class="info-box">💡 Suma szerokości kolumn MUSI wynosić dokładnie 100% (lub mniej).<br>
            Jeśli przekroczy 100% — druga kolumna "spadnie" pod pierwszą!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <style>
                    /* Dodaj tu style dla .ex5-kolumna i .ex5-clear */

                    .ex5-kolumna {
                        /* float: left; width: 50%; padding: 15px; */
                        background-color: #fff9e6;
                        border: 1px solid #ffd200;
                        box-sizing: border-box;
                    }

                    .ex5-clear {
                        /* clear: both; */
                    }
                </style>

                <div class="ex5-kolumna">
                    <h4 style="color:#7a5700;">Kolumna lewa</h4>
                    <p style="color:#555;">Treść lewej kolumny. Lorem ipsum dolor sit amet
                    consectetur adipiscing elit sed do eiusmod.</p>
                </div>

                <div class="ex5-kolumna">
                    <h4 style="color:#7a5700;">Kolumna prawa</h4>
                    <p style="color:#555;">Treść prawej kolumny. Ut labore et dolore magna
                    aliqua ut enim ad minim veniam.</p>
                </div>

                <div class="ex5-clear"></div>

                <p style="color:#999; font-size:0.9em; margin-top:5px;">
                    Ten tekst powinien być POD obiema kolumnami.
                </p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">Sidebar + treść główna (25% + 75%)</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Klasyczny układ strony: wąski sidebar po lewej (25%) i szeroka treść główna po prawej (75%). Obu elementom nadaj <code>float: left</code> z odpowiednimi szerokościami. Pamiętaj o <code>clear: both</code> po kolumnach!</p>
            <div class="info-box">💡 25% + 75% = 100% — suma musi się zgadzać.<br>
            To najczęstszy układ na egzaminie INF.03: "lewy blok 25%, prawy 75%".</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <style>
                    #ex6-sidebar {
                        /* float: left; width: 25%; */
                        background-color: #fff9e6;
                        border: 1px solid #ffd200;
                        padding: 12px;
                        box-sizing: border-box;
                        min-height: 120px;
                    }

                    #ex6-tresc {
                        /* float: left; width: 75%; */
                        background-color: #f9f9f9;
                        border: 1px solid #ddd;
                        padding: 12px;
                        box-sizing: border-box;
                        min-height: 120px;
                    }

                    #ex6-clear {
                        /* clear: both; */
                    }
                </style>

                <div id="ex6-sidebar">
                    <h4 style="color:#7a5700;">Menu</h4>
                    <p style="color:#555; font-size:0.9em;">Aktualności</p>
                    <p style="color:#555; font-size:0.9em;">O nas</p>
                    <p style="color:#555; font-size:0.9em;">Kontakt</p>
                </div>

                <div id="ex6-tresc">
                    <h4 style="color:#333;">Treść główna</h4>
                    <p style="color:#555;">Lorem ipsum dolor sit amet consectetur adipiscing elit.
                    Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                </div>

                <div id="ex6-clear"></div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">Trzy kolumny równej szerokości</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Rozszerz wzorzec z ćwiczenia 5 na trzy kolumny. Każda ma mieć szerokość ~33% (użyj dokładnie <code>33.33%</code>). Wszystkie trzy mają <code>float: left</code>. Dodaj <code>clear: both</code> po trzeciej kolumnie.</p>
            <div class="warning-box">⚠️ Uwaga na padding i border! Jeśli dodasz padding do kolumny o width: 33.33%,
            suma może przekroczyć 100% i kolumna "spadnie". Używaj <code>box-sizing: border-box</code>!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <style>
                    .ex7-kolumna {
                        /* float: left; width: 33.33%; */
                        background-color: #fff9e6;
                        border: 1px solid #ffd200;
                        padding: 15px;
                        box-sizing: border-box;
                        text-align: center;
                    }

                    #ex7-clear {
                        /* clear: both; */
                    }
                </style>

                <div class="ex7-kolumna">
                    <h4 style="color:#7a5700;">Kolumna 1</h4>
                    <p style="color:#555; font-size:0.9em;">Treść pierwszej kolumny</p>
                </div>

                <div class="ex7-kolumna">
                    <h4 style="color:#7a5700;">Kolumna 2</h4>
                    <p style="color:#555; font-size:0.9em;">Treść drugiej kolumny</p>
                </div>

                <div class="ex7-kolumna">
                    <h4 style="color:#7a5700;">Kolumna 3</h4>
                    <p style="color:#555; font-size:0.9em;">Treść trzeciej kolumny</p>
                </div>

                <div id="ex7-clear"></div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">Kolumny z konkretnym kolorem RGB — styl egzaminacyjny</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Na egzaminie INF.03 podają konkretne wartości kolorów i rozmiarów. Ćwicz to teraz. Ustaw dwa bloki według specyfikacji:</p>
            <div class="code-example">
                <h4>📋 Specyfikacja (jak na egzaminie):</h4>
                <pre>
Blok LOGO:
  float: left
  width: 30%
  height: 80px
  background-color: RGB(247, 151, 30)
  text-align: center

Blok MENU:
  float: left (lub right)
  width: 70%
  height: 80px
  background-color: RGB(255, 210, 0)
  text-align: right</pre>
            </div>
            <div class="info-box">💡 Na egzaminie kolory są zawsze podane jako RGB — musisz je poprawnie przepisać.<br>
            <code>background-color: rgb(247, 151, 30);</code> — małe litery, wartości przez przecinki.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <style>
                    /* Uzupełnij wszystkie właściwości dla obu bloków */
                    #ex8-logo {
                        /* float, width, height, background-color (RGB), text-align, line-height */
                        color: white;
                        font-weight: bold;
                        font-size: 1.2em;
                        padding: 0 15px;
                        box-sizing: border-box;
                    }

                    #ex8-menu {
                        /* float, width, height, background-color (RGB), text-align, line-height */
                        color: #7a5700;
                        font-weight: bold;
                        padding: 0 15px;
                        box-sizing: border-box;
                    }

                    #ex8-clear { clear: both; }
                </style>

                <div id="ex8-logo">🏫 Technikum</div>
                <div id="ex8-menu">Strona główna | O nas | Kontakt</div>
                <div id="ex8-clear"></div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: UKŁAD STRONY
         Ćwiczenia 9–12
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">Header na pełną szerokość</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz nagłówek strony na pełną szerokość. Header z float <strong>nie używa</strong> float (jest elementem blokowym zajmującym całą linię). Nadaj mu kolor tła, wysokość i wyrównanie tekstu.</p>
            <div class="code-example">
                <h4>📄 Wzorzec nagłówka:</h4>
                <pre>
#ex9-header {
    background-color: rgb(247, 151, 30);
    color: white;
    padding: 15px 20px;
    text-align: center;
    /* header jest BLOCK — nie potrzebuje float */
}</pre>
            </div>
            <div class="info-box">💡 Header i footer są elementami blokowymi — zajmują całą linię bez float.<br>
            Float stosujemy tylko na elementach WEWNĄTRZ — kolumnach w środkowej sekcji.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 9 ↓↓↓ -->
            <div class="ex-area" id="ex9-area">

                <style>
                    /* Dodaj style dla #ex9-header */
                    #ex9-header {
                        color: white;
                        padding: 15px 20px;
                        /* Dodaj: background-color, text-align */
                    }
                </style>

                <header id="ex9-header">
                    <h2>🏫 Technikum Informatyczne — Nagłówek strony</h2>
                </header>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 9 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">Baner pod nagłówkiem (pełna szerokość)</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Na egzaminie INF.03 często pojawia się baner — kolorowy pas na pełną szerokość z wyśrodkowanym tekstem pod nagłówkiem. Stwórz element <code>&lt;div id="ex10-baner"&gt;</code> z konkretną wysokością, kolorem tła i wyśrodkowanym tekstem. Baner też jest BLOCK — bez float.</p>
            <div class="code-example">
                <h4>📋 Specyfikacja:</h4>
                <pre>
#ex10-baner:
  background-color: rgb(255, 210, 0)
  height: 100px
  text-align: center
  line-height: 100px  ← pionowe wyśrodkowanie tekstu
  font-size: 1.5em
  color: #7a5700</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 10 ↓↓↓ -->
            <div class="ex-area" id="ex10-area">

                <style>
                    /* Uzupełnij style dla #ex10-baner */
                    #ex10-baner {
                        font-weight: bold;
                    }
                </style>

                <div id="ex10-baner">Baner strony — hasło reklamowe</div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 10 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">Dwie kolumny środkowej sekcji</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz środkową sekcję strony z dwoma kolumnami. Lewy blok (sidebar/menu): 30% szerokości. Prawy blok (treść): 70%. Oba z <code>float: left</code>, różne kolory tła, <code>min-height: 200px</code>. Po nich <code>clear: both</code>.</p>
            <div class="code-example">
                <h4>📋 Specyfikacja (styl egzaminacyjny):</h4>
                <pre>
#ex11-lewy:
  float: left
  width: 30%
  min-height: 200px
  background-color: rgb(255, 235, 180)
  padding: 15px
  box-sizing: border-box

#ex11-prawy:
  float: left
  width: 70%
  min-height: 200px
  background-color: rgb(249, 249, 249)
  padding: 15px
  box-sizing: border-box</pre>
            </div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 11 ↓↓↓ -->
            <div class="ex-area" id="ex11-area">

                <style>
                    /* Dodaj tu style dla #ex11-lewy, #ex11-prawy, #ex11-clear */
                </style>

                <div id="ex11-lewy">
                    <h4 style="color:#7a5700; margin-bottom:10px;">Menu boczne</h4>
                    <p style="color:#555; font-size:0.9em;">Aktualności</p>
                    <p style="color:#555; font-size:0.9em;">O szkole</p>
                    <p style="color:#555; font-size:0.9em;">Rekrutacja</p>
                    <p style="color:#555; font-size:0.9em;">Kontakt</p>
                </div>

                <div id="ex11-prawy">
                    <h4 style="color:#333; margin-bottom:10px;">Treść strony</h4>
                    <p style="color:#555;">Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                    Ut enim ad minim veniam, quis nostrud exercitation.</p>
                </div>

                <div id="ex11-clear"></div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 11 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Stopka na pełną szerokość</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Dodaj stopkę pod kolumnami. Ważne: stopka MUSI mieć <code>clear: both</code> albo być po divie z clear: both — inaczej wyświetli się obok kolumn, nie pod nimi. Stwórz footer z kolorem tła, padding, tekstem wyśrodkowanym.</p>
            <div class="info-box">💡 Na egzaminie INF.03 stopka musi być POD kolumnami.<br>
            Jeśli brakuje clear: both — stopka "ucieka" obok floatów. To klasyczny błąd egzaminacyjny!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 12 ↓↓↓ -->
            <div class="ex-area" id="ex12-area">

                <style>
                    /* Bloki z poprzednich ćwiczeń (już z float: left) */
                    .ex12-lewy {
                        float: left;
                        width: 30%;
                        background-color: #fff9e6;
                        padding: 12px;
                        box-sizing: border-box;
                        min-height: 80px;
                    }

                    .ex12-prawy {
                        float: left;
                        width: 70%;
                        background-color: #f9f9f9;
                        padding: 12px;
                        box-sizing: border-box;
                        min-height: 80px;
                    }

                    #ex12-footer {
                        /* Dodaj: clear: both, background-color, padding, text-align */
                        color: white;
                        font-size: 0.9em;
                    }
                </style>

                <div class="ex12-lewy">
                    <strong style="color:#7a5700;">Sidebar</strong>
                </div>
                <div class="ex12-prawy">
                    <strong style="color:#555;">Treść główna</strong>
                </div>

                <footer id="ex12-footer">
                    © 2025 Technikum Informatyczne
                </footer>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 12 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK D: KOMPLETNY UKŁAD + PROJEKT
         Ćwiczenia 13–16
         ========================================== -->

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Nawigacja pozioma z float</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz poziome menu nawigacyjne używając float. Elementy <code>&lt;li&gt;</code> mają <code>float: left</code> — ustawiają się w rzędzie. Dodaj <code>list-style: none</code> żeby usunąć punktory i ostyluj linki.</p>
            <div class="code-example">
                <h4>📄 Wzorzec:</h4>
                <pre>
#ex13-nav ul {
    list-style: none;
    overflow: hidden; /* clearfix dla listy */
    background-color: rgb(247, 151, 30);
    padding: 0;
    margin: 0;
}

#ex13-nav li {
    float: left;
}

#ex13-nav a {
    display: block;
    padding: 12px 18px;
    color: white;
    text-decoration: none;
}

#ex13-nav a:hover {
    background-color: rgb(200, 120, 10);
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 13 ↓↓↓ -->
            <div class="ex-area" id="ex13-area">

                <style>
                    /* Dodaj tu style dla nawigacji */
                </style>

                <nav id="ex13-nav">
                    <ul>
                        <li><a href="#">Strona główna</a></li>
                        <li><a href="#">O szkole</a></li>
                        <li><a href="#">Oferta</a></li>
                        <li><a href="#">Rekrutacja</a></li>
                        <li><a href="#">Kontakt</a></li>
                    </ul>
                </nav>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 13 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Logo po lewej, menu po prawej</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz pasek nagłówka: logo z <code>float: left</code>, blok nawigacji z <code>float: right</code>. Kontener nagłówka musi mieć <code>overflow: hidden</code> żeby się nie zawalił. Nadaj im kolory i wysokości.</p>
            <div class="code-example">
                <h4>📄 Wzorzec:</h4>
                <pre>
#ex14-header {
    background-color: rgb(247, 151, 30);
    overflow: hidden; /* clearfix */
    padding: 0 20px;
}

#ex14-logo {
    float: left;
    line-height: 60px;
    color: white;
    font-size: 1.3em;
    font-weight: bold;
}

#ex14-nav {
    float: right;
    line-height: 60px;
}

#ex14-nav a {
    color: white;
    text-decoration: none;
    margin-left: 20px;
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 14 ↓↓↓ -->
            <div class="ex-area" id="ex14-area">

                <style>
                    /* Dodaj style dla #ex14-header, #ex14-logo, #ex14-nav */
                </style>

                <header id="ex14-header">
                    <div id="ex14-logo">🏫 Technikum IT</div>
                    <nav id="ex14-nav">
                        <a href="#">Strona główna</a>
                        <a href="#">O nas</a>
                        <a href="#">Kontakt</a>
                    </nav>
                </header>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 14 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Kompletny układ strony — złożenie wszystkiego</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Złóż kompletny układ strony w jednym ćwiczeniu. Użyj poniższej struktury i dodaj CSS według specyfikacji.</p>
            <div class="code-example">
                <h4>📋 Pełna specyfikacja layoutu:</h4>
                <pre>
Struktura HTML:
  header → baner → (lewy + prawy) → footer

#ex15-header:  pełna szerokość, bg rgb(247,151,30), h: 60px, tekst biały, wyśrodkowany
#ex15-baner:   pełna szerokość, bg rgb(255,210,0), h: 80px, tekst #7a5700, wyśrodkowany
#ex15-lewy:    float: left, width: 25%, bg rgb(255,235,180), min-height: 150px, padding: 10px
#ex15-prawy:   float: left, width: 75%, bg rgb(249,249,249), min-height: 150px, padding: 10px
#ex15-footer:  clear: both, bg rgb(100,80,0), tekst biały, padding: 10px, wyśrodkowany</pre>
            </div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 15 ↓↓↓ -->
            <div class="ex-area" id="ex15-area">

                <style>
                    /* Uzupełnij wszystkie style */
                    #ex15-header { box-sizing: border-box; }
                    #ex15-baner  { box-sizing: border-box; }
                    #ex15-lewy   { box-sizing: border-box; }
                    #ex15-prawy  { box-sizing: border-box; }
                    #ex15-footer { }
                </style>

                <div id="ex15-header">Nagłówek strony</div>
                <div id="ex15-baner">Baner — hasło szkoły</div>

                <div id="ex15-lewy">
                    <strong>Menu</strong><br>
                    <small>Aktualności</small><br>
                    <small>O szkole</small>
                </div>
                <div id="ex15-prawy">
                    <strong>Witamy na stronie szkoły!</strong>
                    <p style="font-size:0.9em; margin-top:8px; color:#555;">
                    Lorem ipsum dolor sit amet consectetur adipiscing elit.</p>
                </div>

                <footer id="ex15-footer">© 2025 Technikum Informatyczne</footer>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 15 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 16 — PROJEKT EGZAMINACYJNY -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">16</div>
            <div class="task-title">🏆 PROJEKT — Zadanie w stylu egzaminu INF.03</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W nowym pliku <code>zadanie_float.html</code> wykonaj stronę internetową według poniższej specyfikacji. To zadanie jest wzorowane na rzeczywistych arkuszach egzaminacyjnych INF.03.</p>

            <div style="background: #fff9e6; border: 2px solid #ffd200; border-radius: 8px; padding: 20px; margin: 10px 0;">
                <h3 style="color: #7a5700; margin-bottom: 12px;">📋 Specyfikacja zadania:</h3>

                <p style="color:#555; margin-bottom: 12px;">Wykonaj stronę internetową dla Technikum Informatycznego. Strona powinna zawierać:</p>

                <ul style="margin-left: 20px; color: #555; line-height: 2.1;">
                    <li>✅ Poprawny szkielet HTML5 z <code>lang="pl"</code> i kodowaniem UTF-8</li>
                    <li>✅ Arkusz CSS w osobnym pliku <code>styl.css</code> dołączony przez <code>&lt;link&gt;</code></li>
                    <li>✅ Blok <strong>logo</strong>: float: left, szerokość 40%, wysokość 80px, kolor tła <code>rgb(247, 151, 30)</code>, tekst wyrównany do lewej, padding 20px</li>
                    <li>✅ Blok <strong>menu nagłówkowe</strong>: float: left, szerokość 60%, wysokość 80px, kolor tła <code>rgb(255, 210, 0)</code>, tekst wyrównany do prawej, padding 20px</li>
                    <li>✅ Blok <strong>baner</strong> po logo i menu: pełna szerokość, wysokość 100px, kolor tła <code>rgb(200, 150, 0)</code>, tekst biały, wyśrodkowany, font-size: 1.5em</li>
                    <li>✅ Blok <strong>lewy</strong> (sidebar): float: left, szerokość 25%, min-height: 300px, kolor tła <code>rgb(255, 235, 180)</code>, padding 15px</li>
                    <li>✅ Blok <strong>prawy</strong> (treść): float: left, szerokość 75%, min-height: 300px, kolor tła <code>rgb(249, 249, 249)</code>, padding 15px</li>
                    <li>✅ Blok <strong>stopka</strong>: clear: both, kolor tła <code>rgb(100, 80, 0)</code>, kolor tekstu biały, padding 15px, tekst wyśrodkowany</li>
                    <li>✅ W boku lewym: lista nieuporządkowana z 4 elementami (linki nawigacyjne)</li>
                    <li>✅ W boku prawym: nagłówek h2 i co najmniej 2 paragrafy tekstu</li>
                </ul>
            </div>

            <div class="warning-box">⚠️ W tym zadaniu CSS piszesz w OSOBNYM pliku <code>styl.css</code>!<br>
            W bloku HTML: <code>&lt;link rel="stylesheet" href="styl.css"&gt;</code> w sekcji head.</div>
            <div class="info-box">💡 To wzorzec który pojawia się na egzaminie INF.03 od lat.<br>
            Zapamiętaj strukturę: logo+menu → baner → lewy+prawy → stopka.<br>
            Na egzaminie dostaniesz obrazek — musisz odwzorować layout i kolory.</div>
        </div>
    </div>

    <footer class="page-footer">
        <p>HTML5 i CSS — Część 2b | Float | INF.03</p>
        <p style="margin-top: 10px; font-size: 0.9em;">
            float: left/right | clear: both | overflow: hidden | width: %
        </p>
    </footer>

</div>
</body>
</html>
```

---

## 📋 LISTA ĆWICZEŃ

### Blok A — Podstawy float (ćwiczenia 1–4)
| Nr | Temat | Właściwości |
|----|-------|-------------|
| 1 | float: left — element z opływającym tekstem | float: left |
| 2 | float: right | float: right |
| 3 | clear: both — zatrzymanie opływania | clear: both |
| 4 | Problem zawalającego się kontenera | overflow: hidden |

### Blok B — Kolumny (ćwiczenia 5–8)
| Nr | Temat | Właściwości |
|----|-------|-------------|
| 5 | Dwie kolumny po 50% | float: left + width: 50% |
| 6 | Sidebar 25% + treść 75% | float: left + różne width |
| 7 | Trzy kolumny po 33.33% | float + box-sizing |
| 8 | Kolumny z kolorami RGB — styl egzaminacyjny | background-color: rgb() |

### Blok C — Układ strony (ćwiczenia 9–12)
| Nr | Temat | Zakres |
|----|-------|--------|
| 9 | Header na pełną szerokość | block element, bez float |
| 10 | Baner pod nagłówkiem | height, line-height, text-align |
| 11 | Dwie kolumny środkowej sekcji | specyfikacja egzaminacyjna |
| 12 | Stopka z clear: both | clear: both na footer |

### Blok D — Kompletny layout + Projekt (ćwiczenia 13–16)
| Nr | Temat | Zakres |
|----|-------|--------|
| 13 | Nawigacja pozioma (float na li) | float: left na li |
| 14 | Logo po lewej, menu po prawej | float: left + float: right |
| 15 | Kompletny układ strony | wszystkie elementy razem |
| 16 | 🏆 Projekt egzaminacyjny | osobny plik + styl.css |

Miejsce na wysłania prac:

kl 3 TIe Jastrzębie: https://www.dropbox.com/request/avgeCQiIQZ27ldNyysh9

UWAGA Brak wysłania efektów pracy w terminie wyznaczonym przez nauczyciela to ocena ndst!
