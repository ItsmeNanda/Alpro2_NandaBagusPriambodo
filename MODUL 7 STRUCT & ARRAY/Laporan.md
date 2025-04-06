<h1 align="center">Laporan Praktikum Modul 7 <br> STRUCT dan ARRAY </h1>
___
<h5 align="center">Nanda Bagus Priambodo - 103112430007 </h5>
### Dasar Teori STRUCT & ARRAY

**Struct** dalam Go adalah tipe data yang memungkinkan kita untuk mengelompokkan beberapa elemen dengan tipe yang berbeda menjadi satu entitas. Setiap elemen dalam struct disebut field, dan kita bisa mengaksesnya dengan menggunakan nama field. Sedangkan **array** adalah struktur data yang menyimpan elemen-elemen dengan tipe yang sama dalam urutan yang tetap, dengan ukuran yang telah ditentukan sebelumnya dan tidak dapat berubah selama program berjalan. Meskipun keduanya digunakan untuk menyimpan data, struct lebih fleksibel untuk menyimpan data yang heterogen (berbeda tipe), sementara array lebih cocok untuk data yang homogen (bertipe sama) dengan jumlah elemen yang tetap.

### Unguided
___
#### Soal Latihan Modul 7

##### soal 1

Suatu lingkaran didefinisikan dengan koordinat titik pusat (𝑐𝑥,𝑐𝑦) dengan radius 𝑟. Apabila diberikan dua buah lingkaran, maka tentukan posisi sebuah titik sembarang (𝑥,𝑦) berdasarkan dua lingkaran tersebut. Gunakan tipe bentukan titik untuk menyimpan koordinat, dan tipe bentukan lingkaran untuk menyimpan titik pusat lingkaran dan radiusnya.
Masukan terdiri dari beberapa tiga baris. Baris pertama dan kedua adalah koordinat titik pusat dan radius dari lingkaran 1 dan lingkaran 2, sedangkan baris ketiga adalah koordinat titik sembarang. Asumsi sumbu x dan y dari semua titik dan juga radius direpresentasikan dengan bilangan bulat.
Keluaran berupa string yang menyatakan posisi titik "Titik di dalam lingkaran 1 dan 2", "Titik di dalam lingkaran 1", "Titik di dalam lingkaran 2", atau "Titik di luar lingkaran 1 dan 2".

```go

```
![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal1.png)
  
>Code di atas merupakan code 

```go

```

##### soal 2

Sebuah array digunakan untuk menampung sekumpulan bilangan bulat. Buatlah program yang digunakan untuk mengisi array tersebut sebanyak N elemen nilai. Asumsikan array memiliki kapasitas penyimpanan data sejumlah elemen tertentu. Program dapat menampilkan beberapa informasi berikut:
a. Menampilkan keseluruhan isi dari array.
b. Menampilkan elemen-elemen array dengan indeks ganjil saja.
c. Menampilkan elemen-elemen array dengan indeks genap saja (asumsi indek ke-0 adalah genap).
d. Menampilkan elemen-elemen array dengan indeks kelipatan bilangan x. x bisa diperoleh dari masukan pengguna.
e. Menghapus elemen array pada indeks tertentu, asumsi indeks yang hapus selalu valid. Tampilkan keseluruhan isi dari arraynya, pastikan data yang dihapus tidak tampil
f. Menampilkan rata-rata dari bilangan yang ada di dalam array.
g. Menampilkan standar deviasi atau simpangan baku dari bilangan yang ada di dalam array tersebut.
h. Menampilkan frekuensi dari suatu bilangan tertentu di dalam array yang telah diisi tersebut.

```go

```
![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal2.png) 
>-
```go

```
>-

##### soal 3

Sebuah program digunakan untuk menyimpan dan menampilkan nama-nama klub yang memenangkan pertandingan bola pada suatu grup pertandingan. Buatlah program yang digunakan untuk merekap skor pertandingan bola 2 buah klub bola yang berlaga.
Pertama-tama program meminta masukan nama-nama klub yang bertanding, kemudian program meminta masukan skor hasil pertandingan kedua klub tersebut. Yang disimpan dalam array adalah nama-nama klub yang menang saja.
Proses input skor berhenti ketika skor salah satu atau kedua klub tidak valid (negatif). Di akhir program, tampilkan daftar klub yang memenangkan pertandingan.

```go

```

![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal3.png)
>-

```go

```

>-

##### Soal 4

Sebuah array digunakan untuk menampung sekumpulan karakter, Anda diminta untuk membuat sebuah subprogram untuk melakukan membalikkan urutan isi array dan memeriksa apakah membentuk palindrom.

```go

```

![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal4.png)

>-