<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Numerical Simulations in Computational Chemistry | CS1102 Project</title>
    <style>
        /* CSS - Clean modern style inspired by typical CS1102 GitHub Pages projects */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Space+Grotesk:wght@500;600&display=swap');
        
        :root {
            --primary: #00d4ff;
            --dark: #0a0a2a;
            --accent: #7b2cbf;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(180deg, #0a0a2a 0%, #1a0f2e 100%);
            color: #e0f0ff;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        header {
            background: rgba(10, 10, 42, 0.95);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 2px solid var(--primary);
        }
        
        nav {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.6rem;
            font-weight: 600;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .logo::before {
            content: "🧪";
            font-size: 1.8rem;
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }
        
        .nav-links a {
            color: #e0f0ff;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .nav-links a:hover {
            color: var(--primary);
            transform: translateY(-2px);
        }
        
        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -4px;
            left: 0;
            background: var(--primary);
            transition: width 0.3s;
        }
        
        .nav-links a:hover::after {
            width: 100%;
        }
        
        .hero {
            max-width: 1200px;
            margin: 0 auto;
            padding: 5rem 2rem 3rem;
            text-align: center;
            position: relative;
        }
        
        .hero h1 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 3.5rem;
            margin-bottom: 1rem;
            background: linear-gradient(90deg, #00d4ff, #c77dff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .hero .course-title {
            font-size: 1.3rem;
            color: var(--primary);
            margin-bottom: 0.5rem;
            letter-spacing: 2px;
        }
        
        .hero .student-info {
            background: rgba(123, 44, 191, 0.15);
            border: 1px solid var(--accent);
            border-radius: 50px;
            display: inline-block;
            padding: 0.8rem 2rem;
            margin: 2rem 0;
            font-size: 1.1rem;
        }
        
        .section {
            max-width: 1200px;
            margin: 4rem auto;
            padding: 0 2rem;
        }
        
        .section h2 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
            color: var(--primary);
            position: relative;
        }
        
        .section h2::after {
            content: '';
            position: absolute;
            width: 60px;
            height: 4px;
            background: var(--accent);
            bottom: -8px;
            left: 0;
            border-radius: 4px;
        }
        
        .content-box {
            background: rgba(255,255,255,0.05);
            border-radius: 20px;
            padding: 2.5rem;
            margin-bottom: 2rem;
            border: 1px solid rgba(0, 212, 255, 0.2);
            transition: transform 0.3s ease;
        }
        
        .content-box:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.15);
        }
        
        .interactive-demo {
            background: rgba(10, 10, 42, 0.8);
            border-radius: 20px;
            padding: 2rem;
            margin: 2rem 0;
            text-align: center;
            border: 2px dashed var(--primary);
        }
        
        canvas {
            border-radius: 15px;
            background: #000;
            box-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
        }
        
        button {
            background: linear-gradient(90deg, var(--primary), var(--accent));
            color: #0a0a2a;
            border: none;
            padding: 14px 32px;
            font-size: 1.1rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            margin: 1rem 0.5rem;
            transition: all 0.3s ease;
        }
        
        button:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(123, 44, 191, 0.4);
        }
        
        .tech-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 1rem;
        }
        
        .tech-item {
            background: rgba(123, 44, 191, 0.1);
            border: 1px solid var(--accent);
            border-radius: 12px;
            padding: 1rem;
            text-align: center;
            font-weight: 500;
        }
        
        footer {
            background: #05051a;
            text-align: center;
            padding: 3rem 2rem;
            margin-top: 4rem;
            border-top: 3px solid var(--primary);
        }
        
        .footer-text {
            color: #8899bb;
            font-size: 0.95rem;
        }
        
        @media (max-width: 768px) {
            .hero h1 { font-size: 2.8rem; }
            .nav-links { gap: 1rem; font-size: 0.95rem; }
        }
        
        /* Particle animation glow effect */
        .glow {
            animation: glowPulse 2s infinite alternate;
        }
    </style>
