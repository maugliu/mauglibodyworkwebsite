---
name: Maugli Bodywork
description: Body practice and kinesiology in Tbilisi — dark, calm, precise; amber as the only signal.
colors:
  graphite-night: "#0C0C0B"
  graphite-raised: "#141413"
  graphite-surface: "#1F1F1C"
  graphite-line: "#2E2E2B"
  flap: "#262623"
  flap-seam: "rgba(0,0,0,.85)"
  bone: "#F1ECE2"
  bone-soft: "#CFC9BE"
  stone-muted: "#A9A397"
  signal-amber: "#F2A93B"
  signal-amber-deep: "#E89A26"
  amber-ink: "#7A4706"
  daylight: "#F2F1EE"
  daylight-raised: "#E8E6E1"
  daylight-surface: "#DEDBD4"
  daylight-line: "#D2CEC6"
  ink: "#161512"
  ink-soft: "#3A3833"
  ink-muted: "#645F56"
typography:
  display:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "clamp(3.2rem, 6vw, 6rem)"
    fontWeight: 700
    lineHeight: 0.9
    letterSpacing: "0"
  page-title:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "clamp(3rem, 6vw, 5.6rem)"
    fontWeight: 700
    lineHeight: 0.92
  headline:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "clamp(2.4rem, 4.6vw, 4.2rem)"
    fontWeight: 700
    lineHeight: 0.92
  menu:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "2.2rem"
    fontWeight: 700
    lineHeight: 1
  title-lg:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "1.9rem"
    fontWeight: 700
    lineHeight: 0.98
  title:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "1.5rem"
    fontWeight: 600
    lineHeight: 1
  title-sm:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "1.25rem"
    fontWeight: 600
    lineHeight: 1.02
  body-lg:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "1.125rem"
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "1.0625rem"
    fontWeight: 400
    lineHeight: 1.6
  body-sm:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.5
  ui:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "16px"
    fontWeight: 500
  nav:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "15px"
    fontWeight: 400
  caption:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "14px"
    fontWeight: 400
  label:
    fontFamily: "Fira Sans Condensed, Arial Narrow, sans-serif"
    fontSize: "13px"
    fontWeight: 600
    letterSpacing: "0.14em"
  micro:
    fontFamily: "Onest, system-ui, sans-serif"
    fontSize: "12px"
    fontWeight: 400
rounded:
  focus: "2px"
  flap: "3px"
  card: "4px"
  bubble: "18px"
  pill: "999px"
spacing:
  gutter-desktop: "3rem"
  gutter-tablet: "2rem"
  gutter-phone: "1.25rem"
  section: "7rem"
  section-phone: "4.5rem"
components:
  button-primary:
    backgroundColor: "{colors.signal-amber}"
    textColor: "{colors.graphite-night}"
    typography: "{typography.label}"
    rounded: "{rounded.flap}"
    padding: "1.05rem 1.7rem"
  button-primary-hover:
    backgroundColor: "{colors.signal-amber-deep}"
    textColor: "{colors.graphite-night}"
  flap-tile:
    backgroundColor: "{colors.flap}"
    textColor: "{colors.bone}"
    rounded: "{rounded.flap}"
    padding: "0.3rem 0.45rem"
  card:
    backgroundColor: "{colors.graphite-surface}"
    textColor: "{colors.bone}"
    rounded: "{rounded.card}"
  chip-filter:
    textColor: "{colors.bone-soft}"
    rounded: "{rounded.pill}"
    padding: "0.65rem 1.1rem"
    height: "44px"
  chip-filter-active:
    backgroundColor: "{colors.signal-amber}"
    textColor: "{colors.graphite-night}"
  bubble-review:
    backgroundColor: "{colors.graphite-surface}"
    textColor: "{colors.bone}"
    rounded: "{rounded.bubble}"
    padding: "1rem 1.25rem"
---

# Design System: Maugli Bodywork

## Overview

**Creative North Star: «Табло в тихой комнате»**

> Страницы вне меню (promo, gift, staya_promo, en/promo) переодеты только по шрифтам и цветам — их внутренние размеры остались прежними и не являются образцом. webinar-tejp.html — вне системы.

Сайт телесной практики, который говорит языком точной информации, а не языком спа. Тёмная графитовая комната, тёплый свет фотографий, и один сигнальный цвет — янтарь, как лампа «свободно» на табло. Заголовки — узкий капс, как надписи на перекидных флажках; цифры (часы практики, номера шагов, свободное время) живут на плашках-флажках и переворачиваются, когда появляются. Всё остальное — спокойный, читаемый текст.

