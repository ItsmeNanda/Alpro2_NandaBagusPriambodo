<h1 align="center">Laporan Praktikum Modul 2 <br> REVIEW PENGENALAN PEMROGRAMAN </h1>
___
<h5 align="center">Nanda Bagus Priambodo - 103112430007 </h5>
### Dasar Teori

Golang adalah bahasa pemrograman yang dikembangkan oleh Google dan dirilis pada tahun 2009. Bahasa ini dirancang untuk menjadi sederhana, efisien, dan mudah digunakan, dengan sintaksis yang bersih dan jelas. Go mendukung pemrograman berorientasi objek, tetapi tidak memiliki pewarisan kelas tradisional; sebaliknya, ia menggunakan komposisi dan antarmuka untuk mencapai polimorfisme. Salah satu fitur utama Go adalah dukungan bawaan untuk pemrograman konkuren melalui goroutine dan channel, yang memungkinkan pengembang untuk menulis aplikasi yang dapat menangani banyak tugas secara bersamaan dengan efisien. Go juga memiliki pengelolaan memori otomatis melalui garbage collection, serta alat pengembangan yang kuat, termasuk sistem manajemen paket dan alat untuk pengujian dan profiling, menjadikannya pilihan populer untuk pengembangan aplikasi server, sistem, dan layanan cloud.

### Unguided
___
#### Soal Latihan 2A

##### soal 1

Telusuri program berikut dengan cara mengkompilasi dan mengeksekusi program. Silakan masukan data yang sesuai sebanyak yang diminta program. Perhatikan keluaran yang diperoleh. Coba terangkan apa sebenarnya yang dilakukan program tersebut?

```go
package main
import "fmt"  
func main() {

    var (
        satu, dua, tiga string
        temp            string
    )
  
    fmt.Print("Masukan input string: ")
    fmt.Scanln(&satu)
    fmt.Print("Masukan input string: ")
    fmt.Scanln(&dua)
    fmt.Print("Masukan input string: ")
    fmt.Scanln(&tiga)

    fmt.Println("Output awal = " + satu + " " + dua + " " + tiga)
    temp = satu
    satu = dua
    dua = tiga
    tiga = temp

    fmt.Println("Output akhir = " + satu + " " + dua + " " + tiga)
}
```

  
Penjelasan code di atas adalah perubahan cara pemanggilan dan output, pada print awal kita memanggil urutan awal yaitu 1 , 2 , 3 dan selanjutnya kita mengubah parameter atau isi dari variabel yang awalnya di urutan pertama di ubah menjadi urutan ke 3 di ambil dari variabel temp, po  sisi satu di tuker dengan posisis dua yang terdapat pada variabel satu, variabel dua di isi value dari variabel tiga dalam variabel dua dan yang terakhir value 3 di isi oleh temp yang hasilnya yaitu 2 , 3, 1


##### Soal 2

Tahun kabisat adalah tahun yang habis dibagi 400 atau habis dibagi 4 tetapi tidak habis dibagi 100. Buatlah sebuah program yang menerima input sebuah bilangan bulat dan memeriksa apakah bilangan tersebut merupakan tahun kabisat (true) atau bukan (false).

```go
package main
import "fmt"

func main() {
    var tahun, rumus int

    fmt.Scan(&tahun)

    rumus = tahun % 4

    if rumus == 0 {
        fmt.Print("True")
    } else {
        fmt.Print("False")
    }
}
```

![[Output/2a2.png]]

Pada program di atas seperti kita ketahui sebelumnya kita perlu masukan dari seorang user dalam bentuk integer lalu kita melakukan sebuah rumus modulus dala bentuk "%" yang berarti modulus dan akan di bagi dengan 4 lalu akan ada percabangan if dan else dengan kondisi jika saisa bagi dari tahun adalah 0 maka tahun itu kabisat atau habis di bagi dengan empat dan jika terdapat sisa pada pembagian maka tahun itu bukan tahun kabisat dan akan return sebuah nilai "false"

##### Soal 3

