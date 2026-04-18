<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>روايات ذوالفقار</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* تعريف الألوان (الوضع الفاتح والداكن) */
        :root {
            --bg: #f8f9fa; --text: #2d3436; --card: #ffffff; --primary: #e67e22; --nav: #ffffff;
        }
        [data-theme="dark"] {
            --bg: #121212; --text: #dfe6e9; --card: #1e1e1e; --nav: #1e1e1e;
        }

        body {
            font-family: 'Cairo', sans-serif; background: var(--bg); color: var(--text);
            margin: 0; padding-bottom: 80px; transition: 0.3s;
        }

        /* رأس الصفحة */
        header {
            padding: 20px; display: flex; justify-content: space-between; align-items: center;
            background: var(--card); box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .logo { font-size: 22px; font-weight: bold; color: var(--primary); }

        /* قسم القصص (التحريك الأفقي مثل الصور التي أرسلتها) */
        .section-title { padding: 20px 20px 10px; font-size: 18px; font-weight: bold; }
        
        .story-container {
            display: flex; overflow-x: auto; padding: 10px 20px; gap: 15px;
            scrollbar-width: none; /* إخفاء شريط التمرير */
        }

        .story-card {
            min-width: 140px; background: var(--card); border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1); overflow: hidden; transition: 0.3s;
        }

        .story-card img { width: 100%; height: 200px; object-fit: cover; }
        
        .story-info { padding: 10px; text-align: center; font-size: 14px; }

        /* شريط التنقل السفلي */
        .bottom-nav {
            position: fixed; bottom: 0; width: 100%; background: var(--nav);
            display: flex; justify-content: space-around; padding: 12px 0;
            border-top: 1px solid rgba(0,0,0,0.1); box-shadow: 0 -2px 10px rgba(0,0,0,0.05);
        }

        .nav-item { cursor: pointer; opacity: 0.6; font-size: 12px; text-align: center; }
        .nav-item.active { opacity: 1; color: var(--primary); font-weight: bold; }

        /* زر الوضع الليلي */
        .toggle-btn {
            background: var(--primary); color: white; border: none;
            padding: 8px 16px; border-radius: 25px; cursor: pointer; font-family: 'Cairo';
        }
    </style>
</head>
<body id="body">

<header>
    <div class="logo">روايات ذوالفقار</div>
    <button class="toggle-btn" onclick="toggleDarkMode()">الوضع الليلي</button>
</header>

<div class="section-title">أحدث القصص المختارة</div>

<div class="story-container">
    <div class="story-card">
        <img src="https://i.postimg.cc/XvBw1N6s/cover1.jpg" alt="نور وصقر">
        <div class="story-info">نور وصقر</div>
    </div>
    <div class="story-card">
        <img src="https://i.postimg.cc/Kz8p7XWd/cover2.jpg" alt="قصة 2">
        <div class="story-info">غبار الزمن</div>
    </div>
    <div class="story-card">
        <img src="https://i.postimg.cc/MZsH5T9h/cover3.jpg" alt="قصة 3">
        <div class="story-info">نهوة قلم</div>
    </div>
</div>

<div class="section-title">الأكثر قراءة هذا الأسبوع</div>
<div style="padding: 0 20px; opacity: 0.7;">قريباً سيتم إضافة المزيد من الفصول...</div>

<nav class="bottom-nav">
    <div class="nav-item active">🏠<br>الرئيسية</div>
    <div class="nav-item">📖<br>مكتبتي</div>
    <div class="nav-item">👤<br>حسابي</div>
</nav>

<script>
    function toggleDarkMode() {
        const body = document.getElementById('body');
        const currentTheme = body.getAttribute('data-theme');
        if (currentTheme === 'dark') {
            body.removeAttribute('data-theme');
        } else {
            body.setAttribute('data-theme', 'dark');
        }
    }
</script>

</body>
</html>
