# 📝 SZABLON HTML — CZĘŚĆ 3 — FLEXBOX

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT — ŚCIĄGAWKA PRZED ĆWICZENIAMI

### Co to jest Flexbox?

**Flexbox** to sposób na ustawianie elementów HTML **obok siebie** (lub pod sobą) i kontrolowanie ich rozmieszczenia. Bez floatów, bez tricków — po prostu kilka właściwości CSS.

Flexbox działa na zasadzie **rodzic → dzieci**:
- Właściwości piszemy na **rodzicu** (kontenerze)
- Działają automatycznie na wszystkich **dzieciach** (elementach wewnątrz)

```
┌──────────────────────────────────────────────┐
│   KONTENER (display: flex)                   │
│  ┌────────┐  ┌────────┐  ┌────────┐          │
│  │ ITEM 1 │  │ ITEM 2 │  │ ITEM 3 │          │
│  └────────┘  └────────┘  └────────┘          │
└──────────────────────────────────────────────┘
```

---

### Właściwości Flexbox — ściągawka:

#### Na KONTENERZE (rodzicu):

```css
/* 1. Włączenie Flexbox */
display: flex;

/* 2. Kierunek ułożenia elementów */
flex-direction: row;          /* poziomo → (domyślny) */
flex-direction: column;       /* pionowo ↓ */

/* 3. Rozkład w poziomie (oś główna) */
justify-content: flex-start;  /* do lewej (domyślny) */
justify-content: flex-end;    /* do prawej */
justify-content: center;      /* wyśrodkuj */
justify-content: space-between; /* odstępy MIĘDZY elementami */
justify-content: space-around;  /* odstępy WOKÓŁ elementów */

/* 4. Wyrównanie w pionie (oś poprzeczna) */
align-items: stretch;         /* rozciągnij do wysokości kontenera (domyślny) */
align-items: flex-start;      /* do góry */
align-items: flex-end;        /* do dołu */
align-items: center;          /* wyśrodkuj pionowo */

/* 5. Zawijanie — co gdy brakuje miejsca? */
flex-wrap: nowrap;            /* nie zawija (domyślny) */
flex-wrap: wrap;              /* zawija do nowego wiersza */

/* 6. Odstępy między elementami */
gap: 20px;                    /* odstęp między wszystkimi elementami */
gap: 10px 20px;               /* odstęp góra/dół | lewo/prawo */
```

#### Na DZIECIACH (itemach) — opcjonalne:

```css
/* Jak dany element ma rosnąć relative do reszty */
flex: 1;       /* rośnie i zajmuje równą część dostępnego miejsca */
flex: 2;       /* rośnie 2x szybciej niż flex: 1 */
flex: none;    /* nie rośnie — zostaje przy swoim rozmiarze */
```

---

### Wizualna ściągawka justify-content:

```
flex-start:      [A][B][C]               (do lewej)
flex-end:                  [A][B][C]     (do prawej)
center:              [A][B][C]           (środek)
space-between:   [A]      [B]      [C]  (odstępy między)
space-around:      [A]    [B]    [C]    (odstępy wokół)
```

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 — HTML5 i CSS Część 3 — Flexbox</title>
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
            background: linear-gradient(135deg, #d7aefb 0%, #b9d7fb 100%);
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
            background: #d7aefb;
            color: #4a148c;
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
            border-left: 4px solid #d7aefb;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #f3e5f5;
            border: 1px solid #ce93d8;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #6a1b9a;
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
            border: 2px dashed #d7aefb;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            min-height: 60px;
        }

        .ex-area-label {
            font-size: 0.8em;
            color: #d7aefb;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 8px;
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
        <h1>🟣 Flexbox</h1>
        <p>Część 3 — HTML5 i CSS | INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: PIERWSZE KROKI Z FLEXBOX
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">Włączenie Flexbox — display: flex</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej masz kontener z trzema blokami. Bez CSS bloki ustawione są <em>jeden pod drugim</em>. Dodaj do kontenera <code>display: flex</code> — i obserwuj jak bloki układają się automatycznie <em>obok siebie</em>!</p>
            <div class="info-box">💡 Jedna właściwość na rodzicu — i już działa!<br>
            Flexbox zmienia domyślne zachowanie: elementy blokowe (div) normalnie zajmują całą linię. Po <code>display: flex</code> ustawiają się w rząd.</div>
            <div class="warning-box">⚠️ <code>display: flex</code> piszemy na RODZICU (kontenerze), nie na dzieciach!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <style>
                    #ex1-kontener {
                        /* Dodaj tu: display: flex; */
                        background-color: #f3e5f5;
                        padding: 10px;
                    }

                    #ex1-kontener div {
                        background-color: #d7aefb;
                        padding: 20px;
                        margin: 5px;
                        font-weight: bold;
                        color: #4a148c;
                    }
                </style>

                <div id="ex1-kontener">
                    <div>Blok 1</div>
                    <div>Blok 2</div>
                    <div>Blok 3</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">flex-direction — kierunek ułożenia</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz dwa identyczne kontenery z czterema blokami. Ustaw na pierwszym <code>flex-direction: row</code>, a na drugim <code>flex-direction: column</code>. Obserwuj różnicę — elementy w rzędzie vs. w kolumnie.</p>
            <div class="code-example">
                <h4>📄 Kod do uzupełnienia:</h4>
                <pre>