Buat program Bola yang menerima input jari-jari suatu bola (bilangan bulat). Tampilkan Volume dan Luas kulit bola. 𝑣𝑜𝑙𝑢𝑚𝑒𝑏𝑜𝑙𝑎=43𝜋𝑟3 dan 𝑙𝑢𝑎𝑠𝑏𝑜𝑙𝑎=4𝜋𝑟2 (π ≈ 3.1415926535).

```go
package main
import "fmt"

func main() {
    var jari float64
    var volume, luas float64

    fmt.Scan(&jari)
    volume = jari * jari * jari * 4 * 3.1415926535 / 3
    luas = 4 * 3.1415926535 * jari * jari

    fmt.Printf("Bola dengan jejari %f memiliki volume %f dan luas kulit %f", jari, volume, luas)
}
```
![[Output/2a3.png]]
Pada program di atas adalah program mencari volume dan luas lingkaran, kita meminta user menginputkan jari jari lalu program akan memasukan kedalam volume dan rumus lalu output atau return value nya adalah luas dan volume dari hasil yang telah di hitung dalam bentuk float.

##### Soal 4

Dibaca nilai temperatur dalam derajat Celsius. Nyatakan temperatur tersebut dalam Fahrenheit
𝐶𝑒𝑙𝑠𝑖𝑢𝑠=(𝐹𝑎ℎ𝑟𝑒𝑛ℎ𝑒𝑖𝑡−32)×5/9 𝑅𝑒𝑎𝑚𝑢𝑟=𝐶𝑒𝑙𝑐𝑖𝑢𝑠×4/5 𝐾𝑒𝑙𝑣𝑖𝑛=(𝐹𝑎ℎ𝑟𝑒𝑛ℎ𝑒𝑖𝑡+459.67)×5/9

```go
package main

import "fmt"
func main() {

    var celcius float64
    var farenheit, reamur, kelvin float64

    fmt.Scan(&celcius)

    farenheit = (celcius * 9 / 5) + 32
    reamur = celcius * 4 / 5
    kelvin = celcius + 273.15

    fmt.Println("Temperatur Celcius ", celcius)
    fmt.Println("Temperatur Farenheit ", farenheit)
    fmt.Println("Temperatur Reamur ", reamur)
    fmt.Println("Temperatur Kelvin ", kelvin)
}
```
![[Output/2a4.png]]
Mengonversi suhu dari Celsius ke tiga skala suhu lainnya: Fahrenheit, Reamur, dan Kelvin. User akan memasukkan nilai celcisu dan akan di konversikan ke Fahrenheit, Reamur, dan Kelvin sesuai dengan rumus yang ada.

##### Soal 5

Buat program ASCII yang akan membaca 5 buat data integer dan mencetaknya dalam format karakter. Kemudian membaca 3 buah data karakter dan mencetak 3 buah karakter setelah karakter tersebut (menurut tabel ASCII)

Masukan terdiri dari dua baris. Baris pertama berisi 5 buah data integer. Data integer mempunyai nilai antara 32 s.d. 127. Baris kedua berisi 3 buah karakter yang berdampingan satu dengan yang lain (tanpa dipisahkan spasi).

Keluaran juga terdiri dari dua baris. Baris pertama berisi 5 buah representasi karakter dari data yang diberikan, yang berdampingan satu dengan lain, tanpa dipisahkan spasi. Baris kedua berisi 3 buah karakter (juga tidak dipisahkan oleh spasi).

```go
package main 
import "fmt"

func main() {
    var kode1, kode2, kode3, kode4, kode5 int
    var huruf1, huruf2, huruf3 rune

    fmt.Scan(&kode1, &kode2, &kode3, &kode4, &kode5)
    fmt.Scanln()
    fmt.Scanf("%c%c%c\n", &huruf1, &huruf2, &huruf3)

    huruf1 += 1
    huruf2 += 1
    huruf3 += 1

    fmt.Printf("%c%c%c%c%c\n", kode1, kode2, kode3, kode4, kode5)
    fmt.Printf("%c%c%c\n", huruf1, huruf2, huruf3)
}

}
```
![[Output/2a5.png]]
Program diatas digunakan juga untuk menggeser karakter. Jadi permisalan kita akan menggeser masing-masing karakter dari kata SNO. Maka ketika dijalankan, S akan berubah menjadi T (huruf setelah S), N menjadi O dan O menjadi P. Masing-masing karakter akan bergeser satu. Kuncinya ada di penggunaan tipe data rune, yang digunakan untuk menyimpan masing masing karakter.

