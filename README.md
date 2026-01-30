# firsttime
first html
<!DOCTYPE html>
<html lang="en" id="mainHtml">
<!-- VERSION 2.0.3 - LAYOUT & CONTRAST OPTIMIZED -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Tactical Hub - Pro Analysis</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        :root { --emerald: #10b981; --blue: #3b82f6; --red: #ef4444; --dark: #020617; }
        body { background-color: var(--dark); color: white; font-family: 'Cairo', sans-serif; overflow-x: hidden; }
        
        .glass-panel { 
            background: #0f172a; 
            border: 2px solid rgba(255, 255, 255, 0.1); 
            border-radius: 16px; 
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        /* TEXT CLARITY FIX */
        .table-row-item {
            background: #1e293b;
            border-bottom: 2px solid #0f172a;
        }

        .label-text {
            color: #ffffff !important;
            font-weight: 800;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.025em;
            padding: 15px;
            white-space: nowrap; /* Prevents text from cutting off */
        }

        /* INPUT DESIGN */
        .input-cell { 
            background: #020617 !important; 
            border: 2px solid var(--blue) !important; 
            color: #ffffff !important; 
            padding: 8px; 
            border-radius: 6px; 
            width: 90%; 
            text-align: center; 
            font-weight: 900; 
            font-size: 1.1rem;
            outline: none;
        }

        .select-cell { 
            background: #064e3b !important; 
            border: 2px solid var(--emerald) !important; 
            color: #ffffff !important; 
            padding: 8px; 
            border-radius: 6px; 
            width: 95%; 
            font-weight: 900; 
            cursor: pointer;
        }

        .alpha-banner { background: linear-gradient(90deg, #064e3b, #020617); border-bottom: 2px solid var(--emerald); padding: 12px; text-align: center; font-weight: 900; }
        .lang-toggle { position: fixed; top: 20px; right: 20px; z-index: 1000; cursor: pointer; background: var(--blue); padding: 10px 20px; border-radius: 50px; font-weight: 900; box-shadow: 0 4px 15px rgba(0,0,0,0.4); }
        
        @media print { .no-print { display: none; } }
    </style>
</head>
<body dir="ltr">

    <div class="lang-toggle flex items-center gap-2 no-print" onclick="toggleLanguage()">
        <span id="langName">العربية</span> 🌐
    </div>

    <div class="alpha-banner no-print">
        <span id="txtBanner" class="text-white">⚠️ Team Alpha is the team that appears on the LEFT of each video clip.</span>
    </div>

    <div class="max-w-7xl mx-auto p-4 lg:p-10 space-y-12">
        <header class="text-center space-y-4">
            <h1 class="text-4xl lg:text-7xl font-black text-emerald-400 uppercase tracking-tighter" id="txtMainTitle">AI Tactical Hub</h1>
            <p class="text-slate-400 text-sm lg:text-lg font-bold uppercase tracking-widest" id="txtSubTitle">Location-Aware Analysis & Historical Mapping</p>
        </header>

        <!-- TABLES SECTION -->
        <section class="space-y-6 no-print">
            <h2 class="text-2xl font-black border-l-4 border-emerald-500 pl-4 uppercase text-white" id="txtStep1">1. Mandatory Seasonal Statistics</h2>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
                <!-- TEAM A -->
                <div class="glass-panel overflow-hidden border-t-4 border-blue-500">
                    <div class="bg-blue-600/40 p-5">
                        <input type="text" id="nameA" value="Team Alpha" oninput="updateMappingOptions()" class="bg-transparent font-black text-white uppercase outline-none text-2xl w-full placeholder-blue-200">
                    </div>
                    <table class="w-full table-fixed border-collapse">
                        <colgroup>
                            <col style="width: 70%;">
                            <col style="width: 30%;">
                        </colgroup>
                        <tbody id="tableBodyA"></tbody>
                    </table>
                </div>

                <!-- TEAM B -->
                <div class="glass-panel overflow-hidden border-t-4 border-red-500">
                    <div class="bg-red-600/40 p-5">
                        <input type="text" id="nameB" value="Team Beta" oninput="updateMappingOptions()" class="bg-transparent font-black text-white uppercase outline-none text-2xl w-full placeholder-red-200">
                    </div>
                    <table class="w-full table-fixed border-collapse">
                        <colgroup>
                            <col style="width: 70%;">
                            <col style="width: 30%;">
                        </colgroup>
                        <tbody id="tableBodyB"></tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- VIDEO SECTION -->
        <section class="space-y-6 no-print">
            <h2 class="text-2xl font-black border-l-4 border-blue-500 pl-4 uppercase text-white" id="txtStep2">2. Last Match Video Mapping</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="glass-panel p-6 space-y-4">
                    <label class="text-xs font-black uppercase text-emerald-400" id="lblMap1">Which team is on the LEFT?</label>
                    <select id="mapV1" class="select-cell"></select>
                    <div onclick="document.getElementById('file1').click()" class="aspect-video bg-black flex items-center justify-center cursor-pointer rounded-xl border-2 border-dashed border-white/20 hover:border-emerald-500 transition-all">
                        <video id="vPrev1" class="hidden w-full h-full object-cover rounded-xl"></video>
                        <span id="vPrompt1" class="text-white font-black text-center p-4">CLICK TO UPLOAD VIDEO #1</span>
                    </div>
                    <input type="file" id="file1" class="hidden" accept="video/*" onchange="preview(event, 1)">
                </div>

                <div class="glass-panel p-6 space-y-4">
                    <label class="text-xs font-black uppercase text-emerald-400" id="lblMap2">Which team is on the LEFT?</label>
                    <select id="mapV2" class="select-cell"></select>
                    <div onclick="document.getElementById('file2').click()" class="aspect-video bg-black flex items-center justify-center cursor-pointer rounded-xl border-2 border-dashed border-white/20 hover:border-emerald-500 transition-all">
                        <video id="vPrev2" class="hidden w-full h-full object-cover rounded-xl"></video>
                        <span id="vPrompt2" class="text-white font-black text-center p-4">CLICK TO UPLOAD VIDEO #2</span>
                    </div>
                    <input type="file" id="file2" class="hidden" accept="video/*" onchange="preview(event, 2)">
                </div>
            </div>
        </section>

        <div class="text-center py-10 no-print">
            <button onclick="processAI()" class="bg-emerald-600 hover:bg-emerald-500 text-white px-20 py-8 rounded-2xl font-black text-3xl shadow-2xl transition-transform active:scale-95" id="btnRun">RUN AI ANALYSES</button>
        </div>

        <!-- RESULTS -->
        <section id="results" class="hidden space-y-6 pb-20">
            <div class="glass-panel p-10 border-t-8 border-emerald-500 text-center shadow-[0_0_50px_rgba(16,185,129,0.2)]">
                <h2 class="text-2xl font-black text-emerald-400 uppercase mb-10" id="resTitle">Tactical Win Probability</h2>
                <div class="flex flex-col lg:flex-row justify-around items-center gap-10">
                    <div class="flex-1">
                        <div id="resNameA" class="text-4xl font-black text-blue-400 uppercase">---</div>
                        <div id="resLocA" class="text-sm text-white font-bold opacity-70 uppercase">---</div>
                        <div id="resProbA" class="text-8xl font-black text-white mt-4">0%</div>
                    </div>
                    <div class="w-full max-w-md h-8 bg-slate-900 rounded-full flex overflow-hidden border-2 border-white/20">
                        <div id="barA" class="bg-blue-600 h-full transition-all duration-1000"></div>
                        <div id="barB" class="bg-red-600 h-full transition-all duration-1000"></div>
                    </div>
                    <div class="flex-1">
                        <div id="resNameB" class="text-4xl font-black text-red-400 uppercase">---</div>
                        <div id="resLocB" class="text-sm text-white font-bold opacity-70 uppercase">---</div>
                        <div id="resProbB" class="text-8xl font-black text-white mt-4">0%</div>
                    </div>
                </div>
                <div id="aiLogic" class="mt-10 p-8 bg-white/5 rounded-2xl text-white font-medium text-lg border-l-4 border-emerald-500 text-left leading-relaxed"></div>
            </div>
        </section>
    </div>

    <script>
        const i18n = {
            en: {
                banner: "⚠️ Team Alpha is the team that appears on the LEFT of each video clip.",
                mainTitle: "AI Tactical Hub",
                subTitle: "Location-Aware Analysis & Historical Mapping",
                step1: "1. Mandatory Seasonal Statistics",
                step2: "2. Last Match Video Mapping",
                fields: ["Games Played (GP)", "Total Points (PTS)", "Winning Games (W)", "Draw Games (D)", "Lost Games (L)", "Goals Made (GF)", "Goals Against (GA)", "Goal Variance (GD)", "Match Location"],
                locationOpts: ["Home Ground", "Away Ground", "Neutral Ground"],
                run: "RUN AI ANALYSES",
                resT: "Tactical Win Probability",
                lang: "العربية"
            },
            ar: {
                banner: "⚠️ الفريق 'ألفا' هو الفريق الذي يظهر على يسار شاشة الفيديو دائماً.",
                mainTitle: "مركز التوقعات الذكي",
                subTitle: "التحليل المكاني وربط سجلات الفيديو",
                step1: "1. الإحصائيات الموسمية الإلزامية",
                step2: "2. ربط فيديو آخر مباراة مسجلة",
                fields: ["المباريات الملعبة (GP)", "مجموع النقاط (PTS)", "مباريات الفوز (W)", "مباريات التعادل (D)", "مباريات الخسارة (L)", "أهداف مسجلة (GF)", "أهداف مستلمة (GA)", "فارق الأهداف (GD)", "موقع المباراة"],
                locationOpts: ["داخل الأرض", "خارج الأرض", "أرض محايدة"],
                run: "بدء التحليل الذكي",
                resT: "احتمالية الفوز التكتيكية",
                lang: "English"
            }
        };

        const fieldKeys = ["gp", "pts", "w", "d", "l", "gf", "ga", "var", "loc"];
        let currentLang = 'en';

        function renderStaticText() {
            const l = i18n[currentLang];
            document.getElementById('langName').innerText = l.lang;
            document.getElementById('txtBanner').innerText = l.banner;
            document.getElementById('txtMainTitle').innerText = l.mainTitle;
            document.getElementById('txtSubTitle').innerText = l.subTitle;
            document.getElementById('txtStep1').innerText = l.step1;
            document.getElementById('txtStep2').innerText = l.step2;
            document.getElementById('btnRun').innerText = l.run;
            document.getElementById('resTitle').innerText = l.resT;
        }

        function renderTables() {
            const l = i18n[currentLang];
            const align = currentLang === 'ar' ? 'text-right' : 'text-left';
            
            const generateHTML = (team) => fieldKeys.map((key, i) => {
                if(key === 'loc') {
                    return `<tr class="table-row-item">
                        <td class="label-text ${align}">${l.fields[i]}</td>
                        <td class="p-2 text-center">
                            <select id="loc${team}" class="select-cell">
                                <option value="home">${l.locationOpts[0]}</option>
                                <option value="away">${l.locationOpts[1]}</option>
                                <option value="neutral">${l.locationOpts[2]}</option>
                            </select>
                        </td>
                    </tr>`;
                }
                return `<tr class="table-row-item">
                    <td class="label-text ${align}">${l.fields[i]}</td>
                    <td class="p-2 text-center"><input type="number" id="${key}${team}" class="input-cell" value="0" ${key==='var'?'readonly':''}></td>
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
                return Math.max(base * getMultiplier(t.loc), 1);
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
            
            document.getElementById('aiLogic').innerText = currentLang === 'en' 
                ? `SUCCESS: Neural weights applied to ${a.name} vs ${b.name}. Logic: (Points/GP * 40) + (Wins/GP * 20) + (GD/GP * 40) modified by location multipliers (${getMultiplier(a.loc)}x vs ${getMultiplier(b.loc)}x).`
                : `تم بنجاح: تم تطبيق الأوزان العصبية لـ ${a.name} ضد ${b.name}. المنطق: (النقاط/المباريات * 40) + (الفوز/المباريات * 20) + (الفارق/المباريات * 40) معدلة بمضاعفات الموقع (${getMultiplier(a.loc)}x vs ${getMultiplier(b.loc)}x).`;

            window.scrollTo({ top: document.getElementById('results').offsetTop - 20, behavior: 'smooth' });
        }

        function toggleLanguage() {
            currentLang = currentLang === 'en' ? 'ar' : 'en';
            document.getElementById('mainHtml').dir = currentLang === 'ar' ? 'rtl' : 'ltr';
            renderStaticText();
            renderTables();
        }

        window.addEventListener('DOMContentLoaded', () => {
            renderStaticText();
            renderTables();
        });
    </script>
</body>
</html>
