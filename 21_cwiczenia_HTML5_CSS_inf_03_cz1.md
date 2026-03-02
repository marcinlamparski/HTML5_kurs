# 📝 SZABLON HTML - CZĘŚĆ 1 - SEMANTYCZNY HTML5 + SELEKTORY CSS

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT - ŚCIĄGAWKA PRZED ĆWICZENIAMI

Zanim zaczniesz ćwiczenia, przeczytaj to!

### Semantyczne tagi HTML5 — struktura strony:

| Tag | Zastępuje | Do czego służy? |
|-----|-----------|-----------------|
| `<header>` | `<div id="header">` | Nagłówek strony lub sekcji |
| `<nav>` | `<div id="menu">` | Nawigacja, menu linków |
| `<main>` | `<div id="content">` | Główna treść strony (1 na stronie!) |
| `<footer>` | `<div id="footer">` | Stopka strony lub sekcji |
| `<section>` | `<div class="sekcja">` | Tematyczna sekcja treści (ma nagłówek) |
| `<article>` | `<div class="artykul">` | Samodzielna treść (wpis, post, artykuł) |
| `<aside>` | `<div id="sidebar">` | Treść poboczna (sidebar, reklamy, linki) |

### Semantyczne tagi HTML5 — treść:

| Tag | Co robi? | Przykład użycia |
|-----|----------|-----------------|
| `<figure>` | Opakowanie dla ilustracji | Zdjęcie + podpis razem |
| `<figcaption>` | Podpis do `<figure>` | "Fot. Jan Kowalski" |
| `<time>` | Data lub godzina | `<time datetime="2025-09-01">` |
| `<mark>` | Wyróżnienie tekstu (zaznaczenie) | Jak marker na tekście |
| `<details>` | Rozwijana sekcja (bez JS!) | FAQ, spoilery |
| `<summary>` | Nagłówek dla `<details>` | Tekst klikany w details |

### Selektory CSS — ściągawka:

| Selektor | Składnia | Co wybiera? |
|----------|----------|-------------|
| Elementu | `p { }` | Wszystkie `<p>` na stronie |
| Klasy | `.box { }` | Wszystkie elementy z `class="box"` |
| Id | `#glowny { }` | Element z `id="glowny"` (jeden!) |
| Uniwersalny | `* { }` | Wszystkie elementy |
| Potomkowy | `nav a { }` | Wszystkie `<a>` wewnątrz `<nav>` |
| Grupowanie | `h1, h2, h3 { }` | h1 ORAZ h2 ORAZ h3 naraz |

### Właściwości CSS — typografia i kolory:

