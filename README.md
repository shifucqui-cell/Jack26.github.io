<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Numerical Simulations in Computational Chemistry | CS1102 Project</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Poppins:wght@500;600&display=swap');
        
        :root {
            --bg: #f8f9ff;
            --text: #1a2639;
            --primary: #4a6cf7;
            --accent: #7b68ee;
            --light-accent: #e0e7ff;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg);
            color: var(--text);
            line-height: 1.7;
            font-size: 1.05rem;
        }
        
        header {
            background: white;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        nav {
            max-width: 1100px;
            margin: 0 auto;
            padding: 1.2rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-family: 'Poppins', sans-serif;
            font-size: 1.65rem;
            font-weight: 600;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }
        
        .nav-links a {
            color: var(--text);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: var(--primary);
        }
        
        .course-info {
            font-size: 0.95rem;
            color: #555;
            font-weight: 500;
        }
        
        .hero {
            max-width: 1100px;
            margin: 0 auto;
            padding: 5rem 2rem 4rem;
            text-align: center;
            background: linear-gradient(135deg, #f0f4ff 0%, #f8f9ff 100%);
        }
        
        .hero h1 {
            font-family: 'Poppins', sans-serif;
            font-size: 2.8rem;
            margin-bottom: 1rem;
            color: #1a2639;
        }
        
        .hero .course-title {
            color: var(--primary);
            font-size: 1.25rem;
            margin-bottom: 0.5rem;
            letter-spacing: 1px;
        }
        
        .student-info {
            background: var(--light-accent);
            border: 1px solid var(--primary);
            border-radius: 50px;
            display: inline-block;
            padding: 12px 28px;
            margin: 2rem 0;
            font-size: 1.1rem;
        }
        
        .main-content {
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .section {
            margin-bottom: 4rem;
        }
        
        .section h2 {
            font-family: 'Poppins', sans-serif;
            font-size: 2.1rem;
            margin-bottom: 1.5rem;
            color: var(--primary);
            border-bottom: 3px solid var(--light-accent);
            padding-bottom: 10px;
        }
        
        .content-box {
            background: white;
            border-radius: 16px;
            padding: 2.5rem;
            box-shadow: 0 8px 25px rgba(74, 108, 247, 0.08);
            margin-bottom: 2.5rem;
            border: 1px solid #e0e7ff;
        }
        
        .content-box p {
            font-size: 1.15rem;
            margin-bottom: 1.4rem;
            color: #333;
        }
        
        .tech-list {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-top: 2rem;
        }
        
        .tech-item {
            background: var(--light-accent);
            color: var(--primary);
            padding: 10px 20px;
            border-radius: 30px;
            font-size: 1rem;
            font-weight: 500;
        }
        
        footer {
            background: #1a2639;
            color: #c0d0ff;
            text-align: center;
            padding: 3rem 2rem;
            margin-top: 5rem;
        }
        
        footer a {
            color: #a0b8ff;
            text-decoration: none;
        }
        
        @media (max-width: 768px) {
            .nav-links {
                gap: 1.5rem;
                font-size: 1rem;
            }
            .hero h1 {
                font-size: 2.3rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <nav>
            <a href="index.html" class="logo">🧪 NumericalSim</a>
            
            <ul class="nav-links">
                <li><a href="index.html">Home</a></li>
                <li><a href="howtheyareused.html">How they are used</a></li>
            </ul>
            
            <div class="course-info">
                CS1102 - Course Project - 2025 / 2026 Semester B
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="course-title">CS1102 - Course Project - 2025 / 2026 Semester B</div>
        <h1>Numerical Simulations in Computational Chemistry</h1>
        
        <div class="student-info">
            <strong>Lee Tsz Hin</strong> (Student ID: 58752636)
        </div>
        
        <p style="max-width: 700px; margin: 2rem auto; font-size: 1.25rem;">
            Understanding how computers help scientists study molecules without doing real experiments
        </p>
    </section>

    <!-- Main Content -->
    <div class="main-content">

        <!-- What is Numerical Simulation -->
        <div class="section">
            <h2>What is Numerical Simulation?</h2>
            <div class="content-box">
                <p>
                    Numerical simulation involves creating virtual computer models to analyze and predict the behavior of complex physical systems, products, or processes under various conditions.
                </p>
                <p>
                    It is used to simulate, visualize, and optimize systems that are too complex, expensive, or dangerous to test in real life and reduces the need for costly physical prototyping in industries like aerospace, automotive, and manufacturing.
                </p>
            </div>
        </div>

        <!-- Numerical Simulation Techniques -->
        <div class="section">
            <h2>Numerical Simulation Techniques</h2>
            <div class="content-box">
                <h3 style="color: var(--primary); margin: 1.5rem 0 1rem;">Molecular Dynamics (MD)</h3>
                <p>
                    Molecular Dynamics is about tracking how molecules move over time. Computer starts with a bunch of atoms in certain positions and apply physics rules like Newton’s laws of motion to calculates how each atom pushes or pulls on its neighbors every tiny fraction of a second.
                </p>
                
                <h3 style="color: var(--accent); margin: 2rem 0 1rem;">Monte Carlo Methods</h3>
                <p>
                    Monte Carlo methods meanwhile work differently, it don’t care about time at all. Instead, it use random sampling to explore the possible shapes or configurations a molecule can take, then average the properties we care about like energy. The simulation naturally spends more time in low-energy states and after enough steps we get thermodynamic averages without ever simulating the actual motion.
                </p>
            </div>
        </div>

        <!-- Techniques Demonstrated -->
        <div class="section">
            <h2>Techniques Demonstrated</h2>
            <div class="tech-list">
                <div class="tech-item">HTML5</div>
                <div class="tech-item">CSS3 (Flexbox & Modern Styling)</div>
                <div class="tech-item">Responsive Design</div>
                <div class="tech-item">Clean Navigation</div>
                <div class="tech-item">Semantic Structure</div>
            </div>
        </div>

    </div>

    <!-- Footer -->
    <footer>
        <p>CS1102 - Course Project - 2025 / 2026 Semester B</p>
        <p>Created by: Lee Tsz Hin (Student ID: 58752636)</p>
        <p>Project Topic: Numerical Simulations in Computational Chemistry</p>
        <p style="margin-top: 1.5rem; font-size: 0.95rem;">
            This website is made with pure HTML and CSS • All content written by the author
        </p>
    </footer>
</body>
</html>
            
            console.log('%c✅ Website loaded successfully! All techniques demonstrated.', 'color:#00d4ff; font-size:14px');
        };
    </script>
</body>
</html>
