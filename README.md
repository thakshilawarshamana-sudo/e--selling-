
html_code = '''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Purnima Thakshila | Web Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800;900&family=Space+Grotesk:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        :root {
            --primary: #0f0f0f;
            --secondary: #1a1a1a;
            --accent: #00d4aa;
            --accent-glow: rgba(0, 212, 170, 0.3);
            --text: #f5f5f5;
            --text-muted: #888;
            --border: #2a2a2a;
            --card: #141414;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Outfit', sans-serif;
            background: var(--primary);
            color: var(--text);
            overflow-x: hidden;
            cursor: none;
        }

        /* Custom Cursor */
        .cursor {
            width: 20px;
            height: 20px;
            border: 2px solid var(--accent);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 9999;
            transition: transform 0.1s, background 0.2s;
            mix-blend-mode: difference;
        }

        .cursor-dot {
            width: 6px;
            height: 6px;
            background: var(--accent);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 9999;
        }

        .cursor.hover {
            transform: scale(2);
            background: var(--accent-glow);
        }

        /* Scroll Progress */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--accent), #00f5d4);
            z-index: 10000;
            width: 0%;
            transition: width 0.1s;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.5rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            background: rgba(15, 15, 15, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border);
            transition: all 0.3s ease;
        }

        nav.scrolled {
            padding: 1rem 5%;
            background: rgba(15, 15, 15, 0.95);
        }

        .logo {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--text);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .logo span {
            color: var(--accent);
        }

        .nav-links {
            display: flex;
            gap: 2.5rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 0.95rem;
            font-weight: 500;
            position: relative;
            transition: color 0.3s;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--text);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-cta {
            background: var(--accent);
            color: var(--primary) !important;
            padding: 0.6rem 1.5rem;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .nav-cta:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 30px var(--accent-glow);
        }

        .nav-cta::after {
            display: none !important;
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            padding: 0 5%;
        }

        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
        }

        .hero-bg canvas {
            width: 100%;
            height: 100%;
        }

        .hero-content {
            position: relative;
            z-index: 1;
            text-align: center;
            max-width: 900px;
        }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: var(--card);
            border: 1px solid var(--border);
            padding: 0.5rem 1.2rem;
            border-radius: 50px;
            font-size: 0.85rem;
            color: var(--accent);
            margin-bottom: 2rem;
            animation: fadeInUp 0.8s ease;
        }

        .hero-badge .pulse {
            width: 8px;
            height: 8px;
            background: var(--accent);
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.2); }
        }

        .hero h1 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: clamp(2.5rem, 6vw, 5rem);
            font-weight: 700;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            animation: fadeInUp 0.8s ease 0.2s both;
        }

        .hero h1 .highlight {
            background: linear-gradient(135deg, var(--accent), #00f5d4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero p {
            font-size: 1.2rem;
            color: var(--text-muted);
            max-width: 600px;
            margin: 0 auto 2.5rem;
            line-height: 1.7;
            animation: fadeInUp 0.8s ease 0.4s both;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeInUp 0.8s ease 0.6s both;
        }

        .btn {
            padding: 1rem 2.5rem;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            border: none;
            cursor: none;
        }

        .btn-primary {
            background: var(--accent);
            color: var(--primary);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px var(--accent-glow);
        }

        .btn-outline {
            background: transparent;
            color: var(--text);
            border: 2px solid var(--border);
        }

        .btn-outline:hover {
            border-color: var(--accent);
            color: var(--accent);
            transform: translateY(-3px);
        }

        .hero-stats {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin-top: 4rem;
            animation: fadeInUp 0.8s ease 0.8s both;
        }

        .stat {
            text-align: center;
        }

        .stat-number {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--accent);
        }

        .stat-label {
            font-size: 0.9rem;
            color: var(--text-muted);
            margin-top: 0.3rem;
        }

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

        /* About Section */
        .section {
            padding: 8rem 5%;
            position: relative;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-label {
            display: inline-block;
            color: var(--accent);
            font-size: 0.9rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 1rem;
        }

        .section-title {
            font-family: 'Space Grotesk', sans-serif;
            font-size: clamp(2rem, 4vw, 3.5rem);
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .section-subtitle {
            color: var(--text-muted);
            font-size: 1.1rem;
            max-width: 600px;
            margin: 0 auto;
        }

        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .about-image {
            position: relative;
        }

        .about-image .image-frame {
            width: 100%;
            aspect-ratio: 1;
            background: linear-gradient(135deg, var(--accent), #00f5d4);
            border-radius: 30px;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .about-image .image-frame::before {
            content: '';
            position: absolute;
            inset: 3px;
            background: var(--card);
            border-radius: 27px;
        }

        .about-image .image-frame i {
            font-size: 8rem;
            color: var(--accent);
            opacity: 0.3;
            position: relative;
            z-index: 1;
        }

        .about-image .floating-card {
            position: absolute;
            background: var(--card);
            border: 1px solid var(--border);
            padding: 1rem 1.5rem;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            animation: float 3s ease-in-out infinite;
        }

        .floating-card.card-1 {
            top: 10%;
            right: -20px;
            animation-delay: 0s;
        }

        .floating-card.card-2 {
            bottom: 15%;
            left: -30px;
            animation-delay: 1.5s;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        .about-content h3 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 2rem;
            margin-bottom: 1.5rem;
        }

        .about-content p {
            color: var(--text-muted);
            line-height: 1.8;
            margin-bottom: 1.5rem;
            font-size: 1.05rem;
        }

        .skills-list {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
            margin-top: 2rem;
        }

        .skill-tag {
            background: var(--card);
            border: 1px solid var(--border);
            padding: 0.5rem 1.2rem;
            border-radius: 50px;
            font-size: 0.9rem;
            color: var(--text);
            transition: all 0.3s ease;
        }

        .skill-tag:hover {
            border-color: var(--accent);
            color: var(--accent);
            transform: translateY(-2px);
        }

        /* Services Section */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .service-card {
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 2.5rem;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, var(--accent), #00f5d4);
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.4s ease;
        }

        .service-card:hover::before {
            transform: scaleX(1);
        }

        .service-card:hover {
            transform: translateY(-10px);
            border-color: var(--accent);
            box-shadow: 0 20px 60px rgba(0, 212, 170, 0.1);
        }

        .service-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, var(--accent), #00f5d4);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1.5rem;
            font-size: 1.5rem;
            color: var(--primary);
        }

        .service-card h3 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.3rem;
            margin-bottom: 1rem;
        }

        .service-card p {
            color: var(--text-muted);
            line-height: 1.7;
            font-size: 0.95rem;
        }

        .service-features {
            margin-top: 1.5rem;
            list-style: none;
        }

        .service-features li {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        .service-features li i {
            color: var(--accent);
            font-size: 0.8rem;
        }

        /* Portfolio Section */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .portfolio-item {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            aspect-ratio: 16/10;
            background: var(--card);
            border: 1px solid var(--border);
            cursor: none;
        }

        .portfolio-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .portfolio-item:hover img {
            transform: scale(1.1);
        }

        .portfolio-overlay {
            position: absolute;
            inset: 0;
            background: linear-gradient(to top, rgba(15,15,15,0.95), transparent);
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            padding: 2rem;
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .portfolio-item:hover .portfolio-overlay {
            opacity: 1;
        }

        .portfolio-overlay h3 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            transform: translateY(20px);
            transition: transform 0.4s ease;
        }

        .portfolio-overlay p {
            color: var(--text-muted);
            font-size: 0.9rem;
            transform: translateY(20px);
            transition: transform 0.4s ease 0.1s;
        }

        .portfolio-item:hover .portfolio-overlay h3,
        .portfolio-item:hover .portfolio-overlay p {
            transform: translateY(0);
        }

        .portfolio-tags {
            display: flex;
            gap: 0.5rem;
            margin-top: 1rem;
            transform: translateY(20px);
            transition: transform 0.4s ease 0.2s;
        }

        .portfolio-item:hover .portfolio-tags {
            transform: translateY(0);
        }

        .portfolio-tags span {
            background: rgba(0, 212, 170, 0.2);
            color: var(--accent);
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            font-size: 0.75rem;
            font-weight: 500;
        }

        /* Pricing Section */
        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1000px;
            margin: 0 auto;
            align-items: center;
        }

        .pricing-card {
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 2.5rem;
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
        }

        .pricing-card.featured {
            background: linear-gradient(135deg, var(--card), rgba(0, 212, 170, 0.05));
            border-color: var(--accent);
            transform: scale(1.05);
            box-shadow: 0 20px 60px rgba(0, 212, 170, 0.1);
        }

        .pricing-card.featured::before {
            content: 'Most Popular';
            position: absolute;
            top: -12px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--accent);
            color: var(--primary);
            padding: 0.3rem 1rem;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 600;
        }

        .pricing-card:hover {
            transform: translateY(-10px);
            border-color: var(--accent);
        }

        .pricing-card.featured:hover {
            transform: scale(1.05) translateY(-10px);
        }

        .pricing-card h3 {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }

        .pricing-card .price {
            font-family: 'Space Grotesk', sans-serif;
            font-size: 3rem;
            font-weight: 700;
            color: var(--accent);
            margin: 1.5rem 0;
        }

        .pricing-card .price span {
            font-size: 1rem;
            color: var(--text-muted);
            font-weight: 400;
        }

        .pricing-features {
            list-style: none;
            margin: 2rem 0;
            text-align: left;
        }

        .pricing-features li {
            padding: 0.7rem 0;
            border-bottom: 1px solid var(--border);
            display: flex;
            align-items: center;
            gap: 0.8rem;
            font-size: 0.95rem;
        }

        .pricing-features li:last-child {
            border-bottom: none;
        }

        .pricing-features li i {
            color: var(--accent);
            font-size: 0.9rem;
        }

        .pricing-features li.not-included {
            color: var(--text-muted);
            text-decoration: line-through;
        }

        .pricing-features li.not-included i {
            color: #555;
        }

        /* Testimonials */
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .testimonial-card {
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 20px;
           
