# Codex

Repozytorium projektu **Codex** z przygotowanym szkieletem do dalszego rozwoju, obejmującym dokumentację, kod aplikacji, dane, skrypty automatyzacji oraz środowisko deweloperskie oparte na Dev Container i Docker Compose.

## Struktura katalogów

- `.devcontainer/` – konfiguracja środowiska deweloperskiego w kontenerze.
- `src/` – kod źródłowy aplikacji.
- `docs/` – dokumentacja i zebrane informacje projektowe.
- `data/` – dane lokalne/pliki pomocnicze wykorzystywane w projekcie.
- `scripts/` – skrypty narzędziowe i automatyzujące.

## Dev Container

Wymagania:
- Docker Desktop / Docker Engine
- VS Code + rozszerzenie **Dev Containers**

Uruchomienie:
1. Skopiuj plik środowiskowy:
   ```bash
   cp .env.example .env
   ```
2. Otwórz repozytorium w VS Code.
3. Wybierz: **Dev Containers: Reopen in Container**.

Konfiguracja korzysta z Docker Compose (`docker compose`), dzięki czemu kontener deweloperski działa razem z bazą danych.

## Baza danych (Docker Compose)

Start usług:
```bash
docker compose up -d
```

Zatrzymanie usług:
```bash
docker compose down
```

Domyślne ustawienia PostgreSQL:
- host: `localhost`
- port: `5432`
- user: `codex`
- password: wartość `POSTGRES_PASSWORD` z pliku `.env`
- database: `codex`
- volume: `postgres_data`

> ⚠️ Ustaw własne, silne hasło `POSTGRES_PASSWORD` w `.env` przed uruchomieniem usług.

## Zmienne środowiskowe (OpenAI)

W projekcie używany jest plik `.env` (lokalnie, niecommitowany). Bazuj na `.env.example` i ustaw swój klucz:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

Ta zmienna będzie wykorzystywana przez komponenty aplikacji rozwijane w `src/` (np. moduły integracji z API OpenAI).

Możesz też wyeksportować zmienną w shellu:

```bash
export OPENAI_API_KEY="your_openai_api_key_here"
```
