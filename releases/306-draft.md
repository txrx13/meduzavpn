# MeduzaVPN 1.2.55 (306) — release draft / проект выпуска

**Status: prepared from merged source; build 306 has not been announced as published here.** The current direct-download release remains [1.2.54 (305)](1.2.54-305.md). Download links and store availability will be updated by the release publisher after the matching artifacts are published.

**Статус: проект по объединённым исходникам. Этот документ не объявляет сборку 306 выпущенной.** Текущий выпуск прямых загрузок — [1.2.54 (305)](1.2.54-305.md). Ссылки и доступность в магазинах обновляются после публикации соответствующих сборок.

## Русский

### Что подготовлено для нового выпуска

| Раздел | Изменение | Доступность |
|---|---|---|
| SHARED | Новый отдельный тариф на общем сервере: до 10 клиентов на сервер, подключение через ULTRA. PERSONAL остаётся первоначальным выбором; существующая услуга не переключается. | Реализация объединена. Продажи открываются отдельно после готовности собственного пула. |
| Выбор тарифа | Страница SHARED с подробным сравнением, компактный скидочный бейдж −66%, карточки услуг и подписок в личном кабинете. | Сайт и личный кабинет подготовлены; публикация отслеживается отдельно. |
| Цена | На сайте SHARED стоит треть цены PERSONAL за тот же срок и валюту, с округлением. При нескольких локациях итог учитывает выбранные услуги и правила соответствующего типа оплаты. | Стоимость покупки подтверждается сервером. Цена магазина показывается отдельно. |
| Покупка SHARED | Поддержка пакетов от 1 до 20 VPN, нескольких локаций, подписок, пробного периода и промокодов там, где это доступно для выбранного способа оплаты и аккаунта. | Недоступные возможности не предлагаются. Пробный период общий для аккаунта, а не новый для каждого тарифа. |
| Места подписки | Свободное оплачиваемое место можно использовать для новой услуги того же тарифа; отмена отдельного VPN сохраняет остальные услуги подписки. | По условиям подписки и доступным местам. |
| Годовой период | Выбор годового срока в эксперименте оформления и предложение годового продления подходящим пользователям месячной оплаты. | PERSONAL по умолчанию сохранён. Предложение зависит от условий аккаунта и способа оплаты. |
| Платежи | Понятный итог для нескольких услуг, восстановление доступного незавершённого платежа, история услуг и статусы оплаты. | Доступ только владельцу покупки; неподдерживаемый способ не подменяется другим. |
| Приложения | Оформление SHARED с отдельной ценой магазина, количеством и пробным периодом; текст условий отличает обычную оплату от пробной. | Реальные покупки через магазины ещё не проверены и не объявляются доступными. |
| Маршруты ULTRA | SHARED использует настройку направлений трафика; проверены подключения и маршруты по IP и домену на отдельном Android-стенде. | Проверки стенда не означают подтверждённую работу каждой платформы, сети и версии клиента. |
| Подарки и приглашения | Подарочные VPN, выбор страны получателем, новые ссылки и экраны; обновлённая реферальная программа и приглашение друга после оплаты. | Существующие покупки, получатели и ссылки сохранены. |
| Отзывы и приватность | Trustpilot загружается после отдельного согласия; согласие можно изменить или отозвать в настройках уведомлений. Тексты цели отправки приглашения на отзыв уточнены. | По умолчанию согласие выключено. |
| Админка | Отдельный SHARED pool, его настройки, список серверов, занятые и доступные места, статусы, ограничения действий и защита от устаревшего сохранения. | Готовность и включение продаж контролируются отдельно от обычного пула PERSONAL. |

### Уже было в сборке 305

Однократные покупки в разделе подписок; бесплатный тест без аккаунта на компьютерах; доступ к локальной сети при ULTRA в Windows; исправления зависшего отключения и обновления сессии; понятный выбор ULTRA для услуг с маршрутами; стабилизация бесплатного теста и Android-маршрутов через другой VPN. Это сохранённые возможности, а не новые обещания сборки 306.

### Каналы выпуска