#ex2-rzad   { display: flex; flex-direction: ???; }
#ex2-kolumna { display: flex; flex-direction: ???; }</pre>
            </div>
            <div class="info-box">💡 <code>row</code> = elementy obok siebie → (domyślny!)<br>
            <code>column</code> = elementy pod sobą ↓<br>
            <code>row-reverse</code> i <code>column-reverse</code> = te same, ale w odwrotnej kolejności</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <style>
                    #ex2-rzad, #ex2-kolumna {
                        background-color: #f3e5f5;
                        padding: 10px;
                        margin-bottom: 15px;
                        /* Dodaj display: flex i odpowiedni flex-direction */
                    }

                    #ex2-rzad div, #ex2-kolumna div {
                        background-color: #ce93d8;
                        padding: 15px;
                        margin: 4px;
                        text-align: center;
                        color: white;
                        font-weight: bold;
                    }
                </style>

                <p style="margin-bottom:5px; color:#555;"><strong>Rząd (row):</strong></p>
                <div id="ex2-rzad">
                    <div>A</div>
                    <div>B</div>
                    <div>C</div>
                    <div>D</div>
                </div>

                <p style="margin-bottom:5px; color:#555;"><strong>Kolumna (column):</strong></p>
                <div id="ex2-kolumna">
                    <div>A</div>
                    <div>B</div>
                    <div>C</div>
                    <div>D</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">justify-content — rozkład poziomy</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz pięć kontenerów flex. Nadaj każdemu inną wartość <code>justify-content</code> — po jednej na kontener. Obserwuj jak zmieniają się odstępy i pozycja elementów.</p>
            <div class="code-example">
                <h4>📄 Pięć wartości do przypisania:</h4>
                <pre>
