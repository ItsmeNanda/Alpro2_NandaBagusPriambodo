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
package main

import (
    "fmt"
    "math"
)

type Titik struct {
    x, y int
}

type Lingkaran struct {
    titikPusat Titik
    radius     int
}

func jarak(p, q Titik) float64 {
    return math.Sqrt(float64((p.x-q.x)*(p.x-q.x) + (p.y-q.y)*(p.y-q.y)))
}

func didalam(l Lingkaran, p Titik) bool {
    return jarak(l.titikPusat, p) <= float64(l.radius)
}

func main() {
    var titikpst1, radius1, sembarang1, titikpst2, radius2, sembarang2, x, y int

    // Input titik lingkaran 1
    fmt.Scan(&titikpst1, &radius1, &sembarang1)

    // Input titik lingkaran 2
    fmt.Scan(&titikpst2, &radius2, &sembarang2)

    // Input titik sembarang
    fmt.Scan(&x, &y)

    lingkaran1 := Lingkaran{Titik{x: titikpst1, y: radius1}, sembarang1}
    lingkaran2 := Lingkaran{Titik{x: titikpst2, y: radius2}, sembarang2}
    titikSembarangan := Titik{x: x, y: y}

    inLingkaran1 := didalam(lingkaran1, titikSembarangan)
    inLingkaran2 := didalam(lingkaran2, titikSembarangan)

    if inLingkaran1 && inLingkaran2 {
        fmt.Println("Titik di dalam lingkaran 1 dan 2")
    } else if inLingkaran1 {
        fmt.Println("Titik di dalam lingkaran 1")
    } else if inLingkaran2 {
        fmt.Println("Titik di dalam lingkaran 2")
    } else {
        fmt.Println("Titik di luar lingkaran 1 dan 2")
    }
}
```
![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal1.png)
  
>Pada program di atas terdapat beberapa struct dan beberapa function untuk mempogram sebuah titik pusat yang akan di jelaskan secara rinci

```go
type Titik struct {
    x, y int
}

