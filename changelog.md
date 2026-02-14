# Changelog - Quiz Question Editor

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased]

---

## [0.5.0] - 2026-02-14

### Added
- **Edytor pytań** (50% planu zrealizowanego)
- ✏️ **Tworzenie nowych pytań** - pełny formularz z walidacją
- ✏️ **Edycja istniejących pytań** - ładowanie danych do formularza
- 📝 **Obsługa wszystkich typów pytań**:
  - ⭕ Single Choice - radio buttons dla poprawnych odpowiedzi
  - ☑️ Multiple Choice - checkboxy dla poprawnych odpowiedzi
  - 🔢 Ordering - lista z przyciskami up/down
  - 🔗 Pairing - edycja par left-right
- 🎯 **Walidacja w czasie rzeczywistym**:
  - Treść pytania wymagana
  - Kategoria wymagana
  - Minimum 2 opcje dla single/multiple/ordering
  - Minimum 1 poprawna odpowiedź
  - Minimum 1 para dla pairing
- 🏷️ **Obsługa tagów** - dodawanie/usuwanie tagów jako chips
- ⭐ **Wybór poziomu trudności** - 1-5 gwiazdek
- 💾 **Zapisywanie** - Save i Save & New
- 🔄 **Resetowanie formularza** - czyszczenie wszystkich pól
- ✅ **Obsługa importu JSON** - wczytywanie pytań z pliku

### Changed
- Zaktualizowano AppState.version na '0.5.0'
- Dodano AppState.editingQuestionId do śledzenia edytowanego pytania
- Zaktualizowano bindEvents() do obsługi formularza edycji
- Zaktualizowano updateAllText() do obsługi formularza edycji
- Metoda editQuestion() teraz faktycznie otwiera formularz z danymi
- Metoda openEditor() obsługuje tworzenie nowych i edycję istniejących pytań
- Metoda closeEditor() zamyka formularz i wraca do listy pytań

### Technical Details
- **Lines of Code**: ~600 linii (HTML formularz + CSS + JS)
- **Dependencies**: None (Vanilla JS)
- **Browser Support**: Chrome 90+, Firefox 88+, Edge 90+, Safari 14+
- **Form Components**:
  - Typ pytania (dropdown)
  - Treść pytania (textarea)
  - Kategoria (input text)
  - Tagi (input + chips)
  - Poziom trudności (5 przycisków gwiazdek)
  - Wyjaśnienie (textarea - opcjonalne)
  - Opcje odpowiedzi (dynamiczna lista)
  - Pary (dla pairing - dynamiczna lista)

### User Impact
- Możliwość tworzenia nowych pytań z pełną walidacją
- Możliwość edycji istniejących pytań
- Obsługa wszystkich 4 typów pytań w jednym formularzu
- Intuicyjny interfejs z walidacją w czasie rzeczywistym
- Możliwość szybkiego tworzenia wielu pytań (Save & New)
- Łatwe zarządzanie tagami i opcjami

---

## [0.4.0] - 2026-01-30

### Added
- **Filtrowanie i wyszukiwanie** (40% planu zrealizowanego)
- 📋 **Pasek wyszukiwania** - pełnotekstowy wyszukiwanie po tekście (treść pytania, opcje)
- 🔍 **Filtrowanie po typie** - dropdown (all, single, multiple, ordering, pairing)
- 📁 **Filtrowanie po kategorii** - autocomplete z dynamiczną listą kategorii (z pytań)
- 🏷️ **Filtrowanie po tagach** - multi-select tagi jako chips do usuwania
- 🔄 **Resetowanie filtrów** - jeden przycisk resetuje wszystkie filtry
- 📊 **Pasek statystyk** - dynamiczny licznik dla wszystkich filtrów
- ✅ **Walidacja w czasie rzeczywistym** - wyniki pojawiają się natychmiast

### Technical Details
- Dodano paska filtra do toolbar strony pytań
- Implementacja logic filtrów w renderQuestions()
- Dodano metody: getFilteredQuestions(), resetFilters()
- Aktualizacja UI w updateFiltersUI() i updateEmptyState()
- Dynamiczne ładowanie kategorii z pytań
- Tagi z multi-select - można usuwać klikając na X
- Styl CSS dla filtraów (toolbar, chips, inputs)

