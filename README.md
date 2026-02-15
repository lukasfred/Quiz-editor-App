# Quiz Question Editor

Jednoplikowa aplikacja HTML/JS do tworzenia i edycji plików pytań quizowych, w 100% zgodna z aplikacją Android v2.11.2+.

## 📋 Funkcjonalności

### Wersja v0.8.0 (80% zrealizowanego planu)

✅ **Kompletny Import/Export** - walidacja i obsługa formatów
- ✅ Walidacja formatu JSON
- ✅ Walidacja kompatybilności (version check)
- ✅ Merge lub Replace All
- ✅ Export JSON (download)
- ✅ Format v2.11.0 (meta-data)
- ✅ Kompatybilność wsteczna (starsze formaty)
- ✅ Export do schowka (clipboard)
- ✅ Import ze schowka

✅ **Podgląd na żywo** - automatyczne odświeżanie podczas edycji
- 👁️ Podgląd pytania w czasie rzeczywistym
- 📋 Obsługa wszystkich typów pytań (single/multiple/ordering/pairing)
- 🎨 Współczesny design podglądu
- 🔄 Automatyczne odświeżanie przy każdej zmianie
- 📱 Responsywny layout (podgląd na górze na mobile)
- ✨ Pusty stan z informacją

✅ **Obsługa obrazów** - dodawanie i zarządzanie obrazami

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

✅ **Przełącznik języka (PL/EN)** ⬅️ NOWE!
- Zlokalizowana aplikacja
- Preferencja języka zapamiętywana
- Zmiana języka bez odświeżenia strony
- Bezpieczne funkcje (brak błędów przy brakujących elementach)
- Konsolowe logi do debugowania

✅ **Akcje na pytaniach**
- ✏️ **Edytuj** - (w implementacji, v0.5)
- 📋 **Kopiuj** - kopiuje pytanie z nowym ID
- 🗑️ **Usuń** - usuwa pytanie z potwierdzeniem

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

## 📤 Import pytań

1. Przejdź do zakładki **Import/Export**
2. Wybierz plik JSON z pytaniami
3. Pytania zostaną zaimportowane automatycznie
4. Format musi być zgodny z Android v2.11.0+

**Przykładowy plik:** `spanish_a1_questions.json` (100 pytań, wszystkie typy)

## 📋 Format pytań

### Pytanie Single/Multiple/Ordering:

```json
{
  "id": 1700000001001,
  "type": "single",
  "text": "What is 'hello' in Spanish?",
  "category": "Espanyol!",
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
  "id": 1700000001050,
  "type": "pairing",
  "text": "Match English to Spanish translations:",
  "category": "Espanyol!",
  "tags": ["vocabulary", "greetings", "pairing"],
  "explanation": "These are basic greetings in Spanish.",
  "imageData": "",
  "pairs": [
    {"left": "Hello", "right": "Hola"},
    {"left": "Thank you", "right": "Gracias"},
    {"left": "Goodbye", "right": "Adiós"}
  ],
  "options": [],
  "correct": []
}
```

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
- Debugowanie w konsoli przeglądarki

### Flagi krajów:
- 🇵🇱 PL (Polski)
- 🇬🇧 EN (Angielski)

### Debugowanie:
W razie z problemami z przełącznikiem, sprawdź konsolę przeglądarki (F12) pod Console).

Szukaj logów:
```
Quiz Question Editor v0.3.1 - Initializing...
Language preference loaded from localStorage: pl (lub en)
setLanguage() called with: en
updateAllText() called, language: en
updateAllText() completed
```

Jeśli widzisz błędy `Element not found:`, zgłoś je do dokumentacji.

Zobacz też plik `DEBUG_GUIDE.md` szczegółowy przewodnik debugowania.

---

## 🗺️ Plan rozwoju

### Zrealizowane (80%):
- ✅ v0.1 - Podstawowa struktura HTML/CSS
- ✅ v0.2 - Modele danych
- ✅ v0.3 - Lista pytań, statystyki, paginacja
- ✅ v0.3.1 - Przełącznik języka (PL/EN) z debugowaniem
- ✅ v0.4 - Filtrowanie i wyszukiwanie
- ✅ v0.5 - Edytor pytań basic
- ✅ v0.6 - Obsługa obrazów
- ✅ v0.7 - Podgląd na żywo
- ✅ v0.8 - **Kompletny Import/Export**

### Planowane:
- ⏳ v0.9 - Testowanie i poprawki (90%)
- ⏳ v1.0 - Wersja produkcyjna (100%)

## 📄 Pliki

- `quiz_editor.html` - główna aplikacja (jednoplikowa)
- `plan.md` - szczegółowy plan implementacji
- `changelog.md` - historia zmian
- `spanish_a1_questions.json` - przykładowe pytania (100 szt.)
- `DEBUG_GUIDE.md` - przewodnik debugowania przełącznika języka
- `README.md` - ten plik - dokumentacja

## 🤝 Współpraca

Aplikacja jest w pełni zgodna z aplikacją Android v2.11.2+.
Pytania stworzone w tym edytorze można bezproblemowo zaimportować do aplikacji Android.

## 📝 Licencja

Aplikacja jest częścią projektu QuizApp (Android + Web Editor).

---

**Wersja aplikacji:** v0.8.0
**Data:** 2026-02-15
**Postęp implementacji:** 80%
**Status:** Kompletny Import/Export
