<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vasant Medicare Hospital</title>
    <link rel="icon" type="image/x-icon" href="vasant_icon.ico">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        :root {
            --primary: #006666;
            --primary-dark: #003d3d;
            --secondary: #009966;
            --accent: #00b2a9;
            --light: #f0f7f5;
            --dark: #1a1a2e;
            --text: #333;
            --text-light: #666;
            --white: #ffffff;
            --shadow: 0 4px 20px rgba(0,0,0,0.1);
            --shadow-lg: 0 10px 40px rgba(0,0,0,0.15);
            --whatsapp: #25D366;
        }
        html { scroll-behavior: smooth; }
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; color: var(--text); overflow-x: hidden; }
        ::-webkit-scrollbar { width: 10px; }
        ::-webkit-scrollbar-track { background: var(--light); }
        ::-webkit-scrollbar-thumb { background: var(--primary); border-radius: 5px; }
        .loader { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: var(--white); display: flex; align-items: center; justify-content: center; z-index: 9999; transition: opacity 0.5s ease, visibility 0.5s ease; }
        .loader.hidden { opacity: 0; visibility: hidden; }
        .loader-spinner { width: 60px; height: 60px; border: 4px solid var(--light); border-top-color: var(--primary); border-radius: 50%; animation: spin 1s linear infinite; }
        @keyframes spin { to { transform: rotate(360deg); } }
        .navbar { position: fixed; top: 0; width: 100%; background: rgba(255,255,255,0.95); backdrop-filter: blur(10px); z-index: 1000; padding: 12px 0; box-shadow: var(--shadow); transition: all 0.3s ease; }
        .navbar.scrolled { padding: 8px 0; }
        .nav-container { max-width: 1200px; margin: 0 auto; padding: 0 20px; display: flex; justify-content: space-between; align-items: center; }
        .logo { display: flex; align-items: center; gap: 12px; text-decoration: none; }
        .logo-icon { width: 45px; height: 45px; background: linear-gradient(135deg, var(--primary), var(--secondary)); border-radius: 50%; display: flex; align-items: center; justify-content: center; color: var(--white); font-size: 1.3rem; font-weight: 700; position: relative; }
        .logo-icon::after { content: ''; position: absolute; width: 18px; height: 6px; background: var(--white); border-radius: 3px; top: 50%; left: 50%; transform: translate(-50%, -50%); }
        .logo-icon::before { content: ''; position: absolute; width: 6px; height: 18px; background: var(--white); border-radius: 3px; top: 50%; left: 50%; transform: translate(-50%, -50%); }
        .logo-text { display: flex; flex-direction: column; }
        .logo-text .main { font-size: 1.3rem; font-weight: 700; color: var(--primary); line-height: 1.2; }
        .logo-text .main span { color: var(--secondary); }
        .logo-text .sub { font-size: 0.75rem; color: var(--text-light); letter-spacing: 1px; }
        .nav-links { display: flex; gap: 30px; list-style: none; align-items: center; }
        .nav-links a { text-decoration: none; color: var(--text); font-weight: 500; transition: color 0.3s; position: relative; font-size: 0.95rem; }
        .nav-links a:hover { color: var(--primary); }
        .nav-links a::after { content: ''; position: absolute; bottom: -5px; left: 0; width: 0; height: 2px; background: var(--primary); transition: width 0.3s; }
        .nav-links a:hover::after { width: 100%; }
        .nav-cta { background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white) !important; padding: 10px 24px; border-radius: 50px; font-weight: 600; transition: all 0.3s ease; }
        .nav-cta:hover { transform: translateY(-2px); box-shadow: 0 4px 15px rgba(0,102,102,0.3); }
        .nav-cta::after { display: none !important; }
        .mobile-menu-btn { display: none; background: none; border: none; font-size: 1.5rem; color: var(--primary); cursor: pointer; }
        .hero { min-height: 100vh; background: linear-gradient(135deg, var(--primary-dark) 0%, var(--primary) 50%, var(--secondary) 100%); display: flex; align-items: center; justify-content: center; text-align: center; padding: 120px 20px 80px; position: relative; overflow: hidden; }
        .hero::before { content: ''; position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="50" cy="50" r="40" fill="none" stroke="rgba(255,255,255,0.05)" stroke-width="0.5"/></svg>'); background-size: 80px; animation: float 20s linear infinite; }
        @keyframes float { 0% { transform: translateY(0) rotate(0deg); } 100% { transform: translateY(-100px) rotate(360deg); } }
        .hero-content { position: relative; z-index: 1; max-width: 800px; }
        .hero-badge { display: inline-flex; align-items: center; gap: 8px; background: rgba(255,255,255,0.15); color: var(--white); padding: 10px 24px; border-radius: 50px; font-size: 0.9rem; margin-bottom: 25px; backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.2); }
        .hero h1 { font-size: 3.5rem; color: var(--white); margin-bottom: 20px; font-weight: 700; line-height: 1.2; }
        .hero h1 .spaced { letter-spacing: 0.3em; display: block; font-size: 1rem; font-weight: 300; margin-bottom: 10px; text-transform: uppercase; opacity: 0.9; }
        .hero p { font-size: 1.2rem; color: rgba(255,255,255,0.9); margin-bottom: 35px; line-height: 1.8; }
        .hero-buttons { display: flex; gap: 15px; justify-content: center; flex-wrap: wrap; }
        .btn { padding: 14px 32px; border-radius: 50px; text-decoration: none; font-weight: 600; transition: all 0.3s ease; display: inline-flex; align-items: center; gap: 8px; cursor: pointer; border: none; font-size: 1rem; }
        .btn-primary { background: var(--white); color: var(--primary); box-shadow: 0 4px 15px rgba(0,0,0,0.2); }
        .btn-primary:hover { transform: translateY(-3px); box-shadow: 0 8px 25px rgba(0,0,0,0.3); }
        .btn-whatsapp { background: var(--whatsapp); color: var(--white); box-shadow: 0 4px 15px rgba(37,211,102,0.3); }
        .btn-whatsapp:hover { transform: translateY(-3px); box-shadow: 0 8px 25px rgba(37,211,102,0.4); }
        .btn-outline { background: transparent; color: var(--white); border: 2px solid rgba(255,255,255,0.5); }
        .btn-outline:hover { background: rgba(255,255,255,0.1); border-color: var(--white); }
        .scroll-indicator { position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); animation: bounce 2s infinite; }
        .scroll-indicator i { color: var(--white); font-size: 1.5rem; }
        @keyframes bounce { 0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); } 40% { transform: translateX(-50%) translateY(-10px); } 60% { transform: translateX(-50%) translateY(-5px); } }
        .section { padding: 80px 20px; }
        .container { max-width: 1200px; margin: 0 auto; }
        .section-header { text-align: center; margin-bottom: 60px; }
        .section-header h2 { font-size: 2.5rem; color: var(--primary); margin-bottom: 15px; position: relative; display: inline-block; }
        .section-header h2 .spaced { display: block; font-size: 0.9rem; letter-spacing: 0.5em; text-transform: uppercase; color: var(--secondary); margin-bottom: 10px; font-weight: 400; }
        .section-header p { color: var(--text-light); max-width: 600px; margin: 0 auto; }
        .divider { width: 60px; height: 4px; background: linear-gradient(90deg, var(--primary), var(--secondary)); margin: 15px auto; border-radius: 2px; }
        .about { background: var(--light); }
        .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
        .about-image { position: relative; border-radius: 20px; overflow: hidden; box-shadow: var(--shadow-lg); }
        .about-image img { width: 100%; height: 450px; object-fit: cover; display: block; }
        .about-image::after { content: ''; position: absolute; top: 20px; left: 20px; right: -20px; bottom: -20px; border: 3px solid var(--secondary); border-radius: 20px; z-index: -1; }
        .about-content h3 { font-size: 2rem; color: var(--primary); margin-bottom: 20px; }
        .about-content p { color: var(--text-light); margin-bottom: 15px; line-height: 1.8; }
        .about-features { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 30px; }
        .about-feature { display: flex; align-items: flex-start; gap: 12px; }
        .about-feature i { font-size: 1.5rem; color: var(--secondary); margin-top: 3px; }
        .about-feature h4 { color: var(--primary); font-size: 1rem; margin-bottom: 5px; }
        .about-feature p { font-size: 0.9rem; margin: 0; }
        .specialties-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 30px; }
        .specialty-card { background: var(--white); border-radius: 20px; padding: 40px 30px; text-align: center; box-shadow: var(--shadow); transition: all 0.3s ease; position: relative; overflow: hidden; border: 1px solid rgba(0,0,0,0.05); }
        .specialty-card::before { content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 5px; background: linear-gradient(90deg, var(--primary), var(--secondary)); transform: scaleX(0); transition: transform 0.3s ease; }
        .specialty-card:hover { transform: translateY(-10px); box-shadow: var(--shadow-lg); }
        .specialty-card:hover::before { transform: scaleX(1); }
        .specialty-icon { width: 80px; height: 80px; background: linear-gradient(135deg, var(--primary), var(--secondary)); border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 20px; color: var(--white); font-size: 2rem; transition: transform 0.3s ease; }
        .specialty-card:hover .specialty-icon { transform: scale(1.1) rotate(5deg); }
        .specialty-card h3 { color: var(--primary); margin-bottom: 15px; font-size: 1.3rem; }
        .specialty-card p { color: var(--text-light); font-size: 0.95rem; line-height: 1.7; }
        .stats { background: linear-gradient(135deg, var(--primary-dark), var(--primary)); position: relative; overflow: hidden; }
        .stats::before { content: ''; position: absolute; top: -50%; right: -10%; width: 500px; height: 500px; background: rgba(255,255,255,0.03); border-radius: 50%; }
        .stats-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 40px; position: relative; z-index: 1; }
        .stat-item { text-align: center; color: var(--white); }
        .stat-number { font-size: 3.5rem; font-weight: 700; margin-bottom: 10px; }
        .stat-label { font-size: 1.1rem; opacity: 0.9; text-transform: uppercase; letter-spacing: 1px; }
        .why-choose { background: var(--light); }
        .why-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: center; }
        .why-image img { width: 100%; border-radius: 20px; box-shadow: var(--shadow-lg); }
        .why-list { list-style: none; }
        .why-item { display: flex; gap: 20px; margin-bottom: 25px; padding: 25px; background: var(--white); border-radius: 15px; box-shadow: var(--shadow); transition: all 0.3s ease; }
        .why-item:hover { transform: translateX(10px); box-shadow: var(--shadow-lg); }
        .why-number { min-width: 50px; height: 50px; background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); border-radius: 12px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; font-weight: 700; }
        .why-content h3 { color: var(--primary); margin-bottom: 8px; font-size: 1.2rem; }
        .why-content p { color: var(--text-light); font-size: 0.95rem; line-height: 1.6; }
        .faq-list { max-width: 800px; margin: 0 auto; }
        .faq-item { margin-bottom: 15px; border-radius: 15px; overflow: hidden; box-shadow: var(--shadow); background: var(--white); }
        .faq-question { width: 100%; padding: 25px 30px; background: var(--white); border: none; text-align: left; font-size: 1.1rem; font-weight: 600; color: var(--primary); cursor: pointer; display: flex; justify-content: space-between; align-items: center; transition: all 0.3s ease; }
        .faq-question:hover { background: var(--light); }
        .faq-question i { transition: transform 0.3s ease; color: var(--secondary); }
        .faq-item.active .faq-question i { transform: rotate(180deg); }
        .faq-answer { max-height: 0; overflow: hidden; transition: max-height 0.4s ease, padding 0.4s ease; background: var(--white); }
        .faq-item.active .faq-answer { max-height: 500px; padding: 0 30px 25px; }
        .faq-answer p { color: var(--text-light); line-height: 1.8; }
        .faq-answer a { color: var(--primary); text-decoration: none; font-weight: 600; }
        .faq-answer a:hover { text-decoration: underline; }
        .testimonials { background: linear-gradient(135deg, var(--light), #e8f4f8); position: relative; }
        .testimonials-header { text-align: center; margin-bottom: 50px; }
        .testimonials-header p { color: var(--text-light); font-size: 1.1rem; }
        .testimonials-header .highlight { color: var(--primary); font-weight: 700; font-size: 2rem; }
        .testimonials-slider { position: relative; overflow: hidden; max-width: 1000px; margin: 0 auto; }
        .testimonials-track { display: flex; transition: transform 0.5s ease; }
        .testimonial-card { min-width: 100%; padding: 20px; }
        .testimonial-inner { background: var(--white); border-radius: 20px; padding: 40px; box-shadow: var(--shadow); text-align: center; position: relative; }
        .testimonial-inner::before { content: '"'; position: absolute; top: 20px; left: 30px; font-size: 5rem; color: var(--secondary); opacity: 0.2; font-family: Georgia, serif; line-height: 1; }
        .testimonial-avatar { width: 80px; height: 80px; border-radius: 50%; background: linear-gradient(135deg, var(--primary), var(--secondary)); display: flex; align-items: center; justify-content: center; color: var(--white); font-size: 2rem; margin: 0 auto 20px; }
        .testimonial-text { color: var(--text-light); font-style: italic; line-height: 1.8; margin-bottom: 20px; font-size: 1.05rem; }
        .testimonial-author { color: var(--primary); font-weight: 700; font-size: 1.1rem; }
        .testimonial-nav { display: flex; justify-content: center; gap: 15px; margin-top: 30px; }
        .testimonial-nav button { width: 50px; height: 50px; border-radius: 50%; border: 2px solid var(--primary); background: var(--white); color: var(--primary); cursor: pointer; transition: all 0.3s ease; display: flex; align-items: center; justify-content: center; }
        .testimonial-nav button:hover { background: var(--primary); color: var(--white); }
        .testimonial-dots { display: flex; justify-content: center; gap: 10px; margin-top: 20px; }
        .dot { width: 12px; height: 12px; border-radius: 50%; background: #ddd; cursor: pointer; transition: all 0.3s ease; }
        .dot.active { background: var(--primary); width: 30px; border-radius: 6px; }
        .contact { background: var(--white); }
        .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; }
        .contact-info h3 { color: var(--primary); font-size: 1.8rem; margin-bottom: 20px; }
        .contact-details { margin-top: 30px; }
        .contact-item { display: flex; gap: 15px; margin-bottom: 25px; align-items: flex-start; }
        .contact-item i { width: 50px; height: 50px; background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); border-radius: 12px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; flex-shrink: 0; }
        .contact-item h4 { color: var(--primary); margin-bottom: 5px; }
        .contact-item p { color: var(--text-light); font-size: 0.95rem; }
        .contact-item a { color: var(--text-light); text-decoration: none; transition: color 0.3s; }
        .contact-item a:hover { color: var(--primary); }
        .booking-form { background: linear-gradient(135deg, var(--light), #e8f4f8); padding: 40px; border-radius: 20px; border: 2px solid rgba(0,102,102,0.1); }
        .booking-form h3 { color: var(--primary); margin-bottom: 10px; font-size: 1.5rem; }
        .booking-form .subtitle { color: var(--text-light); font-size: 0.9rem; margin-bottom: 25px; }
        .form-group { margin-bottom: 20px; }
        .form-group label { display: block; margin-bottom: 8px; color: var(--primary); font-weight: 600; font-size: 0.9rem; }
        .form-group label .required { color: #e74c3c; }
        .form-group input, .form-group textarea, .form-group select { width: 100%; padding: 14px 18px; border: 2px solid #e0e0e0; border-radius: 12px; font-size: 1rem; transition: all 0.3s ease; font-family: inherit; background: var(--white); }
        .form-group input:focus, .form-group textarea:focus, .form-group select:focus { outline: none; border-color: var(--secondary); box-shadow: 0 0 0 4px rgba(0,153,102,0.1); }
        .form-group textarea { resize: vertical; min-height: 100px; }
        .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .submit-btn { width: 100%; padding: 16px; background: linear-gradient(135deg, var(--whatsapp), #128C7E); color: var(--white); border: none; border-radius: 12px; font-size: 1.1rem; font-weight: 600; cursor: pointer; display: flex; align-items: center; justify-content: center; gap: 10px; transition: all 0.3s ease; }
        .submit-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 25px rgba(37,211,102,0.3); }
        .submit-btn i { font-size: 1.3rem; }
        .whatsapp-float { position: fixed; bottom: 30px; right: 30px; width: 60px; height: 60px; background: var(--whatsapp); color: var(--white); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.8rem; text-decoration: none; box-shadow: 0 4px 20px rgba(37,211,102,0.4); transition: all 0.3s ease; z-index: 999; animation: pulse 2s infinite; }
        .whatsapp-float:hover { transform: scale(1.1); box-shadow: 0 6px 30px rgba(37,211,102,0.5); }
        @keyframes pulse { 0% { box-shadow: 0 0 0 0 rgba(37,211,102,0.4); } 70% { box-shadow: 0 0 0 15px rgba(37,211,102,0); } 100% { box-shadow: 0 0 0 0 rgba(37,211,102,0); } }
        .footer { background: var(--dark); color: var(--white); padding: 60px 20px 20px; }
        .footer-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 40px; margin-bottom: 40px; }
        .footer-brand h3 { color: var(--secondary); margin-bottom: 15px; font-size: 1.5rem; }
        .footer-brand p { color: rgba(255,255,255,0.7); line-height: 1.8; }
        .footer-links h4 { color: var(--white); margin-bottom: 20px; font-size: 1.2rem; }
        .footer-links ul { list-style: none; }
        .footer-links li { margin-bottom: 12px; }
        .footer-links a { color: rgba(255,255,255,0.7); text-decoration: none; transition: color 0.3s; display: flex; align-items: center; gap: 8px; }
        .footer-links a:hover { color: var(--secondary); }
        .footer-links a i { font-size: 0.8rem; }
        .social-links { display: flex; gap: 15px; margin-top: 20px; }
        .social-links a { width: 40px; height: 40px; border-radius: 50%; background: rgba(255,255,255,0.1); display: flex; align-items: center; justify-content: center; color: var(--white); transition: all 0.3s ease; }
        .social-links a:hover { background: var(--secondary); transform: translateY(-3px); }
        .footer-bottom { border-top: 1px solid rgba(255,255,255,0.1); padding-top: 20px; text-align: center; color: rgba(255,255,255,0.5); font-size: 0.9rem; }
        .fade-in { opacity: 0; transform: translateY(30px); transition: all 0.6s ease; }
        .fade-in.visible { opacity: 1; transform: translateY(0); }
        .back-to-top { position: fixed; bottom: 100px; right: 30px; width: 50px; height: 50px; background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; opacity: 0; visibility: hidden; transition: all 0.3s ease; box-shadow: var(--shadow); border: none; z-index: 998; }
        .back-to-top.visible { opacity: 1; visibility: visible; }
        .back-to-top:hover { transform: translateY(-5px); box-shadow: var(--shadow-lg); }
        @media (max-width: 768px) {
            .nav-links { display: none; position: absolute; top: 100%; left: 0; width: 100%; background: var(--white); flex-direction: column; padding: 20px; box-shadow: var(--shadow); }
            .nav-links.active { display: flex; }
            .mobile-menu-btn { display: block; }
            .hero h1 { font-size: 2rem; }
            .about-grid, .why-grid, .contact-grid { grid-template-columns: 1fr; }
            .about-image::after { display: none; }
            .section-header h2 { font-size: 1.8rem; }
            .stat-number { font-size: 2.5rem; }
            .why-item { flex-direction: column; text-align: center; }
            .why-number { margin: 0 auto; }
            .form-row { grid-template-columns: 1fr; }
        }
    </style>
<base target="_blank">
</head>
<body>

    <div class="loader" id="loader"><div class="loader-spinner"></div></div>

    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <a href="#" class="logo">
                <div class="logo-icon">V</div>
                <div class="logo-text">
                    <span class="main">VASANT <span>MEDICARE</span></span>
                    <span class="sub">HOSPITAL</span>
                </div>
            </a>
            <ul class="nav-links" id="navLinks">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#specialties">Specialties</a></li>
                <li><a href="#why-choose">Why Us</a></li>
                <li><a href="#testimonials">Reviews</a></li>
                <li><a href="#contact" class="nav-cta"><i class="fab fa-whatsapp"></i> Book Now</a></li>
            </ul>
            <button class="mobile-menu-btn" id="mobileMenuBtn"><i class="fas fa-bars"></i></button>
        </div>
    </nav>

    <section class="hero" id="home">
        <div class="hero-content">
            <div class="hero-badge"><i class="fas fa-star"></i> Trusted Healthcare </div>
            <h1><span class="spaced">Welcome To</span>Vasant Medicare Hospital</h1>
            <p>Your health is our priority. We provide comprehensive medical care with state-of-the-art facilities, experienced doctors, and compassionate service for you and your family.</p>
            <div class="hero-buttons">
                <a href="#contact" class="btn btn-whatsapp"><i class="fab fa-whatsapp"></i> Book Appointment</a>
                <a href="#about" class="btn btn-outline"><i class="fas fa-info-circle"></i> Learn More</a>
            </div>
        </div>
        <div class="scroll-indicator"><i class="fas fa-chevron-down"></i></div>
    </section>

    <section class="section about" id="about">
        <div class="container">
            <div class="about-grid fade-in">
                <div class="about-image">
                    <img src="https://images.unsplash.com/photo-1631217868264-e5b90bb7e133?w=600&h=450&fit=crop" alt="Vasant Medicare Hospital">
                </div>
                <div class="about-content">
                    <h3>About Our Hospital</h3>
                    <p>Vasant Medicare Hospital is a leading multi-specialty healthcare facility committed to providing patient-centered medical care. Our team of highly qualified doctors and specialists deliver personalized treatment plans tailored to your needs.</p>
                    <p>Equipped with modern diagnostic tools and technology, we ensure accurate results and effective treatments. We prioritize your health and well-being, focusing on education, lifestyle management, and long-term care.</p>
                    <div class="about-features">
                        <div class="about-feature"><i class="fas fa-user-md"></i><div><h4>Expert Doctors</h4><p>Highly qualified specialists</p></div></div>
                        <div class="about-feature"><i class="fas fa-hospital"></i><div><h4>Modern Facility</h4><p>State-of-the-art equipment</p></div></div>
                        <div class="about-feature"><i class="fas fa-hands-helping"></i><div><h4>Patient Care</h4><p>Personalized treatment plans</p></div></div>
                        <div class="about-feature"><i class="fas fa-clock"></i><div><h4>24/7 Emergency</h4><p>Round the clock assistance</p></div></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="section" id="specialties">
        <div class="container">
            <div class="section-header fade-in">
                <h2><span class="spaced">Our Departments</span>Medical Specialties</h2>
                <div class="divider"></div>
                <p>Comprehensive care across multiple medical disciplines</p>
            </div>
            <div class="specialties-grid">
                <!-- <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-heartbeat"></i></div><h3>Cardiology</h3><p>Advanced cardiac care including diagnostics, interventions, and rehabilitation for all heart-related conditions.</p></div> -->
                <!-- <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-bone"></i></div><h3>Orthopedics</h3><p>Comprehensive bone and joint care, from fracture management to joint replacement surgeries.</p></div> -->
                <!-- <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-brain"></i></div><h3>Neurology</h3><p>Expert diagnosis and treatment of neurological disorders, stroke care, and neuro-rehabilitation.</p></div> -->
                <!-- <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-baby"></i></div><h3>Gynecology</h3><p>Complete women's health services including maternity care, fertility treatments, and wellness programs.</p></div> -->
                <!-- <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-child"></i></div><h3>Pediatrics</h3><p>Specialized healthcare for infants, children, and adolescents with a gentle, family-friendly approach.</p></div> -->
                <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-microscope"></i></div><h3>Diabetology</h3><p>Comprehensive diabetes care, including blood sugar management, prevention of complications, lifestyle counseling, and treatment of diabetes-related conditions.</p></div>
                 <div class="specialty-card fade-in"><div class="specialty-icon"><i class="fas fa-microscope"></i></div><h3>Endocrinology</h3><p>Comprehensive care for hormone-related disorders, including diabetes, thyroid conditions, metabolic disorders, and diseases affecting the body's endocrine</p></div>

            </div>
        </div>
    </section>

    <section class="section stats" id="stats">
        <div class="container">
            <div class="stats-grid">
                <div class="stat-item fade-in"><div class="stat-number"><span class="counter" data-target="15000">0</span>+</div><div class="stat-label">Happy Patients</div></div>
                <div class="stat-item fade-in"><div class="stat-number"><span class="counter" data-target="25">0</span>+</div><div class="stat-label">Expert Doctors</div></div>
                <div class="stat-item fade-in"><div class="stat-number"><span class="counter" data-target="50">0</span>+</div><div class="stat-label">Beds Available</div></div>
                <div class="stat-item fade-in"><div class="stat-number"><span class="counter" data-target="12">0</span>+</div><div class="stat-label">Years Experience</div></div>
            </div>
        </div>
    </section>

    <section class="section why-choose" id="why-choose">
        <div class="container">
            <div class="section-header fade-in">
                <h2><span class="spaced">Why Choose Us?</span>Clinical Excellence</h2>
                <div class="divider"></div>
            </div>
            <div class="why-grid">
                <div class="why-image fade-in"><img src="https://images.unsplash.com/photo-1579684385127-1ef15d508118?w=600&h=500&fit=crop" alt="Doctor"></div>
                <div class="why-list">
                    <div class="why-item fade-in"><div class="why-number">1</div><div class="why-content"><h3>Expertise You Can Trust</h3><p>Our team of highly qualified doctors and specialists delivers personalized treatment plans tailored to your needs.</p></div></div>
                    <div class="why-item fade-in"><div class="why-number">2</div><div class="why-content"><h3>Comprehensive Care</h3><p>From diagnosis to advanced treatment options, we offer holistic care for all medical conditions under one roof.</p></div></div>
                    <div class="why-item fade-in"><div class="why-number">3</div><div class="why-content"><h3>State-of-the-Art Facilities</h3><p>Our hospital is equipped with modern diagnostic tools and technology to ensure accurate results and effective treatments.</p></div></div>
                    <div class="why-item fade-in"><div class="why-number">4</div><div class="why-content"><h3>Patient-Centric Approach</h3><p>We prioritize your health and well-being, focusing on education, lifestyle management, and long-term care.</p></div></div>
                    <div class="why-item fade-in"><div class="why-number">5</div><div class="why-content"><h3>Affordable Healthcare</h3><p>Quality medical care at reasonable prices with transparent billing and multiple payment options.</p></div></div>
                </div>
            </div>
        </div>
    </section>

    <section class="section" id="faq">
        <div class="container">
            <div class="section-header fade-in">
                <h2><span class="spaced">Have Questions?</span>Frequently Asked Questions</h2>
                <div class="divider"></div>
            </div>
            <div class="faq-list">
                <div class="faq-item fade-in">
                    <button class="faq-question">How can I book an appointment?<i class="fas fa-chevron-down"></i></button>
                    <div class="faq-answer"><p>You can book an appointment by filling out the booking form on this website, which will send your details directly to our WhatsApp. Or you can call us directly at <a href="tel:+919545315641">+91 9545315641</a>. Walk-in patients are also welcome during OPD hours.</p></div>
                </div>
                <div class="faq-item fade-in">
                    <button class="faq-question">What are the OPD hours?<i class="fas fa-chevron-down"></i></button>
                    <div class="faq-answer"><p>Our OPD consultation hours are: <strong>10 AM to 7 PM (Mon, Tue, Wed & Fri)</strong>, <strong>2:30 PM to 7 PM (Thursday)</strong>, and <strong>10 AM to 6 PM (Saturday)</strong>. Sunday OPD is available for emergencies only. We recommend booking an appointment in advance to avoid waiting.</p></div>
                </div>
                <div class="faq-item fade-in">
                    <button class="faq-question">Do you accept health insurance?<i class="fas fa-chevron-down"></i></button>
                    <div class="faq-answer"><p>Yes, we accept all major health insurance plans and TPAs. Please bring your insurance card and valid ID proof during your visit. Our insurance desk will assist you with the cashless claim process.</p></div>
                </div>
                <div class="faq-item fade-in">
                    <button class="faq-question">Is there parking available?<i class="fas fa-chevron-down"></i></button>
                    <div class="faq-answer"><p>Yes, we have ample parking space for patients and visitors. Valet parking service is also available during peak hours. The parking area is monitored by CCTV for your vehicle's safety.</p></div>
                </div>
            </div>
        </div>
    </section>

    <section class="section testimonials" id="testimonials">
        <div class="container">
            <div class="testimonials-header fade-in">
                <h2><span class="spaced" style="color: var(--secondary); font-size: 0.9rem; letter-spacing: 0.5em;">What Our Patients Say</span><span style="color: var(--primary); font-size: 2.5rem; display: block; margin-top: 10px;">Testimonials</span></h2>
                <p>We're trusted by more than <span class="highlight">2,500+</span> satisfied patients</p>
            </div>
            <div class="testimonials-slider">
                <div class="testimonials-track" id="testimonialsTrack">
                    <div class="testimonial-card"><div class="testimonial-inner"><div class="testimonial-avatar">R</div><p class="testimonial-text">The doctors at Vasant Medicare are very knowledgeable and caring. The staff is cooperative and the facilities are excellent. I highly recommend this hospital for anyone seeking quality healthcare.</p><div class="testimonial-author">Ashish Patle</div></div></div>
                    <div class="testimonial-card"><div class="testimonial-inner"><div class="testimonial-avatar">P</div><p class="testimonial-text">Very clean and well-maintained hospital. The booking process through WhatsApp was so convenient. Dr. Patel explained everything clearly and the treatment was very effective.</p><div class="testimonial-author">Anjali Thakre</div></div></div>
                    <div class="testimonial-card"><div class="testimonial-inner"><div class="testimonial-avatar">A</div><p class="testimonial-text">I was impressed by the quick response and professional care. The emergency services are top-notch. Within hours of arriving, I was diagnosed and treatment began. Truly life-saving!</p><div class="testimonial-author">Shubham Ambule</div></div></div>
                    <div class="testimonial-card"><div class="testimonial-inner"><div class="testimonial-avatar">S</div><p class="testimonial-text">My mother's surgery went very smoothly. The entire team was supportive throughout the process. The post-operative care was exceptional. Thank you Vasant Medicare Hospital!</p><div class="testimonial-author">Umesh Bhoyar</div></div></div>
                    <div class="testimonial-card"><div class="testimonial-inner"><div class="testimonial-avatar">V</div><p class="testimonial-text">Best hospital in the area! The online appointment booking via WhatsApp is a game changer. No more waiting in long queues. The doctors are patient and listen to all concerns.</p><div class="testimonial-author">S. D. Katre</div></div></div>
                </div>
                <div class="testimonial-nav"><button id="prevBtn"><i class="fas fa-chevron-left"></i></button><button id="nextBtn"><i class="fas fa-chevron-right"></i></button></div>
                <div class="testimonial-dots" id="testimonialDots"></div>
            </div>
        </div>
    </section>

    <section class="section contact" id="contact">
        <div class="container">
            <div class="section-header fade-in">
                <h2><span class="spaced">Get In Touch</span>Book an Appointment</h2>
                <div class="divider"></div>
                <p>Fill the form below and we'll confirm your booking via WhatsApp</p>
            </div>
            <div class="contact-grid">
                <div class="contact-info fade-in">
                    <h3>Contact Information</h3>
                    <p>Reach out to us for any queries or emergency services.</p>
                    <div class="contact-details">
                        <div class="contact-item"><i class="fas fa-map-marker-alt"></i><div><h4>Address</h4><p>Ashirwad Nagar, Plot No 6, Godhani Road, near Tanishq Apartment, Sneh Nagar, Zingabai Takli, Nagpur, Maharashtra 440030</p></div></div>
                        <div class="contact-item"><i class="fas fa-phone"></i><div><h4>Phone</h4><p><a href="tel:+919545315641">+91 9545315641</a> (Emergency)<br><a href="tel:+919545315641">+91 9545315641</a> (OPD)</p></div></div>
                        <div class="contact-item"><i class="fas fa-clock"></i><div><h4>Working Hours</h4><p>Mon-Wed, Fri: 10 AM - 7 PM<br>Thu: 2:30 PM - 7 PM<br>Sat: 10 AM - 6 PM<br><strong>24/7 Emergency</strong></p></div></div>
                        <div class="contact-item"><i class="fas fa-envelope"></i><div><h4>Email</h4><p><a href="mailto:vasantmedicare31@gmail.com">vasantmedicare31@gmail.com</a></p></div></div>
                        <div class="contact-item"><i class="fab fa-whatsapp"></i><div><h4>WhatsApp</h4><p><a href="https://wa.me/919545315641" target="_blank">+91 9545315641</a></p></div></div>
                    </div>
                </div>
                <div class="booking-form fade-in">
                    <h3><i class="fab fa-whatsapp" style="color: var(--whatsapp);"></i> Book via WhatsApp</h3>
                    <p class="subtitle">Fill this form and it will be sent directly to our WhatsApp</p>
                    <form id="bookingForm">
                        <div class="form-row">
                            <div class="form-group"><label>Full Name <span class="required">*</span></label><input type="text" id="patientName" placeholder="Enter your full name" required></div>
                            <div class="form-group"><label>Phone Number <span class="required">*</span></label><input type="tel" id="patientPhone" placeholder="e.g., 9876543210" required></div>
                        </div>
                        <div class="form-row">
                            <div class="form-group"><label>Age</label><input type="number" id="patientAge" placeholder="Enter age" min="1" max="120"></div>
                            <div class="form-group"><label>Gender</label><select id="patientGender"><option value="">Select</option><option value="Male">Male</option><option value="Female">Female</option><option value="Other">Other</option></select></div>
                        </div>
                        <div class="form-group">
                            <label>Select Department <span class="required">*</span></label>
                            <select id="department" required>
                                <option value="">Choose a department</option>
                                <option value="General Medicine">General Medicine</option>
                                <option value="Cardiology">Cardiology</option>
                                <option value="Orthopedics">Orthopedics</option>
                                <option value="Neurology">Neurology</option>
                                <option value="Gynecology">Gynecology</option>
                                <option value="Pediatrics">Pediatrics</option>
                                <option value="Dermatology">Dermatology</option>
                                <option value="ENT">ENT</option>
                                <option value="Dental">Dental</option>
                                <option value="Diagnostics">Diagnostics / Lab Tests</option>
                            </select>
                        </div>
                        <div class="form-row">
                            <div class="form-group"><label>Preferred Date <span class="required">*</span></label><input type="date" id="appointmentDate" required></div>
                            <div class="form-group"><label>Preferred Time</label><select id="appointmentTime"><option value="">Any Time</option><option value="Morning (10 AM - 12 PM)">Morning (10 AM - 12 PM)</option><option value="Afternoon (12 PM - 3 PM)">Afternoon (12 PM - 3 PM)</option><option value="Evening (3 PM - 7 PM)">Evening (3 PM - 7 PM)</option></select></div>
                        </div>
                        <div class="form-group"><label>Symptoms / Reason for Visit</label><textarea id="symptoms" placeholder="Briefly describe your symptoms or reason for visit"></textarea></div>
                        <button type="submit" class="submit-btn"><i class="fab fa-whatsapp"></i> Send Booking to WhatsApp</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <footer class="footer">
        <div class="container">
            <div class="footer-grid">
                <div class="footer-brand"><h3><i class="fas fa-heartbeat"></i> Vasant Medicare</h3><p>Providing exceptional healthcare with compassion and excellence. Your health is our mission.</p><div class="social-links"><a href="#"><i class="fab fa-facebook-f"></i></a><a href="#"><i class="fab fa-twitter"></i></a><a href="#"><i class="fab fa-instagram"></i></a><a href="#"><i class="fab fa-linkedin-in"></i></a></div></div>
                <div class="footer-links"><h4>Quick Links</h4><ul><li><a href="#home"><i class="fas fa-chevron-right"></i> Home</a></li><li><a href="#about"><i class="fas fa-chevron-right"></i> About Us</a></li><li><a href="#specialties"><i class="fas fa-chevron-right"></i> Specialties</a></li><li><a href="#testimonials"><i class="fas fa-chevron-right"></i> Testimonials</a></li><li><a href="#contact"><i class="fas fa-chevron-right"></i> Book Appointment</a></li></ul></div>
                <div class="footer-links"><h4>Our Services</h4><ul><li><a href="#"><i class="fas fa-chevron-right"></i> Emergency Care</a></li><li><a href="#"><i class="fas fa-chevron-right"></i> OPD Services</a></li><li><a href="#"><i class="fas fa-chevron-right"></i> Diagnostics</a></li><li><a href="#"><i class="fas fa-chevron-right"></i> Pharmacy</a></li><li><a href="#"><i class="fas fa-chevron-right"></i> Ambulance</a></li></ul></div>
                <div class="footer-links"><h4>Contact</h4><ul><li><a href="#"><i class="fas fa-map-marker-alt"></i> Aashirwad Nagar, Plot No 6, Godhani Road, near Tanishq Apartment, Sneh Nagar, Zingabai Takli, Nagpur, Maharashtra 440030</a></li><li><a href="tel:+919545315641"><i class="fas fa-phone"></i> +91 9545315641</a></li><li><a href="mailto:vasantmedicare31@gmail.com"><i class="fas fa-envelope"></i> vasantmedicare31@gmail.com</a></li><li><a href="https://wa.me/919545315641" target="_blank"><i class="fab fa-whatsapp"></i> WhatsApp Us</a></li></ul></div>
            </div>
            <div class="footer-bottom"><p>&copy; Vasant Medicare Hospital. All Rights Reserved.</p></div>
        </div>
    </footer>

    <a href="https://wa.me/919545315641?text=Hello%2C%20I%20would%20like%20to%20book%20an%20appointment%20at%20Vasant%20Medicare%20Hospital." class="whatsapp-float" target="_blank" title="Chat on WhatsApp"><i class="fab fa-whatsapp"></i></a>

    <button class="back-to-top" id="backToTop"><i class="fas fa-arrow-up"></i></button>

    <script>
        // ========== WHATSAPP BOOKING FUNCTIONALITY ==========
        const HOSPITAL_WHATSAPP_NUMBER = "9545315641";

        document.getElementById('bookingForm').addEventListener('submit', function(e) {
            e.preventDefault();

            const name = document.getElementById('patientName').value.trim();
            const phone = document.getElementById('patientPhone').value.trim();
            const age = document.getElementById('patientAge').value;
            const gender = document.getElementById('patientGender').value;
            const department = document.getElementById('department').value;
            const date = document.getElementById('appointmentDate').value;
            const time = document.getElementById('appointmentTime').value;
            const symptoms = document.getElementById('symptoms').value.trim();

            const dateObj = new Date(date);
            const formattedDate = dateObj.toLocaleDateString('en-IN', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' });

            let message = `*📋 NEW APPOINTMENT REQUEST - Vasant Medicare Hospital*%0A%0A`;
            message += `*👤 Patient Name:* ${name}%0A`;
            message += `*📱 Phone:* ${phone}%0A`;
            if (age) message += `*🎂 Age:* ${age}%0A`;
            if (gender) message += `*⚧ Gender:* ${gender}%0A`;
            message += `%0A*🏥 Department:* ${department}%0A`;
            message += `*📅 Preferred Date:* ${formattedDate}%0A`;
            if (time) message += `*⏰ Preferred Time:* ${time}%0A`;
            if (symptoms) message += `%0A*📝 Symptoms/Reason:*%0A${symptoms}%0A`;
            message += `%0A-------------------%0A`;
            message += `Sent via: Vasant Medicare Hospital Website%0A`;
            message += `Time: ${new Date().toLocaleString('en-IN')}%0A%0A`;
            message += `Please confirm this appointment. Thank you! 🙏`;

            const whatsappURL = `https://wa.me/${HOSPITAL_WHATSAPP_NUMBER}?text=${message}`;
            window.open(whatsappURL, '_blank');

            setTimeout(() => {
                alert('✅ Your appointment details have been sent to our WhatsApp!\\n\\nOur team will contact you shortly to confirm your booking.\\n\\nIf WhatsApp did not open, please check your browser settings or contact us directly.');
            }, 500);

            this.reset();
        });

        const today = new Date().toISOString().split('T')[0];
        document.getElementById('appointmentDate').setAttribute('min', today);

        // Loader
        window.addEventListener('load', () => { setTimeout(() => { document.getElementById('loader').classList.add('hidden'); }, 500); });

        // Navbar
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => { navbar.classList.toggle('scrolled', window.scrollY > 50); });

        // Mobile menu
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const navLinks = document.getElementById('navLinks');
        mobileMenuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            const icon = mobileMenuBtn.querySelector('i');
            icon.classList.toggle('fa-bars'); icon.classList.toggle('fa-times');
        });
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => { navLinks.classList.remove('active'); mobileMenuBtn.querySelector('i').classList.remove('fa-times'); mobileMenuBtn.querySelector('i').classList.add('fa-bars'); });
        });

        // Scroll animations
        const observer = new IntersectionObserver((entries) => { entries.forEach(entry => { if (entry.isIntersecting) entry.target.classList.add('visible'); }); }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

        // Counter
        const counterObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const counter = entry.target;
                    const target = parseInt(counter.getAttribute('data-target'));
                    const duration = 2000;
                    const increment = target / (duration / 16);
                    let current = 0;
                    const updateCounter = () => { current += increment; if (current < target) { counter.textContent = Math.floor(current).toLocaleString(); requestAnimationFrame(updateCounter); } else { counter.textContent = target.toLocaleString(); } };
                    updateCounter(); counterObserver.unobserve(counter);
                }
            });
        }, { threshold: 0.5 });
        document.querySelectorAll('.counter').forEach(counter => counterObserver.observe(counter));

        // FAQ
        document.querySelectorAll('.faq-question').forEach(question => {
            question.addEventListener('click', () => {
                const item = question.parentElement;
                const isActive = item.classList.contains('active');
                document.querySelectorAll('.faq-item').forEach(faq => faq.classList.remove('active'));
                if (!isActive) item.classList.add('active');
            });
        });

        // Testimonials
        const track = document.getElementById('testimonialsTrack');
        const cards = document.querySelectorAll('.testimonial-card');
        const prevBtn = document.getElementById('prevBtn');
        const nextBtn = document.getElementById('nextBtn');
        const dotsContainer = document.getElementById('testimonialDots');
        let currentSlide = 0;

        cards.forEach((_, index) => { const dot = document.createElement('div'); dot.classList.add('dot'); if (index === 0) dot.classList.add('active'); dot.addEventListener('click', () => goToSlide(index)); dotsContainer.appendChild(dot); });
        const dots = document.querySelectorAll('.dot');

        function updateSlider() { track.style.transform = `translateX(-${currentSlide * 100}%)`; dots.forEach((dot, index) => { dot.classList.toggle('active', index === currentSlide); }); }
        function goToSlide(index) { currentSlide = index; if (currentSlide < 0) currentSlide = cards.length - 1; if (currentSlide >= cards.length) currentSlide = 0; updateSlider(); }
        function nextSlide() { goToSlide(currentSlide + 1); }
        function prevSlide() { goToSlide(currentSlide - 1); }
        prevBtn.addEventListener('click', prevSlide);
        nextBtn.addEventListener('click', nextSlide);
        setInterval(nextSlide, 5000);

        // Back to top
        const backToTop = document.getElementById('backToTop');
        window.addEventListener('scroll', () => { backToTop.classList.toggle('visible', window.scrollY > 500); });
        backToTop.addEventListener('click', () => { window.scrollTo({ top: 0, behavior: 'smooth' }); });

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) { e.preventDefault(); const target = document.querySelector(this.getAttribute('href')); if (target) target.scrollIntoView({ behavior: 'smooth', block: 'start' }); });
        });
    </script>
</body>
</html>
