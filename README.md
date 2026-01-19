<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Bai+Jamjuree:wght@400;500;600;700&amp;family=Sarabun:wght@400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Bai Jamjuree', 'Sarabun', sans-serif;
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes pulse-glow {
      0%, 100% { box-shadow: 0 0 20px rgba(59, 130, 246, 0.5); }
      50% { box-shadow: 0 0 30px rgba(59, 130, 246, 0.8); }
    }
    
    @keyframes slideUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    @keyframes confetti {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(-300px) rotate(360deg); opacity: 0; }
    }
    
    .float-anim {
      animation: float 3s ease-in-out infinite;
    }
    
    .slide-up {
      animation: slideUp 0.5s ease-out forwards;
    }
    
    .money-card {
      transition: all 0.3s ease;
    }
    
    .money-card:hover {
      transform: scale(1.05) rotate(2deg);
    }
    
    .btn-primary {
      transition: all 0.3s ease;
    }
    
    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
    }
    
    .confetti-piece {
      position: absolute;
      width: 10px;
      height: 10px;
      animation: confetti 2s ease-out forwards;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app-container" class="h-full w-full overflow-auto">
   <div class="min-h-full p-6 md:p-8"><!-- Header -->
    <header class="text-center mb-8 slide-up relative">
     <div class="absolute top-0 left-4 md:left-8 text-6xl md:text-7xl float-anim" style="animation-delay: 0.2s">
      🎀
     </div>
     <div class="absolute top-0 right-4 md:right-8 text-6xl md:text-7xl float-anim" style="animation-delay: 0.3s">
      🎀
     </div>
     <div class="inline-flex items-center gap-3 bg-white/90 backdrop-blur-sm rounded-3xl px-8 py-4 shadow-xl mb-4"><span class="text-5xl float-anim">💰</span>
      <h1 id="main-title" class="text-3xl md:text-4xl font-bold">คณิตศาสตร์การเงิน ป.5</h1><span class="text-5xl float-anim" style="animation-delay: 0.5s">🪙</span>
     </div>
     <p id="welcome-text" class="text-xl font-medium opacity-90">มาฝึกคิดเงินกันเถอะ!</p>
     <div class="mt-4 inline-block bg-white/80 backdrop-blur-sm rounded-2xl px-6 py-3 shadow-lg">
      <p id="creator-text" class="text-sm font-medium opacity-75">✨ สร้างโดย: <span class="font-semibold">เด็กชายรชตพล อ่อนล่ะมูล</span><br><span class="text-xs">ชั้น ป.5/5 สาย MEP</span></p>
     </div>
    </header><!-- Score Board -->
    <div id="score-board" class="max-w-5xl mx-auto mb-8 slide-up" style="animation-delay: 0.1s">
     <div class="bg-white rounded-3xl shadow-2xl p-6 grid grid-cols-3 gap-6">
      <div class="text-center">
       <p class="text-sm font-medium opacity-60 mb-1">คะแนน</p>
       <p id="score" class="text-4xl font-bold">0</p>
      </div>
      <div class="text-center">
       <p class="text-sm font-medium opacity-60 mb-1">ข้อที่</p>
       <p id="question-num" class="text-4xl font-bold">1</p>
      </div>
      <div class="text-center">
       <p class="text-sm font-medium opacity-60 mb-1">ถูกติดต่อกัน</p>
       <p id="streak" class="text-4xl font-bold">0</p>
      </div>
     </div>
    </div><!-- Game Mode Selection -->
    <div id="mode-selection" class="max-w-5xl mx-auto slide-up" style="animation-delay: 0.2s">
     <div class="bg-white rounded-3xl shadow-2xl p-8 md:p-10">
      <h2 class="text-2xl font-bold text-center mb-8">🎮 เลือกโหมดการเล่น</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6"><button onclick="startGame('counting')" class="btn-primary group p-8 rounded-2xl text-white shadow-xl">
        <div class="text-5xl mb-4 group-hover:scale-110 transition-transform">
         🪙
        </div><h3 id="counting-title" class="text-xl font-bold mb-2">นับเงิน</h3><p class="text-sm opacity-90">ฝึกนับธนบัตรและเหรียญ</p></button> <button onclick="startGame('change')" class="btn-primary group p-8 rounded-2xl text-white shadow-xl">
        <div class="text-5xl mb-4 group-hover:scale-110 transition-transform">
         💵
        </div><h3 id="change-title" class="text-xl font-bold mb-2">ทอนเงิน</h3><p class="text-sm opacity-90">ฝึกคิดเงินทอน</p></button> <button onclick="startGame('shopping')" class="btn-primary group p-8 rounded-2xl text-white shadow-xl">
        <div class="text-5xl mb-4 group-hover:scale-110 transition-transform">
         🛒
        </div><h3 id="shopping-title" class="text-xl font-bold mb-2">ซื้อของ</h3><p class="text-sm opacity-90">คำนวณราคาสินค้า</p></button> <button onclick="startGame('budget')" class="btn-primary group p-8 rounded-2xl text-white shadow-xl">
        <div class="text-5xl mb-4 group-hover:scale-110 transition-transform">
         📊
        </div><h3 id="budget-title" class="text-xl font-bold mb-2">วางแผนการเงิน</h3><p class="text-sm opacity-90">ฝึกจัดสรรเงินและการออม</p></button>
      </div>
     </div>
    </div><!-- Game Area -->
    <div id="game-area" class="max-w-5xl mx-auto hidden">
     <div class="bg-white rounded-3xl shadow-2xl p-8 md:p-10"><!-- Question -->
      <div id="question-container" class="mb-8">
       <h2 id="question-text" class="text-2xl font-bold text-center mb-6"></h2>
       <div id="visual-area" class="flex flex-wrap justify-center gap-3 mb-6"></div>
      </div><!-- Answer Options -->
      <div id="answer-options" class="grid grid-cols-2 gap-4 mb-8"></div><!-- Feedback -->
      <div id="feedback" class="hidden text-center p-6 rounded-2xl mb-6">
       <p id="feedback-text" class="text-2xl font-bold mb-2"></p>
       <p id="feedback-detail" class="text-base"></p>
      </div><!-- Controls -->
      <div class="flex justify-center gap-4"><button onclick="showModeSelection()" class="px-8 py-4 rounded-2xl font-semibold transition-all shadow-lg"> ���� กลับหน้าหลัก </button> <button id="next-btn" onclick="nextQuestion()" class="hidden px-8 py-4 rounded-2xl font-semibold text-white transition-all shadow-lg"> ข้อถัดไป ➡️ </button>
      </div>
     </div>
    </div><!-- Results -->
    <div id="results" class="max-w-5xl mx-auto hidden">
     <div class="bg-white rounded-3xl shadow-2xl p-10 text-center">
      <div class="text-7xl mb-6">
       🏆
      </div>
      <h2 class="text-3xl font-bold mb-3">ยอดเยี่ยม!</h2>
      <p class="text-lg opacity-70 mb-6">คุณทำครบ 10 ข้อแล้ว</p>
      <div class="rounded-2xl p-8 mb-8 shadow-inner">
       <p class="opacity-70 mb-2">คะแนนรวม</p>
       <p id="final-score" class="text-6xl font-bold mb-2">0</p>
       <p class="opacity-60">จาก 100 คะแนน</p>
      </div>
      <div id="result-message" class="text-xl mb-8"></div><button onclick="showModeSelection()" class="px-10 py-5 rounded-2xl font-bold text-white text-lg transition-all shadow-xl hover:scale-105"> 🎮 เล่นอีกครั้ง </button>
     </div>
    </div><!-- Confetti Container -->
    <div id="confetti-container" class="fixed inset-0 pointer-events-none" style="z-index: 9999;"></div>
   </div>
  </div>
  <script>
    // Default Config
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      welcome_message: 'มาฝึกคิดเงินกันเถอะ!',
      creator_name: 'เด็กชายรชตพล อ่อนล่ะมูล',
      creator_class: 'ป.5/5 สาย MEP',
      counting_title: 'นับเงิน',
      change_title: 'ทอนเงิน',
      shopping_title: 'ซื้อของ',
      budget_title: 'วางแผ���การเงิน',
      background_color: '#fef3e2',
      primary_action_color: '#f4a6d7',
      text_color: '#6b5b95',
      accent_color: '#b4a7d6',
      secondary_action_color: '#a8d8ea'
    };

    // Game State
    let currentMode = '';
    let score = 0;
    let questionNum = 1;
    let streak = 0;
    let answered = false;
    let correctAnswer = 0;

    // Money Data
    const bills = [
      { value: 1000, emoji: '💵', label: '1,000 บาท', color: '#6b7280' },
      { value: 500, emoji: '💵', label: '500 บาท', color: '#7c3aed' },
      { value: 100, emoji: '💵', label: '100 บาท', color: '#dc2626' },
      { value: 50, emoji: '💵', label: '50 บาท', color: '#2563eb' },
      { value: 20, emoji: '💵', label: '20 บาท', color: '#16a34a' }
    ];

    const coins = [
      { value: 10, emoji: '🪙', label: '10 บาท', color: '#ca8a04' },
      { value: 5, emoji: '🪙', label: '5 บาท', color: '#92400e' },
      { value: 2, emoji: '🪙', label: '2 บาท', color: '#9ca3af' },
      { value: 1, emoji: '🪙', label: '1 บาท', color: '#6b7280' }
    ];

    const items = [
      { name: 'ดินสอ', emoji: '✏️', price: 15 },
      { name: 'ยางลบ', emoji: '🧽', price: 8 },
      { name: 'ไม้บรรทัด', emoji: '📏', price: 12 },
      { name: 'สมุด', emoji: '📓', price: 25 },
      { name: 'ปากกา', emoji: '🖊️', price: 18 },
      { name: 'กล่องดินสอ', emoji: '📦', price: 45 },
      { name: 'กระเป๋า', emoji: '🎒', price: 199 },
      { name: 'ขนมปัง', emoji: '🍞', price: 25 },
      { name: 'นม', emoji: '🥛', price: 15 },
      { name: 'ไอศกรีม', emoji: '🍦', price: 20 },
      { name: 'น้ำดื่ม', emoji: '💧', price: 10 },
      { name: 'ขนม', emoji: '🍪', price: 12 }
    ];

    // SDK Integration
    async function onConfigChange(config) {
      const mainTitle = document.getElementById('main-title');
      const welcomeText = document.getElementById('welcome-text');
      const creatorText = document.getElementById('creator-text');
      const countingTitle = document.getElementById('counting-title');
      const changeTitle = document.getElementById('change-title');
      const shoppingTitle = document.getElementById('shopping-title');
      const budgetTitle = document.getElementById('budget-title');
      const appContainer = document.getElementById('app-container');
      const scoreBoard = document.getElementById('score-board');

      if (mainTitle) mainTitle.textContent = config.app_title || defaultConfig.app_title;
      if (welcomeText) welcomeText.textContent = config.welcome_message || defaultConfig.welcome_message;
      
      if (creatorText) {
        const creatorName = config.creator_name || defaultConfig.creator_name;
        const creatorClass = config.creator_class || defaultConfig.creator_class;
        creatorText.innerHTML = `✨ สร้างโดย: <span class="font-semibold">${creatorName}</span><br><span class="text-xs">ชั้น ${creatorClass}</span>`;
      }
      
      if (countingTitle) countingTitle.textContent = config.counting_title || defaultConfig.counting_title;
      if (changeTitle) changeTitle.textContent = config.change_title || defaultConfig.change_title;
      if (shoppingTitle) shoppingTitle.textContent = config.shopping_title || defaultConfig.shopping_title;
      if (budgetTitle) budgetTitle.textContent = config.budget_title || defaultConfig.budget_title;

      const bgColor = config.background_color || defaultConfig.background_color;
      const primaryColor = config.primary_action_color || defaultConfig.primary_action_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const accentColor = config.accent_color || defaultConfig.accent_color;
      const secondaryColor = config.secondary_action_color || defaultConfig.secondary_action_color;

      if (appContainer) {
        appContainer.style.background = `linear-gradient(135deg, ${bgColor} 0%, ${adjustColor(bgColor, -10)} 100%)`;
        appContainer.style.color = textColor;
      }

      if (scoreBoard) {
        const scoreEl = scoreBoard.querySelector('#score');
        const questionEl = scoreBoard.querySelector('#question-num');
        const streakEl = scoreBoard.querySelector('#streak');
        
        if (scoreEl) scoreEl.style.color = accentColor;
        if (questionEl) questionEl.style.color = primaryColor;
        if (streakEl) streakEl.style.color = '#10b981';
      }

      document.querySelectorAll('.btn-primary').forEach(btn => {
        btn.style.background = `linear-gradient(135deg, ${primaryColor} 0%, ${adjustColor(primaryColor, -20)} 100%)`;
      });

      document.querySelectorAll('#next-btn').forEach(btn => {
        btn.style.backgroundColor = accentColor;
      });

      document.querySelectorAll('#results button').forEach(btn => {
        btn.style.background = `linear-gradient(to right, ${accentColor}, ${adjustColor(accentColor, 20)})`;
      });

      const resultDiv = document.getElementById('results')?.querySelector('.rounded-2xl.p-8');
      if (resultDiv) {
        resultDiv.style.backgroundColor = adjustColor(bgColor, -5);
      }

      const backBtn = document.querySelector('button[onclick="showModeSelection()"]');
      if (backBtn && !backBtn.id) {
        backBtn.style.backgroundColor = secondaryColor;
        backBtn.style.color = '#ffffff';
      }
    }

    function adjustColor(hex, amount) {
      const num = parseInt(hex.replace('#', ''), 16);
      const r = Math.min(255, Math.max(0, (num >> 16) + amount));
      const g = Math.min(255, Math.max(0, ((num >> 8) & 0x00FF) + amount));
      const b = Math.min(255, Math.max(0, (num & 0x0000FF) + amount));
      return `#${(1 << 24 | r << 16 | g << 8 | b).toString(16).slice(1)}`;
    }

    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                config.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => config.primary_action_color || defaultConfig.primary_action_color,
              set: (value) => {
                config.primary_action_color = value;
                window.elementSdk.setConfig({ primary_action_color: value });
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                config.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => config.accent_color || defaultConfig.accent_color,
              set: (value) => {
                config.accent_color = value;
                window.elementSdk.setConfig({ accent_color: value });
              }
            },
            {
              get: () => config.secondary_action_color || defaultConfig.secondary_action_color,
              set: (value) => {
                config.secondary_action_color = value;
                window.elementSdk.setConfig({ secondary_action_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: undefined,
          fontSizeable: undefined
        }),
        mapToEditPanelValues: (config) => new Map([
          ['app_title', config.app_title || defaultConfig.app_title],
          ['welcome_message', config.welcome_message || defaultConfig.welcome_message],
          ['creator_name', config.creator_name || defaultConfig.creator_name],
          ['creator_class', config.creator_class || defaultConfig.creator_class],
          ['counting_title', config.counting_title || defaultConfig.counting_title],
          ['change_title', config.change_title || defaultConfig.change_title],
          ['shopping_title', config.shopping_title || defaultConfig.shopping_title],
          ['budget_title', config.budget_title || defaultConfig.budget_title]
        ])
      });
    }

    function startGame(mode) {
      currentMode = mode;
      score = 0;
      questionNum = 1;
      streak = 0;
      updateStats();

      document.getElementById('mode-selection').classList.add('hidden');
      document.getElementById('game-area').classList.remove('hidden');
      document.getElementById('results').classList.add('hidden');

      generateQuestion();
    }

    function showModeSelection() {
      document.getElementById('mode-selection').classList.remove('hidden');
      document.getElementById('game-area').classList.add('hidden');
      document.getElementById('results').classList.add('hidden');
    }

    function updateStats() {
      document.getElementById('score').textContent = score;
      document.getElementById('question-num').textContent = questionNum;
      document.getElementById('streak').textContent = streak;
    }

    function generateQuestion() {
      answered = false;
      document.getElementById('feedback').classList.add('hidden');
      document.getElementById('next-btn').classList.add('hidden');

      switch(currentMode) {
        case 'counting':
          generateCountingQuestion();
          break;
        case 'change':
          generateChangeQuestion();
          break;
        case 'shopping':
          generateShoppingQuestion();
          break;
        case 'budget':
          generateBudgetQuestion();
          break;
      }
    }

    function generateCountingQuestion() {
      const moneyItems = [];
      let total = 0;

      const numBills = Math.floor(Math.random() * 3) + 1;
      for (let i = 0; i < numBills; i++) {
        const bill = bills[Math.floor(Math.random() * 3) + 2];
        moneyItems.push(bill);
        total += bill.value;
      }

      const numCoins = Math.floor(Math.random() * 5) + 2;
      for (let i = 0; i < numCoins; i++) {
        const coin = coins[Math.floor(Math.random() * coins.length)];
        moneyItems.push(coin);
        total += coin.value;
      }

      document.getElementById('question-text').textContent = '💰 เงินทั้งหมดมีค����าเท่าไหร่?';

      const visualArea = document.getElementById('visual-area');
      visualArea.innerHTML = moneyItems.map((item, i) => `
        <div class="money-card flex flex-col items-center p-3 text-white rounded-xl text-sm shadow-lg" style="background-color: ${item.color}; animation-delay: ${i * 0.05}s">
          <span class="text-3xl mb-1">${item.emoji}</span>
          <span class="font-semibold">${item.value} บาท</span>
        </div>
      `).join('');

      generateOptions(total, 'บาท');
    }

    function generateChangeQuestion() {
      const prices = [23, 37, 45, 52, 68, 74, 86, 91, 127, 165];
      const payments = [50, 50, 50, 100, 100, 100, 100, 100, 200, 200];

      const idx = Math.floor(Math.random() * prices.length);
      const price = prices[idx];
      const payment = payments[idx];
      const change = payment - price;

      document.getElementById('question-text').innerHTML = `💵 ซื้อของราคา ${price} บาท จ่ายไป ${payment} บาท<br>จะได้เงินทอนเท่าไหร่?`;

      const visualArea = document.getElementById('visual-area');
      visualArea.innerHTML = `
        <div class="w-full max-w-md flex items-center justify-center gap-6">
          <div class="bg-red-100 p-6 rounded-2xl text-center flex-1 shadow-lg">
            <div class="text-3xl mb-2">🏷️</div>
            <p class="text-sm text-red-600 font-medium mb-1">ราคาสินค้า</p>
            <p class="text-3xl font-bold text-red-700">${price} บาท</p>
          </div>
          <div class="text-3xl">➡️</div>
          <div class="bg-green-100 p-6 rounded-2xl text-center flex-1 shadow-lg">
            <div class="text-3xl mb-2">💵</div>
            <p class="text-sm text-green-600 font-medium mb-1">จ่ายเงิน</p>
            <p class="text-3xl font-bold text-green-700">${payment} บาท</p>
          </div>
        </div>
      `;

      generateOptions(change, 'บาท');
    }

    function generateShoppingQuestion() {
      const numItems = Math.floor(Math.random() * 3) + 2;
      const selectedItems = [];
      let total = 0;

      const shuffled = [...items].sort(() => Math.random() - 0.5);
      for (let i = 0; i < numItems; i++) {
        const item = shuffled[i];
        const qty = Math.floor(Math.random() * 3) + 1;
        selectedItems.push({ ...item, qty });
        total += item.price * qty;
      }

      document.getElementById('question-text').textContent = '🛒 ซื้อของต่อไปนี้ ต้องจ่ายเงินทั้งหมดเท่าไหร่?';

      const visualArea = document.getElementById('visual-area');
      visualArea.innerHTML = `
        <div class="w-full max-w-2xl bg-gradient-to-br from-blue-50 to-purple-50 rounded-2xl p-6 shadow-lg">
          <div class="space-y-3">
            ${selectedItems.map(item => `
              <div class="flex justify-between items-center bg-white p-4 rounded-xl shadow-sm">
                <div class="flex items-center gap-3">
                  <span class="text-3xl">${item.emoji}</span>
                  <div>
                    <span class="font-semibold text-lg">${item.name}</span>
                    <p class="text-sm text-gray-500">${item.price} บาท × ${item.qty}</p>
                  </div>
                </div>
                <div class="text-right">
                  <span class="text-xl font-bold text-purple-600">${item.qty * item.price} บาท</span>
                </div>
              </div>
            `).join('')}
            <div class="border-t-2 border-dashed border-gray-300 pt-3 mt-3">
              <div class="text-right text-gray-500">รวมทั้งหมด = ?</div>
            </div>
          </div>
        </div>
      `;

      generateOptions(total, 'บาท');
    }

    function generateBudgetQuestion() {
      const scenarios = [
        { 
          total: 100, 
          items: [{ name: 'ขนม', price: 25 }, { name: 'น้ำ', price: 15 }, { name: 'ของเล่น', price: 30 }],
          question: 'มีเงิน 100 บาท ซื้อของตามรายการ เหลือ���งินเท่าไหร่?'
        },
        { 
          total: 200, 
          save: 40, 
          days: 5,
          question: 'ออมเงินวันละ 40 บาท นาน 5 วัน จะมีเงินออมทั้งหมดเท่าไหร่?'
        },
        { 
          total: 500, 
          percent: 20,
          question: 'มีเงิน 500 บาท ถ้าออม 20% จะออมได้เท่าไหร่?'
        },
        { 
          total: 150, 
          items: [{ name: 'อาหาร', price: 50 }, { name: 'เครื่องดื่ม', price: 20 }],
          question: 'มีเงิน 150 บาท ซื้อของตามรายการ เหลือเงินเท่าไหร่?'
        }
      ];

      const scenario = scenarios[Math.floor(Math.random() * scenarios.length)];
      let answer, visualContent;

      if (scenario.items) {
        const spent = scenario.items.reduce((sum, item) => sum + item.price, 0);
        answer = scenario.total - spent;
        visualContent = `
          <div class="w-full max-w-md space-y-4">
            <div class="bg-green-100 p-5 rounded-2xl text-center shadow-lg">
              <div class="text-3xl mb-2">💵</div>
              <p class="text-sm text-green-600 font-medium mb-1">เงินที่มี</p>
              <p class="text-3xl font-bold text-green-700">${scenario.total} บาท</p>
            </div>
            <div class="bg-red-100 p-5 rounded-2xl shadow-lg">
              <div class="text-center text-3xl mb-2">🛍️</div>
              <p class="text-sm text-red-600 font-medium text-center mb-3">ซื้อของ</p>
              ${scenario.items.map(item => `
                <div class="flex justify-between items-center bg-white/50 p-2 rounded-lg mb-2">
                  <span class="text-sm">${item.name}</span>
                  <span class="font-semibold text-red-700">${item.price} ��าท</span>
                </div>
              `).join('')}
              <div class="border-t-2 border-red-300 mt-2 pt-2 text-center">
                <span class="font-bold text-red-700">ใช้ไปรวม ${spent} บาท</span>
              </div>
            </div>
          </div>
        `;
      } else if (scenario.save) {
        answer = scenario.save * scenario.days;
        visualContent = `
          <div class="w-full max-w-md bg-gradient-to-br from-yellow-100 to-orange-100 p-8 rounded-2xl text-center shadow-lg">
            <div class="text-6xl mb-4">🐷</div>
            <p class="text-xl font-semibold text-orange-800 mb-4">กระปุกออมสิน</p>
            <div class="bg-white/70 p-4 rounded-xl mb-3">
              <p class="text-lg text-orange-700">ออมวันละ <span class="font-bold text-2xl">${scenario.save} บาท</span></p>
            </div>
            <div class="bg-white/70 p-4 rounded-xl">
              <p class="text-lg text-orange-700">เป็นเวล�� <span class="font-bold text-2xl">${scenario.days} วัน</span></p>
            </div>
          </div>
        `;
      } else {
        answer = (scenario.total * scenario.percent) / 100;
        visualContent = `
          <div class="w-full max-w-md bg-gradient-to-br from-purple-100 to-pink-100 p-8 rounded-2xl text-center shadow-lg">
            <div class="text-6xl mb-4">💰</div>
            <p class="text-xl font-semibold text-purple-800 mb-4">การออมเงิน</p>
            <div class="bg-white/70 p-4 rounded-xl mb-3">
              <p class="text-lg text-purple-700">เงินทั้งหมด <span class="font-bold text-2xl">${scenario.total} บาท</span></p>
            </div>
            <div class="bg-white/70 p-4 rounded-xl">
              <p class="text-lg text-purple-700">ออม <span class="font-bold text-2xl">${scenario.percent}%</span></p>
            </div>
          </div>
        `;
      }

      document.getElementById('question-text').innerHTML = `📊 ${scenario.question}`;
      document.getElementById('visual-area').innerHTML = visualContent;

      generateOptions(answer, 'บาท');
    }

    function generateOptions(correct, unit) {
      correctAnswer = correct;
      const options = [correct];

      while (options.length < 4) {
        const offset = Math.floor(Math.random() * 30) + 5;
        const multiplier = Math.random() < 0.5 ? -1 : 1;
        const option = correct + (offset * multiplier);
        if (option > 0 && !options.includes(option)) {
          options.push(option);
        }
      }

      options.sort(() => Math.random() - 0.5);

      const optionsContainer = document.getElementById('answer-options');
      optionsContainer.innerHTML = options.map(opt => `
        <button onclick="checkAnswer(${opt})" class="answer-btn p-6 bg-gray-100 hover:bg-blue-100 rounded-2xl font-bold text-xl transition-all hover:scale-105 border-3 border-transparent shadow-md" data-value="${opt}">
          ${opt} ${unit}
        </button>
      `).join('');
    }

    function checkAnswer(selected) {
      if (answered) return;
      answered = true;

      const buttons = document.querySelectorAll('.answer-btn');
      buttons.forEach(btn => {
        const value = parseInt(btn.dataset.value);
        btn.disabled = true;
        
        if (value === correctAnswer) {
          btn.style.backgroundColor = '#10b981';
          btn.style.color = '#ffffff';
          btn.style.transform = 'scale(1.1)';
          btn.style.boxShadow = '0 10px 30px rgba(16, 185, 129, 0.4)';
        } else if (value === selected) {
          btn.style.backgroundColor = '#ef4444';
          btn.style.color = '#ffffff';
        } else {
          btn.style.opacity = '0.4';
        }
      });

      const feedback = document.getElementById('feedback');
      const feedbackText = document.getElementById('feedback-text');
      const feedbackDetail = document.getElementById('feedback-detail');

      feedback.classList.remove('hidden');

      if (selected === correctAnswer) {
        score += 10;
        streak++;
        feedback.style.backgroundColor = '#d1fae5';
        feedback.style.border = '3px solid #10b981';
        feedbackText.textContent = '🎉 ถูกต้อง ยอดเย������ยม!';
        feedbackText.style.color = '#065f46';
        feedbackDetail.textContent = streak > 1 ? `ตอบถูกต��อเนื่อง ${streak} ข้อ! 🔥` : 'เก่งมาก เก็บคะแนน���ด้ 10 คะแนน!';
        feedbackDetail.style.color = '#059669';
        
        createConfetti();
      } else {
        streak = 0;
        feedback.style.backgroundColor = '#fee2e2';
        feedback.style.border = '3px solid #ef4444';
        feedbackText.textContent = '❌ ไม่ถูกต้อง';
        feedbackText.style.color = '#991b1b';
        feedbackDetail.textContent = `คำตอบที่ถูกคือ ${correctAnswer} บาท ลองใหม่อีกครั้งนะ!`;
        feedbackDetail.style.color = '#dc2626';
      }

      updateStats();
      document.getElementById('next-btn').classList.remove('hidden');
    }

    function createConfetti() {
      const container = document.getElementById('confetti-container');
      const colors = ['#f59e0b', '#3b82f6', '#8b5cf6', '#ec4899', '#10b981'];
      
      for (let i = 0; i < 30; i++) {
        const confetti = document.createElement('div');
        confetti.className = 'confetti-piece';
        confetti.style.left = Math.random() * 100 + '%';
        confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
        confetti.style.animationDelay = (Math.random() * 0.5) + 's';
        container.appendChild(confetti);
        
        setTimeout(() => confetti.remove(), 2000);
      }
    }

    function nextQuestion() {
      questionNum++;
      if (questionNum > 10) {
        showResults();
      } else {
        updateStats();
        generateQuestion();
      }
    }

    function showResults() {
      document.getElementById('game-area').classList.add('hidden');
      document.getElementById('results').classList.remove('hidden');
      document.getElementById('final-score').textContent = score;

      const message = document.getElementById('result-message');
      if (score >= 90) {
        message.innerHTML = '🌟 ยอดเยี่ยมมาก! คุณเป็นนักคำนวณการเงินตัวจริง!';
        message.style.color = '#059669';
        createConfetti();
      } else if (score >= 70) {
        message.innerHTML = '��� ด��มาก! คุณมีคว��มสามารถในการคิดคำนวณได้ดี!';
        message.style.color = '#2563eb';
      } else if (score >= 50) {
        message.innerHTML = '💪 ดีแล้ว! ฝึกฝนเพิ่มอีกนิดจะเก่งขึ้นแน่นอน!';
        message.style.color = '#7c3aed';
      } else {
        message.innerHTML = '📚 ลองฝึกฝนอีกครั้งนะ คราวหน้าต้องทำได้ดีขึ้นแน่!';
        message.style.color = '#dc2626';
      }
    }

    onConfigChange(defaultConfig);
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c033423f5c2732e',t:'MTc2ODc5MjkwNC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
