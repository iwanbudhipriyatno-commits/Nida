<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🌸 Nida's Study Space - SMP Al Irsyad Cilacap 🌸</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome & Fonts -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&family=Quicksand:wght@500;700&display=swap" rel="stylesheet">
    
    <style>
        body {
            font-family: 'Quicksand', sans-serif;
            background: linear-gradient(180deg, #e0f2fe 0%, #f0fdf4 100%);
            min-height: 100vh;
            position: relative;
            overflow-x: hidden;
        }

        /* Background K-Pop Samar-Samar */
        .kpop-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://images.unsplash.com/photo-1534308983496-4fabb1a015ee?q=80&w=1000&auto=format&fit=crop'); /* Placeholder siluet/grup kpop aesthetic */
            background-size: cover;
            background-position: center;
            opacity: 0.04; /* Sangat samar agar mata tetap rileks membaca teks */
            z-index: -2;
            pointer-events: none;
        }

        /* Aksen Rumput Hijau di Bagian Bawah Web */
        .grass-footer {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 25px;
            background: linear-gradient(0deg, #22c55e 0%, #4ade80 100%);
            z-index: 30;
            border-top: 4px solid #16a34a;
            box-shadow: 0 -5px 15px rgba(34, 197, 94, 0.2);
            pointer-events: none;
        }

        /* Glassmorphic Cards (Biru Sejuk) */
        .glass-panel {
            background: rgba(255, 255, 255, 0.75);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(186, 230, 253, 0.5);
            box-shadow: 0 8px 32px 0 rgba(14, 165, 233, 0.08);
        }

        /* Animasi Gelembung / Bubbles Melayang */
        @keyframes floatBubble {
            0% { transform: translateY(105vh) scale(1); opacity: 0; }
            10% { opacity: 0.7; }
            90% { opacity: 0.7; }
            100% { transform: translateY(-15vh) scale(1.1); opacity: 0; }
        }

        .bubble-zone {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 10;
            pointer-events: none;
        }

        .living-bubble {
            position: absolute;
            bottom: -60px;
            background: rgba(14, 165, 233, 0.15);
            border: 2px solid rgba(56, 189, 248, 0.4);
            border-radius: 50%;
            pointer-events: auto;
            cursor: pointer;
            box-shadow: inset 0 0 10px rgba(255,255,255,0.6);
            transition: all 0.3s ease;
        }

        .living-bubble:hover {
            transform: scale(1.3) !important;
            background: rgba(56, 189, 248, 0.8) !important;
            border-color: #0284c7;
        }

        /* Custom Checkbox Style */
        .custom-cb:checked + span {
            text-decoration: line-through;
            color: #94a3b8;
        }

        /* Layout Print untuk PDF Checklist */
        @media print {
            body * { visibility: hidden; }
            #pdf-print-zone, #pdf-print-zone * { visibility: visible; }
            #pdf-print-zone { position: absolute; left: 0; top: 0; width: 100%; }
        }
    </style>
</head>
<body class="text-slate-700 pb-12">

    <div class="kpop-overlay"></div>
    <div class="grass-footer"></div>
    <div class="bubble-zone" id="bubble-container"></div>

    <!-- Main Container -->
    <div class="container mx-auto px-4 py-6 relative z-20 max-w-7xl">
        
        <!-- Header Profil Nida -->
        <div class="glass-panel rounded-3xl p-6 mb-6 flex flex-col md:flex-row items-center justify-between border-b-4 border-sky-400">
            <div class="text-center md:text-left mb-4 md:mb-0">
                <span class="bg-sky-100 text-sky-700 px-3 py-1 rounded-full text-xs font-bold uppercase tracking-wider">
                    <i class="fa-solid fa-school mr-1"></i> SMP Al Irsyad Cilacap
                </span>
                <h1 class="text-3xl font-extrabold text-sky-800 mt-2 font-['Poppins']">
                    💙 Nida Auliya Sholehah
                </h1>
                <p class="text-xs text-sky-500 font-medium mt-0.5">Jadwal Kelas 3 SMP • Kurikulum Merdeka & Persiapan Ujian Akhir (6 Hari Kerja)</p>
            </div>
            
            <!-- Aksi Cetak & Progres Global -->
            <div class="flex flex-wrap gap-3 justify-center">
                <div class="bg-white/90 rounded-2xl px-4 py-2 text-center border border-sky-100">
                    <span class="text-[10px] text-slate-400 font-bold block">TOTAL PROGRES</span>
                    <span class="text-xl font-bold text-sky-600" id="global-progress">0%</span>
                </div>
                <button onclick="window.print()" class="bg-gradient-to-r from-sky-500 to-emerald-500 hover:from-sky-600 hover:to-emerald-600 text-white font-bold px-5 py-2.5 rounded-xl shadow-sm text-sm transition-all flex items-center gap-2">
                    <i class="fa-solid fa-file-pdf"></i> Cetak / Simpan PDF
                </button>
            </div>
        </div>

        <!-- Navigator 12 Bulan -->
        <div class="grid grid-cols-4 sm:grid-cols-6 lg:grid-cols-12 gap-1.5 mb-6" id="month-navigation"></div>

        <!-- Navigator 4 Minggu -->
        <div class="glass-panel rounded-2xl p-3 mb-6 flex justify-center gap-3 border border-sky-100" id="week-navigation"></div>

        <!-- Motivasi Card Mingguan -->
        <div class="bg-sky-50/80 border-l-4 border-sky-500 rounded-xl p-4 mb-6 text-sm italic text-sky-800 font-medium flex items-center gap-3">
            <span class="text-lg">💡</span>
            <span id="weekly-motivation-text">Memuat motivasi indah minggu ini...</span>
        </div>

        <!-- Main Workspace Grid -->
        <div class="grid grid-cols-1 xl:grid-cols-4 gap-6">
            
            <!-- Jadwal Jam Harian & Checklist (3 Kolom) -->
            <div class="xl:col-span-3 space-y-4" id="daily-schedule-workspace">
                <!-- Diisi Dinamis Oleh JS -->
            </div>

            <!-- Catatan Harian & Info Sekolah (1 Kolom) -->
            <div class="space-y-4">
                <!-- Info Rutinitas Tetap SMP Al Irsyad -->
                <div class="glass-panel rounded-2xl p-5 border border-emerald-100">
                    <h3 class="text-sm font-bold text-emerald-800 mb-3 flex items-center gap-2">
                        <i class="fa-solid fa-clock-rotate-left"></i> Rutinitas SMP Al Irsyad
                    </h3>
                    <div class="text-xs space-y-2 text-slate-600 bg-emerald-50/40 p-3 rounded-xl border border-emerald-100">
                        <p class="font-semibold text-slate-700"><i class="fa-solid fa-circle text-[6px] text-emerald-500 mr-1.5"></i> Senin - Jumat (07:00 - 16:00)</p>
                        <p class="pl-3 text-slate-500">KBM Formal, Pembiasaan Karakter, Shalat Berjamaah, & Kurikulum Merdeka.</p>
                        <p class="font-semibold text-slate-700"><i class="fa-solid fa-circle text-[6px] text-amber-500 mr-1.5"></i> Sabtu (Mandiri / Ujian Akhir)</p>
                        <p class="pl-3 text-slate-500">Fokus penuh latihan soal Asesmen Nasional & review mandiri di rumah.</p>
                    </div>
                </div>

                <!-- Lembar Catatan Harian Interaktif -->
                <div class="glass-panel rounded-2xl p-5 border border-sky-100">
                    <div class="flex justify-between items-center mb-2">
                        <h3 class="text-sm font-bold text-sky-800 flex items-center gap-1.5">
                            <i class="fa-solid fa-square-pen"></i> Jurnal & Catatan Nida
                        </h3>
                        <span class="text-[9px] bg-sky-100 text-sky-700 font-bold px-2 py-0.5 rounded-full">Auto-Save</span>
                    </div>
                    <textarea id="nida-daily-note" oninput="saveDailyNote()" class="w-full bg-white/90 border border-sky-100 rounded-xl p-3 text-xs focus:ring-2 focus:ring-sky-300 focus:outline-none resize-none placeholder-slate-400" rows="8" placeholder="Tulis tugas sekolah, target setoran tahfidz, materi sulit hari ini, atau judul lagu K-Pop kesukaanmu..."></textarea>
                </div>
            </div>

        </div>

        <!-- Footer Identitas -->
        <div class="text-center mt-12 mb-6">
            <p class="text-[10px] font-bold tracking-widest text-sky-600 uppercase">✨ Nida Auliya Sholehah Study Dashboard v2026 ✨</p>
            <p class="text-[9px] text-slate-400 mt-0.5">SMP Al Irsyad Cilacap - Bergerak Maju dengan Kurikulum Merdeka</p>
        </div>
    </div>

    <!-- PRINT/PDF ENGINE ZONE -->
    <div id="pdf-print-zone" class="hidden p-8 bg-white text-black">
        <div class="border-b-4 border-sky-600 pb-3 mb-4">
            <h1 class="text-xl font-bold">🌸 DAFTAR REKAP CHECKLIST HARIAN BELAJAR</h1>
            <p class="text-xs uppercase text-gray-500 font-semibold">Nida Auliya Sholehah • SMP Al Irsyad Cilacap</p>
            <p class="text-[10px] text-gray-400" id="print-meta-text">Bulan: - | Minggu: -</p>
        </div>
        <div id="print-tasks-list" class="space-y-4 text-xs"></div>
        <div class="mt-8 pt-4 border-t border-gray-200 grid grid-cols-2 gap-4 text-[10px]">
            <div>
                <p class="font-bold">Jurnal Hari Ini:</p>
                <div id="print-note-box" class="border border-gray-300 p-2 mt-1 rounded min-h-[80px] text-gray-600 italic"></div>
            </div>
            <div class="flex flex-col justify-end items-end text-center">
                <div class="w-40 border-t border-gray-400 pt-1 font-bold">Orang Tua / Wali</div>
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC WORKSPACE -->
    <script>
        // Array 12 Bulan Pembelajaran Kelas 3 SMP Kurikulum Merdeka
        const monthsData = [
            { id: 1, name: "Juli" }, { id: 2, name: "Agustus" }, { id: 3, name: "September" },
            { id: 4, name: "Oktober" }, { id: 5, name: "November" }, { id: 6, name: "Desember" },
            { id: 7, name: "Januari" }, { id: 8, name: "Februari" }, { id: 9, name: "Maret" },
            { id: 10, name: "April" }, { id: 11, name: "Mei" }, { id: 12, name: "Juni" }
        ];

        // 4 Motivasi Berbeda untuk Setiap Minggu (Berulang Otomatis Tiap Bulan)
        const weeklyMotivations = [
            "Minggu 1: 'Awal baru adalah kesempatan emas. Mulai langkah belajarmu di SMP Al Irsyad dengan senyuman dan niat ikhlas!' 🌟",
            "Minggu 2: 'Disiplin adalah jembatan antara cita-cita dan pencapaian nyata. Setiap menit belajarmu sangatlah berharga, Nida!' 💎",
            "Minggu 3: 'Jangan takut menghadapi materi sulit. Layaknya lagu K-Pop favoritmu, nikmati ritmenya dan kamu akan menguasainya!' 🎶",
            "Minggu 4: 'Evaluasi minggu ini dengan bijak. Istirahat yang cukup, bersiap menyambut tantangan berikutnya dengan energi penuh!' 🚀"
        ];

        // Pembagian Jam Kerja Harian Kurikulum Merdeka (Senin - Sabtu)
        const baseSchedule = [
            { day: "Senin", subject: "Matematika & Bhs Indonesia", amTask: "🏫 07:00-16:00 KBM SMP Al Irsyad (Fokus: Eksponen & Struktur LHO)", pmTask: "✏️ 19:30-21:00 Review mandiri & latihan soal literasi membaca" },
            { day: "Selasa", subject: "IPA (Sains Terpadu)", amTask: "🏫 07:00-16:00 KBM SMP Al Irsyad (Fokus: Sistem Reproduksi & Genetika)", pmTask: "✏️ 19:30-21:00 Membuat peta pikiran/mind mapping sistem organ" },
            { day: "Rabu", subject: "IPS & Bahasa Inggris", amTask: "🏫 07:00-16:00 KBM SMP Al Irsyad (Fokus: Interaksi Ruang & Report Text)", pmTask: "✏️ 19:30-21:00 Menghafal 10 vocabulary baru untuk persiapan ujian" },
            { day: "Kamis", subject: "Pendidikan Pancasila & Informatika", amTask: "🏫 07:00-16:00 KBM SMP Al Irsyad (Fokus: UUD 1945 & Berpikir Komputasional)", pmTask: "✏️ 19:30-21:00 Latihan soal studi kasus penalaran Pancasila" },
            { day: "Jumat", subject: "Agama Islam & PJOK/Seni", amTask: "🏫 07:00-16:00 KBM SMP Al Irsyad (Fokus: Akhlak Mulia, Tahfidz & Kebugaran)", pmTask: "✏️ 19:30-21:00 Mengerjakan rangkuman materi agama & relaksasi santai" },
            { day: "Sabtu", subject: "Simulasi Ujian Akhir (Mandiri)", amTask: "📝 08:00-12:00 Pengerjaan try out mandiri / paket soal Asesmen Nasional", pmTask: "✨ 14:00-16:00 Evaluasi jawaban salah & persiapan target minggu depan" }
        ];

        let currentMonth = 1;
        let currentWeek = 1;

        // Konten Motivasi Gelembung K-Pop
        const bubbleQuotes = [
            "Hwaiting Nida! 💙", "SMP Al Irsyad Hebat! ✨", "Cilacap Berprestasi! 🌊",
            "Fokus Ujian Akhir! 📚", "Kurikulum Merdeka Seru 🌿", "Jangan lupa istirahat 🥰",
            "SMA Impian Menantimu 🏫", "You can do it! 🐰"
        ];

        function initApp() {
            renderMonthNav();
            renderWeekNav();
            renderWorkspace();
            loadDailyNote();
            generateBubbles();
            updateGlobalProgress();
        }

        // Render Navigasi 12 Bulan
        function renderMonthNav() {
            const container = document.getElementById('month-navigation');
            container.innerHTML = '';
            monthsData.forEach(m => {
                const btn = document.createElement('button');
                btn.className = `py-2 text-xs font-bold rounded-xl border transition-all ${
                    m.id === currentMonth 
                    ? 'bg-sky-500 text-white border-sky-500 shadow-sm scale-105' 
                    : 'bg-white/80 text-sky-600 border-sky-100 hover:bg-sky-50'
                }`;
                btn.innerText = m.name;
                btn.onclick = () => { currentMonth = m.id; updateSelection(); };
                container.appendChild(btn);
            });
        }

        // Render Navigasi 4 Minggu
        function renderWeekNav() {
            const container = document.getElementById('week-navigation');
            container.innerHTML = '';
            for(let w=1; w<=4; w++) {
                const btn = document.createElement('button');
                btn.className = `px-5 py-1.5 text-xs font-bold rounded-lg border transition-all ${
                    w === currentWeek 
                    ? 'bg-emerald-500 text-white border-emerald-500 shadow-sm' 
                    : 'bg-white/90 text-emerald-600 border-emerald-100 hover:bg-emerald-50'
                }`;
                btn.innerText = `Minggu ${w}`;
                btn.onclick = () => { currentWeek = w; updateSelection(); };
                container.appendChild(btn);
            }
        }

        function updateSelection() {
            renderMonthNav();
            renderWeekNav();
            renderWorkspace();
            loadDailyNote();
            updateGlobalProgress();
        }

        // Render Lembar Kerja Jadwal & Checklist Harian
        function renderWorkspace() {
            // Update Teks Motivasi Mingguan
            document.getElementById('weekly-motivation-text').innerText = weeklyMotivations[currentWeek - 1];

            const container = document.getElementById('daily-schedule-workspace');
            container.innerHTML = '';

            baseSchedule.forEach((sched, index) => {
                const dayKey = `nida_m${currentMonth}_w${currentWeek}_d${index}`;
                const amChecked = localStorage.getItem(`${dayKey}_am`) === 'true';
                const pmChecked = localStorage.getItem(`${dayKey}_pm`) === 'true';

                const card = document.createElement('div');
                card.className = "glass-panel rounded-2xl p-4 border border-sky-100 grid grid-cols-1 md:grid-cols-4 gap-4 items-center";
                card.innerHTML = `
                    <!-- Hari & Mata Pelajaran -->
                    <div class="md:col-span-1 border-b md:border-b-0 md:border-r border-sky-100 pb-2 md:pb-0">
                        <span class="text-[10px] uppercase font-bold text-emerald-600 tracking-wider bg-emerald-50 px-2 py-0.5 rounded-md">${sched.day}</span>
                        <h4 class="text-sm font-bold text-slate-800 mt-1">${sched.subject}</h4>
                    </div>
                    
                    <!-- Slot Waktu 1 (Sekolah/Pagi) -->
                    <div class="md:col-span-1.5 flex items-start gap-3">
                        <input type="checkbox" id="${dayKey}_am" onchange="toggleCheck('${dayKey}_am')" class="custom-cb mt-1 w-4 h-4 text-sky-600 border-sky-300 rounded focus:ring-sky-400 accent-sky-500 cursor-pointer" ${amChecked ? 'checked' : ''}>
                        <span class="text-xs text-slate-600 leading-tight">${sched.amTask}</span>
                    </div>

                    <!-- Slot Waktu 2 (Belajar Mandiri/Malam) -->
                    <div class="md:col-span-1.5 flex items-start gap-3">
                        <input type="checkbox" id="${dayKey}_pm" onchange="toggleCheck('${dayKey}_pm')" class="custom-cb mt-1 w-4 h-4 text-sky-600 border-sky-300 rounded focus:ring-sky-400 accent-sky-500 cursor-pointer" ${pmChecked ? 'checked' : ''}>
                        <span class="text-xs text-slate-600 leading-tight">${sched.pmTask}</span>
                    </div>
                `;
                container.appendChild(card);
            });

            syncPrintData();
        }

        function toggleCheck(key) {
            const cb = document.getElementById(key);
            localStorage.setItem(key, cb.checked);
            updateGlobalProgress();
            syncPrintData();
        }

        // Hitung Progres Global Keseluruhan
        function updateGlobalProgress() {
            let total = 0;
            let checked = 0;

            for(let m=1; m<=12; m++) {
                for(let w=1; w<=4; w++) {
                    for(let d=0; d<6; d++) {
                        total += 2;
                        if(localStorage.getItem(`nida_m${m}_w${w}_d${d}_am`) === 'true') checked++;
                        if(localStorage.getItem(`nida_m${m}_w${w}_d${d}_pm`) === 'true') checked++;
                    }
                }
            }

            const percentage = total > 0 ? Math.round((checked / total) * 100) : 0;
            document.getElementById('global-progress').innerText = `${percentage}%`;
        }

        // Catatan Harian (Tersimpan otomatis per kombinasi Bulan + Minggu)
        function saveDailyNote() {
            const text = document.getElementById('nida-daily-note').value;
            localStorage.setItem(`nida_note_m${currentMonth}_w${currentWeek}`, text);
            syncPrintData();
        }

        function loadDailyNote() {
            const text = localStorage.getItem(`nida_note_m${currentMonth}_w${currentWeek}`) || '';
            document.getElementById('nida-daily-note').value = text;
        }

        // Sinkronisasi data ke struktur layout print PDF
        function syncPrintData() {
            const selectedMonthName = monthsData.find(m => m.id === currentMonth).name;
            document.getElementById('print-meta-text').innerText = `Bulan: ${selectedMonthName} | Minggu ke-${currentWeek}`;
            document.getElementById('print-note-box').innerText = document.getElementById('nida-daily-note').value || "Tidak ada catatan.";

            const printList = document.getElementById('print-tasks-list');
            printList.innerHTML = '';

            baseSchedule.forEach((sched, index) => {
                const dayKey = `nida_m${currentMonth}_w${currentWeek}_d${index}`;
                const amCheck = localStorage.getItem(`${dayKey}_am`) === 'true' ? '[✔]' : '[ ]';
                const pmCheck = localStorage.getItem(`${dayKey}_pm`) === 'true' ? '[✔]' : '[ ]';

                const row = document.createElement('div');
                row.className = "border-b border-gray-200 pb-2";
                row.innerHTML = `
                    <p class="font-bold text-gray-800">${sched.day} - ${sched.subject}</p>
                    <p class="pl-2">${amCheck} ${sched.amTask}</p>
                    <p class="pl-2">${pmCheck} ${sched.pmTask}</p>
                `;
                printList.appendChild(row);
            });
        }

        // Generasi Gelembung Hidup / Living Bubbles Sejuk
        function generateBubbles() {
            const container = document.getElementById('bubble-container');
            const totalBubbles = 8;
            for(let i=0; i<totalBubbles; i++) {
                const bubble = document.createElement('div');
                bubble.className = "living-bubble";
                
                const size = Math.floor(Math.random() * 30) + 50; // 50px - 80px
                bubble.style.width = `${size}px`;
                bubble.style.height = `${size}px`;
                bubble.style.left = `${Math.floor(Math.random() * 90)}%`;
                
                const duration = Math.random() * 8 + 12; // 12s - 20s
                const delay = Math.random() * 5;
                bubble.style.animation = `floatBubble ${duration}s linear ${delay}s infinite`;

                bubble.onclick = (e) => {
                    e.stopPropagation();
                    const quote = bubbleQuotes[Math.floor(Math.random() * bubbleQuotes.length)];
                    
                    // Letupan teks mengambang manis
                    const tooltip = document.createElement('div');
                    tooltip.className = "fixed bg-sky-600 text-white font-bold text-xs px-4 py-2 rounded-xl shadow-md z-50 transform -translate-x-1/2 -translate-y-1/2 transition-opacity duration-500 animate-bounce";
                    tooltip.style.left = `${e.clientX}px`;
                    tooltip.style.top = `${e.clientY}px`;
                    tooltip.innerText = quote;
                    
                    document.body.appendChild(tooltip);
                    
                    // Efek kempis sejenak saat diklik
                    bubble.style.transform = "scale(0.3)";
                    setTimeout(() => {
                        bubble.style.transform = "scale(1)";
                        tooltip.style.opacity = '0';
                        setTimeout(() => tooltip.remove(), 500);
                    }, 2500);
                };

                container.appendChild(bubble);
            }
        }

        window.onload = initApp;
    </script>
</body>
</html>
