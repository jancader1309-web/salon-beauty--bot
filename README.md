# Beauty Factory AI Widget — Backend

## Pliki
- `app.py` — serwer Flask z Claude AI
- `requirements.txt` — zależności Python
- `Procfile` — konfiguracja Render.com
- `widget.html` — widget do osadzenia na stronie klienta

## Deploy na Render.com

1. Wgraj pliki na GitHub (nowe repo: `beauty-bot`)
2. Wejdź na render.com → New → Web Service
3. Połącz repo, ustaw:
   - Environment: Python
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `gunicorn app:app`
4. Dodaj zmienną środowiskową:
   - `ANTHROPIC_API_KEY` = twój klucz

## Osadzenie widgetu na stronie

W pliku `widget.html` zmień linię:
```js
const BACKEND_URL = "https://YOUR-APP.onrender.com";
```
na URL swojego serwisu z Render.com.

Następnie skopiuj kod widgetu między komentarzami
`<!-- WIDGET START -->` i `<!-- WIDGET END -->`
i wklej go w dowolne miejsce na stronie klienta.

## Endpointy
- `POST /chat` — główny endpoint czatu
  - Body: `{ "messages": [{"role": "user", "content": "..."}] }`
  - Response: `{ "reply": "..." }`
- `GET /health` — sprawdzenie statusu serwisu