#jc-start   { justify-content: flex-start;    }
#jc-end     { justify-content: flex-end;      }
#jc-center  { justify-content: center;        }
#jc-between { justify-content: space-between; }
#jc-around  { justify-content: space-around;  }</pre>
            </div>
            <div class="info-box">💡 justify-content działa na OŚ GŁÓWNĄ — poziomo gdy flex-direction: row<br>
            To najczęściej używana właściwość Flexbox — np. wyśrodkowanie menu!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <style>
                    .jc-kontener {
                        display: flex;
                        background-color: #f3e5f5;
                        padding: 8px;
                        margin-bottom: 8px;
                        /* Każdy kontener dostanie osobne justify-content poniżej */
                    }

                    .jc-kontener div {
                        background-color: #ab47bc;
                        color: white;
                        padding: 10px 20px;
                        font-weight: bold;
                        border-radius: 4px;
                    }

                    /* Dodaj poniżej po jednej regule dla każdego kontenera: */

                </style>

                <p style="color:#555; margin-bottom:4px;"><small>flex-start:</small></p>
                <div class="jc-kontener" id="jc-start">
                    <div>A</div><div>B</div><div>C</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>flex-end:</small></p>
                <div class="jc-kontener" id="jc-end">
                    <div>A</div><div>B</div><div>C</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>center:</small></p>
                <div class="jc-kontener" id="jc-center">
                    <div>A</div><div>B</div><div>C</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>space-between:</small></p>
                <div class="jc-kontener" id="jc-between">
                    <div>A</div><div>B</div><div>C</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>space-around:</small></p>
                <div class="jc-kontener" id="jc-around">
                    <div>A</div><div>B</div><div>C</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">align-items — wyrównanie pionowe</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Kontener ma ustawioną wysokość <code>100px</code>. Bloki mają różne wysokości. Wypróbuj trzy wartości <code>align-items</code> na trzech kontenerach — <code>flex-start</code>, <code>center</code>, <code>flex-end</code> — i obserwuj gdzie trafiają elementy pionowo.</p>
            <div class="info-box">💡 align-items działa na OŚ POPRZECZNĄ — pionowo gdy flex-direction: row<br>
            Domyślna wartość to <code>stretch</code> — elementy rozciągają się do pełnej wysokości kontenera.<br>
            <code>center</code> = pionowe wyśrodkowanie — bardzo przydatne!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <style>
                    .ai-kontener {
                        display: flex;
                        height: 100px;
                        background-color: #f3e5f5;
                        padding: 5px;
                        margin-bottom: 10px;
                        gap: 8px;
                        /* Dodaj align-items z różnymi wartościami poniżej */
                    }

                    .ai-kontener div {
                        background-color: #ba68c8;
                        color: white;
                        padding: 8px 16px;
                        font-weight: bold;
                        border-radius: 4px;
                    }

                    .ai-kontener div:nth-child(2) { font-size: 0.8em; }
                    .ai-kontener div:nth-child(3) { font-size: 1.3em; }

                    /* Uzupełnij: */
                    #ai-start  { /* align-items: flex-start; */ }
                    #ai-center { /* align-items: center;     */ }
                    #ai-end    { /* align-items: flex-end;   */ }
                </style>

                <p style="color:#555; margin-bottom:4px;"><small>align-items: flex-start (do góry):</small></p>
                <div class="ai-kontener" id="ai-start">
                    <div>Duży</div><div>Mały</div><div>Jeszcze większy</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>align-items: center (środek):</small></p>
                <div class="ai-kontener" id="ai-center">
                    <div>Duży</div><div>Mały</div><div>Jeszcze większy</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>align-items: flex-end (do dołu):</small></p>
                <div class="ai-kontener" id="ai-end">
                    <div>Duży</div><div>Mały</div><div>Jeszcze większy</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: GAP I FLEX-WRAP
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">gap — odstępy między elementami</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Porównaj dwa kontenery — jeden bez <code>gap</code>, drugi z <code>gap: 20px</code>. Następnie zmień wartość na <code>gap: 10px 40px</code> (różny odstęp pionowy i poziomy) i obserwuj efekt.</p>
            <div class="info-box">💡 <code>gap: 20px</code> — odstęp 20px między każdą parą sąsiednich elementów<br>
            <code>gap: 10px 40px</code> — 10px między wierszami, 40px między kolumnami<br>
            gap zastępuje stare margin na dzieciach — znacznie wygodniejsze!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <style>
                    .gap-kontener {
                        display: flex;
                        background-color: #f3e5f5;
                        padding: 10px;
                        margin-bottom: 10px;
                    }

                    .gap-kontener div {
                        background-color: #9c27b0;
                        color: white;
                        padding: 15px 25px;
                        border-radius: 4px;
                        font-weight: bold;
                    }

                    /* Dodaj gap na drugim kontenerze: */
                    #gap-bez  { /* brak gap */ }
                    #gap-z    { gap: 20px; }
                </style>

                <p style="color:#555; margin-bottom:4px;"><small>Bez gap:</small></p>
                <div class="gap-kontener" id="gap-bez">
                    <div>1</div><div>2</div><div>3</div><div>4</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>Z gap: 20px:</small></p>
                <div class="gap-kontener" id="gap-z">
                    <div>1</div><div>2</div><div>3</div><div>4</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">flex-wrap — zawijanie elementów</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Kontener ma wiele elementów z ustawioną szerokością. Bez <code>flex-wrap</code> wszystkie zmieszczą się w jednej linii (mogą wychodzić poza ekran). Dodaj <code>flex-wrap: wrap</code> na pierwszym kontenerze — elementy zawiną się do nowych linii gdy braknie miejsca.</p>
            <div class="code-example">
                <h4>📄 Do dodania:</h4>
                <pre>
#wrap-nie { flex-wrap: nowrap; }  /* domyślne — nie zawija */
#wrap-tak { flex-wrap: wrap;    } /* zawija do nowego wiersza */</pre>
            </div>
            <div class="info-box">💡 flex-wrap: wrap to podstawa siatek kart (np. sklepy, galerie zdjęć).<br>
            Bez flex-wrap elementy kurczą się lub wylewają poza kontener gdy brakuje miejsca.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <style>
                    .wrap-kontener {
                        display: flex;
                        background-color: #f3e5f5;
                        padding: 8px;
                        margin-bottom: 12px;
                        gap: 8px;
                    }

                    .wrap-kontener div {
                        background-color: #7b1fa2;
                        color: white;
                        padding: 12px;
                        width: 120px;
                        text-align: center;
                        border-radius: 4px;
                        flex-shrink: 0; /* nie kurczy się */
                    }

                    #wrap-nie { flex-wrap: nowrap; overflow: hidden; }
                    #wrap-tak { /* dodaj flex-wrap: wrap */ }
                </style>

                <p style="color:#555; margin-bottom:4px;"><small>flex-wrap: nowrap — nie zawija (elementy mogą się ucinać):</small></p>
                <div class="wrap-kontener" id="wrap-nie">
                    <div>Karta 1</div><div>Karta 2</div><div>Karta 3</div>
                    <div>Karta 4</div><div>Karta 5</div><div>Karta 6</div>
                    <div>Karta 7</div>
                </div>

                <p style="color:#555; margin-bottom:4px;"><small>flex-wrap: wrap — zawija do nowej linii:</small></p>
                <div class="wrap-kontener" id="wrap-tak">
                    <div>Karta 1</div><div>Karta 2</div><div>Karta 3</div>
                    <div>Karta 4</div><div>Karta 5</div><div>Karta 6</div>
                    <div>Karta 7</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">flex: 1 — równy podział miejsca</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Masz trzy kolumny w kontenerze flex. Dodaj <code>flex: 1</code> do wszystkich kolumn — powinny automatycznie podzielić dostępne miejsce równo między siebie. Następnie zmień środkową kolumnę na <code>flex: 2</code> — powinna być dwa razy szersza od pozostałych.</p>
            <div class="code-example">
                <h4>📄 Wzorzec — układ 2 kolumn sidebar + treść:</h4>
                <pre>
