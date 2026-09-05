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
  services.html              ← форматы и цены
  contacts.html
  promo.html                 ← noindex, не в меню
  gift.html                  ← noindex, не в меню
  staya_promo.html           ← noindex, не в меню
  admin.html                 ← noindex, панель лидов, токен-авторизация
  en/                        ← EN-версия, пути к фото через ../
    index.html, about.html, services.html, contacts.html, promo.html
    journal/                 ← посты EN (feedback, mirror-focus, morning-routine, presura)
  journal/                   ← список + посты RU (feedback, mirror-focus, morning-routine, presura)
    index.html

ФОТО (в корне репо, всё в .webp):
  hero, hero_mobile, approach, bodypractice, bodypractice_svc, consultation,
  cta_hands, diag1, diag2, diag3, kinesio, portrait, postnatal, taping,
  gift-cert-bg
  massage_certificate01-05.webp
  Не используются нигде: bodypractice_svc, diag1, "Gen 4 Turbo Gentle Movement.mp4"
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
- Тёмная тема = DEFAULT, антифликер-скрипт в head. Светлая = отсутствие атрибута
  data-theme (не data-theme="light"), тёмная = data-theme="dark" на <html>
- Nav всегда тёмный (многократно проверено)
- Grain overlay на всех страницах
- Промо/QR-механика (.promo-active, ?promo=first, промо-блок, зачёркнутые цены)
  — Маугли ведёт её сам, без отдельного запроса не трогать
- Цвета в промо-ценах брать из переменных (var(--text) / var(--muted)),
  не хардкодить #fff — иначе цена пропадает в светлой теме

СЕТКА ФОРМАТОВ (обновлено 05.09.2026, 6 карточек):
  #intro         Знакомство / Intro Session        25 мин    100 GEL   Вход
  #kinesiofocus  Кинезио · Фокус / Kinesio·Focus   50 мин    140 GEL   Кинезио
  #bodypractice  Телесная практика / Bodywork      80 мин    170 GEL   Релакс
  #kinesio       Кинезио · Комплекс / Kinesio·Full 80 мин    200 GEL   Кинезио
  #taping        Кинезиотейпирование / Taping      по зонам  30 GEL/зона  Кинезио
  #postnatal     Восстановление после родов        2×90 мин  500 GEL   Послеродовое

ФИЛЬТРЫ (05.09.2026): all / entry / relax / kinesio / postnatal.
  data-cat многозначный, через пробел (у #taping — "entry kinesio"),
  матчинг в JS: card.dataset.cat.split(' ').includes(filter)

ТЕКСТЫ КАРТОЧЕК: data-desc — короткий (карточка + тизер на главной),
  data-longdesc — развёрнутый (детальная панель), фолбэк longdesc || desc

УДАЛЕНО, НЕ ВОЗВРАЩАТЬ:
- Lenis smooth scroll (конфликт с мобильным)
- CSS animation-timeline: scroll() (конфликт с Lenis)
- Text Splitting / wrapWords JS (ломал DOM)
- Page loader div (вешал страницу)
- Светлый nav при скролле (элементы сливались с фоном)
- Карточка и тизер «Разминка» (#warmup) и файл warmup.webp — удалены 05.09.2026,
  механика осталась текстом в условиях #bodypractice и #kinesio: +25 мин / 50 GEL
- SLOT_SERVICE_LABELS — слоты чисто временные, привязки к форматам нет
</decisions>

<pending_tasks>
Актуально на 05.09.2026. Закрыто ранее: фон #5C7A62, hero_mobile, фото форматов,
контакты «Экспресс», конвертация в WebP.

БЕЗОПАСНОСТЬ (из аудита 04.09.2026):
1. GitHub PAT лежит открытым текстом в .git/config (remote URL) — отозвать и
   перейти на SSH. В историю коммитов не попал.
2. CLAUDE.md публично отдаётся с сайта (mauglibodywork.com/CLAUDE.md, 200),
   репозиторий public. Внутри — префикс ключа Dikidi. Перенести в .claude/
   или закрыть через _redirects.
3. admin.html шлёт токен в query string (admin.html:437) — перенести в
   заголовок Authorization. Сам эндпоинт защищён, без токена отдаёт 401.

SEO (из аудита 04.09.2026):
4. sitemap.xml отсутствует (404). robots.txt — дефолтная заглушка Cloudflare
   без директивы Sitemap.
5. Ни canonical, ни hreflang ни на одной из 23 страниц. Cloudflare Pages при
   этом редиректит /page.html → /page (307), то есть доступны обе формы URL.
6. Schema.org нет вообще — нужен LocalBusiness + Service + Person.
7. Open Graph и Twitter Card отсутствуют везде. Критично: воронка идёт через
   Telegram, ссылка разворачивается без превью.
8. en/journal/index.html = «Coming soon», не ссылается ни на один из четырёх
   существующих EN-постов — они недостижимы для краулера.

ПРОИЗВОДИТЕЛЬНОСТЬ:
9. Картинки в исходном разрешении с камеры (portrait 6469×4313 / 1.67 MB,
   4480×6720 у нескольких). index.html тянет 4.63 MB, about.html 4.59 MB.
10. Cloudflare отдаёт .webp с cache-control: max-age=0 — нужен файл _headers
    с max-age=31536000, immutable.
11. У 48 из 50 <img> нет width/height → layout shift.

ПРОЧЕЕ:
12. Промо-форма на services.html игнорирует leadId из ответа API — ссылка на
    бота остаётся статической ?start=promo_first, в отличие от promo.html:453.
13. Бот: перевести бронирование на чисто временные слоты (30/60/90 мин),
    убрать привязку к форматам. Сайт уже показывает только время.
14. Бот (src/index.js:379): «Instagram: @mauglibodywork» устарел →
    @maugli.bodywork; «Telegram (бот): @mauglibodywork» → @maugli_bodywork_bot.
15. contacts.html:466 — подпись @mirror_focus_bot при ссылке на
    @maugli_bodywork_bot.
16. contacts.html:478 / en/contacts.html:478 — в шагах записи перечислена
    «Разминка» / «Warm-up», формата больше нет.
17. promo.html:329, en/promo.html:230, staya_promo.html:239 — ссылки на
    services.html#warmup, якоря больше нет.
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
- Перед каждым коммитом обновлять CLAUDE.md свежими данными и решениями из задания
</git>