#### Soal Latihan 2B

##### soal 1

Telusuri program berikut dengan cara mengkompilasi dan mengeksekusi program. Silakan masukan data yang sesuai sebanyak yang diminta program. Perhatikan keluaran yang diperoleh. Coba terangkan apa sebenarnya yang dilakukan program tersebut?

```go
package main
import "fmt"

func main() {
    var zat1, zat2, zat3, zat4 string
    var cocok bool
    
    cocok = true
    for i := 1; i <= 5; i++ {
        fmt.Print("Percobaan ", i, ": ")
        fmt.Scan(&zat1, &zat2, &zat3, &zat4)

        if !(zat1 == "merah" && zat2 == "kuning" && zat3 == "hijau" && zat4 == "ungu") {
            cocok = false
        }
    }
    fmt.Print("Berhasil: ", cocok)

}
```
![[Output/2b1.png]]
  
Program di atas adalah program untuk membandingkan antara zat masukan, semisal zat praktikum tidak sesuai dengan rumus maka hasilnya adalah false.

##### soal 2

Suatu pita (string) berisi kumpulan nama-nama bunga yang dipisahkan oleh spasi dan ‘–‘, contoh pita diilustrasikan seperti berikut ini.
Pita: mawar – melati – tulip – teratai – kamboja – anggrek
Buatlah sebuah program yang menerima input sebuah bilangan bulat positif (dan tidak nol) N, kemudian program akan meminta input berupa nama bunga secara berulang sebanyak N kali dan nama tersebut disimpan ke dalam pita.
(Petunjuk: gunakan operasi penggabungan string dengan operator “+” ).
Tampilkan isi pita setelah proses input selesai.

```go
package main
import "fmt"

func main() {
    var bunga, pita string
    var jumlah int

    jumlah = 0

    for {
        fmt.Print("Bunga ", jumlah+1, ": ")
        fmt.Scan(&bunga)

        if bunga == "selesai" {
            break
        }

        pita = pita + bunga + " - "
        jumlah++
    }

    fmt.Println("Pita:", pita)
    fmt.Println("Bunga:", jumlah)
}
```
![[Output/2b2.png]]
  Program ini meminta user untuk memasukkan nama bunga secara berulang sampai user mengetikkan kata "selesai". Setiap nama bunga yang dimasukkan akan ditambahkan ke string pita, yang berfungsi sebagai daftar bunga, dipisahkan oleh " - ". Variabel `jumlah` digunakan untuk menghitung jumlah bunga yang dimasukkan. Setelah user selesai memasukkan nama bunga, program akan mencetak daftar bunga yang telah dimasukkan dan total jumlah bunga yang dimasukkan.
  
##### soal 3

Setiap hari Pak Andi membawa banyak barang belanjaan dari pasar dengan mengendarai sepeda motor. Barang belanjaan tersebut dibawa dalam kantong terpal di kiri-kanan motor. Sepeda motor tidak akan oleng jika selisih berat barang di kedua kantong sisi tidak lebih dari 9 kg.
Buatlah program Pak Andi yang menerima input dua buah bilangan real positif yang menyatakan berat total masing-masing isi kantong terpal. Program akan terus meminta input bilangan tersebut hingga salah satu kantong terpal berisi 9 kg atau lebih.

```go
package main
import "fmt"

func main() {
    var kantong1, kantong2, selisih float32
    var oleng bool

    for {
        fmt.Print("Masukan berat belanjaan di kedua kantong: ")
        fmt.Scan(&kantong1, &kantong2)

        if kantong1 < 0 || kantong2 < 0 {
            fmt.Println("Proses selesai")
            break
        }

        if kantong1+kantong2 > 150 {
            fmt.Println("Proses selesai")
            break
        }

        if kantong1 > kantong2 {
            selisih = kantong1 - kantong2
        } else {
            selisih = kantong2 - kantong1
        }

        oleng = selisih >= 9
        fmt.Println("Sepeda motor pak Andi akan oleng:", oleng)
    }
}
```
![[Output/2b3.png]]
Program ini meminta user untuk memasukkan berat belanjaan di dua kantong secara berulang. Jika salah satu berat negatif atau total berat kedua kantong melebihi 150, program akan berhenti. Program kemudian menghitung selisih berat antara kedua kantong dan menentukan apakah sepeda motor pak Andi akan oleng, yaitu jika selisihnya 9 atau lebih. Hasilnya dicetak sebagai status oleng atau tidak.

