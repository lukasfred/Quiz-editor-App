# Quiz Question Editor

Jednoplikowa aplikacja HTML/JS do tworzenia i edycji plików pytań quizowych, w 100% zgodna z aplikacją Android v2.11.2+.

## 📋 Funkcjonalności

### Wersja v1.0.0 (100% zrealizowanego planu) - PRODUKCJA

✅ **Kompletny Import/Export** - walidacja i obsługa formatów
- ✅ Walidacja formatu JSON
- ✅ Walidacja kompatybilności (version check)
- ✅ Merge lub Replace All
- ✅ Export JSON (download)
- ✅ Format v2.11.0 (meta-data)
- ✅ Kompatybilność wsteczna (starsze formaty)
- ✅ Export do schowka (clipboard)
- ✅ Import ze schowka
- ✅ Eksport po kategoriach

✅ **Podgląd na żywo** - automatyczne odświeżanie podczas edycji
- 👁️ Podgląd pytania w czasie rzeczywistym
- 📋 Obsługa wszystkich typów pytań (single/multiple/ordering/pairing)
- 🎨 Współczesny design podglądu
- 🔄 Automatyczne odświeżanie przy każdej zmianie
- 📱 Responsywny layout (podgląd na górze na mobile)
- ✨ Pusty stan z informacją

✅ **Obsługa obrazów** - dodawanie i zarządzanie obrazami
- 📷 Upload obrazów z walidacją formatu (JPG, PNG, GIF)
- 🖼️ Podgląd obrazu w formularzu edycji
- 🗑️ Usuwanie obrazu
- 📐 Automatyczna optymalizacja rozmiaru (max 1024x1024px)
- 💾 Kompresja jakości JPEG (85%)
- ✅ Walidacja rozmiaru (max 1MB)
- ℹ️ Wyświetlanie informacji o rozmiarze w KB

✅ **Edytor pytań** - pełny formularz z walidacją w czasie rzeczywistym
- ✏️ Tworzenie nowych pytań
- ✏️ Edycja istniejących pytań
- ⭕ Single Choice - radio buttons
- ☑️ Multiple Choice - checkboxy
- 🔢 Ordering - lista z przyciskami up/down
- 🔗 Pairing - pary left-right
- 🎯 Walidacja w czasie rzeczywistym
- 🏷️ Obsługa tagów (chips)
- ⭐ Wybór poziomu trudności (1-5)
- 💾 Zapisywanie (Save & New)

✅ **Lista pytań z kartami**
- Responsywny grid z kartami pytań
- Kolorystyka według typu (Single/Multiple/Ordering/Pairing)
- Miniatura obrazu (jeśli istnieje)
- Wyświetlanie opcji lub par
- Poziom trudności (1-5 gwiazdek)
- Kategorie i tagi jako badge

✅ **Statystyki pytań**
- Liczba pytań dla każdego typu
- Całkowita liczba pytań
- Aktualizacja w czasie rzeczywistym

✅ **Paginacja**
- 50 pytań na stronę
- Przyciski numeryczne
- Nawigacja: Wstecz / Dalej →
- Info: Wyświetlane 1-50 z 292 pytań

✅ **Filtrowanie i wyszukiwanie**
- 🔍 Pełnotekstowe wyszukiwanie
- 📋 Filtrowanie po typie
- 📁 Filtrowanie po kategorii
- 🏷️ Filtrowanie po tagach (multi-select)
- 🔄 Resetowanie filtrów
- 📊 Dynamiczny licznik wyników

✅ **Akcje na pytaniach**
- ✏️ **Edytuj** - otwiera formularz edycji
- 📋 **Kopiuj** - kopiuje pytanie z nowym ID
- 🗑️ **Usuń** - usuwa pytanie z potwierdzeniem

✅ **Przełącznik języka (PL/EN)**
- Zlokalizowana aplikacja
- Preferencja języka zapamiętywana
- Zmiana języka bez odświeżenia strony
- Bezpieczne funkcje (brak błędów przy brakujących elementach)

✅ **Obsługa kategorii i tagów**
- Dynamiczne generowanie listy kategorii
- Multi-select tagi
- Aktywne tagi jako removable chips
- Czyszczenie pytań z wybranej kategorii

