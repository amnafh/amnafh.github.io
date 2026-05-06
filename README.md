<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kopi Senja & Cerita - Spesialis Kopi & Reservasi</title>
    
    <!-- Font Google -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
    
    <!-- Ikon FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* --- VARIABEL & RESET --- */
        :root {
            --primary-color: #3E2723; /* Coklat Kopi Gelap */
            --secondary-color: #D7CCC8; /* Krem Kopi */
            --accent-color: #A1887F; /* Coklat Muda */
            --accent-hover: #8D6E63;
            --gold-color: #C5A059; /* Warna Emas Mewah */
            --text-dark: #2c2c2c;
            --text-light: #f5f5f5;
            --text-muted: #5d4037;
            --white: #FFFFFF;
            
            --bg-light: #F3E5D8; 
            --card-bg: #FFFFFF;
            
            --shadow-sm: 0 4px 6px rgba(62, 39, 35, 0.05);
            --shadow-md: 0 10px 25px rgba(62, 39, 35, 0.15);
            --transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; font-size: 16px; }
        
        body { 
            font-family: 'Poppins', sans-serif; 
            background-color: var(--bg-light); 
            background-image: radial-gradient(#D7CCC8 2px, transparent 2px);
            background-size: 30px 30px;
            color: var(--text-dark); 
            line-height: 1.6; 
            overflow-x: hidden; 
            -webkit-font-smoothing: antialiased;
        }

        h1, h2, h3, h4 { font-family: 'Playfair Display', serif; color: var(--primary-color); }
        a { text-decoration: none; color: inherit; transition: var(--transition); }
        ul { list-style: none; }
        img { max-width: 100%; display: block; object-fit: cover; }

        /* --- UTILITY --- */
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; position: relative; }
        .section-padding { padding: 100px 0; }
        .text-center { text-align: center; }
        
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 14px 35px;
            border-radius: 50px;
            font-weight: 500;
            font-size: 1rem;
            transition: var(--transition);
            border: none;
            cursor: pointer;
            gap: 10px;
            position: relative;
            overflow: hidden;
            z-index: 1;
        }

        .btn::before {
            content: ''; position: absolute; top: 0; left: 0; width: 0%; height: 100%;
            background: rgba(255,255,255,0.2);
            transition: var(--transition);
            z-index: -1;
        }
        .btn:hover::before { width: 100%; }

        .btn-primary {
            background-color: var(--primary-color);
            color: var(--white);
            box-shadow: 0 4px 15px rgba(62, 39, 35, 0.3);
        }

        .btn-primary:hover {
            background-color: var(--accent-color);
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(62, 39, 35, 0.4);
        }

        /* Tombol Secondary */
        .btn-secondary {
            background-color: transparent;
            border: 2px solid var(--primary-color);
            color: var(--primary-color);
        }
        .btn-secondary:hover {
            background-color: var(--primary-color);
            color: var(--white);
        }

        .section-title { font-size: 2.5rem; margin-bottom: 1rem; position: relative; display: inline-block; }
        .section-title::after {
            content: ''; display: block; width: 60px; height: 3px; 
            background: var(--accent-color); margin: 10px auto 0; border-radius: 2px;
        }

        .section-subtitle {
            color: var(--accent-color);
            text-transform: uppercase;
            letter-spacing: 3px;
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 15px;
            display: block;
        }

        /* --- ANIMATIONS --- */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.8s ease-out, transform 0.8s ease-out;
        }
        .reveal.active { opacity: 1; transform: translateY(0); }

        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }

        @keyframes steam {
            0% { transform: translateY(0) scale(1); opacity: 0; }
            15% { opacity: 0.6; }
            50% { transform: translateY(-20px) scale(1.2); opacity: 0.4; }
            95% { transform: translateY(-40px) scale(1.5); opacity: 0; }
            100% { transform: translateY(-50px) scale(1.6); opacity: 0; }
        }

        @keyframes pulse-gold {
            0% { box-shadow: 0 0 0 0 rgba(255, 215, 0, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(255, 215, 0, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255, 215, 0, 0); }
        }

        /* --- HERO SECTION --- */
        #hero {
            min-height: 100vh;
            background: linear-gradient(135deg, rgba(62,39,35,0.95), rgba(62,39,35,0.85)), url('https://images.unsplash.com/photo-1461023058943-07fcbe16d735?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');
            background-size: cover; background-position: center; background-attachment: fixed;
            display: flex; align-items: center; color: var(--white);
            position: relative;
            overflow: hidden;
        }

        .hero-wrapper {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            align-items: center;
        }

        .hero-text h1 { font-size: 4rem; color: var(--white); margin-bottom: 20px; line-height: 1.1; text-shadow: 2px 2px 4px rgba(0,0,0,0.3); }
        .hero-text p { font-size: 1.2rem; margin-bottom: 40px; max-width: 500px; opacity: 0.9; font-weight: 300; }

        .hero-visual {
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            height: 400px;
        }

        .cup-container {
            position: relative;
            width: 200px;
            height: 200px;
            animation: float 4s ease-in-out infinite;
        }

        .cup-body {
            width: 180px; height: 140px;
            background: #fff;
            border-bottom-left-radius: 80px;
            border-bottom-right-radius: 80px;
            position: absolute;
            bottom: 0; left: 10px;
            box-shadow: inset -10px -5px 20px rgba(0,0,0,0.1);
            z-index: 2;
        }

        .cup-handle {
            width: 60px; height: 70px;
            border: 12px solid #fff;
            border-left: none;
            border-radius: 0 30px 30px 0;
            position: absolute;
            right: -35px; top: 40px;
            z-index: 1;
        }

        .cup-plate {
            width: 240px; height: 20px;
            background: #f0f0f0;
            border-radius: 50%;
            position: absolute;
            bottom: -15px; left: -20px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            z-index: 1;
        }

        .steam {
            position: absolute;
            top: -40px;
            width: 10px;
            height: 40px;
            background: rgba(255,255,255,0.6);
            border-radius: 50%;
            filter: blur(8px);
            z-index: 0;
            opacity: 0;
        }

        .steam:nth-child(1) { left: 50px; animation: steam 2.5s infinite 0.2s; }
        .steam:nth-child(2) { left: 80px; animation: steam 2.5s infinite 0.8s; height: 50px; }
        .steam:nth-child(3) { left: 110px; animation: steam 2.5s infinite 0.5s; }
        .steam:nth-child(4) { left: 140px; animation: steam 2.5s infinite 1.1s; }

        /* --- BADGE --- */
        .badge {
            position: absolute;
            top: 15px;
            left: 15px;
            background-color: #FFD700; 
            color: #3E2723; 
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
            z-index: 2;
            letter-spacing: 0.5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
            animation: pulse-gold 2s infinite;
        }
        .badge.signature {
            background-color: var(--primary-color);
            color: var(--white);
            animation: none; 
        }

        /* --- MODAL --- */
        .modal {
            display: none; 
            position: fixed;
            z-index: 2000; 
            left: 0; top: 0; width: 100%; height: 100%;
            background-color: rgba(62, 39, 35, 0.8); 
            backdrop-filter: blur(8px);
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .modal.show { display: flex; opacity: 1; }

        .modal-content {
            background-color: #fff;
            width: 90%;
            max-width: 500px;
            border-radius: 20px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            position: relative;
            transform: scale(0.9);
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            overflow: hidden;
            max-height: 90vh;
            overflow-y: auto;
        }
        .modal.show .modal-content { transform: scale(1); }

        .modal-header {
            background: var(--primary-color);
            padding: 20px 30px;
            color: white;
            display: flex; justify-content: space-between; align-items: center;
        }
        .modal-body { padding: 30px; }
        .close-btn { background: none; border: none; color: white; font-size: 1.5rem; cursor: pointer; transition: transform 0.2s; }
        .close-btn:hover { transform: rotate(90deg); }

        .form-group { margin-bottom: 20px; }
        .form-group label { display: block; margin-bottom: 8px; font-weight: 600; font-size: 0.9rem; color: var(--primary-color); }
        
        .form-control, .form-select {
            width: 100%; padding: 14px;
            border: 2px solid #eee; border-radius: 10px;
            font-family: inherit; transition: border-color 0.3s;
            background: #fcfcfc;
            font-size: 0.95rem;
        }
        
        .form-control:focus, .form-select:focus {
            border-color: var(--primary-color);
            outline: none; background: #fff;
        }
        
        .form-control[readonly] { background-color: #f0f0f0; color: #777; cursor: not-allowed; border-color: transparent; }

        .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }

        .modal-actions {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        .modal-actions .btn {
            flex: 1;
            padding: 12px 10px;
            font-size: 0.9rem;
        }

        .order-summary-box {
            background: #F9F9F9;
            border: 1px dashed var(--accent-color);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }
        .summary-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 0.9rem;
            color: var(--text-dark);
        }
        .summary-item span:last-child {
            font-weight: 600;
        }
        .summary-notes {
            font-size: 0.8rem;
            color: var(--text-muted);
            font-style: italic;
            margin-top: 5px;
            display: block;
        }

        /* --- NAVBAR --- */
        header {
            position: fixed; top: 0; width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            z-index: 1000; padding: 15px 0;
            transition: box-shadow 0.3s;
            border-bottom: 1px solid rgba(62, 39, 35, 0.05);
        }
        header.scrolled { box-shadow: 0 4px 20px rgba(62, 39, 35, 0.1); }
        
        .nav-container { display: flex; justify-content: space-between; align-items: center; }
        .logo { font-size: 1.5rem; font-weight: 700; color: var(--primary-color); display: flex; align-items: center; gap: 10px; }
        .logo i { color: var(--accent-color); }
        
        .nav-links { display: flex; gap: 30px; }
        .nav-links a { font-weight: 500; color: var(--text-dark); position: relative; font-size: 0.95rem; }
        .nav-links a::after {
            content: ''; position: absolute; width: 0; height: 2px; bottom: -5px; left: 0;
            background-color: var(--accent-color); transition: width 0.3s;
        }
        .nav-links a:hover::after { width: 100%; }
        
        .mobile-toggle { display: none; font-size: 1.5rem; cursor: pointer; color: var(--primary-color); }

        /* --- ABOUT --- */
        #about { background-color: var(--white); }
        .about-content { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
        .about-img { position: relative; }
        .about-img img { border-radius: 20px; box-shadow: var(--shadow-md); }
        .about-img::before {
            content: ''; position: absolute; top: -20px; left: -20px;
            width: 100%; height: 100%; border: 2px solid var(--accent-color);
            border-radius: 20px; z-index: -1; opacity: 0.3;
        }

        /* --- MENU --- */
        #menu { background-color: rgba(243, 229, 216, 0.5); }
        .menu-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 30px; margin-top: 40px; }
        .menu-card {
            background: var(--card-bg); border-radius: 20px; overflow: hidden;
            box-shadow: var(--shadow-sm); transition: var(--transition); display: flex; flex-direction: column;
            position: relative; border: 1px solid rgba(0,0,0,0.02);
        }
        .menu-card:hover { transform: translateY(-10px); box-shadow: var(--shadow-md); }
        
        .menu-img-container { height: 240px; overflow: hidden; position: relative; }
        .menu-img-container img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.6s ease; }
        .menu-card:hover .menu-img-container img { transform: scale(1.1); }
        
        .menu-info { padding: 25px; display: flex; flex-direction: column; flex-grow: 1; }
        .menu-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
        .menu-title { font-weight: 700; font-size: 1.15rem; color: var(--primary-color); }
        .price { color: var(--accent-color); font-weight: 700; font-size: 1.1rem; background: #FBE9E7; padding: 5px 12px; border-radius: 12px; }
        .menu-desc { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 25px; flex-grow: 1; line-height: 1.5; }
        
        .order-btn {
            background-color: var(--white);
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
            padding: 12px; border-radius: 12px;
            text-align: center; font-weight: 600; cursor: pointer;
            transition: var(--transition); display: flex; align-items: center; justify-content: center; gap: 10px;
        }
        .order-btn:hover { background-color: var(--primary-color); color: var(--white); }

        /* --- ROOMS --- */
        #rooms { background-color: var(--white); }
        .room-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }

        .room-card {
            background: var(--bg-light); 
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid #e0d0c0;
            transition: var(--transition);
            position: relative;
        }

        .room-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-md);
            border-color: var(--secondary-color);
        }

        .room-header {
            position: relative;
            height: 200px;
        }

        .room-header img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .room-icon {
            position: absolute;
            bottom: -25px;
            right: 20px;
            width: 50px;
            height: 50px;
            background: var(--primary-color);
            color: var(--white);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            z-index: 2;
        }

        .room-card.premium .room-icon { background: var(--gold-color); }
        .room-card.premium { border: 2px solid var(--gold-color); }

        .room-content { padding: 35px 20px 25px 20px; text-align: center; }
        .room-title { font-size: 1.3rem; margin-bottom: 5px; color: var(--primary-color); }
        .room-subtitle { font-size: 0.9rem; color: var(--accent-color); font-weight: 600; text-transform: uppercase; margin-bottom: 20px; display: block; }
        
        .room-features {
            text-align: left;
            margin-bottom: 25px;
            border-top: 1px solid #e0d0c0;
            padding-top: 15px;
        }

        .room-features li {
            margin-bottom: 10px;
            font-size: 0.9rem;
            color: var(--text-muted);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .room-features i {
            color: var(--accent-color);
            width: 20px;
        }
        
        .room-card.premium .room-features i { color: var(--gold-color); }

        .btn-room {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--primary-color);
            background: transparent;
            color: var(--primary-color);
            border-radius: 50px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
        }
        .btn-room:hover {
            background: var(--primary-color);
            color: white;
        }
        .room-card.premium .btn-room {
            border-color: var(--gold-color);
            color: var(--gold-color);
        }
        .room-card.premium .btn-room:hover {
            background: var(--gold-color);
            color: white;
        }

        /* --- FACILITIES --- */
        #facilities {
            background: linear-gradient(rgba(243, 229, 216, 0.9), rgba(243, 229, 216, 0.9)), url('https://images.unsplash.com/photo-1507133750040-4a8f57021571?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed; 
            position: relative;
        }

        .facilities-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 40px;
            margin-top: 50px;
        }
        .facility-item {
            text-align: center,
            padding: 30px 20px;
            background: white;
            border-radius: 15px;
            box-shadow: var(--shadow-md);
            transition: var(--transition);
            border: 1px solid rgba(255, 255, 255, 0.5);
        }
        .facility-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }
        .facility-icon {
            width: 70px; height: 70px;
            background: #EFEBE9;
            color: var(--primary-color);
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            margin: 0 auto 20px;
            font-size: 1.8rem;
            transition: var(--transition);
        }
        .facility-item:hover .facility-icon {
            background: var(--primary-color);
            color: white;
        }
        .facility-title {
            font-weight: 600;
            color: var(--text-dark);
            font-size: 1.1rem;
        }

        /* --- GALLERY --- */
        #gallery { background-color: var(--white); }
        .gallery-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 15px; margin-top: 40px; }
        .gallery-item { height: 250px; position: relative; overflow: hidden; border-radius: 10px; cursor: pointer; }
        .gallery-item img { width: 100%; height: 100%; transition: 0.5s; }
        .gallery-item:hover img { transform: scale(1.1); filter: brightness(0.8); }

        /* --- TESTIMONIALS --- */
        #testimonials { background-color: var(--primary-color); color: var(--white); position: relative; overflow: hidden; }
        #testimonials::before {
            content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background-image: radial-gradient(#ffffff 1px, transparent 1px);
            background-size: 30px 30px; opacity: 0.05;
        }
        
        #testimonials .section-title { color: var(--white); }
        #testimonials .section-subtitle { color: var(--secondary-color); }
        
        .testimonial-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; position: relative; z-index: 2; }
        .testimonial-card {
            background: rgba(255, 255, 255, 0.05); padding: 40px 30px; border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: var(--transition);
        }
        .testimonial-card:hover { background: rgba(255, 255, 255, 0.1); transform: translateY(-5px); }
        .stars { color: #FFD700; margin-bottom: 20px; font-size: 0.9rem; }
        .quote { font-style: italic; opacity: 0.9; margin-bottom: 25px; min-height: 90px; font-size: 0.95rem; line-height: 1.7; }
        .customer-name { font-weight: 700; font-family: 'Playfair Display', serif; font-size: 1.2rem; color: var(--secondary-color); }
        .customer-role { font-size: 0.85rem; opacity: 0.6; margin-top: 5px; }

        /* --- CONTACT --- */
        #contact { background-color: var(--white); }
        .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
        .contact-info h2 { margin-bottom: 30px; font-size: 2.5rem; color: var(--primary-color); }
        .contact-item { display: flex; align-items: flex-start; gap: 20px; margin-bottom: 30px; }
        .icon-box { 
            width: 50px; height: 50px; background: #EFEBE9; border-radius: 12px; 
            display: flex; align-items: center; justify-content: center; font-size: 1.2rem; 
            color: var(--primary-color); flex-shrink: 0;
        }
        .map-box { width: 100%; height: 400px; border-radius: 20px; overflow: hidden; box-shadow: var(--shadow-md); transform: translateZ(0); }
        .map-box iframe { width: 100%; height: 100%; border: 0; }

        /* --- FOOTER --- */
        footer { background-color: #2D1B18; color: #aaa; padding: 40px 0 20px; text-align: center; font-size: 0.9rem; border-top: 1px solid rgba(255,255,255,0.05); }
        .footer-social { margin-bottom: 20px; }
        .footer-social a { color: white; margin: 0 10px; font-size: 1.2rem; transition: 0.3s; }
        .footer-social a:hover { color: var(--accent-color); transform: translateY(-3px); display: inline-block; }

        /* --- FLOATING WA --- */
        .float-wa {
            position: fixed; bottom: 30px; right: 30px; 
            background-color: #25D366; color: white; 
            width: 60px; height: 60px; border-radius: 50%; 
            display: flex; align-items: center; justify-content: center; 
            font-size: 30px; 
            box-shadow: 0 5px 20px rgba(37, 211, 102, 0.4); 
            z-index: 999; transition: 0.3s;
        }
        .float-wa:hover { transform: scale(1.1) rotate(10deg); background-color: #20bd5a; }

        /* --- TOAST --- */
        .toast {
            position: fixed; top: 100px; right: 20px;
            background: white; border-left: 5px solid var(--primary-color);
            padding: 15px 25px; border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            display: flex; align-items: center; gap: 15px;
            transform: translateX(200%); transition: transform 0.4s cubic-bezier(0.68, -0.55, 0.27, 1.55);
            z-index: 3000;
        }
        .toast.show { transform: translateX(0); }
        .toast i { color: var(--primary-color); font-size: 1.2rem; }

        /* --- RESPONSIVE --- */
        @media (max-width: 992px) { 
            .hero-text h1 { font-size: 3rem; }
            .gallery-grid { grid-template-columns: 1fr 1fr; }
            .hero-wrapper { grid-template-columns: 1fr; text-align: center; }
            .hero-visual { margin-top: 40px; height: 300px; }
            .about-content, .contact-grid { grid-template-columns: 1fr; gap: 40px; }
            .form-row { grid-template-columns: 1fr; }
        }

        @media (max-width: 768px) {
            .hero-text h1 { font-size: 2.2rem; }
            .nav-links { 
                position: absolute; top: 70px; right: -100%; 
                background: white; flex-direction: column; width: 100%; 
                text-align: center; padding: 30px 0; 
                box-shadow: 0 10px 20px rgba(0,0,0,0.05); 
                transition: 0.4s ease-in-out;
            }
            .nav-links.active { right: 0; }
            .mobile-toggle { display: block; }
            .section-title { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <!-- Toast Notification -->
    <div id="toast" class="toast">
        <i class="fas fa-check-circle"></i>
        <div>
            <h4 style="margin:0; font-size:0.9rem; color:var(--primary-color)">Sukses</h4>
            <p style="margin:0; font-size:0.8rem; color:#666" id="toastMsg">Action completed</p>
        </div>
    </div>

    <!-- Navigasi -->
    <header id="navbar">
        <div class="container nav-container">
            <div class="logo">
                <i class="fas fa-coffee"></i> Kopi Senja
            </div>
            <div class="mobile-toggle" onclick="toggleMenu()">
                <i class="fas fa-bars" id="menuIcon"></i>
            </div>
            <nav class="nav-links" id="navLinks">
                <a href="#hero" onclick="toggleMenu()">Beranda</a>
                <a href="#about" onclick="toggleMenu()">Tentang</a>
                <a href="#menu" onclick="toggleMenu()">Menu</a>
                <a href="#rooms" onclick="toggleMenu()">Fasilitas</a>
                <a href="#gallery" onclick="toggleMenu()">Galeri</a>
                <a href="#contact" onclick="toggleMenu()">Lokasi</a>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="hero">
        <div class="container hero-wrapper">
            <div class="hero-text reveal active">
                <h1>Manisknya Senja,<br>Dalam Secangkir Kopi</h1>
                <p>Nikmati perpaduan espresso premium, susu segar, dan gula aren asli yang menemani cerita Anda. Diseduh dengan hati, disajikan dengan senyuman.</p>
                <a href="#menu" class="btn btn-primary">
                    Lihat Menu <i class="fas fa-arrow-right"></i>
                </a>
            </div>
            
            <div class="hero-visual reveal">
                <div class="cup-container">
                    <div class="steam"></div>
                    <div class="steam"></div>
                    <div class="steam"></div>
                    <div class="steam"></div>
                    <div class="cup-handle"></div>
                    <div class="cup-body"></div>
                    <div class="cup-plate"></div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section-padding">
        <div class="container about-content">
            <div class="about-img reveal">
                <img src="https://images.unsplash.com/photo-1442512595331-e89e73853f31?auto=format&fit=crop&w=800&q=80" alt="Suasana Kafe">
            </div>
            <div class="about-text reveal">
                <span class="section-subtitle">Tentang Kami</span>
                <h2 class="section-title">Dedikasi untuk Rasa</h2>
                <p style="margin-bottom: 20px; color: var(--text-muted);">Kami percaya bahwa kopi bukan sekadar minuman, melainkan sebuah pengalaman. Setiap biji kopi yang kami gunakan dipilih langsung dari petani lokal terbaik yang telah berdedikasi puluhan tahun.</p>
                <p style="color: var(--text-muted);">Tempat ini didesain untuk Anda yang mencari ketenangan di tengah hiruk pikuk kota, atau sekadar ingin menikmati varian kopi terbaik kami dalam suasana yang hangat.</p>
                <div style="margin-top: 30px; display: flex; gap: 20px;">
                    <div>
                        <h3 style="color: var(--primary-color); font-size: 2rem;">5+</h3>
                        <p style="font-size: 0.9rem;">Tahun Pengalaman</p>
                    </div>
                    <div>
                        <h3 style="color: var(--primary-color); font-size: 2rem;">20+</h3>
                        <p style="font-size: 0.9rem;">Varian Menu</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Menu Section -->
    <section id="menu" class="section-padding">
        <div class="container">
            <div class="text-center reveal">
                <span class="section-subtitle">Pilihan Terbaik</span>
                <h2 class="section-title">Menu Favorit</h2>
                <p style="max-width: 600px; margin: 0 auto; color: var(--text-muted);">Dikombinasikan dengan bahan berkualitas tinggi untuk menciptakan simfoni rasa di lidah Anda.</p>
            </div>
            <div class="menu-grid">
                <!-- Item 1 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1572442388796-11668a67e53d?auto=format&fit=crop&w=600&q=80" alt="Cappuccino">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Classic Cappuccino</span><span class="price">Rp 30k</span></div>
                        <p class="menu-desc">Keseimbangan sempurna espresso, susu hangat, dan foam yang lembut dan tebal.</p>
                        <div class="order-btn" onclick="openOrderModal('Classic Cappuccino')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 2 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1517701550927-30cf4ba1dba5?auto=format&fit=crop&w=600&q=80" alt="Iced Americano">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Iced Americano</span><span class="price">Rp 20k</span></div>
                        <p class="menu-desc">Double shot espresso ekstrak dengan air dingin segar. Segar, kuat, dan membangkitkan semangat.</p>
                        <div class="order-btn" onclick="openOrderModal('Iced Americano')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 3 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1534778101976-62847782c213?auto=format&fit=crop&w=600&q=80" alt="Caffè Latte">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Caffè Latte</span><span class="price">Rp 28k</span></div>
                        <p class="menu-desc">Espresso dengan susu hangat yang melimpah, sentuhan lembut menenangkan di lidah.</p>
                        <div class="order-btn" onclick="openOrderModal('Caffè Latte')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 4 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?auto=format&fit=crop&w=600&q=80" alt="V60 Manual Brew">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">V60 Manual Brew</span><span class="price">Rp 35k</span></div>
                        <p class="menu-desc">Metode seduh manual untuk menonjolkan karakter buah asli dari biji kopi pilihan.</p>
                        <div class="order-btn" onclick="openOrderModal('V60 Manual Brew')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 5 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1510591509098-f4fdc6d0ff04?auto=format&fit=crop&w=600&q=80" alt="Espresso">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Single Espresso</span><span class="price">Rp 18k</span></div>
                        <p class="menu-desc">Satu shot kopi murni penuh energi untuk pecinta kopi sejati yang intens.</p>
                        <div class="order-btn" onclick="openOrderModal('Single Espresso')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 6 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1578314675249-a6910f80cc4e?auto=format&fit=crop&w=600&q=80" alt="Iced Mocha">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Iced Mocha</span><span class="price">Rp 32k</span></div>
                        <p class="menu-desc">Perpaduan espresso, susu, dan coklat belgia yang kaya rasa manis.</p>
                        <div class="order-btn" onclick="openOrderModal('Iced Mocha')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 7 -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <img src="https://images.unsplash.com/photo-1627435601361-ec25f5b1d0e5?auto=format&fit=crop&w=600&q=80" alt="Affogato">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Affogato</span><span class="price">Rp 30k</span></div>
                        <p class="menu-desc">Espresso panas dituangkan di atas es krim vanilla lezat. Kontras yang sempurna.</p>
                        <div class="order-btn" onclick="openOrderModal('Affogato')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>
                
                <!-- --- 4 MENU BEST SELLER --- -->

                <!-- Item 8: Iced Caramel Macchiato -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <span class="badge">Best Seller</span>
                        <img src="https://images.unsplash.com/photo-1596838132731-3301c3fd4317?auto=format&fit=crop&w=600&q=80" alt="Iced Caramel Macchiato">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Iced Caramel Macchiato</span><span class="price">Rp 32k</span></div>
                        <p class="menu-desc">Vanilla latte dingin dengan saus karamel lezat dan siraman espresso.</p>
                        <div class="order-btn" onclick="openOrderModal('Iced Caramel Macchiato')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 9: Hot Caramel Macchiato -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <span class="badge">Best Seller</span>
                        <img src="https://images.unsplash.com/photo-1596838132731-3301c3fd4317?auto=format&fit=crop&w=600&q=80" alt="Hot Caramel Macchiato">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Hot Caramel Macchiato</span><span class="price">Rp 30k</span></div>
                        <p class="menu-desc">Kehangatan espresso berpadu hangat dengan saus karamel leleh yang memanjakan.</p>
                        <div class="order-btn" onclick="openOrderModal('Hot Caramel Macchiato')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 10: Salted Caramel Macchiato -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <span class="badge">Best Seller</span>
                        <img src="https://images.unsplash.com/photo-1610632380989-680fe40816c6?auto=format&fit=crop&w=600&q=80" alt="Salted Caramel Macchiato">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Salted Caramel Macchiato</span><span class="price">Rp 35k</span></div>
                        <p class="menu-desc">Perpaduan unik manis dan asin garam laut dengan saus karamel premium.</p>
                        <div class="order-btn" onclick="openOrderModal('Salted Caramel Macchiato')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- Item 11: Extra Caramel Macchiato -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <span class="badge">Best Seller</span>
                        <img src="https://images.unsplash.com/photo-1541167760496-1628856ab772?auto=format&fit=crop&w=600&q=80" alt="Extra Caramel Macchiato">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Extra Caramel Macchiato</span><span class="price">Rp 35k</span></div>
                        <p class="menu-desc">Dosis saus karamel ekstra banyak untuk pecinta manis berlebih.</p>
                        <div class="order-btn" onclick="openOrderModal('Extra Caramel Macchiato')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

                <!-- ITEM 12: Hazelnut Signature Latte -->
                <div class="menu-card reveal">
                    <div class="menu-img-container">
                        <span class="badge signature">Signature</span>
                        <img src="https://images.unsplash.com/photo-1595981267035-7b04ca84a82d?auto=format&fit=crop&w=600&q=80" alt="Hazelnut Latte">
                    </div>
                    <div class="menu-info">
                        <div class="menu-header"><span class="menu-title">Hazelnut Signature Latte</span><span class="price">Rp 33k</span></div>
                        <p class="menu-desc">Espresso dengan susu creamy dan sirup hazelnut premium. Aroma kacang yang menenangkan.</p>
                        <div class="order-btn" onclick="openOrderModal('Hazelnut Signature Latte')">
                            <i class="fas fa-shopping-bag"></i> Pesan
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- SECTION: PILIHAN RUANGAN -->
    <section id="rooms" class="section-padding">
        <div class="container">
            <div class="text-center reveal">
                <span class="section-subtitle">Fasilitas Ruang</span>
                <h2 class="section-title">Pilihan Ruangan</h2>
                <p style="max-width: 600px; margin: 0 auto; color: var(--text-muted);">Nikmati kopi Anda di suasana yang sesuai dengan kebutuhan Anda, dari area santai hingga ruang eksklusif.</p>
            </div>

            <div class="room-grid">
                
                <!-- Ruang Biasa -->
                <div class="room-card reveal">
                    <div class="room-header">
                        <img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?auto=format&fit=crop&w=600&q=80" alt="Ruang Biasa">
                        <div class="room-icon"><i class="fas fa-users"></i></div>
                    </div>
                    <div class="room-content">
                        <h3 class="room-title">Ruang Regular</h3>
                        <span class="room-subtitle">Area Terbuka</span>
                        <ul class="room-features">
                            <li><i class="fas fa-check-circle"></i> Free WiFi High Speed</li>
                            <li><i class="fas fa-check-circle"></i> Suasana Santai & Ramai</li>
                            <li><i class="fas fa-check-circle"></i> Akses Stop Kontak</li>
                            <li><i class="fas fa-check-circle"></i> Musik Akustik</li>
                        </ul>
                        <button class="btn-room" onclick="openBookingModal('Ruang Regular')">Booking Tempat</button>
                    </div>
                </div>

                <!-- Ruang VIP -->
                <div class="room-card reveal">
                    <div class="room-header">
                        <img src="https://images.unsplash.com/photo-1521017432531-fbd92d768814?auto=format&fit=crop&w=600&q=80" alt="Ruang VIP">
                        <div class="room-icon"><i class="fas fa-crown"></i></div>
                    </div>
                    <div class="room-content">
                        <h3 class="room-title">Ruang VIP</h3>
                        <span class="room-subtitle">Semi Privat</span>
                        <ul class="room-features">
                            <li><i class="fas fa-check-circle"></i> Sofa Nyaman (2-4 Orang)</li>
                            <li><i class="fas fa-check-circle"></i> Lebih Tenang</li>
                            <li><i class="fas fa-check-circle"></i> Prioritas Pelayanan</li>
                            <li><i class="fas fa-check-circle"></i> Cocok untuk Meeting Kecil</li>
                        </ul>
                        <button class="btn-room" onclick="openBookingModal('Ruang VIP')">Booking Tempat</button>
                    </div>
                </div>

                <!-- Ruang VVIP -->
                <div class="room-card reveal">
                    <div class="room-header">
                        <img src="https://images.unsplash.com/photo-1497366216548-37526070297c?auto=format&fit=crop&w=600&q=80" alt="Ruang VVIP">
                        <div class="room-icon"><i class="fas fa-gem"></i></div>
                    </div>
                    <div class="room-content">
                        <h3 class="room-title">Ruang VVIP</h3>
                        <span class="room-subtitle">Privat Eksklusif</span>
                        <ul class="room-features">
                            <li><i class="fas fa-check-circle"></i> Ruang Tertutup Full AC</li>
                            <li><i class="fas fa-check-circle"></i> TV / Proyektor</li>
                            <li><i class="fas fa-check-circle"></i> Meja Meeting</li>
                            <li><i class="fas fa-check-circle"></i> Kapasitas 6-10 Orang</li>
                        </ul>
                        <button class="btn-room" onclick="openBookingModal('Ruang VVIP')">Booking Tempat</button>
                    </div>
                </div>

                <!-- Premium -->
                <div class="room-card premium reveal">
                    <div class="room-header">
                        <img src="https://images.unsplash.com/photo-1551632436-cbf8dd35adfa?auto=format&fit=crop&w=600&q=80" alt="Premium Lounge">
                        <div class="room-icon"><i class="fas fa-star"></i></div>
                    </div>
                    <div class="room-content">
                        <h3 class="room-title">Premium Lounge</h3>
                        <span class="room-subtitle">Pengalaman Tertinggi</span>
                        <ul class="room-features">
                            <li><i class="fas fa-check-circle"></i> Pelayanan Butler</li>
                            <li><i class="fas fa-check-circle"></i> Menu Khusus Premium</li>
                            <li><i class="fas fa-check-circle"></i> Dekorasi Mewah</li>
                            <li><i class="fas fa-check-circle"></i> Suasana Hening</li>
                        </ul>
                        <button class="btn-room" onclick="openBookingModal('Premium Lounge')">Booking Tempat</button>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- SECTION: FASILITAS UMUM -->
    <section id="facilities" class="section-padding">
        <div class="container">
            <div class="text-center reveal">
                <span class="section-subtitle" style="color: var(--primary-color);">Amenities</span>
                <h2 class="section-title" style="color: var(--primary-color);">Fasilitas Kafe</h2>
                <p style="max-width: 600px; margin: 0 auto; color: var(--text-dark);">Kami menyediakan berbagai fasilitas penunjang untuk kenyamanan Anda selama berkunjung.</p>
            </div>
            <div class="facilities-grid">
                <div class="facility-item reveal">
                    <div class="facility-icon"><i class="fas fa-wifi"></i></div>
                    <h4 class="facility-title">Free WiFi</h4>
                </div>
                <div class="facility-item reveal">
                    <div class="facility-icon"><i class="fas fa-parking"></i></div>
                    <h4 class="facility-title">Parkir Luas</h4>
                </div>
                <div class="facility-item reveal">
                    <div class="facility-icon"><i class="fas fa-mosque"></i></div>
                    <h4 class="facility-title">Musholla</h4>
                </div>
                <div class="facility-item reveal">
                    <div class="facility-icon"><i class="fas fa-restroom"></i></div>
                    <h4 class="facility-title">Toilet Bersih</h4>
                </div>
                <div class="facility-item reveal">
                    <div class="facility-icon"><i class="fas fa-smoking"></i></div>
                    <h4 class="facility-title">Smoking Area</h4>
                </div>
                <div class="facility-item reveal">
                    <div class="facility-icon"><i class="fas fa-chess"></i></div>
                    <h4 class="facility-title">Board Games</h4>
                </div>
            </div>
        </div>
    </section>

    <!-- Gallery Section -->
    <section id="gallery" class="section-padding">
        <div class="container">
            <div class="text-center reveal">
                <span class="section-subtitle">Visual</span>
                <h2 class="section-title">Galeri Kafe</h2>
            </div>
            <div class="gallery-grid">
                <div class="gallery-item reveal"><img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?auto=format&fit=crop&w=400&q=80" alt="Galeri 1"></div>
                <div class="gallery-item reveal"><img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?auto=format&fit=crop&w=400&q=80" alt="Galeri 2"></div>
                <div class="gallery-item reveal"><img src="https://images.unsplash.com/photo-1559496417-e7f25cb247f3?auto=format&fit=crop&w=400&q=80" alt="Galeri 3"></div>
                <div class="gallery-item reveal"><img src="https://images.unsplash.com/photo-1498804103079-a6351b050096?auto=format&fit=crop&w=400&q=80" alt="Galeri 4"></div>
            </div>
        </div>
    </section>

    <!-- TESTIMONIALS SECTION -->
    <section id="testimonials" class="section-padding">
        <div class="container">
            <div class="text-center reveal">
                <span class="section-subtitle">Kata Mereka</span>
                <h2 class="section-title">Testimoni Pelanggan</h2>
            </div>
            <div class="testimonial-grid">
                <div class="testimonial-card reveal">
                    <div class="stars"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></div>
                    <p class="quote">"Tempat paling cozy untuk nugas. Kopinya enak, playlist lagunya juga menyenangkan. Pasti bakal balik lagi!"</p>
                    <div class="customer-name">Rina Amalia</div>
                    <div class="customer-role">Mahasiswi</div>
                </div>
                <div class="testimonial-card reveal">
                    <div class="stars"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star-half-alt"></i></div>
                    <p class="quote">"Manual brew-nya juara! Benar-benar terasa kualitas biji kopinya. Baristanya sangat ramah dan informatif."</p>
                    <div class="customer-name">Budi Santoso</div>
                    <div class="customer-role">Freelancer</div>
                </div>
                <div class="testimonial-card reveal">
                    <div class="stars"><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i></div>
                    <p class="quote">"Sangat rekomendasi buat nongkrong bareng teman. Interior-nya instagrammable banget, cocok buat foto-foto."</p>
                    <div class="customer-name">Amanda Putri</div>
                    <div class="customer-role">Content Creator</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section-padding">
        <div class="container">
            <div class="contact-grid">
                <div class="contact-info reveal">
                    <span class="section-subtitle">Kunjungi Kami</span>
                    <h2>Lokasi & Kontak</h2>
                    
                    <div class="contact-item">
                        <div class="icon-box"><i class="fas fa-map-marker-alt"></i></div>
                        <div>
                            <h4 style="margin-bottom:5px; color:var(--primary-color)">Alamat</h4>
                            <p style="color:var(--text-muted); font-size:0.95rem;">Jl. Wilis No.23, Gading Kasri,<br>Kec. Klojen, Kota Malang,<br>Jawa Timur 65115</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="icon-box"><i class="fas fa-clock"></i></div>
                        <div>
                            <h4 style="margin-bottom:5px; color:var(--primary-color)">Jam Buka</h4>
                            <p style="color:var(--text-muted); font-size:0.95rem;">Senin - Minggu<br>08.00 - 22.00 WIB</p>
                        </div>
                    </div>
                    <div class="contact-item">
                        <div class="icon-box"><i class="fab fa-whatsapp"></i></div>
                        <div>
                            <h4 style="margin-bottom:5px; color:var(--primary-color)">WhatsApp</h4>
                            <p style="color:var(--text-muted); font-size:0.95rem;">+62 888-299-000</p>
                        </div>
                    </div>
                </div>
                <div class="map-box reveal">
                    <iframe 
                        src="https://maps.google.com/maps?q=Jl.+Wilis+No.23,+Gading+Kasri,+Kec.+Klojen,+Kota+Malang,+Jawa+Timur+65115&t=&z=15&ie=UTF8&iwloc=&output=embed" 
                        allowfullscreen="" 
                        loading="lazy" 
                        referrerpolicy="no-referrer-when-downgrade">
                    </iframe>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-social">
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-facebook-f"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
            </div>
            <p>&copy; 2023 Kopi Senja & Cerita. Dibuat dengan cinta dan kopi.</p>
        </div>
    </footer>

    <!-- Floating WhatsApp Button -->
    <a href="https://wa.me/628888299000" class="float-wa" target="_blank">
        <i class="fab fa-whatsapp"></i>
    </a>

    <!-- MODAL 1: FORUM PEMESANAN MENU (MULTI-STEP) -->
    <div id="orderModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 style="margin:0; font-size:1.2rem;">Pemesanan Menu</h3>
                <button class="close-btn" onclick="closeModal('orderModal')">&times;</button>
            </div>
            
            <div class="modal-body">
                <!-- STEP 1: Detail Pesanan -->
                <div id="order-step-1">
                    <form id="orderFormStep1">
                        <div class="form-group">
                            <label for="customerName">Nama Pemesan</label>
                            <input type="text" id="customerName" class="form-control" placeholder="Contoh: Budi Santoso" required>
                        </div>

                        <div class="form-group">
                            <label for="menuName">Menu Pesanan</label>
                            <input type="text" id="menuName" class="form-control" readonly>
                        </div>

                        <div class="form-group">
                            <label for="quantity">Jumlah</label>
                            <input type="number" id="quantity" class="form-control" min="1" value="1" required>
                        </div>

                        <div class="form-group">
                            <label for="notes">Catatan Tambahan (Opsional)</label>
                            <textarea id="notes" class="form-control" rows="3" placeholder="Contoh: Kurangi gula, tambahkan es..."></textarea>
                        </div>
                        
                        <div class="modal-actions">
                            <button type="button" class="btn btn-secondary" onclick="addToCart()">
                                Beli Lagi
                            </button>
                            <button type="button" class="btn btn-primary" onclick="goToStep2()">
                                Lanjut Beli
                            </button>
                        </div>
                    </form>
                </div>

                <!-- STEP 2: Pembayaran (Tersembunyi Awalnya) -->
                <div id="order-step-2" style="display: none;">
                    <h4 style="margin-bottom: 15px; color:var(--primary-color);">Konfirmasi Pesanan</h4>
                    
                    <!-- Ringkasan Pesanan -->
                    <div class="order-summary-box" id="orderSummaryBox">
                        <!-- Isi ringkasan akan di-generate via JS -->
                    </div>

                    <div class="form-group">
                        <label for="paymentMethod">Metode Pembayaran</label>
                        <select id="paymentMethod" class="form-select" required>
                            <option value="" disabled selected>-- Pilih Metode Pembayaran --</option>
                            <option value="Cash (Bayar di Tempat)">Cash (Bayar di Tempat)</option>
                            <option value="QRIS (Scan)">QRIS (Scan)</option>
                            <option value="Transfer Bank BCA">Transfer Bank BCA</option>
                            <option value="E-Wallet (Gopay/Ovo/Dana)">E-Wallet (Gopay/Ovo/Dana)</option>
                        </select>
                    </div>

                    <div class="modal-actions">
                        <button type="button" class="btn btn-secondary" onclick="backToStep1()">
                            Kembali
                        </button>
                        <button type="button" class="btn btn-primary" onclick="sendFinalOrder()">
                            Kirim Pesanan <i class="fas fa-whatsapp"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- MODAL 2: FORUM BOOKING TEMPAT -->
    <div id="bookingModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 style="margin:0; font-size:1.2rem;">Reservasi Meja/Ruangan</h3>
                <button class="close-btn" onclick="closeModal('bookingModal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="whatsappBookingForm">
                    <div class="form-group">
                        <label for="bookingName">Nama Pemesan</label>
                        <input type="text" id="bookingName" class="form-control" placeholder="Nama Anda" required>
                    </div>

                    <div class="form-group">
                        <label for="roomType">Pilihan Ruangan</label>
                        <select id="roomType" class="form-select" required>
                            <option value="" disabled selected>-- Pilih Ruangan --</option>
                            <option value="Ruang Regular">Ruang Regular</option>
                            <option value="Ruang VIP">Ruang VIP</option>
                            <option value="Ruang VVIP">Ruang VVIP</option>
                            <option value="Premium Lounge">Premium Lounge</option>
                        </select>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label for="bookingDate">Tanggal</label>
                            <input type="date" id="bookingDate" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="bookingTime">Jam</label>
                            <input type="time" id="bookingTime" class="form-control" required>
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="guests">Jumlah Orang</label>
                        <input type="number" id="guests" class="form-control" min="1" placeholder="Contoh: 4" required>
                    </div>

                    <div class="form-group">
                        <label for="bookingNotes">Catatan Khusus (Opsional)</label>
                        <textarea id="bookingNotes" class="form-control" rows="2" placeholder="Contoh: Ulang tahun, dekorasi balon..."></textarea>
                    </div>

                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-calendar-check"></i> Kirim Reservasi
                    </button>
                </form>
            </div>
        </div>
    </div>

    <script>
        // --- DATA KERANJANG (CART) ---
        let orderCart = [];
        let savedCustomerName = "";
        let currentFormItem = {}; 

        // 1. MOBILE MENU TOGGLE
        function toggleMenu() {
            const nav = document.getElementById('navLinks');
            const icon = document.getElementById('menuIcon');
            nav.classList.toggle('active');
            
            if(nav.classList.contains('active')){
                icon.classList.remove('fa-bars');
                icon.classList.add('fa-times');
            } else {
                icon.classList.remove('fa-times');
                icon.classList.add('fa-bars');
            }
        }

        // 2. SCROLL REVEAL
        const observerOptions = { threshold: 0.15, rootMargin: "0px 0px -50px 0px" };
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('active');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);
        document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

        // 3. NAVBAR SCROLL
        window.addEventListener('scroll', function() {
            const header = document.getElementById('navbar');
            header.classList.toggle('scrolled', window.scrollY > 50);
        });

        // 4. TOAST
        function showToast(message) {
            const toast = document.getElementById('toast');
            document.getElementById('toastMsg').textContent = message;
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3000);
        }

        // 5. MODAL LOGIC
        function closeModal(modalId) {
            const modal = document.getElementById(modalId);
            modal.classList.remove('show');
            setTimeout(() => { modal.style.display = "none"; }, 300);
            document.body.style.overflow = "auto";
            
            // Reset Form jika modal ditutup
            if(modalId === 'orderModal') {
                document.getElementById('order-step-1').style.display = 'block';
                document.getElementById('order-step-2').style.display = 'none';
                document.getElementById('orderFormStep1').reset();
            }
        }

        function openOrderModal(menuItem) {
            const modal = document.getElementById("orderModal");
            document.getElementById("menuName").value = menuItem;
            
            if(savedCustomerName) {
                document.getElementById("customerName").value = savedCustomerName;
            }
            
            // Reset jumlah & notes untuk menu baru
            document.getElementById("quantity").value = 1;
            document.getElementById("notes").value = "";
            
            modal.style.display = "flex";
            setTimeout(() => modal.classList.add('show'), 10);
            document.body.style.overflow = "hidden";
        }

        function openBookingModal(roomType) {
            const modal = document.getElementById("bookingModal");
            if(roomType) {
                const select = document.getElementById("roomType");
                select.value = roomType;
            }
            modal.style.display = "flex";
            setTimeout(() => modal.classList.add('show'), 10);
            document.body.style.overflow = "hidden";
        }

        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                closeModal(event.target.id);
            }
        }

        // --- LOGIKA MULTI-STEP FORM ---

        // FUNGSI 1: Beli Lagi (Tambah ke Cart & TETAP DI FORM)
        function addToCart() {
            const name = document.getElementById('customerName').value;
            const menu = document.getElementById('menuName').value;
            const qty = document.getElementById('quantity').value;
            const notes = document.getElementById('notes').value;

            if (!name) {
                showToast('Mohon isi Nama Pemesan terlebih dahulu.');
                return;
            }
            if (!menu) {
                showToast('Terjadi kesalahan data menu.');
                return;
            }

            // Simpan Nama agar tidak perlu ketik ulang di order selanjutnya
            savedCustomerName = name;

            // Tambah ke array keranjang
            orderCart.push({
                menu: menu,
                qty: qty,
                notes: notes
            });

            showToast(`"${menu}" (${qty} pcs) berhasil ditambahkan.`);

            // MODIFIKASI: Reset field form TANPA menutup modal
            document.getElementById("quantity").value = 1;
            document.getElementById("notes").value = "";
            
            // Kembali fokus ke jumlah agar user bisa input lagi
            document.getElementById("quantity").focus();
        }

        // FUNGSI 2: Lanjut Beli (Pindah ke Step 2)
        function goToStep2() {
            const name = document.getElementById('customerName').value;
            const menu = document.getElementById('menuName').value;
            const qty = document.getElementById('quantity').value;
            const notes = document.getElementById('notes').value;

            if (!name) {
                showToast('Mohon isi Nama Pemesan terlebih dahulu.');
                return;
            }
            if (!menu) {
                showToast('Terjadi kesalahan data menu.');
                return;
            }

            savedCustomerName = name;
            
            // Siapkan data untuk dikirim (Gabungan Cart + Item Saat Ini)
            let itemsToDisplay = [...orderCart];
            
            // Item form saat ini dianggap sebagai item terakhir yang akan dibayar
            const currentItem = { menu: menu, qty: qty, notes: notes };
            itemsToDisplay.push(currentItem);

            // Simpan referensi item terakhir untuk pengiriman WA nanti
            currentFormItem = currentItem;

            // Generate Ringkasan HTML
            const summaryBox = document.getElementById('orderSummaryBox');
            let summaryHTML = `<div class="summary-item"><strong>Total Menu:</strong> ${itemsToDisplay.length} item</div><hr style="border:0; border-top:1px dashed #ccc; margin:10px 0;">`;
            
            itemsToDisplay.forEach((item, index) => {
                summaryHTML += `
                    <div class="summary-item">
                        <span>${item.menu} x${item.qty}</span>
                    </div>
                `;
                if(item.notes) {
                    summaryHTML += `<span class="summary-notes">Catatan: ${item.notes}</span>`;
                }
            });

            summaryBox.innerHTML = summaryHTML;

            // Switch View
            document.getElementById('order-step-1').style.display = 'none';
            document.getElementById('order-step-2').style.display = 'block';
        }

        // FUNGSI 3: Kembali ke Step 1
        function backToStep1() {
            document.getElementById('order-step-2').style.display = 'none';
            document.getElementById('order-step-1').style.display = 'block';
        }

        // FUNGSI 4: Kirim Pesanan Akhir
        function sendFinalOrder() {
            const paymentMethod = document.getElementById('paymentMethod').value;
            
            if(!paymentMethod) {
                showToast('Mohon pilih Metode Pembayaran.');
                return;
            }

            // Gabungkan Cart + Item Form Saat Ini
            let finalItems = [...orderCart];
            finalItems.push(currentFormItem);

            let message = `Halo Kopi Senja, saya ingin memesan:%0A%0A?? *Nama:* ${savedCustomerName}%0A`;
            
            finalItems.forEach((item, index) => {
                message += `----------------%0A`;
                message += `? *Menu ${index+1}:* ${item.menu}%0A`;
                message += `?? *Jumlah:* ${item.qty} pcs%0A`;
                if (item.notes) message += `?? *Catatan:* ${item.notes}%0A`;
            });

            message += `----------------%0A`;
            message += `?? *Metode Pembayaran:* ${paymentMethod}%0A`;
            message += `%0AMohon diproses ya! Terima kasih.`;

            showToast('Mengarahkan ke WhatsApp...');
            setTimeout(() => {
                window.open(`https://wa.me/628888299000?text=${message}`, '_blank');
                
                // Reset Data setelah kirim
                orderCart = [];
                savedCustomerName = "";
                currentFormItem = {};
                document.getElementById('orderFormStep1').reset();
                closeModal('orderModal');
            }, 1000);
        }

        // 6. HANDLER BOOKING RUANGAN
        document.getElementById('whatsappBookingForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('bookingName').value;
            const room = document.getElementById('roomType').value;
            const date = document.getElementById('bookingDate').value;
            const time = document.getElementById('bookingTime').value;
            const guests = document.getElementById('guests').value;
            const notes = document.getElementById('bookingNotes').value;

            let message = `Halo Kopi Senja, saya ingin reservasi tempat:%0A%0A`;
            message += `?? *Nama:* ${name}%0A`;
            message += `?? *Ruangan:* ${room}%0A`;
            message += `?? *Tanggal:* ${date}%0A`;
            message += `? *Jam:* ${time}%0A`;
            message += `?? *Jumlah Orang:* ${guests} orang%0A`;
            if(notes) message += `?? *Catatan:* ${notes}%0A`;
            message += `%0AMohon konfirmasi ketersediaan tempat. Terima kasih.`;

            showToast('Mengirim data reservasi...');
            setTimeout(() => {
                window.open(`https://wa.me/628888299000?text=${message}`, '_blank');
                this.reset();
                closeModal('bookingModal');
            }, 1000);
        });
    </script>
</body>
</html>
