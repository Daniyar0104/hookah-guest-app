[hookah-guest-app.html](https://github.com/user-attachments/files/26852930/hookah-guest-app.html)
<!DOCTYPE html>
<html lang="ru" data-theme="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Друзья Говорят — подбор кальяна</title>
  <link rel="preconnect" href="https://api.fontshare.com" />
  <link href="https://api.fontshare.com/v2/css?f[]=satoshi@400,500,700,900&display=swap" rel="stylesheet" />
  <style>
    :root, [data-theme="light"] {
      --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
      --text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
      --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
      --text-lg: clamp(1.125rem, 1rem + 0.75vw, 1.5rem);
      --text-xl: clamp(1.5rem, 1.2rem + 1.25vw, 2.25rem);
      --space-1: .25rem; --space-2: .5rem; --space-3: .75rem; --space-4: 1rem; --space-5: 1.25rem; --space-6: 1.5rem; --space-8: 2rem; --space-10: 2.5rem; --space-12: 3rem; --space-16: 4rem;
      --color-bg: #f6f0e7; --color-surface: #fffaf4; --color-surface-2: #f0e7db; --color-text: #241c15; --color-text-muted: #6c6258; --color-primary: #ac633d; --color-primary-soft: rgba(172,99,61,.11); --color-secondary: #27453e; --color-secondary-soft: rgba(39,69,62,.12); --color-border: rgba(36,28,21,.12); --color-card: rgba(255,250,244,.82);
      --radius-sm: .5rem; --radius-md: .9rem; --radius-lg: 1.25rem; --radius-xl: 1.75rem; --radius-full: 999px;
      --shadow-lg: 0 26px 80px rgba(46,32,22,.16);
      --font-body: 'Satoshi', system-ui, sans-serif;
    }
    [data-theme="dark"] {
      --color-bg: #120f0d; --color-surface: #1c1714; --color-surface-2: #261f1a; --color-text: #f3eadf; --color-text-muted: #bcae9f; --color-primary: #d78b62; --color-primary-soft: rgba(215,139,98,.14); --color-secondary: #7fb0a2; --color-secondary-soft: rgba(127,176,162,.12); --color-border: rgba(243,234,223,.1); --color-card: rgba(28,23,20,.84);
      --shadow-lg: 0 30px 90px rgba(0,0,0,.48);
    }
    *,.::before,.::after{box-sizing:border-box}
    *{box-sizing:border-box}
    body{margin:0;min-height:100dvh;font-family:var(--font-body);font-size:var(--text-base);line-height:1.55;color:var(--color-text);background:radial-gradient(circle at top left, rgba(215,139,98,.18), transparent 28%),radial-gradient(circle at 85% 20%, rgba(127,176,162,.12), transparent 24%),linear-gradient(145deg,var(--color-bg),var(--color-surface-2));}
    button,input,textarea{font:inherit} button{cursor:pointer}
    .app{min-height:100dvh;display:grid;grid-template-columns:minmax(340px,530px) 1fr}
    .panel{padding:var(--space-8);backdrop-filter:blur(18px);background:var(--color-card);border-right:1px solid var(--color-border);display:flex;flex-direction:column;gap:var(--space-6);overflow:auto}
    .result{padding:clamp(1rem,3vw,2.5rem);display:flex}
    .brand{display:flex;align-items:center;justify-content:space-between;gap:1rem}
    .brand-lockup{display:flex;align-items:center;gap:1rem}
    .brand-copy small{display:block;color:var(--color-text-muted);text-transform:uppercase;letter-spacing:.16em;font-size:var(--text-xs)}
    .brand-copy strong{display:block;font-size:1.15rem;letter-spacing:.02em}
    .logo{width:52px;height:52px;color:var(--color-primary)}
    .theme-btn,.reset-btn{min-height:44px;padding:.75rem 1rem;border-radius:var(--radius-full);border:1px solid var(--color-border);background:rgba(255,255,255,.03);color:var(--color-text)}
    h1{margin:0;font-size:var(--text-xl);line-height:1.02;max-width:12ch}
    .lead,.hero-sub,.hint,.inline-help,.stat-note,.meta{color:var(--color-text-muted)}
    .hero-card,.field,.result-card,.stat{border:1px solid var(--color-border)}
    .hero-card{padding:var(--space-6);border-radius:var(--radius-xl);background:linear-gradient(135deg,var(--color-primary-soft),rgba(255,255,255,.02));display:grid;gap:1rem}
    .hero-badges,.options{display:flex;flex-wrap:wrap;gap:.7rem}
    .hero-badge,.option-pill,.theme-btn,.reset-btn,.price-badge{border-radius:var(--radius-full)}
    .hero-badge{padding:.6rem .85rem;background:var(--color-secondary-soft);color:var(--color-text);font-size:var(--text-sm)}
    .form-grid{display:grid;gap:var(--space-5)}
    .field{padding:var(--space-5);border-radius:var(--radius-lg);background:rgba(255,255,255,.03);display:grid;gap:var(--space-4)}
    .field h2{margin:0;font-size:var(--text-lg);line-height:1.12}
    .option-pill{position:relative;min-height:48px;padding:.85rem 1rem;border:1px solid var(--color-border);background:rgba(255,255,255,.03);display:inline-flex;align-items:center;justify-content:center;text-align:center;transition:.18s ease}
    .option-pill input{position:absolute;inset:0;opacity:0}
    .option-pill.selected{background:var(--color-primary-soft);border-color:rgba(215,139,98,.42);box-shadow:inset 0 0 0 1px rgba(215,139,98,.18)}
    .option-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:.75rem}
    textarea{width:100%;min-height:110px;resize:vertical;border-radius:var(--radius-md);border:1px solid var(--color-border);background:rgba(255,255,255,.03);color:var(--color-text);padding:1rem;outline:none}
    textarea:focus{box-shadow:0 0 0 3px rgba(215,139,98,.16);border-color:rgba(215,139,98,.45)}
    .controls{display:flex;gap:.75rem;flex-wrap:wrap}
    .result-card{width:100%;min-height:calc(100dvh - 2rem);border-radius:calc(var(--radius-xl) + 10px);overflow:hidden;background:linear-gradient(180deg, rgba(215,139,98,.12), transparent 24%),linear-gradient(155deg, rgba(255,255,255,.06), rgba(255,255,255,.02)),var(--color-surface);box-shadow:var(--shadow-lg);display:grid;grid-template-rows:auto 1fr auto}
    .result-hero{padding:clamp(1.25rem,4vw,3rem);display:grid;gap:1rem;border-bottom:1px solid var(--color-border);background:linear-gradient(135deg, rgba(215,139,98,.16), rgba(127,176,162,.08))}
    .eyebrow{font-size:var(--text-xs);text-transform:uppercase;letter-spacing:.16em;color:var(--color-text-muted)}
    .hookah-name{margin:0;font-size:clamp(2rem,4.5vw,4.8rem);line-height:.95;max-width:9ch}
    .price-badge{display:inline-flex;align-items:center;width:fit-content;padding:.78rem 1rem;background:rgba(39,69,62,.16);border:1px solid rgba(127,176,162,.22);font-weight:700}
    .stats{padding:clamp(1.25rem,3vw,2.4rem);display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:1rem;align-content:start}
    .stat{padding:1rem 1.1rem;border-radius:var(--radius-lg);background:rgba(255,255,255,.03);display:grid;gap:.5rem;min-height:112px}
    .stat-label{font-size:var(--text-xs);text-transform:uppercase;letter-spacing:.08em;color:var(--color-text-muted)}
    .stat-value{font-size:clamp(1.05rem,1rem + .8vw,1.5rem);font-weight:800;line-height:1.12}
    .footer-note{padding:clamp(1.25rem,3vw,2rem);display:grid;gap:1rem;border-top:1px solid var(--color-border);background:rgba(255,255,255,.025)}
    .master-box{padding:1rem 1.1rem;border-radius:var(--radius-lg);background:var(--color-primary-soft);border:1px dashed rgba(215,139,98,.38)}
    .signature{display:grid;gap:.35rem;padding-top:.25rem}
    .signature strong{font-size:1rem}
    @media (max-width:1080px){.app{grid-template-columns:1fr}.panel{border-right:0;border-bottom:1px solid var(--color-border)}.result-card{min-height:auto}}
    @media (max-width:720px){.panel,.result{padding:1rem}.field,.hero-card{padding:1rem}.option-grid,.stats{grid-template-columns:1fr}.brand{align-items:flex-start;flex-direction:column}.hookah-name{max-width:100%}}
  </style>
