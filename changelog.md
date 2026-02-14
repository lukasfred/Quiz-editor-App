# Changelog - Quiz Question Editor

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased]

---

## [1.0.0] - 2026-01-30

### Added
- Jednoplikowa aplikacja HTML do zarządzania pytaniami
- Pełna kompatybilność z aplikacją Android v2.11.2+
- Wsparcie dla 4 typów pytań: single, multiple, ordering, pairing
- Edytor pytań z walidacją w czasie rzeczywistym
- Obsługa obrazów (base64)
- Import/Export JSON z meta-danymi
- Filtrowanie i wyszukiwanie pytań
- Responsywny UI (Material Design)
- Paginacja listy pytań
- Obsługa tagów i kategorii
- Poziom trudności (1-5 gwiazdek)
- Podgląd na żywo pytań
- Kopiowanie i duplikacja pytań

### Changed
- Format JSON zgodny z v2.11.0
- Indeksowanie odpowiedzi jako 1-based (1, 2, 3, 4)
- Meta-data w eksporcie (version, exportDate, category, totalQuestions)

### Technical Details
- **Lines of Code**: ~2500 linii (HTML + CSS + JS)
- **Dependencies**: None (Vanilla JS)
- **Browser Support**: Chrome 90+, Firefox 88+, Edge 90+, Safari 14+

### User Impact
- Możliwość tworzenia pytań w przeglądarce
- Pełna kompatybilność z aplikacją Android
- Łatwy import/export pytań
- Intuicyjny UI Material Design

---

## Wersje deweloperskie (prerelease)

### [0.3.1] - 2026-01-30

### Added
- Przełącznik języka (PL/EN) w lewej górnej części ekranu
- Pełna lokalizacja aplikacji (i18n)
- Tłumaczenia dla wszystkich tekstów v0.3
- Zapisywanie preferowanego języka w localStorage
- Dynamiczna zmiana języka bez odświeżenia strony
- Poprawiona struktura klasy QuizEditorApp (metody wewnątrz klasy)

### Changed
- Wszystkie teksty UI są teraz wielojęzyczne (PL/EN)
- Metoda updateAllText() aktualizuje wszystkie teksty przy zmianie języka
- Metoda t(key) jako helper dla tłumaczeń
- Metoda getQuestionTypeName() zwraca nazwę typu w wybranym języku
- Struktura klasy QuizEditorApp poprawna - wszystkie metody wewnątrz

### Technical Details
- Obiekt Translations z polskim i angielskim tłumaczeniami
- ~60 kluczy tłumaczeń dla każdego języka
- Lang switcher z flagami kraju (🇵🇱 / 🇬🇧)
- Position fixed top-left, z-index: 1000
- Zapisywanie języka w localStorage
- Ładowanie preferowanego języka przy starcie aplikacji

### User Impact
- Możliwość przełączania języka w czasie rzeczywistym
- Preferencja języka jest zapamiętywana
- Pełna obsługa dwujęzyczna (polski/angielski)
- Lepszy UX dla międzynarodowych użytkowników
- Bezpieczna struktura klas - nie powinna powodować błędów

### Bug Fixes
- Poprawiona struktura klasy QuizEditorApp - metody językowe są wewnątrz klasy
- Przełącznik języka działa poprawnie - metody są dostępne przez app.setLanguage()

---

### [0.3] - 2026-01-30
- Przełącznik języka (PL/EN) w lewej górnej części ekranu
- Pełna lokalizacja aplikacji (i18n)
- Tłumaczenia dla wszystkich tekstów v0.3
- Zapisywanie preferowanego języka w localStorage
- Dynamiczna zmiana języka bez odświeżenia strony

### Changed
- Wszystkie teksty UI są teraz wielojęzyczne
- Metoda updateAllText() aktualizuje wszystkie teksty przy zmianie języka
- Metoda getQuestionTypeName() zwraca nazwę typu w wybranym języku
- Metoda t(key) jako helper dla tłumaczeń

### Technical Details
- Obiekt Translations z polskim i angielskim tłumaczeniami
- ~60 kluczy tłumaczeń dla każego języka
- Lang switcher z flagami kraju (🇵🇱 / 🇬🇧)
- Position fixed top-left, z-index: 1000

### User Impact
- Możliwość przełączania języka w czasie rzeczywistym
- Preferencja języka jest zapamiętywana
- Pełna obsługa dwujęzyczna (polski/angielski)
- Lepszy UX dla międzynarodowych użytkowników

---

### [0.3] - 2026-01-30

### Added
- Lista pytań z kartami
- Typ pytania (ikona/emoji): ⭕, ☑️, 🔢, 🔗
- Kategoria i tagi jako badge
- Trudność (gwiazdki 1-5)
- Paginacja (50 pytań na stronę)
- Licznik pytań (stats: Single/Multiple/Ordering/Pairing/Wszystkie)
- Przyciski akcji (Edit, Delete, Copy)
- Miniatura obrazu w karcie pytania
- Wyświetlanie opcji dla single/multiple/ordering
- Wyświetlanie par dla pairing
- Wyświetlanie wyjaśnienia

