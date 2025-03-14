# Tutorial Pemrograman Lanjut: Modul 5 (Java Profiling)
Madeline Clairine Gultom\
2306207846\
ADPRO-A

## Endpoint #1 /all-student
### Before Optimization
![Screenshot (880)](https://github.com/user-attachments/assets/2bfdff63-f295-4a11-8333-54daeb5ab9d1)
### Test Result JMeter
![WhatsApp Image 2025-03-14 at 20 02 26_ebcc7256](https://github.com/user-attachments/assets/584e9159-a775-4a4d-b892-9b7af24a6f6e)
### After Optimization
![Screenshot (901)](https://github.com/user-attachments/assets/d1b60ebb-e634-42cb-bc88-3612f11148a3)

## Endpoint #2 /all-student-name
### Before Optimization
![Screenshot (886)](https://github.com/user-attachments/assets/7f260821-53a3-4acf-925c-17c6726961bf)
### Test Result JMeter
![image](https://github.com/user-attachments/assets/3eeed9bd-951d-4552-b61b-51adbbdc0469)
### After Optimization
![Screenshot (897)](https://github.com/user-attachments/assets/ed504204-01f7-4095-b77e-1a66217d0547)

## Endpoint #3 /highest-gpa
### Before Optimization
![Screenshot (892)](https://github.com/user-attachments/assets/aa120c8c-522e-4bca-b560-c8a2c3fb3248)
### Test Result JMeter
![image](https://github.com/user-attachments/assets/8a4feac2-ab1a-451f-8925-cbf7d29ad08c)
### After Optimization
![Screenshot (900)](https://github.com/user-attachments/assets/0444b600-4819-467a-b43f-4bc1e5c4a39c)

## Refleksi
### 1. Perbedaan JMeter dan Intellij Profiler
**JMeter** berfokus pada performance testing dari sudut pandang pengguna atau sistem, misalnya mengukur response time, throughput, dan concurrent users. **JMeter** membantu mengidentifikasi seberapa baik aplikasi menangani beban kerja tertentu.
**IntelliJ Profiler**, di sisi lain, digunakan untuk profiling aplikasi secara internal. Dengan profiler, kita dapat melihat bagaimana CPU, memori, dan thread digunakan selama eksekusi program. Ini membantu dalam menemukan _bottleneck_ spesifik dalam kode, seperti _loop_ yang tidak efisien atau _query_ database yang lambat.

### 2. Peran _profiling_
Profiling membantu dalam mengidentifikasi titik lemah dalam aplikasi dengan menganalisis penggunaan CPU, memori, dan waktu eksekusi setiap metode. IntelliJ Profiler membantu menemukan metode yang paling banyak mengonsumsi resource atau mengalami _bottleneck_. Contohnya, saat menemukan loop yang berjalan terlalu lama atau pemanggilan database yang tidak efisien, aku bisa langsung mencari cara untuk mengoptimalkannya, seperti mengganti struktur data atau memperbaiki query.

### 3. Efektivitas IntelliJ Profiler
IntelliJ Profiler cukup efektif dalam mengidentifikasi _bottleneck_ dengan fitur seperti _call tree_, _CPU analysis_, dan _memory tracking_. Visualisasinya memudahkan analisis metode yang paling banyak mengonsumsi sumber daya, membantu menentukan prioritas optimasi. Dengan data real-time, profiler ini memastikan perbaikan yang dilakukan benar-benar meningkatkan kinerja aplikasi.

### 4. Tantangan dalam _Performance Testing_ dan _Profiling_
Tantangan utama dalam melakukan pengujian performa dan profiling adalah menangani data seeding dalam jumlah besar, yang dapat menyebabkan peningkatan waktu eksekusi dan konsumsi sumber daya yang tinggi. Selain itu, mengoptimalkan metode agar lebih efisien tanpa mengubah fungsionalitasnya juga menjadi tantangan tersendiri. Untuk mengatasi hal ini, diperlukan pendekatan yang sistematis, seperti membatasi jumlah data saat pengujian awal, menggunakan batch processing untuk mengurangi beban sistem, serta menerapkan algoritma yang lebih optimal berdasarkan hasil profiling. Dengan cara ini, proses pengujian dan optimasi dapat berjalan lebih efektif tanpa mengorbankan stabilitas aplikasi.

### 5. Benefit _IntelliJ Profiler_
_IntelliJ Profiler_ memberikan manfaat utama dalam profiling kode aplikasi, seperti mengidentifikasi _bottleneck_, menganalisis penggunaan CPU dan memori, serta memberikan insight mendalam tentang performa metode tertentu. Dengan alat ini, proses optimasi menjadi lebih terarah karena dapat langsung menemukan bagian kode yang perlu diperbaiki. Selain itu, kemampuannya dalam menampilkan visualisasi data secara real-time membantu dalam memahami pola eksekusi aplikasi dengan lebih cepat dan efisien.

### 6. Ketidakkonsistenan IntelliJ Profiler dan JMeter
Jika hasil profiling dengan IntelliJ Profiler tidak sepenuhnya sesuai dengan pengujian performa di JMeter, maka langkah yang dilakukan adalah membandingkan metrik dari keduanya dengan lebih teliti. Profiling lebih fokus menganalisis kinerja kode secara mendetail, sedangkan JMeter mengukur performa aplikasi saat diberikan beban tertentu. Jika ada perbedaan hasil, saya akan mengecek kembali skenario pengujian, memastikan lingkungan uji sama, dan menggabungkan kedua hasil tersebut untuk memahami masalah secara lebih akurat sebelum melakukan optimasi.

### 7. Strategi Pengoptimalan Kode
Strategi optimasi:
- **Mengurangi pemanggilan database yang tidak perlu**, yaitu mengganti iterasi `findById()` dalam loop dengan langsung mengambil semua data yang dibutuhkan dalam satu query.
- **Menggunakan struktur data yang lebih efisien**, yaitu mengganti `+=` dengan `StringBuilder` untuk menghindari pembuatan objek string yang berlebihan.
- **Menggunakan query database yang lebih optimal**, yaitu mengganti loop pencarian dengan `findTopByOrderByGpaDesc()` untuk mencari mahasiswa dengan GPA tertinggi.

Cara memastikan fungsionalitas tetap benar:
- Membandingkan output sebelum dan sesudah optimasi untuk melihat apakah ada perbedaan yang tidak diinginkan.
- Melakukan profiling ulang setelah perubahan untuk memastikan bahwa optimasi benar-benar meningkatkan performa tanpa efek samping negatif.

**Jadi,** setelah dilakukan profiling dan optimasi pada beberapa metode, pengujian ulang dengan JMeter menunjukkan adanya peningkatan performa dibandingkan dengan pengukuran awal. Optimasi yang dilakukan berhasil mengurangi waktu eksekusi dan meningkatkan efisiensi pemrosesan data tanpa mengubah fungsionalitas utama aplikasi. Hal ini membuktikan bahwa metode yang dioptimalkan kini lebih optimal dalam menangani beban kerja yang diberikan.
