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
  webinar-tejp.html          ← noindex, только по прямой ссылке, не в меню и не в sitemap
  webinar.html               ← noindex, запись на вебинар «Почувствуй своё тело» (17.10.2026),
                               собирается .claude/build/webinar_build.py, не в меню и не в sitemap
  slides/
    webinar-tejp.pdf         ← кнопка «Скачать PDF» на странице вебинара
    webinar-tejp/            ← s-01…28.jpg, 1500×844
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
  mbw_photo_001.webp — фото с афиши вебинара (герой webinar.html); og-webinar.jpg — превью
  Не используются нигде: bodypractice_svc, diag1, "Gen 4 Turbo Gentle Movement.mp4"
  hero_mobile — больше не используется (мобайл берёт hero.webp с кадром)
</file_structure>

<design_tokens>
РЕДИЗАЙН «C + маркер» (утверждён 02–04.10.2026) — перенесён на все страницы сайта
(RU, EN, журнал, promo/gift/staya_promo). Исключение — webinar-tejp.html (свой дизайн).
На promo/gift/staya_promo/en/promo заменены только шрифты и цвета (блок
«РЕДИЗАЙН 10.2026» в конце <style>), разметка и промо-механика прежние.
EN-страницы собраны из RU тем же шаблоном (одинаковые блоки), метки бота src_en_*.

Шрифты: Fira Sans Condensed 500/600/700 (заголовки КАПСОМ, логотип, метки 13px
с трекингом .14em, кнопки) + Onest 400/500/600 (текст, nav).

Тёмная тема (DEFAULT, data-theme="dark"):
--bg:#0C0C0B  --bg-2:#141413  --surface:#1F1F1C  --line:#2E2E2B
--text:#F1ECE2  --text-soft:#CFC9BE  --muted:#A9A397
--accent:#F2A93B (янтарь, заливка кнопок)  --accent-h:#E89A26  --accent-ink:#F2A93B
--on-accent:#0C0C0B (текст на янтаре — всегда тёмный)
Светлая тема (без атрибута):
--bg:#F2F1EE  --bg-2:#E8E6E1  --surface:#DEDBD4  --line:#D2CEC6
--text:#161512  --text-soft:#3A3833  --muted:#645F56
--accent-ink:#7A4706 (янтарь для ТЕКСТА на светлом — иначе нет контраста)
Общие: --paper:#F1ECE2  --flap:#262623 (плашки-флажки табло под цифрами)

Маркер: янтарная линия-подчёркивание (SVG в --marker, класс .mk), прорисовывается
при появлении блока. Только на акцентных словах в H2 ниже героя (сейчас 3 места).
В H1 героя — НЕ маркер, а цвет. Новых мест маркера не добавлять без запроса.
Фото: естественный цвет, чуть теплее (sepia .1, saturate 1.12, contrast 1.04).
Серой/обесцвеченной обработки НЕ делать. Плёночные рамки/кадры — отвергнуты.

Nav: всегда тёмный (rgba(12,12,11,0.86) + backdrop-blur) в обеих темах.
Grain overlay: body::before SVG noise, opacity 0.035 multiply (в тёмной 0.06 screen) —
обязателен на всех страницах.
Анимации: только transform/opacity/clip-path, ease-out cubic-bezier(0.23,1,0.32,1),
появление 12px + opacity; флажки переворачиваются при появлении; prefers-reduced-motion
учитывается. Без magnetic-кнопок, прожектора, бегущей строки, параллакса.
</design_tokens>

<decisions>
НЕЛЬЗЯ МЕНЯТЬ:
- Шрифты: Fira Sans Condensed + Onest (см. design_tokens). Unbounded и Geologica
  на сайте больше не используются (кроме webinar-tejp.html — там системные шрифты)
- Тёмная тема = DEFAULT, антифликер-скрипт в head. Светлая = отсутствие атрибута
  data-theme (не data-theme="light"), тёмная = data-theme="dark" на <html>
- Nav всегда тёмный (многократно проверено)
- Grain overlay на всех страницах
- Промо/QR-механика (.promo-active, ?promo=first, промо-блок, зачёркнутые цены)
  — Маугли ведёт её сам, без отдельного запроса не трогать