type Lingkaran struct {
    titikPusat Titik
    radius     int
}
```
>Code di atas merupakan sebuah struct pada pemograman golang dimana titik adalah sebuah struct yang berisikan variabel x dan y dengan tipe data integer dan selanjutnya terdapat struct Lingkaran yang berisikan titikPusak (Titik) yang berrarati pada pemanggilan titikPusat terdapat variabel titik yaitu x dan y

___

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
package main
import (
    "fmt"
    "math"
)

func rataRata(arr []int) float64 {
    var sum int
    for _, v := range arr { // for _ saya jelaskan bahwa perulangan akan di lakukan oleh semua value dan akan di tambahkan
        sum += v
    }
    return float64(sum) / 10
}
  
func standarDeviasi(arr []int) float64 {
    mean := rataRata(arr)
    var sumSquareDif float64
    for _, v := range arr { // perulangan menggunakan for _ unutk menjumlah seluruh value dan
        sumSquareDif += math.Pow(float64(v)-mean, 2) // menggunakan math pow untuk pangkat
    }
    return math.Sqrt(sumSquareDif / float64(len(arr)))
}

func frekuensi(arr []int, target int) int {
    count := 0
    for _, v := range arr {
        if v == target {
            count++
        }
    }
    return count
}

func tampilkanIndeksGanjil(arr []int) {
    fmt.Println("\nElemen dengan indeks ganjil:")
    for i := 0; i < len(arr); i += 2 {
        fmt.Print(arr[i])
    }
    fmt.Println("")
}

func tampilkanIndeksGenap(arr []int) {
    fmt.Println("\nElemen dengan indeks genap:")
    for i := 1; i < len(arr); i += 2 {
        fmt.Print(arr[i])
    }
    fmt.Println(" ")
}

func tampilkanIndeksKelipatanX(arr []int, x int) {
    fmt.Printf("\nElemen dengan indeks kelipatan %d:\n", x)
    for i := 0; i < len(arr); i++ {
        if i%x == 0 {
            fmt.Print(arr[i])
        }
    }
    fmt.Println("")
}

func hapusElemen(arr []int, index int) []int {
    return append(arr[:index], arr[index+1:]...)
}

func main() {
    var x, target, indexToDelete int

    arr := []int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

    // Input untuk kelipatan x
    fmt.Print("\nMasukkan nilai untuk kelipatan x: ")
    fmt.Scan(&x)

    // Input untuk nomer yang ingin dihapus
    fmt.Print("\nMasukkan nomer yang ingin dihapus: ")
    fmt.Scan(&indexToDelete)

    // Input frekuensi
    fmt.Print("\nMasukkan bilangan yang ingin dihitung frekuensinya: ")
    fmt.Scan(&target)

    fmt.Println("\n--- OUTPUT ---")

    // Menampilkan keseluruhan isi array
    fmt.Println("\nIsi keseluruhan array:")
    fmt.Print(arr, "\n")

    // Menampilkan nomor ganjil
    tampilkanIndeksGanjil(arr)

    // Menampilkan nomor genap
    tampilkanIndeksGenap(arr)

    // Menampilkan nomor kelipatan x
    tampilkanIndeksKelipatanX(arr, x)

    // Menghapus slice
    arr = hapusElemen(arr, indexToDelete)
    fmt.Println("\nIsi array setelah elemen dihapus:")
    fmt.Print(arr, "\n")

    // Menampilkan rata-rata
    fmt.Printf("\nRata-rata: %.2f\n", rataRata(arr))

    // Menampilkan standar deviasi
    fmt.Printf("Standar deviasi: %.2f\n", standarDeviasi(arr))

    // Menampilkan frekuensi
    freq := frekuensi(arr, target)
    fmt.Printf("Frekuensi bilangan %d: %d kali\n", target, freq)
}
```
![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal2.png)
>Program di atas adalah program yang sangat banyak dan banyakkk jadi kita akan pecah beberapa bagian. Pada bagian function main atau program utama terdapat sebuah slice array yang saya buat di range 1 hingga 10, Program meminta input tiga hal:
>1. Kelipatan x: Untuk memeriksa angka dalam array yang merupakan kelipatan dari nilai ini.
>2. Indeks yang ingin dihapus: Untuk menghapus elemen array pada indeks tersebut.
>3. Frekuensi: Untuk menghitung berapa kali nilai tertentu muncul dalam array.
>Lalu program ini akan melakukan pemanggilan function atau melakukan output darimenampilkan array, termasuk angka ganjil, angka genap, kelipatan tertentu, rata-rata, dan standar deviasi.
```go
func rataRata(arr []int) float64 {
    var sum int
    for _, v := range arr { // for _ saya jelaskan bahwa perulangan akan di lakukan oleh semua value dan akan di tambahkan
        sum += v
    }
    return float64(sum) / 10
}
  
func standarDeviasi(arr []int) float64 {
    mean := rataRata(arr)
    var sumSquareDif float64
    for _, v := range arr { // perulangan menggunakan for _ unutk menjumlah seluruh value dan
        sumSquareDif += math.Pow(float64(v)-mean, 2) // menggunakan math pow untuk pangkat
    }
    return math.Sqrt(sumSquareDif / float64(len(arr)))
}

func frekuensi(arr []int, target int) int {
    count := 0
    for _, v := range arr {
        if v == target {
            count++
        }
    }
    return count
}

func tampilkanIndeksGanjil(arr []int) {
    fmt.Println("\nElemen dengan indeks ganjil:")
    for i := 0; i < len(arr); i += 2 {
        fmt.Print(arr[i])
    }
    fmt.Println("")
}

func tampilkanIndeksGenap(arr []int) {
    fmt.Println("\nElemen dengan indeks genap:")
    for i := 1; i < len(arr); i += 2 {
        fmt.Print(arr[i])
    }
    fmt.Println(" ")
}

func tampilkanIndeksKelipatanX(arr []int, x int) {
    fmt.Printf("\nElemen dengan indeks kelipatan %d:\n", x)
    for i := 0; i < len(arr); i++ {
        if i%x == 0 {
            fmt.Print(arr[i])
        }
    }
    fmt.Println("")
}

func hapusElemen(arr []int, index int) []int {
    return append(arr[:index], arr[index+1:]...)
}
```
>Code di atas merupakan code function dari tiap tiap perintah mulau dari penghitungan rata rata yang menggunakan perulangan tiap value nya lalu mencari standar deviasi dan yang berikutnya mencari bilangan ganjil dan genap hingga menampilkan kelipatan yang di perintah oleh inputan user.


___
##### soal 3

Sebuah program digunakan untuk menyimpan dan menampilkan nama-nama klub yang memenangkan pertandingan bola pada suatu grup pertandingan. Buatlah program yang digunakan untuk merekap skor pertandingan bola 2 buah klub bola yang berlaga.
Pertama-tama program meminta masukan nama-nama klub yang bertanding, kemudian program meminta masukan skor hasil pertandingan kedua klub tersebut. Yang disimpan dalam array adalah nama-nama klub yang menang saja.
Proses input skor berhenti ketika skor salah satu atau kedua klub tidak valid (negatif). Di akhir program, tampilkan daftar klub yang memenangkan pertandingan.