</head>
<body>
  <div class="app">
    <aside class="panel">
      <div class="brand">
        <div class="brand-lockup">
          <svg class="logo" viewBox="0 0 64 64" fill="none" aria-label="Друзья Говорят">
            <circle cx="22" cy="24" r="10" stroke="currentColor" stroke-width="4"/>
            <circle cx="42" cy="24" r="10" stroke="currentColor" stroke-width="4"/>
            <path d="M18 45c3.5 4.5 8.4 7 14 7s10.5-2.5 14-7" stroke="currentColor" stroke-width="4" stroke-linecap="round"/>
            <path d="M28 24h8" stroke="currentColor" stroke-width="4" stroke-linecap="round"/>
          </svg>
          <div class="brand-copy">
            <small>Здесь ценят дружбу</small>
            <strong>Друзья Говорят</strong>
          </div>
        </div>
        <button class="theme-btn" type="button" data-theme-toggle>Тема</button>
      </div>

      <section class="hero-card">
        <div class="eyebrow">Больше чем lounge</div>
        <h1>Подбор кальяна в стиле «Друзья Говорят»</h1>
        <p class="lead">Тёплая подача, уютная атмосфера и быстрый сбор пожеланий гостя в одном экране.</p>
        <div class="hero-badges">
          <span class="hero-badge">Лаундж-бар</span>
          <span class="hero-badge">Кухня + угли + атмосфера</span>
          <span class="hero-badge">Тюмень</span>
        </div>
      </section>

      <div class="controls">
        <button class="reset-btn" type="button" id="resetBtn">Сбросить всё</button>
      </div>

      <form id="app" class="form-grid">
        <section class="field">
          <h2>Крепость</h2>
          <p class="hint">Ориентиры по крепости сохранены для понятного выбора гостя.</p>
          <div class="options" data-group="strength"></div>
        </section>

        <section class="field">
          <h2>Основной вкус</h2>
          <div class="options" data-group="profile"></div>
        </section>

        <section class="field">
          <h2>Стоп вкусы</h2>
          <p class="hint">Отметьте направления, которые лучше не использовать в миксе.</p>
          <div class="option-grid" data-group="stops"></div>
        </section>

        <section class="field">
          <h2>Добавить холодок</h2>
          <div class="options" data-group="cold"></div>
        </section>

        <section class="field">
          <h2>Стоимость кальяна</h2>
          <p class="hint">Цена зависит от типа табака и времени подачи.</p>
          <div class="option-grid" data-group="price"></div>
        </section>

        <section class="field">
          <h2>Тяга</h2>
          <div class="options" data-group="draw"></div>
        </section>

        <section class="field">
          <h2>Фольга или калауд</h2>
          <div class="options" data-group="heat"></div>
        </section>

        <section class="field">
          <h2>Когда вынести кальян</h2>
          <div class="options" data-group="timing"></div>
        </section>

        <section class="field">
          <h2>Комментарий гостя</h2>
          <p class="hint">Например: мягко, свежо, без десерта, под чай или под еду.</p>
          <textarea id="guestComment" placeholder="Введите пожелания гостя"></textarea>
        </section>
      </form>
    </aside>

    <main class="result">
      <section class="result-card" aria-live="polite">
        <div class="result-hero">
          <div class="eyebrow">Итоговый кальян</div>
          <h2 class="hookah-name" id="heroTitle">Соберите заказ</h2>
          <p class="hero-sub" id="heroText">Выберите параметры слева. Справа появится готовая карточка кальяна, которую удобно показать гостю.</p>
          <div class="price-badge" id="priceBadge">Стоимость появится после выбора</div>
        </div>

        <div class="stats" id="stats"></div>

        <div class="footer-note">
          <div class="inline-help" id="validationText">Для полной карточки выберите крепость, вкус, цену, тягу, способ прогрева и время подачи.</div>
        </div>
      </section>
    </main>
  </div>

  <script>
    const data = {
      strength: [
        { value: 'Легкое', note: 'как Старлайн' },
        { value: 'Ниже среднего', note: 'ниже Дарксайда' },
        { value: 'Среднее', note: 'как Дарксайд' },
        { value: 'Выше среднего', note: 'выше Дарксайда' },
        { value: 'Крепкое', note: 'как Сатир, Танж, Трофимов' }
      ],
      profile: ['Ягодный', 'Фруктовый', 'Цитрусовый', 'Десертный', 'Гастрономия', 'Специи', 'Цветочный', 'Травянистый', 'Алкогольный'],
      stops: ['Ягодный', 'Фруктовый', 'Цитрусовый', 'Десертный', 'Гастрономия', 'Специи', 'Цветочный', 'Травянистый', 'Алкогольный'],
      cold: ['Да', 'Нет'],
      price: [
        { value: 'Стандарт', note: 'обычный табак, не сигарный · 1100р 12:00–17:00, 1400р после' },
        { value: 'Сигарный табак', note: '1400р до 17:00, 1700р после' },
        { value: 'WTO', note: '1900р всегда' },
        { value: 'Парфюмный табак', note: '3100р' },
        { value: 'Хука сигара', note: '3100р' }
      ],
      draw: ['Легкая', 'Средняя', 'Тяжелая'],
      heat: ['Фольга', 'Калауд'],
      timing: ['Вместе с едой', 'После еды']
    };

    const state = { strength:null, profile:null, stops:[], cold:null, price:null, draw:null, heat:null, timing:null, guestComment:'' };
    const multiGroups = new Set(['stops']);

    function renderGroup(key){
      const holder = document.querySelector(`[data-group="${key}"]`);
      holder.innerHTML = '';
      data[key].forEach((item)=>{
        const obj = typeof item === 'string' ? { value:item } : item;
        const selected = multiGroups.has(key) ? state[key].includes(obj.value) : state[key] === obj.value;
        const label = document.createElement('label');
        label.className = `option-pill${selected ? ' selected' : ''}`;
        label.innerHTML = `<input type="${multiGroups.has(key) ? 'checkbox' : 'radio'}" name="${key}" value="${obj.value}" ${selected ? 'checked' : ''}><span>${obj.value}${obj.note ? `<br><small class="meta">${obj.note}</small>` : ''}</span>`;
        label.querySelector('input').addEventListener('change',()=>{
          if(multiGroups.has(key)){
            state[key] = state[key].includes(obj.value) ? state[key].filter(v=>v!==obj.value) : [...state[key], obj.value];
          } else {
            state[key] = obj.value;
          }
          renderAll();
        });
        holder.appendChild(label);
      });
    }

    const findNote = (group, value) => (data[group].find(item => typeof item === 'string' ? item === value : item.value === value)?.note) || 'Не выбрано';
    const ready = () => ['strength','profile','cold','price','draw','heat','timing'].every(key => !!state[key]);

    function renderAll(){
      Object.keys(data).forEach(renderGroup);
      state.guestComment = document.getElementById('guestComment').value.trim();
      document.getElementById('heroTitle').textContent = state.profile && state.strength ? `${state.profile} кальян ${state.cold === 'Да' ? 'с холодком' : 'без холодка'}` : 'Соберите заказ';
      document.getElementById('heroText').textContent = ready()
        ? `Готовый вариант для гостя: ${state.strength.toLowerCase()} крепость, ${state.profile.toLowerCase()} профиль, ${state.draw.toLowerCase()} тяга, ${state.heat.toLowerCase()} и подача ${state.timing.toLowerCase()}.`
        : 'Выберите параметры слева. Справа появится готовая карточка кальяна, которую удобно показать гостю.';
      document.getElementById('priceBadge').textContent = state.price ? `${state.price} — ${findNote('price', state.price)}` : 'Стоимость появится после выбора';
      const cards = [
        ['Крепость', state.strength || 'Не выбрано', findNote('strength', state.strength)],
        ['Основной вкус', state.profile || 'Не выбрано', state.stops.length ? `Исключить: ${state.stops.join(', ')}` : 'Стоп вкусы не выбраны'],
        ['Холодок', state.cold || 'Не выбрано', state.cold === 'Да' ? 'Освежающий акцент' : state.cold === 'Нет' ? 'Без охлаждающего эффекта' : 'Ожидает выбора'],
        ['Формат', state.price || 'Не выбрано', findNote('price', state.price)],
        ['Тяга', state.draw || 'Не выбрано', state.draw ? `Тяга: ${state.draw.toLowerCase()}` : 'Ожидает выбора'],
        ['Прогрев и подача', `${state.heat || 'Не выбрано'} · ${state.timing || 'Не выбрано'}`, 'Финальная сборка и вынос'],
        ['Пожелание гостя', state.guestComment ? 'Есть комментарий' : 'Без комментария', state.guestComment || 'Дополнительных пожеланий нет'],
        ['Статус', ready() ? 'Готово к приготовлению' : 'Нужны ещё ответы', ready() ? 'Можно передавать мастеру' : 'Заполните обязательные поля']
      ];
      document.getElementById('stats').innerHTML = cards.map(([label,value,note]) => `<article class="stat"><div class="stat-label">${label}</div><div class="stat-value">${value}</div><div class="stat-note">${note}</div></article>`).join('');
      document.getElementById('validationText').textContent = ready()
        ? 'Карточка готова. Покажите её гостю, затем запишите итог от мастера и сохраните скриншот.'
        : 'Для полной карточки выберите крепость, вкус, цену, тягу, способ прогрева и время подачи.';
    }

    document.getElementById('guestComment').addEventListener('input', renderAll);
    document.getElementById('resetBtn').addEventListener('click', ()=>{
      state.strength=null; state.profile=null; state.stops=[]; state.cold=null; state.price=null; state.draw=null; state.heat=null; state.timing=null; state.guestComment='';
      document.getElementById('guestComment').value='';
      renderAll();
    });
    document.querySelector('[data-theme-toggle]').addEventListener('click', ()=>{
      const root = document.documentElement;
      root.setAttribute('data-theme', root.getAttribute('data-theme') === 'dark' ? 'light' : 'dark');
    });
    renderAll();
  </script>
</body>
</html>
