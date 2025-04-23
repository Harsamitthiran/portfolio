<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="V S Harsamitthiran - Innovate Farming Portfolio showcasing sustainable agriculture and cutting-edge techniques.">
    <meta name="author" content="V S Harsamitthiran">
    <title>V S Harsamitthiran - Farming Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;800&family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Roboto', sans-serif;
            line-height: 1.7;
            color: #2d2d2d;
            background: #f9fafb;
            overflow-x: hidden;
        }

        /* Navigation */
        nav {
            background: linear-gradient(135deg, #1a3c34, #2e7d32);
            color: #fff;
            padding: 1.5rem 4rem;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.15);
            transition: background 0.4s ease, padding 0.3s ease;
        }

        nav.scrolled {
            background: #1a3c34;
            padding: 1rem 4rem;
        }

        .logo {
            font-family: 'Montserrat', sans-serif;
            font-size: 2.2rem;
            font-weight: 800;
            letter-spacing: 1.5px;
            text-transform: uppercase;
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 3rem;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-size: 1.1rem;
            font-weight: 400;
            position: relative;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: #a5d6a7;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background: #a5d6a7;
            left: 0;
            bottom: -8px;
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .burger {
            display: none;
            cursor: pointer;
        }

        .burger div {
            width: 30px;
            height: 4px;
            background: #fff;
            margin: 6px;
            transition: all 0.3s ease;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: url('https://images.unsplash.com/photo-1500595046743-ddf4d3d753fd?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80') no-repeat center center/cover;
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: #fff;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.6));
            z-index: 1;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            padding: 3rem;
            border-radius: 20px;
            animation: fadeInUp 1.2s ease-out;
        }

        .hero h1 {
            font-family: 'Montserrat', sans-serif;
            font-size: 4.5rem;
            font-weight: 800;
            margin-bottom: 1.5rem;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.5);
        }

        .hero h2 {
            font-size: 2.2rem;
            font-weight: 300;
            margin-bottom: 2rem;
        }

        .hero p {
            font-size: 1.4rem;
            margin-bottom: 3rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .btn {
            display: inline-block;
            padding: 1.2rem 3.5rem;
            background: #2e7d32;
            color: #fff;
            text-decoration: none;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        .btn:hover {
            background: #1a3c34;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
        }

        /* Sections */
        .section {
            padding: 7rem 4rem;
            text-align: center;
            position: relative;
            background: #fff;
        }

        .section h2 {
            font-family: 'Montserrat', sans-serif;
            font-size: 3.2rem;
            font-weight: 600;
            margin-bottom: 3rem;
            color: #1a3c34;
            position: position: relative;
        }

        .section h2::after {
            content: '';
            position: absolute;
            width: 100px;
            height: 4px;
            background: #2e7d32;
            left: 50%;
            transform: translateX(-50%);
            bottom: -15px;
        }

        .about-content {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 4rem;
            max-width: 1200px;
            margin: 0 auto;
            flex-wrap: wrap;
        }

        .about-img {
            width: 400px;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .about-img:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        .about-content p {
            font-size: 1.3rem;
            max-width: 600px;
            line-height: 1.9;
            color: #4a4a4a;
        }

        /* Philosophy Section with Parallax */
        #philosophy {
            background: url('https://images.unsplash.com/photo-1500382017468-9049fed747ef?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80') no-repeat center center/cover;
            background-attachment: fixed;
            color: #fff;
            position: relative;
            padding: 8rem 4rem;
        }

        #philosophy::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.65);
        }

        #philosophy h2,
        #philosophy p {
            position: relative;
            z-index: 1;
        }

        #philosophy p {
            max-width: 900px;
            margin: 0 auto;
            font-size: 1.3rem;
            line-height: 1.9;
        }

        .farm-content {
            display: flex;
            justify-content: center;
            gap: 3rem;
            flex-wrap: wrap;
        }

        .farm-card {
            background: #f9fafb;
            padding: 2.5rem;
            border-radius: 20px;
            width: 280px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
            cursor: pointer;
        }

        .farm-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
        }

        .farm-card h3 {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 1.2rem;
            color: #1a3c34;
        }

        .farm-card p {
            font-size: 1.1rem;
            color: #4a4a4a;
        }

        .farm-card#location-card {
            background: linear-gradient(135deg, #2e7d32, #4caf50);
            color: #fff;
        }

        .farm-card#location-card h3,
        .farm-card#location-card p {
            color: #fff;
        }

        /* Projects Section */
        #projects {
            background: #f9fafb;
        }

        .project-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .project-card {
            background: #fff;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
            text-align: left;
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
        }

        .project-video-container {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            height: 0;
            overflow: hidden;
        }

        .project-video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        .project-info {
            padding: 2rem;
        }

        .project-card h3 {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.8rem;
            color: #1a3c34;
            margin-bottom: 1rem;
        }

        .project-card p {
            font-size: 1.1rem;
            color: #4a4a4a;
            margin-bottom: 1.5rem;
        }

        .achievements ul {
            list-style: none;
            max-width: 900px;
            margin: 0 auto;
            text-align: left;
        }

        .achievements li {
            margin: 1.8rem 0;
            font-size: 1.3rem;
            position: relative;
            padding-left: 2.5rem;
            animation: slideIn 0.6s ease-out;
        }

        .achievements li::before {
            content: '\f058';
            font-family: 'Font Awesome 6 Free';
            font-weight: 900;
            position: absolute;
            left: 0;
            color: #2e7d32;
            font-size: 1.5rem;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .gallery-grid img {
            width: 100%;
            height: 300px;
            object-fit: cover;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
            transition: transform 0.4s ease, box-shadow 0.4s ease;
        }

        .gallery-grid img:hover {
            transform: scale(1.05);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        /* Contact Section with Map */
        #contact {
            background: #f9fafb;
        }

        #contact-form {
            max-width: 800px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 1.8rem;
            background: #fff;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }

        #contact-form.highlight {
            transform: scale(1.02);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
        }

        #contact-form input,
        #contact-form textarea {
            padding: 1.2rem;
            border: 1px solid #d1d5db;
            border-radius: 10px;
            font-size: 1.1rem;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
        }

        #contact-form input:focus,
        #contact-form textarea:focus {
            border-color: #2e7d32;
            box-shadow: 0 0 8px rgba(46, 125, 50, 0.3);
            outline: none;
        }

        #contact-form textarea {
            resize: vertical;
            min-height: 180px;
        }

        #contact-form button {
            align-self: center;
        }

        #map {
            height: 400px;
            width: 100%;
            max-width: 800px;
            margin: 2rem auto;
            border-radius: 20px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }

        /* Footer */
        footer {
            background: linear-gradient(135deg, #1a3c34, #2e7d32);
            color: #fff;
            text-align: center;
            padding: 2.5rem;
            font-size: 1.2rem;
        }

        footer p {
            margin: 0;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-30px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        /* Responsive Design */
        @media (max-width: 1024px) {
            .about-content {
                flex-direction: column;
                text-align: center;
            }

            .gallery-grid, .project-grid {
                grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            }
        }

        @media (max-width: 768px) {
            nav {
                padding: 1rem 2rem;
            }

            .nav-links {
                display: none;
                flex-direction: column;
                position: absolute;
                top: 80px;
                right: 0;
                background: linear-gradient(135deg, #1a3c34, #2e7d32);
                width: 100%;
                padding: 2rem 0;
                box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            }

            .nav-links.active {
                display: flex;
            }

            .nav-links li {
                margin: 1rem 0;
            }

            .burger {
                display: block;
            }

            .hero h1 {
                font-size: 3rem;
            }

            .hero h2 {
                font-size: 1.8rem;
            }

            .hero p {
                font-size: 1.2rem;
            }

            .section {
                padding: 5rem 2rem;
            }

            .about-img {
                width: 300px;
            }

            .farm-card, .project-card {
                width: 100%;
                max-width: 300px;
            }

            #contact-form {
                padding: 2rem;
            }

            #map {
                height: 300px;
            }
        }

        @media (max-width: 480px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .hero h2 {
                font-size: 1.5rem;
            }

            .section h2 {
                font-size: 2.5rem;
            }

            .btn {
                padding: 1rem 2.5rem;
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="logo">V S Harsamitthiran</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#philosophy">Philosophy</a></li>
            <li><a href="#farm">Farm</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#achievements">Achievements</a></li>
            <li><a href="#gallery">Gallery</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="burger">
            <div class="line1"></div>
            <div class="line2"></div>
            <div class="line3"></div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>V S Harsamitthiran</h1>
            <h2>Pioneering Sustainable Agriculture</h2>
            <p>Blending tradition with innovation to cultivate a greener future</p>
            <a href="#about" class="btn">Discover My Journey</a>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section">
        <h2>Meet V S Harsamitthiran</h2>
        <div class="about-content">
            <img src="https://images.unsplash.com/photo-1596281872898-f70f3c3f7d65?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="V S Harsamitthiran" class="about-img" loading="lazy">
            <p>I am V S Harsamitthiran, a visionary farmer from Tamil Nadu, India, with a passion for sustainable agriculture. With over 15 years of experience, I have transformed my farm into a model of innovation, integrating IoT-based irrigation, drone monitoring, and organic practices. My mission is to produce high-quality, eco-friendly crops while inspiring a global shift toward sustainable farming.</p>
        </div>
    </section>

    <!-- Philosophy Section -->
    <section id="philosophy" class="section">
        <h2>My Farming Philosophy</h2>
        <p>Farming is a harmonious partnership with nature. My approach emphasizes sustainability through organic fertilizers, crop rotation, and advanced technologies like AI-driven analytics and precision irrigation. By minimizing environmental impact and maximizing yields, I aim to set a benchmark for eco-conscious agriculture worldwide.</p>
    </section>

    <!-- Farm Overview Section -->
    <section id="farm" class="section">
        <h2>My Farm: A Beacon of Innovation</h2>
        <div class="farm-content">
            <div class="farm-card" id="location-card" onclick="scrollToContact()">
                <h3>Location</h3>
                <p>Tamil Nadu, India</p>
            </div>
            <div class="farm-card">
                <h3>Size</h3>
                <p>25 acres</p>
            </div>
            <div class="farm-card">
                <h3>Specialization</h3>
                <p>Organic Crops, IoT Farming</p>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section">
        <h2>My Projects</h2>
        <div class="project-grid">
            <div class="project-card">
                <div class="project-video-container">
                    <iframe class="project-video" src="https://www.youtube.com/watch?v=4zW0qLRhQ" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
                <div class="project-info">
                    <h3>IoT-Based Irrigation System</h3>
                    <p>An automated irrigation system using IoT sensors to monitor soil moisture and optimize water usage, reducing waste by 40%.</p>
                    <a href="projects.html?project=iot-irrigation" class="btn">View Project</a>
                </div>
            </div>
            <div class="project-card">
                <div class="project-video-container">
                    <iframe class="project-video" src="https://www.youtube.com/watch?v=DRONE12345" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
                <div class="project-info">
                    <h3>Drone Crop Monitoring</h3>
                    <p>Utilizing drones equipped with multispectral cameras to monitor crop health and detect issues early, improving yield efficiency.</p>
                    <a href="projects.html?project=drone-monitoring" class="btn">View Project</a>
                </div>
            </div>
            <div class="project-card">
                <div class="project-video-container">
                    <iframe class="project-video" src="https://www.youtube.com/watch?v=COMPOST2025" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
                <div class="project-info">
                    <h3>Organic Compost Unit</h3>
                    <p>A sustainable composting system that converts farm waste into high-quality organic fertilizer, promoting soil health.</p>
                    <a href="projects.html?project=compost-unit" class="btn">View Project</a>
                </div>
            </div>
            <div class="project-card">
                <div class="project-video-container">
                    <iframe class="project-video" src="https://www.youtube.com/watch?v=SMARTFARM2025" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>
                <div class="project-info">
                    <h3>Working Model: Smart Farm</h3>
                    <p>A fully functional model demonstrating IoT integration for irrigation, weather monitoring, and automated pest control.</p>
                    <a href="projects.html?project=smart-farm" class="btn">View Project</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Achievements Section -->
    <section id="achievements" class="section">
        <h2>Achievements</h2>
        <ul>
            <li>Recipient of the National Sustainable Farming Award, 2024</li>
            <li>Reduced water usage by 40% with IoT-based irrigation</li>
            <li>Certified Organic Farmer since 2018</li>
            <li>Featured in 'Global Farmer' Magazine, 2023</li>
            <li>Implemented drone technology for crop monitoring</li>
        </ul>
    </section>

    <!-- Gallery Section -->
    <section id="gallery" class="section">
        <h2>Gallery</h2>
        <div class="gallery-grid">
            <img src="https://images.unsplash.com/photo-1500076656116-558758c991c1?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Organic Crops" loading="lazy">
            <img src="https://images.unsplash.com/photo-1500932334442-8761ee4810a7?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Farm Irrigation" loading="lazy">
            <img src="https://images.unsplash.com/photo-1501430593644-2e7104ba1dea?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Harvest Season" loading="lazy">
            <img src="https://images.unsplash.com/photo-1530836265289-e1a6651eb06b?ixlib=rb-4.0.3&auto=format&fit=crop&w=400&q=80" alt="Farm Technology" loading="lazy">
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
        <h2>Contact Me</h2>
        <div id="map"></div>
        <form id="contact-form">
            <input type="text" placeholder="Name" required aria-label="Name">
            <input type="email" placeholder="Email" required aria-label="Email">
            <textarea placeholder="Message" required aria-label="Message"></textarea>
            <button type="submit" class="btn">Send Message</button>
        </form>
    </section>

    <!-- Footer -->
    <footer>
        <p>© 2025 V S Harsamitthiran. All Rights Reserved.</p>
    </footer>

    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script>
        // Navigation Toggle for Mobile
        const burger = document.querySelector('.burger');
        const navLinks = document.querySelector('.nav-links');

        burger.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            burger.classList.toggle('toggle');
        });

        // Smooth Scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
                navLinks.classList.remove('active');
                burger.classList.remove('toggle');
            });
        });

        // Sticky Navigation Effect
        window.addEventListener('scroll', () => {
            const nav = document.querySelector('nav');
            nav.classList.toggle('scrolled', window.scrollY > 50);
        });

        // Scroll to Contact Section with Highlight
        function scrollToContact() {
            const contactSection = document.querySelector('#contact');
            contactSection.scrollIntoView({ behavior: 'smooth' });
            const form = document.querySelector('#contact-form');
            form.classList.add('highlight');
            setTimeout(() => form.classList.remove('highlight'), 2000);
        }

        // Contact Form Submission
        document.getElementById('contact-form').addEventListener('submit', function (e) {
            e.preventDefault();
            const name = this.querySelector('input[type="text"]').value;
            const email = this.querySelector('input[type="email"]').value;
            const message = this.querySelector('textarea').value;

            if (name && email && message) {
                alert(`Thank you, ${name}! Your message has been sent successfully.`);
                this.reset();
            } else {
                alert('Please complete all fields.');
            }
        });

        // Lazy Load Images
        document.addEventListener('DOMContentLoaded', () => {
            const images = document.querySelectorAll('img[loading="lazy"]');
            const options = {
                root: null,
                rootMargin: '0px',
                threshold: 0.1
            };

            const observer = new IntersectionObserver((entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const img = entry.target;
                        img.src = img.dataset.src || img.src;
                        img.classList.add('loaded');
                        observer.unobserve(img);
                    }
                });
            }, options);

            images.forEach(img => {
                img.dataset.src = img.src;
                img.src = 'https://via.placeholder.com/400?text=Loading...';
                observer.observe(img);
            });
        });

        // Initialize Leaflet Map
        document.addEventListener('DOMContentLoaded', () => {
            const map = L.map('map').setView([10.8505, 78.6908], 8);
            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
            }).addTo(map);
            L.marker([10.8505, 78.6908]).addTo(map)
                .bindPopup('V S Harsamitthiran Farm<br>Tamil Nadu, India')
                .openPopup();
        });

        // Scroll-Triggered Animations
        const animateOnScroll = () => {
            const elements = document.querySelectorAll('.section, .farm-card, .project-card, .gallery-grid img, .about-content');
            elements.forEach(el => {
                const rect = el.getBoundingClientRect();
                if (rect.top <= window.innerHeight * 0.8) {
                    el.classList.add('animate');
                }
            });
        };

        window.addEventListener('scroll', animateOnScroll);
        document.addEventListener('DOMContentLoaded', animateOnScroll);

        // Add animate class for CSS
        const style = document.createElement('style');
        style.textContent = `
            .section, .farm-card, .project-card, .gallery-grid img, .about-content {
                opacity: 0;
                transform: translateY(50px);
                transition: opacity 0.6s ease, transform 0.6s ease;
            }
            .section.animate, .farm-card.animate, .project-card.animate, .gallery-grid img.animate, .about-content.animate {
                opacity: 1;
                transform: translateY(0);
            }
            img.loaded {
                animation: fadeIn 0.5s ease;
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
