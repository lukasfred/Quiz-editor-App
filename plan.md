# Plan Implementacji - Quiz Question Editor

## 📋 Informacje ogólne

**Aplikacja:** Quiz Question Editor (HTML/JS)
**Wersja docelowa:** 1.0
**Data rozpoczęcia:** 2026-01-30
**Autor:** OpenCode AI

## 🎯 Cel

Stworzenie jednoplikowej aplikacji HTML do tworzenia i edycji plików pytań JSON, w 100% zgodnej z aplikacją Android v2.11.2+.

## 📊 Struktura folderu

```
/home/lukas/opencode/quizadfr/question_app/
├── quiz_editor.html      # Główna aplikacja HTML
├── plan.md              # Ten plik - plan implementacji
├── changelog.md         # Historia zmian
└── README.md            # Dokumentacja użytkownika (do stworzenia)
```

## 🔄 Numeracja wersji

Wersje są oznaczane na podstawie procentu zrealizowanego planu:

| % planu | Wersja | Opis                    |
|----------|---------|-------------------------|
| 10%      | 0.1     | Podstawowa struktura HTML/CSS |
| 20%      | 0.2     | Modele danych           |
| 30%      | 0.3     | Lista pytań           |
| 40%      | 0.4     | Filtrowanie i wyszukiwanie |
| 50%      | 0.5     | Edytor pytań (basic) |
| 60%      | 0.6     | Edytor pytań (all types) |
| 70%      | 0.7     | Obsługa obrazów       |
| 80%      | 0.8     | Import/Export          |
| 90%      | 0.9     | Testowanie i poprawki |
| 100%     | 1.0     | Wersja produkcyjna    |

## 📝 Plan implementacji (kroki)

### Krok 1: Struktura HTML i CSS (v0.1 - 10%)
**Cel:** Podstawowa struktura aplikacji z Material Design

**Zadania:**
- [ ] Szablon HTML5 z odpowiednimi meta tagami
- [ ] Style CSS Material Design
- [ ] Główny kontener aplikacji
- [ ] Nawigacja (sidebar/header)
- [ ] Podstawowe komponenty UI (buttony, inputy, karty)

**Technologie:**
- HTML5
- CSS3 (Flexbox, Grid, Variables)
- Material Design colors

**Pliki:** `quiz_editor.html`

---

### Krok 2: Modele danych (v0.2 - 20%)
**Cel:** Klasa Question z pełną walidacją

**Zadania:**
- [ ] Klasa Question (konstruktor, metody)
- [ ] Metoda toJson() (export)
- [ ] Metoda fromJson() (import)
- [ ] Walidacja (isValid getter)
- [ ] Konwersja indeksów (0-based ↔ 1-based)
- [ ] Klasa PairItem (dla pairing)
- [ ] Helper functions (generowanie ID, base64)

**Specyfikacja modelu Question:**
```javascript
{
  id: string,           // Unikalny ID
  type: string,         // 'single'|'multiple'|'ordering'|'pairing'
  text: string,        // Treść pytania (HTML dozwolony)
  explanation: string?, // Opcjonalne wyjaśnienie
  options: string[],   // Opcje odpowiedzi
  correct: number[],   // 1-based indeksy
  pairs: PairItem[],   // Tylko dla pairing
  category: string,    // Nazwa kategorii
  tags: string[],      // Tablica tagów
  imageData: string?,   // Base64 data URI
  difficulty: number?,  // 1-5
  markedForReview: boolean // Bookmark
}
```

**Pliki:** `quiz_editor.html`

---

### Krok 3: Lista pytań (v0.3 - 30%)
**Cel:** Wyświetlanie listy wszystkich pytań

**Zadania:**
- [ ] Lista pytań z kartami
- [ ] Typ pytania (ikona/emoji)
- [ ] Kategoria i tagi
- [ ] Trudność (gwiazdki)
- [ ] Paginacja (50 pytań na stronę)
- [ ] Licznik pytań
- [ ] Pusty stan (brak pytań)

