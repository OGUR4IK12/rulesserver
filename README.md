<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>LunariksSMP — Правила сервера (список модов)</title>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #0c0b10;
  background-image: radial-gradient(circle at 10% 20%, rgba(210, 70, 120, 0.08) 0%, rgba(30, 20, 35, 0.4) 100%);
  font-family: 'Segoe UI', 'Inter', system-ui, -apple-system, 'Roboto', sans-serif;
  color: #f5efe7;
  padding: 2rem 1rem;
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  background: rgba(10, 8, 14, 0.7);
  backdrop-filter: blur(12px);
  border-radius: 2rem;
  border: 1px solid rgba(230, 130, 150, 0.3);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.6);
  overflow: hidden;
  padding: 1.8rem 2rem 2rem;
}

/* шапка */
.header {
  text-align: center;
  margin-bottom: 2rem;
  border-bottom: 1px solid #cc7b8e30;
  padding-bottom: 1.2rem;
}
.server-name {
  font-size: 2.6rem;
  font-weight: 800;
  letter-spacing: 2px;
  background: linear-gradient(135deg, #f3c6ad, #ec9fbb, #d67a9a);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  display: inline-flex;
  align-items: center;
  gap: 12px;
}
.server-name:before { content: "🌸"; font-size: 2rem; background: none; color: #ecb0c5; }
.server-name:after { content: "🍡"; font-size: 1.8rem; background: none; color: #ecb0c5; }
.badge {
  background: #231c24cc;
  border: 1px solid #e07c9e40;
  padding: 0.2rem 1.2rem;
  border-radius: 40px;
  display: inline-block;
  font-size: 0.75rem;
  color: #ffcfdf;
  margin-top: 10px;
}
.subhead {
  font-size: 0.85rem;
  margin-top: 0.6rem;
  color: #c9adbb;
}

/* вкладки */
.tabs {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 0.6rem;
  margin: 1.6rem 0 1.8rem;
  border-bottom: 1px solid #d97c9b30;
  padding-bottom: 0.8rem;
}
.tab-btn {
  background: rgba(30, 22, 28, 0.8);
  border: 1px solid #e0799f30;
  font-size: 1rem;
  font-weight: 600;
  padding: 0.5rem 1.5rem;
  border-radius: 40px;
  cursor: pointer;
  color: #efcddc;
  font-family: inherit;
  transition: 0.2s;
  display: inline-flex;
  align-items: center;
  gap: 8px;
}
.tab-btn:hover {
  background: #d47a9c30;
  color: #ffeef4;
  transform: translateY(-1px);
}
.tab-btn.active {
  background: linear-gradient(135deg, #c26586, #a5496b);
  color: white;
  border-color: #ffb7ce;
  box-shadow: 0 4px 12px rgba(190, 70, 100, 0.4);
}

/* контент */
.tab-content {
  display: none;
  animation: fade 0.25s ease;
}
.tab-content.active { display: block; }
@keyframes fade {
  from { opacity: 0; transform: translateY(6px);}
  to { opacity: 1; transform: translateY(0);}
}

/* карточки правил */
.rules-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.rule-item {
  background: rgba(18, 15, 22, 0.7);
  border-radius: 1.5rem;
  border: 1px solid rgba(230, 130, 155, 0.25);
  overflow: hidden;
}
.rule-header {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  padding: 1rem 1.4rem;
  cursor: pointer;
  background: rgba(0, 0, 0, 0.2);
  flex-wrap: wrap;
  gap: 10px;
}
.rule-code {
  font-family: monospace;
  font-weight: 800;
  background: #b7567c30;
  padding: 0.2rem 0.8rem;
  border-radius: 40px;
  font-size: 0.8rem;
  color: #f7bfd4;
}
.rule-title {
  font-weight: 700;
  font-size: 1rem;
  color: #f3dee8;
  flex: 1;
}
.rule-toggle {
  font-size: 0.7rem;
  background: #b7557a20;
  padding: 0.2rem 0.7rem;
  border-radius: 30px;
  color: #ffc0d4;
}
.rule-detail {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
  padding: 0 1.4rem;
  background: rgba(0, 0, 0, 0.25);
  border-top: 1px solid transparent;
}
.rule-detail.open {
  max-height: 500px;
  padding: 0.9rem 1.4rem;
  border-top-color: #de8eae40;
}
.rule-detail p {
  margin: 0.6rem 0;
  font-size: 0.85rem;
  color: #ddcfd8;
  line-height: 1.45;
}
.rule-detail strong {
  color: #f8b0ca;
}

/* список модов */
.mod-list {
  margin: 0.5rem 0 0 1.2rem;
}
.mod-list li {
  margin: 0.4rem 0;
  font-size: 0.85rem;
  color: #e5d0db;
}
.mod-category {
  font-weight: 700;
  color: #ffc0d4;
  margin-top: 0.7rem;
  margin-bottom: 0.3rem;
}

/* персонал */
.staff-grid {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.staff-card {
  background: rgba(18, 15, 22, 0.7);
  border-radius: 1.5rem;
  border: 1px solid rgba(120, 180, 220, 0.25);
  overflow: hidden;
}
.staff-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.9rem 1.4rem;
  cursor: pointer;
  background: rgba(0,0,0,0.2);
  flex-wrap: wrap;
  gap: 8px;
}
.staff-code {
  font-family: monospace;
  font-weight: bold;
  background: #3d6e8c30;
  padding: 0.2rem 0.8rem;
  border-radius: 40px;
  font-size: 0.75rem;
  color: #aad0ff;
}
.staff-name {
  font-weight: 700;
  font-size: 1rem;
  color: #cce5ff;
  display: flex;
  align-items: center;
  gap: 8px;
  flex: 1;
}
.staff-detail {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
  padding: 0 1.4rem;
  background: rgba(0, 0, 0, 0.2);
  border-top: 1px solid transparent;
}
.staff-detail.open {
  max-height: 250px;
  padding: 0.8rem 1.4rem;
  border-top-color: #6f9dcd40;
}
.staff-detail p {
  margin: 0.5rem 0;
  font-size: 0.85rem;
  display: flex;
  gap: 10px;
  align-items: baseline;
  flex-wrap: wrap;
}
.staff-detail strong {
  color: #7fc1ff;
  min-width: 110px;
}

/* заметки */
.note {
  background: rgba(255, 200, 210, 0.05);
  border-radius: 1.2rem;
  padding: 0.7rem 1rem;
  text-align: center;
  margin-top: 1.5rem;
  font-size: 0.75rem;
  border: 1px solid #dc8aaa20;
  color: #cba6bb;
}

/* футер */
footer {
  margin-top: 2rem;
  border-top: 1px solid #c77b9830;
  padding-top: 1.2rem;
}
.footer-credit {
  background: #0c0910cc;
  border-radius: 1.5rem;
  padding: 0.8rem;
  text-align: center;
  font-size: 0.7rem;
  color: #bc9aab;
}
.footer-credit p { margin: 4px 0; }
.owner-name { color: #f5b0cc; font-weight: 700; }
.notice-line {
  border-top: 1px dashed #b6628330;
  margin-top: 6px;
  padding-top: 6px;
}
.tg-link {
  text-align: center;
  margin-top: 12px;
  font-size: 0.75rem;
}
.tg-link a {
  color: #ffb7d0;
  text-decoration: none;
  border-bottom: 1px dotted #ffb0cc;
}
.tg-link a:hover { color: white; }

@media (max-width: 680px) {
  .container { padding: 1rem; }
  .server-name { font-size: 1.8rem; }
  .tab-btn { padding: 0.3rem 1rem; font-size: 0.8rem; }
}
</style>
</head>
<body>
<div class="container">
  <div class="header">
    <div class="server-name">LunariksSMP</div>
    <div class="badge">🌸 честная игра · уважение · порядок 🌸</div>
    <div class="subhead">Правила сервера | Нарушители получают бан</div>
  </div>

  <div class="tabs">
    <button class="tab-btn active" data-tab="players">🎮 Игрокам</button>
    <button class="tab-btn" data-tab="staff">🛡 Персонал</button>
    <button class="tab-btn" data-tab="builder">🏗 Билдерам</button>
    <button class="tab-btn" onclick="window.open('https://t.me/LunariksSmp','_blank')">📢 Telegram</button>
  </div>

  <!-- ВКЛАДКА: ИГРОКИ (1.1 - 1.10 + запрещённые моды) -->
  <div id="players" class="tab-content active">
    <div class="rules-list">
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.1】</span><span class="rule-title">Читы, X-Ray, автокликеры</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Запрещено:</strong> Любые программы/моды дающие преимущество (X-Ray, автокликеры, макросы, радары).</p><p><strong>Наказание:</strong> Первый раз — бан 7 дней. Повтор — перманентный бан.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.2】</span><span class="rule-title">Баги и эксплойты</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Запрещено:</strong> Использовать баги (дупликация, баги регионов). Найденный баг — сообщить администрации.</p><p><strong>Наказание:</strong> Бан до 14 дней + откат прогресса.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.3】</span><span class="rule-title">Оскорбления и токсичность</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Запрещено:</strong> Оскорбления игроков/админов, расизм, угрозы, травля.</p><p><strong>Наказание:</strong> Мут от 2 часов до 7 дней. Рецидив — вечный бан.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.4】</span><span class="rule-title">Реклама и спам</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Запрещено:</strong> Реклама других серверов, флуд, капс.</p><p><strong>Наказание:</strong> Кик + мут 1 день. Повтор — бан до 30 дней.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.5】</span><span class="rule-title">Выдача себя за администрацию</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Запрещено:</strong> Имитация ников или стиля модераторов/админов.</p><p><strong>Наказание:</strong> Перманентный бан.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.6】</span><span class="rule-title">Препятствие работе администрации</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Запрещено:</strong> Игнорирование требований, спам в тикеты, оскорбления при разбирательствах.</p><p><strong>Наказание:</strong> Варн → бан до 14 дней.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.7】</span><span class="rule-title">Гриферство</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p><strong>Разрешено:</strong> Грифер в диких зонах. <strong>Запрещено:</strong> Спавн, постройки администрации, чужие приваты.</p><p><strong>Наказание:</strong> Бан до 3 дней + возмещение ущерба.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.8】</span><span class="rule-title">PvP правила</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p>PvP разрешено везде, кроме зон восстановления (/spawn). Запрещено убивать новичков (первые 30 минут) и использовать читы в PvP.</p><p><strong>Наказание:</strong> Предупреждение или бан на 1 день.</p></div></div>
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.9】</span><span class="rule-title">Незнание правил</span><span class="rule-toggle">▼ подробнее</span></div><div class="rule-detail"><p>Незнание правил не освобождает от ответственности. Заходя на сервер, вы соглашаетесь со всеми пунктами.</p></div></div>
      
      <!-- 1.10 СПИСОК ЗАПРЕЩЁННЫХ МОДОВ -->
      <div class="rule-item"><div class="rule-header"><span class="rule-code">【1.10】</span><span class="rule-title">📛 ЗАПРЕЩЁННЫЕ МОДЫ И КЛИЕНТЫ</span><span class="rule-toggle">▼ развернуть список</span></div><div class="rule-detail">
        <p><strong>Любые моды, дающие нечестное преимущество, строго запрещены. Примеры (список не полный):</strong></p>
        <div class="mod-category">🔴 X-Ray / радар / ESP:</div>
        <ul class="mod-list"><li>X-Ray resource packs, Advanced XRay, OreRadar</li><li>Chest ESP, Entity Radar, Player Radar, Wallhack</li></ul>
        <div class="mod-category">⚡ Автокликеры / макросы / аимбот:</div>
        <ul class="mod-list"><li>Autoclicker, Macro mods (автоматизация), AimBot, KillAura, TriggerBot</li><li>AutoTool, AutoArmor, AutoFish (полностью автоматические)</li></ul>
        <div class="mod-category">🧬 Чит-клиенты:</div>
        <ul class="mod-list"><li>Wurst, Impact, Future, RusherHack, SalHack, Aristois</li><li>LiquidBounce, Inertia, Phobos, Lambda, Rise, Novoline</li><li>Любые клиенты с функцией Fly, Speed, NoFall, Scaffold, Criticals, AntiKB</li></ul>
        <div class="mod-category">🗺️ Миникарты с радаром:</div>
        <ul class="mod-list"><li>JourneyMap (с радаром сущностей), VoxelMap (режим радара), Xaero's Minimap (Radar mode)</li></ul>
        <div class="mod-category">🌿 Прочие читы:</div>
        <ul class="mod-list"><li>Freecam, GhostHand, ChestStealer, Timer, Speed, Jesus (ходьба по воде), LongJump</li></ul>
        <p><strong>Важно:</strong> Даже если мода нет в списке, но он даёт преимущество — он запрещён. Рекомендуется использовать ванильный клиент или разрешённые моды (OptiFine, Sodium, Litematica без принта).</p>
      </div></div>
    </div>
    <div class="note">🌸 Уважай других, не читерь, играй честно — и ты станешь частью лучшего комьюнити 🌸</div>
  </div>

  <!-- ВКЛАДКА: ПЕРСОНАЛ 2.1 - 2.9 -->
  <div id="staff" class="tab-content">
    <div class="staff-grid">
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.1】</span><div class="staff-name">🧪 Тестер</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Проверять новые обновления и плагины.</p><p><strong>•</strong> Сообщать о найденных багах.</p><p><strong>•</strong> Не злоупотреблять своими возможностями.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.2】</span><div class="staff-name">🛡 Младший модератор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Следить за порядком в чате, выдавать предупреждения.</p><p><strong>•</strong> Докладывать старшей администрации о серьёзных нарушениях.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.3】</span><div class="staff-name">🛡 Модератор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Следить за порядком на сервере, выдавать муты и баны (до 7 дней).</p><p><strong>•</strong> Рассматривать жалобы игроков, возвращать ущерб от гриферства.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.4】</span><div class="staff-name">🛡 Старший модератор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Контролировать работу модераторов, проверять логи.</p><p><strong>•</strong> Выдавать баны до 30 дней.</p><p><strong>•</strong> Следить за соблюдением правил персоналом.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.5】</span><div class="staff-name">⚙ Младший администратор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Помогать игрокам с техническими проблемами, следить за сервером.</p><p><strong>•</strong> Не использовать права для личной выгоды.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.6】</span><div class="staff-name">⚙ Администратор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Следить за работой модерации, выдавать баны до 90 дней.</p><p><strong>•</strong> Решать спорные ситуации, рассматривать апелляции.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.7】</span><div class="staff-name">⚙ Старший администратор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Контролировать администрацию, рассматривать жалобы на персонал.</p><p><strong>•</strong> Помогать развитию сервера, ивенты.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.8】</span><div class="staff-name">👑 Заместитель администратора</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Следить за всей администрацией, заменять главного администратора.</p><p><strong>•</strong> Решать важные вопросы сервера.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【2.9】</span><div class="staff-name">👑 Главный администратор</div><span class="rule-toggle">▼ обязанности</span></div><div class="staff-detail"><p><strong>•</strong> Управлять сервером, назначать и снимать персонал.</p><p><strong>•</strong> Изменять правила, принимать окончательные решения.</p></div></div>
    </div>
    <div class="note">⚜️ Персонал — опора сервера. Будьте справедливы и не злоупотребляйте полномочиями.</div>
  </div>

  <!-- ВКЛАДКА: БИЛДЕРЫ 3.1 - 3.4 -->
  <div id="builder" class="tab-content">
    <div class="staff-grid">
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【3.1】</span><div class="staff-name">🏗 Качество построек</div><span class="rule-toggle">▼ подробнее</span></div><div class="staff-detail"><p><strong>•</strong> Строить качественные, эстетичные постройки в стиле сервера.</p><p><strong>•</strong> Использовать WorldEdit ответственно, без ущерба для ландшафта.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【3.2】</span><div class="staff-name">🚫 Запрет на разрушение</div><span class="rule-toggle">▼ подробнее</span></div><div class="staff-detail"><p><strong>•</strong> Не ломать свои и чужие постройки без причины.</p><p><strong>•</strong> Запрещено гриферить в билдер-зонах и чужих проектах.</p><p><strong>•</strong> Нарушение = снятие роли + возможный бан.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【3.3】</span><div class="staff-name">🎨 Оформление сервера</div><span class="rule-toggle">▼ подробнее</span></div><div class="staff-detail"><p><strong>•</strong> Помогать в оформлении спавна, ивент-зон, варпов.</p><p><strong>•</strong> Согласовывать глобальные проекты с администрацией.</p></div></div>
      <div class="staff-card"><div class="staff-header"><span class="staff-code">【3.4】</span><div class="staff-name">🔧 Технические права</div><span class="rule-toggle">▼ подробнее</span></div><div class="staff-detail"><p><strong>•</strong> Доступ к WorldEdit (//wand, //set, //copy). Запрещено использовать в личных приватах для читерства.</p><p><strong>•</strong> Злоупотребление режимом творчества = лишение прав.</p></div></div>
    </div>
    <div class="note">🎋 Билдеры создают красоту сервера. Творите с душой!</div>
  </div>

  <footer>
    <div class="footer-credit">
      <p>© 2025 LunariksSMP — Создатель: <span class="owner-name">W1zixc</span></p>
      <p>Все права защищены. Любая копировка правил запрещена без согласия владельца.</p>
      <p>Обновлено: 31.10.2025</p>
      <p class="notice-line">Уведомление: LunariksSMP не связан с Mojang или Microsoft. Все права на игры и логотипы принадлежат их владельцам.</p>
    </div>
    <div class="tg-link">📢 Наш Telegram: <a href="https://t.me/LunariksSmp" target="_blank">@LunariksSmp</a></div>
  </footer>
</div>

<script>
  // переключение вкладок
  const tabBtns = document.querySelectorAll('.tab-btn[data-tab]');
  const tabs = {
    players: document.getElementById('players'),
    staff: document.getElementById('staff'),
    builder: document.getElementById('builder')
  };
  function setActiveTab(tabId) {
    for (let key in tabs) if(tabs[key]) tabs[key].classList.remove('active');
    if(tabs[tabId]) tabs[tabId].classList.add('active');
    tabBtns.forEach(btn => {
      if(btn.getAttribute('data-tab') === tabId) btn.classList.add('active');
      else btn.classList.remove('active');
    });
  }
  tabBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      const tid = btn.getAttribute('data-tab');
      if(tid && tabs[tid]) setActiveTab(tid);
    });
  });

  // аккордеон для правил игроков
  document.querySelectorAll('.rule-item .rule-header').forEach(header => {
    header.addEventListener('click', () => {
      const parent = header.closest('.rule-item');
      const detail = parent.querySelector('.rule-detail');
      const toggleSpan = header.querySelector('.rule-toggle');
      if(detail.classList.contains('open')) {
        detail.classList.remove('open');
        detail.style.maxHeight = null;
        toggleSpan.innerHTML = '▼ подробнее';
      } else {
        detail.classList.add('open');
        detail.style.maxHeight = detail.scrollHeight + 'px';
        toggleSpan.innerHTML = '▲ свернуть';
      }
    });
  });

  // аккордеон для персонала и билдеров
  document.querySelectorAll('.staff-card .staff-header').forEach(header => {
    header.addEventListener('click', () => {
      const parent = header.closest('.staff-card');
      const detail = parent.querySelector('.staff-detail');
      const toggleSpan = header.querySelector('.rule-toggle');
      if(detail.classList.contains('open')) {
        detail.classList.remove('open');
        detail.style.maxHeight = null;
        toggleSpan.innerHTML = '▼ обязанности';
      } else {
        detail.classList.add('open');
        detail.style.maxHeight = detail.scrollHeight + 'px';
        toggleSpan.innerHTML = '▲ свернуть';
      }
    });
  });

  // дефолт
  if(!document.querySelector('.tab-btn.active')) setActiveTab('players');
</script>
</body>
</html>