#lewa  { flex: 1; }   /* 1 część */
#srodek { flex: 2; }  /* 2 części — dwukrotnie szerszy */
#prawa { flex: 1; }   /* 1 część */
/* Razem: 4 części. Lewa i prawa po 25%, środek 50% */</pre>
            </div>
            <div class="info-box">💡 <code>flex: 1</code> mówi elementowi: "weź jedną równą część dostępnego miejsca"<br>
            To znacznie wygodniejsze niż ręczne liczenie procentów!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <style>
                    #ex7-kontener {
                        display: flex;
                        gap: 10px;
                        background-color: #f3e5f5;
                        padding: 10px;
                    }

                    #ex7-lewa, #ex7-srodek, #ex7-prawa {
                        padding: 20px;
                        text-align: center;
                        border-radius: 6px;
                        font-weight: bold;
                        color: white;
                        /* Dodaj tu flex: 1 na wszystkich,
                           potem zmień #ex7-srodek na flex: 2 */
                    }

                    #ex7-lewa  { background-color: #ab47bc; }
                    #ex7-srodek { background-color: #7b1fa2; }
                    #ex7-prawa { background-color: #ab47bc; }
                </style>

                <div id="ex7-kontener">
                    <div id="ex7-lewa">Lewa (flex: 1)</div>
                    <div id="ex7-srodek">Środek (flex: 2)</div>
                    <div id="ex7-prawa">Prawa (flex: 1)</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">Wyśrodkowanie elementu — justify-content + align-items</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Użyj Flexboxa do idealnego wyśrodkowania pudełka — zarówno poziomo jak i pionowo — wewnątrz kontenera. Kontener ma ustawioną wysokość 200px. Dodaj trzy właściwości do <code>#ex8-kontener</code>: <code>display: flex</code>, <code>justify-content: center</code>, <code>align-items: center</code>.</p>
            <div class="info-box">💡 To najsłynniejszy trick Flexboxa — pionowe wyśrodkowanie elementu!<br>
            Przed Flexboxem był to jeden z najtrudniejszych problemów CSS.<br>
            Teraz: 3 właściwości i gotowe.</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <style>
                    #ex8-kontener {
                        height: 200px;
                        background-color: #f3e5f5;
                        border: 2px dashed #ce93d8;
                        /* Dodaj: display: flex, justify-content: center, align-items: center */
                    }

                    #ex8-pudelko {
                        background-color: #9c27b0;
                        color: white;
                        padding: 20px 40px;
                        border-radius: 8px;
                        font-weight: bold;
                        font-size: 1.1em;
                    }
                </style>

                <div id="ex8-kontener">
                    <div id="ex8-pudelko">Wyśrodkowane!</div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: PRAKTYCZNE UKŁADY
         Ćwiczenia 9–12
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">Nawigacja pozioma — menu w rzędzie</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej jest lista nawigacyjna. Domyślnie elementy <code>&lt;li&gt;</code> są pionowe. Użyj Flexbox na tagu <code>&lt;ul&gt;</code> żeby linki ułożyły się poziomo. Usuń też domyślne punktory listy (<code>list-style: none</code>).</p>
            <div class="code-example">
                <h4>📄 Style do dodania:</h4>
                <pre>
#ex9-nav ul {
    display: flex;
    list-style: none;
    gap: 5px;
    background-color: #7b1fa2;
    padding: 10px;
}

#ex9-nav a {
    display: block;
    padding: 8px 16px;
    color: white;
    text-decoration: none;
    border-radius: 4px;
}

