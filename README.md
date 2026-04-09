## Ringkasan Proyek

Dalam pembangunan ruang pamer etalase produk bunga di `4_GridLayoutApp`, kerangka
antarmuka dieksekusi mematuhi arsitektur **GridLayout**. Menyimpang dari metode kaku
untaian berkalang vertikal/horizontal biasa, Grid membentuk belahan parit silang
kisi matriks presisi (contoh: 2 baris *x* 2 kolom). Elemen produk kartu gambar 
Anggrek maupun Mawar secara kodrati disisipkan berjajar menghabiskan ruas horizontal
batas indeks layar, lantas banting setir tersusun terjun serentak merangkai sepetak
barisan baru tatkala kuota lorong terisi genap, mereproduksi perilaku beranda toko
komersial pada umumnya.

## Dokumentasi Teknis

### 1. Penjelasan File Resource Pendukung

Antarmuka pajangan grid tak lantas puas menggunakan pewarnaan konvensional, tapi
melibatkan asupan benda material rakitan dari OS Android yaitu `MaterialCardView`.

-   **Fungsinya:** Objek utilitas istimewa turunan Pustaka Material Google ini
    melontarkan efek lekukan tikungan kotak tumpul alami (*radius border corner*),
    menyandingkan rona putih krem bersinar menyumbat proyeksi pantulan siluet gelap
    lempeng ketinggian elemen aslinya (*Z-axis elevation shadow*).
-   **Mengapa dipisah (digunakan arsitektur komponen luar)?:** Membentuk tatanan 
    matriks membutuhkan perhitungan dimensi seragam antar blok. Penggunaan CardView 
    mencegah programmer buang-buang usia memahat belasan perintah bingkai latar 
    buatan (Drawables) di ruang eksternal; Cukup sematkan fitur instan wawa OS 
    serta sisipkan penataan *weight* agar produk nampak rapi.

### 2. Penjelasan Logika Layout Utama (`activity_main.xml`)

Mengapa mengabaikan perulangan letak tata berjalur dan memeluk **GridLayout** utuh?
Hal tersebut dilandasi kepraktisan letak otomatis tatanan matriks.

-   **`android:columnCount="2"` / `android:rowCount="2"`**: Titik pondasi awal 
    mula petak layar dicanangkan di sepasang atribut panglima ini. Sistem melarang 
    kartu bungkus ketiga mendarat menerkam rute sisi badan jalan pertama, melangkah 
    tertib batas dinding asalkan jumlahnya mutlak beranggotakan dua.
-   **`android:layout_columnWeight="1"`**: Dituangkan memadamkan keluhan tampilan 
    yang kaku asimetris. Elemen akan mencubit sisa jarak sel kosong yang tersisa 
    dalam perbatasan baris dan mengekspansikan dirinya setara satu sama lain. Lebar 
    kertas tak peduli secuil apapun layar *smartphone*, akan proporsional lunas
    membelah kue porsi secara absolut merata.

### 3. Alur Visual

Pandangan dilarutkan ke relung ubin ubin simetris menyambut jemari konsumen:

1.  **Pajangan Gerbang Perkenalan**: Teks pembuka horizontal menembakkan gubahan
    identitas "Toko Bunga" bernuansa corak Sage Green di posisi paling menjulang 
    yang diikat utuh ke dalam kontainer vertikal pembimbing jalan (*parent*).
2.  **Injeksi Produk Perdana**: Di tanah kekuasaan grid, kotak bunga "Mawar Merah"
    [Baris 0, Kolom 0] mendarat menyita tanah pojok lajur pertama.
3.  **Hentakan Penutupan Gerbang Sisi**: Rekan dagangan "Tulip Kuning" dilesatkan
    ke [Baris 0, Kolom 1]. Layar secara dinamis menyatukan porsi dan menyumbat 
    dinding tepian pinggir kanan penuh total.
4.  **Gelombang Migrasi Tumpah Ruah (*Wrap Flow*)**: Karena limit parit horizontal 
    tandas (2 pilar terpenuhi), maka kuncup jualan "Anggrek Ungu" dan "Lily Putih" 
    ditendang merosot bersilangan guling menciptakan dataran barisan dasar baru 
    [Baris 1], menyuguhkan harmoni catur perwajahan nan eksotis rapi!
