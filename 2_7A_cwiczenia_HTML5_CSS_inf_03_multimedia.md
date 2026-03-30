# 📝 SZABLON HTML — CZĘŚĆ 5A — MULTIMEDIA

Uczniowie pracują na tym pliku. Skopiuj blok HTML do nowego pliku `.html` i otwórz w przeglądarce.

---

## 📚 SUPLEMENT — ŚCIĄGAWKA PRZED ĆWICZENIAMI

### Obrazki — `<img>`

```html
<!-- Podstawowa składnia -->
<img src="zdjecie.jpg" alt="Opis zdjęcia">

<!-- Pełna składnia z wymiarami i podpisem -->
<img src="zdjecie.jpg" alt="Opis zdjęcia" width="400" height="300" title="Tekst po najechaniu">

<!-- Semantyczne opakowanie z podpisem -->
<figure>
    <img src="zdjecie.jpg" alt="Opis zdjęcia">
    <figcaption>Podpis pod zdjęciem</figcaption>
</figure>
```

### Ścieżki do plików — WAŻNE!

```
Struktura folderów:                 Ścieżki:
projekt/
├── index.html                      src="zdjecie.jpg"          (ten sam folder)
├── zdjecie.jpg
├── obrazki/
│   └── logo.png                    src="obrazki/logo.png"     (podfolder)
└── podstrony/
    └── kontakt.html                src="../zdjecie.jpg"        (folder wyżej)
                                    src="../obrazki/logo.png"   (folder wyżej + podfolder)

Ścieżka bezwzględna (URL):          src="https://example.com/foto.jpg"
```

### Formaty obrazów — kiedy który?

```
JPG / JPEG  → zdjęcia, fotografie — dobra kompresja, małe pliki
PNG         → logo, ikony, grafiki z przezroczystością (tło transparentne)
GIF         → proste animacje, małe ikony
WebP        → nowoczesny format — mniejszy od JPG i PNG, dobra jakość
SVG         → grafika wektorowa — skaluje się bez utraty jakości (logo, ikony)
```

### Stylowanie obrazków przez CSS

```css
img {
    width: 300px;           /* szerokość (nadpisuje atrybut HTML) */
    height: auto;           /* wysokość automatyczna — zachowuje proporcje */
    border: 3px solid red;  /* ramka */
    border-radius: 50%;     /* okrągły obrazek */
    object-fit: cover;      /* wypełnia obszar nie deformując obrazka */
    float: left;            /* obrazek z opływającym tekstem */
    margin: 10px;           /* odstępy */
}
```

### Tło z obrazka — CSS `background-image`

```css
div {
    background-image: url("tlo.jpg");
    background-size: cover;      /* wypełnia cały element */
    background-size: contain;    /* mieści cały obrazek */
    background-position: center; /* wyśrodkowanie */
    background-repeat: no-repeat; /* bez powtarzania */
}
```

### Responsywne obrazki — `srcset`

```html
<!-- Przeglądarka wybiera odpowiedni rozmiar zależnie od ekranu -->
<img
    src="foto-800.jpg"
    srcset="foto-400.jpg 400w,
            foto-800.jpg 800w,
            foto-1200.jpg 1200w"
    sizes="(max-width: 600px) 400px, 800px"
    alt="Opis zdjęcia">

<!-- Lub przez <picture> — różne zdjęcia dla różnych ekranów -->
<picture>
    <source media="(max-width: 600px)" srcset="foto-male.jpg">
    <source media="(max-width: 1200px)" srcset="foto-srednie.jpg">
    <img src="foto-duze.jpg" alt="Opis zdjęcia">
</picture>
```

### Audio

```html
<audio controls>
    <source src="muzyka.mp3" type="audio/mpeg">
    <source src="muzyka.ogg" type="audio/ogg">
    Twoja przeglądarka nie obsługuje tagu audio.
</audio>

<!-- Atrybuty: -->
controls   → pokazuje kontrolki odtwarzacza
autoplay   → automatyczne odtwarzanie (często blokowane przez przeglądarki)
loop       → zapętlenie
muted      → wyciszony na start
```

### Video

```html
<video width="640" height="360" controls poster="okladka.jpg">
    <source src="film.mp4" type="video/mp4">
    <source src="film.webm" type="video/webm">
    Twoja przeglądarka nie obsługuje tagu video.
</video>

<!-- Atrybuty: -->
controls   → kontrolki odtwarzacza
poster     → obrazek wyświetlany przed odtworzeniem
autoplay   → auto-start (wymaga też muted w większości przeglądarek)
loop       → zapętlenie
muted      → wyciszony
width/height → wymiary odtwarzacza
```

---

## 🎯 SZABLON HTML DO PRACY

