# HTML5 - Moduł 6: Multimedia (Obrazy, Audio, Video)

## Wprowadzenie

Multimedia to najciekawsza część nowoczesnych stron. W tym module nauczysz się osadzać obrazy, audio, video i tworzyć responsywne multimedia[1][2].

**Czego się nauczysz w tym module:**
- ✅ Tag `<img>` i atrybuty
- ✅ Formaty obrazów
- ✅ Responsywne obrazy
- ✅ SVG wektory
- ✅ Audio (`<audio>`)
- ✅ Video (`<video>`)
- ✅ Canvas
- ✅ Best practices

---

## Część 1: Obrazy

### Podstawowa Składnia

```html
<img src="obraz.jpg" alt="Opis obrazu">
```

- `src` - ścieżka do pliku
- `alt` - alternatywny tekst (dla niewidomych, gdy obraz się nie załaduje)

### Atrybuty

```html
<img src="obraz.jpg" 
     alt="Moje zdjęcie" 
     width="300" 
     height="200"
     title="Najedź myszką">
```

### Ścieżki Obrazów

```html
<!-- Pliki w tym samym folderze -->
<img src="logo.png" alt="Logo">

<!-- W podfolderze -->
<img src="images/logo.png" alt="Logo">

<!-- Z folderu wyżej -->
<img src="../images/logo.png" alt="Logo">

<!-- URL bezwzględny -->
<img src="https://example.com/logo.png" alt="Logo">
```

---

## Część 2: Responsywne Obrazy

### Srcset - Różne Rozmiary

```html
<img src="photo-small.jpg" 
     srcset="photo-small.jpg 480w,
             photo-medium.jpg 800w,
             photo-large.jpg 1200w"
     sizes="(max-width: 600px) 100vw,
            (max-width: 1200px) 50vw,
            33vw"
     alt="Zdjęcie">
```

### Picture Element

```html
<picture>
    <source media="(max-width: 600px)" srcset="small.jpg">
    <source media="(max-width: 1200px)" srcset="medium.jpg">
    <source media="(min-width: 1201px)" srcset="large.jpg">
    <img src="default.jpg" alt="Fallback">
</picture>
```

---

## Część 3: Figure i Figcaption

```html
<figure>
    <img src="diagram.jpg" alt="Diagram architektury">
    <figcaption>Rysunek 1: Architektura systemu</figcaption>
</figure>
```

---

## Część 4: Audio

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.wav" type="audio/wav">
    Przeglądarka nie wspiera audio
</audio>
```

### Atrybuty

```html
<audio controls autoplay loop muted>
    <source src="audio.mp3" type="audio/mpeg">
</audio>
```

- `controls` - pokaż przyciski kontrolne
- `autoplay` - graj automatycznie
- `loop` - powtarzaj
- `muted` - na start wyciszony

---

## Część 5: Video

```html
<video controls width="640" height="480">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    Przeglądarka nie wspiera video
</video>
```

### Atrybuty

```html
<video controls autoplay loop muted poster="poster.jpg">
    <source src="video.mp4" type="video/mp4">
</video>
```

- `poster` - obrazek do wyświetlenia przed graniem

---

## Część 6: SVG

```html
<!-- Inline SVG -->
<svg width="200" height="200">
    <circle cx="100" cy="100" r="80" fill="red" />
    <rect x="50" y="50" width="100" height="100" fill="blue" />
</svg>

<!-- SVG jako plik -->
<img src="graphic.svg" alt="Grafika wektorowa">
```

---

## Część 7: Canvas

```html
<canvas id="myCanvas" width="200" height="200"></canvas>

<script>
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');
ctx.fillStyle = 'red';
ctx.fillRect(10, 10, 100, 100);
</script>
```

---

## Część 8: Praktyczne Przykłady

### Galeria Zdjęć

```html
<section>
    <h2>Nasza Galeria</h2>
    <div class="gallery">
        <figure>
            <img src="photo1.jpg" alt="Zdjęcie 1">
            <figcaption>Zdjęcie 1 - Krajobraz</figcaption>
        </figure>
        <figure>
            <img src="photo2.jpg" alt="Zdjęcie 2">
            <figcaption>Zdjęcie 2 - Morze</figcaption>
        </figure>
    </div>
</section>
```

### Video Player

```html
<section>
    <h2>Nasz Film</h2>
    <video controls width="100%">
        <source src="movie.mp4" type="video/mp4">
    </video>
    <p>Film o naszej firmie</p>
</section>
```

### Audio Playlist

```html
<section>
    <h2>Piosenki</h2>
    <audio controls>
        <source src="song1.mp3" type="audio/mpeg">
    </audio>
    <p>Piosenka 1</p>
    
    <audio controls>
        <source src="song2.mp3" type="audio/mpeg">
    </audio>
    <p>Piosenka 2</p>
</section>
```

---

## Część 9: Ćwiczenia

### Ćwiczenie 1: Galeria

Stwórz galerię co najmniej 6 zdjęć z:
- Figure i figcaption
- Alt tagi na wszystkich
- Responsive rozmiary

### Ćwiczenie 2: Video

Osadź video z:
- Controls
- Poster
- Alternatywne źródła

### Ćwiczenie 3: Audio

Stwórz playlistę audio z minimum 3 piosenkami.

### Ćwiczenie 4: Responsywne

Utwórz responsywne multimedia:
- Picture element dla obrazów
- Srcset dla różnych rozmiarów

---

## Best Practices

✅ Zawsze używaj `alt` tagów  
✅ Optymalizuj rozmiary obrazów  
✅ Używaj odpowiednich formatów (JPEG dla zdjęć, PNG dla grafiki)  
✅ Responsywne obrazy zawsze  
✅ Figure + figcaption dla obrazów z opisem  
✅ Waliduj HTML  

---

*Gotowy do Modułu 7? Nauczymy się Tabel! 🚀*