✅ **Responsywny design**
- Mobile-friendly layout
- Sidebar toggle dla urządzeń mobilnych
- Click-outside-to-close functionality
- Optymalizacja na różnych ekranach

✅ **Obsługiwane typy pytań**
- ⭕ **Single Choice** - jedna poprawna odpowiedź
- ☑️ **Multiple Choice** - wiele poprawnych odpowiedzi
- 🔢 **Ordering** - ułóż w odpowiedniej kolejności
- 🔗 **Pairing** - łącz pary

---

## 🚀 Szybki start

### Otwórz aplikację w przeglądarce:

```bash
cd /home/lukas/opencode/quizadfr/question_app/Quiz-editor-App
python3 -m http.server 8080
```

Następnie otwórz w przeglądarce:
```
http://localhost:8080/quiz_editor.html
```

Alternatywnie, po prostu dwukrotnie kliknij na `quiz_editor.html`

---

## 📖 Instrukcja użycia

### Tworzenie nowych pytań

1. Kliknij przycisk **"Nowe pytanie"** w menu bocznym
2. Wybierz **typ pytania** z dropdownu:
   - Single Choice - jedna poprawna odpowiedź
   - Multiple Choice - wiele poprawnych odpowiedzi
   - Ordering - ułóż opcje w odpowiedniej kolejności
   - Pairing - łącz pary left-right
3. Wprowadź **treść pytania**
4. Wybierz **kategorię** (opcjonalnie)
5. Dodaj **opcje odpowiedzi** (minimum 2 dla single/multiple/ordering)
6. Zaznacz **poprawne odpowiedzi** (minimum 1 dla single/multiple)
7. Dodaj **tagi** (wpisz tekst i naciśnij Enter)
8. Wybierz **poziom trudności** (1-5 gwiazdek)
9. Dodaj **wyjaśnienie** (opcjonalnie)
10. Dodaj **obraz** (opcjonalnie) - max 1MB, format JPG/PNG/GIF
11. Kliknij **"Zapisz"** lub **"Zapisz i dodaj nowy"**

### Edycja istniejących pytań

1. Przejdź do zakładki **"Pytania"**
2. Znajdź pytanie do edycji (możesz użyć wyszukiwania lub filtrów)
3. Kliknij przycisk **"Edytuj"** na karcie pytania
4. Zmodyfikuj pola według potrzeb
5. Kliknij **"Zapisz"** aby zapisać zmiany

### Kopiowanie pytań

1. Przejdź do zakładki **"Pytania"**
2. Znajdź pytanie do skopiowania
3. Kliknij przycisk **"Kopiuj"** na karcie pytania
4. Pytanie zostanie skopiowane z nowym ID i tekstem "(copy)"

### Usuwanie pytań

1. Przejdź do zakładki **"Pytania"**
2. Znajdź pytanie do usunięcia
3. Kliknij przycisk **"Usuń"** na karcie pytania
4. Potwierdź usunięcie w oknie dialogowym

### Wyszukiwanie pytań

1. Przejdź do zakładki **"Pytania"**
2. Użyj paska wyszukiwania aby znaleźć pytania po tekście
3. Wyszukiwanie przeszukuje:
   - Treść pytania
   - Opcje odpowiedzi
   - Kategorie
   - Tagi

### Filtrowanie pytań

1. Przejdź do zakładki **"Pytania"**
2. Użyj filtrów aby zawęzić wyniki:
   - **Typ** - Wybierz typ pytania z dropdownu
   - **Kategoria** - Wybierz kategorię z listy lub wpisz nazwę
   - **Tagi** - Wybierz tagi z dropdownu (multi-select)
3. Kliknij **"Resetuj filtry"** aby wyczyścić wszystkie filtry

### Import pytań

1. Przejdź do zakładki **"Import/Export"**
2. Kliknij **"Importuj z pliku"** i wybierz plik JSON
3. Wybierz opcję importu:
   - **Merge** - dołącza pytania do istniejących
   - **Replace** - zamienia wszystkie pytania
   - **Cancel** - anuluje import
4. Pytania zostaną zaimportowane i sprawdzone pod kątem błędów

### Import ze schowka