**UI:**
- Grid lub lista kart
- Miniatura obrazu (jeśli istnieje)
- Przyciski akcji (Edit, Delete, Copy)

**Pliki:** `quiz_editor.html`

---

### Krok 4: Filtrowanie i wyszukiwanie (v0.4 - 40%)
**Cel:** Zaawansowane filtrowanie pytań

**Zadania:**
- [ ] Wyszukiwanie po tekście (full text search)
- [ ] Filtrowanie po typie (single/multiple/ordering/pairing)
- [ ] Filtrowanie po kategorii
- [ ] Filtrowanie po tagach (multi-select)
- [ ] Resetowanie filtrów
- [ ] Dynamiczne tagi z pytań
- [ ] Licznik wyników

**UI:**
- Search bar z ikoną
- Dropdown dla typu
- Autocomplete dla kategorii
- Tag chips dla tagów

**Pliki:** `quiz_editor.html`

---

### Krok 5: Edytor pytań - basic (v0.5 - 50%)
**Cel:** Formularz tworzenia/edycji pytań

**Zadania:**
- [ ] Modal formularza
- [ ] Pola: text, category, tags, explanation, difficulty
- [ ] Dynamiczne typy pytań (dropdown)
- [ ] Walidacja w czasie rzeczywistym
- [ ] Zapisywanie (Create/Update)
- [ ] Anulowanie
- [ ] Przycisk "Save & New"

**Walidacja:**
- Text nie może być pusty
- Category nie może być pusta
- Min. 2 opcje dla single/multiple/ordering
- Min. 1 poprawna odpowiedź
- Min. 1 para dla pairing

**Pliki:** `quiz_editor.html`

---

### Krok 6: Edytor pytań - wszystkie typy (v0.6 - 60%)
**Cel:** Pełne wsparcie dla wszystkich typów pytań

**Zadania:**
- [ ] Single choice (Radio buttons dla odpowiedzi)
- [ ] Multiple choice (Checkboxes dla odpowiedzi)
- [ ] Ordering (drag & drop / przyciski up/down)
- [ ] Pairing (pary left-right z dodawaniem/usuwaniem)
- [ ] Podgląd na żywo dla każdego typu
- [ ] Dynamiczne dodawanie opcji/par
- [ ] Usuwanie opcji/par
- [ ] Auto-zaznaczanie poprawnych odpowiedzi

**UI dla typów:**

**Single/Multiple:**
- Lista opcji z checkbox/radio
- Przycisk "Add Option"
- Przycisk "Remove" przy każdej opcji

**Ordering:**
- Lista opcji z przyciskami up/down
- Drag & drop (opcjonalnie)
- Przycisk "Add Option"

**Pairing:**
- Dwie kolumny: left | right
- Przycisk "Add Pair"
- Przycisk "Remove" przy każdej parze
- Walidacja (left i right nie puste)

**Pliki:** `quiz_editor.html`

---

### Krok 7: Obsługa obrazów (v0.7 - 70%)
**Cel:** Dodawanie obrazów do pytań

**Zadania:**
- [ ] Upload przycisk (file input)
- [ ] Konwersja do base64 (FileReader)
- [ ] Podgląd obrazu
- [ ] Usuwanie obrazu
- [ ] Optymalizacja rozmiaru (max 1024x1024px)
- [ ] Walidacja rozmiaru (max 1MB)
- [ ] Walidacja formatu (JPG, PNG, GIF)
- [ ] Kompresja jakości (85%)

**UI:**
- Sekcja "Image" w formularzu
- Przycisk "Upload Image"
- Podgląd z przyciskiem "Remove"
- Informacja o rozmiarze
- Błędy walidacji

**Technologie:**
- FileReader API
- Canvas (do resize)
- data URI format

**Pliki:** `quiz_editor.html`

---

### Krok 8: Import/Export (v0.8 - 80%)
**Cel:** Pełna kompatybilność z Androidem