##### soal 4

√2 merupakan bilangan irasional. Meskipun demikian, nilai tersebut dapat dihampiri dengan rumus berikut: √2=Π(4𝑘+2)2(4𝑘+1)(4𝑘+3)∞𝑘=0
Modifikasi program sebelumnya yang menerima input integer 𝐾 dan menghitung √2 untuk 𝐾 tersebut. Hampiran √2 dituliskan dalam ketelitian 10 angka di belakang koma.

```go
package main
import (
    "fmt"
    "math"
)
func main() {
    var k int
    fmt.Print("Nilai K: ")
    fmt.Scan(&k)
    result := 1.0

    for i := 0; i < k; i++ {
        numerator := math.Pow(float64(4*i+2), 2)
        denumerator := float64((4*i + 1) * (4*i + 3))
        result *= numerator / denumerator
    }
    fmt.Printf("Hasil dari operasi fungsi = %.10f\n", result)

}
```
 ![[Output/2b4.png]]
 
 Dalam setiap iterasi, program menghitung nilai `numerator` sebagai kuadrat dari (4*i + 2) dan denominator sebagai hasil kali dari (4*i + 1) dan (4*i + 3). Hasil dari pembagian numerator dengan denominator kemudian dikalikan dengan result, sehingga result menyimpan hasil kumulatif dari operasi tersebut.Dengan menggunakan fungsi `math.Pow`, program dapat melakukan perhitungan kuadrat dengan akurasi tinggi, dan hasilnya memberikan gambaran tentang bagaimana nilai k mempengaruhi hasil akhir dari operasi matematis yang dilakukan. Program ini dapat digunakan untuk menghitung nilai tertentu dalam konteks matematis yang lebih luas, seperti dalam analisis deret atau fungsi tertentu.


#### Soal Latihan 2C

##### soal 1

PT POS membutuhkan aplikasi perhitungan biaya kirim berdasarkan berat parsel. Maka, buatlah program BiayaPos untuk menghitung biaya pengiriman tersebut dengan ketentuan sebagai berikut!
Dari berat parsel (dalam gram), harus dihitung total berat dalam kg dan sisanya (dalam gram). Biaya jasa pengiriman adalah Rp. 10.000,- per kg. Jika sisa berat tidak kurang dari 500 gram, maka tambahan biaya kirim hanya Rp. 5,- per gram saja. Tetapi jika kurang dari 500 gram, maka tambahan biaya akan dibebankan sebesar Rp. 15,- per gram. Sisa berat (yang kurang dari 1kg) digratiskan biayanya apabila total berat ternyata lebih dari 10kg

```go
package main
import "fmt"

func main() {
    var berat, kg, gram, harga int

    fmt.Print("Masukkan Berat Parsel dalam Gram: ")
    fmt.Scanln(&berat)

    kg = berat / 1000
    gram = berat % 1000

    fmt.Printf("Detail berat: %d kg %d gr\n", kg, gram)

    if gram >= 500 {
        gram = gram * 5
    } else {
        gram = gram * 15
    }

    if kg < 10 {
        kg = kg * 10000
        harga = kg + gram
    } else {
        kg = kg * 10000
        harga = kg
    }

    fmt.Printf("Detail biaya: Rp%d + Rp%d\n", kg, gram)
    fmt.Print("Total biaya: Rp", harga)
}
```
![[Output/2c1.png]]
Program ini meminta user memasukkan berat parsel dalam gram, kemudian mengonversi berat tersebut menjadi kilogram dan sisa gram. Setelah menampilkan detail berat  biaya pengiriman berdasarkan berat sisa dan jika sisa gram lebih dari atau sama dengan 500, tarif per gram adalah 5, sedangkan jika kurang dari 500, tarifnya adalah 15. Biaya untuk kilogram dihitung dengan mengalikan berat dalam kilogram dengan 10.000, dan total biaya ditentukan berdasarkan berat kemudian menampilkan detail biaya dan total biaya pengiriman kepada pengguna.

