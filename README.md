<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Adharv's Wild One Birthday</title>
    
    <!-- Fonts: Playfair Display (Elegant), Quicksand (Clean), Dancing Script (Handwritten) -->
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Playfair+Display:wght@700&family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
    
    <!-- Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <!-- Tailwind CSS for Layout (CDN) -->
    <script src="https://cdn.tailwindcss.com"></script>

    <style>
        /* --- Custom Theme Configuration --- */
        :root {
            --bg-cream: #F9F7F2;
            --leaf-green: #6B8E23;
            --sage-green: #8FBC8F;
            --gold: #D4AF37;
            --text-dark: #4A4A4A;
            --soft-brown: #8D6E63;
        }

        body {
            background-color: var(--bg-cream);
            font-family: 'Quicksand', sans-serif;
            color: var(--text-dark);
            overflow-x: hidden;
            margin: 0;
            padding: 0;
            /* Subtle paper texture */
            background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23dcdcdc' fill-opacity='0.2'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' /%3E%3C/g%3E%3C/svg%3E");
        }

        /* --- Animations --- */
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-15px) rotate(2deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }

        @keyframes sway {
            0% { transform: rotate(-5deg); }
            50% { transform: rotate(5deg); }
            100% { transform: rotate(-5deg); }
        }

        @keyframes fall {
            0% { top: -10%; transform: translateX(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            100% { top: 110%; transform: translateX(20px) rotate(360deg); opacity: 0; }
        }

        @keyframes pulse-soft {
            0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(212, 175, 55, 0.4); }
            70% { transform: scale(1.02); box-shadow: 0 0 0 10px rgba(212, 175, 55, 0); }
            100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(212, 175, 55, 0); }
        }

        .animate-float { animation: float 6s ease-in-out infinite; }
        .animate-sway { animation: sway 4s ease-in-out infinite; }
        .animate-pulse-soft { animation: pulse-soft 3s infinite; }

        /* --- Leaf/Confetti Container --- */
        #leaves-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .leaf {
            position: absolute;
            width: 30px;
            height: 30px;
            background-size: contain;
            background-repeat: no-repeat;
            opacity: 0.6;
        }

        /* --- Typography Classes --- */
        .font-wild { font-family: 'Playfair Display', serif; }
        .font-script { font-family: 'Dancing Script', cursive; }
        .text-gold { color: var(--gold); }
        .text-sage { color: var(--leaf-green); }

        /* --- Components --- */
        .page-section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 2rem;
            position: relative;
            z-index: 10;
            transition: opacity 1s ease-in-out;
            border-bottom: 2px dashed rgba(143, 188, 143, 0.3);
        }

        .photo-frame {
            width: 250px;
            height: 250px;
            border-radius: 50%;
            border: 5px solid #fff;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
            z-index: 20;
            background-color: #eee;
        }

        .animal-decoration {
            position: absolute;
            width: 80px;
            height: auto;
            z-index: 25;
            filter: drop-shadow(0 4px 6px rgba(0,0,0,0.1));
        }

        /* Glassmorphism Card for Details */
        .glass-card {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 2rem;
            border: 1px solid rgba(255, 255, 255, 0.9);
            width: 100%;
            max-width: 500px;
            text-align: center;
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.1);
        }

        /* Music Button */
        .music-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--gold);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 100;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            transition: transform 0.3s;
        }
        .music-btn:hover { transform: scale(1.1); }

        /* Opening Overlay */
        #open-envelope {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #F9F7F2;
            z-index: 1000;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            transition: transform 1s ease-in-out;
        }
        
        /* Map Button */
        .btn-gold {
            background: linear-gradient(45deg, #D4AF37, #C5A059);
            color: white;
            padding: 10px 25px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            display: inline-block;
            margin-top: 15px;
            box-shadow: 0 4px 15px rgba(212, 175, 55, 0.3);
        }

    </style>
</head>
<body>

    <!-- Audio Element (Hidden) -->
    <audio id="bg-music" loop>
        <!-- Using a royalty free gentle music placeholder -->
        <source src="https://cdn.pixabay.com/download/audio/2022/10/25/audio_226759a22d.mp3?filename=soft-piano-125345.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>

    <!-- Floating Leaves Background -->
    <div id="leaves-container"></div>

    <!-- Music Control -->
    <div class="music-btn" onclick="toggleMusic()">
        <i class="fas fa-music" id="music-icon"></i>
    </div>

    <!-- Opening Screen -->
    <div id="open-envelope">
        <div class="glass-card animate-pulse-soft" style="cursor: pointer;" onclick="startExperience()">
            <h1 class="font-wild text-3xl mb-2 text-gold">Wild ONE</h1>
            <p class="mb-4">You have a special invitation...</p>
            <div id="guest-name-display-landing" class="font-script text-2xl text-sage mb-4"></div>
            <button class="bg-green-700 text-white px-6 py-2 rounded-full shadow-lg">Tap to Open</button>
        </div>
    </div>

    <!-- PAGE 1: Intro & Baby -->
    <section class="page-section" id="section-1">
        
        <!-- Dynamic Guest Greeting -->
        <div id="dynamic-guest" class="absolute top-10 left-0 w-full text-center opacity-0 transition-opacity duration-1000">
            <span class="bg-white/80 px-4 py-2 rounded-full text-sm font-bold text-gray-600 shadow-sm">
                Specially for <span id="guest-name" class="text-green-700">Guest</span>
            </span>
        </div>

        <!-- Heading -->
        <div class="text-center mb-8 relative">
            <h1 class="font-wild text-6xl text-gold drop-shadow-sm tracking-wide">Wild</h1>
            <h1 class="font-wild text-8xl text-green-800 -mt-4 animate-pulse-soft">ONE</h1>
            
            <!-- Decorative Leaves -->
            <i class="fas fa-leaf text-green-400 text-3xl absolute -top-4 -left-8 animate-sway"></i>
            <i class="fas fa-leaf text-green-600 text-4xl absolute bottom-0 -right-12 animate-sway" style="animation-delay: 1s;"></i>
        </div>

        <!-- Photo Section -->
        <div class="relative w-full flex justify-center items-center mb-8">
            <!-- Animals around frame -->
            <img src="https://cdn-icons-png.flaticon.com/512/3069/3069172.png" class="animal-decoration" style="top: -20px; left: 50%; transform: translateX(-160px) rotate(-10deg);" alt="Giraffe">
            <img src="https://cdn-icons-png.flaticon.com/512/3069/3069186.png" class="animal-decoration animate-float" style="bottom: -10px; right: 50%; transform: translateX(170px);" alt="Lion">
            
            <!-- Balloon -->
            <div class="absolute top-0 right-10 animate-float" style="animation-delay: 2s; z-index: 5;">
                <i class="fas fa-balloon text-yellow-400 text-5xl opacity-80"></i>
            </div>

            <!-- Baby Photo Frame -->
            <div class="photo-frame animate-float">
                <!-- Placeholder for Baby Photo - Replace src with actual baby photo -->
              <img src="asset/img/WhatsApp%20Image%202026-02-13%20at%2007.35.16.jpeg" class="w-full h-full object-cover" alt="Adharv">

            </div>
        </div>

        <div class="glass-card mt-4">
            <p class="text-gray-500 uppercase tracking-widest text-xs mb-2">Please join us to celebrate the First Birthday of</p>
            <h2 class="font-wild text-3xl text-gray-800 mt-2">👶 ADHARV RAJ SHARMA</h2>
        </div>
        
        <div class="absolute bottom-10 animate-bounce text-gray-400">
            <p class="text-xs">Scroll Down</p>
            <i class="fas fa-chevron-down"></i>
        </div>
    </section>

    <!-- PAGE 2: Family Details -->
    <section class="page-section" id="section-2">
        <div class="glass-card relative">
            <!-- Religious Header -->
            <div class="mb-6 border-b pb-4 border-gray-200">
                <p class="font-script text-2xl text-orange-600">Jai Shri Krishna</p>
                <p class="font-script text-xl text-orange-500">Om Har Shree Nath Ji</p>
            </div>

            <p class="text-xs uppercase tracking-widest text-gray-500 mb-2">
    You are cordially invited
</p>

            <h2 class="font-wild text-2xl text-green-800 mb-6">👨‍👩‍👦 The Family</h2>

            <div class="space-y-6">
                <!-- Parents -->
                <div class="family-group">
                    <p class="text-xs text-gray-400 uppercase tracking-widest">Mom & Dad</p>
                    <p class="font-bold text-gray-700">Mrs. Vijay Lakshmi Sharma</p>
                    <span class="text-gold text-sm">&</span>
                    <p class="font-bold text-gray-700">Mr. Deepak Raj Sharma</p>
                </div>

                <!-- Grandparents -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-4">
                    <div class="bg-white/50 p-3 rounded-lg">
                        <p class="text-xs text-gray-400 uppercase">Dada & Dadi</p>
                        <p class="text-sm font-semibold text-gray-600">Late Smt. Usha Sharma</p>
                        <p class="text-xs text-gray-400">&</p>
                        <p class="text-sm font-semibold text-gray-600">Late Shri Yograj Sharma</p>
                    </div>
                    <div class="bg-white/50 p-3 rounded-lg">
                        <p class="text-xs text-gray-400 uppercase">Nana & Nani</p>
                        <p class="text-sm font-semibold text-gray-600">Late Smt. Vidhyawati Sharma</p>
                        <p class="text-xs text-gray-400">&</p>
                        <p class="text-sm font-semibold text-gray-600">Late Shri Bhisham Pitamah Sharma</p>
                    </div>
                </div>
            </div>

            <img src="https://cdn-icons-png.flaticon.com/512/3069/3069177.png" class="animal-decoration" style="bottom: -30px; left: -20px; width: 60px;" alt="Elephant">
        </div>
    </section>

    <!-- PAGE 3: Event Details -->
    <section class="page-section" id="section-3">
        <div class="glass-card text-center">
            <h2 class="font-wild text-3xl text-gold mb-6">Celebration Details</h2>

            <div class="space-y-6 text-gray-700">
                <!-- Date -->
                <div class="flex items-center justify-center space-x-3">
                    <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center text-green-700">
                        <i class="far fa-calendar-alt"></i>
                    </div>
                    <div class="text-left">
                        <p class="text-xs text-gray-400 uppercase">Date</p>
                        <p class="font-bold text-lg">1 MARCH 2026</p>
                    </div>
                </div>

                <!-- Time -->
                <div class="flex items-center justify-center space-x-3">
                    <div class="w-10 h-10 bg-blue-100 rounded-full flex items-center justify-center text-blue-700">
                        <i class="far fa-clock"></i>
                    </div>
                    <div class="text-left">
                        <p class="text-xs text-gray-400 uppercase">Time</p>
                        <p class="font-bold text-lg">7:00 PM Onwards</p>
                    </div>
                </div>

                <!-- Venue -->
                <div class="flex items-center justify-center space-x-3">
                    <div class="w-10 h-10 bg-red-100 rounded-full flex items-center justify-center text-red-700">
                        <i class="fas fa-map-marker-alt"></i>
                    </div>
                    <div class="text-left">
                        <p class="text-xs text-gray-400 uppercase">Venue</p>
                        <p class="font-bold">Hotel Sharma Parivar</p>
                        <p class="text-sm text-gray-500">Ganga Vihar Colony, Near Shantikunj</p>
                    </div>
                </div>

                <!-- Map Button -->
               <a href="https://share.google/cUWY10pmL3edFprKZ" target="_blank" class="btn-gold animate-pulse-soft">
    📍 Open Location
</a>

                    <i class="fas fa-location-arrow mr-2"></i> View On Map
                </a>
            </div>

            <!-- Footer -->
            <div class="mt-8 pt-4 border-t border-gray-200">
                <p class="font-script text-xl text-green-800">Can't wait to see you there!</p>
            </div>
        </div>
    </section>

    <script>
        /* --- 1. Dynamic Guest Name Logic --- */
        document.addEventListener('DOMContentLoaded', () => {
            const urlParams = new URLSearchParams(window.location.search);
            // Looks for ?guest=Name OR ?Guest=Name
            const guest = urlParams.get('guest') || urlParams.get('Guest');
            
            const guestElement = document.getElementById('guest-name');
            const dynamicContainer = document.getElementById('dynamic-guest');
            const landingName = document.getElementById('guest-name-display-landing');

            if (guest) {
                // Remove hyphens or underscores if used in URL (e.g., Rahul-Ji)
                const cleanName = guest.replace(/[-_]/g, ' ');
                
                guestElement.textContent = cleanName;
                landingName.textContent = `Specially for ${cleanName}`;
                
                // Show the container
                dynamicContainer.classList.remove('opacity-0');
            } else {
                // If no name, hide the special banner
                dynamicContainer.style.display = 'none';
                landingName.style.display = 'none';
            }
        });

        /* --- 2. Music & Opening Logic --- */
        let isMusicPlaying = false;
        const audio = document.getElementById('bg-music');
        const musicIcon = document.getElementById('music-icon');
        const envelope = document.getElementById('open-envelope');

        function startExperience() {
            // Slide up the overlay
            envelope.style.transform = 'translateY(-100%)';
            
            // Start music (browsers allow this because it's triggered by a user click)
            toggleMusic();
        }

        function toggleMusic() {
            if (isMusicPlaying) {
                audio.pause();
                musicIcon.classList.remove('fa-pause');
                musicIcon.classList.add('fa-music');
            } else {
                audio.play().catch(e => console.log("Audio play failed interaction required"));
                musicIcon.classList.remove('fa-music');
                musicIcon.classList.add('fa-pause');
            }
            isMusicPlaying = !isMusicPlaying;
        }

        /* --- 3. Falling Leaves/Confetti Animation --- */
        function createLeaf() {
            const container = document.getElementById('leaves-container');
            const leaf = document.createElement('div');
            leaf.classList.add('leaf');
            
            // Randomize leaf properties
            const left = Math.random() * 100;
            const animDuration = Math.random() * 5 + 5; // 5 to 10 seconds
            const delay = Math.random() * 5;
            
            // Simple SVG shapes for leaves
            const leafShapes = [
                `url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%238FBC8F'%3E%3Cpath d='M17,8C8,10,5.9,16.17,3.82,21.34L5.71,22l1-2.3A4.49,4.49,0,0,0,8,20C19,20,22,3,22,3,21,5,14,5.25,9,6.25S2,11.5,2,13.5a6.23,6.23,0,0,0,1.75,4.91l.12.13L4,19c1-5,4-11.5,13-11Z'/%3E%3C/svg%3E")`, // Leaf 1
                `url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%236B8E23'%3E%3Cpath d='M12,22c4.97,0,9-4.03,9-9c0-4.97-9-13-9-13S3,8.03,3,13C3,17.97,7.03,22,12,22z'/%3E%3C/svg%3E")` // Leaf 2
            ];
            
            const randomShape = leafShapes[Math.floor(Math.random() * leafShapes.length)];

            leaf.style.left = left + '%';
            leaf.style.backgroundImage = randomShape;
            leaf.style.animation = `fall ${animDuration}s linear ${delay}s infinite`;
            
            container.appendChild(leaf);
        }

        // Create 20 falling leaves
        for (let i = 0; i < 15; i++) {
            createLeaf();
        }

        /* --- 4. Intersection Observer for Smooth Fade-ins on Scroll --- */
        const observerOptions = {
            threshold: 0.2
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.remove('opacity-0', 'translate-y-10');
                    entry.target.classList.add('opacity-100', 'translate-y-0');
                }
            });
        }, observerOptions);

        // Apply fade-in class logic
        document.querySelectorAll('.glass-card, .photo-frame').forEach(el => {
            el.classList.add('transition-all', 'duration-1000', 'opacity-0', 'translate-y-10');
            observer.observe(el);
        });

    </script>
</body>
</html># index.html
