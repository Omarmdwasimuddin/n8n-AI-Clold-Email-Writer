<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pitch Dark</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Syncopate:wght@400;700&family=Plus+Jakarta+Sans:wght@300;500;800&display=swap" rel="stylesheet">
    <style>
        :root { --accent: #8b5cf6; }
        body { 
            transition: background-color 0.5s ease, color 0.5s ease;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
        }
        body.dark { background: #020205; color: #fff; }
        body.light { background: #f8fafc; color: #0f172a; }
        .mesh {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: -1;
            transition: opacity 0.8s ease;
        }
        .dark .mesh {
            background: radial-gradient(at 0% 0%, rgba(139, 92, 246, 0.15) 0px, transparent 50%),
                        radial-gradient(at 100% 100%, rgba(37, 99, 235, 0.1) 0px, transparent 50%);
        }
        .light .mesh {
            background: radial-gradient(at 0% 0%, rgba(139, 92, 246, 0.1) 0px, transparent 50%),
                        radial-gradient(at 100% 100%, rgba(203, 213, 225, 0.5) 0px, transparent 50%);
        }
        .glass-container {
            backdrop-filter: blur(20px);
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .dark .glass-container {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }
        .light .glass-container {
            background: rgba(255, 255, 255, 0.7);
            border: 1px solid rgba(0, 0, 0, 0.05);
            box-shadow: 0 20px 40px rgba(0,0,0,0.05);
        }
        .theme-input { transition: all 0.3s ease; }
        .dark .theme-input { color: #fff; background: rgba(255,255,255,0.03); border-color: rgba(255,255,255,0.1); }
        .light .theme-input { color: #0f172a; background: rgba(0,0,0,0.02); border-color: rgba(0,0,0,0.1); }
        .killing-btn {
            background: linear-gradient(135deg, #8b5cf6 0%, #3b82f6 100%);
            transition: all 0.3s ease;
        }
        .killing-btn:hover { transform: translateY(-3px); box-shadow: 0 15px 30px rgba(139, 92, 246, 0.4); }
        .title-font { font-family: 'Syncopate', sans-serif; }
    </style>
</head>
<body class="dark min-h-screen flex items-center justify-center p-4">

    <div class="mesh"></div>

    <button onclick="toggleTheme()" class="fixed top-8 right-8 w-12 h-12 rounded-full glass-container z-50 flex items-center justify-center hover:scale-110 active:scale-95 transition-all outline-none">
        <i id="themeIcon" class="fa-solid fa-moon text-xl text-purple-400"></i>
    </button>

    <main class="w-full max-w-[450px]">
        <div class="text-center mb-10">
            <div class="inline-block px-4 py-1 rounded-full border border-purple-500/30 bg-purple-500/10 text-purple-400 text-[9px] font-bold uppercase tracking-[4px] mb-4">
                Version 2.0 Active
            </div>
            <h1 class="title-font text-4xl font-bold tracking-tighter mb-2">
                AI <span class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-blue-500">OUTREACH</span>
            </h1>
            <p class="opacity-50 text-sm font-light uppercase tracking-widest">Cold Outreach Redefined</p>
        </div>

        <div class="glass-container p-8 rounded-[2.5rem] space-y-8">
            <div class="space-y-6">
                <div class="group relative">
                    <label class="text-[10px] font-bold text-gray-500 uppercase tracking-widest ml-1 mb-2 block group-focus-within:text-purple-500 transition-all">Target Prospect Name</label>
                    <input id="clientName" type="text" placeholder="Elon Musk" 
                        class="theme-input w-full border rounded-2xl px-5 py-4 text-sm outline-none focus:ring-2 focus:ring-purple-500/20 placeholder:opacity-30">
                </div>

                <div class="group relative">
                    <label class="text-[10px] font-bold text-gray-500 uppercase tracking-widest ml-1 mb-2 block group-focus-within:text-purple-500 transition-all">Target Email Address</label>
                    <input id="clientEmail" type="email" placeholder="elon@spacex.com" 
                        class="theme-input w-full border rounded-2xl px-5 py-4 text-sm outline-none focus:ring-2 focus:ring-purple-500/20 placeholder:opacity-30">
                </div>

                <div class="group relative">
                    <label class="text-[10px] font-bold text-gray-500 uppercase tracking-widest ml-1 mb-2 block group-focus-within:text-purple-500 transition-all">What's the offer?</label>
                    <input id="service" type="text" placeholder="Growth Hacking" 
                        class="theme-input w-full border rounded-2xl px-5 py-4 text-sm outline-none focus:ring-2 focus:ring-purple-500/20 placeholder:opacity-30">
                </div>
            </div>

            <button onclick="generateOutreach()" id="btn" 
                class="killing-btn w-full py-5 rounded-2xl text-xs font-black uppercase tracking-[3px] text-white flex items-center justify-center gap-3 active:scale-95">
                <span id="btnText">Execute Draft</span>
                <i id="icon" class="fa-solid fa-bolt text-xs"></i>
                <div id="loader" class="hidden w-5 h-5 border-2 border-white/20 border-t-white rounded-full animate-spin"></div>
            </button>
        </div>

        <div id="resultBox" class="hidden mt-8 transition-all">
            <div class="flex items-center justify-between px-4 mb-3">
                <span class="text-[10px] font-bold text-purple-500 uppercase tracking-[2px]">System Generated</span>
                <button onclick="copyEmail()" class="text-[9px] text-gray-500 hover:text-purple-500 transition-all uppercase font-bold tracking-widest outline-none">Copy File</button>
            </div>
            <div class="glass-container p-6 rounded-3xl border-l-4 border-purple-500">
                <p id="emailContent" class="text-[13px] opacity-80 leading-relaxed font-medium"></p>
            </div>
        </div>
    </main>

    <script>
        function toggleTheme() {
            const body = document.body;
            const icon = document.getElementById('themeIcon');
            if (body.classList.contains('dark')) {
                body.classList.replace('dark', 'light');
                icon.classList.replace('fa-moon', 'fa-sun');
                icon.classList.replace('text-purple-400', 'text-orange-500');
            } else {
                body.classList.replace('light', 'dark');
                icon.classList.replace('fa-sun', 'fa-moon');
                icon.classList.replace('text-orange-500', 'text-purple-400');
            }
        }

        async function generateOutreach() {
            const clientInput = document.getElementById('clientName');
            const emailInput = document.getElementById('clientEmail');
            const serviceInput = document.getElementById('service');
            
            const client = clientInput.value;
            const email = emailInput.value;
            const service = serviceInput.value;
            
            const btn = document.getElementById('btn');
            const btnText = document.getElementById('btnText');
            const icon = document.getElementById('icon');
            const loader = document.getElementById('loader');
            const resultBox = document.getElementById('resultBox');
            const content = document.getElementById('emailContent');

            if(!client || !service || !email) {
                alert("Please fill all fields");
                return;
            }

            btn.disabled = true;
            btnText.innerText = "Processing...";
            icon.classList.add('hidden');
            loader.classList.remove('hidden');

            try {
                const response = await fetch('http://localhost:5678/webhook-test/c86afbea-5b3d-47b5-ac4e-c26e44e97171', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ 
                        clientName: client, 
                        clientEmail: email,
                        service: service 
                    })
                });
                const data = await response.text();
                
                resultBox.classList.remove('hidden');
                content.innerText = data;

                clientInput.value = "";
                emailInput.value = "";
                serviceInput.value = "";
                
            } catch (e) {
                resultBox.classList.remove('hidden');
                content.innerText = "Network Error. Check your connection.";
            } finally {
                btn.disabled = false;
                btnText.innerText = "Execute Draft";
                icon.classList.remove('hidden');
                loader.classList.add('hidden');
            }
        }

        function copyEmail() {
            const text = document.getElementById('emailContent').innerText;
            navigator.clipboard.writeText(text);
            const btn = event.target;
            btn.innerText = "Copied!";
            setTimeout(() => btn.innerText = "Copy File", 2000);
        }
    </script>
</body>
</html>
