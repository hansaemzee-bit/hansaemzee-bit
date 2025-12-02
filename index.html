<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>나만의 여행 플래너 V5.3</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Inter Font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Leaflet CSS (For Map) -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
    
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0fdfa; /* Light Teal Background */
            -webkit-tap-highlight-color: transparent;
        }
        .container-card {
            max-width: 1000px;
            min-height: 100vh; /* Full height for mobile */
        }
        @media (min-width: 640px) {
            .container-card {
                min-height: 90vh;
            }
        }
        .tab-button {
            transition: all 0.2s;
            white-space: nowrap;
        }
        .tab-button.active {
            border-bottom: 3px solid #06b6d4; /* Teal 400 */
            color: #06b6d4;
            font-weight: 700;
            background-color: #ecfeff;
        }
        .itinerary-item {
            background-color: #f8fafc;
            border-left: 4px solid #cbd5e1;
            transition: all 0.2s;
        }
        .itinerary-item:focus-within {
            background-color: #f0f9ff;
            border-left-color: #22d3ee;
        }
        textarea, input, select {
            transition: all 0.2s;
        }
        textarea:focus, input:focus, select:focus {
            border-color: #06b6d4;
            box-shadow: 0 0 0 3px rgba(6, 182, 212, 0.3);
            outline: none;
        }
        .scrollbar-hide::-webkit-scrollbar { display: none; }
        .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }
        
        /* Map Container */
        #map { height: 350px; width: 100%; z-index: 1; border-radius: 0.75rem; }

        /* Toast Notification */
        #toast {
            visibility: hidden;
            min-width: 250px;
            background-color: #333;
            color: #fff;
            text-align: center;
            border-radius: 8px;
            padding: 16px;
            position: fixed;
            z-index: 1000;
            left: 50%;
            bottom: 30px;
            transform: translateX(-50%);
            font-size: 14px;
            opacity: 0;
            transition: opacity 0.3s, bottom 0.3s;
        }
        #toast.show {
            visibility: visible;
            opacity: 1;
            bottom: 50px;
        }
    </style>