- Цвета в промо-ценах брать из переменных (var(--text) / var(--muted)),
  не хардкодить #fff — иначе цена пропадает в светлой теме

СЕТКА ФОРМАТОВ (обновлено 05.09.2026, 6 карточек; цены Фокус 150 / Практика 180 — с 04.10.2026):
  #intro         Знакомство / Intro Session        25 мин    100 GEL   Вход
  #kinesiofocus  Кинезио · Фокус / Kinesio·Focus   50 мин    150 GEL   Кинезио
  #bodypractice  Телесная практика / Bodywork      80 мин    180 GEL   Релакс
  #kinesio       Кинезио · Комплекс / Kinesio·Full 80 мин    200 GEL   Кинезио
  #taping        Кинезиотейпирование / Taping      по зонам  30 GEL/зона  Кинезио
  #postnatal     Восстановление после родов        2×90 мин  500 GEL   Послеродовое

ФИЛЬТРЫ (значения 05.09.2026, подписи 04.10.2026): all «Все» / entry «Первый раз» /
  relax «Расслабиться» / kinesio «Боль и скованность» / postnatal «После родов».
  data-cat-label на карточках — те же слова. data-cat многозначный, через пробел
  (матчинг: card.dataset.cat.split(' ').includes(filter)); у #taping с 04.10 только "kinesio".
  На карточке services: строка «кому подходит» (.svc-card-fit), в панели — «ближайшее
  свободное время» (первый слот из /api/slots), кнопка с меткой src_svc_<якорь>,
  строка «Отмена бесплатно за 24 часа · оплата после сеанса» (у #intro — «по предоплате»).
  Общая полоса свободных окон над сеткой остаётся. Блок противопоказаний — id="contra".

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

СТРАНИЦА ВЕБИНАРА (добавлена 10.09.2026):
- webinar-tejp.html — самодостаточная, вне общего дизайна сайта: системные шрифты,
  prefers-color-scheme вместо data-theme, без grain и без общего nav. Так и задумано,
  под токены сайта не подгонять без отдельного запроса.
- Пути в её JS жёстко зашиты: src() собирает slides/webinar-tejp/s-NN.jpg,
  кнопка PDF ведёт на slides/webinar-tejp.pdf. Файлы не переименовывать.
- В навигацию не добавлять, в sitemap не включать — доступ только по прямой ссылке.

ВЕБИНАР «ПОЧУВСТВУЙ СВОЁ ТЕЛО» (10.10.2026):
- 17.10.2026, 11:00 GMT+4 Тбилиси (10:00 Москва, 09:00 Берлин), онлайн, ~2 ч с перерывом.
  Ведущие: Иван — первая, теоретическая часть; Настя — вторая, практическая (упражнения), Иван комментирует. С собой — массажный мяч (теннисный/собачий).
- Участие за донат по желанию: две кнопки «Записаться и поддержать» / «Записаться бесплатно».
  Реквизиты получают все (у «бесплатно» свёрнуты). Без платёжных форм и выбора суммы —
  только список: TBC, BoG, ссылка Альфа-банка. Пока заглушки: DONATE в webinar_build.py
  и WEBINAR.donate в боте.
- Запись эфира — только поддержавшим (отметку supported ставит владелец); PDF — всем.
- Форма → POST /api/webinar-register → таблица webinar_regs (ключ webinar+контакт, повтор
  обновляет строку) → ссылка в бота ?start=webinar_<id>_<key> привязывает Telegram.
  Конфиг вебинара в боте — константа WEBINAR (код feel-2026-10, startsAt, platform, url).
- Этап 2 (до 16.10): напоминания за 24 ч и 1 ч, вкладка «Вебинар» в admin.html.
  Этап 3 (после 17.10): рассылка PDF всем и записи поддержавшим.

КЛАВИАТУРА БОТА (15.09.2026), MAIN_KEYBOARD, порядок кнопок:
  Записаться на сеанс · Форматы · Сайт · 🎁 Подарочный сертификат · Контакты
- Reply-клавиатура НЕ поддерживает URL-кнопки (это умеет только inline), и у одного
  сообщения может быть лишь одна reply_markup. Поэтому «Форматы» и «Сайт» — обычные
  текстовые кнопки, а сама ссылка приходит inline-кнопкой в ответном сообщении.
- Константы SITE_URL и SERVICES_URL — рядом с MAIN_KEYBOARD, ведут на
  mauglibodywork.com и mauglibodywork.com/services (чистые URL, без .html).

ГЛАВНАЯ (04.10.2026), 9 блоков: герой → полоса доверия → «С чем приходят»
(3 запроса → формат) → «Как проходит сеанс» (3 шага + принципы) → отзывы
(6 + «ещё», длинные свёрнуты) → форматы (БЕЗ цен — за ценой идут на services,
решение владельца) → обо мне коротко → FAQ → финальный CTA.
- Главная кнопка везде «Записаться» + подпись «откроется бот в Telegram».
- Метки источника в ссылках на бота: ?start=src_<место> (src_nav, src_home_hero,
  src_home_final, src_sticky, дальше src_svc_<якорь>, src_about, src_contacts,
  src_journal_<slug>; EN — src_en_…). promo_* и slot_* не трогать.
  Обработка меток в боте — отдельная задача, промт: .claude/notes/bot-prompt-start-tags.md
- Липкая кнопка «Записаться» на мобиле (≤860px), прячется, когда видна другая кнопка записи.
- Обращение «ты», но без рода: никаких «готов/уверен/устал/пришёл» о читателе.
- Пункт меню «Контакты» → «Запись и контакты» (адрес contacts.html прежний).

ЭТАП 6 (04.10.2026) — финальная проверка (accessibility-review, emil-design-eng, mobile-native, детектор impeccable):
- Ссылка «К содержанию» (#main), фокус-рамка янтарём (в светлой теме — --accent-ink), меню на мобиле:
  фокус внутрь, фон inert, Esc закрывает и возвращает фокус на бургер.
- Hover-эффекты только для мыши: @media (hover:hover) and (pointer:fine) (оборачивается автоматически при сборке).
- prefers-reduced-motion: без сдвигов, только мягкое появление opacity 200ms; view transitions отключаются.
- services: внутри кнопки карточки только span; фокус в панель при открытии с клавиатуры, Esc возвращает
  фокус на карточку; карточка не прыгает при переносе панели; hashchange открывает карточку;
  aria-live «Показано форматов: N»; ошибки промо-формы role="alert".
- Промо (с согласия владельца): строки без скидки и старые цены — цвет var(--muted) вместо opacity .5–.55
  (контраст AA), на promo/en-promo/staya_promo и services?promo=first.
- DESIGN.md в корне — описание дизайн-системы (токены + правила). Creative North Star — «Табло в тихой комнате» (утверждено).
- ВЕБИНАР: пока непубличный — noindex, без sitemap. Когда откроем: добавить текстовую версию слайдов
  и включить индексацию.
- СБОРКА: about, contacts, journal/* и все en/* собираются скриптами из index.html и services.html —
  .claude/build/ (README там). Правишь RU → пересобираешь → en_build. Руками EN не править. Последним шагом — seo.py (canonical/OG/sitemap).

КОНТАКТЫ И ФАКТЫ ДЛЯ FAQ (04.10.2026):
- Бот записи: @maugli_bodywork_bot · личный Telegram: @vanmaugli · Instagram: @maugli.bodywork
- Где: Тбилиси, Мтацминда, метро Liberty Square (улицу/дом на сайте НЕ публиковать).
- С собой: резинка для волос; сеанс в нижнем белье; полотенце на месте; одноразовые
  простыни не используются — персональная хлопковая простынка.
- Оплата: наличные или перевод, после сеанса; Знакомство — по предоплате.
- Отмена/перенос: >24 ч бесплатно, 24–12 ч 50%, позже 100%; писать в личку или боту.
- После родов: через 1–2 недели, после кесарева — когда шов заживёт, с согласия врача, без малыша.
- Знакомство засчитывается только в Телесную практику или Кинезио·Комплекс в течение 14 дней.
</decisions>

<pending_tasks>
Актуально на 15.09.2026. Закрыто ранее: фон #5C7A62, hero_mobile, фото форматов,
контакты «Экспресс», конвертация в WebP, контакты в боте (Instagram/Telegram).

БЕЗОПАСНОСТЬ (из аудита 04.09.2026):
1. ✅ 04.10.2026 — токен из .git/config убран, вход через gh, старый токен истёк.
2. ✅ 05.10.2026 — _redirects: /CLAUDE.md, /PRODUCT.md, /DESIGN.md → 301 на главную.
3. ✅ 10.10.2026 — admin.html шлёт токен в заголовке Authorization: Bearer, хранит в sessionStorage;
   ADMIN_TOKEN ротирован (владелец, wrangler secret put). ?token= из воркера убран (10.10.2026).
   ЛИДЫ (10.10.2026): повтор = счётчик hits (+ last_seen_at), ключ «tg_id + source»,
   promo_first не склеивается; владелец (OWNER_ID) в лиды не пишется. В админке — ×N,
   удаление строки и пачкой (POST /api/admin/leads/delete). Миграции бота — migrations/*.sql,
   бэкап до склейки: таблица leads_backup_20261010 (удалить, когда всё ок).
   Админку проверять только на живом сайте — с file:// запрос режется CORS и выглядит как «Неверный токен».

SEO (из аудита 04.09.2026):
4. ✅ 05.10.2026 — sitemap.xml (18 URL, RU+EN с hreflang) и свой robots.txt
   (Content-Signal: search=yes, ai-input=yes, ai-train=no; Disallow /admin.html; Sitemap).
5. ✅ 05.10.2026 — canonical (чистые URL без .html) + hreflang ru/en/x-default на основных страницах.
6. ✅ 05.10.2026 — JSON-LD HealthAndBeautyBusiness (основатель, каталог цен) на главной RU/EN.
7. ✅ 05.10.2026 — OG + Twitter на всех страницах (и на promo/gift для превью в Telegram),
   обложки og-cover.jpg / og-cover-en.jpg (1200×630, из cta_hands).
8. ✅ 04.10.2026 — en/journal/index.html: список из 4 EN-постов вместо «Coming soon».

ПРОИЗВОДИТЕЛЬНОСТЬ:
9. ✅ 05.10.2026 — фото ужаты до 2000px (сертификаты 1600px), все .webp: 10 МБ → 2 МБ.
   Оригиналы — в истории git.
10. ✅ 05.10.2026 — _headers: картинки кешируются на год (immutable).
    ПРАВИЛО: новое или заменённое фото = новое имя файла, иначе посетители увидят старое.
11. ✅ почти закрыто: новые страницы держат пропорции контейнерами (aspect-ratio),
    у ключевых фото есть width/height.

ПРОЧЕЕ:
12. ✅ 04.10.2026 — services (RU/EN) передаёт leadId в ссылку бота: ?start=promo_first_<leadId>.
13. Бот: перевести бронирование на чисто временные слоты (30/60/90 мин),
    убрать привязку к форматам. Сайт уже показывает только время.
14. ✅ 04.10.2026 — contacts переделан, подпись бота @maugli_bodywork_bot (EN — на этапе 5).
15. ✅ RU 04.10.2026 — «Разминка» убрана из шагов записи (EN — на этапе 5).
16. ✅ 04.10.2026 — строка «Разминка» убрана из promo, en/promo и staya_promo.
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

После каждого этапа, который владелец одобрил («ок», «нравится», «дальше», «готовь коммит»
и т.п.) — Claude сам обновляет CLAUDE.md, коммитит и пушит, без отдельного «да»
(решение 04.10.2026). В отчёте — хэш коммита и что в него вошло.
  git add .   (служебное — .claude/, .agents/, .impeccable/, skills-lock.json — в .gitignore)
  git commit -m "описание"
  git push    (авторизация через gh: credential helper настроен, токена в URL нет)

Правила коммитов:
- Без одобрения результата этапа — не коммитить и не пушить
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