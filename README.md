# TAKARIN

**TAKARIN** adalah aplikasi web khusus untuk membantu pengguna merencanakan menu makanan yang sehat, hemat, dan minim limbah makanan. Berbeda dari aplikasi resep konvensional, TAKARIN memulai perencanaan dari anggaran dan stok bahan yang sudah tersedia, kemudian menyusun rekomendasi menu untuk hari-hari selanjutnya.

## Anggota Kelompok

| Nama | NPM |
| --- | --- |
| Alfredo Nathaniel Putra Harsono | 2506656412 |
| Alena Aura Deviyana | 2506656394 |
| Aiko Zahwa | 2506617140 |
| Attar Rais Hakam | 2506656495 |
| Rajendra Akbar Mahdiansyah | 2506596874 |

## Latar Belakang dan Value Proposition

### Visi

TAKARIN bertujuan mendukung pola konsumsi pangan yang terencana, efisien secara finansial, dan ramah lingkungan. Aplikasi ini ingin membuat pola makan sehat yang terjangkau lebih mudah diakses masyarakat Indonesia tanpa menyisakan bahan makanan yang terbuang.

### Masalah yang Diselesaikan

- **Food waste rumah tangga:** bahan makanan terlupakan, kedaluwarsa, atau membusuk karena pengguna tidak tahu kapan harus mengolahnya.
- **Budget belanja tidak efisien:** pengguna kesulitan membagi anggaran makan harian atau mingguan secara realistis.
- **Nutrisi terabaikan demi hemat:** penghematan sering dilakukan dengan mengorbankan kualitas gizi.
- **Resep kurang fleksibel:** banyak aplikasi resep mengharuskan pengguna membeli bahan baru yang mahal atau tidak sesuai dengan kebiasaan masak lokal.

### Target Pengguna

- Mahasiswa dan anak kos yang membutuhkan menu bergizi dengan anggaran terbatas.
- Keluarga muda yang ingin mengoptimalkan pengeluaran dapur dan isi kulkas.
- Konsumen yang peduli lingkungan dan ingin mengurangi limbah makanan.

### Cara TAKARIN Membantu

- **Ketika belum berbelanja:** pengguna menentukan budget dan target gizi, lalu TAKARIN memberi saran bahan belanja serta menu.
- **Ketika sudah berbelanja:** pengguna memindai bahan atau struk, lalu TAKARIN memanfaatkan stok tersebut untuk menyusun menu dan mencegah bahan terbuang.

## Perbandingan dengan Aplikasi Serupa

| Aspek | Cookpad (Indonesia) | SuperCook (Global) | Mealime (Global) | TAKARIN |
| --- | --- | --- | --- | --- |
| Fokus utama | Komunitas dan resep | Pencocokan bahan dan resep | Perencanaan menu | Optimasi anggaran dan zero waste |
| Alur utama | Cari resep → beli bahan | Pilih bahan → dapat resep | Pilih menu → shopping list | Input budget → belanja + menu, atau scan stok → menu |
| Konteks bahan Indonesia | Ya | Terbatas | Terbatas | Ya, termasuk bahan dan bumbu lokal |
| Perencanaan anggaran | Tidak | Tidak | Terbatas/premium | Ya, berdasarkan target gizi dan durasi makan |
| Pemindaian bahan/struk | Tidak | Barcode terbatas | Tidak | Ya, melalui foto bahan atau struk |
| Prioritas bahan kedaluwarsa | Tidak | Tidak | Tidak | Ya, berbasis masa simpan dan cuaca |
| Meal scheduler | Tidak | Tidak | Manual | Otomatis untuk 3–5 hari |

## Pembagian Modul

### Modul 1 — Smart Budget Meal Planner

**PIC:** Alfredo Nathaniel Putra Harsono

Pengguna memasukkan nominal budget, jumlah hari atau porsi makan, serta target gizi. Sistem menghasilkan rekomendasi bahan yang perlu dibeli, estimasi biaya, dan rencana menu untuk beberapa hari ke depan.

### Modul 2 — Smart Pantry & Meal Planner

**PIC:** Rajendra Akbar Mahdiansyah

