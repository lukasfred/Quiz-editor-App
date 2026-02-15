# LINKI DO PLIKÓW KONFIGURACYJNYCH

## PLIKI .MD

### Główny katalog pracy:
```bash
/home/lukas/.local/share/Trash/files/question_app/Quiz-editor-App/
```
- `changelog.md` - Historia zmian aplikacji
- `progress.md` - Postęp implementacji
- `plan.md` - Globalny plan implementacji

### Katalog dzienny:
```bash
/home/lukas/opencode/quizadfr/question_app/Quiz-editor-App/
```
- `TODO_JUTRO.md` - Plan pracy na jutro **🔜 PRZECZYTAJ TO!**
- `STATUS.md` - Status aktualny
- `SHORTCUTS.md` - Skróty i komendy
- `LINKS.md` - Ten plik - linki do plików
- `changelog.md` - Historia zmian (kopia)
- `progress.md` - Postęp (kopia)

## PLIKI HTML

### Główna aplikacja:
```bash
/home/lukas/.local/share/Trash/files/question_app/Quiz-editor-App/quiz_editor.html
```

### Backupy:
```bash
/home/lukas/.local/share/Trash/files/question_app/Quiz-editor-App/
├── quiz_editor.html.backup-v0.4.0
├── quiz_editor.html.backup-v0.5.0-20260215
├── quiz_editor.html.backup-v0.6.0-20260215
├── quiz_editor.html.backup-v0.7.0-20260215
├── quiz_editor.html.backup-v0.8.0-20260215
└── quiz_editor.html.backup-v0.9.7-20260215-233100

/home/lukas/opencode/quizadfr/question_app/
├── quiz_editor.html.backup-v0.5.0-20260215
├── quiz_editor.html.backup-v0.6.0-20260215
├── quiz_editor.html.backup-v0.7.0-20260215
├── quiz_editor.html.backup-v0.8.0-20260215
├── quiz_editor.html.backup-v0.9.7-20260215-232757
└── quiz_editor.html.backup-v1.0.0-20260215-232131
```

## PRZYDATNE KOMENDY

### Otwórz wszystkie .md pliki:
```bash
cd /home/lukas/.local/share/Trash/files/question_app/Quiz-editor-App
code changelog.md progress.md plan.md
```

### Otwórz pliki dziennie:
```bash
cd /home/lukas/opencode/quizadfr/question_app/Quiz-editor-App
code TODO_JUTRO.md STATUS.md SHORTCUTS.md LINKS.md
```

### Porównaj pliki:
```bash
# Porównaj aktualne z v0.8.0
diff quiz_editor.html.backup-v0.8.0-20260215 quiz_editor.html

# Porównaj z ostatnim backupem
diff quiz_editor.html.backup-v0.9.7-20260215-233100 quiz_editor.html
```

### Znajdź metody:
```bash
# Znajdź metodę editQuestion
grep -n "editQuestion" quiz_editor.html

# Znajdź metodę copyQuestion
grep -n "copyQuestion" quiz_editor.html

# Znajdź metodę deleteQuestion
grep -n "deleteQuestion" quiz_editor.html

# Znajdź metodę getFilteredQuestions
grep -n "getFilteredQuestions" quiz_editor.html
```

### Znajdź wersje:
```bash
# Znajdź wszystkie wystąpienia numeru wersji
grep -n "v0.9.7\|0.9.7" quiz_editor.html
```

## STRUKTURA KATALOGÓW

```
/home/lukas/.local/share/Trash/files/question_app/
├── Quiz-editor-App/                     # Główny katalog pracy
│   ├── quiz_editor.html              # Aktualna aplikacja
│   ├── changelog.md                  # Historia zmian
│   ├── progress.md                   # Postęp
│   ├── plan.md                       # Plan
│   └── quiz_editor.html.backup-v*    # Backupy
│
/home/lukas/opencode/quizadfr/
└── question_app/
    ├── Quiz-editor-App/              # Katalog dzienny
    │   ├── TODO_JUTRO.md             # Plan jutro
    │   ├── STATUS.md                 # Status
    │   ├── SHORTCUTS.md             # Skróty
    │   ├── LINKS.md                 # Ten plik
    │   ├── quiz_editor.html          # Kopia aktualna
    │   ├── changelog.md              # Kopia historii
    │   ├── progress.md               # Kopia postępu
    │   └── quiz_editor.html.backup-v* # Backupy
    │
    └── quiz_editor.html.backup-v*    # Backupy główne
```

## PRZYDATNE LINKI

### Wewnątrz aplikacji:
- Strona główna: http://localhost:8080/quiz_editor.html
- Pomoc: http://localhost:8080/quiz_editor.html#help
- Import/Export: http://localhost:8080/quiz_editor.html#import-export

### Dokumentacja:
- GitHub: https://github.com/anomalyco/opencode/issues
- OpenCode Docs: https://opencode.ai

---

## PODSUMOWANIE

**Plik do przeczytania JUTRO rano**:
```bash
/home/lukas/opencode/quizadfr/question_app/Quiz-editor-App/TODO_JUTRO.md
```

**Plik główny aplikacji**:
```bash
/home/lukas/.local/share/Trash/files/question_app/Quiz-editor-App/quiz_editor.html
```

**Wszystkie pliki .md**:
```bash
/home/lukas/opencode/quizadfr/question_app/Quiz-editor-App/*.md
```

---

Powodzenia jutro! 🚀
