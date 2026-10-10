<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Sister! 🎉💖</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600;700&family=Playfair+Display:ital,wght@0,500;0,700;1,400&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Canvas Confetti Library -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        rosegold: {
                            50: '#fdf8f8',
                            100: '#f9eeef',
                            200: '#f3d9dc',
                            300: '#e7b8be',
                            400: '#d7909a',
                            500: '#c56d7b',
                            600: '#b05261',
                            700: '#93404e',
                        },
                        champagne: '#f7e7ce',
                        blush: '#fff0f3',
                    },
                    fontFamily: {
                        serif: ['Playfair Display', 'serif'],
                        handwritten: ['Dancing Script', 'cursive'],
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #fef2f4;
        }
        ::-webkit-scrollbar-thumb {
            background: #e7b8be;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #c56d7b;
        }

        /* 3D Flip Card Styles */
        .perspective-1000 {
            perspective: 1000px;
        }
        .transform-style-3d {
            transform-style: preserve-3d;
        }
        .backface-hidden {
            backface-visibility: hidden;
            -webkit-backface-visibility: hidden;
        }
        .rotate-y-180 {
            transform: rotateY(180deg);
        }

        /* Candle Flame Flickering Animation */
        @keyframes flicker {
            0%, 100% { transform: scale(1) rotate(-1deg); opacity: 0.9; }
            20% { transform: scale(1.1, 0.9) rotate(2deg); opacity: 1; }
            40% { transform: scale(0.95, 1.05) rotate(-2deg); opacity: 0.85; }
            60% { transform: scale(1.05, 0.98) rotate(1deg); opacity: 0.95; }
            80% { transform: scale(0.98, 1.02) rotate(-1deg); opacity: 1; }
        }
        .flame-anim {
            animation: flicker 1.2s infinite ease-in-out;
            transform-origin: bottom center;
        }

        /* Smoke effect after candle blowout */
        @keyframes smoke {
            0% { opacity: 0.8; transform: translateY(0) scale(0.8); }
            100% { opacity: 0; transform: translateY(-30px) scale(2); }
        }
        .smoke-anim {
            animation: smoke 1.8s forwards ease-out;
        }

        /* Floating Balloon Animation */
        @keyframes floatSlow {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-18px) rotate(3deg); }
        }
        .float-balloon {
            animation: floatSlow 5s ease-in-out infinite;
        }

        /* Sparkle Pulse */
        @keyframes sparklePulse {
            0%, 100% { opacity: 0.3; transform: scale(0.8); }
            50% { opacity: 1; transform: scale(1.2); }
        }
        .sparkle-anim {
            animation: sparklePulse 2.5s ease-in-out infinite;
        }

        /* Gift Box Lid Animation */
        .lid-open {
            transform: translateY(-80px) rotate(-15deg);
            opacity: 0;
            transition: all 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
        }

        /* Gradient Text Shimmer */
        .text-gradient-rosegold {
            background: linear-gradient(135deg, #b05261 0%, #d7909a 50%, #8a3342 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
    </style>
</head>

<body class="bg-gradient-to-br from-blush via-rose-50 to-amber-50 font-sans text-slate-800 min-h-screen relative overflow-x-hidden selection:bg-rosegold-200 selection:text-rosegold-700">

    <div id="gift-overlay" class="fixed inset-0 z-50 flex flex-col items-center justify-center bg-slate-900/90 backdrop-blur-md transition-opacity duration-1000 p-4 text-center">
        <div class="max-w-md w-full bg-white/10 border border-white/20 p-8 rounded-3xl shadow-2xl backdrop-blur-lg flex flex-col items-center relative overflow-hidden">
            <!-- Decorative Ambient Sparkles -->
            <div class="absolute top-4 left-4 text-yellow-300 text-xl sparkle-anim"><i class="fa-solid fa-sparkles"></i></div>
            <div class="absolute bottom-6 right-6 text-pink-300 text-2xl sparkle-anim" style="animation-delay: 1s;"><i class="fa-solid fa-star"></i></div>
            
            <span class="inline-block px-4 py-1.5 rounded-full bg-rosegold-500/20 text-rosegold-200 text-sm font-medium tracking-wide mb-4 border border-rosegold-400/30">
                ✨ A Special Surprise Awaits ✨
            </span>
            
            <h1 class="text-3xl sm:text-4xl font-serif text-white font-bold mb-2">For My Dearest Sister</h1>
            <p class="text-rose-200 text-sm sm:text-base mb-8">Someone loves you very much! Tap the gift box below to unwrap your birthday surprise.</p>

            <!-- Interactive Gift Box Container -->
            <div id="gift-container" onclick="openGiftSurprise()" class="cursor-pointer group relative w-44 h-44 flex items-center justify-center transition-transform duration-300 hover:scale-105 my-4">
                <!-- Sparkle halo behind box -->
                <div class="absolute inset-0 bg-rosegold-400/30 rounded-full blur-2xl group-hover:bg-rosegold-300/50 transition-all"></div>
                
                <!-- Gift Box Graphic -->
                <div class="relative w-36 h-36 flex flex-col items-center justify-end">
                    <!-- Lid -->
                    <div id="gift-lid" class="w-40 h-10 bg-gradient-to-r from-rosegold-400 via-rosegold-500 to-rosegold-600 rounded-t-lg shadow-lg relative z-20 flex items-center justify-center transition-all duration-700">
                        <!-- Bow -->
                        <div class="absolute -top-6 w-12 h-8 bg-amber-300 rounded-full flex items-center justify-center shadow-md">
                            <div class="w-4 h-4 bg-amber-400 rounded-full"></div>
                        </div>
                        <div class="w-6 h-full bg-amber-300"></div>
                    </div>
                    <!-- Box Body -->
                    <div class="w-36 h-28 bg-gradient-to-br from-rosegold-500 to-rosegold-700 rounded-b-xl shadow-xl relative z-10 flex justify-center items-center overflow-hidden">
                        <div class="w-6 h-full bg-amber-300"></div>
                        <!-- Ribbon Cross -->
                        <div class="absolute h-6 w-full bg-amber-300/80"></div>
                    </div>
                </div>
            </div>

            <!-- Pulsing Tap Prompt -->
            <button onclick="openGiftSurprise()" class="mt-6 px-6 py-3 bg-gradient-to-r from-rosegold-500 to-amber-500 text-white font-semibold rounded-full shadow-lg hover:shadow-rosegold-500/40 hover:scale-105 active:scale-95 transition-all duration-300 flex items-center space-x-2 animate-bounce">
                <i class="fa-solid fa-gift"></i>
                <span>Tap to Open Your Surprise!</span>
            </button>
        </div>
    </div>

    <header class="sticky top-0 z-40 bg-white/70 backdrop-blur-md border-b border-rose-100 shadow-sm transition-all">
        <div class="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-2">
                <div class="w-9 h-9 rounded-full bg-rosegold-100 border border-rosegold-300 flex items-center justify-center text-rosegold-600 shadow-inner">
                    <i class="fa-solid fa-heart text-sm"></i>
                </div>
                <span class="font-serif font-bold text-lg sm:text-xl text-slate-800 tracking-tight">Sister's Birthday Spot</span>
            </div>

            <!-- Quick Action Buttons -->
            <div class="flex items-center space-x-2">
                <!-- Background Melody Synth Toggle -->
                <button id="music-btn" onclick="toggleAudio()" class="px-3 py-1.5 text-xs sm:text-sm bg-rose-100 hover:bg-rose-200 text-rosegold-700 font-medium rounded-full transition flex items-center space-x-1.5" title="Toggle Birthday Chime">
                    <i id="music-icon" class="fa-solid fa-music"></i>
                    <span id="music-text" class="hidden sm:inline">Play Melody</span>
                </button>

                <!-- Edit Mode Toggle Button -->
                <button id="edit-mode-btn" onclick="toggleEditMode()" class="px-3 py-1.5 text-xs sm:text-sm bg-amber-100 hover:bg-amber-200 text-amber-800 font-medium rounded-full transition flex items-center space-x-1.5" title="Customize Text & Names">
                    <i class="fa-solid fa-pen-to-square"></i>
                    <span id="edit-text" class="hidden sm:inline">Customize Page</span>
                </button>
            </div>
        </div>
    </header>

    <main class="max-w-6xl mx-auto px-4 py-8 space-y-16">
        
        <!-- HERO GREETING SECTION -->
        <section class="relative bg-white/80 border border-rose-100/80 rounded-3xl p-6 sm:p-12 shadow-xl backdrop-blur-md overflow-hidden text-center flex flex-col items-center">
            
            <!-- Ambient Floating Balloons Graphic Elements -->
            <div class="absolute -top-4 -left-4 text-rosegold-300/40 text-7xl float-balloon pointer-events-none select-none">🎈</div>
            <div class="absolute top-10 right-4 text-pink-300/40 text-6xl float-balloon pointer-events-none select-none" style="animation-delay: 1.5s;">🎈</div>
            <div class="absolute -bottom-6 left-12 text-rose-300/30 text-8xl float-balloon pointer-events-none select-none" style="animation-delay: 2.5s;">🎈</div>

            <div class="inline-flex items-center space-x-2 px-4 py-1.5 rounded-full bg-rose-100/80 text-rosegold-700 text-xs sm:text-sm font-semibold tracking-wider uppercase mb-4 border border-rose-200">
                <i class="fa-solid fa-cake-candles text-rosegold-500"></i>
                <span>Celebrating The World's Best Sister</span>
            </div>

            <h1 class="text-4xl sm:text-6xl md:text-7xl font-serif font-bold text-slate-800 leading-tight mb-4">
                Happy Birthday, <br class="hidden sm:inline" />
                <span id="sister-name-display" class="text-gradient-rosegold font-handwritten text-5xl sm:text-7xl md:text-8xl font-normal inline-block transition-all">
                    Dearest Sister!
                </span>
            </h1>

            <p id="hero-tagline-display" class="text-slate-600 text-base sm:text-xl max-w-2xl font-light leading-relaxed mb-8">
                Today is all about celebrating you! Your laughter brightens our home, your warmth touches everyone around you, and life is simply so much sweeter with you as my sister.
            </p>

            <!-- Anniversary / Countdown / Celebration Counter Badge -->
            <div class="grid grid-cols-2 sm:grid-cols-3 gap-3 sm:gap-6 max-w-xl w-full">
                <div class="bg-rose-50/80 border border-rose-100 rounded-2xl p-4 flex flex-col items-center shadow-sm">
                    <span class="text-rosegold-600 text-2xl font-bold font-serif">365 / 365</span>
                    <span class="text-xs text-slate-500 font-medium uppercase mt-1">Days of Joy</span>
                </div>
                <div class="bg-rose-50/80 border border-rose-100 rounded-2xl p-4 flex flex-col items-center shadow-sm">
                    <span class="text-rosegold-600 text-2xl font-bold font-serif">#1</span>
                    <span class="text-xs text-slate-500 font-medium uppercase mt-1">Sister Rank</span>
                </div>
                <div class="col-span-2 sm:col-span-1 bg-rose-50/80 border border-rose-100 rounded-2xl p-4 flex flex-col items-center shadow-sm">
                    <span class="text-rosegold-600 text-2xl font-bold font-serif">∞</span>
                    <span class="text-xs text-slate-500 font-medium uppercase mt-1">Love & Smiles</span>
                </div>
            </div>

            <!-- Decorative divider -->
            <div class="mt-8 flex items-center justify-center space-x-3 text-rosegold-300">
                <span class="h-px w-12 bg-rosegold-200"></span>
                <i class="fa-solid fa-crown text-sm"></i>
                <span class="h-px w-12 bg-rosegold-200"></span>
            </div>
        </section>

        <section class="bg-gradient-to-br from-white to-rose-50/50 border border-rose-100 rounded-3xl p-6 sm:p-10 shadow-xl relative overflow-hidden">
            <div class="text-center max-w-xl mx-auto mb-8">
                <span class="text-rosegold-600 text-sm font-semibold tracking-wider uppercase"><i class="fa-solid fa-wand-magic-sparkles mr-1"></i> Make A Wish</span>
                <h2 class="text-3xl sm:text-4xl font-serif font-bold text-slate-800 mt-1">Interactive Birthday Cake</h2>
                <p class="text-slate-600 text-sm sm:text-base mt-2">Tap the candle flames or click the button below to blow out the candles and make a magical birthday wish!</p>
            </div>

            <!-- Virtual Cake Container -->
            <div class="flex flex-col items-center justify-center my-6 relative min-h-[260px]">
                
                <!-- Cake Base Graphic -->
                <div class="relative w-64 sm:w-72 flex flex-col items-center">
                    
                    <!-- Candle Row -->
                    <div class="flex justify-center space-x-6 mb-1 relative z-20">
                        <!-- Candle 1 -->
                        <div class="candle-wrapper flex flex-col items-center cursor-pointer group" onclick="extinguishCandle(this)">
                            <div class="flame flame-anim w-4 h-6 bg-gradient-to-t from-amber-500 via-orange-400 to-yellow-200 rounded-full shadow-[0_0_12px_rgba(251,191,36,0.9)]"></div>
                            <div class="smoke hidden w-2 h-6 bg-slate-300/60 rounded-full"></div>
                            <div class="w-3 h-12 bg-gradient-to-b from-pink-300 to-rose-400 rounded-t-sm shadow-inner border-t border-white/40"></div>
                        </div>
                        <!-- Candle 2 (Center) -->
                        <div class="candle-wrapper flex flex-col items-center cursor-pointer group" onclick="extinguishCandle(this)">
                            <div class="flame flame-anim w-4 h-6 bg-gradient-to-t from-amber-500 via-orange-400 to-yellow-200 rounded-full shadow-[0_0_12px_rgba(251,191,36,0.9)]"></div>
                            <div class="smoke hidden w-2 h-6 bg-slate-300/60 rounded-full"></div>
                            <div class="w-3 h-14 bg-gradient-to-b from-amber-200 to-amber-400 rounded-t-sm shadow-inner border-t border-white/40"></div>
                        </div>
                        <!-- Candle 3 -->
                        <div class="candle-wrapper flex flex-col items-center cursor-pointer group" onclick="extinguishCandle(this)">
                            <div class="flame flame-anim w-4 h-6 bg-gradient-to-t from-amber-500 via-orange-400 to-yellow-200 rounded-full shadow-[0_0_12px_rgba(251,191,36,0.9)]"></div>
                            <div class="smoke hidden w-2 h-6 bg-slate-300/60 rounded-full"></div>
                            <div class="w-3 h-12 bg-gradient-to-b from-purple-300 to-indigo-400 rounded-t-sm shadow-inner border-t border-white/40"></div>
                        </div>
                    </div>

                    <!-- Top Tier -->
                    <div class="w-48 h-16 bg-gradient-to-r from-pink-200 via-rose-200 to-pink-300 rounded-t-2xl border-b-4 border-rose-300 shadow-md relative overflow-hidden flex items-center justify-around px-4">
                        <!-- Cream Drippings -->
                        <div class="absolute top-0 inset-x-0 h-4 bg-white/90 rounded-b-xl"></div>
                        <span class="text-xs text-rosegold-700 font-serif font-bold relative z-10">★ Sweet Sister ★</span>
                    </div>

                    <!-- Bottom Tier -->
                    <div class="w-64 h-20 bg-gradient-to-r from-amber-100 via-rose-100 to-amber-200 rounded-t-xl border-b-8 border-amber-200 shadow-lg relative overflow-hidden flex items-center justify-center">
                        <div class="absolute top-0 inset-x-0 h-5 bg-white/80 rounded-b-2xl"></div>
                        <div class="flex space-x-3 text-rosegold-400 text-sm">
                            <i class="fa-solid fa-heart"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-heart"></i>
                            <i class="fa-solid fa-star"></i>
                            <i class="fa-solid fa-heart"></i>
                        </div>
                    </div>

                    <!-- Cake Stand Plate -->
                    <div class="w-72 sm:w-80 h-4 bg-slate-200 border-t-2 border-white rounded-full shadow-md"></div>
                    <div class="w-24 h-6 bg-slate-300 rounded-b-lg shadow-inner"></div>
                </div>
            </div>

            <!-- Cake Actions Controls -->
            <div class="flex flex-wrap items-center justify-center gap-4 mt-4">
                <button id="blow-candles-btn" onclick="blowAllCandles()" class="px-6 py-3 bg-gradient-to-r from-rosegold-500 to-rose-600 text-white font-semibold rounded-full shadow-lg hover:shadow-rose-500/30 hover:scale-105 active:scale-95 transition-all flex items-center space-x-2">
                    <i class="fa-solid fa-wind"></i>
                    <span>Blow Out Candles!</span>
                </button>
                <button onclick="reLightCandles()" class="px-5 py-3 bg-white border border-rose-200 text-rosegold-600 font-semibold rounded-full shadow-sm hover:bg-rose-50 transition-all flex items-center space-x-2">
                    <i class="fa-solid fa-fire-flame-curved text-amber-500"></i>
                    <span>Relight Candles</span>
                </button>
            </div>

            <!-- Wish Revealed Modal Banner -->
            <div id="wish-modal" class="hidden mt-6 bg-amber-50/90 border border-amber-200 rounded-2xl p-6 text-center animate-fade-in shadow-md">
                <div class="inline-flex p-3 bg-amber-100 text-amber-600 rounded-full mb-3">
                    <i class="fa-solid fa-wand-magic-sparkles text-xl"></i>
                </div>
                <h3 class="text-xl font-serif font-bold text-amber-900">Your Birthday Wish Has Been Sent to the Universe! ✨</h3>
                <p id="wish-text-display" class="text-amber-800 text-sm sm:text-base mt-2 max-w-md mx-auto">
                    May all your dreams come true, your year be filled with laughter, success, happiness, and all the love you so richly deserve!
                </p>
            </div>
        </section>

        <section class="space-y-6">
            <div class="text-center max-w-xl mx-auto">
                <span class="text-rosegold-600 text-sm font-semibold tracking-wider uppercase"><i class="fa-solid fa-camera-retro mr-1"></i> Treasured Times</span>
                <h2 class="text-3xl sm:text-4xl font-serif font-bold text-slate-800 mt-1">Sister Memory Lane</h2>
                <p class="text-slate-600 text-sm sm:text-base mt-2">A tiny glance at all the wonderful moments, laughs, and memories shared together.</p>
            </div>

            <!-- Polaroid Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 pt-4">
                
                <!-- Polaroid Card 1 -->
                <div class="bg-white p-4 pb-6 rounded-lg shadow-md hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 hover:rotate-1 border border-slate-100 relative group">
                    <!-- Washi Tape Decor -->
                    <div class="absolute -top-3 left-1/2 -translate-x-1/2 w-20 h-6 bg-amber-200/60 backdrop-blur-sm transform -rotate-2 border border-amber-300/40 z-10"></div>
                    
                    <div class="relative overflow-hidden rounded-md bg-slate-100 aspect-square flex items-center justify-center mb-4 border border-slate-100">
                        <img id="img-1" src="https://images.unsplash.com/photo-1511895426328-dc8714191300?auto=format&fit=crop&q=80&w=600" alt="Sister smile" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" onerror="this.src='https://placehold.co/600x600/f3d9dc/b05261?text=Best+Sister+Memories'">
                        
                        <!-- Upload replacement photo overlay -->
                        <label for="upload-1" class="absolute inset-0 bg-slate-900/40 opacity-0 group-hover:opacity-100 transition-opacity flex flex-col items-center justify-center text-white cursor-pointer p-2 text-center text-xs">
                            <i class="fa-solid fa-camera text-2xl mb-1"></i>
                            <span>Click to Change Photo</span>
                            <input type="file" id="upload-1" accept="image/*" class="hidden" onchange="previewImage(event, 'img-1')">
                        </label>
                    </div>
                    <p id="caption-1" class="font-handwritten text-xl text-center text-slate-700 px-2 font-semibold">"Always my favorite partner in crime!"</p>
                </div>

                <!-- Polaroid Card 2 -->
                <div class="bg-white p-4 pb-6 rounded-lg shadow-md hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 hover:-rotate-1 border border-slate-100 relative group">
                    <div class="absolute -top-3 left-1/2 -translate-x-1/2 w-20 h-6 bg-rose-200/60 backdrop-blur-sm transform rotate-3 border border-rose-300/40 z-10"></div>
                    
                    <div class="relative overflow-hidden rounded-md bg-slate-100 aspect-square flex items-center justify-center mb-4 border border-slate-100">
                        <img id="img-2" src="https://images.unsplash.com/photo-1529156069898-49953e39b3ac?auto=format&fit=crop&q=80&w=600" alt="Warm Laughs" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" onerror="this.src='https://placehold.co/600x600/f3d9dc/b05261?text=Laughs+%26+Joy'">
                        
                        <label for="upload-2" class="absolute inset-0 bg-slate-900/40 opacity-0 group-hover:opacity-100 transition-opacity flex flex-col items-center justify-center text-white cursor-pointer p-2 text-center text-xs">
                            <i class="fa-solid fa-camera text-2xl mb-1"></i>
                            <span>Click to Change Photo</span>
                            <input type="file" id="upload-2" accept="image/*" class="hidden" onchange="previewImage(event, 'img-2')">
                        </label>
                    </div>
                    <p id="caption-2" class="font-handwritten text-xl text-center text-slate-700 px-2 font-semibold">"Endless laughs & secret gossip sessions."</p>
                </div>

                <!-- Polaroid Card 3 -->
                <div class="bg-white p-4 pb-6 rounded-lg shadow-md hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-2 hover:rotate-2 border border-slate-100 relative group">
                    <div class="absolute -top-3 left-1/2 -translate-x-1/2 w-20 h-6 bg-champagne/80 backdrop-blur-sm transform -rotate-1 border border-amber-300/40 z-10"></div>
                    
                    <div class="relative overflow-hidden rounded-md bg-slate-100 aspect-square flex items-center justify-center mb-4 border border-slate-100">
                        <img id="img-3" src="https://images.unsplash.com/photo-1492562080023-ab3db95bfbce?auto=format&fit=crop&q=80&w=600" alt="Sunkissed Joy" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" onerror="this.src='https://placehold.co/600x600/f3d9dc/b05261?text=Sunlight+%26+Smiles'">
                        
                        <label for="upload-3" class="absolute inset-0 bg-slate-900/40 opacity-0 group-hover:opacity-100 transition-opacity flex flex-col items-center justify-center text-white cursor-pointer p-2 text-center text-xs">
                            <i class="fa-solid fa-camera text-2xl mb-1"></i>
                            <span>Click to Change Photo</span>
                            <input type="file" id="upload-3" accept="image/*" class="hidden" onchange="previewImage(event, 'img-3')">
                        </label>
                    </div>
                    <p id="caption-3" class="font-handwritten text-xl text-center text-slate-700 px-2 font-semibold">"Shining brighter than any star!"</p>
                </div>

            </div>
        </section>

        <section class="space-y-8">
            <div class="text-center max-w-xl mx-auto">
                <span class="text-rosegold-600 text-sm font-semibold tracking-wider uppercase"><i class="fa-solid fa-list-check mr-1"></i> Countless Reasons</span>
                <h2 class="text-3xl sm:text-4xl font-serif font-bold text-slate-800 mt-1">Why You're The Best Sister</h2>
                <p class="text-slate-600 text-sm sm:text-base mt-2">Click or tap any card to flip it over and uncover a sweet truth!</p>
            </div>

            <!-- Flip Cards Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                
                <!-- Reason Card 1 -->
                <div class="perspective-1000 h-48 cursor-pointer" onclick="flipCard(this)">
                    <div class="card-inner relative w-full h-full duration-500 transform-style-3d transition-transform">
                        <!-- Front -->
                        <div class="absolute inset-0 bg-gradient-to-br from-rose-100 to-rosegold-100 border border-rosegold-200 rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden">
                            <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-rosegold-500 shadow-sm mb-3">
                                <i class="fa-solid fa-user-shield text-xl"></i>
                            </div>
                            <h3 class="font-serif font-bold text-lg text-slate-800">1. Master Secret Keeper</h3>
                            <span class="text-xs text-rosegold-600 mt-2 flex items-center"><i class="fa-solid fa-hand-pointer mr-1"></i> Tap to Flip</span>
                        </div>
                        <!-- Back -->
                        <div class="absolute inset-0 bg-rosegold-600 text-white rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden rotate-y-180">
                            <p class="text-sm sm:text-base leading-relaxed">You know all my deepest secrets, embarrassing moments, and dreams—and you never ever judge!</p>
                        </div>
                    </div>
                </div>

                <!-- Reason Card 2 -->
                <div class="perspective-1000 h-48 cursor-pointer" onclick="flipCard(this)">
                    <div class="card-inner relative w-full h-full duration-500 transform-style-3d transition-transform">
                        <div class="absolute inset-0 bg-gradient-to-br from-rose-100 to-rosegold-100 border border-rosegold-200 rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden">
                            <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-rosegold-500 shadow-sm mb-3">
                                <i class="fa-solid fa-utensils text-xl"></i>
                            </div>
                            <h3 class="font-serif font-bold text-lg text-slate-800">2. Comfort Food Partner</h3>
                            <span class="text-xs text-rosegold-600 mt-2 flex items-center"><i class="fa-solid fa-hand-pointer mr-1"></i> Tap to Flip</span>
                        </div>
                        <div class="absolute inset-0 bg-rosegold-600 text-white rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden rotate-y-180">
                            <p class="text-sm sm:text-base leading-relaxed">Whether it's midnight snacks, sweet cravings, or quick tea sessions, you're always down for food!</p>
                        </div>
                    </div>
                </div>

                <!-- Reason Card 3 -->
                <div class="perspective-1000 h-48 cursor-pointer" onclick="flipCard(this)">
                    <div class="card-inner relative w-full h-full duration-500 transform-style-3d transition-transform">
                        <div class="absolute inset-0 bg-gradient-to-br from-rose-100 to-rosegold-100 border border-rosegold-200 rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden">
                            <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-rosegold-500 shadow-sm mb-3">
                                <i class="fa-solid fa-face-smile-beam text-xl"></i>
                            </div>
                            <h3 class="font-serif font-bold text-lg text-slate-800">3. Instant Mood Booster</h3>
                            <span class="text-xs text-rosegold-600 mt-2 flex items-center"><i class="fa-solid fa-hand-pointer mr-1"></i> Tap to Flip</span>
                        </div>
                        <div class="absolute inset-0 bg-rosegold-600 text-white rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden rotate-y-180">
                            <p class="text-sm sm:text-base leading-relaxed">No matter how chaotic the day gets, your jokes, silly dances, and smile instantly turn things around.</p>
                        </div>
                    </div>
                </div>

                <!-- Reason Card 4 -->
                <div class="perspective-1000 h-48 cursor-pointer" onclick="flipCard(this)">
                    <div class="card-inner relative w-full h-full duration-500 transform-style-3d transition-transform">
                        <div class="absolute inset-0 bg-gradient-to-br from-rose-100 to-rosegold-100 border border-rosegold-200 rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden">
                            <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-rosegold-500 shadow-sm mb-3">
                                <i class="fa-solid fa-compass text-xl"></i>
                            </div>
                            <h3 class="font-serif font-bold text-lg text-slate-800">4. Best Life Advisor</h3>
                            <span class="text-xs text-rosegold-600 mt-2 flex items-center"><i class="fa-solid fa-hand-pointer mr-1"></i> Tap to Flip</span>
                        </div>
                        <div class="absolute inset-0 bg-rosegold-600 text-white rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden rotate-y-180">
                            <p class="text-sm sm:text-base leading-relaxed">You give the most thoughtful, practical, and honest advice whenever I need a guiding hand.</p>
                        </div>
                    </div>
                </div>

                <!-- Reason Card 5 -->
                <div class="perspective-1000 h-48 cursor-pointer" onclick="flipCard(this)">
                    <div class="card-inner relative w-full h-full duration-500 transform-style-3d transition-transform">
                        <div class="absolute inset-0 bg-gradient-to-br from-rose-100 to-rosegold-100 border border-rosegold-200 rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden">
                            <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-rosegold-500 shadow-sm mb-3">
                                <i class="fa-solid fa-hand-holding-heart text-xl"></i>
                            </div>
                            <h3 class="font-serif font-bold text-lg text-slate-800">5. Unconditional Backing</h3>
                            <span class="text-xs text-rosegold-600 mt-2 flex items-center"><i class="fa-solid fa-hand-pointer mr-1"></i> Tap to Flip</span>
                        </div>
                        <div class="absolute inset-0 bg-rosegold-600 text-white rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden rotate-y-180">
                            <p class="text-sm sm:text-base leading-relaxed">Knowing I always have you in my corner gives me so much confidence and strength every day.</p>
                        </div>
                    </div>
                </div>

                <!-- Reason Card 6 -->
                <div class="perspective-1000 h-48 cursor-pointer" onclick="flipCard(this)">
                    <div class="card-inner relative w-full h-full duration-500 transform-style-3d transition-transform">
                        <div class="absolute inset-0 bg-gradient-to-br from-rose-100 to-rosegold-100 border border-rosegold-200 rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden">
                            <div class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-rosegold-500 shadow-sm mb-3">
                                <i class="fa-solid fa-gem text-xl"></i>
                            </div>
                            <h3 class="font-serif font-bold text-lg text-slate-800">6. One In A Million</h3>
                            <span class="text-xs text-rosegold-600 mt-2 flex items-center"><i class="fa-solid fa-hand-pointer mr-1"></i> Tap to Flip</span>
                        </div>
                        <div class="absolute inset-0 bg-rosegold-600 text-white rounded-2xl p-6 flex flex-col items-center justify-center text-center shadow-md backface-hidden rotate-y-180">
                            <p class="text-sm sm:text-base leading-relaxed">Simply put, there is no one else like you. Having you as my sister is one of life's greatest blessings!</p>
                        </div>
                    </div>
                </div>

            </div>
        </section>

        <section class="bg-gradient-to-br from-amber-50/90 via-white to-rose-50 border border-amber-200/60 rounded-3xl p-8 sm:p-12 shadow-2xl relative overflow-hidden">
            <!-- Decorative Ribbon Corner -->
            <div class="absolute top-0 right-0 w-32 h-32 overflow-hidden pointer-events-none">
                <div class="bg-gradient-to-r from-rosegold-400 to-rosegold-600 text-white text-xs font-bold uppercase py-1 text-center w-48 tracking-widest shadow-md transform rotate-45 translate-x-12 translate-y-6">
                    With Love ❤️
                </div>
            </div>

            <div class="max-w-3xl mx-auto space-y-6 relative z-10">
                <div class="flex items-center space-x-3 text-rosegold-600">
                    <i class="fa-solid fa-envelope-open-text text-3xl"></i>
                    <h2 class="text-2xl sm:text-3xl font-serif font-bold text-slate-800">A Personal Birthday Letter</h2>
                </div>

                <div class="h-0.5 w-full bg-gradient-to-r from-rosegold-300 via-rose-200 to-transparent"></div>

                <!-- Letter Body Container (Editable in Edit Mode) -->
                <div id="letter-content" class="space-y-4 text-slate-700 font-serif leading-relaxed text-base sm:text-lg pt-2">
                    <p class="font-handwritten text-3xl text-rosegold-700">Dearest Sister,</p>
                    <p>
                        As your birthday arrives, I wanted to take a quiet moment to tell you just how much you mean to me. Life moves fast, but the bond we share is timeless.
                    </p>
                    <p>
                        Thank you for all the laughter, for listening when I needed someone to talk to, for sharing food, and for standing by me through every high and low. You bring so much light and joy into our family.
                    </p>
                    <p>
                        On this birthday, my wish for you is boundless happiness, perfect health, huge success in every endeavor you pursue, and all the love in the universe. May this upcoming year bring you unforgettable adventures!
                    </p>
                    <div class="pt-4 flex flex-col items-end text-right">
                        <span class="font-handwritten text-3xl text-rosegold-700">Always & Forever,</span>
                        <span id="sender-name-display" class="font-serif font-bold text-lg text-slate-800 mt-1">Your Loving Brother, Krishna</span>
                    </div>
                </div>
            </div>
        </section>

        <section class="bg-slate-900 text-white rounded-3xl p-8 sm:p-12 shadow-2xl relative overflow-hidden text-center space-y-6">
            <!-- Background Sky Stars -->
            <div class="absolute inset-0 bg-[radial-gradient(#fff_1px,transparent_1px)] [background-size:16px_16px] opacity-20 pointer-events-none"></div>

            <div class="max-w-xl mx-auto relative z-10 space-y-3">
                <div class="inline-flex p-3 bg-rosegold-500/20 border border-rosegold-400/30 text-rosegold-300 rounded-full mb-1">
                    <i class="fa-solid fa-paper-plane text-xl"></i>
                </div>
                <h2 class="text-3xl sm:text-4xl font-serif font-bold">Virtual Wish Balloon Release</h2>
                <p class="text-slate-300 text-sm sm:text-base">Type a special birthday wish or prayer below and tap 'Release Sky Balloon' to send it floating into the sky!</p>
            </div>

            <div class="max-w-md mx-auto relative z-10 flex flex-col sm:flex-row gap-3">
                <input type="text" id="balloon-wish-input" placeholder="e.g. Wishing you endless health & happiness!" class="flex-grow px-5 py-3 rounded-full bg-slate-800/90 border border-slate-700 text-white placeholder-slate-400 focus:outline-none focus:border-rosegold-400 text-sm shadow-inner">
                <button onclick="releaseWishBalloon()" class="px-6 py-3 bg-gradient-to-r from-rosegold-500 to-amber-500 text-white font-semibold rounded-full hover:scale-105 active:scale-95 transition-all shadow-lg flex items-center justify-center space-x-2">
                    <i class="fa-solid fa-balloon text-base"></i>
                    <span>Release</span>
                </button>
            </div>

            <!-- Canvas Container for Released Sky Balloons -->
            <div id="sky-container" class="relative w-full h-40 overflow-hidden rounded-2xl bg-slate-950/50 border border-slate-800/80 mt-4">
                <div id="sky-prompt" class="absolute inset-0 flex items-center justify-center text-slate-500 text-xs italic">
                    Your released balloons will float up across the night sky here ✨
                </div>
            </div>
        </section>

    </main>

    <div id="edit-modal" class="fixed inset-0 z-50 bg-slate-900/80 backdrop-blur-sm hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-lg w-full p-6 sm:p-8 space-y-6 shadow-2xl relative max-h-[90vh] overflow-y-auto">
            <div class="flex items-center justify-between border-b pb-3">
                <h3 class="text-xl font-serif font-bold text-slate-800"><i class="fa-solid fa-pen-to-square text-rosegold-500 mr-2"></i>Customize Greeting Page</h3>
                <button onclick="toggleEditMode()" class="text-slate-400 hover:text-slate-600 text-lg"><i class="fa-solid fa-xmark"></i></button>
            </div>

            <div class="space-y-4 text-sm">
                <div>
                    <label class="block font-semibold text-slate-700 mb-1">Sister's Name / Nickname</label>
                    <input type="text" id="edit-sister-name" value="Dearest Sister!" class="w-full px-4 py-2 border rounded-xl focus:ring-2 focus:ring-rosegold-300 outline-none">
                </div>

                <div>
                    <label class="block font-semibold text-slate-700 mb-1">Hero Tagline</label>
                    <textarea id="edit-tagline" rows="2" class="w-full px-4 py-2 border rounded-xl focus:ring-2 focus:ring-rosegold-300 outline-none">Today is all about celebrating you! Your laughter brightens our home, your warmth touches everyone around you, and life is simply so much sweeter with you as my sister.</textarea>
                </div>

                <div>
                    <label class="block font-semibold text-slate-700 mb-1">Your Name (Sender)</label>
                    <input type="text" id="edit-sender-name" value="Your Loving Brother, Krishna" class="w-full px-4 py-2 border rounded-xl focus:ring-2 focus:ring-rosegold-300 outline-none">
                </div>
            </div>

            <div class="flex justify-end space-x-3 pt-2 border-t">
                <button onclick="toggleEditMode()" class="px-5 py-2.5 bg-slate-100 text-slate-600 font-semibold rounded-full hover:bg-slate-200">Cancel</button>
                <button onclick="saveCustomizations()" class="px-6 py-2.5 bg-rosegold-600 text-white font-semibold rounded-full hover:bg-rosegold-700 shadow-md">Save Changes</button>
            </div>
        </div>
    </div>

    <footer class="mt-16 bg-white/60 border-t border-rose-100 py-8 text-center text-slate-500 text-sm">
        <div class="max-w-4xl mx-auto px-4 space-y-3">
            <p class="font-serif font-medium text-slate-700">Created with ❤️ for the world's best sister.</p>
            <div class="flex justify-center items-center space-x-4 text-xs text-rosegold-600">
                <button onclick="retriggerConfetti()" class="hover:underline flex items-center space-x-1"><i class="fa-solid fa-sparkles"></i> <span>Trigger Confetti</span></button>
                <span>•</span>
                <button onclick="resetSurpriseOverlay()" class="hover:underline flex items-center space-x-1"><i class="fa-solid fa-rotate-left"></i> <span>Replay Opening Surprise</span></button>
            </div>
            <p class="text-xs text-slate-400">Happy Birthday! 🎉</p>
        </div>
    </footer>

    <script>
        /* Web Audio API Synth Generator for Melody & FX */
        let audioCtx = null;
        let isMusicPlaying = false;
        let melodyInterval = null;

        function initAudioContext() {
            if (!audioCtx) {
                audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            }
            if (audioCtx.state === 'suspended') {
                audioCtx.resume();
            }
        }

        // Play a soft pleasant synth tone
        function playNote(freq, type = 'sine', duration = 0.4, vol = 0.15) {
            try {
                initAudioContext();
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = type;
                osc.frequency.setValueAtTime(freq, audioCtx.currentTime);
                gain.gain.setValueAtTime(vol, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + duration);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start();
                osc.stop(audioCtx.currentTime + duration);
            } catch (e) { console.log(e); }
        }

        // Celebratory chime sound when gift opens or cake blow out
        function playChimeSound() {
            const notes = [523.25, 659.25, 783.99, 1046.50]; // C5, E5, G5, C6
            notes.forEach((note, idx) => {
                setTimeout(() => playNote(note, 'triangle', 0.8, 0.2), idx * 120);
            });
        }

        // Candle blow noise sound
        function playBlowSound() {
            try {
                initAudioContext();
                const bufferSize = audioCtx.sampleRate * 0.5;
                const buffer = audioCtx.createBuffer(1, bufferSize, audioCtx.sampleRate);
                const data = buffer.getChannelData(0);
                for (let i = 0; i < bufferSize; i++) {
                    data[i] = Math.random() * 2 - 1;
                }
                const noise = audioCtx.createBufferSource();
                noise.buffer = buffer;
                const filter = audioCtx.createBiquadFilter();
                filter.type = 'lowpass';
                filter.frequency.value = 400;
                
                const gain = audioCtx.createGain();
                gain.gain.setValueAtTime(0.3, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.5);

                noise.connect(filter);
                filter.connect(gain);
                gain.connect(audioCtx.destination);
                noise.start();
            } catch(e) {}
        }

        // Happy Birthday Synth Jingle Sequence
        function toggleAudio() {
            initAudioContext();
            const btnText = document.getElementById('music-text');
            const btnIcon = document.getElementById('music-icon');

            if (isMusicPlaying) {
                clearInterval(melodyInterval);
                isMusicPlaying = false;
                btnText.textContent = "Play Melody";
                btnIcon.className = "fa-solid fa-music";
            } else {
                isMusicPlaying = true;
                btnText.textContent = "Pause Melody";
                btnIcon.className = "fa-solid fa-pause text-rosegold-500 animate-pulse";

                // Simple synthesized Happy Birthday melody notes
                const happyBirthdayNotes = [
                    261.63, 261.63, 293.66, 261.63, 349.23, 329.63,
                    261.63, 261.63, 293.66, 261.63, 392.00, 349.23
                ];
                let noteIdx = 0;
                playNote(happyBirthdayNotes[0], 'sine', 0.5, 0.2);

                melodyInterval = setInterval(() => {
                    noteIdx = (noteIdx + 1) % happyBirthdayNotes.length;
                    playNote(happyBirthdayNotes[noteIdx], 'sine', 0.5, 0.15);
                }, 500);
            }
        }

        // Open Gift Box Surprise Action
        function openGiftSurprise() {
            const lid = document.getElementById('gift-lid');
            const overlay = document.getElementById('gift-overlay');
            
            // Lid pop animation
            lid.classList.add('lid-open');
            playChimeSound();

            // Fire burst of confetti
            if (window.confetti) {
                confetti({
                    particleCount: 120,
                    spread: 80,
                    origin: { y: 0.6 }
                });
                setTimeout(() => {
                    confetti({
                        particleCount: 80,
                        angle: 60,
                        spread: 55,
                        origin: { x: 0 }
                    });
                    confetti({
                        particleCount: 80,
                        angle: 120,
                        spread: 55,
                        origin: { x: 1 }
                    });
                }, 300);
            }

            // Fade out overlay after short delay
            setTimeout(() => {
                overlay.style.opacity = '0';
                setTimeout(() => {
                    overlay.style.display = 'none';
                }, 1000);
            }, 800);
        }

        // Reset Overlay
        function resetSurpriseOverlay() {
            const overlay = document.getElementById('gift-overlay');
            const lid = document.getElementById('gift-lid');
            lid.classList.remove('lid-open');
            overlay.style.display = 'flex';
            setTimeout(() => {
                overlay.style.opacity = '1';
            }, 50);
        }

        // Confetti Trigger
        function retriggerConfetti() {
            playChimeSound();
            confetti({
                particleCount: 100,
                spread: 70,
                origin: { y: 0.6 }
            });
        }

        // Extinguish Individual Candle
        function extinguishCandle(element) {
            const flame = element.querySelector('.flame');
            const smoke = element.querySelector('.smoke');
            if (!flame.classList.contains('hidden')) {
                playBlowSound();
                flame.classList.add('hidden');
                smoke.classList.remove('hidden');
                smoke.classList.add('smoke-anim');
                checkAllCandlesExtinguished();
            }
        }

        // Blow out all candles
        function blowAllCandles() {
            playBlowSound();
            const candles = document.querySelectorAll('.candle-wrapper');
            candles.forEach((c, idx) => {
                setTimeout(() => {
                    const flame = c.querySelector('.flame');
                    const smoke = c.querySelector('.smoke');
                    if (flame) flame.classList.add('hidden');
                    if (smoke) {
                        smoke.classList.remove('hidden');
                        smoke.classList.add('smoke-anim');
                    }
                }, idx * 150);
            });

            setTimeout(checkAllCandlesExtinguished, 600);
        }

        // Relight Candles
        function reLightCandles() {
            playNote(600, 'sine', 0.2);
            const candles = document.querySelectorAll('.candle-wrapper');
            candles.forEach(c => {
                const flame = c.querySelector('.flame');
                const smoke = c.querySelector('.smoke');
                if (flame) flame.classList.remove('hidden');
                if (smoke) {
                    smoke.classList.add('hidden');
                    smoke.classList.remove('smoke-anim');
                }
            });
            document.getElementById('wish-modal').classList.add('hidden');
        }

        // Check if all candles extinguished -> show wish
        function checkAllCandlesExtinguished() {
            const visibleFlames = document.querySelectorAll('.flame:not(.hidden)');
            if (visibleFlames.length === 0) {
                playChimeSound();
                retriggerConfetti();
                document.getElementById('wish-modal').classList.remove('hidden');
            }
        }

        // Flip 3D Cards
        function flipCard(cardWrapper) {
            playNote(400, 'sine', 0.15, 0.08);
            const inner = cardWrapper.querySelector('.card-inner');
            inner.classList.toggle('rotate-y-180');
        }

        // Live Upload Image Preview for Polaroids
        function previewImage(event, targetImgId) {
            const input = event.target;
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById(targetImgId).src = e.target.result;
                    playChimeSound();
                }
                reader.readAsDataURL(input.files[0]);
            }
        }

        // Release Wish Balloon Function
        function releaseWishBalloon() {
            const input = document.getElementById('balloon-wish-input');
            const wishText = input.value.trim();
            const skyContainer = document.getElementById('sky-container');
            const prompt = document.getElementById('sky-prompt');

            if (!wishText) return;

            if (prompt) prompt.style.display = 'none';

            playNote(880, 'sine', 0.4, 0.2);

            // Create floating balloon element inside sky container
            const balloon = document.createElement('div');
            balloon.className = 'absolute bottom-0 text-xs px-3 py-1.5 rounded-full bg-gradient-to-r from-pink-500 to-rosegold-500 text-white shadow-lg flex items-center space-x-1.5 transition-all duration-[6000ms] linear pointer-events-none opacity-90';
            balloon.style.left = Math.floor(Math.random() * 65 + 10) + '%';
            balloon.style.transform = 'translateY(100%)';

            balloon.innerHTML = `<i class="fa-solid fa-balloon text-amber-300"></i><span>${wishText}</span>`;
            skyContainer.appendChild(balloon);

            // Trigger animation upwards
            requestAnimationFrame(() => {
                setTimeout(() => {
                    balloon.style.transform = 'translateY(-180px)';
                    balloon.style.opacity = '0.2';
                }, 50);
            });

            // Remove after float finishes
            setTimeout(() => {
                balloon.remove();
            }, 6200);

            input.value = '';
        }

        // Edit Mode Customization Controls
        function toggleEditMode() {
            const modal = document.getElementById('edit-modal');
            modal.classList.toggle('hidden');
        }

        function saveCustomizations() {
            const newSisterName = document.getElementById('edit-sister-name').value;
            const newTagline = document.getElementById('edit-tagline').value;
            const newSender = document.getElementById('edit-sender-name').value;

            if (newSisterName) document.getElementById('sister-name-display').textContent = newSisterName;
            if (newTagline) document.getElementById('hero-tagline-display').textContent = newTagline;
            if (newSender) document.getElementById('sender-name-display').textContent = newSender;

            toggleEditMode();
            retriggerConfetti();
        }
    </script>
</body>
</html>
