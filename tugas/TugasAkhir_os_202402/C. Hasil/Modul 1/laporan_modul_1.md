# 📝 Laporan Tugas Akhir

**Mata Kuliah:** Sistem Operasi

**Semester:** Genap / Tahun Ajaran 2024–2025

**Nama:** Defita Dwi Wulandary

**NIM:** 240202856

Modul yang Dikerjakan: Modul 1 – System Call dan Instrumentasi Kernel
---

## 📌 Deskripsi Singkat Tugas

Tuliskan deskripsi singkat dari modul yang Anda kerjakan. Misalnya:

* **Modul 1 – System Call dan Instrumentasi Kernel**:
 Pada Modul 1 ini, diminta untuk memodifikasi kernel xv6-public dengan menambahkan dua buah system call baru, yaitu:

   * `getpinfo(struct pinfo *ptable)`
    → Mengembalikan informasi proses yang sedang aktif, termasuk PID, ukuran memori, dan nama proses.

   * `getreadcount()`
    → Mengembalikan total jumlah pemanggilan fungsi `read()` sejak sistem boot.

Tugas ini melatih pemahaman dalam memodifikasi kernel, menambahkan system call, serta mengakses dan memanipulasi informasi proses di tingkat kernel. Selain itu, juga membuat program uji pada level user untuk menguji kedua system call yang telah dibuat.

---

## 🛠️ Rincian Implementasi

Tuliskan secara ringkas namun jelas apa yang Anda lakukan:

### Contoh untuk Modul 1:

* Menambahkan dua system call baru `(getpinfo dan getreadcount)` di file `sysproc.c` dan mendaftarkannya di `syscall.c`

* Menambahkan nomor syscall di `syscall.h`, serta deklarasinya di `user.h` dan `usys.S`

* Membuat struktur struct pinfo di `proc.h` untuk menyimpan info proses aktif

* Menambahkan variabel global `readcount` di `sysproc.c` dan menginkrementasinya di fungsi `sys_read()` `(sysfile.c)`

* Membuat dua program uji user-level: `ptest.c` untuk `getpinfo` dan `rtest.c` untuk `getreadcount`

---

## ✅ Uji Fungsionalitas

Tuliskan program uji apa saja yang Anda gunakan, misalnya:

* `ptest`: untuk menguji `getpinfo()`
* `rtest`: untuk menguji `getReadCount()`

---

## 📷 Hasil Uji

Lampirkan hasil uji berupa screenshot atau output terminal. Contoh:

### 📍 Contoh Output `ptest`:

```
$ ptest
PID	MEM	NAME
1	12288 init
2	16384	sh
3	12288	ptest

```
### 📍 Contoh Output `rtest`:

```
$ rtest
Read Count Sebelum: 12
hello
Read Count Setelah: 13
```

Jika ada screenshot:

<img width="946" height="534" alt="modul1_" src="https://github.com/user-attachments/assets/abb1dc3a-1f80-46cb-9695-341fc65f0d40" />


---

## ⚠️ Kendala yang Dihadapi

* Perlu memastikan struktur pinfo di file user `(ptest.c)` sama persis dengan yang didefinisikan di kernel `(proc.h)`, agar data tidak korup saat dikembalikan       dari `syscall`.
  
* Pada versi xv6-public, ptable_lock mungkin tidak didefinisikan, sehingga perlu menggunakan `ptable.lock` atau mengimplementasikan `spinlock` baru.
  
* Salah menaruh  `readcount++` di awal fungsi `sys_read()`
---


## 📚 Referensi

Tuliskan sumber referensi yang Anda gunakan, misalnya:

* Buku xv6 MIT: [https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf](https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf)
* Repositori xv6-public: [https://github.com/mit-pdos/xv6-public](https://github.com/mit-pdos/xv6-public)
* Stack Overflow, GitHub Issues, diskusi praktikum

---

