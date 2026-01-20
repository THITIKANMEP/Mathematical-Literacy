<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตการเงินน้อง ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Kanit', sans-serif;
    }
    .activity-card {
      transition: all 0.3s ease;
      cursor: pointer;
    }
    .activity-card:hover {
      transform: translateY(-8px) scale(1.02);
    }
    .coin-spin {
      animation: spin 2s linear infinite;
    }
    @keyframes spin {
      from { transform: rotateY(0deg); }
      to { transform: rotateY(360deg); }
    }
    .score-pop {
      animation: pop 0.5s ease;
    }
    @keyframes pop {
      0% { transform: scale(0); }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }
    .gradient-bg {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
    }
    .btn-primary {
      background: linear-gradient(135deg, #4ade80 0%, #22c55e 100%);
    }
    .btn-primary:hover {
      background: linear-gradient(135deg, #22c55e 0%, #16a34a 100%);
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body class="h-full">
  <div class="h-full overflow-auto gradient-bg"><!-- Home Screen -->
   <div id="home-screen" class="min-h-full p-6">
    <header class="text-center mb-8 pt-4">
     <div class="flex justify-center items-center gap-3 mb-3"><span class="text-6xl coin-spin">🪙</span>
      <h1 id="app-title" class="text-4xl font-bold text-white drop-shadow-lg">คณิตการเงินน้อง ป.5</h1>
     </div>
     <p id="welcome-text" class="text-xl text-white/90">มาเรียนรู้เรื่องเงินกันเถอะ!</p>
    </header>
    <main class="max-w-4xl mx-auto"><!-- Activity Cards -->
     <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8"><!-- Money Recognition -->
      <div class="activity-card bg-white rounded-3xl p-6 shadow-2xl" onclick="startActivity('money')">
       <div class="text-center">
        <div class="text-7xl mb-4">
         💵
        </div>
        <h2 class="text-2xl font-bold text-purple-700 mb-2">รู้จักธนบัตร-เหรียญ</h2>
        <p class="text-gray-600 mb-4">เรียนรู้มูลค่าของเงินบาท</p>
        <div class="bg-purple-100 rounded-2xl p-3">
         <p class="text-sm text-purple-800 font-semibold">✨ ฝึกนับเงิน</p>
        </div>
       </div>
      </div><!-- Addition -->
      <div class="activity-card bg-white rounded-3xl p-6 shadow-2xl" onclick="startActivity('add')">
       <div class="text-center">
        <div class="text-7xl mb-4">
         ➕
        </div>
        <h2 class="text-2xl font-bold text-green-700 mb-2">บวกเงิน</h2>
        <p class="text-gray-600 mb-4">ฝึกบวกเงินจากการซื้อของ</p>
        <div class="bg-green-100 rounded-2xl p-3">
         <p class="text-sm text-green-800 font-semibold">🛒 ซื้อของ</p>
        </div>
       </div>
      </div><!-- Subtraction -->
      <div class="activity-card bg-white rounded-3xl p-6 shadow-2xl" onclick="startActivity('subtract')">
       <div class="text-center">
        <div class="text-7xl mb-4">
         ➖
        </div>
        <h2 class="text-2xl font-bold text-orange-700 mb-2">ลบเงิน (เงินทอน)</h2>
        <p class="text-gray-600 mb-4">คำนวณเงินทอนจากการซื้อของ</p>
        <div class="bg-orange-100 rounded-2xl p-3">
         <p class="text-sm text-orange-800 font-semibold">💰 คิดเงินทอน</p>
        </div>
       </div>
      </div><!-- Saving -->
      <div class="activity-card bg-white rounded-3xl p-6 shadow-2xl" onclick="startActivity('saving')">
       <div class="text-center">
        <div class="text-7xl mb-4">
         🐷
        </div>
        <h2 class="text-2xl font-bold text-pink-700 mb-2">การออมเงิน</h2>
        <p class="text-gray-600 mb-4">เรียนรู้การออมเงินและวางแผน</p>
        <div class="bg-pink-100 rounded-2xl p-3">
         <p class="text-sm text-pink-800 font-semibold">🎯 ออมเป็นเป้าหมาย</p>
        </div>
       </div>
      </div>
     </div><!-- Score History -->
     <div class="bg-white/90 rounded-3xl p-6 shadow-2xl backdrop-blur">
      <h3 class="text-2xl font-bold text-purple-800 mb-4 flex items-center gap-2"><span>🏆</span> ประวัติการเล่น</h3>
      <div id="score-history" class="space-y-2">
       <p class="text-gray-500 text-center py-4">ยังไม่มีประวัติ เริ่มเล่นเลย!</p>
      </div>
     </div>
    </main>
   </div><!-- Activity Screen -->
   <div id="activity-screen" class="hidden min-h-full p-6">
    <div class="max-w-3xl mx-auto"><!-- Header -->
     <div class="flex justify-between items-center mb-6"><button onclick="goHome()" class="bg-white text-purple-700 px-6 py-3 rounded-2xl font-bold shadow-lg hover:shadow-xl transition-all"> ← กลับ </button>
      <div class="bg-white rounded-2xl px-6 py-3 shadow-lg"><span class="text-gray-600 font-semibold">คะแนน: </span> <span id="current-score" class="text-2xl font-bold text-purple-700">0</span> <span class="text-gray-600 font-semibold"> / </span> <span id="total-questions" class="text-xl font-bold text-gray-700">5</span>
      </div>
     </div><!-- Question Card -->
     <div class="bg-white rounded-3xl p-8 shadow-2xl mb-6">
      <h2 id="activity-title" class="text-3xl font-bold text-purple-800 mb-6 text-center"></h2>
      <div id="question-container" class="text-center">
       <div id="question-text" class="text-2xl font-semibold text-gray-800 mb-8"></div>
       <div id="question-visual" class="mb-8"></div>
       <div id="answer-options" class="grid grid-cols-2 gap-4"></div>
      </div>
      <div id="result-message" class="hidden mt-6 p-6 rounded-2xl text-center text-xl font-bold"></div>
     </div><!-- Progress -->
     <div class="bg-white/80 rounded-2xl p-4">
      <div class="flex gap-2 justify-center">
       <div id="progress-dots"></div>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
    const defaultConfig = {
      app_title: 'คณิตการเงินน้อง ป.5',
      welcome_text: 'มาเรียนรู้เรื่องเงินกันเถอะ!',
      primary_color: '#a855f7',
      secondary_color: '#22c55e',
      background_color: '#667eea',
      text_color: '#1f2937',
      accent_color: '#f093fb'
    };

    let currentActivity = '';
    let currentQuestion = 0;
    let score = 0;
    let questions = [];
    let activityRecords = [];

    // Money values in Thai Baht
    const moneyValues = {
      coins: [1, 2, 5, 10],
      notes: [20, 50, 100, 500, 1000]
    };

    // Data SDK Handler
    const dataHandler = {
      onDataChanged(data) {
        activityRecords = data;
        renderScoreHistory();
      }
    };

    // Initialize Data SDK
    async function initDataSdk() {
      const result = await window.dataSdk.init(dataHandler);
      if (!result.isOk) {
        console.error('Failed to initialize data SDK');
      }
    }

    // Render score history
    function renderScoreHistory() {
      const container = document.getElementById('score-history');
      if (activityRecords.length === 0) {
        container.innerHTML = '<p class="text-gray-500 text-center py-4">ยังไม่มีประวัติ เริ่มเล่นเลย!</p>';
        return;
      }

      const activityNames = {
        money: '💵 รู้จักเงิน',
        add: '➕ บวกเงิน',
        subtract: '➖ ลบเงิน',
        saving: '🐷 การออม'
      };

      const sortedRecords = [...activityRecords].sort((a, b) => 
        new Date(b.timestamp) - new Date(a.timestamp)
      ).slice(0, 5);

      container.innerHTML = sortedRecords.map(record => `
        <div class="flex justify-between items-center bg-purple-50 rounded-xl p-4">
          <span class="font-semibold text-gray-800">${activityNames[record.activity_type] || record.activity_type}</span>
          <span class="text-lg font-bold text-purple-700">${record.score}/${record.total_questions} คะแนน</span>
        </div>
      `).join('');
    }

    // Save score to Data SDK
    async function saveScore(activityType, score, totalQuestions) {
      if (activityRecords.length >= 999) {
        showMessage('บันทึกคะแนนไม่ได้ เนื่องจากถึงขีดจำกัด 999 รายการแล้ว', 'error');
        return;
      }

      const record = {
        id: Date.now().toString(),
        activity_type: activityType,
        score: score,
        total_questions: totalQuestions,
        timestamp: new Date().toISOString()
      };

      const result = await window.dataSdk.create(record);
      if (!result.isOk) {
        console.error('Failed to save score');
      }
    }

    // Show inline message
    function showMessage(message, type) {
      const resultDiv = document.getElementById('result-message');
      resultDiv.textContent = message;
      resultDiv.className = `mt-6 p-6 rounded-2xl text-center text-xl font-bold ${
        type === 'success' ? 'bg-green-100 text-green-700' : 'bg-red-100 text-red-700'
      }`;
      resultDiv.classList.remove('hidden');
      setTimeout(() => resultDiv.classList.add('hidden'), 2000);
    }

    // Start activity
    function startActivity(type) {
      currentActivity = type;
      currentQuestion = 0;
      score = 0;
      
      const titles = {
        money: '💵 รู้จักธนบัตรและเหรียญ',
        add: '➕ บวกเงิน',
        subtract: '➖ ลบเงิน (เงินทอน)',
        saving: '🐷 การออมเงิน'
      };

      document.getElementById('activity-title').textContent = titles[type];
      document.getElementById('current-score').textContent = '0';
      document.getElementById('total-questions').textContent = '5';

      generateQuestions(type);
      showQuestion();

      document.getElementById('home-screen').classList.add('hidden');
      document.getElementById('activity-screen').classList.remove('hidden');
    }

    // Generate questions
    function generateQuestions(type) {
      questions = [];
      for (let i = 0; i < 5; i++) {
        switch(type) {
          case 'money':
            questions.push(generateMoneyQuestion());
            break;
          case 'add':
            questions.push(generateAddQuestion());
            break;
          case 'subtract':
            questions.push(generateSubtractQuestion());
            break;
          case 'saving':
            questions.push(generateSavingQuestion());
            break;
        }
      }
    }

    // Generate money recognition question
    function generateMoneyQuestion() {
      const allMoney = [...moneyValues.coins, ...moneyValues.notes];
      const value = allMoney[Math.floor(Math.random() * allMoney.length)];
      const isNote = value >= 20;
      
      const emoji = isNote ? '💵' : '🪙';
      const type = isNote ? 'ธนบัตร' : 'เหรียญ';
      
      return {
        text: `${emoji} นี่คือ${type}มูลค่าเท่าไหร่?`,
        visual: `<div class="text-8xl">${emoji}</div><div class="text-4xl font-bold text-purple-600 mt-4">${value}</div>`,
        answer: value,
        options: generateOptions(value, allMoney)
      };
    }

    // Generate addition question
    function generateAddQuestion() {
      const price1 = [10, 15, 20, 25, 30, 35][Math.floor(Math.random() * 6)];
      const price2 = [5, 10, 15, 20, 25][Math.floor(Math.random() * 5)];
      const total = price1 + price2;

      return {
        text: `ซื้อขนม ${price1} บาท และน้ำ ${price2} บาท รวมเท่าไหร่?`,
        visual: `<div class="flex justify-center gap-8 text-6xl mb-4"><div>🍪<br><span class="text-2xl font-bold">${price1}฿</span></div><div>🧃<br><span class="text-2xl font-bold">${price2}฿</span></div></div>`,
        answer: total,
        options: generateOptions(total, [total - 10, total - 5, total, total + 5])
      };
    }

    // Generate subtraction question
    function generateSubtractQuestion() {
      const price = [25, 30, 35, 40, 45, 55, 65, 75][Math.floor(Math.random() * 8)];
      const paid = [50, 100][Math.floor(Math.random() * 2)];
      const change = paid - price;

      return {
        text: `ซื้อของ ${price} บาท จ่ายด้วย ${paid} บาท ได้เงินทอนเท่าไหร่?`,
        visual: `<div class="text-5xl mb-4">🛍️</div><div class="text-xl font-semibold text-gray-700">ราคา ${price} บาท<br>จ่าย ${paid} บาท</div>`,
        answer: change,
        options: generateOptions(change, [change - 10, change - 5, change, change + 5])
      };
    }

    // Generate saving question
    function generateSavingQuestion() {
      const daily = [10, 15, 20, 25, 30][Math.floor(Math.random() * 5)];
      const days = [5, 7, 10, 14][Math.floor(Math.random() * 4)];
      const total = daily * days;

      return {
        text: `ออมเงินวันละ ${daily} บาท ออมไป ${days} วัน จะได้เงินเท่าไหร่?`,
        visual: `<div class="text-7xl mb-4">🐷</div><div class="text-xl font-semibold text-pink-700">${daily} บาท/วัน × ${days} วัน</div>`,
        answer: total,
        options: generateOptions(total, [total - 20, total - 10, total, total + 10])
      };
    }

    // Generate answer options
    function generateOptions(correct, pool) {
      let opts = [correct];
      while (opts.length < 4) {
        const rand = pool[Math.floor(Math.random() * pool.length)];
        if (!opts.includes(rand) && rand > 0) {
          opts.push(rand);
        }
      }
      return opts.sort(() => Math.random() - 0.5);
    }

    // Show question
    function showQuestion() {
      if (currentQuestion >= questions.length) {
        endActivity();
        return;
      }

      const q = questions[currentQuestion];
      document.getElementById('question-text').textContent = q.text;
      document.getElementById('question-visual').innerHTML = q.visual;

      const optionsHtml = q.options.map(opt => `
        <button onclick="checkAnswer(${opt}, ${q.answer})" 
                class="bg-purple-100 hover:bg-purple-200 text-purple-800 font-bold text-2xl py-6 rounded-2xl transition-all transform hover:scale-105 shadow-lg">
          ${opt} บาท
        </button>
      `).join('');
      document.getElementById('answer-options').innerHTML = optionsHtml;

      updateProgress();
    }

    // Check answer
    function checkAnswer(selected, correct) {
      const buttons = document.querySelectorAll('#answer-options button');
      buttons.forEach(btn => btn.disabled = true);

      if (selected === correct) {
        score++;
        document.getElementById('current-score').textContent = score;
        showMessage('ถูกต้อง! เก่งมาก 🎉', 'success');
      } else {
        showMessage(`ไม่ถูกต้อง คำตอบคือ ${correct} บาท`, 'error');
      }

      setTimeout(() => {
        currentQuestion++;
        showQuestion();
      }, 2000);
    }

    // Update progress dots
    function updateProgress() {
      const dotsHtml = Array(5).fill(0).map((_, i) => {
        let color = 'bg-gray-300';
        if (i < currentQuestion) color = 'bg-green-500';
        else if (i === currentQuestion) color = 'bg-purple-500';
        return `<div class="w-12 h-12 rounded-full ${color}"></div>`;
      }).join('');
      document.getElementById('progress-dots').innerHTML = dotsHtml;
    }

    // End activity
    async function endActivity() {
      document.getElementById('question-container').innerHTML = `
        <div class="text-center score-pop">
          <div class="text-8xl mb-6">🎊</div>
          <h3 class="text-4xl font-bold text-purple-800 mb-4">เสร็จแล้ว!</h3>
          <div class="text-6xl font-bold text-green-600 mb-6">${score}/5</div>
          <p class="text-2xl text-gray-700 mb-8">${score >= 4 ? 'เก่งมาก! 🌟' : score >= 3 ? 'ดีมาก! 👍' : 'ลองใหม่อีกครั้งนะ! 💪'}</p>
          <button onclick="goHome()" class="btn-primary text-white px-8 py-4 rounded-2xl font-bold text-xl shadow-lg hover:shadow-xl transition-all">
            กลับหน้าหลัก
          </button>
        </div>
      `;

      await saveScore(currentActivity, score, 5);
    }

    // Go home
    function goHome() {
      document.getElementById('home-screen').classList.remove('hidden');
      document.getElementById('activity-screen').classList.add('hidden');
    }

    // Element SDK implementation
    async function onConfigChange(config) {
      document.getElementById('app-title').textContent = config.app_title || defaultConfig.app_title;
      document.getElementById('welcome-text').textContent = config.welcome_text || defaultConfig.welcome_text;
    }

    function mapToCapabilities(config) {
      return {
        recolorables: [],
        borderables: [],
        fontEditable: undefined,
        fontSizeable: undefined
      };
    }

    function mapToEditPanelValues(config) {
      return new Map([
        ['app_title', config.app_title || defaultConfig.app_title],
        ['welcome_text', config.welcome_text || defaultConfig.welcome_text]
      ]);
    }

    // Initialize
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }

    if (window.dataSdk) {
      initDataSdk();
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c0bbf3152b67336',t:'MTc2ODg4MjQ4Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
