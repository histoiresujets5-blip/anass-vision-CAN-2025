<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anass Vision | CAN 2025 - رؤيـــة أنس | كأس افريقيا 2025</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;800&family=Tajawal:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            /* Couleurs tirées de l'image officielle */
            --can-bg: #5a0c16;      /* Rouge très foncé du fond */
            --can-red: #8a1523;     /* Rouge des cartes */
            --can-green: #00974e;   /* Vert vif des motifs */
            --can-gold: #e2b13c;    /* Or des logos */
            --can-text: #ffffff;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: var(--can-bg);
            color: var(--can-text);
            /* Motifs verts dans les coins inspirés de l'affiche */
            background-image: 
                radial-gradient(circle at 0% 0%, var(--can-green) 0%, transparent 25%),
                radial-gradient(circle at 100% 100%, var(--can-green) 0%, transparent 25%),
                radial-gradient(circle at 50% 50%, rgba(138, 21, 35, 0.3) 0%, transparent 60%);
            background-attachment: fixed;
        }

        .font-arabic {
            font-family: 'Tajawal', sans-serif;
        }

        /* Boutons et éléments interactifs */
        .btn-primary {
            background: linear-gradient(135deg, var(--can-green) 0%, #006a35 100%);
            color: white;
            border: 1px solid rgba(255,255,255,0.2);
            transition: all 0.2s;
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 0 15px rgba(0, 151, 78, 0.5);
        }

        /* Cartes des équipes style "Affiche Officielle" */
        .group-header {
            background-image: linear-gradient(to right, transparent, #6d111c, transparent);
            border: 1px solid var(--can-gold);
            border-radius: 9999px; /* Pill shape */
            color: white;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            text-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }

        .team-card {
            background: linear-gradient(to right, #9c1c2b, #8a1523);
            border: 1px solid rgba(226, 177, 60, 0.3); /* Gold border subtile */
            color: white;
            transition: all 0.2s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }
        .team-card:hover {
            border-color: var(--can-gold);
            transform: translateX(5px);
            background: linear-gradient(to right, #b02030, #9c1c2b);
        }
        .team-card.selected {
            background: linear-gradient(to right, var(--can-green), #006a35);
            border-color: var(--can-gold);
            box-shadow: 0 0 10px rgba(0, 151, 78, 0.5);
        }

        /* Bracket Connectors */
        .bracket-connector::after {
            background-color: var(--can-gold);
            opacity: 0.5;
        }

        /* Chat Styles */
        .chat-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .chat-window {
            background: rgba(90, 12, 22, 0.95);
            backdrop-filter: blur(10px);
            border: 1px solid var(--can-gold);
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            height: 0;
            width: 320px;
            overflow: hidden;
            transition: height 0.3s ease;
            border-radius: 12px;
        }
        .chat-window.open {
            height: 400px;
        }
        .chat-messages::-webkit-scrollbar {
            width: 6px;
        }
        .chat-messages::-webkit-scrollbar-thumb {
            background-color: var(--can-gold);
            border-radius: 3px;
        }
        
        .flag-icon {
            width: 32px;
            height: 24px;
            object-fit: cover;
            border: 1px solid rgba(255,255,255,0.2);
            box-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }

        /* Responsive Iframe for video */
        .responsive-iframe-container {
            position: relative;
            width: 100%;
            padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
            height: 0;
            overflow: hidden;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.4);
        }
        .responsive-iframe-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        [dir="rtl"] .arrow-right { transform: rotate(180deg); }
        [dir="rtl"] .chat-container { right: auto; left: 20px; }
    </style>
</head>
<body class="min-h-screen flex flex-col overflow-x-hidden">

    <!-- Navbar -->
    <nav class="sticky top-0 z-50 border-b border-[color:var(--can-gold)] bg-[#5a0c16]/95 backdrop-blur-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16 items-center">
                <div class="flex items-center gap-3">
                    <img src="https://upload.wikimedia.org/wikipedia/fr/6/66/Coupe_d_Afrique_des_Nations_2025_Logo.png" alt="Logo" class="h-10 w-auto bg-white/10 rounded-full p-1 border border-[color:var(--can-gold)]" onerror="this.src='https://placehold.co/40x40/transparent/white?text=CAF'">
                    <div class="flex flex-col justify-center">
                        <div class="flex items-center gap-2 leading-none">
                            <span class="font-extrabold text-lg tracking-tight text-white drop-shadow-md uppercase whitespace-nowrap">
                                Anass Vision
                            </span>
                            <span class="text-[color:var(--can-gold)] font-bold text-sm font-arabic whitespace-nowrap border-l border-white/20 pl-2 ml-2">رؤيـــة أنس</span>
                        </div>
                        <span class="text-[10px] font-bold text-white/60 tracking-[0.2em] uppercase mt-0.5">
                            CAN <span class="text-[color:var(--can-gold)]">2025</span> Morocco
                        </span>
                    </div>
                </div>
                <div class="flex space-x-2 bg-black/20 p-1 rounded-lg">
                    <button onclick="setLang('fr')" class="px-3 py-1 text-sm rounded font-bold transition-all lang-btn" data-lang="fr">FR</button>
                    <button onclick="setLang('en')" class="px-3 py-1 text-sm rounded font-bold transition-all lang-btn" data-lang="en">EN</button>
                    <button onclick="setLang('ar')" class="px-3 py-1 text-sm rounded font-bold transition-all lang-btn font-arabic" data-lang="ar">عربي</button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="flex-grow container mx-auto px-4 py-8 max-w-7xl relative z-10">
        <!-- Video Mascot Section -->
        <div class="mb-12 bg-[#3d080f]/50 p-6 rounded-xl border-2 border-[color:var(--can-gold)]/50 shadow-2xl shadow-black/50">
            <h2 class="text-3xl font-extrabold mb-4 text-center text-[color:var(--can-gold)]" id="video-title"></h2>
            <div class="max-w-3xl mx-auto">
                <div class="responsive-iframe-container">
                    <!-- YouTube Embed (Video ID: Ci5tyJvx194) -->
                    <iframe 
                        id="mascot-video"
                        src="https://www.youtube.com/embed/Ci5tyJvx194?autoplay=0&controls=1&rel=0" 
                        title="Meet Assad, the official mascot welcoming you to Morocco." 
                        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
                        allowfullscreen>
                    </iframe>
                </div>
                <p class="text-center text-sm mt-3 text-white/70" id="video-description"></p>
            </div>
        </div>

        <!-- Dynamic Content -->
        <div id="app"></div>
    </main>

    <!-- Chat Widget -->
    <div class="chat-container">
        <!-- Chat Window -->
        <div id="chatWindow" class="chat-window flex flex-col mb-4">
            <div class="bg-[#3d080f] p-3 border-b border-[color:var(--can-gold)] flex justify-between items-center">
                <span class="font-bold text-[color:var(--can-gold)] flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-green-500 animate-pulse"></span>
                    <span id="chatTitle">Fan Zone Live</span>
                </span>
                <button onclick="toggleChat()" class="text-white/70 hover:text-white">✕</button>
            </div>
            
            <div id="chatMessages" class="chat-messages flex-1 overflow-y-auto p-3 space-y-3 bg-black/20">
                <!-- Messages injected here -->
            </div>
            
            <div class="p-3 bg-[#3d080f] border-t border-[color:var(--can-gold)]">
                <div class="flex gap-2">
                    <input type="text" id="chatInput" class="flex-1 bg-black/30 border border-[color:var(--can-red)] rounded px-3 py-2 text-sm text-white focus:outline-none focus:border-[color:var(--can-gold)]" placeholder="...">
                    <button onclick="sendMessage()" class="bg-[color:var(--can-gold)] text-[#5a0c16] font-bold px-3 py-2 rounded hover:bg-yellow-400 transition-colors">➤</button>
                </div>
            </div>
        </div>

        <!-- FAB Button -->
        <button onclick="toggleChat()" class="float-right bg-[color:var(--can-gold)] text-[#5a0c16] w-14 h-14 rounded-full shadow-lg flex items-center justify-center font-bold text-2xl hover:scale-110 transition-transform border-4 border-[#5a0c16]">
            💬
        </button>
    </div>

    <!-- Footer -->
    <footer class="bg-[#3d080f] text-white/50 py-6 mt-8 border-t border-[color:var(--can-red)] relative z-10">
        <div class="container mx-auto px-4 text-center">
            <p class="text-xs" id="footer-text">© 2025 CAN Simulator. Concept non officiel.</p>
        </div>
    </footer>

    <!-- Templates & Logic -->
    <script>
        // --- DATA ---
        const TEAMS = {
            "MA": { name: "Maroc", code: "MA", flag: "ma" },
            "ML": { name: "Mali", code: "ML", flag: "ml" },
            "ZM": { name: "Zambie", code: "ZM", flag: "zm" },
            "KM": { name: "Comores", code: "KM", flag: "km" },
            "EG": { name: "Égypte", code: "EG", flag: "eg" },
            "ZA": { name: "Afrique du Sud", code: "ZA", flag: "za" },
            "AO": { name: "Angola", code: "AO", flag: "ao" },
            "ZW": { name: "Zimbabwe", code: "ZW", flag: "zw" },
            "NG": { name: "Nigeria", code: "NG", flag: "ng" },
            "TN": { name: "Tunisie", code: "TN", flag: "tn" },
            "UG": { name: "Ouganda", code: "UG", flag: "ug" },
            "TZ": { name: "Tanzanie", code: "TZ", flag: "tz" },
            "SN": { name: "Sénégal", code: "SN", flag: "sn" },
            "CD": { name: "RD Congo", code: "CD", flag: "cd" },
            "BJ": { name: "Bénin", code: "BJ", flag: "bj" },
            "BW": { name: "Botswana", code: "BW", flag: "bw" },
            "DZ": { name: "Algérie", code: "DZ", flag: "dz" },
            "BF": { name: "Burkina Faso", code: "BF", flag: "bf" },
            "GQ": { name: "Guinée Équatoriale", code: "GQ", flag: "gq" },
            "SD": { name: "Soudan", code: "SD", flag: "sd" },
            "CI": { name: "Côte d’Ivoire", code: "CI", flag: "ci" },
            "CM": { name: "Cameroun", code: "CM", flag: "cm" },
            "GA": { name: "Gabon", code: "GA", flag: "ga" },
            "MZ": { name: "Mozambique", code: "MZ", flag: "mz" }
        };

        const INITIAL_GROUPS = {
            "A": ["MA", "ML", "ZM", "KM"],
            "B": ["EG", "ZA", "AO", "ZW"],
            "C": ["NG", "TN", "UG", "TZ"],
            "D": ["SN", "CD", "BJ", "BW"],
            "E": ["DZ", "BF", "GQ", "SD"],
            "F": ["CI", "CM", "GA", "MZ"]
        };
        
        const MASCOT_VIDEO = {
            id: 'Ci5tyJvx194',
            title: {
                fr: "Découvrez Assad, la Mascotte Officielle de la CAN 2025 au Maroc",
                en: "Meet Assad, the Official Mascot of AFCON 2025 in Morocco",
                ar: "تعرف على أسد، التميمة الرسمية لكأس الأمم الأفريقية 2025 بالمغرب"
            },
            desc: {
                fr: "Assad, le lion de l'Atlas, vous accueille au Maroc pour la Coupe d'Afrique des Nations 2025. Un symbole de force et d'hospitalité.",
                en: "Assad, the Atlas Lion, welcomes you to Morocco for the Africa Cup of Nations 2025. A symbol of strength and hospitality.",
                ar: "أسد، أسد الأطلس، يرحب بكم في المغرب لبطولة كأس الأمم الأفريقية 2025. رمز للقوة والكرم."
            }
        };

        const TRANSLATIONS = {
            fr: {
                title: "Anass Vision | CAN 2025",
                step1: "Phase de Groupes",
                step1Desc: "Classez les équipes dans chaque groupe (1er à 4ème).",
                step2: "Meilleurs 3èmes",
                step2Desc: "Sélectionnez les 4 meilleures équipes classées 3ème.",
                step3: "Tableau Final",
                step3Desc: "Cliquez sur le gagnant de chaque match.",
                group: "Groupe",
                nextBtn: "Étape Suivante",
                prevBtn: "Retour",
                generateBtn: "Générer le Tableau",
                winner: "Champion",
                r16: "Huitièmes",
                qf: "Quarts",
                sf: "Demi-finales",
                fin: "Finale",
                select4: "Sélectionnez 4 équipes.",
                reset: "Réinitialiser",
                chatTitle: "Chat des Supporters",
                chatPlaceholder: "Votre message...",
                you: "Vous"
            },
            en: {
                title: "Anass Vision | AFCON 2025",
                step1: "Group Stage",
                step1Desc: "Rank the teams in each group (1st to 4th).",
                step2: "Best 3rd Place",
                step2Desc: "Select the 4 best 3rd-placed teams.",
                step3: "Knockout Stage",
                step3Desc: "Click on the winner of each match.",
                group: "Group",
                nextBtn: "Next Step",
                prevBtn: "Back",
                generateBtn: "Generate Bracket",
                winner: "Champion",
                r16: "Round of 16",
                qf: "Quarter-Finals",
                sf: "Semi-Finals",
                fin: "Final",
                select4: "Select 4 teams.",
                reset: "Reset",
                chatTitle: "Fan Zone Chat",
                chatPlaceholder: "Type a message...",
                you: "You"
            },
            ar: {
                title: "رؤيـــة أنس | كأس افريقيا 2025",
                step1: "دور المجموعات",
                step1Desc: "رتب الفرق في كل مجموعة (من 1 إلى 4).",
                step2: "أفضل الثوالث",
                step2Desc: "اختر أفضل 4 فرق احتلت المركز الثالث.",
                step3: "الأدوار الإقصائية",
                step3Desc: "اضغط على الفائز في كل مباراة للتقدم.",
                group: "المجموعة",
                nextBtn: "الخطوة التالية",
                prevBtn: "عودة",
                generateBtn: "إنشاء الجدول",
                winner: "البطل",
                r16: "دور الـ 16",
                qf: "ربع النهائي",
                sf: "نصف النهائي",
                fin: "النهائي",
                select4: "اختر 4 فرق.",
                reset: "إعادة تعيين",
                chatTitle: "دردشة الجماهير",
                chatPlaceholder: "أكتب رسالة...",
                you: "أنت"
            }
        };

        // --- STATE ---
        let state = {
            lang: 'fr',
            step: 1,
            groups: JSON.parse(JSON.stringify(INITIAL_GROUPS)),
            thirds: [],
            bracket: {},
            chatOpen: false,
            username: "Fan_" + Math.floor(Math.random() * 1000)
        };

        // --- UTILS ---
        const getFlagUrl = (isoCode) => `https://flagcdn.com/w40/${isoCode.toLowerCase()}.png`;

        function setLang(lang) {
            state.lang = lang;
            document.documentElement.lang = lang;
            document.body.dir = lang === 'ar' ? 'rtl' : 'ltr';
            
            document.querySelectorAll('.lang-btn').forEach(btn => {
                if(btn.dataset.lang === lang) {
                    btn.classList.add('bg-[color:var(--can-gold)]', 'text-[#5a0c16]');
                    btn.classList.remove('text-white');
                } else {
                    btn.classList.remove('bg-[color:var(--can-gold)]', 'text-[#5a0c16]');
                    btn.classList.add('text-white');
                }
            });

            if(lang === 'ar') document.body.classList.add('font-arabic');
            else document.body.classList.remove('font-arabic');

            // Update Video Texts
            document.getElementById('video-title').innerText = MASCOT_VIDEO.title[lang];
            document.getElementById('video-description').innerText = MASCOT_VIDEO.desc[lang];


            // Update Chat UI texts
            const t = TRANSLATIONS[lang];
            document.getElementById('chatTitle').innerText = t.chatTitle;
            document.getElementById('chatInput').placeholder = t.chatPlaceholder;

            render();
        }

        // --- CHAT LOGIC ---
        
        // Mock existing messages
        const initialMessages = [
            { user: "Ahmed_MA", text: "Dima Maghrib! 🇲🇦", time: "10:00" },
            { user: "Sarah_SN", text: "Teranga Lions for the win! 🦁", time: "10:02" },
            { user: "Mo_EG", text: "Seven stars ⭐️🇪🇬", time: "10:05" }
        ];

        function loadChat() {
            const saved = localStorage.getItem('can2025_chat');
            const messages = saved ? JSON.parse(saved) : initialMessages;
            const container = document.getElementById('chatMessages');
            container.innerHTML = '';
            
            messages.forEach(msg => {
                appendMessage(msg.user, msg.text, msg.time);
            });
            container.scrollTop = container.scrollHeight;
        }

        function appendMessage(user, text, time) {
            const container = document.getElementById('chatMessages');
            const isMe = user === state.username;
            const div = document.createElement('div');
            div.className = `flex flex-col ${isMe ? 'items-end' : 'items-start'}`;
            div.innerHTML = `
                <div class="text-[10px] text-white/50 mb-0.5">${user}</div>
                <div class="${isMe ? 'bg-[color:var(--can-green)]' : 'bg-[#5a0c16]'} border border-white/10 text-white px-3 py-2 rounded-lg text-sm max-w-[85%] shadow-sm">
                    ${text}
                </div>
            `;
            container.appendChild(div);
            container.scrollTop = container.scrollHeight;
        }

        function sendMessage() {
            const input = document.getElementById('chatInput');
            const text = input.value.trim();
            if(!text) return;

            const now = new Date();
            const time = now.getHours() + ":" + String(now.getMinutes()).padStart(2, '0');
            const user = state.username;

            // Save to localStorage
            const saved = localStorage.getItem('can2025_chat');
            let messages = saved ? JSON.parse(saved) : initialMessages;
            messages.push({ user, text, time });
            // Keep only last 50
            if(messages.length > 50) messages = messages.slice(-50);
            localStorage.setItem('can2025_chat', JSON.stringify(messages));

            appendMessage(user, text, time);
            input.value = '';
        }

        function toggleChat() {
            state.chatOpen = !state.chatOpen;
            const win = document.getElementById('chatWindow');
            if(state.chatOpen) {
                win.classList.add('open');
                loadChat();
            } else {
                win.classList.remove('open');
            }
        }

        // Add Enter key listener for chat
        document.getElementById('chatInput').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') sendMessage();
        });


        // --- GAME LOGIC ---

        function moveTeam(groupLetter, index, direction) {
            const group = state.groups[groupLetter];
            if (direction === 'up' && index > 0) {
                [group[index], group[index - 1]] = [group[index - 1], group[index]];
            } else if (direction === 'down' && index < group.length - 1) {
                [group[index], group[index + 1]] = [group[index + 1], group[index]];
            }
            render();
        }

        function toggleThird(groupLetter) {
            if (state.thirds.includes(groupLetter)) {
                state.thirds = state.thirds.filter(g => g !== groupLetter);
            } else {
                if (state.thirds.length < 4) {
                    state.thirds.push(groupLetter);
                }
            }
            render();
        }

        function getThirdsPairings(thirdsArray) {
            const sorted = thirdsArray.sort().join("");
            const table = {
                "ABCD": { "1A": "3C", "1B": "3D", "1C": "3A", "1D": "3B" },
                "ABCE": { "1A": "3C", "1B": "3A", "1C": "3B", "1D": "3E" },
                "ABCF": { "1A": "3C", "1B": "3A", "1C": "3B", "1D": "3F" },
                "ABDE": { "1A": "3D", "1B": "3A", "1C": "3B", "1D": "3E" },
                "ABDF": { "1A": "3D", "1B": "3A", "1C": "3B", "1D": "3F" },
                "ABEF": { "1A": "3E", "1B": "3A", "1C": "3B", "1D": "3F" },
                "ACDE": { "1A": "3C", "1B": "3D", "1C": "3A", "1D": "3E" },
                "ACDF": { "1A": "3C", "1B": "3D", "1C": "3A", "1D": "3F" },
                "ACEF": { "1A": "3C", "1B": "3A", "1C": "3F", "1D": "3E" },
                "ADEF": { "1A": "3D", "1B": "3A", "1C": "3F", "1D": "3E" },
                "BCDE": { "1A": "3C", "1B": "3D", "1C": "3B", "1D": "3E" },
                "BCDF": { "1A": "3C", "1B": "3D", "1C": "3B", "1D": "3F" },
                "BCEF": { "1A": "3E", "1B": "3C", "1C": "3B", "1D": "3F" },
                "BDEF": { "1A": "3E", "1B": "3D", "1C": "3B", "1D": "3F" },
                "CDEF": { "1A": "3C", "1B": "3D", "1C": "3F", "1D": "3E" }
            };
            return table[sorted] || { "1A": "3C", "1B": "3D", "1C": "3A", "1D": "3B" }; 
        }

        function generateBracket() {
            if (state.thirds.length !== 4) return;
            const pairings = getThirdsPairings(state.thirds);
            
            const t = (grp, pos) => {
                const teamCode = state.groups[grp][pos-1];
                return TEAMS[teamCode];
            };
            const t3 = (grp) => t(grp, 3);

            const op1A = t3(pairings["1A"].charAt(1));
            const op1B = t3(pairings["1B"].charAt(1));
            const op1C = t3(pairings["1C"].charAt(1));
            const op1D = t3(pairings["1D"].charAt(1));

            state.bracket = {
                r16: [
                    { id: 1, p1: t('A', 2), p2: t('C', 2), winner: null },
                    { id: 2, p1: t('D', 1), p2: op1D, winner: null },
                    { id: 3, p1: t('B', 1), p2: op1B, winner: null },
                    { id: 4, p1: t('F', 1), p2: t('E', 2), winner: null },
                    { id: 5, p1: t('E', 1), p2: t('D', 2), winner: null },
                    { id: 6, p1: t('C', 1), p2: op1C, winner: null },
                    { id: 7, p1: t('A', 1), p2: op1A, winner: null },
                    { id: 8, p1: t('B', 2), p2: t('F', 2), winner: null }
                ],
                qf: Array(4).fill({ p1: null, p2: null, winner: null }),
                sf: Array(2).fill({ p1: null, p2: null, winner: null }),
                final: [{ p1: null, p2: null, winner: null }]
            };
            state.step = 3;
            render();
        }

        function advanceTeam(round, matchIndex, team) {
            if (!team) return;
            
            state.bracket[round][matchIndex] = { ...state.bracket[round][matchIndex], winner: team };

            let nextRound = '', nextMatchIndex = 0, slot = '';

            if (round === 'r16') {
                nextRound = 'qf'; nextMatchIndex = Math.floor(matchIndex / 2); slot = (matchIndex % 2 === 0) ? 'p1' : 'p2';
            } else if (round === 'qf') {
                nextRound = 'sf'; nextMatchIndex = Math.floor(matchIndex / 2); slot = (matchIndex % 2 === 0) ? 'p1' : 'p2';
            } else if (round === 'sf') {
                nextRound = 'final'; nextMatchIndex = 0; slot = (matchIndex === 0) ? 'p1' : 'p2';
            } else if (round === 'final') {
                triggerConfetti(); render(); return;
            }

            const nextMatch = state.bracket[nextRound][nextMatchIndex];
            state.bracket[nextRound][nextMatchIndex] = { ...nextMatch, [slot]: team, winner: null };
            render();
        }

        function triggerConfetti() {
            for(let i=0; i<50; i++) {
                const conf = document.createElement('div');
                conf.className = 'fixed w-3 h-3 z-[2000]';
                conf.style.left = Math.random() * 100 + 'vw';
                conf.style.top = '-10px';
                conf.style.backgroundColor = ['#e2b13c', '#00974e', '#ffffff'][Math.floor(Math.random()*3)];
                conf.style.animation = `fall ${Math.random() * 2 + 2}s linear forwards`;
                document.body.appendChild(conf);
                setTimeout(() => conf.remove(), 4000);
            }
        }
        
        // --- STYLE HELPERS ---
        const style = document.createElement('style');
        style.innerHTML = `
            @keyframes fall { to { transform: translateY(100vh) rotate(720deg); } }
        `;
        document.head.appendChild(style);

        // --- RENDERERS ---

        function renderHeader(t) {
            const stepClass = (active) => active 
                ? 'bg-[color:var(--can-green)] text-white border-[color:var(--can-gold)] scale-110 shadow-lg shadow-green-900/50' 
                : 'bg-white/10 text-white/40 border-transparent';
            
            return `
                <div class="text-center mb-8 relative">
                    <div class="inline-flex items-center justify-center space-x-2 bg-black/30 backdrop-blur rounded-full px-6 py-3 border border-white/10">
                         <div class="flex items-center gap-2">
                            <span class="w-8 h-8 rounded-full flex items-center justify-center font-bold border transition-all duration-300 ${stepClass(state.step >= 1)}">1</span>
                            <span class="text-sm font-bold uppercase hidden md:inline ${state.step >= 1 ? 'text-[color:var(--can-gold)]' : 'text-white/30'}">${t.step1}</span>
                         </div>
                         <div class="w-8 h-px bg-white/20"></div>
                         <div class="flex items-center gap-2">
                            <span class="w-8 h-8 rounded-full flex items-center justify-center font-bold border transition-all duration-300 ${stepClass(state.step >= 2)}">2</span>
                            <span class="text-sm font-bold uppercase hidden md:inline ${state.step >= 2 ? 'text-[color:var(--can-gold)]' : 'text-white/30'}">${t.step2}</span>
                         </div>
                         <div class="w-8 h-px bg-white/20"></div>
                         <div class="flex items-center gap-2">
                            <span class="w-8 h-8 rounded-full flex items-center justify-center font-bold border transition-all duration-300 ${stepClass(state.step >= 3)}">3</span>
                            <span class="text-sm font-bold uppercase hidden md:inline ${state.step >= 3 ? 'text-[color:var(--can-gold)]' : 'text-white/30'}">${t.step3}</span>
                         </div>
                    </div>
                </div>
            `;
        }

        function renderGroups(t) {
            let html = `<div class="text-center mb-6"><p class="text-lg text-[color:var(--can-gold)] opacity-90">${t.step1Desc}</p></div>`;
            html += `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">`;

            for (const [letter, teams] of Object.entries(state.groups)) {
                html += `
                    <div class="space-y-3">
                        <div class="group-header py-2 px-6 text-center shadow-lg relative overflow-hidden">
                            <h3 class="font-extrabold text-xl relative z-10">${t.group} ${letter}</h3>
                        </div>
                        <div class="space-y-2">
                            ${teams.map((teamCode, index) => {
                                const team = TEAMS[teamCode];
                                return `
                                    <div class="team-card rounded-lg flex items-center justify-between p-3 group relative">
                                        <div class="flex items-center gap-4 relative z-10">
                                            <span class="text-white/40 font-mono font-bold w-4 text-center">${index + 1}</span>
                                            <img src="${getFlagUrl(team.flag)}" class="flag-icon" alt="${team.name}">
                                            <span class="font-bold tracking-wide text-sm">${team.name}</span>
                                        </div>
                                        <div class="flex flex-col gap-1 relative z-10">
                                            ${index > 0 ? `<button onclick="moveTeam('${letter}', ${index}, 'up')" class="w-6 h-6 flex items-center justify-center bg-black/20 hover:bg-[color:var(--can-green)] rounded text-xs transition-colors">▲</button>` : '<div class="w-6 h-6"></div>'}
                                            ${index < 3 ? `<button onclick="moveTeam('${letter}', ${index}, 'down')" class="w-6 h-6 flex items-center justify-center bg-black/20 hover:bg-[color:var(--can-red)] rounded text-xs transition-colors">▼</button>` : '<div class="w-6 h-6"></div>'}
                                        </div>
                                    </div>
                                `;
                            }).join('')}
                        </div>
                    </div>
                `;
            }
            html += `</div>`;
            html += `
                <div class="mt-10 flex justify-center">
                    <button onclick="state.step = 2; render()" class="btn-primary py-3 px-10 rounded-full font-bold text-lg shadow-xl flex items-center gap-3">
                        ${t.nextBtn} <span class="arrow-right">➜</span>
                    </button>
                </div>
            `;
            return html;
        }

        function renderThirds(t) {
            let html = `<div class="text-center mb-6"><p class="text-lg text-[color:var(--can-gold)]">${t.step2Desc}</p></div>`;
            html += `<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4 mb-8">`;
            
            Object.keys(state.groups).forEach(letter => {
                const teamCode = state.groups[letter][2];
                const team = TEAMS[teamCode];
                const isSelected = state.thirds.includes(letter);
                
                html += `
                    <div onclick="toggleThird('${letter}')" 
                         class="cursor-pointer bg-[#6d111c] p-4 rounded-xl shadow-lg transition-all transform hover:scale-105 border-2 ${isSelected ? 'border-[color:var(--can-green)] ring-2 ring-green-500/50' : 'border-transparent hover:border-[color:var(--can-gold)]'}">
                        <div class="text-xs font-bold text-[color:var(--can-gold)] mb-2 uppercase text-center border-b border-white/10 pb-1">${t.group} ${letter}</div>
                        <div class="flex flex-col items-center gap-3 pt-2">
                            <img src="${getFlagUrl(team.flag)}" class="w-16 h-10 object-cover rounded shadow-md border border-white/10">
                            <span class="font-bold text-center text-sm">${team.name}</span>
                        </div>
                        <div class="mt-3 flex justify-center">
                            <div class="w-6 h-6 rounded-full border border-white/30 flex items-center justify-center ${isSelected ? 'bg-[color:var(--can-green)] text-white border-transparent' : 'bg-black/20 text-transparent'}">
                                ✓
                            </div>
                        </div>
                    </div>
                `;
            });
            html += `</div>`;
            
            const count = state.thirds.length;
            html += `
                <div class="flex flex-col items-center gap-6 bg-black/20 p-6 rounded-2xl border border-white/5 max-w-lg mx-auto backdrop-blur-sm">
                    <div class="text-xl font-bold ${count === 4 ? 'text-[color:var(--can-green)]' : 'text-red-400'}">
                        ${count} / 4 Selected
                    </div>
                    <div class="flex gap-4">
                        <button onclick="state.step = 1; render()" class="px-6 py-3 rounded-full bg-white/10 hover:bg-white/20 font-bold text-white transition-colors">
                            ${t.prevBtn}
                        </button>
                        <button onclick="generateBracket()" ${count !== 4 ? 'disabled' : ''} class="btn-primary py-3 px-8 rounded-full font-bold text-lg shadow-lg flex items-center gap-2 disabled:opacity-50 disabled:grayscale disabled:cursor-not-allowed">
                            ${t.generateBtn}
                        </button>
                    </div>
                </div>
            `;
            return html;
        }

        function renderMatch(match, round, index) {
            if (!match.p1 || !match.p2) return `<div class="bg-black/20 rounded p-2 text-center text-xs text-white/30 border border-white/5">...</div>`;
            
            const p1Won = match.winner && match.winner.code === match.p1.code;
            const p2Won = match.winner && match.winner.code === match.p2.code;

            return `
                <div class="bg-[#6d111c] rounded-lg shadow-lg border border-[color:var(--can-gold)]/30 overflow-hidden flex flex-col w-full text-sm">
                    <div onclick="advanceTeam('${round}', ${index}, TEAMS['${match.p1.code}'])" 
                         class="team-card p-2 flex justify-between items-center border-b border-white/10 ${p1Won ? 'selected' : ''}">
                        <div class="flex items-center gap-2">
                            <img src="${getFlagUrl(match.p1.flag)}" class="w-5 h-3.5 object-cover opacity-90">
                            <span class="font-semibold truncate max-w-[100px]">${match.p1.name}</span>
                        </div>
                        ${p1Won ? '<span class="text-[color:var(--can-gold)]">★</span>' : ''}
                    </div>
                    <div onclick="advanceTeam('${round}', ${index}, TEAMS['${match.p2.code}'])" 
                         class="team-card p-2 flex justify-between items-center ${p2Won ? 'selected' : ''}">
                        <div class="flex items-center gap-2">
                            <img src="${getFlagUrl(match.p2.flag)}" class="w-5 h-3.5 object-cover opacity-90">
                            <span class="font-semibold truncate max-w-[100px]">${match.p2.name}</span>
                        </div>
                        ${p2Won ? '<span class="text-[color:var(--can-gold)]">★</span>' : ''}
                    </div>
                </div>
            `;
        }

        function renderBracketView(t) {
            let html = `<div class="text-center mb-6"><p class="text-lg text-[color:var(--can-gold)]">${t.step3Desc}</p></div>`;
            
            html += `<div class="overflow-x-auto pb-12 custom-scrollbar"><div class="min-w-[1000px] px-4">`;
            
            html += `<div class="grid grid-cols-7 gap-4 items-center">`;
            
            const colStyle = "flex flex-col justify-around h-full gap-4";
            
            html += `<div class="${colStyle}">
                        <h4 class="text-center font-bold text-[color:var(--can-gold)] mb-2 uppercase text-xs tracking-widest">${t.r16}</h4>
                        ${state.bracket.r16.map((m, i) => renderMatch(m, 'r16', i)).join('<div class="h-2"></div>')}
                     </div>`;

            html += `<div class="flex flex-col justify-around items-center h-full opacity-30"><div class="h-[90%] w-px bg-[color:var(--can-gold)]"></div></div>`;

            html += `<div class="${colStyle} py-8">
                        <h4 class="text-center font-bold text-[color:var(--can-gold)] mb-2 uppercase text-xs tracking-widest">${t.qf}</h4>
                        ${state.bracket.qf.map((m, i) => renderMatch(m, 'qf', i)).join('')}
                     </div>`;
            
            html += `<div class="flex flex-col justify-around items-center h-full opacity-30"><div class="h-[80%] w-px bg-[color:var(--can-gold)]"></div></div>`;

            html += `<div class="${colStyle} py-16">
                        <h4 class="text-center font-bold text-[color:var(--can-gold)] mb-2 uppercase text-xs tracking-widest">${t.sf}</h4>
                        ${state.bracket.sf.map((m, i) => renderMatch(m, 'sf', i)).join('')}
                     </div>`;

            html += `<div class="flex flex-col justify-around items-center h-full opacity-30"><div class="h-[60%] w-px bg-[color:var(--can-gold)]"></div></div>`;

            html += `<div class="flex flex-col justify-center items-center gap-6 h-full">
                        <h4 class="text-center font-bold text-[color:var(--can-gold)] text-xl mb-4 uppercase tracking-widest">🏆 ${t.fin}</h4>
                        <div class="scale-125 transform w-full shadow-2xl shadow-black/50">
                             ${renderMatch(state.bracket.final[0], 'final', 0)}
                        </div>
                        ${state.bracket.final[0].winner ? `
                            <div class="mt-8 text-center animate-bounce">
                                <div class="text-xs uppercase tracking-widest text-[color:var(--can-gold)] mb-2">${t.winner}</div>
                                <div class="text-3xl font-extrabold text-white drop-shadow-md">
                                    ${state.bracket.final[0].winner.name}
                                </div>
                                <img src="${getFlagUrl(state.bracket.final[0].winner.flag)}" class="w-24 h-auto mx-auto mt-4 shadow-xl rounded border-2 border-[color:var(--can-gold)]">
                            </div>
                        ` : ''}
                     </div>`;
            
            html += `</div></div></div>`;

            html += `
                <div class="mt-8 flex justify-center gap-4 relative z-20">
                    <button onclick="state.step = 2; render()" class="px-6 py-3 rounded-full bg-white/10 hover:bg-white/20 font-bold text-white transition-colors">
                        ${t.prevBtn}
                    </button>
                    <button onclick="window.location.reload()" class="px-6 py-3 rounded-full border border-[color:var(--can-red)] text-red-300 hover:bg-red-900/50 font-bold transition-colors">
                        ${t.reset}
                    </button>
                </div>
            `;
            return html;
        }

        function render() {
            const app = document.getElementById('app');
            const t = TRANSLATIONS[state.lang];
            let content = renderHeader(t);
            if (state.step === 1) content += renderGroups(t);
            else if (state.step === 2) content += renderThirds(t);
            else if (state.step === 3) content += renderBracketView(t);
            app.innerHTML = content;
        }

        // Init
        // Note: The setLang function is called here to initialize the language and the UI texts (including video titles/descriptions).
        setLang('fr');
    </script>
</body>
</html>