- Прямые загрузки Android, Windows, macOS, Linux и роутеров: новая сборка публикуется только после сборки из опубликованной главной ветки и проверки артефактов. Этот проект не меняет текущие ссылки на 305.
- Apple: подготовлены отдельные продукты SHARED и региональные цены. Доступность продукта и одобрение магазина — разные этапы; новая покупка не объявляется открытой до завершения необходимых этапов. macOS App Store 1.2.53 остаётся на рассмотрении и не отменяется ради этого выпуска.
- Google Play: продукты SHARED подготовлены как черновики. Для SHARED отдельно закрыты территории IQ и JO с неподдерживаемой точностью валюты; это не отключает PERSONAL.
- Цена SHARED в App Store/Google Play определяется соответствующим магазином и регионом. Бейдж на сайте не обещает одинаковую сумму во всех магазинах.

## English

### Prepared changes

| Area | Change | Availability |
|---|---|---|
| SHARED | A separate plan on a shared server, with up to 10 clients per server and ULTRA connections. PERSONAL remains the initial choice; an existing service is not switched. | Merged implementation. Sales open separately when the dedicated shared pool is ready. |
| Plan selection | A SHARED comparison page, a compact −66% badge, and service/subscription cards in the account area. | Prepared website and account UI; publication tracked separately. |
| Pricing | Website SHARED pricing is one third of PERSONAL for the same period and currency, with rounding. Multi-location totals follow the selected services and payment model. | The server confirms the purchase amount; store prices are shown separately. |
| SHARED checkout | Support for 1–20 VPN packages, multiple locations, subscriptions, trials and promotions where supported by the payment method and account. | Unsupported choices remain unavailable. Trial eligibility is shared across the account. |
| Subscription slots | A free paid slot can create a new service of the same plan; cancelling one VPN preserves the remaining subscription services. | Subject to subscription terms and available capacity. |
| Annual plans | Annual-period checkout experiment and an annual-renewal offer for eligible monthly customers. | PERSONAL remains the default plan. Account/payment conditions apply. |
| Billing | Clear totals, recovery of eligible pending payments, service history and payment status. | Purchase-owner access; unsupported payment methods are not substituted. |
| Applications | SHARED checkout with distinct store pricing, quantity and trial selection; paid and trial disclosures are separate. | Genuine store purchases have not been verified or announced as available. |
| ULTRA routing | Traffic destinations for SHARED; connection and IP/domain routing verified on an isolated Android test setup. | This does not establish every platform, network or old client version. |
| Gifts and invitations | Gift VPNs, recipient country selection, updated links/screens, referral programme and post-payment friend invitation. | Existing purchases, recipients and links are preserved. |
| Reviews and privacy | Trustpilot loads after separate consent, which can be changed or withdrawn in notification settings; review-invitation purpose text clarified. | Consent is off by default. |
| Administration | Dedicated SHARED pool/settings/server list, capacity/status, restricted actions and protection against stale saves. | Readiness and sales activation are separate from the PERSONAL pool. |

### Already available in 305

One-time plans in Subscriptions, the account-free computer trial, Windows local-network access while ULTRA is connected, disconnect/session-refresh fixes, clear ULTRA selection for routed services, and trial/Android routing stability. These are preserved features, not new build-306 claims.

### Release channels

Direct downloads stay on 305 until matching release artifacts are published from canonical main. SHARED store products/prices are prepared; genuine store purchases are not yet verified. Apple availability and review approval are separate; macOS App Store 1.2.53 remains in review. Google SHARED products remain drafts, with IQ/JO excluded for unsupported currency precision; PERSONAL is unaffected. Final in-store pricing depends on store and region.

## Publication checklist for the release owner

- Replace draft status only after actual channel publication; do not infer publication from a merged commit, successful build or uploaded image.
- Bind checksums/download links to the current published canonical main. Rebuild if the source tip changes before publication.
- Keep SHARED sales closed until pool readiness and the applicable payment/store gates are satisfied.
- Preserve the existing Mac App Store review and distinguish real store purchases from UI/SDK fixtures.
- Update this draft with actual per-channel status; do not promise resolution of an individual support ticket from a release alone.