```html
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>INF.03 — HTML5 i CSS Część 5A — Multimedia</title>
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
            background: linear-gradient(135deg, #ff6b6b 0%, #feca57 100%);
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
            background: #ff6b6b;
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
            border-left: 4px solid #ff6b6b;
        }

        .task-content > p {
            margin: 10px 0;
            color: #555;
            line-height: 1.6;
        }

        .info-box {
            background: #fff5e6;
            border: 1px solid #feca57;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #8b5e00;
            font-size: 0.95em;
            line-height: 1.5;
        }

        .warning-box {
            background: #fff0f0;
            border: 1px solid #ff6b6b;
            border-radius: 4px;
            padding: 10px 14px;
            margin: 10px 0;
            color: #c0392b;
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
            border: 2px dashed #feca57;
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
        <h1>🎨 Multimedia</h1>
        <p>Część 5A — HTML5 i CSS | INF.03</p>
    </header>

    <!-- ==========================================
         BLOK A: PODSTAWY <img>
         Ćwiczenia 1–4
         ========================================== -->

    <!-- ĆWICZENIE 1 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">1</div>
            <div class="task-title">Podstawowy tag &lt;img&gt; — src i alt</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wstaw trzy obrazki za pomocą tagu <code>&lt;img&gt;</code>. Każdy musi mieć atrybuty <code>src</code> i <code>alt</code>. Użyj adresów URL z serwisu <code>https://picsum.photos</code> — podajesz szerokość i wysokość w adresie i dostajesz losowe zdjęcie.</p>
            <div class="code-example">
                <h4>📄 Serwis do ćwiczeń bez własnych zdjęć:</h4>
                <pre>
&lt;!-- picsum.photos/szerokość/wysokość --&gt;
&lt;img src="https://picsum.photos/300/200" alt="Losowe zdjęcie 1"&gt;
&lt;img src="https://picsum.photos/200/200" alt="Losowe zdjęcie 2"&gt;

&lt;!-- Konkretne zdjęcie po ID: --&gt;
&lt;img src="https://picsum.photos/id/10/300/200" alt="Las"&gt;</pre>
            </div>
            <div class="warning-box">⚠️ Atrybut <code>alt</code> jest OBOWIĄZKOWY — brak alt to błąd walidacji W3C!<br>
            Opisuj co widać na zdjęciu: <code>alt="Zachód słońca nad morzem"</code>, nie <code>alt="zdjecie1"</code>.</div>
            <div class="info-box">💡 Na egzaminie INF.03 obrazki mają podany plik lokalny np. <code>src="foto.jpg"</code>.<br>
            W ćwiczeniach używamy picsum.photos żeby nie potrzebować własnych plików graficznych.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 1 ↓↓↓ -->
            <div class="ex-area" id="ex1-area">

                <!-- Wstaw tu 3 obrazki z picsum.photos z różnymi rozmiarami i opisami alt -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 1 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 2 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">2</div>
            <div class="task-title">Atrybuty width, height i title</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wstaw obrazek i ustaw jego wymiary atrybutami <code>width="300"</code> i <code>height="200"</code>. Dodaj też atrybut <code>title="Opis po najechaniu"</code> — najedź myszką żeby zobaczyć efekt. Następnie sprawdź co się dzieje gdy ustawisz tylko <code>width</code> bez <code>height</code>.</p>
            <div class="code-example">
                <h4>📄 Przykład:</h4>
                <pre>
&lt;img src="https://picsum.photos/600/400"
     alt="Krajobraz górski"
     width="300"
     height="200"
     title="Kliknij aby zobaczyć pełny rozmiar"&gt;</pre>
            </div>
            <div class="info-box">💡 Różnica między <code>width/height</code> w HTML a w CSS:<br>
            — <code>width="300"</code> w HTML → zawsze 300px, nie reaguje na CSS<br>
            — <code>width: 300px</code> w CSS → można nadpisać media query, <code>max-width</code> itp.<br>
            Dobra praktyka: wymiary ustawiaj przez CSS, nie atrybuty HTML.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 2 ↓↓↓ -->
            <div class="ex-area" id="ex2-area">

                <style>
                    /* Dodaj tu style dla obrazków z tego ćwiczenia */
                </style>

                <!-- Wstaw obrazek z: src, alt, width, height, title -->
                <!-- Potem wstaw drugi obrazek z TYLKO width (bez height) — czy proporcje się zachowają? -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 2 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 3 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">3</div>
            <div class="task-title">Ścieżki do plików — względne i bezwzględne</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> To ćwiczenie rozwiązujesz w edytorze tekstowym (nie w przeglądarce). Na podstawie poniższej struktury folderów zapisz poprawne ścieżki. Plik z rozwiązaniem załącz do paczki *.zip i prześlij do oceny. <code>src</code> dla każdego przypadku.</p>
            <div class="code-example">
                <h4>📁 Struktura projektu:</h4>
                <pre>
projekt/
├── index.html          ← piszesz kod w tym pliku
├── kontakt.html
├── logo.png
├── img/
│   ├── banner.jpg
│   └── galeria/
│       └── zdjecie1.jpg
└── podstrony/
    └── onas.html       ← i w tym pliku też</pre>
            </div>
            <div class="code-example">
                <h4>✏️ Uzupełnij ścieżki src:</h4>
                <pre>
<!-- Z pliku index.html: -->
logo.png         → &lt;img src="???" alt="Logo"&gt;
banner.jpg       → &lt;img src="???" alt="Baner"&gt;
zdjecie1.jpg     → &lt;img src="???" alt="Zdjęcie"&gt;

<!-- Z pliku podstrony/onas.html: -->
logo.png         → &lt;img src="???" alt="Logo"&gt;
banner.jpg       → &lt;img src="???" alt="Baner"&gt;
zdjecie1.jpg     → &lt;img src="???" alt="Zdjęcie"&gt;</pre>
            </div>
            <div class="info-box">💡 Zasada ścieżek względnych:<br>
            <code>./</code> lub brak prefiksu → ten sam folder<br>
            <code>nazwa_folderu/</code> → wejdź do podfolderu<br>
            <code>../</code> → cofnij się o jeden folder wyżej<br>
            <code>../../</code> → cofnij się dwa foldery wyżej</div>
            <div class="warning-box">⚠️ Na egzaminie INF.03 zdjęcia są zwykle w tym samym folderze co plik HTML.<br>
            Używaj wtedy: <code>src="nazwa_pliku.jpg"</code> — bez żadnych ukośników na początku.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ ODPOWIEDZI — Ćwiczenie 3 ↓↓↓ -->
            <div class="ex-area" id="ex3-area">

                <style>
                    #ex3-area table { border-collapse: collapse; width: 100%; }
                    #ex3-area th, #ex3-area td {
                        border: 1px solid #ddd;
                        padding: 8px 12px;
                        text-align: left;
                        font-size: 0.9em;
                    }
                    #ex3-area th { background-color: #fff5e6; color: #8b5e00; }
                </style>

                <table>
                    <tr>
                        <th>Plik HTML</th>
                        <th>Szukany obrazek</th>
                        <th>Ścieżka src (uzupełnij)</th>
                    </tr>
                    <tr>
                        <td>index.html</td>
                        <td>logo.png</td>
                        <td><code>src="..."</code></td>
                    </tr>
                    <tr>
                        <td>index.html</td>
                        <td>img/banner.jpg</td>
                        <td><code>src="..."</code></td>
                    </tr>
                    <tr>
                        <td>index.html</td>
                        <td>img/galeria/zdjecie1.jpg</td>
                        <td><code>src="..."</code></td>
                    </tr>
                    <tr>
                        <td>podstrony/onas.html</td>
                        <td>logo.png</td>
                        <td><code>src="..."</code></td>
                    </tr>
                    <tr>
                        <td>podstrony/onas.html</td>
                        <td>img/banner.jpg</td>
                        <td><code>src="..."</code></td>
                    </tr>
                    <tr>
                        <td>podstrony/onas.html</td>
                        <td>img/galeria/zdjecie1.jpg</td>
                        <td><code>src="..."</code></td>
                    </tr>
                </table>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 3 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 4 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">4</div>
            <div class="task-title">&lt;figure&gt; i &lt;figcaption&gt; — semantyczne opakowanie obrazka</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz trzy karty z obrazkami używając semantycznych tagów <code>&lt;figure&gt;</code> i <code>&lt;figcaption&gt;</code>. Każda karta ma obrazek i podpis pod nim. Ułóż karty obok siebie przez Flexbox na kontenerze.</p>
            <div class="code-example">
                <h4>📄 Struktura semantyczna:</h4>
                <pre>
&lt;figure&gt;
    &lt;img src="https://picsum.photos/id/20/300/200"
         alt="Dzika przyroda"
         width="300"&gt;
    &lt;figcaption&gt;Fot. 1 — Dzika przyroda&lt;/figcaption&gt;
&lt;/figure&gt;</pre>
            </div>
            <div class="info-box">💡 <code>&lt;figure&gt;</code> = semantyczny kontener dla treści ilustracyjnej (zdjęcie, diagram, kod)<br>
            <code>&lt;figcaption&gt;</code> = podpis do figure — może być przed lub po obrazku<br>
            Dlaczego nie samo <code>&lt;img&gt;</code>? Bo figure + figcaption daje kontekst: czytniki ekranowe ogłaszają "Rysunek: [podpis]"</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 4 ↓↓↓ -->
            <div class="ex-area" id="ex4-area">

                <style>
                    #ex4-galeria {
                        display: flex;
                        gap: 15px;
                        flex-wrap: wrap;
                    }

                    #ex4-galeria figure {
                        margin: 0;
                        /* Dodaj: border, border-radius, padding, text-align */
                    }

                    #ex4-galeria img {
                        display: block;
                        width: 100%;
                        /* Dodaj: border-radius na dole = 0, max-width */
                    }

                    #ex4-galeria figcaption {
                        /* Dodaj: padding, font-size, color, text-align */
                    }
                </style>

                <div id="ex4-galeria">
                    <!-- Wstaw 3 elementy figure z img i figcaption -->
                    <!-- Użyj picsum.photos/id/[10-99]/280/180 dla różnych zdjęć -->
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 4 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK B: STYLOWANIE OBRAZKÓW CSS
         Ćwiczenia 5–8
         ========================================== -->

    <!-- ĆWICZENIE 5 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">5</div>
            <div class="task-title">CSS: border, border-radius, box-shadow na obrazku</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wstaw cztery identyczne obrazki i ostyluj każdy inaczej przez CSS: pierwszy z ramką, drugi zaokrąglony, trzeci okrągły (<code>border-radius: 50%</code>), czwarty z cieniem (<code>box-shadow</code>). Obrazki powinny być kwadratowe (taka sama szerokość i wysokość).</p>
            <div class="code-example">
                <h4>📄 Przykłady stylów:</h4>
                <pre>
.img-ramka   { border: 4px solid #ff6b6b; }
.img-zaokr   { border-radius: 15px; }
.img-okrag   { border-radius: 50%; }
.img-cien    { box-shadow: 5px 5px 15px rgba(0,0,0,0.4); }</pre>
            </div>
            <div class="info-box">💡 Aby border-radius: 50% dało okrąg — obrazek musi być KWADRATOWY.<br>
            Ustaw width i height na tę samą wartość w CSS: <code>width: 200px; height: 200px; object-fit: cover;</code></div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 5 ↓↓↓ -->
            <div class="ex-area" id="ex5-area">

                <style>
                    #ex5-area {
                        display: flex;
                        gap: 20px;
                        flex-wrap: wrap;
                        align-items: center;
                        padding: 20px;
                    }

                    .ex5-img-base {
                        width: 160px;
                        height: 160px;
                        object-fit: cover;
                        display: block;
                    }

                    /* Dodaj style dla 4 klas: ramka, zaokrąglony, okrągły, z cieniem */
                </style>

                <!-- 4 obrazki z tymi samymi wymiarami, różnymi klasami CSS -->
                <!-- src="https://picsum.photos/id/22/300/300" — kwadratowe zdjęcie -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 5 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 6 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">6</div>
            <div class="task-title">object-fit — jak obrazek wypełnia swój obszar</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz pięć divów o stałych wymiarach (200×150px) z tym samym obrazkiem wewnątrz. Na każdym obrazku zastosuj inną wartość <code>object-fit</code> i obserwuj różnicę w wyglądzie.</p>
            <div class="code-example">
                <h4>📄 Wartości object-fit:</h4>
                <pre>
object-fit: fill;       /* rozciąga — deformuje proporcje */
object-fit: contain;    /* mieści całość — mogą być puste pasy */
object-fit: cover;      /* wypełnia całość — przycina boki */
object-fit: none;       /* oryginalny rozmiar — może wystawać */
object-fit: scale-down; /* mniejszy z: contain lub none */</pre>
            </div>
            <div class="info-box">💡 <code>object-fit: cover</code> to najczęściej stosowana wartość w praktyce —<br>
            wypełnia pojemnik nie deformując proporcji, przycina co nie pasuje.<br>
            Używaj razem z <code>object-position: center</code> żeby kontrolować który fragment jest widoczny.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 6 ↓↓↓ -->
            <div class="ex-area" id="ex6-area">

                <style>
                    #ex6-kontenery {
                        display: flex;
                        gap: 15px;
                        flex-wrap: wrap;
                    }

                    .ex6-ramka {
                        width: 200px;
                        height: 150px;
                        border: 2px solid #feca57;
                        overflow: hidden; /* przycina co wystaje poza ramkę */
                        flex-shrink: 0;
                    }

                    .ex6-ramka img {
                        width: 100%;
                        height: 100%;
                        /* Tu zmień object-fit dla każdego */
                    }

                    .ex6-ramka p {
                        text-align: center;
                        font-size: 0.8em;
                        color: #888;
                        margin-top: 4px;
                    }

                    /* Dodaj 5 klas z różnymi wartościami object-fit */
                </style>

                <div id="ex6-kontenery">
                    <!-- 5 divów .ex6-ramka, każdy z img i <p> z nazwą wartości -->
                    <!-- src="https://picsum.photos/id/30/400/300" -->
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 6 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 7 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">7</div>
            <div class="task-title">float z obrazkiem — tekst opływający zdjęcie</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz dwa bloki artykułów: w pierwszym obrazek z <code>float: left</code> (tekst opływa po prawej), w drugim obrazek z <code>float: right</code> (tekst opływa po lewej). Dodaj <code>margin</code> do obrazka żeby tekst nie przylegał do niego.</p>
            <div class="code-example">
                <h4>📄 Klasyczny wzorzec — artykuł ze zdjęciem:</h4>
                <pre>
.artykul { overflow: hidden; margin-bottom: 20px; }

.img-lewo {
    float: left;
    width: 200px;
    margin: 0 15px 10px 0; /* prawo i dół */
}

.img-prawo {
    float: right;
    width: 200px;
    margin: 0 0 10px 15px; /* lewo i dół */
}</pre>
            </div>
            <div class="info-box">💡 <code>overflow: hidden</code> na rodzicu zapobiega "zawaleniu się" kontenera<br>
            gdy obrazek z float jest wyższy niż tekst obok niego — znasz to już z Części 2b!</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 7 ↓↓↓ -->
            <div class="ex-area" id="ex7-area">

                <style>
                    /* Dodaj style dla .ex7-artykul, .ex7-img-lewo, .ex7-img-prawo */
                </style>

                <!-- ARTYKUŁ 1: obrazek po lewej, tekst po prawej -->
                <div class="ex7-artykul">
                    <img class="ex7-img-lewo"
                         src="https://picsum.photos/id/40/200/150"
                         alt="Krajobraz">
                    <h3 style="color:#333;">Artykuł — obrazek po lewej</h3>
                    <p style="color:#555;">Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                    Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                    nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in
                    reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla.</p>
                </div>

                <!-- ARTYKUŁ 2: obrazek po prawej, tekst po lewej -->
                <div class="ex7-artykul">
                    <img class="ex7-img-prawo"
                         src="https://picsum.photos/id/50/200/150"
                         alt="Architektura">
                    <h3 style="color:#333;">Artykuł — obrazek po prawej</h3>
                    <p style="color:#555;">Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                    Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
                    nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor.</p>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 7 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 8 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">8</div>
            <div class="task-title">background-image — obrazek jako tło elementu</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz trzy sekcje z tłem w postaci obrazka. Pierwsza: <code>background-size: cover</code>, druga: <code>background-size: contain</code>, trzecia: <code>background-repeat: repeat</code> (tapeta). Każda sekcja ma nałożony tekst na tle.</p>
            <div class="code-example">
                <h4>📄 Wzorzec tła z obrazkiem:</h4>
                <pre>
.hero-baner {
    background-image: url("https://picsum.photos/id/60/1000/400");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 200px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    text-shadow: 1px 1px 3px black;
}</pre>
            </div>
            <div class="warning-box">⚠️ Różnica: <code>&lt;img&gt;</code> vs <code>background-image</code><br>
            <code>&lt;img&gt;</code> → treść strony, wymaga alt, indeksowana przez wyszukiwarki<br>
            <code>background-image</code> → dekoracja, brak znaczenia semantycznego, brak alt</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 8 ↓↓↓ -->
            <div class="ex-area" id="ex8-area">

                <style>
                    .ex8-sekcja {
                        height: 180px;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        margin-bottom: 10px;
                        border-radius: 6px;
                        color: white;
                        font-size: 1.2em;
                        font-weight: bold;
                        text-shadow: 1px 1px 4px rgba(0,0,0,0.8);
                    }

                    /* Dodaj 3 klasy z różnymi background-size i background-repeat */
                    .ex8-cover    { /* background-image + size:cover */ }
                    .ex8-contain  { /* background-image + size:contain + kolor tła */ }
                    .ex8-tapeta   { /* background-image + repeat + size:100px */ }
                </style>

                <div class="ex8-sekcja ex8-cover">background-size: cover</div>
                <div class="ex8-sekcja ex8-contain">background-size: contain</div>
                <div class="ex8-sekcja ex8-tapeta">background-repeat: repeat</div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 8 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK C: RESPONSYWNE OBRAZKI
         Ćwiczenia 9–12
         ========================================== -->

    <!-- ĆWICZENIE 9 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">9</div>
            <div class="task-title">Responsywny obrazek przez CSS — max-width: 100%</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Ustaw na obrazku <code>max-width: 100%</code> i <code>height: auto</code>. Zwęź okno przeglądarki — obrazek powinien się kurczyć razem z kontenerem, nigdy nie wychodząc poza jego szerokość. To najprostsza technika responsywnego obrazka.</p>
            <div class="code-example">
                <h4>📄 Złoty wzorzec responsywnego obrazka:</h4>
                <pre>
img {
    max-width: 100%; /* nie szerszy niż rodzic */
    height: auto;    /* proporcje zachowane */
    display: block;  /* usuwa domyślny odstęp pod obrazkiem */
}</pre>
            </div>
            <div class="info-box">💡 <code>max-width: 100%</code> zamiast <code>width: 100%</code> — różnica:<br>
            <code>width: 100%</code> → obrazek zawsze rozciągnie się do 100% rodzica (nawet mały 50px obrazek)<br>
            <code>max-width: 100%</code> → obrazek nie przekroczy 100% rodzica, ale mniejszy zostanie mały</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 9 ↓↓↓ -->
            <div class="ex-area" id="ex9-area">

                <style>
                    #ex9-kontener {
                        max-width: 600px;
                        border: 2px dashed #feca57;
                        padding: 10px;
                        margin: 0 auto;
                    }

                    #ex9-kontener img {
                        /* Dodaj: max-width: 100%, height: auto, display: block */
                    }
                </style>

                <div id="ex9-kontener">
                    <img src="https://picsum.photos/id/70/800/400"
                         alt="Rozległy krajobraz">
                    <p style="color:#888; font-size:0.9em; margin-top:8px;">
                        Zwęź okno przeglądarki — obrazek powinien się dostosować.
                    </p>
                </div>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 9 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 10 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">10</div>
            <div class="task-title">srcset — różne wersje obrazka dla różnych rozdzielczości</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wstaw obrazek z atrybutem <code>srcset</code> — podaj trzy wersje o różnych szerokościach. Przeglądarka sama wybierze optymalny plik zależnie od rozdzielczości ekranu i prędkości łącza.</p>
            <div class="code-example">
                <h4>📄 srcset z podaniem szerokości pliku (descriptor w):</h4>
                <pre>
&lt;img
    src="https://picsum.photos/id/80/800/500"
    srcset="https://picsum.photos/id/80/400/250  400w,
            https://picsum.photos/id/80/800/500  800w,
            https://picsum.photos/id/80/1200/750 1200w"
    sizes="(max-width: 600px)  400px,
           (max-width: 1000px) 800px,
           1200px"
    alt="Wersja dopasowana do ekranu"&gt;</pre>
            </div>
            <div class="info-box">💡 <code>srcset</code> = "mam te pliki, o tych szerokościach"<br>
            <code>sizes</code> = "przy tej szerokości okna, obrazek będzie zajmował tyle miejsca"<br>
            Przeglądarka sama wybiera najlepszy plik — nie pobiera niepotrzebnie dużych plików na małym ekranie.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 10 ↓↓↓ -->
            <div class="ex-area" id="ex10-area">

                <style>
                    #ex10-area img {
                        max-width: 100%;
                        height: auto;
                        display: block;
                    }
                </style>

                <!-- Wstaw img z src, srcset (3 rozmiary) i sizes -->
                <!-- Otwórz DevTools → Network → Img żeby zobaczyć który plik przeglądarka wybrała -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 10 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 11 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">11</div>
            <div class="task-title">&lt;picture&gt; — różne zdjęcia dla różnych ekranów</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Użyj tagu <code>&lt;picture&gt;</code> żeby na wąskim ekranie (do 600px) pokazać zbliżenie twarzy, a na szerokim — panoramę. Zmień szerokość okna przeglądarki żeby zobaczyć jak zmienia się obrazek.</p>
            <div class="code-example">
                <h4>📄 Wzorzec — różne zdjęcia dla różnych ekranów:</h4>
                <pre>
&lt;picture&gt;
    &lt;!-- Na małym ekranie (do 600px): --&gt;
    &lt;source
        media="(max-width: 600px)"
        srcset="https://picsum.photos/id/90/400/400"&gt;

    &lt;!-- Na średnim ekranie (601–1000px): --&gt;
    &lt;source
        media="(max-width: 1000px)"
        srcset="https://picsum.photos/id/90/700/350"&gt;

    &lt;!-- Domyślny (duży ekran lub brak dopasowania): --&gt;
    &lt;img src="https://picsum.photos/id/90/1200/400"
         alt="Adaptacyjny obrazek"&gt;
&lt;/picture&gt;</pre>
            </div>
            <div class="info-box">💡 srcset = ta sama fotografia w różnych rozmiarach (art direction: nie)<br>
            &lt;picture&gt; = zupełnie inne ujęcia dla różnych ekranów (art direction: tak)<br>
            Przykład: panorama miasta na desktopie, zbliżenie centrum na telefonie.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 11 ↓↓↓ -->
            <div class="ex-area" id="ex11-area">

                <style>
                    #ex11-area picture img {
                        max-width: 100%;
                        height: auto;
                        display: block;
                        border-radius: 6px;
                    }
                </style>

                <!-- Wstaw tu <picture> z 2 source i fallback img -->
                <!-- Użyj różnych ID z picsum.photos dla różnych ujęć -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 11 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 12 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">12</div>
            <div class="task-title">Galeria — połączenie figure, figcaption i Flexbox</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz responsywną galerię 6 zdjęć używając <code>&lt;figure&gt;</code>, <code>&lt;figcaption&gt;</code> i Flexbox z <code>flex-wrap: wrap</code>. Każde zdjęcie ma opis pod spodem. Zdjęcia powinny układać się w rzędy i zawijać gdy brakuje miejsca. Użyj <code>object-fit: cover</code> żeby wszystkie zdjęcia miały jednakową wysokość.</p>
            <div class="code-example">
                <h4>📄 Struktura galerii:</h4>
                <pre>
&lt;section class="galeria"&gt;
    &lt;figure class="galeria-karta"&gt;
        &lt;img src="..." alt="Opis"&gt;
        &lt;figcaption&gt;Podpis zdjęcia&lt;/figcaption&gt;
    &lt;/figure&gt;
    &lt;!-- ... 5 kolejnych figure ... --&gt;
&lt;/section&gt;

.galeria       { display: flex; flex-wrap: wrap; gap: 12px; }
.galeria-karta { flex: 1; min-width: 200px; }
.galeria-karta img { width: 100%; height: 150px; object-fit: cover; }</pre>
            </div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 12 ↓↓↓ -->
            <div class="ex-area" id="ex12-area">

                <style>
                    /* Dodaj style dla .ex12-galeria i .ex12-karta */
                </style>

                <section class="ex12-galeria">
                    <!-- 6 elementów figure.ex12-karta z img i figcaption -->
                    <!-- picsum.photos/id/[10,20,30,40,50,60]/400/300 -->
                </section>

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 12 ↑↑↑ -->
        </div>
    </div>

    <!-- ==========================================
         BLOK D: AUDIO I VIDEO
         Ćwiczenia 13–16
         ========================================== -->

    <!-- ĆWICZENIE 13 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">13</div>
            <div class="task-title">Tag &lt;audio&gt; — odtwarzacz dźwięku</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wstaw odtwarzacz audio z atrybutem <code>controls</code>. Dodaj dwa elementy <code>&lt;source&gt;</code> — jeden dla formatu MP3, drugi dla OGG (fallback dla starszych przeglądarek). Następnie stwórz drugi odtwarzacz z atrybutami <code>loop</code> i <code>muted</code>.</p>
            <div class="code-example">
                <h4>📄 Tag audio z fallback:</h4>
                <pre>
&lt;audio controls&gt;
    &lt;source src="muzyka.mp3" type="audio/mpeg"&gt;
    &lt;source src="muzyka.ogg" type="audio/ogg"&gt;
    &lt;p&gt;Twoja przeglądarka nie obsługuje odtwarzacza audio.
       &lt;a href="muzyka.mp3"&gt;Pobierz plik&lt;/a&gt;&lt;/p&gt;
&lt;/audio&gt;</pre>
            </div>
            <div class="info-box">💡 Dlaczego dwa formaty? Stare przeglądarki obsługiwały różne formaty.<br>
            Dziś MP3 działa wszędzie — ale OGG jako fallback to dobra praktyka.<br>
            Kolejność source ma znaczenie — przeglądarka bierze PIERWSZY który obsługuje.</div>
            <div class="warning-box">⚠️ W ćwiczeniu nie masz pliku audio — kod będzie poprawny, ale odtwarzacz pokaże "Błąd źródła".<br>
            Na egzaminie INF.03 plik audio jest dostarczony w archiwum ZIP razem z zadaniem.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 13 ↓↓↓ -->
            <div class="ex-area" id="ex13-area">

                <style>
                    #ex13-area audio {
                        display: block;
                        margin-bottom: 15px;
                        width: 100%;
                    }
                    #ex13-area p {
                        color: #555;
                        font-size: 0.9em;
                        margin-bottom: 8px;
                    }
                </style>

                <p>Odtwarzacz 1 — z kontrolkami:</p>
                <!-- audio z controls i dwoma source (mp3 + ogg) -->

                <p>Odtwarzacz 2 — z pętlą i wyciszeniem:</p>
                <!-- audio z controls + loop + muted -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 13 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 14 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">14</div>
            <div class="task-title">Tag &lt;video&gt; — odtwarzacz wideo</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Wstaw odtwarzacz wideo z <code>controls</code>, ustaw mu <code>width</code> i <code>height</code>, dodaj atrybut <code>poster</code> (obrazek wyświetlany przed odtworzeniem) i dwa formaty przez <code>&lt;source&gt;</code>: MP4 i WebM. Użyj picsum.photos jako poster.</p>
            <div class="code-example">
                <h4>📄 Pełna składnia video:</h4>
                <pre>
&lt;video
    width="640"
    height="360"
    controls
    poster="https://picsum.photos/id/100/640/360"&gt;

    &lt;source src="film.mp4"  type="video/mp4"&gt;
    &lt;source src="film.webm" type="video/webm"&gt;

    &lt;p&gt;Przeglądarka nie obsługuje video.
       &lt;a href="film.mp4"&gt;Pobierz film&lt;/a&gt;&lt;/p&gt;
&lt;/video&gt;</pre>
            </div>
            <div class="info-box">💡 <code>poster</code> = miniaturka wyświetlana przed kliknięciem "play".<br>
            Bez poster — widać pierwszą klatkę wideo (lub czarny ekran).<br>
            Dobra praktyka: zawsze podawaj poster — strona wygląda lepiej przed załadowaniem.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 14 ↓↓↓ -->
            <div class="ex-area" id="ex14-area">

                <style>
                    #ex14-area video {
                        display: block;
                        max-width: 100%;
                        border-radius: 8px;
                        box-shadow: 0 4px 12px rgba(0,0,0,0.2);
                    }
                </style>

                <!-- video z: width, height, controls, poster i dwoma source (mp4 + webm) -->

            </div>
            <!-- ↑↑↑ KONIEC — Ćwiczenie 14 ↑↑↑ -->
        </div>
    </div>

    <!-- ĆWICZENIE 15 -->
    <div class="task">
        <div class="task-header">
            <div class="task-number">15</div>
            <div class="task-title">Atrybuty video — autoplay, loop, muted, preload</div>
            <div class="difficulty">Trudność: <span class="difficulty-star">⭐⭐</span></div>
        </div>
        <div class="task-content">
            <p><strong>Polecenie:</strong> Stwórz dwa odtwarzacze video — pierwszy "zwykły" z kontrolkami, drugi skonfigurowany jako <strong>wideo w tle</strong> (autoplay + loop + muted — tak jak na stronach firmowych). Tabela poniżej przypomina co robi każdy atrybut.</p>
            <div class="code-example">
                <h4>📋 Atrybuty video:</h4>
                <pre>
controls    → pokazuje pasek odtwarzacza
autoplay    → automatyczne odtwarzanie po załadowaniu
loop        → powtarza od początku po zakończeniu
muted       → wyciszony dźwięk (WYMAGANY gdy autoplay!)
preload     → "none" | "metadata" | "auto"
             none     = nie pobieraj zanim nie kliknę play
             metadata = pobierz tylko info (czas trwania, rozmiar)
             auto     = pobierz cały plik z góry (domyślne)</pre>
            </div>
            <div class="warning-box">⚠️ Przeglądarki blokują <code>autoplay</code> bez <code>muted</code>.<br>
            Jeśli chcesz autoplay — musisz dodać też <code>muted</code>. To celowa decyzja przeglądarek — strony nie mogą "hałasować" bez zgody użytkownika.</div>
            <!-- ↓↓↓ TUTAJ WPISUJESZ KOD — Ćwiczenie 15 ↓↓↓ -->
            <div class="ex-area" id="ex15-area">

                <style>
                    #ex15-area > div { margin-bottom: 20px; }
                    #ex15-area p { color: #555; font-size: 0.9em; margin-bottom: 8px; }
                    #ex15-area video { max-width: 100%; display: block; }
                </style>

                <div>
                    <p><strong>Odtwarzacz 1</strong> — normalny z kontrolkami:</p>
                    <!-- video z controls, poster, source mp4 -->
                </div>

                <div>
                    <p><strong>Odtwarzacz 2</strong> — wideo w tle (autoplay + loop + muted):</p>
                    <!-- video z autoplay + loop + muted + source mp4, BEZ controls -->
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
            <p><strong>Polecenie:</strong> W nowym pliku <code>galeria_multimediow.html</code> z osobnym <code>styl.css</code> wykonaj stronę galerii multimedialnej szkoły według specyfikacji.</p>

            <div class="code-example">
                <h4>📐 Diagram układu:</h4>
                <pre>
┌─────────────────────────────────────────────────────┐
│  &lt;header&gt; — logo szkoły + nawigacja (Flexbox)       │
│  tło: rgb(220, 80, 60)   tekst: biały                │
├─────────────────────────────────────────────────────┤
│  &lt;section id="hero"&gt; — tło background-image         │
│  height: 300px, background-size: cover               │
│  tekst wyśrodkowany (Flexbox, position:relative)     │
│  nakładka rgba(0,0,0,0.5)                            │
├─────────────────────────────────────────────────────┤
│  &lt;section id="galeria"&gt; — siatka 6 zdjęć            │
│  display:flex, flex-wrap:wrap, gap:15px              │
│  każde zdjęcie: figure + img + figcaption            │
│  object-fit:cover, height:200px                      │
├─────────────────────────────────────────────────────┤
│  &lt;section id="multimedia"&gt;                          │
│  │  &lt;article&gt; z odtwarzaczem audio                 │
│  │  &lt;article&gt; z odtwarzaczem video + poster        │
│  display:flex, gap:30px                              │
├─────────────────────────────────────────────────────┤
│  &lt;footer&gt; — tło rgb(220,80,60), wyśrodkowany        │
└─────────────────────────────────────────────────────┘</pre>
            </div>

            <div style="background: #fff5e6; border: 2px solid #feca57; border-radius: 8px; padding: 20px; margin: 10px 0;">
                <h3 style="color: #8b5e00; margin-bottom: 14px;">📋 Specyfikacja:</h3>

                <p style="color:#8b5e00; font-weight:bold; margin-bottom:8px;">Header:</p>
                <ul style="margin-left:20px; color:#555; line-height:2.0; margin-bottom:12px;">
                    <li><code>display:flex</code>, <code>justify-content:space-between</code>, <code>align-items:center</code></li>
                    <li>Kolor tła: <code>rgb(220, 80, 60)</code>, padding: 15px 30px</li>
                    <li>Logo: <code>&lt;h1&gt;</code> z tekstem szkoły, kolor biały</li>
                    <li>Nav: 3 linki <code>&lt;a href="#"&gt;</code>, kolor biały, bez podkreślenia, gap: 20px</li>
                </ul>

                <p style="color:#8b5e00; font-weight:bold; margin-bottom:8px;">Sekcja hero (tło z obrazka):</p>
                <ul style="margin-left:20px; color:#555; line-height:2.0; margin-bottom:12px;">
                    <li><code>background-image</code> z dowolnym URL picsum.photos, <code>background-size:cover</code>, <code>background-position:center</code></li>
                    <li>Wysokość: 300px, <code>position:relative</code></li>
                    <li>Nakładka: <code>position:absolute</code>, 100%×100%, <code>background:rgba(0,0,0,0.5)</code>, z-index:1</li>
                    <li>Treść: <code>position:absolute</code>, wyśrodkowana (top:50%, left:50%, transform), z-index:2, kolor biały</li>
                    <li>W treści: <code>&lt;h2&gt;</code> + <code>&lt;p&gt;</code></li>
                </ul>

                <p style="color:#8b5e00; font-weight:bold; margin-bottom:8px;">Galeria 6 zdjęć:</p>
                <ul style="margin-left:20px; color:#555; line-height:2.0; margin-bottom:12px;">
                    <li>Kontener: <code>display:flex</code>, <code>flex-wrap:wrap</code>, <code>gap:15px</code>, padding: 30px</li>
                    <li>6 elementów <code>&lt;figure&gt;</code> z klasą <code>.karta-galerii</code>: <code>flex:1</code>, <code>min-width:250px</code></li>
                    <li>Obrazki: <code>width:100%</code>, <code>height:200px</code>, <code>object-fit:cover</code>, <code>display:block</code></li>
                    <li><code>&lt;figcaption&gt;</code>: padding: 8px, background: <code>rgb(245,245,245)</code>, font-size: 0.9em</li>
                </ul>

                <p style="color:#8b5e00; font-weight:bold; margin-bottom:8px;">Sekcja multimedia:</p>
                <ul style="margin-left:20px; color:#555; line-height:2.0; margin-bottom:12px;">
                    <li>Kontener: <code>display:flex</code>, <code>gap:30px</code>, padding: 30px, <code>flex-wrap:wrap</code></li>
                    <li>Dwa <code>&lt;article&gt;</code>: <code>flex:1</code>, <code>min-width:280px</code>, border: 1px solid rgb(220,80,60), border-radius:8px, padding:20px</li>
                    <li>Pierwszy article: tytuł <code>&lt;h3&gt;</code> + <code>&lt;audio controls&gt;</code> z dwoma source (mp3 + ogg)</li>
                    <li>Drugi article: tytuł <code>&lt;h3&gt;</code> + <code>&lt;video controls width="100%"&gt;</code> z poster i dwoma source (mp4 + webm)</li>
                </ul>

                <p style="color:#8b5e00; font-weight:bold; margin-bottom:8px;">Footer:</p>
                <ul style="margin-left:20px; color:#555; line-height:2.0;">
                    <li>Kolor tła: <code>rgb(220, 80, 60)</code>, kolor tekstu: biały, padding: 20px</li>
                    <li><code>display:flex</code>, <code>justify-content:center</code></li>
                    <li>Tekst: „© 2025 Technikum Informatyczne" + Twój PESEL pogrubionym</li>
                </ul>
            </div>

            <div class="warning-box">⚠️ CSS w osobnym pliku <code>styl.css</code> dołączonym przez <code>&lt;link&gt;</code>!<br>
            Pliki audio i video nie istnieją — wpisz przykładowe nazwy (np. muzyka.mp3).<br>
            Odtwarzacze pojawią się poprawnie — tylko nie będą miały czego odtwarzać.</div>
            <div class="info-box">💡 Sprawdź stronę walidatorem W3C — czy wszystkie img mają alt? Czy video ma fallback?<br>
            To ćwiczenie łączy multimedia z Flexboxem i pozycjonowaniem z poprzednich części.</div>
        </div>
    </div>

    <footer class="page-footer">
        <p>HTML5 i CSS — Część 5A | Multimedia | INF.03</p>
        <p style="margin-top:10px; font-size:0.9em;">
            🖼️ img + alt | 📁 ścieżki | 🎨 object-fit | 🔊 audio | 🎬 video
        </p>
    </footer>

</div>
</body>
</html>
```