#ex9-nav a:hover {
    background-color: #4a148c;
}</pre>
            </div>
            <div class="info-box">💡 To klasyczny wzorzec menu strony — pozioma nawigacja z Flexbox.<br>
            Pamiętaj: flex dajemy na ul (rodzica listingów li), nie na li!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS — Ćwiczenie 9 ↓↓↓ -->
            <div class="ex-area" id="ex9-area">

                <style>
                    /* Dodaj tu style dla nawigacji */
                </style>

                <nav id="ex9-nav">
                    <ul>
                        <li><a href="#">Strona główna</a></li>
                        <li><a href="#">O nas</a></li>
                        <li><a href="#">Oferta</a></li>
                        <li><a href="#">Kontakt</a></li>
                    </ul>
                </nav>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 9 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">Karty obok siebie — siatka produktów</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz siatkę kart produktów. Użyj <code>display: flex</code>, <code>flex-wrap: wrap</code> i <code>gap</code> na kontenerze. Każda karta powinna mieć stałą szerokość (~200px) i równą wysokość dzięki Flexbox.</p>
            <div class="code-example">
                <h4>📄 Style kontenera i karty:</h4>
                <pre>
#ex10-siatka {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.karta-produktu {
    width: 200px;
    background-color: white;
    border: 1px solid #d7aefb;
    border-radius: 8px;
    padding: 15px;
    text-align: center;
}</pre>
            </div>
            <div class="info-box">💡 display: flex + flex-wrap: wrap + stała szerokość kart = responsywna siatka.<br>
            Karty same "wiedzą" kiedy zawinąć do nowej linii!</div>
            <!-- ↓↓↓ TUTAJ DODAJESZ CSS I KARTY — Ćwiczenie 10 ↓↓↓ -->
            <div class="ex-area" id="ex10-area">

                <style>
                    /* Dodaj style dla #ex10-siatka i .karta-produktu */
                </style>

                <div id="ex10-siatka">
                    <!-- Stwórz 5–6 kart z klasą .karta-produktu -->
                    <!-- Każda karta: nagłówek h3 z nazwą produktu + paragraf z ceną -->
                    <!-- Przykład jednej karty:
                    <div class="karta-produktu">
                        <h3>Laptop Gaming</h3>
                        <p>4 999 zł</p>
                    </div>
                    -->
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 10 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">Układ strony — header, main, footer</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz klasyczny układ strony z nagłówkiem, treścią główną i stopką. Sekcja <code>&lt;main&gt;</code> powinna zawierać dwie kolumny — sidebar i artykuł — ułożone za pomocą Flexbox.</p>
            <div class="code-example">
                <h4>📄 Struktura HTML i potrzebne style:</h4>
                <pre>
&lt;div id="ex11-strona"&gt;
    &lt;header&gt;Nagłówek&lt;/header&gt;
    &lt;main&gt;
        &lt;aside&gt;Sidebar&lt;/aside&gt;
        &lt;article&gt;Główna treść&lt;/article&gt;
    &lt;/main&gt;
    &lt;footer&gt;Stopka&lt;/footer&gt;
&lt;/div&gt;

/* main jako kontener flex: */
#ex11-strona main {
    display: flex;
    gap: 15px;
}
#ex11-strona aside   { flex: 1; }   /* 1/4 szerokości */
#ex11-strona article { flex: 3; }   /* 3/4 szerokości */</pre>
            </div>
            <div class="info-box">💡 To standardowy układ egzaminacyjny INF.03!<br>
            aside (sidebar) + article (treść) w rzędzie wewnątrz main — to podstawa layoutu stron.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ HTML I CSS — Ćwiczenie 11 ↓↓↓ -->
            <div class="ex-area" id="ex11-area">

                <style>
                    #ex11-strona header,
                    #ex11-strona footer {
                        background-color: #7b1fa2;
                        color: white;
                        padding: 15px;
                        text-align: center;
                        border-radius: 6px;
                        margin-bottom: 10px;
                    }

                    #ex11-strona footer {
                        margin-bottom: 0;
                        margin-top: 10px;
                    }

                    #ex11-strona aside {
                        background-color: #e1bee7;
                        padding: 15px;
                        border-radius: 6px;
                    }

                    #ex11-strona article {
                        background-color: #f3e5f5;
                        padding: 15px;
                        border-radius: 6px;
                    }

                    /* Dodaj: main jako display: flex, gap, oraz flex na aside i article */

                </style>

                <!-- Wpisz tu strukturę HTML z header, main (aside + article), footer -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 11 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Pasek nagłówka — logo po lewej, menu po prawej</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz pasek nagłówka strony z logo po lewej i linkami nawigacyjnymi po prawej. Użyj <code>justify-content: space-between</code> na headerze i <code>align-items: center</code> żeby logo i menu były wyrównane pionowo.</p>
            <div class="code-example">
                <h4>📄 Struktura i klucz CSS:</h4>
                <pre>
