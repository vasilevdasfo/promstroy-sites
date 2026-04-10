# Promstroy Sites Deployment

Репозиторий для GitHub Pages деплоя сайтов Евгения Бычковского.

## Структура

- `index.html` — главная навигация (копия sites-dashboard.html)
- `evgeny-metal.html` — сайт Metal компании Евгения (L1 уровень)
- `evgeny-metal-L2.html` — сайт Metal (L2 premium уровень)
- `evgeny-metal-L3.html` — сайт Metal (L3 cinematic уровень)
- `evgeny-mangal.html` — сайт Mangal компании Евгения (L1 уровень)
- `evgeny-mangal-L2.html` — сайт Mangal (L2 premium уровень)
- `evgeny-mangal-L3.html` — сайт Mangal (L3 cinematic уровень)
- `pavlo-promstroy.html` — сайт Promstroy компании Павла
- `sites-dashboard.html` — дашборд со ссылками на все сайты

## Деплой на GitHub Pages

### Шаг 1. Создать репозиторий на GitHub

Зайти на https://github.com/new

Заполнить:
- Repository name: `promstroy-sites`
- Description: `Promstroy sites deployment`
- Public
- Initialize with README? **NO** (уже есть)

Нажать Create repository.

### Шаг 2. Добавить remote и push

```bash
cd /sessions/gallant-ecstatic-brahmagupta/promstroy-deploy

# Добавить remote (замени USERNAME на твой GitHub username, должно быть vasilevdasfo)
git remote add origin https://github.com/vasilevdasfo/promstroy-sites.git

# Push на GitHub
git branch -M main
git push -u origin main
```

### Шаг 3. Включить GitHub Pages

Зайти в репозиторий → Settings → Pages

Выбрать:
- Build and deployment → Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/ (root)**

Нажать Save.

### Шаг 4. Дождаться деплоя

GitHub Pages будет готов через 1-2 минуты. 

URL сайта: `https://vasilevdasfo.github.io/promstroy-sites/`

## Альтернатива: использовать GitHub CLI (быстрее)

Если у тебя установлена GitHub CLI (`gh`), можно через неё:

```bash
cd /sessions/gallant-ecstatic-brahmagupta/promstroy-deploy

# Создать репозиторий и сразу push
gh repo create vasilevdasfo/promstroy-sites --public --source=. --push

# Включить GitHub Pages
gh api repos/vasilevdasfo/promstroy-sites/pages -X POST \
  -f build_type=legacy \
  -f 'source={"branch":"main","path":"/"}'

# Проверить статус
gh api repos/vasilevdasfo/promstroy-sites/pages
```

Всё готово. Репо находится в `/sessions/gallant-ecstatic-brahmagupta/promstroy-deploy/`.
