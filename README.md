# praktikum 8

### Struktur Dasar Class

```python
class NilaiMahasiswa:
    def __init__(self):
        self.daftar_mahasiswa = []
```
- Saat class diinisialisasi, dibuat list kosong `daftar_mahasiswa`
- List ini akan menyimpan data mahasiswa sebagai dictionary

### Method Tambah (`tambah()`)
```python
def tambah(self, nama, nim, mata_kuliah, nilai):
    # Cek apakah mahasiswa sudah ada
    for mahasiswa in self.daftar_mahasiswa:
        if mahasiswa['nama'] == nama and mahasiswa['nim'] == nim:
            print(f"Mahasiswa {nama} dengan NIM {nim} sudah ada.")
            return
    
    # Tambahkan mahasiswa baru
    mahasiswa_baru = {
        'nama': nama,
        'nim': nim,
        'mata_kuliah': mata_kuliah,
        'nilai': nilai
    }
    self.daftar_mahasiswa.append(mahasiswa_baru)
    print(f"Data mahasiswa {nama} berhasil ditambahkan.")
```
- Menerima 4 parameter: nama, nim, mata kuliah, dan nilai
- Pertama, memeriksa apakah mahasiswa sudah ada di list
- Jika belum ada, membuat dictionary baru dengan data mahasiswa
- Menambahkan dictionary ke `daftar_mahasiswa`
- Menampilkan pesan konfirmasi

### Method Tampilkan (`tampilkan()`)
```python
def tampilkan(self):
    if not self.daftar_mahasiswa:
        print("Tidak ada data mahasiswa.")
        return
    
    print("Daftar Nilai Mahasiswa:")
    print("-" * 50)
    for mahasiswa in self.daftar_mahasiswa:
        print(f"Nama: {mahasiswa['nama']}")
        print(f"NIM: {mahasiswa['nim']}")
        print(f"Mata Kuliah: {mahasiswa['mata_kuliah']}")
        print(f"Nilai: {mahasiswa['nilai']}")
        print("-" * 50)
```
- Memeriksa apakah list mahasiswa kosong
- Jika tidak kosong, mencetak detail setiap mahasiswa
- Menggunakan format yang rapi dengan garis pemisah

### Method Hapus (`hapus()`)
```python
def hapus(self, nama):
    for mahasiswa in self.daftar_mahasiswa[:]:
        if mahasiswa['nama'] == nama:
            self.daftar_mahasiswa.remove(mahasiswa)
            print(f"Data mahasiswa {nama} berhasil dihapus.")
            return
    
    print(f"Mahasiswa dengan nama {nama} tidak ditemukan.")
```
- Menerima parameter nama mahasiswa yang akan dihapus
- Menggunakan `self.daftar_mahasiswa[:]` untuk membuat salinan list saat iterasi
- Mencari mahasiswa berdasarkan nama
- Menghapus data menggunakan method `remove()`
- Menampilkan pesan konfirmasi atau pesan jika tidak ditemukan

### Method Ubah (`ubah()`)
```python
def ubah(self, nama, nim_baru=None, mata_kuliah_baru=None, nilai_baru=None):
    for mahasiswa in self.daftar_mahasiswa:
        if mahasiswa['nama'] == nama:
            # Ubah data sesuai parameter yang diberikan
            if nim_baru:
                mahasiswa['nim'] = nim_baru
            if mata_kuliah_baru:
                mahasiswa['mata_kuliah'] = mata_kuliah_baru
            if nilai_baru is not None:
                mahasiswa['nilai'] = nilai_baru
            
            print(f"Data mahasiswa {nama} berhasil diubah.")
            return
    
    print(f"Mahasiswa dengan nama {nama} tidak ditemukan.")
```
- Menerima nama mahasiswa dan parameter opsional untuk perubahan
- Parameter opsional: nim baru, mata kuliah baru, nilai baru
- Mencari mahasiswa berdasarkan nama
- Mengubah data sesuai parameter yang diberikan
- Hanya mengubah data yang ditentukan
- Menampilkan pesan konfirmasi

### Fungsi Utama (`main()`)
```python
def main():
    # Membuat objek manajemen nilai mahasiswa
    sistem_nilai = NilaiMahasiswa()
    
    # Menambah beberapa data mahasiswa
    sistem_nilai.tambah("Ahmad", "2101001", "Matematika", 85)
    sistem_nilai.tambah("Budi", "2101002", "Fisika", 90)
    sistem_nilai.tambah("Citra", "2101003", "Kimia", 88)
    
    # Menampilkan seluruh data
    sistem_nilai.tampilkan()
    
    # Mengubah data mahasiswa
    sistem_nilai.ubah("Budi", mata_kuliah_baru="Kimia", nilai_baru=92)
    
    # Menghapus data mahasiswa
    sistem_nilai.hapus("Citra")
    
    # Menampilkan data setelah perubahan
    sistem_nilai.tampilkan()
```
- Membuat objek `NilaiMahasiswa`
- Mendemonstrasikan penggunaan setiap method
- Menambah, mengubah, dan menghapus data
- Menampilkan data sebelum dan sesudah perubahan

### Cara Menjalankan
```python
if __name__ == "__main__":
    main()
```
- Memastikan `main()` hanya dijalankan jika script dieksekusi langsung
- Tidak dijalankan jika di-import sebagai modul

### Keunggulan Program
1. Fleksibel dalam mengelola data mahasiswa
2. Mencegah duplikasi data
3. Memberikan konfirmasi setiap operasi
4. Mudah dibaca dan dipelihara

### Contoh Alur Kerja
1. Tambah mahasiswa baru
2. Tampilkan seluruh data
3. Ubah data mahasiswa tertentu
4. Hapus data mahasiswa
5. Tampilkan data terbaru
