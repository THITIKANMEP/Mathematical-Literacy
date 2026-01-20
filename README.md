<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
    }
    * {
      font-family: 'Prompt', sans-serif;
    }
    .calculator-card {
      backdrop-filter: blur(10px);
      transition: all 0.3s ease;
    }
    .calculator-card:hover {
      transform: translateY(-4px);
    }
    .tab-btn.active {
      background: linear-gradient(135deg, #059669 0%, #10b981 100%);
      color: white;
    }
    .input-field:focus {
      box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.2);
    }
    .result-box {
      background: linear-gradient(135deg, #ecfdf5 0%, #d1fae5 100%);
      animation: fadeIn 0.4s ease;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.95); }
      to { opacity: 1; transform: scale(1); }
    }
    .gradient-bg {
      background: linear-gradient(135deg, #064e3b 0%, #047857 50%, #10b981 100%);
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full bg-gray-50">
  <div class="h-full overflow-auto">
   <div class="gradient-bg min-h-full"><!-- Header -->
    <header class="pt-8 pb-6 px-4 text-center">
     <div class="flex items-center justify-center gap-3 mb-2">
      <svg class="w-10 h-10 text-emerald-200" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      <h1 id="app-title" class="text-3xl font-bold text-white">คณิตศาสตร์การเงิน</h1>
     </div>
     <p class="text-emerald-200 text-sm">เครื่องมือคำนวณทางการเงินครบวงจร</p>
    </header><!-- Tab Navigation -->
    <nav class="px-4 pb-4">
     <div class="flex flex-wrap justify-center gap-2 max-w-3xl mx-auto"><button class="tab-btn active px-4 py-2 rounded-full text-sm font-medium bg-white/20 text-white transition-all" data-tab="compound">ดอกเบี้ยทบต้น</button> <button class="tab-btn px-4 py-2 rounded-full text-sm font-medium bg-white/20 text-white transition-all" data-tab="loan">สินเชื่อ/ผ่อนชำระ</button> <button class="tab-btn px-4 py-2 rounded-full text-sm font-medium bg-white/20 text-white transition-all" data-tab="savings">เป้าหมายออมเงิน</button> <button class="tab-btn px-4 py-2 rounded-full text-sm font-medium bg-white/20 text-white transition-all" data-tab="roi">ผลตอบแทนการลงทุน</button> <button class="tab-btn px-4 py-2 rounded-full text-sm font-medium bg-white/20 text-white transition-all" data-tab="inflation">มูลค่าเงินตามเวลา</button>
     </div>
    </nav><!-- Calculator Sections -->
    <main class="px-4 pb-8">
     <div class="max-w-2xl mx-auto"><!-- Compound Interest -->
      <section id="compound" class="calculator-card bg-white rounded-2xl p-6 shadow-xl">
       <div class="flex items-center gap-3 mb-6">
        <div class="w-12 h-12 rounded-xl bg-emerald-100 flex items-center justify-center"><span class="text-2xl">📈</span>
        </div>
        <div>
         <h2 class="text-xl font-semibold text-gray-800">คำนวณดอกเบี้ยทบต้น</h2>
         <p class="text-sm text-gray-500">คำนวณผลตอบแทนจากการออมหรือลงทุน</p>
        </div>
       </div>
       <div class="space-y-4">
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="principal">เงินต้น (บาท)</label> <input type="number" id="principal" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-emerald-500 outline-none transition" placeholder="100,000">
        </div>
        <div class="grid grid-cols-2 gap-4">
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="rate">อัตราดอกเบี้ย (%/ปี)</label> <input type="number" id="rate" step="0.01" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-emerald-500 outline-none transition" placeholder="5">
         </div>
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="years">ระยะเวลา (ปี)</label> <input type="number" id="years" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-emerald-500 outline-none transition" placeholder="10">
         </div>
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="compound-freq">ความถี่ทบต้น</label> <select id="compound-freq" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-emerald-500 outline-none transition bg-white"> <option value="1">ปีละครั้ง</option> <option value="2">ปีละ 2 ครั้ง</option> <option value="4">ปีละ 4 ครั้ง (รายไตรมาส)</option> <option value="12" selected>ปีละ 12 ครั้ง (รายเดือน)</option> <option value="365">ปีละ 365 ครั้ง (รายวัน)</option> </select>
        </div><button onclick="calculateCompound()" class="w-full py-3 bg-gradient-to-r from-emerald-600 to-emerald-500 text-white font-semibold rounded-xl hover:from-emerald-700 hover:to-emerald-600 transition-all shadow-lg shadow-emerald-200"> คำนวณ </button>
        <div id="compound-result" class="hidden result-box rounded-xl p-5 mt-4">
         <div class="grid grid-cols-2 gap-4 text-center">
          <div>
           <p class="text-sm text-gray-600">ยอดเงินรวม</p>
           <p id="compound-total" class="text-2xl font-bold text-emerald-700">-</p>
          </div>
          <div>
           <p class="text-sm text-gray-600">ดอกเบี้ยที่ได้รับ</p>
           <p id="compound-interest" class="text-2xl font-bold text-emerald-600">-</p>
          </div>
         </div>
        </div>
       </div>
      </section><!-- Loan Calculator -->
      <section id="loan" class="calculator-card bg-white rounded-2xl p-6 shadow-xl hidden">
       <div class="flex items-center gap-3 mb-6">
        <div class="w-12 h-12 rounded-xl bg-blue-100 flex items-center justify-center"><span class="text-2xl">🏦</span>
        </div>
        <div>
         <h2 class="text-xl font-semibold text-gray-800">คำนวณสินเชื่อ/ผ่อนชำระ</h2>
         <p class="text-sm text-gray-500">คำนวณยอดผ่อนต่อเดือนและดอกเบี้ยรวม</p>
        </div>
       </div>
       <div class="space-y-4">
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="loan-amount">จำนวนเงินกู้ (บาท)</label> <input type="number" id="loan-amount" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-blue-500 outline-none transition" placeholder="1,000,000">
        </div>
        <div class="grid grid-cols-2 gap-4">
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="loan-rate">อัตราดอกเบี้ย (%/ปี)</label> <input type="number" id="loan-rate" step="0.01" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-blue-500 outline-none transition" placeholder="7">
         </div>
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="loan-years">ระยะเวลา (ปี)</label> <input type="number" id="loan-years" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-blue-500 outline-none transition" placeholder="30">
         </div>
        </div><button onclick="calculateLoan()" class="w-full py-3 bg-gradient-to-r from-blue-600 to-blue-500 text-white font-semibold rounded-xl hover:from-blue-700 hover:to-blue-600 transition-all shadow-lg shadow-blue-200"> คำนวณ </button>
        <div id="loan-result" class="hidden result-box rounded-xl p-5 mt-4" style="background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%);">
         <div class="grid grid-cols-3 gap-4 text-center">
          <div>
           <p class="text-sm text-gray-600">ผ่อนต่อเดือน</p>
           <p id="loan-monthly" class="text-xl font-bold text-blue-700">-</p>
          </div>
          <div>
           <p class="text-sm text-gray-600">ดอกเบี้ยรวม</p>
           <p id="loan-total-interest" class="text-xl font-bold text-blue-600">-</p>
          </div>
          <div>
           <p class="text-sm text-gray-600">จ่ายทั้งหมด</p>
           <p id="loan-total" class="text-xl font-bold text-blue-800">-</p>
          </div>
         </div>
        </div>
       </div>
      </section><!-- Savings Goal -->
      <section id="savings" class="calculator-card bg-white rounded-2xl p-6 shadow-xl hidden">
       <div class="flex items-center gap-3 mb-6">
        <div class="w-12 h-12 rounded-xl bg-amber-100 flex items-center justify-center"><span class="text-2xl">🎯</span>
        </div>
        <div>
         <h2 class="text-xl font-semibold text-gray-800">เป้าหมายออมเงิน</h2>
         <p class="text-sm text-gray-500">คำนวณจำนวนเงินที่ต้องออมต่อเดือน</p>
        </div>
       </div>
       <div class="space-y-4">
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="goal-amount">เป้าหมาย (บาท)</label> <input type="number" id="goal-amount" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-amber-500 outline-none transition" placeholder="500,000">
        </div>
        <div class="grid grid-cols-2 gap-4">
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="goal-rate">ผลตอบแทน (%/ปี)</label> <input type="number" id="goal-rate" step="0.01" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-amber-500 outline-none transition" placeholder="4">
         </div>
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="goal-years">ระยะเวลา (ปี)</label> <input type="number" id="goal-years" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-amber-500 outline-none transition" placeholder="5">
         </div>
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="initial-saving">เงินเริ่มต้น (บาท)</label> <input type="number" id="initial-saving" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-amber-500 outline-none transition" placeholder="0">
        </div><button onclick="calculateSavings()" class="w-full py-3 bg-gradient-to-r from-amber-500 to-orange-500 text-white font-semibold rounded-xl hover:from-amber-600 hover:to-orange-600 transition-all shadow-lg shadow-amber-200"> คำนวณ </button>
        <div id="savings-result" class="hidden result-box rounded-xl p-5 mt-4" style="background: linear-gradient(135deg, #fffbeb 0%, #fef3c7 100%);">
         <div class="text-center">
          <p class="text-sm text-gray-600 mb-1">ต้องออมต่อเดือน</p>
          <p id="savings-monthly" class="text-3xl font-bold text-amber-700">-</p>
          <p class="text-sm text-gray-500 mt-2">รวมเงินที่ออม: <span id="savings-total-contributed" class="font-semibold text-amber-600">-</span></p>
         </div>
        </div>
       </div>
      </section><!-- ROI Calculator -->
      <section id="roi" class="calculator-card bg-white rounded-2xl p-6 shadow-xl hidden">
       <div class="flex items-center gap-3 mb-6">
        <div class="w-12 h-12 rounded-xl bg-purple-100 flex items-center justify-center"><span class="text-2xl">💹</span>
        </div>
        <div>
         <h2 class="text-xl font-semibold text-gray-800">ผลตอบแทนการลงทุน (ROI)</h2>
         <p class="text-sm text-gray-500">คำนวณอัตราผลตอบแทนจากการลงทุน</p>
        </div>
       </div>
       <div class="space-y-4">
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="investment">เงินลงทุน (บาท)</label> <input type="number" id="investment" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-purple-500 outline-none transition" placeholder="100,000">
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="return-amount">มูลค่าปัจจุบัน (บาท)</label> <input type="number" id="return-amount" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-purple-500 outline-none transition" placeholder="150,000">
        </div>
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="holding-years">ระยะเวลาถือครอง (ปี)</label> <input type="number" id="holding-years" step="0.5" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-purple-500 outline-none transition" placeholder="3">
        </div><button onclick="calculateROI()" class="w-full py-3 bg-gradient-to-r from-purple-600 to-purple-500 text-white font-semibold rounded-xl hover:from-purple-700 hover:to-purple-600 transition-all shadow-lg shadow-purple-200"> คำนวณ </button>
        <div id="roi-result" class="hidden result-box rounded-xl p-5 mt-4" style="background: linear-gradient(135deg, #faf5ff 0%, #f3e8ff 100%);">
         <div class="grid grid-cols-3 gap-4 text-center">
          <div>
           <p class="text-sm text-gray-600">กำไร/ขาดทุน</p>
           <p id="roi-profit" class="text-xl font-bold text-purple-700">-</p>
          </div>
          <div>
           <p class="text-sm text-gray-600">ROI รวม</p>
           <p id="roi-total" class="text-xl font-bold text-purple-600">-</p>
          </div>
          <div>
           <p class="text-sm text-gray-600">ROI ต่อปี</p>
           <p id="roi-annual" class="text-xl font-bold text-purple-800">-</p>
          </div>
         </div>
        </div>
       </div>
      </section><!-- Inflation / Time Value -->
      <section id="inflation" class="calculator-card bg-white rounded-2xl p-6 shadow-xl hidden">
       <div class="flex items-center gap-3 mb-6">
        <div class="w-12 h-12 rounded-xl bg-rose-100 flex items-center justify-center"><span class="text-2xl">⏳</span>
        </div>
        <div>
         <h2 class="text-xl font-semibold text-gray-800">มูลค่าเงินตามเวลา</h2>
         <p class="text-sm text-gray-500">คำนวณผลกระทบของเงินเฟ้อ</p>
        </div>
       </div>
       <div class="space-y-4">
        <div><label class="block text-sm font-medium text-gray-700 mb-1" for="current-amount">จำนวนเงินปัจจุบัน (บาท)</label> <input type="number" id="current-amount" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-rose-500 outline-none transition" placeholder="1,000,000">
        </div>
        <div class="grid grid-cols-2 gap-4">
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="inflation-rate">เงินเฟ้อ (%/ปี)</label> <input type="number" id="inflation-rate" step="0.1" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-rose-500 outline-none transition" placeholder="3">
         </div>
         <div><label class="block text-sm font-medium text-gray-700 mb-1" for="future-years">จำนวนปี</label> <input type="number" id="future-years" class="input-field w-full px-4 py-3 rounded-xl border border-gray-200 focus:border-rose-500 outline-none transition" placeholder="20">
         </div>
        </div><button onclick="calculateInflation()" class="w-full py-3 bg-gradient-to-r from-rose-500 to-pink-500 text-white font-semibold rounded-xl hover:from-rose-600 hover:to-pink-600 transition-all shadow-lg shadow-rose-200"> คำนวณ </button>
        <div id="inflation-result" class="hidden result-box rounded-xl p-5 mt-4" style="background: linear-gradient(135deg, #fff1f2 0%, #fecdd3 100%);">
         <div class="grid grid-cols-2 gap-4 text-center">
          <div>
           <p class="text-sm text-gray-600">มูลค่าที่แท้จริงในอนาคต</p>
           <p id="future-value" class="text-2xl font-bold text-rose-700">-</p>
          </div>
          <div>
           <p class="text-sm text-gray-600">กำลังซื้อที่ลดลง</p>
           <p id="purchasing-power-loss" class="text-2xl font-bold text-rose-600">-</p>
          </div>
         </div>
         <p class="text-center text-sm text-gray-500 mt-3">เงิน <span id="equiv-need" class="font-semibold text-rose-600">-</span> ในอนาคตจะมีค่าเท่ากับเงินปัจจุบันของคุณ</p>
        </div>
       </div>
      </section>
     </div>
    </main>
   </div>
  </div>
  <script>
    // Default config
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน'
    };

    // Format number with commas
    function formatNumber(num) {
      return num.toLocaleString('th-TH', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
    }

    // Tab switching
    document.querySelectorAll('.tab-btn').forEach(btn => {
      btn.addEventListener('click', function() {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        
        const tabId = this.dataset.tab;
        document.querySelectorAll('section[id]').forEach(section => {
          if (section.id === tabId) {
            section.classList.remove('hidden');
          } else {
            section.classList.add('hidden');
          }
        });
      });
    });

    // Compound Interest Calculator
    function calculateCompound() {
      const principal = parseFloat(document.getElementById('principal').value) || 0;
      const rate = parseFloat(document.getElementById('rate').value) / 100 || 0;
      const years = parseFloat(document.getElementById('years').value) || 0;
      const n = parseInt(document.getElementById('compound-freq').value) || 12;

      if (principal <= 0 || rate <= 0 || years <= 0) {
        return;
      }

      const amount = principal * Math.pow((1 + rate / n), n * years);
      const interest = amount - principal;

      document.getElementById('compound-total').textContent = '฿' + formatNumber(amount);
      document.getElementById('compound-interest').textContent = '฿' + formatNumber(interest);
      document.getElementById('compound-result').classList.remove('hidden');
    }

    // Loan Calculator
    function calculateLoan() {
      const principal = parseFloat(document.getElementById('loan-amount').value) || 0;
      const annualRate = parseFloat(document.getElementById('loan-rate').value) / 100 || 0;
      const years = parseFloat(document.getElementById('loan-years').value) || 0;

      if (principal <= 0 || annualRate <= 0 || years <= 0) {
        return;
      }

      const monthlyRate = annualRate / 12;
      const numPayments = years * 12;
      const monthlyPayment = principal * (monthlyRate * Math.pow(1 + monthlyRate, numPayments)) / (Math.pow(1 + monthlyRate, numPayments) - 1);
      const totalPayment = monthlyPayment * numPayments;
      const totalInterest = totalPayment - principal;

      document.getElementById('loan-monthly').textContent = '฿' + formatNumber(monthlyPayment);
      document.getElementById('loan-total-interest').textContent = '฿' + formatNumber(totalInterest);
      document.getElementById('loan-total').textContent = '฿' + formatNumber(totalPayment);
      document.getElementById('loan-result').classList.remove('hidden');
    }

    // Savings Goal Calculator
    function calculateSavings() {
      const goal = parseFloat(document.getElementById('goal-amount').value) || 0;
      const annualRate = parseFloat(document.getElementById('goal-rate').value) / 100 || 0;
      const years = parseFloat(document.getElementById('goal-years').value) || 0;
      const initial = parseFloat(document.getElementById('initial-saving').value) || 0;

      if (goal <= 0 || years <= 0) {
        return;
      }

      const monthlyRate = annualRate / 12;
      const numMonths = years * 12;
      
      // Future value of initial amount
      const futureValueInitial = initial * Math.pow(1 + monthlyRate, numMonths);
      const remainingGoal = goal - futureValueInitial;

      let monthlyPayment;
      if (monthlyRate === 0) {
        monthlyPayment = remainingGoal / numMonths;
      } else {
        monthlyPayment = remainingGoal * monthlyRate / (Math.pow(1 + monthlyRate, numMonths) - 1);
      }

      const totalContributed = initial + (monthlyPayment * numMonths);

      document.getElementById('savings-monthly').textContent = '฿' + formatNumber(Math.max(0, monthlyPayment));
      document.getElementById('savings-total-contributed').textContent = '฿' + formatNumber(Math.max(0, totalContributed));
      document.getElementById('savings-result').classList.remove('hidden');
    }

    // ROI Calculator
    function calculateROI() {
      const investment = parseFloat(document.getElementById('investment').value) || 0;
      const currentValue = parseFloat(document.getElementById('return-amount').value) || 0;
      const years = parseFloat(document.getElementById('holding-years').value) || 1;

      if (investment <= 0) {
        return;
      }

      const profit = currentValue - investment;
      const roiTotal = ((currentValue - investment) / investment) * 100;
      const roiAnnual = (Math.pow(currentValue / investment, 1 / years) - 1) * 100;

      const profitEl = document.getElementById('roi-profit');
      profitEl.textContent = (profit >= 0 ? '+' : '') + '฿' + formatNumber(profit);
      profitEl.className = 'text-xl font-bold ' + (profit >= 0 ? 'text-green-600' : 'text-red-600');

      document.getElementById('roi-total').textContent = roiTotal.toFixed(2) + '%';
      document.getElementById('roi-annual').textContent = roiAnnual.toFixed(2) + '%';
      document.getElementById('roi-result').classList.remove('hidden');
    }

    // Inflation Calculator
    function calculateInflation() {
      const currentAmount = parseFloat(document.getElementById('current-amount').value) || 0;
      const inflationRate = parseFloat(document.getElementById('inflation-rate').value) / 100 || 0;
      const years = parseFloat(document.getElementById('future-years').value) || 0;

      if (currentAmount <= 0 || years <= 0) {
        return;
      }

      const futureValue = currentAmount / Math.pow(1 + inflationRate, years);
      const purchasingPowerLoss = currentAmount - futureValue;
      const equivalentNeed = currentAmount * Math.pow(1 + inflationRate, years);

      document.getElementById('future-value').textContent = '฿' + formatNumber(futureValue);
      document.getElementById('purchasing-power-loss').textContent = '-฿' + formatNumber(purchasingPowerLoss);
      document.getElementById('equiv-need').textContent = '฿' + formatNumber(equivalentNeed);
      document.getElementById('inflation-result').classList.remove('hidden');
    }

    // Element SDK implementation
    async function onConfigChange(config) {
      const title = config.app_title || defaultConfig.app_title;
      document.getElementById('app-title').textContent = title;
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
        ['app_title', config.app_title || defaultConfig.app_title]
      ]);
    }

    // Initialize SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c0bab4390487323',t:'MTc2ODg4MTY3MC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