&lt;header id="ex12-header"&gt;
    &lt;div class="logo"&gt;🌐 MojaFirma&lt;/div&gt;
    &lt;nav&gt;
        &lt;a href="#"&gt;Strona&lt;/a&gt;
        &lt;a href="#"&gt;O nas&lt;/a&gt;
        &lt;a href="#"&gt;Kontakt&lt;/a&gt;
    &lt;/nav&gt;
&lt;/header&gt;

#ex12-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    /* reszta stylów... */
}</pre>
            </div>
            <div class="info-box">💡 justify-content: space-between to klasyczny trick na logo-lewoPRAWO-menu.<br>
            Jeden element "pcha" się do lewej, drugi do prawej — Flexbox to robi automatycznie!</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ HTML I CSS — Ćwiczenie 12 ↓↓↓ -->
            <div class="ex-area" id="ex12-area">

                <style>
                    #ex12-header {
                        background-color: #4a148c;
                        padding: 15px 25px;
                        border-radius: 6px;
                        /* Dodaj: display: flex, justify-content: space-between, align-items: center */
                    }

                    #ex12-header .logo {
                        color: white;
                        font-size: 1.3em;
                        font-weight: bold;
                    }

                    #ex12-header nav {
                        display: flex;
                        gap: 10px;
                    }

                    #ex12-header nav a {
                        color: #e1bee7;
                        text-decoration: none;
                        padding: 6px 12px;
                        border-radius: 4px;
                    }

                    #ex12-header nav a:hover {
                        background-color: #7b1fa2;
                        color: white;
                    }
                </style>

                <!-- Wpisz tu header z .logo i nav z linkami -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 12 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK D: ŁĄCZENIE + PROJEKT
         Ćwiczenia 13–16
         ========================================== -->

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Przyciski w rzędzie — flex na grupie przycisków</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Umieść trzy przyciski w rzędzie z równymi odstępami. Użyj Flexbox na kontenerze przycisków. Dodaj <code>justify-content: center</code> żeby cały rząd był wyśrodkowany i <code>gap: 10px</code> między przyciskami.</p>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 13 ↓↓↓ -->
            <div class="ex-area" id="ex13-area">

                <style>
                    #ex13-przyciski {
                        /* display: flex, justify-content: center, gap: 10px */
                    }

                    #ex13-przyciski button {
                        padding: 10px 24px;
                        border: none;
                        border-radius: 6px;
                        font-size: 15px;
                        cursor: pointer;
                    }

                    #ex13-przyciski .btn-primary {
                        background-color: #7b1fa2;
                        color: white;
                    }

                    #ex13-przyciski .btn-secondary {
                        background-color: #e1bee7;
                        color: #4a148c;
                    }
                </style>

                <div id="ex13-przyciski">
                    <button class="btn-primary">Zapisz</button>
                    <button class="btn-secondary">Anuluj</button>
                    <button class="btn-secondary">Podgląd</button>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 13 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Galeria zdjęć — flex-wrap + karty</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz galerię zdjęć (możesz użyć prostokątów z kolorami zamiast prawdziwych zdjęć). Każdy element galerii powinien mieć stały rozmiar. Użyj <code>flex-wrap: wrap</code> i <code>justify-content: center</code> żeby galeria sama się układała w rzędy.</p>
            <div class="code-example">
                <h4>📄 Zamiast zdjęć możesz użyć:</h4>
                <pre>
&lt;div class="zdjecie"&gt;Zdjęcie 1&lt;/div&gt;

.zdjecie {
    width: 150px;
    height: 100px;
    background-color: #ba68c8;
    /* różne odcienie dla każdego elementu */
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 14 ↓↓↓ -->
            <div class="ex-area" id="ex14-area">

                <style>
                    #ex14-galeria {
                        /* display: flex, flex-wrap: wrap, justify-content: center, gap: 10px */
                    }

                    #ex14-galeria .zdjecie {
                        width: 150px;
                        height: 100px;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        color: white;
                        font-weight: bold;
                        border-radius: 6px;
                        font-size: 0.9em;
                    }
                </style>

                <div id="ex14-galeria">
                    <!-- Stwórz 8 divów z klasą .zdjecie i różnymi kolorami tła -->
                    <!-- Możesz dodać inline style="background-color: #kolorX" na każdym -->
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 14 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Karta z Flexbox — ikona, tytuł i opis obok siebie</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz trzy karty z ikoną po lewej i tekstem po prawej (układ poziomy wewnątrz karty). Użyj <code>display: flex</code> i <code>align-items: center</code> wewnątrz każdej karty — a same karty ułóż pionowo (<code>flex-direction: column</code>) w kontenerze.</p>
            <div class="code-example">
                <h4>📄 Struktura jednej karty:</h4>
                <pre>