### Filter Logic
```javascript
// Zwraca przefiltrowane pytania
getFilteredQuestions() {
    let questions = AppState.questions;

    // Filtrowanie po tekście
    if (AppState.filterSearch.trim() !== '') {
        const searchLower = AppState.filterSearch.toLowerCase();
        questions = questions.filter(q => {
            return q.text.toLowerCase().includes(searchLower) ||
                   q.options.some(o => o.toLowerCase().includes(searchLower));
        });
    }

    // Filtrowanie po typie
    if (AppState.filterType !== 'all') {
        questions = questions.filter(q => q.type === AppState.filterType);
    }

    // Filtrowanie po kategorii
    if (AppState.filterCategory && AppState.filterCategory !== 'all') {
        questions = questions.filter(q => q.category === AppState.filterCategory);
    }

    // Filtrowanie po tagach
    if (AppState.filterTags.length > 0) {
        questions = questions.filter(q => {
            const questionTags = q.tags || [];
            return AppState.filterTags.every(tag => questionTags.includes(tag));
        });
    }
}
```

### UI Components
- Search input z placeholderem (PL: "Szukaj...", EN: "Search...")
- Dropdown typ pytań (All/Single/Multiple/Ordering/Pairing)
- Autocomplete kategorii z opcją "Wszystkie"
- Multi-select tagi z usuwaniem (chip z X)
- Przycisk resetujący wszystkie filtry

### User Impact
- Szybkie i intuicyjne filtrowanie
- Wszystkie filtry działają razem (AND logic)
- Przeładowanie wyników natychmiast
- Możliwość resetowania wszystkich filtrów jednym przyciskiem
- Statystyka pokazuje liczbę przefiltrowanych pytań
- Zwiększa używalność aplikacji

### Changed
- Aktualizacja renderQuestions() - teraz uwzględa wszystkie filtry
- Dodano pasek filtrów do interfejsu pytań
- Zmieniono toolbar na karty z filtrami
- Dodano dynamiczne kategorie do dropdowna
- Dodano kontener tagów z chips

### Technical Details
- **Lines of Code**: ~400 linii (HTML + CSS + JS)
- **Dependencies**: None (Vanilla JS)
- **Browser Support**: Chrome 90+, Firefox 88+, Edge 90+, Safari 14+

---

## Wersje deweloperskie (prerelease)

### [0.3.1] - 2026-01-30

### Added
- Przełącznik języka (PL/EN) w lewej górnej części ekranu
- Pełna lokalizacja aplikacji (i18n)
- Tłumaczenia dla wszystkich tekstów v0.3
- Zapisywanie preferowanego języka w localStorage
- Dynamiczna zmiana języka bez odświeżenia strony
- Bezpieczne funkcje (brakujące elementy)

### Technical Details
- Obiekt Translations z polskim i angielskim tłumaczeniami
- Metoda setLanguage(lang) - zmiana języka (PL/EN)
- Metoda updateAllText() - aktualizacja wszystkich tekstów
- Metoda t(key) - helper dla tłumaczeń
- Metoda getQuestionTypeName(type) - nazwa typu w wybranym języku
- Safe helper functions: safeGetElement(), safeSetText(), safeSetHTML()

### User Impact
- Możliwość przełączania języka w czasie rzeczywistym
- Preferencja języka jest zapamiętywana
- Pełna obsługa dwujęzyczna (polski/angielski)
- Lepszy UX dla międzynarodowych użytkowników

---

### [0.3] - 2026-01-30

### Added
- Lista pytań z kartami
- Statystyki pytań (5 kart z liczbami)
- Paginacja (50 pytań na stronę)
- Kopiowanie pytań (z nowym ID)
- Usuwanie pytań (z potwierdzeniem)

### Changed
- Aktualizacja renderStats() - liczniki per typ
- Aktualizacja renderQuestions() - renderowanie listy pytań
- Aktualizacja renderPagination() - przyciski numeracji stron
- Aktualizacja updateUI() - główna metoda odświeżania UI

