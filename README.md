
<html lang="en" id="mainHtml">
<!-- VERSION 2.0.4 - FORCED CONTRAST & WIDTH FIX -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Tactical Hub - Pro Analysis</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        :root { --emerald: #10b981; --blue: #3b82f6; --red: #ef4444; --dark: #020617; }
        body { background-color: var(--dark); color: white; font-family: 'Cairo', sans-serif; }
        
        /* TABLE CONTAINER FIX */
        .glass-panel { 
            background: #0f172a !important; 
            border: 1px solid rgba(255, 255, 255, 0.1); 
            border-radius: 12px; 
            overflow: hidden;
        }

        /* ROW STYLING - FORCING DARK BACKGROUND */
        .table-row-custom {
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            display: flex;
            align-items: center;
            background-color: #1e293b !important; /* Deep Blue/Grey */
        }

        /* LABEL STYLING - FORCING WHITE TEXT */
        .label-cell {
            width: 75%;
            padding: 14px 20px;
            color: #ffffff !important; /* PURE WHITE */
            font-weight: 800 !important;
            font-size: 0.95rem;
            text-transform: uppercase;
            background-color: #111827 !important; /* darker shade for text area */
            border-right: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* INPUT AREA STYLING */
        .value-cell {
            width: 25%;
            padding: 10px;
            text-align: center;
            background-color: #1e293b !important;
        }

        .input-field { 
            background: #020617 !important; 
            border: 1px solid var(--blue) !important; 
            color: #ffffff !important; 
            padding: 6px; 
            border-radius: 4px; 
            width: 90%; 
            text-align: center; 
            font-weight: 900; 
            font-size: 1rem;
            outline: none;
        }

        .select-field { 
            background: #064e3b !important; 
            border: 1px solid var(--emerald) !important; 
            color: #ffffff !important; 
            padding: 6px; 
            border-radius: 4px; 
            width: 90%; 
            font-weight: 900; 
            cursor: pointer;
            font-size: 0.8rem;
        }

        .alpha-banner { background: linear-gradient(90deg, #064e3b, #020617); border-bottom: 2px solid var(--emerald); padding: 12px; text-align: center; font-weight: 900; }
        .lang-toggle { position: fixed; top: 20px; right: 20px; z-index: 1000; cursor: pointer; background: var(--blue); padding: 10px 20px; border-radius: 50px; font-weight: 900; }
        
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

    <div class="max-w-7xl mx-auto p-4 lg:p-10 space-y-10">
        <header class="text-center space-y-2">
            <h1 class="text-4xl lg:text-6xl font-black text-emerald-400 uppercase tracking-tighter" id="txtMainTitle">AI Tactical Hub</h1>
            <p class="text-slate-500 text-xs lg:text-sm font-bold uppercase tracking-[0.3em]" id="txtSubTitle">Professional Match Intelligence</p>
        </header>

        <!-- TABLES SECTION -->
        <section class="space-y-6 no-print">
            <h2 class="text-xl font-black border-l-4 border-emerald-500 pl-4 uppercase text-white" id="txtStep1">1. Seasonal Statistics</h2>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <!-- TEAM A -->
                <div class="glass-panel border-t-4 border-blue-500">
                    <div class="bg-blue-900/50 p-4">
                        <input type="text" id="nameA" value="Team Alpha" oninput="updateMappingOptions()" class="bg-transparent font-black text-white uppercase outline-none text-xl w-full">
                    </div>
                    <div id="tableBodyA"></div>
                </div>

                <!-- TEAM B -->
                <div class="glass-panel border-t-4 border-red-500">
                    <div class="bg-red-900/50 p-4">
                        <input type="text" id="nameB" value="Team Beta" oninput="updateMappingOptions()" class="bg-transparent font-black text-white uppercase outline-none text-xl w-full">
                    </div>
                    <div id="tableBodyB"></div>
                </div>
            </div>
        </section>

        <!-- VIDEO SECTION -->
        <section class="space-y-6 no-print">
            <h2 class="text-xl font-black border-l-4 border-blue-500 pl-4 uppercase text-white" id="txtStep2">2. Video Mapping</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="glass-panel p-5 space-y-4">
                    <label class="text-[10px] font-black uppercase text-emerald-400" id="lblMap1">Team on Left in Video:</label>
                    <select id="mapV1" class="select-field w-full"></select>
                    <div onclick="document.getElementById('file1').click()" class="aspect-video bg-black flex items-center justify-center cursor-pointer rounded-lg border-2 border-dashed border-white/10">
                        <video id="vPrev1" class="hidden w-full h-full object-cover rounded-lg"></video>
                        <span id="vPrompt1" class="text-white text-xs font-black">UPLOAD VIDEO 1</span>
                    </div>
                    <input type="file" id="file1" class="hidden" accept="video/*" onchange="preview(event, 1)">
                </div>

                <div class="glass-panel p-5 space-y-4">
                    <label class="text-[10px] font-black uppercase text-emerald-400" id="lblMap2">Team on Left in Video:</label>
                    <select id="mapV2" class="select-field w-full"></select>
                    <div onclick="document.getElementById('file2').click()" class="aspect-video bg-black flex items-center justify-center cursor-pointer rounded-lg border-2 border-dashed border-white/10">
                        <video id="vPrev2" class="hidden w-full h-full object-cover rounded-lg"></video>
                        <span id="vPrompt2" class="text-white text-xs font-black">UPLOAD VIDEO 2</span>
                    </div>
                    <input type="file" id="file2" class="hidden" accept="video/*" onchange="preview(event, 2)">
                </div>
            </div>
        </section>

        <div class="text-center py-6 no-print">
            <button onclick="processAI()" class="bg-emerald-600 hover:bg-emerald-500 text-white px-12 py-5 rounded-xl font-black text-2xl shadow-xl transition-all" id="btnRun">RUN AI ANALYSES</button>
        </div>

        <!-- RESULTS -->
        <section id="results" class="hidden space-y-6 pb-20">
            <div class="glass-panel p-8 border-t-8 border-emerald-500 text-center">
                <h2 class="text-lg font-black text-emerald-400 uppercase mb-8" id="resTitle">Tactical Win Probability</h2>
                <div class="flex flex-col lg:flex-row justify-around items-center gap-8">
                    <div class="flex-1">
                        <div id="resNameA" class="text-2xl font-black text-blue-400 uppercase">---</div>
                        <div id="resProbA" class="text-7xl font-black text-white mt-2">0%</div>
                    </div>
                    <div class="w-full max-w-sm h-6 bg-slate-900 rounded-full flex overflow-hidden border border-white/20">
                        <div id="barA" class="bg-blue-600 h-full"></div>
                        <div id="barB" class="bg-red-600 h-full"></div>
                    </div>
                    <div class="flex-1">
                        <div id="resNameB" class="text-2xl font-black text-red-400 uppercase">---</div>
                        <div id="resProbB" class="text-7xl font-black text-white mt-2">0%</div>
                    </div>
                </div>
                <div id="aiLogic" class="mt-8 p-6 bg-white/5 rounded-xl text-white font-medium text-sm border-l-4 border-emerald-500 text-left"></div>
            </div>
        </section>
    </div>

    <script>
        const i18n = {
            en: {
                banner: "⚠️ Team Alpha is the team that appears on the LEFT of each video clip.",
                mainTitle: "AI Tactical Hub",
                subTitle: "Professional Match Intelligence",
                step1: "1. Seasonal Statistics",
                step2: "2. Video Mapping",
                fields: ["Games Played (GP)", "Points (PTS)", "Wins (W)", "Draws (D)", "Losses (L)", "Goals For (GF)", "Goals Against (GA)", "Goal Diff (GD)", "Location"],
                locationOpts: ["Home", "Away", "Neutral"],
                run: "RUN AI ANALYSES",
                resT: "Tactical Win Probability",
                lang: "العربية"
            },
            ar: {
                banner: "⚠️ الفريق 'ألفا' هو الفريق الذي يظهر على يسار شاشة الفيديو دائماً.",
                mainTitle: "مركز التوقعات الذكي",
                subTitle: "ذكاء المباراة الاحترافي",
                step1: "1. الإحصائيات الموسمية",
                step2: "2. ربط الفيديو",
                fields: ["المباريات (GP)", "النقاط (PTS)", "الفوز (W)", "التعادل (D)", "الخسارة (L)", "الأهداف له (GF)", "الأهداف عليه (GA)", "الفارق (GD)", "الموقع"],
                locationOpts: ["داخل الأرض", "خارج الأرض", "أرض محايدة"],
                run: "بدء التحليل",
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
                    return `<div class="table-row-custom">
                        <div class="label-cell ${align}">${l.fields[i]}</div>
                        <div class="value-cell">
                            <select id="loc${team}" class="select-field">
                                <option value="home">${l.locationOpts[0]}</option>
                                <option value="away">${l.locationOpts[1]}</option>
                                <option value="neutral">${l.locationOpts[2]}</option>
                            </select>
                        </div>
                    </div>`;
                }
                return `<div class="table-row-custom">
                    <div class="label-cell ${align}">${l.fields[i]}</div>
                    <div class="value-cell"><input type="number" id="${key}${team}" class="input-field" value="0" ${key==='var'?'readonly':''}></div>
                </div>`;
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
            document.getElementById('resProbA').innerText = pA + "%";
            document.getElementById('resProbB').innerText = pB + "%";
            document.getElementById('barA').style.width = pA + "%";
            document.getElementById('barB').style.width = pB + "%";
            
            document.getElementById('aiLogic').innerText = currentLang === 'en' 
                ? `Tactical analysis finished. Efficiency scores: ${a.name} (${sA.toFixed(1)}) vs ${b.name} (${sB.toFixed(1)}). Weights applied for ${a.loc} advantage.`
                : `تم الانتهاء من التحليل التكتيكي. درجات الكفاءة: ${a.name} (${sA.toFixed(1)}) مقابل ${b.name} (${sB.toFixed(1)}). تم تطبيق الأوزان لميزة الـ ${a.loc}.`;

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