&lt;div class="info-karta"&gt;
    &lt;div class="ikona"&gt;📧&lt;/div&gt;
    &lt;div class="tekst"&gt;
        &lt;h4&gt;Email&lt;/h4&gt;
        &lt;p&gt;kontakt@szkola.pl&lt;/p&gt;
    &lt;/div&gt;
&lt;/div&gt;

.info-karta {
    display: flex;
    align-items: center;
    gap: 15px;
    padding: 15px;
    /* border, border-radius, margin-bottom */
}</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 15 ↓↓↓ -->
            <div class="ex-area" id="ex15-area">

                <style>
                    .info-karta {
                        display: flex;
                        align-items: center;
                        gap: 15px;
                        padding: 15px;
                        border: 1px solid #d7aefb;
                        border-radius: 8px;
                        margin-bottom: 10px;
                        background-color: white;
                    }

                    .info-karta .ikona {
                        font-size: 2em;
                        flex-shrink: 0;
                    }

                    .info-karta h4 {
                        color: #4a148c;
                        margin-bottom: 4px;
                    }

                    .info-karta p {
                        color: #666;
                        font-size: 0.9em;
                    }
                </style>

                <!-- Stwórz 3 karty .info-karta z ikonką (emoji) i tekstem (h4 + p) -->
                <!-- Przykład: 📧 Email, 📞 Telefon, 📍 Adres -->

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
            <p><strong>Polecenie:</strong> W nowym pliku <code>strona_szkoly.html</code> z osobnym arkuszem <code>styl.css</code> wykonaj stronę internetową Technikum Informatycznego według poniższej specyfikacji. Układ strony pokazuje poniższy diagram.</p>

            <div class="code-example">
                <h4>📐 Diagram układu strony:</h4>
                <pre>
┌─────────────────────────────────────────────┐
│  LOGO (40%)          │  MENU NAGŁÓWKOWE (60%)│  ← display:flex, align-items:center
├─────────────────────────────────────────────┤
│               BANER (100%)                  │
├──────────────┬──────────────────────────────┤
│              │                              │
│  SIDEBAR     │      TREŚĆ GŁÓWNA            │  ← display:flex na main
│  (30%)       │      (70%)                   │
│              │   ┌──────┐┌──────┐┌──────┐   │
│              │   │KARTA ││KARTA ││KARTA │   │  ← flex-wrap:wrap
│              │   └──────┘└──────┘└──────┘   │
├─────────────────────────────────────────────┤
│                  STOPKA                     │  ← justify-content:center
└─────────────────────────────────────────────┘</pre>
            </div>

            <div style="background: #f3e5f5; border: 2px solid #d7aefb; border-radius: 8px; padding: 20px; margin: 10px 0;">
                <h3 style="color: #4a148c; margin-bottom: 14px;">📋 Specyfikacja (jak na egzaminie INF.03):</h3>

                <p style="color:#6a1b9a; font-weight:bold; margin-bottom:8px;">Blok LOGO:</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li><code>display: flex</code> na kontenerze nagłówka + <code>align-items: center</code></li>
                    <li>Logo: <code>flex: 1</code>, kolor tła <code>rgb(95, 39, 205)</code>, padding: 15px, kolor tekstu biały</li>
                    <li>Menu nagłówkowe: <code>flex: 2</code>, kolor tła <code>rgb(185, 215, 251)</code>, padding: 15px</li>
                    <li>Menu nagłówkowe: linki ułożone poziomo przez <code>display: flex</code> + <code>gap: 20px</code>, wyrównanie do prawej (<code>justify-content: flex-end</code>)</li>
                </ul>

                <p style="color:#6a1b9a; font-weight:bold; margin-bottom:8px;">Blok BANER:</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li>Pełna szerokość, wysokość <code>120px</code></li>
                    <li>Kolor tła <code>rgb(215, 174, 251)</code>, kolor tekstu <code>rgb(74, 20, 140)</code></li>
                    <li>Tekst wyśrodkowany: <code>display: flex</code> + <code>justify-content: center</code> + <code>align-items: center</code></li>
                    <li>Font-size: 1.6em, font-weight: bold</li>
                </ul>

                <p style="color:#6a1b9a; font-weight:bold; margin-bottom:8px;">Układ dwukolumnowy (main):</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li><code>display: flex</code> na elemencie <code>&lt;main&gt;</code>, <code>gap: 0</code></li>
                    <li>Sidebar (<code>&lt;aside&gt;</code>): <code>flex: 3</code>, kolor tła <code>rgb(243, 229, 245)</code>, padding: 20px, min-height: 300px</li>
                    <li>Treść (<code>&lt;article&gt;</code>): <code>flex: 7</code>, kolor tła <code>rgb(249, 249, 249)</code>, padding: 20px, min-height: 300px</li>
                    <li>W sidebarze: nagłówek h3 + lista nieuporządkowana z 4 linkami nawigacyjnymi</li>
                </ul>

                <p style="color:#6a1b9a; font-weight:bold; margin-bottom:8px;">Siatka kart w treści:</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0; margin-bottom:12px;">
                    <li>Kontener kart: <code>display: flex</code> + <code>flex-wrap: wrap</code> + <code>gap: 15px</code> + <code>margin-top: 20px</code></li>
                    <li>Minimum 4 karty, każda: <code>flex: 1</code> + <code>min-width: 150px</code>, kolor tła biały, border: 1px solid <code>rgb(215, 174, 251)</code>, border-radius: 8px, padding: 15px</li>
                    <li>W każdej karcie: nagłówek h4 + krótki paragraf</li>
                </ul>

                <p style="color:#6a1b9a; font-weight:bold; margin-bottom:8px;">Blok STOPKA:</p>
                <ul style="margin-left: 20px; color: #555; line-height: 2.0;">
                    <li>Kolor tła <code>rgb(74, 20, 140)</code>, kolor tekstu biały, padding: 20px</li>
                    <li>Treść wyśrodkowana: <code>display: flex</code> + <code>justify-content: center</code> + <code>align-items: center</code></li>
                    <li>Tekst stopki: "© 2025 Technikum Informatyczne" + Twój fikcyjny numer PESEL (11 cyfr) czcionką pogrubioną</li>
                </ul>
            </div>

            <div class="warning-box">⚠️ CSS piszesz w OSOBNYM pliku <code>styl.css</code> dołączonym przez <code>&lt;link&gt;</code> w sekcji head!<br>
            Na egzaminie INF.03 brak osobnego pliku CSS = utrata punktów.</div>
            <div class="info-box">💡 Przepisując kolory RGB ze specyfikacji pamiętaj: w CSS zawsze małe litery — <code>rgb(95, 39, 205)</code>, nie <code>RGB(95, 39, 205)</code>.<br>
            Sprawdź na końcu: czy suma flex sidebar + article = 10? (3 + 7 = 10 ✅)</div>
        </div>
    </div>

    <footer class="page-footer">
        <p>HTML5 i CSS — Część 3 | Flexbox | INF.03</p>
        <p style="margin-top: 10px; font-size: 0.9em;">📐 display:flex | ↔ justify-content | ↕ align-items | 🔀 flex-wrap</p>
    </footer>

