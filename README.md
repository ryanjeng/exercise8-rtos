# **Eliminasi Kontensi Sumber Daya dengan Semaphore**

## **Deskripsi**
Repositori ini berisi implementasi dari *Exercise 8 – Demonstrate how to eliminate resource contention in a selective manner using a semaphore*. Latihan ini menunjukkan cara menggunakan semaphore untuk menghilangkan masalah kontensi sumber daya dalam sistem multitasking FreeRTOS dengan cara yang lebih fokus dan minimal mengganggu sistem.

---

## **Konsep Utama**
- **Semaphore**:
  - Mekanisme kontrol aliran tugas dengan dua status: dilepaskan (bebas) dan terkunci
  - Mengontrol akses ke sumber daya kritis dengan minimal gangguan sistem
- **Keuntungan**:
  - Perlindungan sumber daya yang lebih selektif dibandingkan penonaktifan interrupt
- **Kekurangan**:
  - Memerlukan pemahaman yang lebih mendalam tentang sinkronisasi tugas

---

## **Implementasi**
### **Konfigurasi Semaphore**
1. **Pembuatan Semaphore**:
   - Definisikan referensi semaphore
   - Buat semaphore menggunakan CubeMX
   - Gunakan `osSemaphoreCreate()` dengan parameter default

2. **Penggunaan Semaphore**:
   - `osSemaphoreWait()`: Tunggu atau periksa status semaphore
   - `osSemaphoreRelease()`: Bebaskan semaphore setelah menggunakan sumber daya

3. **Contoh Kode**:
   ```c
   // Ambil semaphore dengan waktu tunggu
   osSemaphoreWait(CriticalResourceSemaphoreHandle, WaitTimeMilliseconds);
   
   // Akses sumber daya kritis
   // Kode Anda di sini
   
   // Lepaskan semaphore
   osSemaphoreRelease(CriticalResourceSemaphoreHandle);
   ```

---

## **Langkah Penggunaan**
1. **Persiapan Hardware**:
   - Mikrokontroler dengan dukungan FreeRTOS
   - LED untuk demonstrasi (oranye, biru)

2. **Konfigurasi Proyek**:
   - Gunakan STM32CubeMX
   - Aktifkan FreeRTOS
   - Tambahkan binary semaphore

3. **Implementasi dan Pengujian**:
   - **Latihan 8.1**: Ganti `taskENTER_CRITICAL()` dengan `osSemaphoreWait()`
   - **Latihan 8.2**: Atur waktu tunggu semaphore ke nol dan amati perilaku LED

---

## **Demonstrasi**
![Exercise8](https://github.com/user-attachments/assets/624166aa-669c-406f-b8dc-e3fffcdba50c)


---

## **Pelajaran yang Didapat**
- **Mekanisme Semaphore**:
  - Kontrol akses sumber daya yang lebih tepat
  - Minimal gangguan terhadap sistem multitasking
- **Strategi Sinkronisasi**:
  - Pentingnya pemilihan mekanisme kontrol akses yang sesuai
  - Trade-off antara kemudahan implementasi dan efisiensi sistem

---

Dengan memahami penggunaan semaphore, Anda dapat mengelola sumber daya bersama secara efisien dalam sistem multitasking.