</head>
<body>
    <!-- NAVBAR - copied style from typical clean CS1102 GitHub projects -->
    <header>
        <nav>
            <a href="index.html" class="logo">NumericalSim</a>
            
            <ul class="nav-links">
                <li><a href="#simulation">What is Numerical Simulation?</a></li>
                <li><a href="#techniques">MD & Monte Carlo</a></li>
                <li><a href="md.html">Molecular Dynamics</a></li>
                <li><a href="montecarlo.html">Monte Carlo</a></li>
                <li><a href="applications.html">Applications</a></li>
                <li><a href="discovery.html">Our Discovery</a></li>
            </ul>
            
            <div style="font-size: 0.9rem; color: #00d4ff; font-weight: 500;">
                CS1102 - Course Project - 2025 / 2026 Semester B
            </div>
        </nav>
    </header>

    <!-- HERO SECTION -->
    <section class="hero">
        <div class="course-title glow">CS1102 - Course Project - 2025 / 2026 Semester B</div>
        <h1>Numerical Simulations in Computational Chemistry</h1>
        
        <div class="student-info">
            <strong>Group Member:</strong> Lee Tsz Hin (Student ID: 58752636)
        </div>
        
        <p style="max-width: 700px; margin: 2rem auto; font-size: 1.3rem; opacity: 0.9;">
            Exploring how computers can predict the invisible dance of molecules
        </p>
        
        <!-- Unordered list of techniques demonstrated -->
        <h3 style="margin: 3rem 0 1rem; color: #c77dff;">Techniques Demonstrated in This Website</h3>
        <div class="tech-list">
            <div class="tech-item">✅ HTML5 Semantic Structure</div>
            <div class="tech-item">✅ Modern CSS3 (Flexbox, Grid, Gradients, Animations)</div>
            <div class="tech-item">✅ JavaScript Interactivity</div>
            <div class="tech-item">✅ HTML5 Canvas Animation (Live Simulation)</div>
            <div class="tech-item">✅ Responsive Design for All Devices</div>
            <div class="tech-item">✅ Sticky Navigation & Smooth Scrolling</div>
            <div class="tech-item">✅ Hover Effects & Micro-interactions</div>
            <div class="tech-item">✅ Pure CSS Glow Animations</div>
        </div>
        
        <button onclick="window.location.href='#simulation'" style="margin-top: 2rem;">
            Start Exploring the Simulations →
        </button>
    </section>

    <!-- MAIN CONTENT - Using the exact text you provided -->
    <section id="simulation" class="section">
        <h2>What is Numerical Simulation?</h2>
        <div class="content-box">
            <p style="font-size: 1.25rem; margin-bottom: 1.5rem;">
                Numerical simulation involves creating virtual computer models to analyze and predict the behavior of complex physical systems, products, or processes under various conditions.
            </p>
            <p style="font-size: 1.25rem;">
                It is used to simulate, visualize, and optimize systems that are too complex, expensive, or dangerous to test in real life and reduces the need for costly physical prototyping in industries like aerospace, automotive, and manufacturing.
            </p>
            
            <!-- Interactive Demo -->
            <div class="interactive-demo">
                <h3 style="margin-bottom: 1rem; color: var(--primary);">🔬 Try a Tiny Numerical Simulation Right Now!</h3>
                <p style="margin-bottom: 1rem; font-size: 1.1rem;">Watch atoms move like in a real Molecular Dynamics simulation</p>
                <canvas id="demoCanvas" width="800" height="400"></canvas>
                <div style="margin-top: 1rem;">
                    <button onclick="startSimulation()">▶️ Run MD Simulation</button>
                    <button onclick="resetSimulation()">⟳ Reset</button>
                    <button onclick="toggleMC()">🎲 Switch to Monte Carlo Mode</button>
                </div>
                <p id="demoStatus" style="margin-top: 1rem; font-size: 0.95rem; color: #c77dff;">Currently in Molecular Dynamics mode • 42 atoms moving in real-time</p>
            </div>
        </div>
    </section>

    <section id="techniques" class="section">
        <h2>Numerical Simulation Techniques</h2>
        <div class="content-box">
            <h3 style="color: #00d4ff; margin-bottom: 1rem;">Molecular Dynamics (MD)</h3>
            <p style="font-size: 1.25rem; margin-bottom: 2rem;">
                Molecular Dynamics is about tracking how molecules move over time. Computer starts with a bunch of atoms in certain positions and apply physics rules like Newton’s laws of motion to calculates how each atom pushes or pulls on its neighbors every tiny fraction of a second.
            </p>
            
            <h3 style="color: #c77dff; margin-bottom: 1rem;">Monte Carlo Methods</h3>
            <p style="font-size: 1.25rem;">
                Monte Carlo methods meanwhile work differently, it don’t care about time at all. Instead, it use random sampling to explore the possible shapes or configurations a molecule can take, then average the properties we care about like energy. The simulation naturally spends more time in low-energy states and after enough steps we get thermodynamic averages without ever simulating the actual motion.
            </p>
        </div>
        
        <p style="text-align: center; font-size: 1.1rem; margin-top: 2rem; opacity: 0.85;">
            Continue reading about real-world uses in <a href="applications.html" style="color: var(--primary);">Drug Discovery & Materials Science</a>
        </p>
    </section>

    <!-- FOOTER -->
    <footer>
        <div class="footer-text">
            CS1102 - Course Project - 2025 / 2026 Semester B<br>
            Created by Lee Tsz Hin (58752636)<br>
            Project Topic: Numerical Simulations in Computational Chemistry<br><br>
            This website is fully open-sourced on GitHub Pages • All code written manually in VS Code
        </div>
    </footer>

    <script>
        // JavaScript for interactivity - Live Canvas Simulation (MD + MC toggle)
        let canvas = document.getElementById('demoCanvas');
        let ctx = canvas.getContext('2d');
        let particles = [];
        let isMC = false;
        let animationFrame;
        
        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.vx = (Math.random() - 0.5) * 3;
                this.vy = (Math.random() - 0.5) * 3;
                this.radius = 8;
                this.color = isMC ? '#c77dff' : '#00d4ff';
            }
            update() {
                if (!isMC) {
                    // MD mode: follow Newton's laws (simple physics)
                    this.x += this.vx;
                    this.y += this.vy;
                    
                    // Bounce off walls
                    if (this.x < 0 || this.x > canvas.width) this.vx *= -1;
                    if (this.y < 0 || this.y > canvas.height) this.vy *= -1;
                } else {
                    // MC mode: random jumps (no time, just sampling)
                    this.x += (Math.random() - 0.5) * 25;
                    this.y += (Math.random() - 0.5) * 25;
                    if (this.x < 0) this.x = canvas.width;
                    if (this.x > canvas.width) this.x = 0;
                    if (this.y < 0) this.y = canvas.height;
                    if (this.y > canvas.height) this.y = 0;
                }
            }
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 20;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.shadowBlur = 0;
            }
        }
        
        function initParticles(count) {
            particles = [];
            for (let i = 0; i < count; i++) {
                particles.push(new Particle());
            }
        }
        
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // Background grid for chemistry feel
            ctx.strokeStyle = 'rgba(0, 212, 255, 0.1)';
            for (let x = 0; x < canvas.width; x += 40) {
                ctx.beginPath();
                ctx.moveTo(x, 0);
                ctx.lineTo(x, canvas.height);
                ctx.stroke();
            }
            for (let y = 0; y < canvas.height; y += 40) {
                ctx.beginPath();
                ctx.moveTo(0, y);
                ctx.lineTo(canvas.width, y);
                ctx.stroke();
            }
            
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            
            // Draw connecting lines (MD bonds)
            if (!isMC) {
                ctx.strokeStyle = 'rgba(123, 44, 191, 0.3)';
                for (let i = 0; i < particles.length; i++) {
                    for (let j = i + 1; j < particles.length; j++) {
                        let dx = particles[i].x - particles[j].x;
                        let dy = particles[i].y - particles[j].y;
                        if (Math.sqrt(dx*dx + dy*dy) < 120) {
                            ctx.beginPath();
                            ctx.moveTo(particles[i].x, particles[i].y);
                            ctx.lineTo(particles[j].x, particles[j].y);
                            ctx.stroke();
                        }
                    }
                }
            }
            
            animationFrame = requestAnimationFrame(animate);
        }
        
        function startSimulation() {
            if (animationFrame) cancelAnimationFrame(animationFrame);
            initParticles(42);
            animate();
            document.getElementById('demoStatus').textContent = isMC ? 
                '🎲 Monte Carlo Mode • Random sampling active' : 
                '🧪 Molecular Dynamics Mode • Real-time motion';
        }
        
        function resetSimulation() {
            if (animationFrame) cancelAnimationFrame(animationFrame);
            initParticles(42);
            animate();
        }
        
        function toggleMC() {
            isMC = !isMC;
            particles.forEach(p => p.color = isMC ? '#c77dff' : '#00d4ff');
            document.getElementById('demoStatus').textContent = isMC ? 
                '🎲 Monte Carlo Mode • Random sampling active' : 
                '🧪 Molecular Dynamics Mode • Real-time motion';
        }
        
        // Auto-start demo when page loads
        window.onload = function() {
            initParticles(42);
            animate();
            
            // Smooth scrolling for nav links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    if (this.getAttribute('href') !== '#') {
                        e.preventDefault();
                        document.querySelector(this.getAttribute('href')).scrollIntoView({
                            behavior: 'smooth'
                        });
                    }
                });
            });
            
            console.log('%c✅ Website loaded successfully! All techniques demonstrated.', 'color:#00d4ff; font-size:14px');
        };
    </script>
</body>
</html>