1. Przejdź do zakładki **"Import/Export"**
2. Kliknij **"Importuj ze schowka"**
3. Wklej JSON ze schowka
4. Kliknij **"Importuj"**
5. Wybierz opcję importu (Merge/Replace/Cancel)

### Eksport pytań

1. Przejdź do zakładki **"Import/Export"**
2. Wybierz kategorię do eksportu (opcjonalnie)
3. Kliknij **"Eksportuj do pliku"** aby pobrać plik JSON
4. Lub kliknij **"Kopiuj do schowka"** aby skopiować JSON do schowka

### Czyszczenie pytań

1. Przejdź do zakładki **"Import/Export"**
2. Kliknij **"Usuń wszystkie"** aby wyczyścić całą bazę pytań
3. Lub wybierz kategorię i kliknij **"Wyczyść kategorię"** aby usunąć tylko pytania z tej kategorii

---

## 📤 Import pytań

### Obsługiwane formaty:

**Format v2.11.0** (aktualny, zalecany):
```json
{
  "version": "2.11.0",
  "exportDate": "2026-01-30T16:54:06.300Z",
  "category": "all",
  "totalQuestions": 292,
  "questions": [...]
}
```

**Format v2.0** (kompatybilny):
```json
{
  "version": "2.0",
  "exportDate": "2026-01-30T16:54:06.300Z",
  "questions": [...]
}
```

**Format v1.0** (prosty, kompatybilny):
```json
[
  {
    "id": 1700000001001,
    "type": "single",
    "text": "Question text...",
    "options": ["A", "B", "C", "D"],
    "correct": [1]
  }
]
```

### Przykładowy plik:
`sample_questions.json` - zawiera przykładowe pytania wszystkich typów

---

## 📋 Format pytań

### Pytanie Single/Multiple/Ordering:

```json
{
  "id": "1700000001001",
  "type": "single",
  "text": "What is 'hello' in Spanish?",
  "category": "Spanish",
  "tags": ["greetings", "basics"],
  "explanation": "Hola is most common way to say hello in Spanish.",
  "imageData": "",
  "options": [
    "Hola",
    "Adiós",
    "Gracias",
    "Por favor"
  ],
  "correct": [1],
  "difficulty": 1
}
```

### Pytanie Pairing:

```json
{
  "id": "1700000001050",
  "type": "pairing",
  "text": "Match English to Spanish translations:",
  "category": "Spanish",
  "tags": ["vocabulary", "greetings", "pairing"],
  "explanation": "These are basic greetings in Spanish.",
  "imageData": "",
  "pairs": [
    {"left": "Hello", "right": "Hola"},
    {"left": "Thank you", "right": "Gracias"},
    {"left": "Goodbye", "right": "Adiós"}
  ],
  "options": [],
  "correct": [],
  "difficulty": 1
}
```

### Opis pól:

- **id**: Unikalny identyfikator pytania (string)
- **type**: Typ pytania - "single", "multiple", "ordering", "pairing"
- **text**: Treść pytania (HTML dozwolony)
- **category**: Nazwa kategorii (string)
- **tags**: Tablica tagów (string[])
- **explanation**: Opcjonalne wyjaśnienie (string)
- **imageData**: Base64 data URI obrazu (opcjonalne)
- **options**: Tablica opcji odpowiedzi (string[])
- **correct**: Tablica indeksów poprawnych odpowiedzi (number[], 1-based)
- **pairs**: Tablica par left-right (tylko dla pairing)
- **difficulty**: Poziom trudności 1-5 (number)

---

## 📊 Format eksportu (v2.11.0)

```json
{
  "version": "2.11.0",
  "exportDate": "2026-01-30T16:54:06.300Z",
  "category": "all",
  "totalQuestions": 292,
  "questions": [...]
}
```

---

## 🎨 Kompatybilność z Androidem

### Współpraca z aplikacją Android v2.11.2+:

✅ **Import** - aplikacja Android poprawnie importuje pytania
✅ **Export** - aplikacja Android poprawnie odczytuje export
✅ **Indeksowanie** - odpowiedzi są 1-based (1, 2, 3, 4)
✅ **Typy pytań** - wszystkie 4 typy są obsługiwane
✅ **Meta-data** - version, exportDate, category, totalQuestions
✅ **Obrazy** - base64 format jest kompatybilny
✅ **Tagi** - tablica stringów
✅ **Kategorie** - string
✅ **Trudność** - 1-5
✅ **Wyjaśnienia** - opcjonalne pole

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

