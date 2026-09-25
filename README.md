
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Masria | Portofolio Atlet Bulutangkis</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* Reset & Variabel */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        :root {
            --primary-color: #e63946; /* Merah enerjik */
            --secondary-color: #1d3557; /* Biru gelap */
            --text-color: #333;
            --bg-light: #f1faee;
            --white: #fff;
        }

        body {
            font-family: 'Poppins', sans-serif;
            color: var(--text-color);
            line-height: 1.6;
        }

        /* Navigasi */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 20px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: transparent;
            transition: 0.4s;
            z-index: 1000;
        }

        nav.scrolled {
            background: var(--secondary-color);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--white);
        }

        .nav-links {
            list-style: none;
            display: flex;
            gap: 20px;
        }

        .nav-links a {
            color: var(--white);
            text-decoration: none;
            font-weight: 600;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--primary-color);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(rgba(29, 53, 87, 0.8), rgba(29, 53, 87, 0.8)), url('https://images.unsplash.com/photo-1626224583764-f87db24ac4ea?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80') center/cover;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: var(--white);
            padding: 0 20px;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 10px;
        }

        .highlight {
            color: var(--primary-color);
        }

        .hero h2 {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 20px;
        }

        .hero p {
            max-width: 600px;
            margin: 0 auto 30px;
        }

        /* Tombol */
        .btn {
            display: inline-block;
            padding: 12px 30px;
            background: var(--primary-color);
            color: var(--white);
            text-decoration: none;
            border-radius: 25px;
            font-weight: 600;
            transition: 0.3s;
            border: 2px solid var(--primary-color);
        }

        .btn:hover {
            background: transparent;
            color: var(--primary-color);
        }

        .btn-outline {
            background: transparent;
            color: var(--secondary-color);
            border-color: var(--secondary-color);
            margin: 0 10px;
        }

        .btn-outline:hover {
            background: var(--secondary-color);
            color: var(--white);
        }

        /* Bagian Umum */
        .section {
            padding: 80px 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 50px;
            color: var(--secondary-color);
            position: relative;
        }

        .section-title::after {
            content: '';
            width: 60px;
            height: 4px;
            background: var(--primary-color);
            display: block;
            margin: 10px auto 0;
            border-radius: 2px;
        }

        .bg-light {
            background: var(--bg-light);
        }

        .text-center {
            text-align: center;
        }

        /* Timeline Prestasi */
        .timeline {
            position: relative;
            border-left: 4px solid var(--primary-color);
            padding-left: 30px;
            margin-left: 20px;
        }

        .timeline-item {
            margin-bottom: 30px;
            position: relative;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -41px;
            top: 5px;
            width: 18px;
            height: 18px;
            background: var(--white);
            border: 4px solid var(--primary-color);
            border-radius: 50%;
        }

        .timeline-item h3 {
            color: var(--secondary-color);
            margin-bottom: 5px;
        }

        /* Galeri Foto */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .gallery-item {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            aspect-ratio: 4 / 3;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            cursor: pointer;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s ease;
        }

        .gallery-item:hover img {
            transform: scale(1.1);
        }

        .gallery-overlay {
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: rgba(29, 53, 87, 0.7);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.3s ease;
            color: white;
            font-weight: 600;
            font-size: 1.2rem;
        }

        .gallery-item:hover .gallery-overlay {
            opacity: 1;
        }

        /* Modal Lightbox */
        .modal {
            display: none; 
            position: fixed; 
            z-index: 2000; 
            left: 0;
            top: 0;
            width: 100%; 
            height: 100%; 
            overflow: auto; 
            background-color: rgba(0,0,0,0.9);
            backdrop-filter: blur(5px);
        }

        .modal-content {
            margin: auto;
            display: block;
            max-width: 90%;
            max-height: 90vh;
            margin-top: 5vh;
            border-radius: 8px;
            animation: zoom 0.3s ease;
        }

        @keyframes zoom {
            from {transform:scale(0)} 
            to {transform:scale(1)}
        }

        .close {
            position: absolute;
            top: 20px;
            right: 40px;
            color: #f1f1f1;
            font-size: 40px;
            font-weight: bold;
            transition: 0.3s;
            cursor: pointer;
        }

        .close:hover,
        .close:focus {
            color: var(--primary-color);
        }

        /* Footer */
        footer {
            background: var(--secondary-color);
            color: var(--white);
            text-align: center;
            padding: 20px;
        }

        /* Responsif */
        @media (max-width: 768px) {
            nav {
                padding: 15px 20px;
                flex-direction: column;
                background: var(--secondary-color);
            }
            .nav-links {
                margin-top: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            .hero h1 { font-size: 2.5rem; }
        }
    </style>
</head>
<body>

    <!-- Navigasi -->
    <nav id="navbar">
        <div class="logo">Masria.</div>
        <ul class="nav-links">
            <li><a href="#home">Beranda</a></li>
            <li><a href="#about">Tentang</a></li>
            <li><a href="#prestasi">Prestasi</a></li>
            <li><a href="#galeri">Galeri</a></li>
            <li><a href="#kontak">Kontak</a></li>
        </ul>
    </nav>

    <!-- Beranda / Hero Section -->
    <header id="home" class="hero">
        <div class="hero-content">
            <h1>Halo, Saya <span class="highlight">Masria</span></h1>
            <h2>Atlet Bulutangkis Profesional dari Tolitoli</h2>
            <p>Berdedikasi, pantang menyerah, dan selalu memberikan yang terbaik di setiap pertandingan di atas lapangan.</p>
            <a href="#prestasi" class="btn">Lihat Prestasi</a>
        </div>
    </header>

    <!-- Tentang Saya -->
    <section id="about" class="section animate-on-scroll">
        <div class="container">
            <h2 class="section-title">Tentang Saya</h2>
            <div class="about-content">
                <div class="about-text text-center">
                    <p>Saya adalah seorang atlet bulutangkis yang lahir dan besar di <strong>Tolitoli, Sulawesi Tengah</strong>. Sejak usia dini, lapangan bulutangkis telah menjadi rumah kedua saya. Melalui disiplin dan latihan keras, saya telah berkompetisi di berbagai tingkat turnamen dan meraih berbagai gelar juara.</p>
                    <p style="margin-top: 15px;">Fokus utama saya adalah bermain di sektor tunggal/ganda, dengan gaya permainan menyerang dan kecepatan kaki yang menjadi andalan saya di lapangan.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Prestasi -->
    <section id="prestasi" class="section bg-light animate-on-scroll">
        <div class="container">
            <h2 class="section-title">Daftar Juara & Prestasi</h2>
            <div class="timeline">
                <div class="timeline-item">
                    <h3>Juara 1 - Kejuaraan Daerah (Kejurda) Sulteng</h3>
                    <p>Medali Emas kategori Tunggal Putri/Putra tingkat provinsi.</p>
                </div>
                <div class="timeline-item">
                    <h3>Medali Emas - Bupati Cup Tolitoli</h3>
                    <p>Meraih posisi pertama dalam turnamen tahunan tingkat kabupaten.</p>
                </div>
                <div class="timeline-item">
                    <h3>Juara 1 - Open Tournament Regional Sulawesi</h3>
                    <p>Mengalahkan pemain unggulan dari berbagai provinsi di Sulawesi.</p>
                </div>
                <div class="timeline-item">
                    <h3>Pemain Terbaik (MVP) - Liga Badminton Antar Klub</h3>
                    <p>Dianugerahi sebagai pemain dengan performa paling konsisten sepanjang liga.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Galeri Foto -->
    <section id="galeri" class="section animate-on-scroll">
        <div class="container">
            <h2 class="section-title">Galeri Aksi</h2>
            <div class="gallery-grid">
                <!-- Foto 1 -->
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1626224583764-f87db24ac4ea?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Aksi Lapangan 1">
                    <div class="gallery-overlay">Lihat Foto</div>
                </div>
                <!-- Foto 2 -->
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1599474924187-334a4ae5bd3c?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Aksi Lapangan 2">
                    <div class="gallery-overlay">Lihat Foto</div>
                </div>
                <!-- Foto 3 -->
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1611250282006-4484dd3fba6b?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Turnamen">
                    <div class="gallery-overlay">Lihat Foto</div>
                </div>
                <!-- Foto 4 -->
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1521537634581-0dced2fee2ef?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Latihan">
                    <div class="gallery-overlay">Lihat Foto</div>
                </div>
                <!-- Foto 5 -->
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1579952363873-27f3bade9f55?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Peralatan">
                    <div class="gallery-overlay">Lihat Foto</div>
                </div>
                <!-- Foto 6 -->
                <div class="gallery-item">
                    <img src="https://images.unsplash.com/photo-1605335198124-74737d995c76?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80" alt="Medali & Selebrasi">
                    <div class="gallery-overlay">Lihat Foto</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Modal Lightbox -->
    <div id="imageModal" class="modal">
        <span class="close">&times;</span>
        <img class="modal-content" id="modalImage">
    </div>

    <!-- Kontak -->
    <section id="kontak" class="section bg-light animate-on-scroll">
        <div class="container text-center">
            <h2 class="section-title">Mari Bekerja Sama</h2>
            <p>Untuk undangan turnamen, tawaran sponsor, atau kolaborasi, silakan hubungi saya melalui email atau media sosial.</p>
            <div class="contact-buttons" style="margin-top: 25px;">
                <a href="mailto:emailmasria@contoh.com" class="btn btn-outline">Kirim Email</a>
                <a href="https://instagram.com" class="btn btn-outline" target="_blank">Instagram</a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 Masria - Atlet Bulutangkis Tolitoli. Dibuat untuk GitHub Pages.</p>
    </footer>

    <!-- Script Javascript -->
    <script>
        // Efek mengubah warna latar belakang navigasi saat di-scroll
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Animasi muncul perlahan untuk elemen saat di-scroll
        const observerOptions = {
            root: null,
            rootMargin: '0px',
            threshold: 0.15
        };

        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.animate-on-scroll, .timeline-item, .gallery-item').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'all 0.6s ease-out';
            observer.observe(el);
        });

        // Logika untuk Modal / Lightbox Galeri
        const modal = document.getElementById("imageModal");
        const modalImg = document.getElementById("modalImage");
        const closeBtn = document.getElementsByClassName("close")[0];
        const galleryItems = document.querySelectorAll('.gallery-item img');

        // Buka modal saat gambar diklik
        galleryItems.forEach(img => {
            img.parentElement.addEventListener('click', function() {
                modal.style.display = "block";
                modalImg.src = img.src; // Ambil sumber gambar yang diklik
            });
        });

        // Tutup modal saat tombol 'x' diklik
        closeBtn.onclick = function() { 
            modal.style.display = "none";
        }

        // Tutup modal saat area gelap di luar gambar diklik
        modal.onclick = function(event) {
            if (event.target === modal) {
                modal.style.display = "none";
            }
        }
    </script>
</body>
</html>
```
