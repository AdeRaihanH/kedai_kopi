https://aderaihanh.github.io/kedai_kopi/

# Kedai Kopi Senja

# Tugas Minggu 2

Website tugas Minggu 2, tiga halaman tanpa CSS. Isinya beranda kedai kopi, daftar menu, sama form pemesanan.

## a. Apa yang muncul di address bar setelah form dikirim, dan mengapa data form tampil di sana? Hubungkan dengan materi method HTTP di Minggu 1.

Form yang masih kosong tidak terkirim karena atribut required pada nama dan nomor WhatsApp menahannya, muncul pesan Please fill out this field di kolom nama dan address bar tetap di pesan.html sehingga request HTTP belum dibuat. Setelah semua field diisi lengkap, address bar berubah menjadi http://127.0.0.1:5500/pesan.html?nama=Ade+Raihan&whatsapp=081234567890&menu=kopi-susu-senja&jumlah=2&cara_ambil=Diantar&catatan=Es+sedikit%2C+tanpa+gula. Bagian sebelum tanda tanya adalah nama halaman, sedangkan bagian sesudahnya adalah query string berisi enam pasangan nama dan nilai yang disambung dengan &, nama pasangannya berasal dari atribut name tiap field dan spasi serta koma diubah menjadi + dan %2C lewat URL encoding. Hal ini terjadi karena form memakai method get, dan sesuai materi Minggu 1 metode GET memang menempelkan data di URL dengan request line berbentuk GET /pesan.html?nama=... sehingga datanya terlihat di address bar, tersimpan di history, dan tidak cocok untuk data sensitif, berbeda dengan method post yang mengirim data lewat body dan address bar tetap pesan.html saja.

## b. Pilih satu bagian halamanmu yang memakai element semantic. Mengapa kamu memilih element itu dan bukan div?

Bagian yang dipilih adalah nav berisi link Beranda, Menu, dan Pesan di dalam header. Element nav dipakai karena maknanya memang wadah navigasi sehingga browser dan screen reader langsung mengenalinya sebagai landmark navigasi dan bisa melompat ke sana, sedangkan div hanya kotak pembungkus biasa tanpa arti sehingga kemampuan tersebut hilang padahal tampilannya sama saja apalagi halaman ini belum memakai CSS. Penambahan aria-label Navigasi utama membuat landmark tersebut punya nama yang jelas, dan alasan yang sama dipakai untuk header, main, footer, dan address karena nama elementnya sudah menjelaskan perannya tanpa perlu ditebak dari class atau susunan div.

# Tugas Minggu 3

Website tiga halaman kedai kopi. Semua tampilan diatur lewat satu berkas `css/style.css`; tidak ada atribut `style` atau tag `<style>` di HTML.

## a. Sebutkan satu bagian yang kamu susun dengan Flexbox dan satu bagian dengan Grid. Mengapa pilihan itu cocok untuk kedua bagian tersebut?

Bagian header saya susun dengan Flexbox. Isinya cuma nama kedai dan navigasi, jadi saya butuh cara sederhana untuk menaruh nama di kiri dan link di kanan. Di ponsel saya set `flex-direction: column` supaya keduanya tersusun ke bawah, lalu mulai lebar 600px saya ubah jadi row dan pakai `justify-content: space-between`. Flexbox cocok karena isinya satu baris dan yang perlu diatur hanya perataan dan jarak; kalau pakai Grid untuk header rasanya berlebihan karena tidak ada baris dan kolom yang rumit.

Daftar menu saya susun dengan Grid. Di ponsel satu kolom, mulai 600px dua kolom, dan mulai 960px tiga kolom. Grid cocok karena semua card harus punya lebar kolom yang sama dan jumlah kolomnya berubah di media query. Saya cukup menulis `grid-template-columns: repeat(2, minmax(0, 1fr))` lalu `repeat(3, ...)` tanpa mengatur lebar tiap card. Kalau pakai Flexbox, card akan membungkus dan lebarnya belum tentu sama, jadi harus menghitung `flex-basis` sendiri.

## b. Ceritakan satu aturan CSS yang awalnya tidak berlaku. Apa yang kamu lihat di panel Styles, dan bagaimana kamu memperbaikinya?

Aturan yang awalnya tidak berlaku adalah media query tiga kolom untuk `.daftar-menu`. Saya sempat menaruh `@media (min-width: 960px)` di atas media query 600px. Waktu saya buka di lebar 1280px, menu tetap dua kolom, bukan tiga. Di panel Styles, aturan 960px terlihat dicoret, dan yang menang adalah aturan 600px yang letaknya lebih bawah. Ternyata specificity kedua aturan sama, jadi urutan yang menentukan. Saya perbaiki dengan memindahkan media query 960px ke bawah setelah media query 600px, jadi urutannya mobile first: aturan ponsel dulu, lalu 600px, lalu 960px. Setelah itu di 1280px card menu tampil tiga kolom.
