# Kedai Kopi Senja

Website tugas Minggu 2, tiga halaman tanpa CSS. Isinya beranda kedai kopi, daftar menu, sama form pemesanan.

## a. Apa yang muncul di address bar setelah form dikirim, dan mengapa data form tampil di sana? Hubungkan dengan materi method HTTP di Minggu 1.

Form yang masih kosong tidak terkirim karena atribut required pada nama dan nomor WhatsApp menahannya, muncul pesan Please fill out this field di kolom nama dan address bar tetap di pesan.html sehingga request HTTP belum dibuat. Setelah semua field diisi lengkap, address bar berubah menjadi http://127.0.0.1:5500/pesan.html?nama=Ade+Raihan&whatsapp=081234567890&menu=kopi-susu-senja&jumlah=2&cara_ambil=Diantar&catatan=Es+sedikit%2C+tanpa+gula. Bagian sebelum tanda tanya adalah nama halaman, sedangkan bagian sesudahnya adalah query string berisi enam pasangan nama dan nilai yang disambung dengan &, nama pasangannya berasal dari atribut name tiap field dan spasi serta koma diubah menjadi + dan %2C lewat URL encoding. Hal ini terjadi karena form memakai method get, dan sesuai materi Minggu 1 metode GET memang menempelkan data di URL dengan request line berbentuk GET /pesan.html?nama=... sehingga datanya terlihat di address bar, tersimpan di history, dan tidak cocok untuk data sensitif, berbeda dengan method post yang mengirim data lewat body dan address bar tetap pesan.html saja.

## b. Pilih satu bagian halamanmu yang memakai element semantic. Mengapa kamu memilih element itu dan bukan div?

Bagian yang dipilih adalah nav berisi link Beranda, Menu, dan Pesan di dalam header. Element nav dipakai karena maknanya memang wadah navigasi sehingga browser dan screen reader langsung mengenalinya sebagai landmark navigasi dan bisa melompat ke sana, sedangkan div hanya kotak pembungkus biasa tanpa arti sehingga kemampuan tersebut hilang padahal tampilannya sama saja apalagi halaman ini belum memakai CSS. Penambahan aria-label Navigasi utama membuat landmark tersebut punya nama yang jelas, dan alasan yang sama dipakai untuk header, main, footer, dan address karena nama elementnya sudah menjelaskan perannya tanpa perlu ditebak dari class atau susunan div.
