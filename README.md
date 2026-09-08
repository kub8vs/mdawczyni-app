# mDawczyni — wdrożenie na Vercel

To jest gotowa, statyczna strona (bez backendu) — Vercel obsłuży ją od razu, bez konfiguracji.

## Struktura

```
index.html              ← cała aplikacja
manifest.webmanifest     ← plik "manifest" (żeby dało się dodać do ekranu głównego jak apkę)
sw.js                    ← Service Worker (wymagany przez Chrome/Android do trybu pełnoekranowego)
vercel.json              ← drobne ustawienia nagłówków
icons/                   ← ikony aplikacji w różnych rozmiarach
```

## Najszybszy sposób wdrożenia (bez Gita)

1. Zainstaluj Vercel CLI (jednorazowo): `npm i -g vercel`
2. W tym folderze uruchom: `vercel --prod`
3. Zaloguj się, gdy poprosi (przez przeglądarkę), zatwierdź domyślne ustawienia.
4. Po chwili dostaniesz link `https://twoj-projekt.vercel.app` — to już jest publiczny adres aplikacji.

## Alternatywnie — przez GitHub (zalecane, jeśli będziesz to jeszcze rozwijać)

1. Załóż nowe, puste repozytorium na GitHubie i wrzuć do niego zawartość tego folderu.
2. Wejdź na vercel.com → "Add New Project" → wskaż to repozytorium → Deploy (nic nie trzeba zmieniać w ustawieniach, Vercel sam rozpozna stronę statyczną).
3. Każdy kolejny `git push` będzie automatycznie aktualizował stronę na żywo.

## Jak sprawdzić, że "Dodaj do ekranu głównego" działa jak apka

1. Po wdrożeniu otwórz link **w Safari na iPhonie** (nie w Chrome — Chrome na iOS nie obsługuje instalacji do ekranu głównego jako pełnoekranowej apki, robi to tylko Safari).
2. Stuknij ikonę udostępniania (kwadrat ze strzałką) → **Dodaj do ekranu początkowego**.
3. Otwórz aplikację z nowej ikony na ekranie głównym — powinna otworzyć się na pełnym ekranie, bez paska adresu Safari.

Na Androidzie w Chrome zadziała to automatycznie (Chrome sam zaproponuje "Zainstaluj aplikację" albo zrobisz to z menu ⋮ → "Dodaj do ekranu głównego") — dzięki plikom `manifest.webmanifest` i `sw.js`.

## Uwaga

To wciąż jest **prototyp / klikalna makieta** — dane (dziennik, banki mleka, leki) są zapisane na sztywno w kodzie strony, nic nie zapisuje się na serwerze. Do prawdziwego wdrożenia produkcyjnego (realne konta, baza danych, powiadomienia push) potrzebny będzie osobny etap budowy backendu.
