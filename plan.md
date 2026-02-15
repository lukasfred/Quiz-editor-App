# Plan Implementacji - Quiz Question Editor

## 📋 Informacje ogólne

**Aplikacja:** Quiz Question Editor (HTML/JS)
**Wersja docelowa:** 1.0
**Wersja aktualna:** 0.8.0
**Data rozpoczęcia:** 2026-01-30
**Data aktualizacji:** 2026-02-15
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
| 50%      | 0.5     | Edytor pytań (basic + wszystkie typy) |
| 60%      | 0.6     | Obsługa obrazów       |
| 70%      | 0.7     | Podgląd na żywo i poprawki |
| 80%      | 0.8     | Kompletny Import/Export          |
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
- [x] Lista pytań z kartami
- [x] Typ pytania (ikona/emoji)
- [x] Kategoria i tagi
- [x] Trudność (gwiazdki)
- [x] Paginacja (50 pytań na stronę)
- [x] Licznik pytań
- [x] Pusty stan (brak pytań)

**UI:**
- Grid lub lista kart
- Miniatura obrazu (jeśli istnieje)
- Przyciski akcji (Edit, Delete, Copy)

**Pliki:** `quiz_editor.html`

---

### Krok 4: Filtrowanie i wyszukiwanie (v0.4 - 40%)
**Cel:** Zaawansowane filtrowanie pytań

**Zadania:**
- [x] Wyszukiwanie po tekście (full text search)
- [x] Filtrowanie po typie (single/multiple/ordering/pairing)
- [x] Filtrowanie po kategorii
- [x] Filtrowanie po tagach (multi-select)
- [x] Resetowanie filtrów
- [x] Dynamiczne tagi z pytań
- [x] Licznik wyników

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
- [x] Formularz edycji (create/update)
- [x] Pola: text, category, tags, explanation, difficulty
- [x] Dynamiczne typy pytań (dropdown)
- [x] Walidacja w czasie rzeczywistym
- [x] Zapisywanie (Create/Update)
- [x] Anulowanie
- [x] Przycisk "Save & New"
- [x] Obsługa wszystkich typów pytań (single/multiple/ordering/pairing)
- [x] Tagi jako chips (dodawanie/usuwanie)
- [x] Poziom trudności (1-5 gwiazdek)

**Walidacja:**
- Text nie może być pusty
- Category nie może być pusta
- Min. 2 opcje dla single/multiple/ordering
- Min. 1 poprawna odpowiedź
- Min. 1 para dla pairing

**Pliki:** `quiz_editor.html`

---

### Krok 6: Obsługa obrazów (v0.6 - 60%)
**Cel:** Dodawanie obrazów do pytań

**Zadania:**
- [x] Upload przycisk (file input)
- [x] Konwersja do base64 (FileReader)
- [x] Podgląd obrazu
- [x] Usuwanie obrazu
- [x] Optymalizacja rozmiaru (max 1024x1024px)
- [x] Walidacja rozmiaru (max 1MB)
- [x] Walidacja formatu (JPG, PNG, GIF)
- [x] Kompresja jakości (85%)

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

### Krok 7: Podgląd na żywo i poprawki (v0.7 - 70%)
**Cel:** Podgląd pytania podczas edycji

**Zadania:**
- [x] Podgląd pytania podczas edycji
- [x] Podgląd dla każdego typu (single/multiple/ordering/pairing)
- [x] Współczesny design podglądu
- [x] Automatyczne odświeżanie podglądu
- [x] Poprawki błędów w edytorze
- [x] Poprawa walidacji
- [x] Ulepszenia UX

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

### Krok 7: Podgląd na żywo i poprawki (v0.7 - 70%)
**Cel:** Rozszerzona edycja z podglądem

**Zadania:**
- [ ] Podgląd pytania podczas edycji
- [ ] Podgląd dla każdego typu (single/multiple/ordering/pairing)
- [ ] Współczesny design podglądu
- [ ] Automatyczne odświeżanie podglądu
- [ ] Poprawki błędów w edytorze
- [ ] Poprawa walidacji
- [ ] Ulepszenia UX

**UI:**
- Sekcja podglądu w edytorze (right sidebar)
- Stylizacja karty podglądu
- Animacje przejść

**Pliki:** `quiz_editor.html`

---

### Krok 8: Kompletny Import/Export (v0.8 - 80%)
**Cel:** Pełna kompatybilność z Androidem

**Zadania:**
- [x] Import JSON (file input) - już zaimplementowane
- [x] Walidacja formatu JSON
- [x] Walidacja kompatybilności (version check)
- [x] Merge lub Replace All
- [x] Export JSON (download)
- [x] Format v2.11.0 (meta-data)
- [x] Kompatybilność wsteczna (starsze formaty)
- [x] Export do schowka (clipboard)
- [x] Import ze schowka

**Format export:**
```javascript
{
  "version": "2.11.0",
  "exportDate": "2026-02-14T...",
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
**Ostatnia aktualizacja:** 2026-02-15
**Status:** W implementacji (80% zrealizowanego planu)
