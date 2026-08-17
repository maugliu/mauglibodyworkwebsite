# Cowork System Prompt — mauglibodywork.com
# Вставить в Project Instructions перед началом сессии

---

<project>
Site: mauglibodywork.com
Owner: Иван («Маугли») — массажист, кинезиолог, телесный практик, Тбилиси
Stack: static HTML/CSS/JS, no frameworks, no build tools
Hosting: Cloudflare Pages → GitHub
Telegram bot: @maugli_bodywork_bot — Cloudflare Worker (repo: telegram-bot, "Telegram Bot Ver.2/src/index.js"), webhook на mauglibodywork.com/api/bot, база D1. Старый bot.py (Railway/aiogram/Python) — легаси, не используется.
</project>

<file_structure>
Корневая папка: /Users/macbookairm1/Documents/mauglibodywork.com/mauglibodyworkwebsite

КОРЕНЬ РЕПО (все файлы сайта здесь):
  index.html                 ← главная RU
  about.html
  services.html              ← ⚠ pending: вернуть фон #5C7A62 на блок цен
  contacts.html
  promo.html                 ← noindex, не в меню
  gift.html                  ← noindex, не в меню
  en/                        ← EN-версия, пути к фото через ../
    index.html, about.html, services.html, contacts.html, promo.html
    journal/                 ← посты EN (feedback, mirror-focus, morning-routine, presura)
  journal/                   ← список + посты RU (feedback, mirror-focus, morning-routine, presura)
    index.html

ФОТО (в корне репо):
  hero.jpg, hero_mobile.jpg, approach.jpg, bodypractice.jpg
  bodypractice_svc.jpg, consultation.jpg, cta_hands.jpg
  diag1.jpg, diag2.jpg, diag3.jpg, kinesio.jpg
  portrait.jpg, postnatal.jpg, warmup.jpg
  massage_certificate01-05.png
</file_structure>

<design_tokens>
Шрифты: Unbounded (заголовки, логотип, акценты) + Geologica (текст, nav)

CSS-переменные (светлая тема):
--bg: #F4EFE7
--bg-2: #FAF6F0
--bg-dark: #1A1510
--text: #1A1510
--text-soft: #2C2620
--muted: #8A7D72
--accent: #C4694A
--line: #D8CFC4
--sage: #5C7A62

Тёмная тема (DEFAULT, data-theme="dark" на <html>):
--bg:#15110D  --bg-2:#1E1A14  --bg-dark:#0B0908
--text:#F0E8DE  --accent:#D77A5B  --line:#2A241E

Nav: всегда тёмный (rgba(21,17,13,0.72) + backdrop-blur), не меняется при скролле.
Grain overlay: body::before SVG noise, opacity 0.035, mix-blend multiply — обязателен на всех страницах.
</design_tokens>

<decisions>
НЕЛЬЗЯ МЕНЯТЬ:
- Шрифты только Unbounded + Geologica
- Тёмная тема = DEFAULT, антифликер-скрипт в head
- Nav всегда тёмный (многократно проверено)
- Grain overlay на всех страницах
- Цены: фон #5C7A62 (sage), белый шрифт
- Anchor links: #intro, #warmup, #kinesiofocus, #bodypractice, #kinesio, #postnatal (обновлено 17.08.2026 — было #express/#bodypractice/#kinesio/#postnatal, сетка форматов расширена с 4 до 6)
- data-theme на <html>, не на body

УДАЛЕНО, НЕ ВОЗВРАЩАТЬ:
- Lenis smooth scroll (конфликт с мобильным)
- CSS animation-timeline: scroll() (конфликт с Lenis)
- Text Splitting / wrapWords JS (ломал DOM)
- Page loader div (вешал страницу)
- Светлый nav при скролле (элементы сливались с фоном)
</decisions>

<pending_tasks>
КРИТИЧНЫЕ:
1. services.html — вернуть фон #5C7A62 на блок цен (white text) — ПЕРВЫЙ ПРИОРИТЕТ
2. hero_mobile.jpg — проверить что лежит в корне репо; для EN путь: ../hero_mobile.jpg
3. Изображения services: проверить наличие consultation.jpg, bodypractice_svc.jpg, kinesio.jpg, postnatal.jpg

ЖЕЛАТЕЛЬНЫЕ:
4. contacts.html — заменить «Консультация 25 мин» на «Экспресс 45 мин» в тексте шагов
5. Конвертация фото в WebP (squoosh.app) → заменить src во всех img
6. Dikidi API — онлайн-запись через Cloudflare Worker (API ключ acb5e75f..., base URL уточнить)
7. EN журнал — переводы постов (начинать с presura + mirror-focus)
8. Видео в hero — 5-7 сек loop MP4, fallback на hero.jpg (обсуждалось, не реализовано)
</pending_tasks>

<rules>
- Работать только в папке /Users/macbookairm1/Documents/mauglibodywork.com/mauglibodyworkwebsite
- Перед любым ответом о конкретном файле — прочитать его
- Бот (Telegram Bot Ver.2/src/index.js) — независимо от сайта, не смешивать задачи; bot.py в том же репо больше не используется
- Новые фото для сайта → в корень репо, именование: mbw_photo_NNN.jpg
- Все страницы самодостаточны (CSS в <style>, JS в defer-скрипте внизу)
- EN страницы: пути к фото через ../ (на уровень выше)
- Посты журнала лежат в папке journal/ (и en/journal/ для EN)
</rules>

<workflow>
1. ПЛАН: список файлов которые будут изменены + почему (3–7 пунктов)
2. СТОП: ждать подтверждения («да» / «ок» / «поехали»)
3. ДЕЙСТВИЕ: внести правки, короткий отчёт после
Без подтверждения файлы не трогать, даже если задача очевидна.
Формат отчёта: Что сделано → Что НЕ сделано → Допущения
</workflow>

<style>
Отвечать на русском. Кратко, без воды.
Если видишь что-то постороннее что стоит починить — упомянуть в плане отдельным пунктом, не делать самостоятельно.
</style>

<git>
Локальная папка: /Users/macbookairm1/Documents/mauglibodywork.com/mauglibodyworkwebsite
Репозиторий: https://github.com/maugliu/mauglibodyworkwebsite.git
Ветка: main

После каждой выполненной задачи — предложить коммит:
  cd /Users/macbookairm1/Documents/mauglibodywork.com/mauglibodyworkwebsite
  git add .
  git commit -m "описание"
  git push

Правила коммитов:
- Делать ТОЛЬКО после явного подтверждения («да» / «пуш» / «коммить»)
- Сообщение на английском, коротко: тип + что именно
- Типы: fix / add / update / remove
- Примеры:
    "fix: restore sage-green background on price block"
    "update: contacts — replace consultation with express"
    "add: mbw_photo_009.jpg to photo_site"
    "fix: hero_mobile path in EN pages"
- Никогда не делать git push --force
- Никогда не менять ветку без явной команды
</git>