```css
/* CZCIONKA */
font-family: Arial, sans-serif;   /* rodzina czcionki */
font-size: 18px;                  /* rozmiar */
font-weight: bold;                /* grubość: normal, bold, 100-900 */
font-style: italic;               /* styl: normal, italic */
line-height: 1.6;                 /* odstęp między liniami */

/* KOLOR I TŁO */
color: #333333;                   /* kolor tekstu (hex) */
color: rgb(51, 51, 51);           /* kolor tekstu (rgb) */
color: darkgray;                  /* kolor tekstu (nazwa) */
background-color: #f0f0f0;        /* kolor tła */
background-color: rgb(240,240,240);
```

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 - HTML5 i CSS Część 1 - Semantyka i Selektory</title>
    <style>
        /* ============================================================
           STYLE SZABLONU - nie zmieniaj tej sekcji!
           ============================================================ */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%);
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
            background: #84fab0;
            color: #2d6a4f;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            text-align: center;
            line-height: 40px;
            font-weight: bold;
            margin-right: 15px;
            font-size: 1.2em;
        }

        .task-title {
            color: #333;
            font-size: 1.3em;
        }

        .difficulty {
            margin-left: auto;
            font-size: 0.9em;
            color: #888;
        }

        .difficulty-star {
            color: #ffa500;
        }

        .task-content {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 6px;
            border-left: 4px solid #84fab0;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #e8f5e9;
            border: 1px solid #a5d6a7;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #2e7d32;
            font-size: 0.95em;
        }

        .warning-box {
            background: #fff8e1;
            border: 1px solid #ffe082;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #f57f17;
            font-size: 0.95em;
        }

        .code-before {
            background: #ffebee;
            border: 1px solid #ef9a9a;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            font-size: 0.9em;
        }

        .code-before h4 {
            color: #c62828;
            margin-bottom: 6px;
            font-size: 0.9em;
        }

        .code-before pre {
            color: #555;
            line-height: 1.5;
            white-space: pre-wrap;
        }

        /* ============================================================
           OBSZARY ĆWICZEŃ
           ============================================================ */
        .ex-area {
            background: white;
            border: 2px dashed #84fab0;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            min-height: 60px;
        }

        .ex-area-label {
            font-size: 0.8em;
            color: #84fab0;
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

        /* ============================================================
           ↓↓↓ ĆWICZENIA CSS 9-16: TWÓJ KOD PISZESZ PONIŻEJ ↓↓↓
           ============================================================ */

        /* === ĆWICZENIE 9: Selektor elementu ===
           Zadanie: Nadaj style elementom w sekcji id="ex9-area"
           Wskazówka: używaj selektora potomkowego np. #ex9-area p { }
        */


        /* === ĆWICZENIE 10: Selektor klasy ===
           Zadanie: Ostyluj elementy z klasami .ex10-tytul, .ex10-tekst, .ex10-wazny
        */


        /* === ĆWICZENIE 11: Selektor id ===
           Zadanie: Ostyluj elementy #ex11-naglowek, #ex11-tresc, #ex11-stopka
        */


        /* === ĆWICZENIE 12: Selektor potomkowy ===
           Zadanie: Ostyluj a tylko w nav#ex12-nav i p tylko w article.ex12-art
        */


        /* === ĆWICZENIE 13: Grupowanie selektorów ===
           Zadanie: Ostyluj h2, h3, h4 w sekcji #ex13-area naraz, potem * w #ex13-box
        */


        /* === ĆWICZENIE 14: Właściwości czcionki ===
           Zadanie: Ostyluj elementy w #ex14-area: font-family, size, weight, style, line-height
        */


        /* === ĆWICZENIE 15: Kolory i tła ===
           Zadanie: Nadaj kolory (hex, rgb, named) elementom w #ex15-area
        */


        /* === ĆWICZENIE 16: Mini-projekt — strona wizytówkowa ===
           Zadanie: Ostyluj cały mini-projekt #ex16-area
        */

    </style>
</head>
<body>

<div class="container">

    <!-- NAGŁÓWEK STRONY (element szablonu - nie modyfikuj) -->
    <header class="page-header">
        <h1>🌿 HTML5 + CSS — Część 1</h1>
        <p>Semantyczny HTML5 i Selektory CSS | Przygotowanie do egzaminu INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: SEMANTYCZNA STRUKTURA STRONY
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">Zamień divy na tagi strukturalne</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej widzisz stronę zbudowaną ze zwykłych <code>&lt;div&gt;</code>. Zamień każdy <code>&lt;div&gt;</code> na odpowiedni semantyczny tag HTML5: <code>&lt;header&gt;</code>, <code>&lt;nav&gt;</code>, <code>&lt;main&gt;</code>, <code>&lt;footer&gt;</code>. Treść zostawiasz bez zmian!</p>
            <div class="code-before">
                <h4>❌ PRZED — kod z divami (tak nie robimy!):</h4>
                <pre>
&lt;div id="header"&gt;
    &lt;h1&gt;Moja strona&lt;/h1&gt;
&lt;/div&gt;
&lt;div id="nav"&gt;
    &lt;a href="#"&gt;Strona główna&lt;/a&gt;
    &lt;a href="#"&gt;O mnie&lt;/a&gt;
&lt;/div&gt;
&lt;div id="main"&gt;
    &lt;p&gt;Witaj na mojej stronie!&lt;/p&gt;
&lt;/div&gt;
&lt;div id="footer"&gt;
    &lt;p&gt;&copy; 2025 Jan Kowalski&lt;/p&gt;
&lt;/div&gt;</pre>
            </div>
            <div class="info-box">💡 Zamień: div#header → &lt;header&gt;, div#nav → &lt;nav&gt;, div#main → &lt;main&gt;, div#footer → &lt;footer&gt;</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — napisz tu semantyczny HTML:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <!-- Zamień divy poniżej na semantyczne tagi! -->
                <div>
                    <h1>Moja strona</h1>
                </div>
                <div>
                    <a href="#">Strona główna</a>
                    <a href="#">O mnie</a>
                    <a href="#">Kontakt</a>
                </div>
                <div>
                    <p>Witaj na mojej stronie! Tu znajdziesz informacje o mnie i moich projektach.</p>
                </div>
                <div>
                    <p>© 2025 Jan Kowalski</p>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">section i article — podział treści</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W obszarze poniżej masz trzy bloki treści opakowane w <code>&lt;div&gt;</code>. Pierwszy blok to wiadomości — zamień go na <code>&lt;section&gt;</code>. Dwa bloki wewnętrzne to osobne artykuły — zamień je na <code>&lt;article&gt;</code>.</p>
            <div class="info-box">💡 <strong>section</strong> = tematyczna sekcja z nagłówkiem | <strong>article</strong> = samodzielna treść (można ją wyjąć ze strony i nadal ma sens)</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <!-- Zamień div na section, a dwa wewnętrzne div na article -->
                <div>
                    <h2>Najnowsze wiadomości</h2>

                    <div>
                        <h3>Szkoła zdobyła nagrodę!</h3>
                        <p>Nasza szkoła zajęła pierwsze miejsce w konkursie programistycznym.</p>
                    </div>

                    <div>
                        <h3>Nowe pracownie komputerowe</h3>
                        <p>W tym roku otwieramy dwie nowe pracownie wyposażone w nowoczesny sprzęt.</p>
                    </div>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">aside — treść poboczna</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej masz układ z artykułem i bocznym panelem. Zamień tagi tak, by: główna treść była w <code>&lt;article&gt;</code>, a panel boczny w <code>&lt;aside&gt;</code>. Opakuj całość w <code>&lt;main&gt;</code>.</p>
            <div class="info-box">💡 <strong>aside</strong> = treść powiązana, ale poboczna: linki, reklamy, biogram autora, widget kalendarza</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <!-- Zamień strukturę na: main > article + aside -->
                <div id="strona">

                    <div id="artykul">
                        <h2>Jak nauczyć się programowania?</h2>
                        <p>Programowania najlepiej uczyć się przez praktykę. Zacznij od małych projektów i stopniowo zwiększaj poziom trudności.</p>
                        <p>Wybierz jeden język i opanuj go dobrze, zanim przejdziesz do następnego.</p>
                    </div>

                    <div id="panel-boczny">
                        <h3>Powiązane artykuły</h3>
                        <ul>
                            <li><a href="#">Najlepsze kursy online</a></li>
                            <li><a href="#">Jakim językiem zacząć?</a></li>
                            <li><a href="#">Portfolio dla programisty</a></li>
                        </ul>
                    </div>

                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">Zbuduj nawigację od podstaw</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Napisz od zera kod nawigacji strony szkoły. Użyj: <code>&lt;nav&gt;</code> jako opakowania, <code>&lt;ul&gt;</code> z elementami <code>&lt;li&gt;</code>, w każdym <code>&lt;li&gt;</code> link <code>&lt;a href="#"&gt;</code>. Linki: Strona główna, Plan lekcji, Nauczyciele, Galeria, Kontakt.</p>
            <div class="warning-box">⚠️ Pamiętaj o prawidłowym zagnieżdżeniu: nav → ul → li → a</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — napisz tu nawigację:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <!-- Tu napisz całą nawigację od zera -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: SEMANTYCZNE TAGI TREŚCI
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">figure i figcaption — ilustracja z podpisem</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Opakuj zdjęcie i jego podpis w tagi <code>&lt;figure&gt;</code> i <code>&lt;figcaption&gt;</code>. Zdjęcie (<code>&lt;img&gt;</code>) oraz podpis tekstowy mają się znaleźć wewnątrz <code>&lt;figure&gt;</code>. Podpis wsadź w <code>&lt;figcaption&gt;</code>.</p>
            <div class="info-box">💡 figure opakuje: obraz, wykres, schemat, kod, cytat z podpisem. figcaption = legenda/podpis</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <!-- Opakuj to w figure + figcaption -->
                <img src="https://via.placeholder.com/300x200/84fab0/ffffff?text=Zdjecie+szkolne"
                     alt="Budynek szkoły" width="300">
                Fot. Archiwum szkoły, 2024 rok

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">time — oznaczanie dat</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Opakuj każdą datę/godzinę w tekście znacznikiem <code>&lt;time&gt;</code> z odpowiednim atrybutem <code>datetime</code>. Format datetime: <code>RRRR-MM-DD</code> dla dat, <code>HH:MM</code> dla godzin.</p>
            <div class="info-box">💡 Przykład: &lt;time datetime="2025-09-01"&gt;1 września 2025&lt;/time&gt;<br>
            Atrybut datetime jest dla przeglądarek i wyszukiwarek — treść tagu widzą użytkownicy.</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — opakuj daty w time:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <article>
                    <h3>Zebranie rady pedagogicznej</h3>
                    <p>Zebranie odbędzie się <span>15 września 2025</span> o godzinie <span>16:00</span>.</p>
                    <p>Opublikowano: <span>10 września 2025</span></p>
                </article>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">mark — wyróżnianie tekstu</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Użyj znacznika <code>&lt;mark&gt;</code> do wyróżnienia kluczowych słów w poniższym tekście. Wyróżnij: "HTML5", "CSS" i "JavaScript". Sprawdź jak wygląda efekt w przeglądarce!</p>
            <div class="info-box">💡 &lt;mark&gt; to semantyczne wyróżnienie (jak żółty marker). Używaj gdy zaznaczasz wyniki wyszukiwania lub kluczowe pojęcia.</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — dodaj mark do kluczowych słów:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <p>Na egzaminie INF.03 musisz znać trzy technologie: HTML5, CSS i JavaScript.
                HTML5 służy do tworzenia struktury strony, CSS do jej stylizowania,
                a JavaScript do dodawania interaktywności. Opanowanie HTML5 i CSS
                to podstawa — bez nich nie napiszesz żadnej strony internetowej.</p>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">details i summary — rozwijana sekcja (bez JS!)</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz sekcję FAQ (Często zadawane pytania) używając wyłącznie <code>&lt;details&gt;</code> i <code>&lt;summary&gt;</code>. Każde pytanie to jeden blok <code>&lt;details&gt;</code>, pytanie w <code>&lt;summary&gt;</code>, odpowiedź w <code>&lt;p&gt;</code>. Zrób 3 pytania z dowolnymi odpowiedziami.</p>
            <div class="info-box">💡 details + summary = rozwijany/zwijany element bez żadnego JavaScript! Kliknij wynikowy element w przeglądarce.</div>
            <div class="ex-area-label">✏️ TWOJE ROZWIĄZANIE — stwórz FAQ z 3 pytaniami:</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <!-- Tu napisz 3 bloki details+summary -->
                <!-- Przykład struktury jednego:
                <details>
                    <summary>Pytanie?</summary>
                    <p>Odpowiedź.</p>
                </details>
                -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: SELEKTORY CSS — PODSTAWOWE
         Ćwiczenia 9–11
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">Selektor elementu — styluj tagi bezpośrednio</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> W sekcji CSS (na górze pliku) dopisz reguły dla selektora elementu, które ostylują elementy wewnątrz <code>#ex9-area</code>. Wymagania:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li>Nagłówek <code>h3</code> — kolor tekstu <code>#2d6a4f</code>, rozmiar czcionki <code>20px</code></li>
                <li>Paragrafy <code>p</code> — kolor tekstu <code>#555</code>, odstęp między liniami <code>1.7</code></li>
                <li>Lista <code>ul</code> — lewy margines wewnętrzny (padding-left) <code>20px</code></li>
            </ul>
            <div class="warning-box">⚠️ Używaj selektora potomkowego! Pisz: <code>#ex9-area h3 { }</code> — nie samo <code>h3 { }</code>, bo zmienisz styl wszystkich h3 na stronie!</div>
            <!-- HTML do ostylowania - nie modyfikuj -->
            <div class="ex-area" id="ex9-area">
                <h3>Języki webowe</h3>
                <p>Do tworzenia stron internetowych używamy trzech głównych technologii.</p>
                <ul>
                    <li>HTML5 — struktura i treść</li>
                    <li>CSS — wygląd i układ</li>
                    <li>JavaScript — interaktywność</li>
                </ul>
                <p>Każda z nich ma swoją określoną rolę.</p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">Selektor klasy — styluj przez .klasa</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Poniżej masz elementy z różnymi klasami. W sekcji CSS dopisz reguły dla:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li><code>.ex10-tytul</code> — czcionka pogrubiona, kolor <code>#1b5e20</code>, rozmiar <code>22px</code></li>
                <li><code>.ex10-tekst</code> — kolor <code>#444</code>, kursywa</li>
                <li><code>.ex10-wazny</code> — kolor tła <code>#fff9c4</code>, kolor tekstu <code>#e65100</code>, pogrubiony</li>
            </ul>
            <div class="info-box">💡 Jeden element może mieć kilka klas: class="ex10-tekst ex10-wazny" — dostaną oba zestawy stylów!</div>
            <!-- HTML do ostylowania -->
            <div class="ex-area" id="ex10-area">
                <p class="ex10-tytul">Zasady pisania czystego kodu</p>
                <p class="ex10-tekst">Dobry kod jest czytelny, dobrze skomentowany i łatwy do modyfikacji.</p>
                <p class="ex10-tekst">Stosuj wcięcia i spójne nazewnictwo zmiennych i klas.</p>
                <p class="ex10-wazny">WAŻNE: Nie kopiuj kodu bez zrozumienia!</p>
                <p class="ex10-tekst ex10-wazny">Ten paragraf ma dwie klasy naraz!</p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">Selektor id — styluj unikalny element</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Ostyluj trzy unikalne elementy używając selektora <code>#id</code>:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li><code>#ex11-naglowek</code> — tło <code>#2d6a4f</code>, kolor tekstu <code>white</code>, padding <code>15px</code></li>
                <li><code>#ex11-tresc</code> — tło <code>#f1f8e9</code>, padding <code>15px</code>, rozmiar czcionki <code>16px</code></li>
                <li><code>#ex11-stopka</code> — kolor tekstu <code>#888</code>, rozmiar czcionki <code>12px</code>, kursywa</li>
            </ul>
            <div class="warning-box">⚠️ id musi być UNIKALNE — tylko jeden element na stronie może mieć dane id. Jeśli chcesz stylować wiele elementów → użyj klasy!</div>
            <!-- HTML do ostylowania -->
            <div class="ex-area" id="ex11-area">
                <div id="ex11-naglowek">
                    <h3>Karta ucznia</h3>
                </div>
                <div id="ex11-tresc">
                    <p>Imię i nazwisko: Jan Kowalski</p>
                    <p>Klasa: 3TIA</p>
                    <p>Specjalizacja: Programowanie aplikacji internetowych</p>
                </div>
                <div id="ex11-stopka">
                    <p>Wygenerowano automatycznie przez system szkolny.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- ==========================================
         BLOK D: SELEKTORY ZAAWANSOWANE
         Ćwiczenia 12–13
         ========================================== -->

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Selektor potomkowy — styluj elementy w kontekście</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Użyj selektora potomkowego, żeby te same tagi wyglądały inaczej w różnych kontekstach:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li>Linki <code>a</code> wewnątrz <code>nav#ex12-nav</code> — kolor <code>#1b5e20</code>, bez podkreślenia, pogrubione</li>
                <li>Paragrafy <code>p</code> wewnątrz <code>article.ex12-art</code> — wcięcie tekstowe <code>20px</code> (text-indent), kolor <code>#333</code></li>
                <li>Elementy <code>li</code> wewnątrz <code>aside.ex12-aside</code> — styl listy: brak punktorów, kolor <code>#555</code></li>
            </ul>
            <div class="info-box">💡 Selektor potomkowy: <code>nav a { }</code> wybiera WSZYSTKIE &lt;a&gt; wewnątrz &lt;nav&gt; — nie tylko bezpośrednie dzieci!</div>
            <!-- HTML do ostylowania -->
            <div class="ex-area" id="ex12-area">
                <nav id="ex12-nav">
                    <a href="#">Start</a> |
                    <a href="#">Kursy</a> |
                    <a href="#">Kontakt</a>
                </nav>
                <article class="ex12-art">
                    <h3>O kursie HTML5</h3>
                    <p>Kurs obejmuje wszystkie nowe elementy semantyczne HTML5.</p>
                    <p>Nauczysz się budować strony zgodne ze standardami W3C.</p>
                </article>
                <aside class="ex12-aside">
                    <h4>Zasoby:</h4>
                    <ul>
                        <li><a href="#">MDN Web Docs</a></li>
                        <li><a href="#">W3Schools</a></li>
                        <li><a href="#">CSS-Tricks</a></li>
                    </ul>
                </aside>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Grupowanie selektorów i selektor * (gwiazdka)</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Ćwiczenie w dwóch częściach:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li><strong>Część A:</strong> Jedną regułą CSS nadaj styl dla <code>h2</code>, <code>h3</code> i <code>h4</code> w <code>#ex13-area</code>: kolor <code>#2d6a4f</code>, dolna granica <code>1px solid #84fab0</code></li>
                <li><strong>Część B:</strong> Użyj <code>* { }</code> dla elementów w <code>#ex13-box</code>: ustaw <code>box-sizing: border-box</code> i <code>font-family: Arial, sans-serif</code></li>
            </ul>
            <div class="info-box">💡 Grupowanie: <code>h2, h3, h4 { }</code> — przecinek oznacza "ORAZ". Zamiast pisać 3 reguły, piszesz jedną!</div>
            <!-- HTML do ostylowania -->
            <div class="ex-area" id="ex13-area">
                <h2>Nagłówek H2</h2>
                <p>Akapit między nagłówkami.</p>
                <h3>Nagłówek H3</h3>
                <p>Kolejny akapit.</p>
                <h4>Nagłówek H4</h4>

                <div id="ex13-box">
                    <p>Ten box ma własny font i box-sizing przez selektor *.</p>
                    <span>Span też dostanie styl od gwiazdki.</span>
                </div>
            </div>
        </div>
    </div>

    <!-- ==========================================
         BLOK E: TYPOGRAFIA I KOLORY CSS
         Ćwiczenia 14–16
         ========================================== -->

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Właściwości czcionki — font-*</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Ostyluj elementy w <code>#ex14-area</code> używając właściwości czcionki:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li><code>#ex14-tytul</code> — font-family: Georgia, serif | font-size: 28px | font-weight: bold</li>
                <li><code>#ex14-autor</code> — font-family: Arial, sans-serif | font-size: 14px | font-style: italic | kolor: #888</li>
                <li><code>#ex14-tresc</code> — font-family: 'Segoe UI', sans-serif | font-size: 16px | line-height: 2.0</li>
                <li><code>#ex14-cytat</code> — font-size: 18px | font-style: italic | font-weight: bold | kolor: #2d6a4f</li>
            </ul>
            <!-- HTML do ostylowania -->
            <div class="ex-area" id="ex14-area">
                <p id="ex14-tytul">Semantyczny HTML5 — dlaczego warto?</p>
                <p id="ex14-autor">Autor: Anna Nowak | Data: 2025-09-10</p>
                <div id="ex14-tresc">
                    <p>Semantyczny HTML5 sprawia, że kod strony jest czytelniejszy — zarówno dla programistów, jak i dla wyszukiwarek internetowych. Tagi takie jak &lt;article&gt;, &lt;section&gt; czy &lt;nav&gt; jednoznacznie opisują zawartość.</p>
                </div>
                <p id="ex14-cytat">"Dobry kod HTML to taki, który rozumiesz po roku bez zaglądania do komentarzy."</p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Kolory i tła — hex, rgb, nazwy kolorów</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Nadaj kolory elementom w <code>#ex15-area</code> — używając trzech różnych formatów zapisu:</p>
            <ul style="margin: 10px 0 10px 20px; color: #555;">
                <li><code>.ex15-hex</code> — kolor tekstu: <code>#c0392b</code> (hex), tło: <code>#fadbd8</code> (hex), padding: 10px</li>
                <li><code>.ex15-rgb</code> — kolor tekstu: <code>rgb(39, 174, 96)</code> (rgb), tło: <code>rgb(212, 239, 223)</code> (rgb), padding: 10px</li>
                <li><code>.ex15-nazwa</code> — kolor tekstu: <code>navy</code> (nazwa), tło: <code>lightblue</code> (nazwa), padding: 10px</li>
                <li><code>.ex15-mix</code> — dowolna kombinacja, ale różne tło i tekst, margin-top: 10px</li>
            </ul>
            <div class="info-box">💡 Wszystkie trzy zapisy są równoważne: <code>#ff0000</code> = <code>rgb(255,0,0)</code> = <code>red</code></div>
            <!-- HTML do ostylowania -->
            <div class="ex-area" id="ex15-area">
                <p class="ex15-hex">Ten tekst używa kolorów zapisanych w formacie HEX (#rrggbb)</p>
                <p class="ex15-rgb">Ten tekst używa kolorów zapisanych w formacie RGB(r,g,b)</p>
                <p class="ex15-nazwa">Ten tekst używa nazw kolorów CSS (color keywords)</p>
                <p class="ex15-mix">Ten tekst używa dowolnej mieszanki formatów — Twój wybór!</p>
            </div>
        </div>
    </div>

    <!-- ĆWICZENIE 16 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">16</div>
            <div class="task-title">Mini-projekt — strona wizytówkowa</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Uzupełnij stronę wizytówkową dwuetapowo:</p>
            <p><strong>Etap 1 (HTML):</strong> W obszarze poniżej zastąp wszystkie <code>&lt;div&gt;</code> semantycznymi tagami. Użyj: <code>&lt;header&gt;</code>, <code>&lt;nav&gt;</code>, <code>&lt;main&gt;</code>, <code>&lt;article&gt;</code>, <code>&lt;aside&gt;</code>, <code>&lt;footer&gt;</code>, <code>&lt;figure&gt;</code>, <code>&lt;figcaption&gt;</code>.</p>
            <p><strong>Etap 2 (CSS):</strong> W sekcji CSS nadaj stronie atrakcyjny wygląd: tło nagłówka, styl nawigacji, kolory tekstu, czcionki.</p>
            <div class="warning-box">⚠️ To jest ćwiczenie integrujące! Łączysz WSZYSTKO z tej lekcji: semantykę HTML5 + selektory CSS + typografię + kolory.</div>
            <!-- ↓↓↓ TUTAJ MODYFIKUJESZ HTML — Ćwiczenie 16 ↓↓↓ -->
            <div class="ex-area" id="ex16-area">

                <!-- ETAP 1: Zamień divy na semantyczne tagi! -->
                <div id="ex16-strona">

                    <div><!-- nagłówek -->
                        <h1>Katarzyna Wiśniewska</h1>
                        <p>Programistka | Projektantka UI | Nauczycielka</p>
                    </div>

                    <div><!-- nawigacja -->
                        <a href="#">O mnie</a>
                        <a href="#">Portfolio</a>
                        <a href="#">Blog</a>
                        <a href="#">Kontakt</a>
                    </div>

                    <div><!-- główna treść -->

                        <div><!-- artykuł -->
                            <h2>O mnie</h2>
                            <p>Tworzę strony internetowe od 2010 roku. Specjalizuję się w HTML5, CSS3 i JavaScript. Uczę programowania w technikum informatycznym.</p>
                            <p>Lubię tworzyć czytelny kod i intuicyjne interfejsy użytkownika.</p>
                        </div>

                        <div><!-- sidebar -->
                            <h3>Umiejętności</h3>
                            <ul>
                                <li>HTML5 / CSS3</li>
                                <li>JavaScript</li>
                                <li>PHP / MySQL</li>
                                <li>Git / GitHub</li>
                            </ul>

                            <div><!-- figure z zdjęciem -->
                                <img src="https://via.placeholder.com/150x150/2d6a4f/ffffff?text=KW"
                                     alt="Katarzyna Wiśniewska" width="150">
                                Katarzyna Wiśniewska, 2025
                            </div>
                        </div>

                    </div>

                    <div><!-- stopka -->
                        <p>© 2025 Katarzyna Wiśniewska | Ostatnia aktualizacja:
                            <span>1 września 2025</span>
                        </p>
                    </div>

                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 16 ↑↑↑ -->
        </div>
    </div>

    <footer class="page-footer">
        <p>Przygotowanie do egzaminu INF.03 — HTML5 i CSS Część 1</p>
        <p style="margin-top: 10px; font-size: 0.9em;">🌿 HTML5 | 🎨 CSS | 📐 Semantyka | 🔍 Selektory</p>
    </footer>

</div>
</body>
</html>
```

**Instrukcja dla uczniów:**
1. Skopiuj powyższy HTML do nowego pliku `cwiczenia_html_css_cz1.html`
2. Otwórz go w VS Code
3. Otwórz w przeglądarce (Live Server lub F5)
4. **Ćwiczenia 1–8 (HTML):** Szukaj komentarzy `↓↓↓ TUTAJ MODYFIKUJESZ HTML ↓↓↓` — tam zamieniasz tagi
5. **Ćwiczenia 9–16 (CSS):** Dodajesz reguły CSS w sekcji `<style>` na górze pliku — są tam już przygotowane komentarze!
6. Po każdej zmianie odśwież przeglądarkę i sprawdź efekt

---

## 📋 LISTA ĆWICZEŃ (bez rozwiązań)

### Blok A — Semantyczna struktura strony (ćwiczenia 1–4)

| Nr | Temat | Nowe tagi |
|----|-------|-----------|
| 1 | Zamień divy na tagi strukturalne | header, nav, main, footer |
| 2 | section i article — podział treści | section, article |
| 3 | aside — treść poboczna | main, article, aside |
| 4 | Zbuduj nawigację od podstaw | nav, ul, li, a |

### Blok B — Semantyczne tagi treści (ćwiczenia 5–8)

| Nr | Temat | Nowe tagi |
|----|-------|-----------|
| 5 | figure i figcaption | figure, figcaption |
| 6 | time — oznaczanie dat | time, datetime="" |
| 7 | mark — wyróżnianie tekstu | mark |
| 8 | details i summary — FAQ bez JS | details, summary |

### Blok C — Selektory CSS podstawowe (ćwiczenia 9–11)

| Nr | Temat | Selektor CSS |
|----|-------|-------------|
| 9 | Selektor elementu | p { }, h3 { }, ul { } |
| 10 | Selektor klasy | .nazwa-klasy { } |
| 11 | Selektor id | #nazwa-id { } |

### Blok D — Selektory zaawansowane (ćwiczenia 12–13)

| Nr | Temat | Selektor CSS |
|----|-------|-------------|
| 12 | Selektor potomkowy | nav a { }, article p { } |
| 13 | Grupowanie + gwiazdka | h1, h2, h3 { } i * { } |

### Blok E — Typografia i kolory (ćwiczenia 14–16)

| Nr | Temat | Właściwości CSS |
|----|-------|----------------|
| 14 | Właściwości czcionki | font-family, font-size, font-weight, font-style, line-height |
| 15 | Kolory i tła | color, background-color (hex, rgb, nazwy) |
| 16 | Mini-projekt wizytówka | Wszystko razem! |

Link do wysłania ćwiczeń (tylko plik HTML) 

Klasa 3TIe Jastrzębie Zdrój: https://www.dropbox.com/request/3P3rnorUeObc2RZLnr7s