Pengguna dapat memasukkan stok melalui foto bahan makanan atau foto struk belanja. Sistem menyimpan bahan ke Virtual Pantry, memperkirakan masa simpannya berdasarkan jenis bahan dan kondisi cuaca, lalu membuat rekomendasi menu dari stok yang tersedia dengan prioritas bahan yang cepat rusak.

### Modul 3 — User Account & Food Preference

**PIC:** Attar Rais Hakam

Mengelola register, login, logout, profil pengguna, serta preferensi makanan. Pengguna dapat memilih target diet, mencatat alergi, dan menentukan preferensi seperti halal. Data ini menjadi acuan bagi Smart Budget Meal Planner dan Smart Pantry & Meal Planner.

### Modul 4 — Recipe Book & Cooking Tracker

**PIC:** Alena Aura Deviyana

Menyediakan daftar dan detail resep yang dapat direkomendasikan oleh sistem. Pengguna dapat mencari resep, menyimpan resep favorit, dan menekan tombol **Sudah Masak**. Setelah memasak, bahan yang digunakan dikurangi dari Virtual Pantry.

### Modul 5 — Eco-Savings Dashboard & Market Locator

**PIC:** Aiko Zahwa

Menampilkan estimasi uang yang dihemat, jumlah bahan yang berhasil digunakan sebelum rusak, dan perkiraan pengurangan limbah makanan. Modul ini juga menyediakan pencarian pasar tradisional atau bank sampah terdekat melalui peta.

## Public API

| API | Kegunaan di TAKARIN |
| --- | --- |
| [Open-Meteo Forecast API](https://open-meteo.com/en/docs) | Mengambil suhu dan kelembapan berdasarkan lokasi pengguna untuk menyesuaikan estimasi masa simpan bahan di Virtual Pantry. |
| [USDA FoodData Central API](https://fdc.nal.usda.gov/api-guide/) | Mengambil data gizi generik, seperti kalori, protein, dan serat, untuk bahan mentah sebagai acuan Smart Budget Meal Planner. API key disimpan sebagai environment variable. |
| [Open Food Facts API](https://openfoodfacts.github.io/documentation/docs/Product-Opener/api/) | Mengambil informasi produk kemasan berdasarkan barcode, termasuk nama produk dan data nutrisi. Data bahan mentah lokal tetap memiliki fallback ke data internal. |
| [TheMealDB API](https://www.themealdb.com/docs_api_guide.php) | Menjadi pelengkap variasi resep internasional. Database resep internal tetap menjadi sumber utama karena cakupan resep Indonesia pada API ini terbatas. |
| [OpenStreetMap](https://www.openstreetmap.org/) — Nominatim dan Overpass | Mendukung geocoding serta pencarian pasar tradisional atau bank sampah terdekat. |

## Teknologi dan Data Pendukung

| Teknologi / Data | Kegunaan di TAKARIN |
| --- | --- |
| [Tesseract.js](https://github.com/naptha/tesseract.js) | OCR untuk membaca teks pada foto struk belanja. Tesseract.js dijalankan sebagai library, bukan Public API. |
| [Hugging Face Inference](https://huggingface.co/docs/inference-providers/tasks/image-classification) | Klasifikasi foto bahan makanan. Sistem akan menampilkan beberapa tebakan bahan agar pengguna dapat mengonfirmasi hasilnya. |

## Peran Pengguna

| Peran | Hak Akses |
| --- | --- |
| Guest | Mengakses landing page, informasi fitur, dan simulasi sederhana budget/nutrisi. |
| Registered User | Mengelola budget planner, Virtual Pantry, ScanStok, jadwal menu, resep favorit, dan dashboard pribadi. |
| Administrator | Mengelola master bahan, harga referensi, serta database resep masakan Indonesia. |

## Deployment dan Desain

- **PWS:** [https://alfredo-nathaniel-takarin.pws.cs.ui.ac.id](https://alfredo-nathaniel-takarin.pws.cs.ui.ac.id)
- **Figma:** [Desain TAKARIN](https://www.figma.com/design/GbnAebmRymsFjgLebkKmUJ/PBPUY?node-id=0-1&t=6YqR0aO6YTlJA2SH-1)