##### soal 2

a. Jika nam diberikan adalah 80.1, apa keluaran dari program tersebut? Apakah eksekusi program tersebut sesuai spesifikasi soal?
b. Apa saja kesalahan dari program tersebut? Mengapa demikian? Jelaskan alur program seharusnya!
c. Perbaiki program tersebut! Ujilah dengan masukan: 93.5; 70.6; dan 49.5. Seharusnya keluaran yang diperoleh adalah ‘A’, ‘B’, dan ‘D’.

Code awal
```go
package main 
import “fmt” 

func main() { 
var nam float64 
var nmk string 

fmt.Print(“Nilai akhir mata kuliah: “) 
fmt.Scanln(&nam) 

if nam > 80 { 
nam = “A” 
} 
if nam > 72.5 { 
nam = “AB” 
} 
if nam > 65 {
nam = “B” 
} 
if nam > 57.5 { 
nam = “BC” 
} 
if nam > 50 { 
nam = “C” 
} 
if nam > 40 {
nam = “D” 
} else if nam <= 40 {
nam = “E” 
} 

fmt.Println(“Nilai mata kuliah: “, nmk) 
}
```

Jawaban:
A. Keluaran dari program adalah eror dan tidak sesuai dengan spesifikasi
B. Terdapat beberapa kesalahan yaitu pada percabangan yang seharusnya menjadikan 1 percabangan saja dengan operator else if, yang kedua adalah kesalahan pada variabel yang di panggil seharusnya menggunakan nmk bukan nam yang bersifat string bukan float, yang ketiga adalah tidak ada pembatas pada perbandingan lebih dari sampai kurang dari berapa.
C. Berikut adalah code yang benar
```go
package main
import "fmt"

func main() {
    var nam float64
    var nmk string
    
    fmt.Print("Nilai akhir mata kuliah: ")
    fmt.Scanln(&nam)

    if nam > 80 {
        nmk = "A"
    } else if nam > 72.5 && nam <= 80 {
        nmk = "AB"
    } else if nam > 65 && nam <= 72.5 {
        nmk = "B"
    } else if nam > 57.5 && nam <= 57.5 {
        nmk = "BC"
    } else if nam > 50 && nam <= 57.5 {
        nmk = "C"
    } else if nam > 40 && nam <= 50 {
        nmk = "D"
    } else if nam <= 40 && nam <= 40 {
        nmk = "E"
    }

    fmt.Println("Nilai mata kuliah: ", nmk)
}
```
![[Output/2c2.png]]
##### soal 3

Sebuah bilangan bulat b memiliki faktor bilangan f > 0 jika f habis membagi b. Contoh: 2 merupakan faktor dari bilangan 6 karena 6 habis dibagi 2.
Buatlah program yang menerima input sebuah bilangan bulat b dan b > 1. Program harus dapat mencari dan menampilkan semua faktor dari bilangan tersebut!Bilangan bulat b > 0 merupakan bilangan prima p jika dan hanya jika memiliki persis dua faktor bilangan saja, yaitu 1 dan dirinya sendiri.
Lanjutkan program sebelumnya. Setelah menerima masukan sebuah bilangan bulat b > 0. Program tersebut mencari dan menampilkan semua faktor bilangan tersebut. Kemudian, program menentukan apakah b merupakan bilangan prima.

```go
package main
import "fmt"

func main() {
    var angka, faktor int
    var prima bool

    fmt.Print("Masukan Bilangan: ")
    fmt.Scan(&angka)
    fmt.Print("Faktor: ")
    for i := 1; i <= angka; i++ {

        if angka%i == 0 {
            fmt.Print(i, " ")
            faktor++
        }
    }
    fmt.Println()
    if faktor == 2 {
        prima = true
    } else {
        prima = false
    }

    fmt.Println("Prima:", prima)
}
```
![[Output/2c3.png]]
