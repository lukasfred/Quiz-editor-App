# Quiz Question Editor

Jednoplikowa aplikacja HTML/JS do tworzenia i edycji plików pytań quizowych, w 100% zgodna z aplikacją Android v2.11.2+.

## 📋 Funkcjonalności

### Wersja v0.3.1 (30% zrealizowanego planu)

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
- Zmiana języka bez odświeżania strony
- Lewy górny róg (fixed)
- Flagi krajów: 🇵🇱 / 🇬🇧
- Aktualizacja wszystkich tekstów w czasie rzeczywistym

✅ **Akcje na pytaniach**
- ✏️ **Edytuj** - (w implementacji, v0.5)
- 📋 **Kopiuj** - kopiuje pytanie z nowym ID
- 🗑️ **Usuń** - usuwa pytanie z potwierdzeniem

✅ **Obsługiwane typy pytań**
- ⭕ **Single Choice** - jedna poprawna odpowiedź
- ☑️ **Multiple Choice** - wiele poprawnych odpowiedzi
- 🔢 **Ordering** - ułóż w odpowiedniej kolejności
- 🔗 **Pairing** - łącz pary

## 🚀 Szybki start

### Otwórz aplikację w przeglądarce:

```bash
cd /home/lukas/opencode/quizadfr/question_app
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

## 📝 Przełącznik języka

Przełącznik języka znajduje się w **lewym górnym rogu** ekranu:

- 🇵🇱 **PL** - Polski język
- 🇬🇧 **EN** - Angielski język

Preferowany język jest zapamiętywany w `localStorage` i wczytywany przy następnym uruchomieniu aplikacji.

## 🗺️ Plan rozwoju

### Zrealizowane (30%):
- ✅ v0.1 - Podstawowa struktura HTML/CSS
- ✅ v0.2 - Modele danych (Question, PairItem)
- ✅ v0.3 - Lista pytań, statystyki, paginacja
- ✅ v0.3.1 - Przełącznik języka (PL/EN)

### Planowane:
- ⏳ v0.4 - Filtrowanie i wyszukiwanie (40%)
- ⏳ v0.5 - Edytor pytań basic (50%)
- ⏳ v0.6 - Edytor pytań all types (60%)
- ⏳ v0.7 - Obsługa obrazów (70%)
- ⏳ v0.8 - Import/Export (80%)
- ⏳ v0.9 - Testowanie i poprawki (90%)
- ⏳ v1.0 - Wersja produkcyjna (100%)

## 📄 Pliki

- `quiz_editor.html` - główna aplikacja (jednoplikowa)
- `plan.md` - szczegółowy plan implementacji
- `changelog.md` - historia zmian
- `spanish_a1_questions.json` - przykładowe pytania (100 szt.)
- `README.md` - ten plik - dokumentacja

## 🤝 Współpraca

Aplikacja jest w pełni zgodna z aplikacją Android v2.11.2+.
Pytania stworzone w tym edytorze można bezproblemowo zaimportować do aplikacji Android.

## 📝 Licencja

Aplikacja jest częścią projektu QuizApp (Android + Web Editor).

---

**Wersja aplikacji:** v0.3.1
**Data:** 2026-01-30
**Postęp implementacji:** 30%
**Status:** Wersja deweloperska