**Zadania:**
- [ ] Import JSON (file input)
- [ ] Walidacja formatu JSON
- [ ] Walidacja kompatybilności (version check)
- [ ] Merge lub Replace All
- [ ] Export JSON (download)
- [ ] Format v2.11.0 (meta-data)
- [ ] Kompatybilność wsteczna (starsze formaty)
- [ ] Export do schowka (clipboard)
- [ ] Import ze schowka

**Format export:**
```javascript
{
  "version": "2.11.0",
  "exportDate": "2026-01-30T...",
  "category": "all",
  "totalQuestions": N,
  "questions": [...]
}
```

**Kompatybilność wsteczna:**
- v1.0 (prosty format)
- v2.0 (z meta-data)
- v2.11.0 (aktualny format)

**UI:**
- Przyciski "Import" i "Export"
- Dialog dla wyboru (Replace/Merge)
- Komunikaty sukcesu/błędu

**Pliki:** `quiz_editor.html`

---

### Krok 9: Testowanie i poprawki (v0.9 - 90%)
**Cel:** Stabilna wersja aplikacji

**Zadania:**
- [ ] Testowanie wszystkich typów pytań
- [ ] Testowanie walidacji
- [ ] Testowanie importu/eksportu
- [ ] Testowanie obrazów
- [ ] Testowanie responsywności (mobile/desktop)
- [ ] Testowanie przeglądarek (Chrome, Firefox, Edge)
- [ ] Poprawki błędów
- [ ] Optymalizacja wydajności
- [ ] Dodanie pomocniczych komunikatów

**Scenariusze testowe:**
1. Utworzenie pytania single/multiple/ordering/pairing
2. Edycja istniejącego pytania
3. Usunięcie pytania
4. Dodanie obrazu
5. Usunięcie obrazu
6. Export do pliku
7. Import z pliku (merge)
8. Import z pliku (replace)
9. Filtrowanie po typie
10. Wyszukiwanie tekstu
11. Filtrowanie po kategorii
12. Filtrowanie po tagach

**Pliki:** `quiz_editor.html`

---

### Krok 10: Wersja produkcyjna (v1.0 - 100%)
**Cel:** Gotowa do użycia aplikacja

**Zadania:**
- [ ] Finalne testy
- [ ] Dokumentacja użytkownika (README.md)
- [ ] Instrukcja użycia
- [ ] Zrzuty ekranu (opcjonalnie)
- [ ] Przykładowe dane (sample_questions.json)
- [ ] Wersja 1.0 oznaczona w UI
- [ ] Changelog zakończony

**Dokumentacja:**
- Jak tworzyć pytania
- Jak edytować pytania
- Jak importować/eksportować
- Format pytań
- Wymagania przeglądarki

**Pliki:**
- `quiz_editor.html`
- `README.md`
- `sample_questions.json`

---

## 🎨 Szczegóły UI/UX

### Kolorystyka (Material Design):
- Primary: `#673AB7` (deepPurple)
- Primary Dark: `#320B86`
- Secondary: `#FF9800` (orange)
- Background: `#F5F5F5`
- Surface: `#FFFFFF`
- Error: `#F44336`
- Success: `#4CAF50`
- Warning: `#FF9800`

### Layout:
- Sidebar z nawigacją (desktop) / Bottom nav (mobile)
- Główny panel z treścią
- Modal formularza (overlay)
- Toast notifications

### Responsywność:
- Desktop (> 768px): Sidebar + main content
- Tablet (768px - 1024px): Collapsible sidebar
- Mobile (< 768px): Bottom navigation + stacked content

---

## 🔧 Wymagania przeglądarki

### Minimalne:
- Chrome 90+
- Firefox 88+
- Edge 90+
- Safari 14+

### Wymagane API:
- ES6+ (Arrow functions, Classes, Template literals)
- FileReader
- Canvas
- Fetch API
- LocalStorage
- Clipboard API

---

## 📝 Zmiany w planie

Wszystkie zmiany w planie będą odnotowane w `changelog.md`.

---

**Data utworzenia:** 2026-01-30
**Ostatnia aktualizacja:** 2026-01-30
**Status:** Rozpoczęty