</head>
<body class="sm:p-6 bg-gray-50">

    <div id="app" class="container-card mx-auto bg-white sm:rounded-xl shadow-2xl overflow-hidden flex flex-col">
        
        <!-- Header -->
        <div class="bg-gradient-to-r from-teal-500 to-cyan-600 p-5 text-white sticky top-0 z-20">
            <h1 class="text-2xl font-bold flex items-center">
                <i class="fa-solid fa-plane-up mr-3"></i>
                Trip Master
            </h1>
            <p class="text-cyan-100 text-xs mt-1 flex items-center justify-between">
                <span id="storage-mode-indicator"><i class="fa-solid fa-wifi mr-1"></i> Checking...</span>
                <span class="opacity-75 font-mono bg-black/10 px-2 py-0.5 rounded">ID: <span id="user-id-display">...</span></span>
            </p>
        </div>

        <!-- Loading -->
        <div id="loading-indicator" class="flex justify-center items-center h-64 flex-grow">
            <div class="animate-spin rounded-full h-12 w-12 border-b-4 border-cyan-500"></div>
        </div>

        <!-- Main Content -->
        <div id="main-content" class="hidden p-4 space-y-6 flex-grow pb-20">

            <!-- 1. DASHBOARD -->
            <div class="grid grid-cols-2 lg:grid-cols-4 gap-3">
                <!-- 환율 -->
                <div class="bg-slate-50 p-3 rounded-xl border border-slate-200 shadow-sm col-span-2 sm:col-span-1">
                    <div class="flex justify-between items-start mb-1">
                        <h3 class="text-[10px] font-bold text-slate-500 uppercase">JPY 환율 (100엔)</h3>
                        <button id="refresh-rate-btn" class="text-cyan-500 hover:text-cyan-700 text-xs p-1"><i class="fa-solid fa-rotate-right"></i></button>
                    </div>
                    <div class="flex items-baseline">
                        <span id="currency-rate" class="text-xl font-extrabold text-slate-800">---</span>
                        <span class="ml-1 text-xs text-slate-500">KRW</span>
                    </div>
                </div>

                <!-- 총 예산 -->
                <div class="bg-indigo-50 p-3 rounded-xl border border-indigo-100 shadow-sm col-span-2 sm:col-span-1 relative">
                    <h3 class="text-[10px] font-bold text-indigo-500 uppercase mb-1">총 여행 예산</h3>
                    <div class="flex gap-1">
                        <select id="budget-currency-select" class="bg-white border border-indigo-200 text-indigo-900 text-xs rounded px-1 font-bold focus:outline-none">
                            <option value="KRW">KRW</option>
                            <option value="JPY">JPY</option>
                        </select>
                        <input type="number" id="total-budget-input" class="w-full px-2 py-1 bg-white border border-indigo-200 rounded text-indigo-900 font-bold focus:border-indigo-500 text-sm" placeholder="0">
                    </div>
                </div>

                <!-- 지출 -->
                <div class="bg-orange-50 p-3 rounded-xl border border-orange-100 shadow-sm">
                    <h3 class="text-[10px] font-bold text-orange-500 uppercase mb-1">총 지출</h3>
                    <div class="flex items-baseline">
                        <span id="spent-currency-symbol" class="text-orange-400 text-xs mr-1">₩</span>
                        <span id="total-expense-display" class="text-lg font-extrabold text-orange-800">0</span>
                    </div>
                </div>

                <!-- 잔액 -->
                <div class="bg-emerald-50 p-3 rounded-xl border border-emerald-100 shadow-sm">
                    <h3 class="text-[10px] font-bold text-emerald-600 uppercase mb-1">남은 예산</h3>
                    <div class="flex items-baseline">
                        <span id="remain-currency-symbol" class="text-emerald-500 text-xs mr-1">₩</span>
                        <span id="remaining-budget" class="text-lg font-extrabold text-emerald-700">0</span>
                    </div>
                </div>
            </div>

            <!-- 2. SETTINGS -->
            <div class="bg-white border border-gray-200 p-3 rounded-xl shadow-sm flex flex-wrap items-center gap-3 text-sm">
                <!-- City -->
                <div class="flex items-center gap-1 flex-grow sm:flex-grow-0">
                    <i class="fa-solid fa-location-dot text-gray-400 text-xs"></i>
                    <input type="text" id="trip-city" class="border-b border-gray-300 p-1 w-16 text-center focus:border-cyan-500 focus:outline-none font-semibold text-xs" value="후쿠오카">
                </div>
                <!-- Date -->
                <div class="flex items-center gap-1">
                    <i class="fa-regular fa-calendar text-gray-400 text-xs"></i>
                    <input type="date" id="trip-start-date" class="border rounded p-1 text-xs w-24">
                </div>
                <!-- Duration (Changed to Input) -->
                <div class="flex items-center gap-1">
                    <i class="fa-solid fa-clock text-gray-400 text-xs"></i>
                    <input type="number" id="trip-duration" class="border rounded p-1 text-xs w-10 text-center font-bold" value="3" min="1" max="60">
                    <span class="text-xs text-gray-500">일</span>
                </div>
                <!-- API Key -->
                <div class="flex items-center gap-1 flex-grow sm:flex-grow-0">
                    <i class="fa-solid fa-key text-gray-400 text-xs"></i>
                    <input type="password" id="user-api-key" class="border rounded p-1 text-xs w-20 focus:w-32 transition-all" placeholder="Gemini API Key">
                </div>
                
                <button id="update-trip-settings" class="ml-auto px-3 py-1 bg-gray-800 text-white text-xs rounded hover:bg-gray-700 whitespace-nowrap">저장</button>
            </div>

            <!-- 3. TABS -->
            <div class="flex overflow-x-auto scrollbar-hide border-b border-gray-200 -mx-4 px-4 sm:mx-0 sm:px-0" id="tabs-container">
                <!-- Dynamic Tabs Here -->
            </div>

            <!-- 4. CONTENT AREA -->
            <div>
                <!-- Itinerary Contents (Dynamic) -->
                <div id="tab-content-container"></div>

                <!-- MAP TAB (Static) -->
                <div id="map-tab-content" class="hidden mt-4">
                    <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm">
                        
                        <!-- Map Controls -->
                        <div class="p-3 bg-gray-50 border-b border-gray-200">
                             <div class="flex gap-2 mb-3">
                                <input type="text" id="map-search-keyword" class="flex-grow p-2 border border-gray-300 rounded text-sm" placeholder="예: 텐진 야키토리, 하카타 빈티지샵">
                                <button id="search-local-btn" class="px-3 py-2 bg-teal-600 text-white rounded text-sm whitespace-nowrap shadow-sm active:bg-teal-700">
                                    <i class="fa-solid fa-search mr-1"></i> 검색
                                </button>
                            </div>
                            
                            <!-- Sub Tabs (Search vs Favorites) -->
                            <div class="flex border-b border-gray-200">
                                <button id="view-search-btn" class="flex-1 py-2 text-sm font-bold border-b-2 border-teal-500 text-teal-600 transition-colors">
                                    검색 결과
                                </button>
                                <button id="view-fav-btn" class="flex-1 py-2 text-sm font-bold border-b-2 border-transparent text-gray-400 hover:text-gray-600 transition-colors">
                                    즐겨찾기 (<span id="fav-count">0</span>)
                                </button>
                            </div>
                        </div>

                        <!-- Map View -->
                        <div id="map"></div>

                        <!-- Results List -->
                        <div id="map-results-container" class="p-0 bg-white max-h-80 overflow-y-auto">
                            <!-- Search Results List -->
                            <div id="map-search-list" class="p-3 space-y-3">
                                <div class="text-xs text-gray-400 text-center py-8">
                                    <i class="fa-solid fa-magnifying-glass mb-2 text-lg"></i><br>
                                    키워드를 검색하면<br>현지인 핫플을 추천해드립니다.
                                </div>
                            </div>
                            <!-- Favorites List -->
                            <div id="map-fav-list" class="hidden p-3 space-y-3">
                                <div class="text-xs text-gray-400 text-center py-8">
                                    <i class="fa-regular fa-star mb-2 text-lg"></i><br>
                                    아직 즐겨찾기가 없습니다.<br>검색 결과에서 별표를 눌러 추가해보세요.
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- NOTE TAB (Static) -->
                <div id="notes-tab-content" class="hidden mt-4">
                     <div class="bg-yellow-50 border border-yellow-200 rounded-xl p-4">
                        <textarea id="notes-content" class="w-full h-60 p-3 bg-white border border-yellow-300 rounded-lg focus:outline-none text-sm leading-relaxed" placeholder="메모장"></textarea>
                    </div>
                </div>
            </div>

            <!-- 5. UTILITIES (Translator & Expenses) -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-2">
                <!-- Expenses -->
                <div class="bg-white border border-gray-200 rounded-xl p-4 shadow-sm order-1 md:order-2">
                    <h2 class="text-sm font-bold text-gray-800 mb-3 flex items-center">
                        <span class="bg-orange-100 text-orange-600 px-1.5 py-0.5 rounded mr-2"><i class="fa-solid fa-won-sign"></i></span>
                        빠른 지출 기록
                    </h2>
                    <div class="bg-gray-50 p-3 rounded-lg mb-3 space-y-2 text-sm">
                        <div class="flex gap-2">
                            <input type="date" id="expense-date" class="w-1/3 p-1.5 border rounded">
                            <select id="expense-category" class="w-2/3 p-1.5 border rounded">
                                <option value="식비">식비 🍜</option><option value="교통">교통 🚌</option>
                                <option value="쇼핑">쇼핑 🛍️</option><option value="숙박">숙박 🏨</option>
                                <option value="관광">관광 🎫</option><option value="기타">기타 🎸</option>
                            </select>
                        </div>
                        <div class="flex gap-2">
                            <input type="number" id="expense-amount" class="w-1/3 p-1.5 border rounded" placeholder="금액">
                            <select id="expense-currency" class="w-20 p-1.5 border rounded bg-white font-bold text-gray-700">
                                <option value="JPY">JPY</option><option value="KRW">KRW</option>
                            </select>
                            <input type="text" id="expense-description" class="flex-grow p-1.5 border rounded" placeholder="내용">
                        </div>
                        <button id="add-expense-btn" class="w-full py-2 bg-orange-500 text-white rounded font-bold hover:bg-orange-600">추가하기</button>
                    </div>
                    <div id="expense-list" class="space-y-2 max-h-60 overflow-y-auto pr-1"></div>
                </div>

                <!-- Translator -->
                <div class="bg-white border border-gray-200 rounded-xl p-4 shadow-sm order-2 md:order-1">
                    <h2 class="text-sm font-bold text-gray-800 mb-3 flex items-center">
                        <span class="bg-pink-100 text-pink-600 px-1.5 py-0.5 rounded mr-2"><i class="fa-solid fa-camera"></i></span>
                        메뉴판 번역
                    </h2>
                    <div class="space-y-3">
                        <label class="block border-2 border-dashed border-gray-300 rounded-lg p-4 text-center cursor-pointer hover:bg-gray-50 transition active:bg-gray-100">
                            <input type="file" id="image-upload" accept="image/*" class="hidden">
                            <i class="fa-solid fa-camera text-2xl text-gray-400 mb-1"></i>
                            <p class="text-xs text-gray-500">사진 찍기 / 업로드 (API Key 필요)</p>
                        </label>
                        <div id="preview-container" class="hidden text-center bg-black/5 p-2 rounded relative">
                            <img id="image-preview" class="max-h-40 mx-auto rounded shadow-sm">
                            <button id="close-preview-btn" class="absolute top-1 right-1 bg-black/50 text-white w-6 h-6 rounded-full text-xs">X</button>
                        </div>
                        <button id="translate-btn" class="w-full py-2 bg-pink-500 text-white rounded font-bold hover:bg-pink-600 disabled:opacity-50 disabled:cursor-not-allowed" disabled>번역하기</button>
                        <div id="translation-result" class="hidden bg-gray-50 p-3 rounded border border-gray-200">
                            <p id="result-text" class="text-xs text-gray-800 whitespace-pre-wrap leading-relaxed"></p>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </div>

    <!-- Toast Notification -->
    <div id="toast">주소가 복사되었습니다!</div>

    <!-- Scripts -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>
    
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, onSnapshot, setDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // 중요: 단독 실행 시 Firebase Config가 없으면 로컬 스토리지 모드
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'trip-master-v5-local';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
        const systemApiKey = ""; 

        let app, db, auth, userId;
        let isAuthReady = false;
        let useLocalStorage = false;
        let currentJpyRate = 0; 
        let map = null;
        let currentMapTab = 'search';
        let currentSearchResults = []; 

        const DEFAULT_DATA = {
            city: "후쿠오카",
            tripStartDate: new Date().toISOString().split('T')[0],
            tripDuration: 3,
            totalBudget: 100000,
            budgetCurrency: 'KRW',
            notes: "",
            expenses: [],
            favorites: [], // Stores {id, name, desc, address, lat, lng}
            day1: [{ time: "10:00", activity: "공항 도착" }]
        };

        let appData = { ...DEFAULT_DATA };

        const els = {
            loading: document.getElementById('loading-indicator'),
            main: document.getElementById('main-content'),
            userId: document.getElementById('user-id-display'),
            modeIndicator: document.getElementById('storage-mode-indicator'),
            rate: document.getElementById('currency-rate'),
            refreshRate: document.getElementById('refresh-rate-btn'),
            
            // Budget
            budgetCurrSel: document.getElementById('budget-currency-select'),
            budgetInput: document.getElementById('total-budget-input'),
            spentDisplay: document.getElementById('total-expense-display'),
            spentSymbol: document.getElementById('spent-currency-symbol'),
            remainDisplay: document.getElementById('remaining-budget'),
            remainSymbol: document.getElementById('remain-currency-symbol'),

            city: document.getElementById('trip-city'),
            startDate: document.getElementById('trip-start-date'),
            duration: document.getElementById('trip-duration'),
            userApiKey: document.getElementById('user-api-key'),
            updateSettings: document.getElementById('update-trip-settings'),
            tabsContainer: document.getElementById('tabs-container'),
            tabContentContainer: document.getElementById('tab-content-container'),
            notesContent: document.getElementById('notes-content'),
            
            // Map
            mapSearchKey: document.getElementById('map-search-keyword'),
            searchLocalBtn: document.getElementById('search-local-btn'),
            viewSearchBtn: document.getElementById('view-search-btn'),
            viewFavBtn: document.getElementById('view-fav-btn'),
            favCount: document.getElementById('fav-count'),
            searchList: document.getElementById('map-search-list'),
            favList: document.getElementById('map-fav-list'),
            
            // Trans/Exp
            imgUpload: document.getElementById('image-upload'),
            imgPreview: document.getElementById('image-preview'),
            previewBox: document.getElementById('preview-container'),
            closePreview: document.getElementById('close-preview-btn'),
            translateBtn: document.getElementById('translate-btn'),
            transResult: document.getElementById('translation-result'),
            transResultText: document.getElementById('result-text'),
            
            expDate: document.getElementById('expense-date'),
            expCat: document.getElementById('expense-category'),
            expAmt: document.getElementById('expense-amount'),
            expCurr: document.getElementById('expense-currency'),
            expDesc: document.getElementById('expense-description'),
            addExpBtn: document.getElementById('add-expense-btn'),
            expList: document.getElementById('expense-list'),
            
            toast: document.getElementById('toast'),
        };
        
        function getApiKey() {
            const userInput = els.userApiKey.value.trim();
            if (userInput) return userInput;
            const stored = localStorage.getItem('trip_planner_gemini_key');
            if (stored) return stored;
            return systemApiKey;
        }

        async function init() {
            try {
                const storedKey = localStorage.getItem('trip_planner_gemini_key');
                if (storedKey) els.userApiKey.value = storedKey;

                if (Object.keys(firebaseConfig).length === 0) {
                    useLocalStorage = true;
                    userId = "Device-Local";
                    els.modeIndicator.innerHTML = '<i class="fa-solid fa-floppy-disk mr-1"></i> Local Mode';
                    els.userId.textContent = "Offline";
                    const saved = localStorage.getItem('trip_planner_v5_data');
                    if (saved) appData = { ...DEFAULT_DATA, ...JSON.parse(saved) };
                    renderApp();
                    els.loading.classList.add('hidden');
                    els.main.classList.remove('hidden');
                } else {
                    app = initializeApp(firebaseConfig);
                    db = getFirestore(app);
                    auth = getAuth(app);
                    els.modeIndicator.innerHTML = '<i class="fa-solid fa-cloud mr-1"></i> Cloud Sync';
                    await new Promise(r => {
                        const u = onAuthStateChanged(auth, async (user) => {
                            if (!user) {
                                if (initialAuthToken) await signInWithCustomToken(auth, initialAuthToken);
                                else await signInAnonymously(auth);
                            }
                            userId = auth.currentUser?.uid;
                            isAuthReady = true;
                            u(); r();
                        });
                    });
                    els.userId.textContent = userId.substring(0, 4);
                    setupRealtimeListener();
                }
                els.expDate.value = new Date().toISOString().split('T')[0];
                fetchExchangeRate();
                setupEventListeners();
                initMap();
            } catch (e) { 
                if (!useLocalStorage) {
                    useLocalStorage = true;
                    userId = "Error-Fallback";
                    renderApp();
                    els.loading.classList.add('hidden');
                    els.main.classList.remove('hidden');
                }
            }
        }

        function getDocRef() { return doc(db, `artifacts/${appId}/users/${userId}/trip_planner_v5/data`); }

        function setupRealtimeListener() {
            if(useLocalStorage) return;
            onSnapshot(getDocRef(), (snap) => {
                if (snap.exists()) appData = { ...DEFAULT_DATA, ...snap.data() };
                else { appData = { ...DEFAULT_DATA }; saveData(); }
                renderApp();
                els.loading.classList.add('hidden');
                els.main.classList.remove('hidden');
            });
        }

        let saveTimeout;
        function saveData() {
            clearTimeout(saveTimeout);
            saveTimeout = setTimeout(async () => {
                if (useLocalStorage) {
                    localStorage.setItem('trip_planner_v5_data', JSON.stringify(appData));
                } else if (isAuthReady) {
                    await setDoc(getDocRef(), appData, { merge: true });
                }
            }, 500);
        }

        function calculateBudget() {
            const budgetAmt = parseFloat(appData.totalBudget) || 0;
            const budgetCurr = appData.budgetCurrency || 'KRW';
            const rate = currentJpyRate || 9.5;
            let totalSpent = 0;
            (appData.expenses || []).forEach(ex => {
                let amt = ex.amount;
                if (budgetCurr === 'KRW' && ex.currency === 'JPY') amt = ex.amount * rate;
                else if (budgetCurr === 'JPY' && ex.currency === 'KRW') amt = ex.amount / rate;
                totalSpent += amt;
            });
            const remaining = budgetAmt - totalSpent;
            els.budgetInput.value = budgetAmt;
            els.budgetCurrSel.value = budgetCurr;
            const symbol = budgetCurr === 'KRW' ? '₩' : '¥';
            els.spentSymbol.textContent = symbol;
            els.remainSymbol.textContent = symbol;
            els.spentDisplay.textContent = Math.round(totalSpent).toLocaleString();
            els.remainDisplay.textContent = Math.round(remaining).toLocaleString();
            els.remainDisplay.className = `text-lg font-extrabold ${remaining >= 0 ? 'text-emerald-700' : 'text-red-600'}`;
        }

        let currentTab = 'day1';
        function renderApp() {
            els.city.value = appData.city;
            els.startDate.value = appData.tripStartDate;
            els.duration.value = appData.tripDuration;
            els.notesContent.value = appData.notes || '';
            els.favCount.textContent = (appData.favorites || []).length;
            
            calculateBudget();
            generateTabs();
            renderExpenseList();
            renderMapList();
        }

        function generateTabs() {
            const duration = parseInt(appData.tripDuration) || 3;
            let tabsHtml = '';
            let contentHtml = '';
            for (let i = 1; i <= duration; i++) {
                const dayId = `day${i}`;
                const isActive = currentTab === dayId;
                const label = getDayLabel(appData.tripStartDate, i - 1);
                tabsHtml += `
                    <button class="tab-button px-4 py-2 border-b-2 border-transparent ${isActive ? 'active' : 'text-gray-400 hover:text-cyan-600'}" data-tab="${dayId}">
                        <div class="text-[10px] uppercase">Day ${i}</div>
                        <div class="font-bold text-sm">${label}</div>
                    </button>`;
                
                const dayPlan = appData[dayId] || [];
                const hiddenClass = isActive ? '' : 'hidden';
                contentHtml += `
                    <div id="content-${dayId}" class="tab-content ${hiddenClass}">
                        <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm mt-2">
                            <div class="bg-gray-50 px-4 py-2 border-b border-gray-200 flex justify-between items-center">
                                <h3 class="font-bold text-gray-700 text-sm">일정</h3>
                                <button class="add-act-btn text-[10px] bg-cyan-100 text-cyan-700 px-2 py-1 rounded hover:bg-cyan-200 font-bold" data-day="${dayId}">
                                    <i class="fa-solid fa-plus mr-1"></i>추가
                                </button>
                            </div>
                            <div class="p-3 space-y-2">
                                ${dayPlan.map((item, idx) => `
                                    <div class="itinerary-item p-2 rounded flex gap-2 items-center group">
                                        <input type="time" class="p-1 border rounded text-xs bg-white w-16 text-center font-bold text-gray-600" value="${item.time}" onchange="updateAct('${dayId}', ${idx}, 'time', this.value)">
                                        <input type="text" class="flex-grow p-1 bg-transparent text-sm text-gray-800 border-b border-transparent focus:border-cyan-300" value="${item.activity}" placeholder="일정 입력" onchange="updateAct('${dayId}', ${idx}, 'activity', this.value)">
                                        <button class="text-gray-300 hover:text-red-400 opacity-100 sm:opacity-0 sm:group-hover:opacity-100 px-2" onclick="removeAct('${dayId}', ${idx})"><i class="fa-solid fa-trash-can"></i></button>
                                    </div>
                                `).join('')}
                                ${dayPlan.length === 0 ? '<div class="text-center text-gray-300 py-4 text-xs">일정이 비어있습니다.</div>' : ''}
                            </div>
                        </div>
                    </div>`;
            }
            const staticTabs = [
                { id: 'map', icon: 'fa-map', label: '지도', color: 'teal' },
                { id: 'notes', icon: 'fa-note-sticky', label: '메모', color: 'yellow' }
            ];
            staticTabs.forEach(t => {
                const isActive = currentTab === t.id;
                tabsHtml += `
                    <button class="tab-button px-4 py-2 border-b-2 border-transparent ${isActive ? 'active' : `text-gray-400 hover:text-${t.color}-600`}" data-tab="${t.id}">
                        <div class="text-[10px] text-transparent">.</div>
                        <div class="font-bold text-sm"><i class="fa-solid ${t.icon} mr-1"></i>${t.label}</div>
                    </button>`;
            });
            els.tabsContainer.innerHTML = tabsHtml;
            els.tabContentContainer.innerHTML = contentHtml;
            ['map', 'notes'].forEach(id => {
                const div = document.getElementById(`${id}-tab-content`);
                if(currentTab === id) {
                    div.classList.remove('hidden');
                    els.tabContentContainer.classList.add('hidden');
                    if(id === 'map' && map) setTimeout(()=> {
                        map.invalidateSize();
                        renderMapMarkers();
                    }, 100);
                } else {
                    div.classList.add('hidden');
                }
            });
            document.querySelectorAll('.tab-button').forEach(btn => btn.onclick = () => { currentTab = btn.dataset.tab; renderApp(); });
            document.querySelectorAll('.add-act-btn').forEach(btn => btn.onclick = () => addActivity(btn.dataset.day));
        }

        function getDayLabel(startStr, idx) {
            if (!startStr) return `Day ${idx + 1}`;
            const d = new Date(startStr); d.setDate(d.getDate() + idx);
            return `${d.getMonth()+1}/${d.getDate()}`;
        }
        window.updateAct = (d, i, f, v) => { appData[d][i][f] = v; saveData(); };
        window.removeAct = (d, i) => { appData[d].splice(i, 1); renderApp(); saveData(); };
        function addActivity(d) { if(!appData[d]) appData[d]=[]; appData[d].push({time:"10:00", activity:""}); renderApp(); saveData(); }
        window.removeExpense = (id) => { appData.expenses = appData.expenses.filter(x=>x.id!==id); renderApp(); saveData(); };

        function renderExpenseList() {
            const list = [...(appData.expenses||[])].sort((a,b)=>new Date(b.date)-new Date(a.date));
            els.expList.innerHTML = list.length ? list.map(ex => {
                let approx = '';
                const bCurr = appData.budgetCurrency || 'KRW';
                if(bCurr !== ex.currency && currentJpyRate > 0) {
                    const conv = (ex.currency === 'JPY') ? ex.amount * currentJpyRate : ex.amount / currentJpyRate;
                    approx = `<span class="text-[10px] text-gray-400">≈ ${Math.round(conv).toLocaleString()}${bCurr==='KRW'?'원':'엔'}</span>`;
                }
                const iconMap = {'식비':'🍜','교통':'🚌','쇼핑':'🛍️','숙박':'🏨','관광':'🎫','기타':'🎸'};
                return `
                <div class="flex items-center justify-between p-2 bg-gray-50 rounded border border-gray-100">
                    <div class="flex items-center gap-2 overflow-hidden">
                        <div class="text-lg">${iconMap[ex.category]||'💰'}</div>
                        <div class="min-w-0">
                            <div class="font-bold text-gray-700 text-xs truncate">${ex.description}</div>
                            <div class="text-[10px] text-gray-400">${ex.date}</div>
                        </div>
                    </div>
                    <div class="text-right flex-shrink-0">
                        <div class="font-bold text-gray-800 text-sm">${ex.amount.toLocaleString()}<span class="text-[10px] font-normal ml-0.5">${ex.currency}</span></div>
                        ${approx}
                    </div>
                    <button class="text-gray-300 hover:text-red-400 ml-2 px-1" onclick="removeExpense('${ex.id}')"><i class="fa-solid fa-xmark"></i></button>
                </div>`;
            }).join('') : '<div class="text-center text-gray-300 py-4 text-xs">지출 내역이 없습니다.</div>';
        }

        // --- MAP & FAVORITES LOGIC ---
        function initMap() {
            map = L.map('map').setView([33.5902, 130.4017], 13);
            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {attribution: '&copy; OpenStreetMap'}).addTo(map);
        }

        function toggleMapTab(tabName) {
            currentMapTab = tabName;
            
            const searchActive = tabName === 'search';
            els.viewSearchBtn.className = `flex-1 py-2 text-sm font-bold border-b-2 ${searchActive ? 'border-teal-500 text-teal-600' : 'border-transparent text-gray-400 hover:text-gray-600'} transition-colors`;
            els.viewFavBtn.className = `flex-1 py-2 text-sm font-bold border-b-2 ${!searchActive ? 'border-teal-500 text-teal-600' : 'border-transparent text-gray-400 hover:text-gray-600'} transition-colors`;
            
            els.searchList.classList.toggle('hidden', !searchActive);
            els.favList.classList.toggle('hidden', searchActive);

            renderMapList();
            renderMapMarkers();
        }
        window.toggleMapTab = toggleMapTab; // Expose to global scope for initial button clicks

        function renderMapMarkers() {
            if(!map) return;
            map.eachLayer((layer) => {
                if (layer instanceof L.Marker) map.removeLayer(layer);
            });

            const items = currentMapTab === 'search' ? currentSearchResults : (appData.favorites || []);
            
            items.forEach((p, idx) => {
                if(p.lat && p.lng) {
                    L.marker([p.lat, p.lng]).addTo(map)
                        .bindPopup(`<b>${p.name}</b><br><span style="font-size:10px">${p.desc}</span>`);
                    if(idx === 0) map.setView([p.lat, p.lng], 14);
                }
            });
        }

        function renderMapList() {
            if(currentMapTab === 'search') {
                if(currentSearchResults.length === 0) {
                     els.searchList.innerHTML = `<div class="text-xs text-gray-400 text-center py-8">
                                                    <i class="fa-solid fa-magnifying-glass mb-2 text-lg"></i><br>
                                                    키워드를 검색하면<br>현지인 핫플을 추천해드립니다.
                                                </div>`;
                } else {
                    els.searchList.innerHTML = currentSearchResults.map((p, i) => {
                        const isFav = (appData.favorites || []).some(f => f.name === p.name);
                        return `
                        <div class="p-3 bg-gray-50 border border-gray-100 rounded-lg hover:bg-teal-50 transition group relative">
                            <div class="font-bold text-gray-800 text-sm pr-6">${i+1}. ${p.name}</div>
                            <div class="text-xs text-gray-500 mt-1 mb-1">${p.desc}</div>
                            <div class="text-[10px] text-blue-500 cursor-pointer hover:underline" onclick="copyAddress('${p.address || ''}')">
                                <i class="fa-solid fa-location-dot"></i> ${p.address || '주소 정보 없음'}
                            </div>
                            <button class="absolute top-2 right-2 text-lg ${isFav ? 'text-yellow-400' : 'text-gray-300 hover:text-yellow-400'}" 
                                onclick="toggleFavorite(currentSearchResults[${i}])">
                                <i class="${isFav ? 'fa-solid' : 'fa-regular'} fa-star"></i>
                            </button>
                        </div>`;
                    }).join('');
                }
            } else {
                const favs = appData.favorites || [];
                if(favs.length === 0) {
                     els.favList.innerHTML = `<div class="text-xs text-gray-400 text-center py-8">
                                                <i class="fa-regular fa-star mb-2 text-lg"></i><br>
                                                아직 즐겨찾기가 없습니다.<br>검색 결과에서 별표를 눌러 추가해보세요.
                                            </div>`;
                } else {
                    els.favList.innerHTML = favs.map((p, i) => `
                        <div class="p-3 bg-yellow-50 border border-yellow-100 rounded-lg relative">
                            <div class="font-bold text-gray-800 text-sm pr-6">${p.name}</div>
                            <div class="text-xs text-gray-600 mt-1 mb-1">${p.desc}</div>
                            <div class="text-[10px] text-blue-600 cursor-pointer hover:underline flex items-center bg-white/50 p-1 rounded" 
                                onclick="copyAddress('${p.address || ''}')">
                                <i class="fa-regular fa-copy mr-1"></i> ${p.address || '주소 정보 없음'}
                            </div>
                            <button class="absolute top-2 right-2 text-gray-400 hover:text-red-500 text-xs" 
                                onclick="removeFavorite('${p.id}')">
                                <i class="fa-solid fa-trash-can"></i>
                            </button>
                        </div>
                    `).join('');
                }
            }
        }

        async function searchLocalGems() {
            const key = getApiKey();
            if(!key) return alert("API Key가 필요합니다. 설정에 입력해주세요.");

            const k=els.mapSearchKey.value; const c=appData.city; if(!k) return alert("키워드 입력");
            
            toggleMapTab('search');
            
            els.searchLocalBtn.disabled=true; 
            els.searchList.innerHTML='<div class="text-center py-4 text-gray-500"><i class="fa-solid fa-circle-notch fa-spin mr-2"></i>AI 검색 중...</div>';
            
            try {
                const prompt = `Find 5 places in ${c} for keyword "${k}". 
                Criteria: Highly rated by LOCAL reviews. 
                Output JSON: [{"name":"Place Name","desc":"Short description","address":"Full Address","lat":0.0,"lng":0.0}]. Give ONLY the JSON array.`;
                
                const res = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${key}`, {
                    method:'POST', body:JSON.stringify({contents:[{parts:[{text:prompt}]}], tools:[{"google_search":{}}]})
                });
                const d = await res.json();
                const jsonText = d.candidates?.[0]?.content?.parts?.[0]?.text;
                const jsonMatch = jsonText.match(/\[.*\]/s);
                
                if(jsonMatch) {
                    currentSearchResults = JSON.parse(jsonMatch[0]);
                    renderMapList();
                    renderMapMarkers();
                } else {
                    throw new Error("Invalid JSON or No Results");
                }
            } catch(e){
                currentSearchResults = [];
                renderMapList();
                alert("검색 중 오류가 발생했습니다. (API Key 또는 응답 확인 필요)");
            } finally {
                els.searchLocalBtn.disabled=false;
            }
        }
        
        // Attached to window for HTML access
        window.toggleFavorite = (place) => {
            const favs = appData.favorites || [];
            const existingIdx = favs.findIndex(f => f.name === place.name);
            
            if(existingIdx >= 0) {
                favs.splice(existingIdx, 1);
            } else {
                favs.push({ ...place, id: Date.now().toString() });
            }
            appData.favorites = favs;
            saveData();
            renderApp();
            if(currentMapTab === 'favorites') renderMapMarkers();
        };

        window.removeFavorite = (id) => {
            appData.favorites = (appData.favorites || []).filter(f => f.id !== id);
            saveData();
            renderApp();
            if(currentMapTab === 'favorites') renderMapMarkers();
        };

        window.copyAddress = (text) => {
            if(!text) return;
            const el = document.createElement('textarea');
            el.value = text;
            document.body.appendChild(el);
            el.select();
            document.execCommand('copy');
            document.body.removeChild(el);
            
            const toast = els.toast;
            toast.textContent = "주소가 복사되었습니다: " + text.substring(0, 20) + "...";
            toast.className = "show";
            setTimeout(() => { toast.className = toast.className.replace("show", ""); }, 3000);
        };

        // --- Event Listeners ---
        function setupEventListeners() {
            els.updateSettings.onclick = () => {
                appData.city = els.city.value; 
                appData.tripStartDate = els.startDate.value; 
                
                const keyInput = els.userApiKey.value.trim();
                if(keyInput) localStorage.setItem('trip_planner_gemini_key', keyInput);
                
                appData.tripDuration = parseInt(els.duration.value);
                for(let i=1; i<=appData.tripDuration; i++) {
                    if(!appData[`day${i}`]) appData[`day${i}`]=[];
                }
                
                saveData(); renderApp(); alert("설정이 저장되었습니다.");
                fetchExchangeRate();
            };
            
            const handleBudgetChange = () => {
                appData.totalBudget = els.budgetInput.value;
                appData.budgetCurrency = els.budgetCurrSel.value;
                calculateBudget(); saveData(); renderExpenseList();
            };
            els.budgetInput.onchange = handleBudgetChange;
            els.budgetCurrSel.onchange = handleBudgetChange;

            els.notesContent.oninput = (e) => { appData.notes = e.target.value; saveData(); };
            els.refreshRate.onclick = fetchExchangeRate;
            
            els.searchLocalBtn.onclick = searchLocalGems;
            els.viewSearchBtn.onclick = () => toggleMapTab('search');
            els.viewFavBtn.onclick = () => toggleMapTab('favorites');
            
            els.addExpBtn.onclick = () => {
                if(!els.expAmt.value || !els.expDesc.value) return;
                appData.expenses = [{id:Date.now().toString(), date:els.expDate.value, category:els.expCat.value, amount:parseFloat(els.expAmt.value), currency:els.expCurr.value, description:els.expDesc.value}, ...appData.expenses];
                els.expAmt.value=''; els.expDesc.value=''; renderApp(); saveData();
            };
            
            els.imgUpload.onchange = (e) => { const f=e.target.files[0]; if(f){const r=new FileReader(); r.onload=e=>{els.imgPreview.src=e.target.result; els.previewBox.classList.remove('hidden'); els.translateBtn.disabled=false;}; r.readAsDataURL(f); }};
            els.closePreview.onclick = () => { els.previewBox.classList.add('hidden'); els.imgUpload.value=''; els.translateBtn.disabled=true; };
            els.translateBtn.onclick = async () => {
                const key = getApiKey();
                if(!key) return alert("API Key가 필요합니다. 설정에 입력해주세요.");
                const f = els.imgUpload.files[0]; if(!f) return;
                els.translateBtn.disabled=true; els.translateBtn.textContent="번역 중...";
                try {
                    const b64 = await new Promise(r=>{const rd=new FileReader(); rd.onload=()=>r(rd.result.split(',')[1]); rd.readAsDataURL(f);});
                    const res = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${key}`, {
                        method:'POST', body:JSON.stringify({contents:[{parts:[{text:"Translate Japanese menu to Korean. Format: 'Item (Pronunciation): Description'"},{inlineData:{mimeType:f.type, data:b64}}]}]})
                    });
                    const d = await res.json();
                    els.transResult.classList.remove('hidden'); els.transResultText.textContent = d.candidates?.[0]?.content?.parts?.[0]?.text||"실패";
                } catch(e){alert("Error: " + e.message);} finally {els.translateBtn.disabled=false; els.translateBtn.textContent="번역하기";}
            };
        }

        async function fetchExchangeRate() {
            const key = getApiKey();
            if(!key) { els.rate.textContent = "Key?"; return; }
            els.rate.textContent = "...";
            
            // Exponential Backoff Logic
            for (let attempt = 0; attempt < 3; attempt++) {
                try {
                    const res = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${key}`, {
                        method:'POST', body:JSON.stringify({contents:[{parts:[{text:"Current JPY to KRW rate for 100 JPY (number only)."}]}], tools:[{"google_search":{}}]})
                    });
                    
                    if (!res.ok) {
                        const errorBody = await res.json();
                        console.error(`Attempt ${attempt + 1}: HTTP Error ${res.status}`, errorBody);
                        throw new Error("HTTP Status Error");
                    }
                    
                    const d = await res.json();
                    const text = d.candidates?.[0]?.content?.parts?.[0]?.text;
                    const num = text?.match(/\d+(\.\d+)?/);

                    if(num) { 
                        currentJpyRate = parseFloat(num[0])/100; 
                        els.rate.textContent=Math.round(parseFloat(num[0])); 
                        calculateBudget(); 
                        renderExpenseList(); 
                        return; // Success, exit function
                    } else {
                        console.error("Attempt " + (attempt + 1) + ": Failed to parse rate:", text);
                        throw new Error("Parse Fail");
                    }
                } catch(e) { 
                    if (attempt < 2) {
                        const delay = Math.pow(2, attempt) * 1000; // 1s, 2s delay
                        console.warn(`Retrying in ${delay / 1000}s...`);
                        await new Promise(resolve => setTimeout(resolve, delay));
                    } else {
                        console.error("Exchange Rate Fetch Error after 3 attempts:", e);
                        els.rate.textContent="API Fail"; 
                    }
                }
            }
        }

        init();
    </script>
</body>
</html>
