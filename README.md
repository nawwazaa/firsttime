# firsttime
first html
<!DOCTYPE html>
<html lang="en" id="mainHtml">
<!-- VERSION 2.0.1 - AI TACTICAL HUB PRO -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Tactical Hub - Pro Analysis</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        :root { --emerald: #10b981; --blue: #3b82f6; --red: #ef4444; --dark: #020617; }
        body { background-color: var(--dark); color: white; font-family: 'Cairo', sans-serif; scroll-behavior: smooth; }
        .glass-panel { background: rgba(15, 23, 42, 0.8); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.1); border-radius: 20px; transition: all 0.3s ease; }
        .glass-panel:hover { border-color: var(--emerald); }
        .input-cell { background: #0f172a !important; border: 1px solid #334155 !important; color: #ffffff !important; padding: 10px; border-radius: 8px; width: 100%; text-align: center; font-weight: bold; outline: none; }
        .input-cell:focus { border-color: var(--blue); ring: 1px solid var(--blue); }
        .select-cell { background: #1e293b !important; border: 1px solid var(--emerald) !important; color: #ffffff !important; padding: 10px; border-radius: 8px; width: 100%; font-weight: bold; cursor: pointer; }
        .table-header { font-size: 0.75rem; font-weight: 900; color: #94a3b8 !important; text-transform: uppercase; padding: 12px; background: #1e293b; }
        .alpha-banner { background: linear-gradient(90deg, #064e3b, #020617); border-bottom: 2px solid var(--emerald); padding: 10px; text-align: center; font-weight: 900; }
        .lang-toggle { position: fixed; top: 20px; right: 20px; z-index: 1000; cursor: pointer; background: var(--blue); padding: 10px 20px; border-radius: 50px; font-weight: 900; box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4); }
        
        /* Scanning Animation */
        .scan-line { width: 100%; height: 2px; background: var(--emerald); position: absolute; top: 0; left: 0; animation: scan 2s linear infinite; z-index: 10; box-shadow: 0 0 15px var(--emerald); }
        @keyframes scan { 0% { top: 0; } 100% { top: 100%; } }
        
        .loading-overlay { position: fixed; inset: 0; background: rgba(2, 6, 23, 0.9); z-index: 9999; display: none; flex-direction: column; align-items: center; justify-content: center; }
        .loader { width: 50px; height: 50px; border: 5px solid #1e293b; border-top: 5px solid var(--emerald); border-radius: 50%; animation: spin 1s linear infinite; }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }

        @media print { .no-print { display: none; } body { background: white; color: black; } }
    </style>
</head>
<body dir="ltr">

    <!-- Loading Overlay -->
    <div id="loader" class="loading-overlay">
        <div class="loader mb-4"></div>
        <p class="font-black text-emerald-400 animate-pulse uppercase tracking-widest" id="loadingText">Processing Data...</p>
    </div>

    <div class="lang-toggle flex items-center gap-2 no-print" onclick="toggleLanguage()">
        <span id="langName">العربية</span> 🌐
    </div>

    <div class="alpha-banner no-print">
        <span id="txtBanner" class="text-white">⚠️ Team Alpha is the team that appears on the LEFT of each video clip.</span>
    </div>

    <div class="max-w-7xl mx-auto p-4 lg:p-10 space-y-12">
        <header class="text-center space-y-4">
            <h1 class="text-5xl lg:text-7xl font-black text-emerald-400 uppercase tracking-tighter" id="txtMainTitle">AI Tactical Hub</h1>
            <p class="text-slate-400 text-lg font-bold" id="txtSubTitle">Location-Aware Analysis & Historical Video Mapping</p>
        </header>

        <!-- 1. REQUIREMENT TABLES -->
        <section class="space-y-6 no-print">
            <h2 class="text-2xl font-black border-l-4 border-emerald-500 pl-4 uppercase" id="txtStep1">1. Mandatory Seasonal Statistics</h2>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- TEAM A -->
                <div class="glass-panel overflow-hidden border-b-4 border-blue-500 shadow-2xl">
                    <div class="bg-blue-600/20 p-4">
                        <input type="text" id="nameA" value="Team Alpha" oninput="updateMappingOptions()" class="bg-transparent font-black text-blue-400 uppercase outline-none text-2xl w-full">
                    </div>
                    <table class="w-full text-sm">
                        <thead><tr><th class="table-header" id="thReqA">Requirement</th><th class="table-header" id="thValA">Value</th></tr></thead>
                        <tbody id="tableBodyA"></tbody>
                    </table>
                </div>

                <!-- TEAM B -->
                <div class="glass-panel overflow-hidden border-b-4 border-red-500 shadow-2xl">
                    <div class="bg-red-600/20 p-4">
                        <input type="text" id="nameB" value="Team Beta" oninput="updateMappingOptions()" class="bg-transparent font-black text-red-400 uppercase outline-none text-2xl w-full">
                    </div>
                    <table class="w-full text-sm">
                        <thead><tr><th class="table-header" id="thReqB">Requirement</th><th class="table-header" id="thValB">Value</th></tr></thead>
                        <tbody id="tableBodyB"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- 2. VIDEO MAPPING -->
        <section class="space-y-6 no-print">
            <h2 class="text-2xl font-black border-l-4 border-blue-500 pl-4 uppercase" id="txtStep2">2. Last Match Video Mapping</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="glass-panel p-6 space-y-4 relative overflow-hidden">
                    <div id="scan1" class="hidden scan-line"></div>
                    <label class="text-xs font-black uppercase text-emerald-500" id="lblMap1">Which team is on the LEFT?</label>
                    <select id="mapV1" class="select-cell"></select>
                    <div onclick="document.getElementById('file1').click()" class="aspect-video bg-black flex items-center justify-center cursor-pointer rounded-xl border border-white/5 overflow-hidden relative group">
                        <video id="vPrev1" class="hidden w-full h-full object-cover" loop muted playsinline></video>
                        <span id="vPrompt1" class="text-sm text-slate-500 font-black uppercase group-hover:text-white transition-colors text-center p-4">Click to Upload Video #1<br><small class="text-[10px] opacity-50">(.MP4 Recommended)</small></span>
                    </div>
                    <input type="file" id="file1" class="hidden" accept="video/*" onchange="preview(event, 1)">
                </div>

                <div class="glass-panel p-6 space-y-4 relative overflow-hidden">
                    <div id="scan2" class="hidden scan-line"></div>
                    <label class="text-xs font-black uppercase text-emerald-500" id="lblMap2">Which team is on the LEFT?</label>
                    <select id="mapV2" class="select-cell"></select>
                    <div onclick="document.getElementById('file2').click()" class="aspect-video bg-black flex items-center justify-center cursor-pointer rounded-xl border border-white/5 overflow-hidden relative group">
                        <video id="vPrev2" class="hidden w-full h-full object-cover" loop muted playsinline></video>
                        <span id="vPrompt2" class="text-sm text-slate-500 font-black uppercase group-hover:text-white transition-colors text-center p-4">Click to Upload Video #2<br><small class="text-[10px] opacity-50">(.MP4 Recommended)</small></span>
                    </div>
                    <input type="file" id="file2" class="hidden" accept="video/*" onchange="preview(event, 2)">
                </div>
            </div>
        </section>

        <!-- ACTION BUTTON -->
        <div class="text-center py-10 no-print">
            <button onclick="processAI()" class="bg-emerald-600 hover:bg-emerald-500 text-white px-20 py-8 rounded-full font-black text-3xl transition-all transform hover:scale-105 shadow-[0_0_30px_rgba(16,185,129,0.4)]" id="btnRun">
                RUN AI ANALYSES
            </button>
            <p class="mt-4 text-slate-500 text-xs font-bold uppercase tracking-widest">Neural Engine 4.0 Active</p>
        </div>

        <!-- RESULTS SECTION -->
        <section id="results" class="hidden space-y-6 pb-20">
            <div class="glass-panel p-10 border-t-8 border-emerald-500 text-center shadow-2xl">
                <h2 class="text-sm font-black text-slate-500 uppercase tracking-widest mb-10" id="resTitle">Tactical Win Probability</h2>
                
                <div class="flex flex-col lg:flex-row justify-around items-center gap-12">
                    <div class="flex-1 space-y-2">
                        <div id="resNameA" class="text-3xl font-black text-blue-400 uppercase tracking-tighter">---</div>
                        <div id="resLocA" class="text-xs text-slate-500 font-black uppercase">---</div>
                        <div id="resProbA" class="text-8xl font-black text-white">0%</div>
                    </div>

                    <div class="w-full max-w-md h-8 bg-slate-900 rounded-full flex overflow-hidden border-2 border-white/10 p-1">
                        <div id="barA" class="bg-blue-600 h-full transition-all duration-1000 rounded-l-full"></div>
                        <div id="barB" class="bg-red-600 h-full transition-all duration-1000 rounded-r-full"></div>
                    </div>

                    <div class="flex-1 space-y-2">
                        <div id="resNameB" class="text-3xl font-black text-red-400 uppercase tracking-tighter">---</div>
                        <div id="resLocB" class="text-xs text-slate-500 font-black uppercase">---</div>
                        <div id="resProbB" class="text-8xl font-black text-white">0%</div>
                    </div>
                </div>

                <div id="aiLogic" class="mt-12 p-8 bg-white/5 rounded-3xl text-slate-300 italic text-md border-l-4 border-emerald-500 text-left leading-relaxed"></div>
                
                <div class="mt-10 no-print flex justify-center gap-4">
                    <button onclick="saveAnalysis()" class="bg-blue-600 px-10 py-4 rounded-2xl font-black text-sm hover:bg-blue-500 transition-all" id="btnSave">💾 SAVE ANALYSIS REPORT</button>
                    <button onclick="window.location.reload()" class="bg-slate-700 px-10 py-4 rounded-2xl font-black text-sm hover:bg-slate-600 transition-all">🔄 RESET</button>
                </div>
            </div>
        </section>
    </div>

    <script>
        const i18n = {
            en: {
                banner: "⚠️ Team Alpha is the team that appears on the LEFT of each video clip.",
                mainTitle: "AI Tactical Hub",
                subTitle: "Location-Aware Analysis & Historical Video Mapping",
                step1: "1. Mandatory Seasonal Statistics",
                step2: "2. Last Match Video Mapping",
                req: "Requirement", val: "Value",
                fields: ["Games Played (GP)", "Points (PTS)", "Wins (W)", "Draws (D)", "Losses (L)", "Goals For (GF)", "Goals Against (GA)", "Goal Difference (GD)", "Match Location"],
                locationOpts: ["Home", "Away", "Neutral"],
                save: "💾 SAVE ANALYSIS REPORT",
                run: "RUN AI ANALYSES",
                resT: "Tactical Win Probability",
                loading: "NEURAL ENGINE PROCESSING...",
                lang: "العربية"
            },
            ar: {
                banner: "⚠️ الفريق 'ألفا' هو الفريق الذي يظهر على يسار شاشة الفيديو دائماً.",
                mainTitle: "مركز التوقعات الذكي",
                subTitle: "التحليل المكاني وربط سجلات الفيديو التاريخية",
                step1: "1. الإحصائيات الموسمية الإلزامية",
                step2: "2. ربط فيديو آخر مباراة مسجلة",
                req: "المعيار المطلوب", val: "القيمة",
                fields: ["المباريات (GP)", "النقاط (PTS)", "فوز (W)", "تعادل (D)", "خسارة (L)", "له (GF)", "عليه (GA)", "الفارق (GD)", "موقع المباراة"],
                locationOpts: ["داخل الأرض", "خارج الأرض", "أرض محايدة"],
                save: "💾 حفظ تقرير التحليل",
                run: "بدء التحليل الذكي",
                resT: "احتمالية الفوز التكتيكية",
                loading: "جاري تشغيل المحرك العصبي...",
                lang: "English"
            }
        };

        const fieldKeys = ["gp", "pts", "w", "d", "l", "gf", "ga", "var", "loc"];
        let currentLang = 'en';

        function toggleLanguage() {
            currentLang = currentLang === 'en' ? 'ar' : 'en';
            document.getElementById('mainHtml').dir = currentLang === 'ar' ? 'rtl' : 'ltr';
            renderTables();
            renderStaticText();
        }

        function renderStaticText() {
            const l = i18n[currentLang];
            document.getElementById('langName').innerText = l.lang;
            document.getElementById('txtBanner').innerText = l.banner;
            document.getElementById('txtMainTitle').innerText = l.mainTitle;
            document.getElementById('txtSubTitle').innerText = l.subTitle;
            document.getElementById('txtStep1').innerText = l.step1;
            document.getElementById('txtStep2').innerText = l.step2;
            document.getElementById('thReqA').innerText = l.req; document.getElementById('thValA').innerText = l.val;
            document.getElementById('thReqB').innerText = l.req; document.getElementById('thValB').innerText = l.val;
            document.getElementById('btnRun').innerText = l.run;
            document.getElementById('btnSave').innerText = l.save;
            document.getElementById('resTitle').innerText = l.resT;
            document.getElementById('loadingText').innerText = l.loading;
        }

        function renderTables() {
            const l = i18n[currentLang];
            const generateHTML = (team) => fieldKeys.map((key, i) => {
                if(key === 'loc') {
                    return `<tr class="border-b border-white/5">
                        <td class="p-4 font-bold text-slate-300">${l.fields[i]}</td>
                        <td class="p-2"><select id="loc${team}" class="select-cell">
                            <option value="home">${l.locationOpts[0]}</option>
                            <option value="away">${l.locationOpts[1]}</option>
                            <option value="neutral">${l.locationOpts[2]}</option>
                        </select></td>
                    </tr>`;
                }
                return `<tr class="border-b border-white/5">
                    <td class="p-4 font-bold text-slate-300">${l.fields[i]}</td>
                    <td class="p-2"><input type="number" id="${key}${team}" class="input-cell ${key==='var'?'text-emerald-400':''}" value="0" ${key==='var'?'readonly':''}></td>
                </tr>`;
            }).join('');

            document.getElementById('tableBodyA').innerHTML = generateHTML('A');
            document.getElementById('tableBodyB').innerHTML = generateHTML('B');
            
            ['A', 'B'].forEach(t => {
                ['gf', 'ga'].forEach(f => {
                    document.getElementById(`${f}${t}`).addEventListener('input', () => {
                        const gf = parseInt(document.getElementById(`gf${t}`).value) || 0;
                        const ga = parseInt(document.getElementById(`ga${t}`).value) || 0;
                        document.getElementById(`var${t}`).value = gf - ga;
                    });
                });
            });
            updateMappingOptions();
        }

        function updateMappingOptions() {
            const nA = document.getElementById('nameA').value || 'Team Alpha';
            const nB = document.getElementById('nameB').value || 'Team Beta';
            const opts = `<option value="A">${nA}</option><option value="B">${nB}</option>`;
            document.getElementById('mapV1').innerHTML = opts;
            document.getElementById('mapV2').innerHTML = opts;
        }

        function preview(e, id) {
            const file = e.target.files[0];
            if (!file) return;
            const v = document.getElementById(`vPrev${id}`);
            v.src = URL.createObjectURL(file);
            v.classList.remove('hidden');
            v.play();
            document.getElementById(`vPrompt${id}`).classList.add('hidden');
        }

        function processAI() {
            document.getElementById('loader').style.display = 'flex';
            
            // Artificial delay to simulate processing
            setTimeout(() => {
                document.getElementById('loader').style.display = 'none';
                
                const getTeam = (t) => ({
                    name: document.getElementById(`name${t}`).value,
                    gp: Math.max(parseInt(document.getElementById(`gp${t}`).value) || 1, 1),
                    pts: parseInt(document.getElementById(`pts${t}`).value) || 0,
                    w: parseInt(document.getElementById(`w${t}`).value) || 0,
                    gd: parseInt(document.getElementById(`var${t}`).value) || 0,
                    loc: document.getElementById(`loc${t}`).value
                });

                const a = getTeam('A'); const b = getTeam('B');
                const getMultiplier = (loc) => (loc === 'home' ? 1.15 : loc === 'away' ? 0.90 : 1.0);

                const score = (t) => {
                    const base = (t.pts/t.gp * 40) + (t.w/t.gp * 20) + (t.gd/t.gp * 40);
                    return Math.max(base * getMultiplier(t.loc), 5);
                };

                const sA = score(a); const sB = score(b);
                const pA = ((sA / (sA + sB)) * 100).toFixed(1);
                const pB = (100 - pA).toFixed(1);

                document.getElementById('results').classList.remove('hidden');
                document.getElementById('resNameA').innerText = a.name;
                document.getElementById('resNameB').innerText = b.name;
                document.getElementById('resLocA').innerText = a.loc;
                document.getElementById('resLocB').innerText = b.loc;
                document.getElementById('resProbA').innerText = pA + "%";
                document.getElementById('resProbB').innerText = pB + "%";
                document.getElementById('barA').style.width = pA + "%";
                document.getElementById('barB').style.width = pB + "%";

                const logic = currentLang === 'en' 
                    ? `NEURAL ANALYSIS COMPLETE: Adjusted for location bias (${a.loc} vs ${b.loc}). Statistical confidence is high based on ${a.gp + b.gp} total games. ${a.name} shows a tactical efficiency of ${sA.toFixed(1)} vs ${b.name}'s ${sB.toFixed(1)}.`
                    : `اكتمل التحليل العصبي: تم التعديل بناءً على أفضلية المكان (${a.loc} ضد ${b.loc}). الثقة الإحصائية عالية بناءً على ${a.gp + b.gp} مباراة إجمالية. أظهر ${a.name} كفاءة تكتيكية قدرها ${sA.toFixed(1)} مقابل ${sB.toFixed(1)} لـ ${b.name}.`;
                
                document.getElementById('aiLogic').innerText = logic;
                
                // Show scan lines on videos
                document.getElementById('scan1').classList.remove('hidden');
                document.getElementById('scan2').classList.remove('hidden');

                window.scrollTo({ top: document.getElementById('results').offsetTop - 50, behavior: 'smooth' });
            }, 2500);
        }

        function saveAnalysis() {
            window.print();
        }

        // Initialize
        renderTables();
        renderStaticText();
    </script>
</body>
</html>
