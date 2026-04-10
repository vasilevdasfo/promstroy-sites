# 📋 ИНСТРУКЦИЯ ПО ДЕПЛОЮ PROMSTROY-SITES НА GITHUB PAGES

Репозиторий готов локально. Нужно завершить деплой на GitHub вручную.

## СТАТУС ГОТОВНОСТИ

✅ Локальный репозиторий создан: `/sessions/gallant-ecstatic-brahmagupta/promstroy-deploy/`
✅ Все 8 файлов скопированы (6 сайтов + dashboard + index)
✅ Git инициализирован, первый коммит сделан
✅ Ветка переименована в main
⏳ Нужно: создать репо на GitHub и push

## ВАРИАНТ 1: ЧЕРЕЗ GITHUB WEB UI (если нет gh CLI)

### 1. Создать репозиторий на GitHub

Переди на https://github.com/new

Заполни:
- **Repository name**: promstroy-sites
- **Description**: Promstroy sites deployment (optional)
- **Visibility**: Public
- ❌ DO NOT initialize with README (у нас уже есть)

Нажми **Create repository**

### 2. Add remote и push код

```bash
cd /sessions/gallant-ecstatic-brahmagupta/promstroy-deploy

git remote add origin https://github.com/vasilevdasfo/promstroy-sites.git
git push -u origin main
```

### 3. Включить GitHub Pages

1. Открыть репозиторий на GitHub
2. Settings → Pages (слева в меню)
3. Source: **Deploy from a branch**
4. Branch: **main** / folder: **/ (root)**
5. Нажать **Save**

GitHub Pages включится через 1-2 минуты.

**URL**: https://vasilevdasfo.github.io/promstroy-sites/

---

## ВАРИАНТ 2: ЧЕРЕЗ GITHUB CLI (быстрее, если gh установлена)

Сначала проверить, установлена ли GitHub CLI:

```bash
gh auth status
```

Если не установлена, установить:
```bash
brew install gh  # macOS
# или для Linux/Windows смотри https://cli.github.com/
```

Авторизоваться:
```bash
gh auth login
# Выбрать GitHub.com
# Authenticate Git with GitHub? Y
# Protocol: HTTPS
# Authorize with your GitHub credentials
```

Затем выполнить:

```bash
cd /sessions/gallant-ecstatic-brahmagupta/promstroy-deploy

# Создать репо на GitHub и сразу push
gh repo create vasilevdasfo/promstroy-sites \
  --public \
  --source=. \
  --push

# Включить GitHub Pages
gh api repos/vasilevdasfo/promstroy-sites/pages \
  -X POST \
  -f build_type=legacy \
  -f 'source={"branch":"main","path":"/"}'
```

Готово. Сайт заживет на https://vasilevdasfo.github.io/promstroy-sites/

---

## ПРОВЕРКА

После деплоя:

1. Открыть https://vasilevdasfo.github.io/promstroy-sites/
2. Должен загрузиться sites-dashboard.html (index.html)
3. Клики по ссылкам должны открывать каждый сайт:
   - Metal (L1/L2/L3)
   - Mangal (L1/L2/L3)
   - Promstroy

---

## ЕСЛИ ЧТО-ТО НЕ РАБОТАЕТ

Проверь статус Pages:

```bash
gh api repos/vasilevdasfo/promstroy-sites/pages
```

Если Pages ещё не запустился, подожди 2-3 минуты и обнови страницу.

Если видишь ошибку 404 — проверь:
1. Репо публичный? (Settings → General → Visibility)
2. GitHub Pages включен? (Settings → Pages → Build and deployment)
3. Ветка main есть и содержит файлы?

```bash
git remote -v
git log --oneline
```

---

## ФАЙЛЫ В РЕПО

```
promstroy-sites/
├── index.html                    ← Dashboard (главная страница)
├── sites-dashboard.html          ← Копия index.html (для архива)
├── evgeny-metal.html             ← Metal L1
├── evgeny-metal-L2.html          ← Metal L2
├── evgeny-metal-L3.html          ← Metal L3
├── evgeny-mangal.html            ← Mangal L1
├── evgeny-mangal-L2.html         ← Mangal L2
├── evgeny-mangal-L3.html         ← Mangal L3
├── pavlo-promstroy.html          ← Promstroy
├── README.md
└── DEPLOY_INSTRUCTIONS_RUS.md    ← Этот файл
```

Всё готово. Push и живи спокойно 🎯