---

## 📋 LISTA ĆWICZEŃ

### Blok A — Podstawy `<img>` (ćwiczenia 1–4)
| Nr | Temat | Właściwości / tagi |
|----|-------|--------------------|
| 1 | src, alt — obowiązkowe atrybuty | `<img src alt>` |
| 2 | width, height, title | atrybuty HTML vs CSS |
| 3 | Ścieżki względne i bezwzględne | `./` `../` URL |
| 4 | `<figure>` i `<figcaption>` | semantyczne opakowanie |

### Blok B — Stylowanie obrazków CSS (ćwiczenia 5–8)
| Nr | Temat | Właściwości CSS |
|----|-------|-----------------|
| 5 | border, border-radius, box-shadow | okrągłe i z cieniem |
| 6 | object-fit — 5 wartości | fill / contain / cover / none / scale-down |
| 7 | float z obrazkiem | tekst opływający zdjęcie |
| 8 | background-image | cover / contain / repeat |

### Blok C — Responsywne obrazki (ćwiczenia 9–12)
| Nr | Temat | Technika |
|----|-------|----------|
| 9 | max-width: 100% | najprostsza responsywność |
| 10 | srcset + sizes | różne rozmiary tego samego zdjęcia |
| 11 | `<picture>` + `<source>` | różne ujęcia dla różnych ekranów |
| 12 | Galeria — figure + Flexbox | połączenie technik |

### Blok D — Audio i Video (ćwiczenia 13–16)
| Nr | Temat | Tagi / atrybuty |
|----|-------|-----------------|
| 13 | `<audio>` z kontrolkami | controls, source, loop, muted |
| 14 | `<video>` z posterem | controls, poster, source mp4/webm |
| 15 | Atrybuty video | autoplay, loop, muted, preload |
| 16 | 🏆 Galeria multimedialna | styl.css + wszystkie techniki |


Miejsce na wysłanie prac
Klasa 3 TIe JS - [https://www.dropbox.com/request/Bj0IUNLjMbAtwGpIJw06]