## 🌐 Przełącznik języka

### Lokalizacja:
- Lewy górny róg ekranu (fixed)
- Pozycja: Top: 1rem, Left: 1rem
- Z-index: 1000 (nad wszystkimi elementami)

### Funkcje:
- Zmiana języka w czasie rzeczywistym
- Zapamiętywanie preferencji w localStorage
- Automatyczna aktualizacja wszystkich tekstów UI
- Bezpieczne funkcje (brak błędów przy brakujących elementach)

### Flagi krajów:
- 🇵🇱 PL (Polski)
- 🇬🇧 EN (Angielski)

---

## 🎯 Skróty klawiszowe

- **Ctrl + S** - Zapisz pytanie (w edytorze)
- **Ctrl + N** - Nowe pytanie
- **Esc** - Zamknij edytor / modal

---

## 📱 Responsywność

### Desktop (> 768px):
- Sidebar z nawigacją
- Grid kart pytań
- Pełna funkcjonalność

### Tablet (768px - 1024px):
- Collapsible sidebar
- Dostosowany grid kart

### Mobile (< 768px):
- Bottom navigation + stacked content
- Sidebar toggle button
- Optymalizowany layout

---

## 🗺️ Historia wersji

### Zrealizowane (100%):
- ✅ v0.1 - Podstawowa struktura HTML/CSS
- ✅ v0.2 - Modele danych
- ✅ v0.3 - Lista pytań, statystyki, paginacja
- ✅ v0.4 - Filtrowanie i wyszukiwanie
- ✅ v0.5 - Edytor pytań basic
- ✅ v0.6 - Obsługa obrazów
- ✅ v0.7 - Podgląd na żywo
- ✅ v0.8 - Kompletny Import/Export
- ✅ v0.9 - Testowanie i poprawki
- ✅ v1.0 - **Wersja produkcyjna** ✨

---

## 📄 Pliki

- `quiz_editor.html` - główna aplikacja (jednoplikowa)
- `plan.md` - szczegółowy plan implementacji
- `changelog.md` - historia zmian
- `progress.md` - postęp implementacji
- `sample_questions.json` - przykładowe pytania
- `README.md` - ten plik - dokumentacja

---

## 🤝 Współpraca z aplikacją Android

Aplikacja jest w pełni zgodna z aplikacją Android v2.11.2+.
Pytania stworzone w tym edytorze można bezproblemowo zaimportować do aplikacji Android.

### Flow pracy:
1. Utwórz pytania w Quiz Question Editor
2. Eksportuj do pliku JSON lub skopiuj do schowka
3. Zaimportuj do aplikacji Android
4. Gotowe!

---

## 🐛 Rozwiązywanie problemów

### Pytania nie zapisują się:
- Sprawdź czy wszystkie wymagane pola są wypełnione
- Sprawdź czy masz co najmniej 2 opcje dla single/multiple/ordering
- Sprawdź czy zaznaczyłeś co najmniej 1 poprawną odpowiedź dla single/multiple

### Import nie działa:
- Sprawdź czy plik JSON ma poprawny format
- Sprawdź czy wersja formatu jest kompatybilna
- Sprawdź konsolę przeglądarki pod kątem błędów

### Obrazy się nie wyświetlają:
- Sprawdź czy format to JPG, PNG lub GIF
- Sprawdź czy rozmiar pliku nie przekracza 1MB
- Sprawdź czy obraz nie jest uszkodzony

---

## 📝 Licencja

Aplikacja jest częścią projektu QuizApp (Android + Web Editor).

---

## 📞 Pomoc

W razie pytań lub problemów:
1. Sprawdź sekcję **"Pomoc"** w aplikacji
2. Przejrzyj `changelog.md` dla informacji o zmianach
3. Sprawdź konsolę przeglądarki (F12) pod kątem błędów

---

**Wersja aplikacji:** v1.0.0 ✨
**Data:** 2026-02-16
**Postęp implementacji:** 100%
**Status:** Wersja produkcyjna
