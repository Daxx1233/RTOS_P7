# Praktikum RTOS - SEMESTER 5 (3 Teknik Komputer A)
- Triyas Rahmadiyanti (3222600001)
- Duta Fithra Qolby (3222600003)
# Exercise 7 – Demonstrate that the sharing of resources in a multitasking design can lead to a deterioration in system performance.

## Deskripsi Projek
Projek ini adalah implementasi firmware untuk sebuah sistem embedded menggunakan mikrokontroler STM32. 
Tujuan utamanya adalah untuk mengontrol empat LED dengan tugas berbeda menggunakan FreeRTOS. 
Proyek ini memanfaatkan multitasking untuk mengatur perilaku setiap LED sesuai interval dan prioritas yang telah ditentukan.

## Deskripsi Alur Kerja
1. Inisialisasi:
   - Inisialisasi sistem dilakukan di fungsi main():
     - Inisialisasi clock sistem (SystemClock_Config()).
     - Inisialisasi GPIO (MX_GPIO_Init()).
   - Kernel RTOS dimulai menggunakan osKernelStart().
2. Pembuatan Tugas:
   - Setiap LED dikontrol oleh tugas RTOS yang didefinisikan menggunakan osThreadDef():
     - red_led untuk LED Merah.
     - green_led untuk LED Hijau.
     - yellow_led untuk LED Kuning.
3. Pengendalian LED:
   - LED Merah:
     - Tugas red_led menghidupkan dan mematikan LED dengan interval 550 ms.
     - Akses data bersama dilakukan dengan pengamanan critical section untuk mencegah konflik.
  - LED Hijau:
    - Tugas green_led menghidupkan dan mematikan LED dengan interval 200 ms.
    - Menggunakan pengamanan critical section untuk akses data bersama.
  - LED Kuning: Tugas yellow_led melakukan toggle LED setiap 50 ms tanpa akses ke data bersama.
  - LED Biru: Menyala saat terjadi konflik data dalam fungsi accessSharedData().
4. Akses Data Bersama:
  - Fungsi accessSharedData():
    - Mengecek dan memperbarui status startFlag.
    - Jika konflik terdeteksi, LED Biru menyala selama proses berlangsung.
5. Manajemen Waktu: Interval penundaan ditangani dengan osDelay().
6. Error Handling: Jika terjadi kesalahan selama runtime, fungsi Error_Handler() akan menangani kesalahan tersebut dengan cara mematikan interrupt dan masuk ke infinite loop.

## Fungsi Utama
1. Pengaturan tugas secara paralel.
2. Manajemen akses data bersama menggunakan critical section.
3. Penanganan potensi konflik data dengan LED Biru sebagai indikator.
Proyek ini menunjukkan prinsip-prinsip inti pengembangan sistem berbasis RTOS seperti sinkronisasi, prioritas tugas, dan pengendalian perangkat keras.

# Gambar Hardware
![Screenshot 2024-11-20 203131](https://github.com/user-attachments/assets/ffd3f769-3096-49b2-be6d-dc6c2d8841e7)

# Video Hardware

https://github.com/user-attachments/assets/a3697899-013f-4a64-902a-7d970c7c26b4