### UI Components
- Statystyki (5 kart z liczbami)
- Grid kart pytań (responsive)
- Pagination z przyciskami numerycznymi
- Empty state z przyciskiem importu

### Technical Details
- Renderowanie listy pytań z paginacją
- Kopiowanie pytań z nowym ID
- Usuwanie pytań z potwierdzeniem
- Statystyki w czasie rzeczywistym
- Scroll do góry przy zmianie strony

### User Impact
- Możliwość przeglądania wszystkich pytań
- Kopiowanie pytań jako szablon
- Szybkie usuwanie pytań
- Czytelne karty z kolorystyką według typu

---

### [0.9] - 2026-01-30

### Fixed
- Poprawki błędów walidacji
- Poprawki responsywności

### Changed
- Optymalizacja wydajności
- Dodanie komunikatów pomocniczych

---

### [0.8] - 2026-01-30

### Added
- Import JSON (file input)
- Export JSON (download)
- Format v2.11.0 z meta-danymi
- Kompatybilność wsteczna
- Export do schowka
- Import ze schowka

### Changed
- Format exportu z meta-data
- Walidacja kompatybilności

---

### [0.7] - 2026-01-30

### Added
- Upload obrazów (file input)
- Konwersja do base64
- Podgląd obrazów
- Optymalizacja rozmiaru (max 1024x1024px)
- Walidacja rozmiaru (max 1MB)
- Walidacja formatu (JPG, PNG, GIF)
- Kompresja jakości (85%)

### Technical Details
- FileReader API
- Canvas (resize)
- data URI format

---

### [0.6] - 2026-01-30

### Added
- Single choice (Radio buttons)
- Multiple choice (Checkboxes)
- Ordering (up/down buttons)
- Pairing (left-right pairs)
- Podgląd na żywo dla każdego typu
- Dynamiczne dodawanie opcji/par
- Usuwanie opcji/par
- Auto-zaznaczanie poprawnych odpowiedzi

### Changed
- Dynamiczne pola w zależności od typu pytania

---

### [0.5] - 2026-01-30

### Added
- Modal formularza
- Pola: text, category, tags, explanation, difficulty
- Dynamiczne typy pytań (dropdown)
- Walidacja w czasie rzeczywistym
- Zapisywanie (Create/Update)
- Anulowanie
- Przycisk "Save & New"

### Validation Rules
- Text nie może być pusty
- Category nie może być pusta
- Min. 2 opcje dla single/multiple/ordering
- Min. 1 poprawna odpowiedź
- Min. 1 para dla pairing

---

### [0.4] - 2026-01-30

### Added
- Wyszukiwanie po tekście (full text search)
- Filtrowanie po typie
- Filtrowanie po kategorii
- Filtrowanie po tagach (multi-select)
- Resetowanie filtrów
- Dynamiczne tagi z pytań
- Licznik wyników

### UI
- Search bar z ikoną
- Dropdown dla typu
- Autocomplete dla kategorii
- Tag chips dla tagów

---

### [0.3] - 2026-01-30

### Added
- Lista pytań z kartami
- Typ pytania (ikona/emoji)
- Kategoria i tagi
- Trudność (gwiazdki)
- Paginacja (50 pytań na stronę)
- Licznik pytań
- Pusty stan (brak pytań)

### UI
- Grid lub lista kart
- Miniatura obrazu
- Przyciski akcji (Edit, Delete, Copy)

---

### [0.2] - 2026-01-30

### Added
- Klasa Question
- Metoda toJson() (export)
- Metoda fromJson() (import)
- Walidacja (isValid getter)
- Konwersja indeksów (0-based ↔ 1-based)
- Klasa PairItem (dla pairing)
- Helper functions (generowanie ID, base64)

### Model Specification
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

---

### [0.1] - 2026-01-30

### Added
- Szablon HTML5 z odpowiednimi meta tagami
- Style CSS Material Design
- Główny kontener aplikacji
- Nawigacja (sidebar/header)
- Podstawowe komponenty UI (buttony, inputy, karty)

### Technologies
- HTML5
- CSS3 (Flexbox, Grid, Variables)
- Material Design colors

---

## Format notacji

### Added
- Nowe funkcjonalności

### Changed
- Zmiany w istniejących funkcjonalnościach

### Deprecated
- Funkcjonalności które zostaną usunięte w przyszłych wersjach

### Removed
- Usunięte funkcjonalności

### Fixed
- Poprawki błędów

### Security
- Poprawki bezpieczeństwa

---

**Data rozpoczęcia:** 2026-01-30
**Wersja aplikacji:** 1.0.0
**Ostatnia aktualizacja:** 2026-01-30