### Technical Details
- **Lines of Code**: ~700 linii (HTML + CSS + JS)
- **Grid Layout**: repeat(auto-fill, minmax(400px, 1fr))
- **Card Design**: Material Design z kolorystyką typów (Green/Blue/Orange/Purple)
- **Difficulty Display**: 1-5 gwiazdek
- **Badge System**: Tagi i kategorie jako badge
- **Pagination**: Previous/Next/Page Number/Info

### User Impact
- Możliwość przeglądania wszystkich pytań
- Kopiowanie pytań jako szablonów
- Szybkie usuwanie pytań
- Responsywny layout (mobile-friendly)
- Liczniki pytań w czasie rzeczywistym

---

### [0.2] - 2026-01-30

### Added
- Modele danych (Question, PairItem)
- Metoda toJson() (export format v2.11.0)
- Metoda fromJson() (import z walidacją)
- Konwersja indeksów (0-based ↔ 1-based)
- Helper functions (generateId, fileToBase64, resizeImage)

### Technical Details
- **Lines of Code**: ~250 linii (HTML + CSS + JS)
- **Model Structure**: Question, PairItem classes with validation
- **Validation**: isValid getter checks all required fields
- **Index Conversion**: 0-based internally, 1-based for export
- **Format Compatibility**: v2.11.0, v2.0, v1.0

### User Impact
- Pełna kompatybilność z aplikacją Android v2.11.2+
- Możliwość tworzenia pytań zgodnych z Androidem
- Walidacja struktury JSON
- Obsługa wszystkich 4 typów pytań

---

### [0.1] - 2026-01-30

### Added
- Podstawowa struktura HTML5
- Style CSS Material Design
- Główny kontener aplikacji
- Nawigacja (sidebar/header)
- Podstawowe komponenty UI (buttony, inputy, karty)
- Toast notifications
- Pusty stan (brak pytań)
- Obsługa jęzka (PL)

### Technical Details
- **Lines of Code**: ~800 linii (HTML + CSS + JS)
- **Material Design**: Material 3 colors, cards, shadows, transitions
- **Responsive Design**: Mobile-first approach
- **Components**: Buttons, Inputs, Cards, Notifications
- **Colors**: Primary #673AB7, Secondary #FF9800, Background #F5F5F5

### User Impact
- Solidna podstawa dla edytora pytań
- Możliwość zarządzania pytań w przeglądarce
- Responsywny layout na wszystkich urządzeniach

---

## [1.0.0] - 2026-01-27

### Added
- Jednoplikowa aplikacja HTML do zarządzania pytaniami
- Pełna kompatybilność z aplikacją Android v2.11.2+
- Obsługa 4 typów pytań: single, multiple, ordering, pairing
- Edytor pytań z walidacją w czasie rzeczywistym
- Obsługa obrazów (base64)
- Import/Export JSON z meta-danymi
- Responsywny UI (Material Design)
- Wielojęzyczny (PL)

### Technical Details
- **Lines of Code**: ~2800 linii (jednoplikowy HTML + CSS + JS)
- **Dependencies**: None (Vanilla JS)
- **Browser Support**: Chrome 90+, Firefox 88+, Edge 90+, Safari 14+
- **Format Compatibility**: JSON v2.11.0 with metadata

### User Impact
- Możliwość tworzenia pytań w przeglądarce
- Pełna zgodność z aplikacją Android
- Łatwy import/Export pytań
- Dostępny w 100% bez instalacji

---

## [Unreleased]

---

## Next Version: [0.5.0] - Edytor pytań (50% planu)
**Status:** W implementacji

### Planowane funkcjonalności:
- Formularz edycji pytań
- Walidacja w czasie rzeczywistym
- Podgląd na żywo pytań
- Zapisywanie (Create/Update)
- Anulowanie

---

**Format notacji:**
### Added
- Nowa funkcjonalność
- Poprawka błędu
- Zmiana w istniejącym

### Changed
- Zmiana w istniejącej funkcjonalności
- Deprecacja starej funkcjonalności