Плотность умеренная: большие поля, длинные паузы между блоками, один главный призыв на экран. Акцент редкий и потому заметный. Тёмная тема — по умолчанию, светлая — равноправная.

Отвергнуто владельцем: плёночные рамки и «контактный лист», серая/обесцвеченная обработка фото, терракота и Unbounded прошлой версии, бегущая строка, «магнитные» кнопки, прожектор за курсором, огромные полупрозрачные цифры, английские слова-водяные знаки.

**Key Characteristics:**
- Графит + кость + один янтарь.
- Узкий капс Fira Sans Condensed для заголовков, Onest для текста.
- Плашки-флажки для цифр и номеров.
- Живые фото в естественном тёплом цвете.
- Маркер-подчёркивание — редкий жест, не украшение.

## Colors

Почти монохромная тёплая графитовая палитра с одним сигнальным цветом.

### Primary
- **Signal Amber** (#F2A93B): заливка главных кнопок и активного фильтра, точки-«лампы» у меток, маркер-подчёркивание, акцентное слово H1 в тёмной теме. Текст на янтаре — всегда тёмный (#0C0C0B).
- **Amber Deep** (#E89A26): hover главной кнопки.
- **Amber Ink** (#7A4706): янтарь для ТЕКСТА в светлой теме (иначе нет контраста): акцент H1, имена в отзывах, «Подробнее».

### Neutral (тёмная тема, по умолчанию)
- **Graphite Night** (#0C0C0B): фон страницы, nav, футер.
- **Graphite Raised** (#141413): чередующиеся секции (отзывы, FAQ, противопоказания).
- **Graphite Surface** (#1F1F1C): карточки, пузыри-отзывы.
- **Flap** (#262623): плашки-флажки под цифрами (одинаковы в обеих темах).
- **Graphite Line** (#2E2E2B): линии и рамки.
- **Bone** (#F1ECE2) / **Bone Soft** (#CFC9BE) / **Stone Muted** (#A9A397): основной, вторичный и приглушённый текст.

### Neutral (светлая тема)
- **Daylight** (#F2F1EE), **Daylight Raised** (#E8E6E1), **Daylight Surface** (#DEDBD4), **Daylight Line** (#D2CEC6); текст **Ink** (#161512), **Ink Soft** (#3A3833), **Ink Muted** (#645F56).

### Named Rules
**The One Lamp Rule.** Янтарь — единственный цветной акцент на сайте. Никаких вторых акцентов (синего, шалфея, терракоты).
**The Dark Text on Amber Rule.** На янтарной заливке текст только тёмный (#0C0C0B), никогда белый.

## Typography

**Display Font:** Fira Sans Condensed (fallback Arial Narrow)
**Body Font:** Onest (fallback system-ui)

**Character:** узкий плотный капс звучит как табло и спортивная/техническая разметка — точно и без пафоса; Onest — мягкий современный гротеск для спокойного чтения на русском.

### Hierarchy
Шкала фиксирована — новых размеров не вводить.
- **Display** (700, clamp(3.2rem, 6vw, 6rem), 0.9, капс): H1 героя главной.
- **Page title** (700, clamp(3rem, 6vw, 5.6rem), 0.92, капс): H1 внутренних страниц.
- **Headline** (700, clamp(2.4rem, 4.6vw, 4.2rem), 0.92, капс): H2 секций на всех страницах.
- **Menu** (700, 2.2rem, капс): пункты мобильного меню.
- **Title L / Title / Title S** (1.9 / 1.5 / 1.25rem, капс): заголовки блоков-врезок / карточек и шагов / вопросов FAQ, сертификатов, каналов.
- **Body L** (400, 1.125rem, 1.6): подзаголовки-лиды, текст статей журнала (1.75), ≤36–44em.
- **Body** (400, 1.0625rem, 1.6): основной текст.
- **Body S** (400, 1rem, 1.5): текст карточек и отзывов.
- **UI** (16px): кнопки и поля ввода (16px — чтобы iOS не зумил).
- **Nav** (15px), **Caption** (14px), **Micro** (12px, минимум на сайте): навигация, подписи, время в отзывах.
- **Label** (600, 13px, трекинг 0.14em, капс): метки и «Подробнее».

### Named Rules
**The Caps Only for Short Rule.** Капс — только заголовки и метки до одной строки. Абзацы — всегда обычным регистром.

## Layout

Контейнер 1280px, поля 3rem → 2rem (≤1100px) → 1.25rem (≤860px). Секции 7rem по вертикали, 4.5rem на телефоне. Типовые сетки: 7/4 (контент + пузырь), 5/6 (фото + шаги), 4/7 (заголовок + FAQ), карточки форматов 3 → 2 → 1 колонки (1100 / 600px). Герой — две колонки, на телефоне фото сверху (78vw, ≤520px), заголовок под ним. Nav фиксированный, 64px, бургер ≤860px. На телефоне — липкая кнопка «Записаться» снизу с safe-area.

## Elevation & Depth

Плоская система без теней. Глубина — тоном: чередование Night / Raised / Surface и тонкие линии 1px. Единственное «свечение» — мягкий ореол у янтарных точек-ламп (это знак системы, не декор). Nav — полупрозрачный графит с backdrop-blur.

## Shapes

Почти прямые углы: 3px у кнопок и плашек, 4px у карточек и фото. Круглые — только пузыри-отзывы (18px с «хвостиком» 4px в углу отправителя), фильтры-пилюли и кнопка темы. Плашка-флажок: тёмный фон с тонкой горизонтальной линией посередине — как разрез перекидного табло.

## Components

### Buttons
- **Shape:** почти прямые (3px).
- **Primary:** янтарь, тёмный текст, Fira Sans Condensed 600 16px капс, трекинг 0.07em, padding 1.05rem 1.7rem. Под главной кнопкой — подпись «откроется бот в Telegram».
- **Hover / Active / Focus:** hover — Amber Deep; нажатие — scale(0.97) за 160ms; фокус — янтарный outline 2px с отступом 4px.
- **Text link:** текст + янтарная линия 1.5px снизу.

### Chips (фильтры на «Форматах»)
- **Style:** пилюля, рамка линии, текст Onest 15px, высота ≥44px; на телефоне листаются в одну строку.
- **State:** активный — янтарная заливка, тёмный текст, aria-pressed.

### Cards / Containers
- **Corner Style:** 4px. **Background:** Surface. **Border:** 1px линия, на hover/активной — янтарная.
- Карточка формата: фото 16:10 → метка-категория → название капсом → строка «кому подходит» → длительность · цена + «Подробнее».

### Inputs / Fields
- Фон страницы, рамка линии, 3px, Onest 16px (чтобы iOS не зумил); фокус — янтарная рамка.

### Navigation
- Всегда тёмная в обеих темах. Логотип капсом «MAUGLI BODYWORK» (второе слово янтарное). Ссылки Onest 15px, текущая — янтарная. Справа: «Записаться», переключатель темы, RU/EN.

### Плашка-флажок (signature)
Цифры доверия, номера шагов, номера постов, свободные окна. Тёмная плашка, светлые цифры, тонкая линия посередине; при появлении переворачивается (rotateX 85° → 0, 420ms, ease-out, ступенька 70–90ms).

### Маркер (signature)
Янтарная рукописная линия под одним акцентным словом в H2 — прорисовывается при появлении блока (900ms). Только 3 места на главной. В H1 героя — никогда (там цвет).

### Пузыри-отзывы
Отзывы клиентов — как сообщения в мессенджере: имя капсом янтарём, время мелко справа. Текст — без редактуры.

## Do's and Don'ts

### Do:
- **Do** держать янтарь единственным акцентом и ставить на него только тёмный текст.
- **Do** набирать цифры и номера на плашках-флажках, с табличными цифрами.
- **Do** показывать фото в естественном цвете, слегка теплее (sepia .1, saturate 1.12).
- **Do** кадрировать фото по рукам и телу клиента, а не по картине на стене.
- **Do** анимировать только transform / opacity / clip-path, ease-out cubic-bezier(0.23, 1, 0.32, 1), и уважать prefers-reduced-motion.
- **Do** обращаться на «ты» без рода (никаких «готов/уверен/пришёл» о читателе).

### Don't:
- **Don't** использовать серую/обесцвеченную обработку фото и плёночные рамки.
- **Don't** возвращать бегущую строку, магнитные кнопки, прожектор, параллакс, огромные полупрозрачные цифры и слова-водяные знаки.
- **Don't** добавлять новые места для маркера без запроса владельца.
- **Don't** делать nav светлым ни при скролле, ни в светлой теме.
- **Don't** использовать Lenis, animation-timeline: scroll(), разбивку текста на слова через JS и лоадер страницы.
- **Don't** ставить цены в тизеры форматов на главной — за ценой идут на страницу форматов.
