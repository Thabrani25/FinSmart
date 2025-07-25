<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>FinSmart - Keuangan Mahasiswa</title>
  <style>
:root {
  --primary: #4cb4f5;
  --secondary: #a3f7bf;
  --bg: #f0f5fa;
  --text: #333;
  --card-bg: #ffffff;
  --radius: 16px;
  --shadow: 0 4px 12px rgba(0,0,0,0.05);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', sans-serif;
}

body {
  background: var(--bg);
  color: var(--text);
  display: flex;
  flex-direction: column;
  height: 100vh;
  overflow-x: hidden;
}

header {
  background: linear-gradient(90deg, var(--primary), var(--secondary));
  padding: 16px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom-left-radius: var(--radius);
  border-bottom-right-radius: var(--radius);
  box-shadow: var(--shadow);
  color: white;
}

.logo-app {
  display: flex;
  align-items: center;
  gap: 12px;
}

.logo-app img {
  width: 36px;
  height: 36px;
  filter: brightness(0) invert(1);
}

.logo-app span {
  font-size: 22px;
  font-weight: 600;
}

.user-photo img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 2px solid #fff;
}

.content {
  flex: 1;
  padding: 20px;
  overflow-y: auto;
}

.grid-menu {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
  margin-top: 10px;
}

.menu-card {
  background: var(--card-bg);
  border-radius: var(--radius);
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: var(--shadow);
  transition: 0.2s ease;
  cursor: pointer;
}

.menu-card:hover {
  transform: translateY(-3px);
  background: #ebf9ff;
}

.menu-card i {
  font-size: 28px;
  color: var(--primary);
  margin-bottom: 8px;
}

.menu-card span {
  font-weight: 500;
  font-size: 15px;
}

.card {
  background: var(--card-bg);
  border-radius: var(--radius);
  padding: 18px;
  margin-top: 28px;
  box-shadow: var(--shadow);
}

input, select, textarea {
  width: 100%;
  padding: 12px;
  margin-top: 10px;
  margin-bottom: 18px;
  border: 1px solid #ddd;
  border-radius: var(--radius);
  background: #fff;
}

button.submit-btn {
  background-color: var(--primary);
  color: white;
  border: none;
  padding: 12px;
  width: 100%;
  border-radius: var(--radius);
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: 0.2s ease;
}

button.submit-btn:hover {
  background-color: #38a3e0;
}

.nav-bar {
  display: flex;
  justify-content: space-around;
  background-color: var(--card-bg);
  border-top: 1px solid #ddd;
  padding: 10px 0;
  position: fixed;
  bottom: 0;
  width: 100%;
  z-index: 10;
  box-shadow: 0 -1px 8px rgba(0,0,0,0.03);
}

.nav-bar button {
  background: none;
  border: none;
  color: #777;
  font-size: 13px;
  display: flex;
  flex-direction: column;
  align-items: center;
  cursor: pointer;
  transition: 0.2s;
}

.nav-bar button i {
  font-size: 18px;
  margin-bottom: 4px;
}

.nav-bar button.active {
  color: var(--primary);
  font-weight: bold;
}

.hidden {
  display: none;
}

.profile-info p {
  margin-bottom: 8px;
  font-size: 15px;
}

  </style>
</head>
<body>

  <header>
    <div class="logo-app">
        <span><h3>FinSmart</h3></span>
    </div>
    <div class="user-photo">
    </div>
  </header>

  <div class="content">
    <!-- Dashboard -->
    <div id="dashboard" class="page">
      <div class="grid-menu">
        <div class="menu-card" onclick="navigateTo('input')">
          <i>➕</i>
          <span>Tambah Pengeluaran</span>
        </div>
        <div class="menu-card" onclick="navigateTo('transaksi')">
          <i>💰</i>
          <span>Transaksi</span>
        </div>
        <div class="menu-card">
          <i>📊</i>
          <span>Ringkasan Bulan Ini</span>
        </div>
        <div class="menu-card" onclick="navigateTo('profil')">
          <i>👤</i>
          <span>Profil</span>
        </div>
      </div>

      <div class="card">
        <h3>Saldo Saat Ini</h3>
        <p>Rp. 1.500.000</p>
      </div>
    </div>

    <!-- Transaksi -->
    <div id="transaksi" class="page hidden">
      <div class="card">
        <h3>Histori Transaksi</h3>
        <ul>
          <li>📥 Uang Saku - Rp. 50.000</li>
          <li>📤 Beli Buku - Rp. 30.000</li>
          <li>📤 Jajan - Rp. 20.000</li>
        </ul>
      </div>
    </div>

    <!-- Input Pengeluaran -->
    <div id="input" class="page hidden">
      <div class="card">
        <h3>Input Pengeluaran</h3>
        <form id="formPengeluaran">
          <label>Deskripsi</label>
          <input type="text" name="deskripsi" placeholder="Contoh: Beli Pulpen" required>

          <label>Jumlah</label>
          <input type="number" name="jumlah" placeholder="Contoh: 5000" required>

          <label>Tanggal</label>
          <input type="date" name="tanggal" required>

          <button type="submit" class="submit-btn">Simpan</button>
        </form>
      </div>
    </div>

    <!-- Profil -->
    <div id="profil" class="page hidden">
      <div class="card profile-info">
        <h3>Profil Mahasiswa</h3>
        <p><strong>Nama:</strong> ARISKI NIKMAN GADING</p>
        <p><strong>Kelas:</strong> HE22X</p>
        <p><strong>NIM</strong> 0711522016</p>
      </div>
    </div>
  </div>

  <!-- Navigasi Bawah -->
  <nav class="nav-bar">
    <button class="nav-btn active" data-page="dashboard">🏠<span>Dashboard</span></button>
    <button class="nav-btn" data-page="transaksi">💰<span>Transaksi</span></button>
    <button class="nav-btn" data-page="input">➕<span>Input</span></button>
    <button class="nav-btn" data-page="profil">👤<span>Profil</span></button>
  </nav>

  <script>
    const navButtons = document.querySelectorAll('.nav-btn');
    const pages = document.querySelectorAll('.page');

    function navigateTo(page) {
      pages.forEach(p => p.classList.add('hidden'));
      document.getElementById(page).classList.remove('hidden');
      navButtons.forEach(btn => btn.classList.remove('active'));
      document.querySelector(`.nav-btn[data-page="${page}"]`)?.classList.add('active');
    }

    navButtons.forEach(button => {
      button.addEventListener('click', () => {
        const page = button.getAttribute('data-page');
        navigateTo(page);
      });
    });

    const form = document.getElementById('formPengeluaran');
    form.addEventListener('submit', function (e) {
      e.preventDefault();
      alert("Pengeluaran berhasil disimpan!");
      form.reset();
      navigateTo('dashboard');
    });
  </script>

</body>
</html>