</div>
</body>
</html>
```

---

## 📋 LISTA ĆWICZEŃ

### Blok A — Pierwsze kroki (ćwiczenia 1–4)
| Nr | Temat | Właściwości CSS |
|----|-------|-----------------|
| 1 | Włączenie Flexbox | display: flex |
| 2 | Kierunek ułożenia | flex-direction: row / column |
| 3 | Rozkład poziomy | justify-content (5 wartości) |
| 4 | Wyrównanie pionowe | align-items: flex-start / center / flex-end |

### Blok B — Gap i flex-wrap (ćwiczenia 5–8)
| Nr | Temat | Właściwości CSS |
|----|-------|-----------------|
| 5 | Odstępy między elementami | gap |
| 6 | Zawijanie do nowej linii | flex-wrap: nowrap / wrap |
| 7 | Równy podział miejsca | flex: 1, flex: 2 |
| 8 | Wyśrodkowanie poziome + pionowe | justify-content + align-items: center |

### Blok C — Praktyczne układy (ćwiczenia 9–12)
| Nr | Temat | Zastosowanie |
|----|-------|--------------|
| 9 | Nawigacja pozioma | menu w rzędzie — ul + li |
| 10 | Siatka kart produktów | flex-wrap na kontenerze kart |
| 11 | Układ strony: header/main/footer | aside + article w main |
| 12 | Pasek nagłówka | logo po lewej, menu po prawej |

### Blok D — Łączenie + Projekt (ćwiczenia 13–16)
| Nr | Temat | Zakres |
|----|-------|--------|
| 13 | Przyciski w rzędzie | justify-content: center na grupie przycisków |
| 14 | Galeria zdjęć | flex-wrap + justify-content: center |
| 15 | Karta pozioma (ikona + tekst) | align-items: center wewnątrz karty |
| 16 | 🏆 Strona szkoły / firmy | Wszystkie wzorce Flexbox w nowym pliku |

Miejsce na wysłanie plików pracy:

kl 3 TIe Jastrzębie: https://www.dropbox.com/request/f9ESlPFZOdyyfu2tnxH2


UWAGA Brak wysłania efektów pracy w terminie wyznaczonym przez nauczyciela to ocena ndst!
