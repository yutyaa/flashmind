
# FlashMind: AI Flashcard App (GitHub Pages + Cloudflare Worker)

## 📁 Содержимое
- `index.html` — основной интерфейс
- `worker.js` — Cloudflare Worker, скрывающий OpenRouter API-ключ

## 🚀 Как развернуть

### 1. GitHub Pages (Frontend)
1. Создай публичный репозиторий (например, `flashmind`)
2. Загрузи `index.html`
3. Включи GitHub Pages:
   - Settings → Pages → Source: `main / root`
   - Получи ссылку вроде `https://<username>.github.io/flashmind/`

### 2. Cloudflare Worker (Backend)
1. Перейди на https://dash.cloudflare.com → Workers → Create Application
2. Вставь содержимое `worker.js`
3. В разделе Settings → Variables:
   - Добавь переменную `ROUTER_API_KEY` со своим OpenRouter API ключом
4. Опубликуй и получи URL, например `https://flashmind-worker.<user>.workers.dev`

### 3. В `index.html` замени вызов API:
Найди строчку:
```js
const resp = await fetch('http://localhost:3000/quiz', { ...
```

И замени на:
```js
const resp = await fetch('https://flashmind-worker.<user>.workers.dev', { ...
```

Готово! 🎉