```go
package main

import (
    "fmt"
)

func main() {
    var klubA, klubB string
    var scoreA, scoreB int
    var juara []string // Slice untuk menyimpan nama klub yang menang

    fmt.Print("Masukkan nama Klub A: ")
    fmt.Scanln(&klubA)
    fmt.Print("Masukkan nama Klub B: ")
    fmt.Scanln(&klubB)

    for {
        fmt.Print("Masukkan skor Klub A dan Klub B: ")
        fmt.Scanln(&scoreA, &scoreB)

        if scoreA < 0 || scoreB < 0 {
            break
        }

        if scoreA > scoreB {
            juara = append(juara, klubA)
        } else if scoreB > scoreA {
            juara = append(juara, klubB)
        }
    }

    for i, winner := range juara {
        fmt.Printf("Hasil %d: %s\n", i+1, winner)
    }
    
    fmt.Println("Pertandingan selesai")

}
```
![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal3.png)
>Pada awal program di jalankan, code akan meminta inputan dari user berupa nama klub A dan B dan setelah itu program akan masuk kedalam perulangan dan akan di jelaskan sebagai berikut

```go
for {
        fmt.Print("Masukkan skor Klub A dan Klub B: ")
        fmt.Scanln(&scoreA, &scoreB)

        if scoreA < 0 || scoreB < 0 {
            break
        }

        if scoreA > scoreB {
            juara = append(juara, klubA)
        } else if scoreB > scoreA {
            juara = append(juara, klubB)
        }
    }
```

>Pada perulangan di atas user akan di minta memasukkan skor untuk club A dan B dan perulangan ini akan berhenti jika terdapat poin -. Setelah itu ada terdapat sebauh base case atau percabangan dimana percabangan itu akan menentukan kemenangan dari sebauh tim terdapat fungsi "Append" yaitu penambahan nilai kedalam slice array

```go
var juara []string // Slice untuk menyimpan nama klub yang menang
```
>code atas adalah sebuah slice yang akan menyimpan kemenangan club yang akan di tambahkan berupa "Append" pada percabangan skor



___
##### Soal 4

Sebuah array digunakan untuk menampung sekumpulan karakter, Anda diminta untuk membuat sebuah subprogram untuk melakukan membalikkan urutan isi array dan memeriksa apakah membentuk palindrom.

```go
package main

import "fmt"

const NMAX int = 127
type tabel [NMAX]rune

func isiArray(t *tabel, n *int) {
    *n = 0
    var c rune
    
    for *n < NMAX {
    
        fmt.Scanf("%c", &c)
        
        if c == '.' {
            break
        }

        t[*n] = c
        *n++
    }
}

func cetakArray(t tabel, n int) {
    for i := 0; i < n; i++ {
        fmt.Printf("%c ", t[i])
    }
    fmt.Println()
}

func balikanArray(t *tabel, n int) {
    for i := 0; i < n/2; i++ {
        t[i], t[n-1-i] = t[n-1-i], t[i]
    }
}

func palindrom(t tabel, n int) bool {
    for i := 0; i < n/2; i++ {
        if t[i] != t[n-1-i] {
            return false
        }
    }
    return true
}

func main() {
    var tab tabel
    var m int

    isiArray(&tab, &m)

    fmt.Println("\nTeks: ")
    cetakArray(tab, m)

    balikanArray(&tab, m)

    fmt.Println("\nReverse teks: ")
    cetakArray(tab, m)

    fmt.Println("\nPalindrom: ", palindrom(tab, m))
}
```

![](MODUL%207%20STRUCT%20&%20ARRAY/Output/soal4.png)

>Program ini ngelola array yang isinya karakter-karakter, yang diambil dari input user. Maksimal ada 127 karakter, dan kalau udah masuk titik (.) sebagai tanda berhenti, inputnya stop. Ada beberapa fungsi nih, kayak "isiArray" yang bakal ngisi array itu dengan karakter-karakter yang dimasukin, terus "cetakArray" buat nampilinnya. Terus ada juga fungsi "balikanArray" buat ngabalikin urutan karakter, jadi teks yang tadinya ditulis dari kiri ke kanan jadi kebalik, gitu. Terakhir, ada fungsi "palindrom" yang ngecek apakah teks itu tetep sama kalau dibaca dari depan atau belakang. 