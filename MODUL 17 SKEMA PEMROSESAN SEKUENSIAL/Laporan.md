<h1 align="center">Laporan Praktikum Modul 17 <br> SKEMA PEMROSESAN SEKUENSIAL </h1>
___
<h4 align="center">Nanda Bagus Priambodo - 103112430007 </h4>
### Dasar Teori Skema Pemrosesan Sekuensial
Dengan dipersenjatai bentuk perulangan dan bentuk percabangan, banyak problem komputasi yang dapat diselesaikan. Berikut ini beberapa skema (pola) yang umum ditemukan untuk pemrosesan data (secara sekuensial).

___

## Guided

### Soal 1

Aldi memiliki daftar nilai ulangan matematika temannya: 75, 60, 90, 85, dan 70. Ia ingin mengurutkan nilai tersebut dari yang terkecil ke yang terbesar menggunakan metode Bubble Sort. Pertanyaan:

1. Tunjukkan proses pengurutan nilai menggunakan Bubble Sort hingga semua nilai terurut.
2. Berapa kali pertukaran (swap) terjadi dalam proses ini?

```go
package main

import "fmt"

func BubbleSort(nilai []int) []int {

    swap := 0

    for i := 0; i < len(nilai)-1; i++ {
        for j := 0; j < len(nilai)-i-1; j++ {
            if nilai[j] > nilai[j+1] {
                nilai[j], nilai[j+1] = nilai[j+1], nilai[j]
                swap++
            }
        }
    }

    fmt.Println(swap)
    return nilai
}

  

func main() {
    nilai := []int{75, 60, 90, 85, 70}
    fmt.Println(BubbleSort(nilai))
}
```
![](Output/gd1.png)
>Program ini dimulai dengan mendefinisikan sebuah array yang berisi angka-angka yang akan diurutkan. Fungsi BubbleSort kemudian dipanggil untuk mengurutkan array dari angka terkecil ke terbesar. Terdapat 2 Perulangan yaitu perulangan luar dan dalam yang akan mengurutkan bilangan dari angka terkecil ke terbesar. For di dalam membandingkan angka pertma dengan angka di kanan nya dan jika angka sudah selesai maka lanjut untuk perulangan luar yang akan menjalankan angka ke 2 untuk di bandingkan


___
## Unguided

### soal 1

Diberikan sejumlah bilangan real yang diakhiri dengan marker 9999, cari rerata dari bilangan-bilangan tersebut.

```go
package main

import "fmt"

func main() {
    var jumlah, total, angka int

    for {
        fmt.Scan(&angka)

        if angka == 9999 {
            break
        }

        jumlah += angka
        total++
    }

    rataRata := float64(jumlah) / float64(total)
    fmt.Printf("Rata-rata dari angka yang dimasukkan: %.2f\n", rataRata)
}
```
![](Output/soal1.png)
  
>Code di atas merupakan sebuah program mencari rata rata dan akan berhenti jika user menginputkan 9999. Program tersebut terdapat sebuah perulangan dan di dalam perulangan terdapat sebauh percabangan kondisi serta jika selesai maka total inputan user akan di bagi dengan total perulangan dan akan menghasilkan rata-rata.

### soal 2

Diberikan string x dan n buah string. x adalah data pertama yang dibaca, n adalah data bilangan yang dibaca kedua, dan n data berikutnya adalah data string. Buat algoritma untuk menjawab pertanyaan berikut:
a. Apakah string x ada dalam kumpulan n data string tersebut?
b. Pada posisi ke berapa string x tersebut ditemukan?
c. Ada berapakah string x dalam kumpulan n data string tersebut?
d. Adakah sedikitnya dua string x dalam n data string tersebut?

```go
package main

import "fmt"

func main() {
    var target string
    var banyak int

    fmt.Print("Masukan kata yang akan dicari: ")
    fmt.Scanln(&target)

    fmt.Print("Masukan banyak data: ")
    fmt.Scanln(&banyak)

    cariKata(target, banyak)

}

func cariKata(target string, banyak int) {

    var posisi []int

    for i := 1; i <= banyak; i++ {
        var input string
        fmt.Print("Masukan kata ke-", i, ": ")
        fmt.Scanln(&input)
        if input == target {
            posisi = append(posisi, i)
        }
    }

    if len(posisi) > 0 {
        fmt.Print("Kata ditemukan pada posisi: ")
        for i, p := range posisi {
            if i > 0 {
                fmt.Print(", ")
            }
            fmt.Print(p)
        }
        fmt.Println("\nJumlah kemunculan:", len(posisi))
        if len(posisi) >= 2 {
            fmt.Println("Ada sedikitnya dua kata", target)
        } else {
            fmt.Println("Hanya ada satu string", target)
        }
    } else {
        fmt.Println("Kata tidak ditemukan.")
    }
}
```
![](Output/soal2.png) 
>Code di atas berfungsi untuk mencari dan menampilkan posisi kemunculan sebuah kata dan sejumlah inputan user. Program meminta user untuk menginputkan kata yang ingin dicari dan jumlah data kata yang akan dimasukkan . Selanjutnya, program melakukan perulangan sebanyak jumlah data untuk menerima input kata satu per satu, dan jika ada kata yang sama dengan target, akan disimpan. Setelah semua data dimasukkan, program akan menampilkan posisi kemunculan kata target. Jika kata tidak ditemukan sama sekali, maka akan ditampilkan pesan bahwa kata tidak ditemukan.

### soal 3

Empat daerah A, B, C, dan D yang berdekatan ingin mengukur curah hujan. Keempat daerah tersebut digambarkan pada bidang berikut: Misal curah hujan dihitung berdasarkan banyaknya tetesan air hujan. Setiap tetesan berukuran 0.0001 ml curah hujan. Tetesan air hujan turun secara acak dari titik (0,0) sampai (1,1). Jika diterima input yang menyatakan banyaknya tetesan air hujan. Tentukan curah hujan untuk keempat daerah tersebut.

Buatlah program yang menerima input berupa banyaknya tetesan air hujan. Kemudian buat koordinat/titik (x, y) secara acak dengan menggunakan fungsi rand.Float64(). Hitung dan tampilkan banyaknya tetesan yang jatuh pada daerah A, B, C dan D. Konversikan satu tetesan berukuran 0.0001 milimeter.

Catatan: Lihat lampiran untuk informasi menggunakan paket math/rand untuk menggunakan rand.Float64() yang menghasilkan bilangan riil acak 0..1

```go
package main

import (
    "fmt"
    "math/rand"
)

func inisialisasi() int {

    var jumlahTetesan int
    fmt.Print("Masukkan jumlah tetesan air hujan: ")
    fmt.Scan(&jumlahTetesan)
    return jumlahTetesan
}

func tetesHujan(jumlahTetesan int) (int, int, int, int) {
    var daerahA, daerahB, daerahC, daerahD int
    
    for i := 0; i < jumlahTetesan; i++ {
        x := rand.Float64()
        y := rand.Float64()

        if x < 0.5 && y < 0.5 {
            daerahA++
        } else if x >= 0.5 && y < 0.5 {
            daerahB++
        } else if x < 0.5 && y >= 0.5 {
            daerahC++
        } else {
            daerahD++
        }
    }
    return daerahA, daerahB, daerahC, daerahD
}

func hitungCurahHujan(daerahA, daerahB, daerahC, daerahD int, ukuranTetesan float64) (float64, float64, float64, float64) {

    curahHujanA := float64(daerahA) * ukuranTetesan
    curahHujanB := float64(daerahB) * ukuranTetesan
    curahHujanC := float64(daerahC) * ukuranTetesan
    curahHujanD := float64(daerahD) * ukuranTetesan
    return curahHujanA, curahHujanB, curahHujanC, curahHujanD
}

func tampilkanHasil(curahHujanA, curahHujanB, curahHujanC, curahHujanD float64) {

    fmt.Printf("Curah hujan daerah A: %.3f milimeter\n", curahHujanA)
    fmt.Printf("Curah hujan daerah B: %.3f milimeter\n", curahHujanB)
    fmt.Printf("Curah hujan daerah C: %.3f milimeter\n", curahHujanC)
    fmt.Printf("Curah hujan daerah D: %.3f milimeter\n", curahHujanD)
}

func main() {

    ukuranTetesan := 0.0001

    jumlahTetesan := inisialisasi()
    daerahA, daerahB, daerahC, daerahD := tetesHujan(jumlahTetesan)
    curahHujanA, curahHujanB, curahHujanC, curahHujanD := hitungCurahHujan(daerahA, daerahB, daerahC, daerahD, ukuranTetesan)
    tampilkanHasil(curahHujanA, curahHujanB, curahHujanC, curahHujanD)

}
```
![](Output/soal3.png)
> Code di atas merupakan perhitungan  hujan pada empat daerah berdasarkan jumlah tetesan air hujan yang diinputkan user. Program diawali meminta input jumlah tetesan, lalu setiap tetesan diibaratkan jatuh secara acak di koordinat (x, y) antara 0 hingga 1. Posisi koordinat, tetesan ke dalam empat daerah: A (x<0.5, y<0.5), B (x≥0.5, y<0.5), C (x<0.5, y≥0.5), dan D (x≥0.5, y≥0.5). Setiap daerah dihitung jumlah tetesannya dan dikalikan dengan volume satu tetesan (0.0001) untuk mendapatkan curah hujan. Terakhir, program menampilkan curah hujan masing-masing daerah dengan format tiga angka di belakang koma.

### soal 4

Berdasarkan formula Leibniz, nilai π dapat dinyatakan sebagai deret harmonik ganti sebagai berikut:
1−13+15−17+19−⋯=𝜋4
Suku ke-i dinyatakan sebagai 𝑆𝑖 dan jumlah deret adalah 𝑆. Apabila diketahui suku pertama 𝑆1=1, suku kedua 𝑆2=−13 . Temukan rumus untuk suku ke-𝒊 atau 𝑆𝑖.
Berdasarkan rumus tersebut, buatlah program yang menghitung 𝑆 untuk 1000000 suku pertama.
Perhatikan contoh sesi interaksi program di bawah ini (teks bergaris bawah adalah input/read):

Setelah jalan, modifikasi program tersebut agar menyimpan nilai dua suku yang bersebelahan, 𝑆𝑖 dan 𝑆𝑖+1. Buatlah agar program tersebut sekarang berhenti apabila selisih dari kedua suku tersebut tidak lebih dari 0.00001.
Perhatikan contoh sesi interaksi program di bawah ini (teks bergaris bawah adalah input/read):


```go
package main

import (
    "fmt"
    "math"
)

func pembulatan(x float64) float64 {
    return math.Trunc(x*1e10) / 1e10
}

func hitungPI(n int) (float64, float64, int) {
    total, sebelumnya := 0.0, 0.0

    for i, tanda := 0, 1.0; i < n; i, tanda = i+1, -tanda {
        total += tanda / float64(2*i+1)
        sekarang := total * 4

        if i > 0 && math.Abs(sekarang-sebelumnya) < 0.00001 {
            return pembulatan(sebelumnya), pembulatan(sekarang), i + 1
        }
        sebelumnya = sekarang
    }
    return pembulatan(sebelumnya), pembulatan(sebelumnya), n
}

func main() {

    var suku int

    fmt.Print("N suku pertama: ")
    fmt.Scan(&suku)

    pi1, pi2, iter := hitungPI(suku)

    fmt.Printf("Hasil PI: %.10f\n", pi1)
    fmt.Printf("Hasil PI: %.10f\n", pi2)
    fmt.Printf("Pada i ke: %d\n", iter)
}
```
![](Output/soal4.png)
>Program ini menghitung nilai pendekatan konstanta π (pi) menggunakan deret Leibniz hingga jumlah suku yang ditentukan pengguna. Setiap iterasi menambahkan atau mengurangi suku ke total, lalu mengalikan hasilnya dengan 4. Program membandingkan dua hasil pendekatan terakhir dan berhenti lebih awal jika selisihnya kurang dari 0.00001. Nilai π kemudian dibulatkan hingga 10 angka di belakang koma dan ditampilkan bersama dengan iterasi keberapa pendekatan tersebut stabil.

### soal 5

Monti bekerja pada sebuah kedai pizza, saking ramainya kedai tersebut membuat Monti tidak ada waktu untuk bersantai. Suatu ketika saat sedang menaburkan topping pada pizza yang diletakkan pada wadah berbentuk persegi, terpikirkan oleh Monti cara menghitung berapa banyak topping yang dia butuhkan, dan cara menghitung nilai 𝝅.

Ilustrasi seperti gambar yang diberikan di bawah, topping adalah lingkaran-lingkaran kecil. Ada yang tepat berada di atas pizza, dan ada yang jatuh di dalam kotak tetapi berada di luar pizza. Apabila luas pizza yang memiliki radius r adalah 𝐿𝑢𝑎𝑠𝑃𝑖𝑧𝑧𝑎=𝜋𝑟2 dan luas wadah pizza yang memiliki panjang sisi 𝑑=2𝑟 adalah 𝐿𝑢𝑎𝑠𝑊𝑎𝑑𝑎ℎ=𝑑2=4𝑟2, maka diperoleh perbandingan luas kedua bidang tersebut 𝐿𝑢𝑎𝑠𝑃𝑖𝑧𝑧𝑎𝐿𝑢𝑎𝑠𝑊𝑎𝑑𝑎ℎ=𝜋𝑟24𝑟2=𝜋4

Persamaan lingkaran adalah (𝑥−𝑥𝑐)2+(𝑦−𝑦𝑐)2=𝑟2 dengan titik pusat lingkaran adalah (𝑥𝑐,𝑦𝑐). Suatu titik sembarang (𝑥,𝑦) dikatakan berada di dalam lingkaran apabila memenuhi ketidaksamaan: (𝑥−𝑥𝑐)2+(𝑦−𝑦𝑐)2≤𝑟2

Pada ilustrasi topping berbentuk bulat kecil merah dan biru pada gambar adalah titik-titik (𝑥,𝑦) acak pada sebuah wadah yang berisi pizza. Dengan jumlah yang sangat banyak dan ditaburkan merata (secara acak), maka kita bisa mengetahui berapa banyak titik/topping yang berada tepat di dalam pizza menggunakan ketidaksamaan di atas.

Buatlah program yang menerima input berupa banyaknya topping yang akan ditaburkan, kemudian buat titik acak (𝑥,𝑦) dari bilangan acak riil pada kisaran nilai 0 hingga 1 sebanyak topping yang diberikan. Hitung dan tampilkan berapa banyak topping yang jatuh tepat di atas pizza.

Titik pusat pizza adalah (0.5, 0.5) dan jari-jari pizza adalah 0.5 satuan wadah.
Perhatikan contoh sesi interaksi program di bawah ini (teks bergaris bawah adalah input/read):

Apabila topping yang ditaburkan oleh Monti secara merata berjumlah yang sangat banyak, maka topping akan menutupi keseluruhan wadah pizza. Luas Pizza sebanding dengan topping yang berada pada pizza, sedangkan Luas Wadah sebanding dengan banyaknya topping yang ditaburkan. Dengan menggunakan rumus perbandingan luas yang diberikan di atas, maka nilai konstanta 𝜋 dapat dihitung.

Modifikasi program di atas sehingga dapat menghitung dan menampilkan nilai konstanta π.
Perhatikan contoh sesi interaksi program di bawah ini (teks bergaris bawah adalah input/read):

```go
package main

import (
    "fmt"
    "math/rand"
)

func ambilTopping() int {
    var jumlah int

    fmt.Print("Banyak Topping: ")
    fmt.Scan(&jumlah)
    return jumlah
}

func cekDiPizza(x, y, cx, cy, r float64) bool {
    return (x-cx)*(x-cx)+(y-cy)*(y-cy) <= r*r
}

func hitungTopping(n int, cx, cy, r float64) int {

    toppingCount := 0
    for i := 0; i < n; i++ {
        x := rand.Float64()
        y := rand.Float64()
        
        if cekDiPizza(x, y, cx, cy, r) {
            toppingCount++
        }
    }
    return toppingCount
}

func perkirakanPI(n, count int) float64 {
    return float64(count) / float64(n) * 4
}

func main() {

    n := ambilTopping()
    cx, cy, r := 0.5, 0.5, 0.5
    toppingCount := hitungTopping(n, cx, cy, r)

    fmt.Printf("Topping pada Pizza: %d\n", toppingCount)

    pi := perkirakanPI(n, toppingCount)
    fmt.Printf("PI : %.10f\n", pi)

}
```
![](Output/soal5.png)
> Program di atas menggunakan metode Monte Carlo untuk memperkirakan nilai π dengan mensimulasikan pelemparan topping secara acak ke dalam persegi yang berisi lingkaran (pizza). Titik-titik yang jatuh dalam lingkaran dihitung, lalu dipakai untuk menghitung π dengan rumus `π ≈ 4 × (titik dalam lingkaran / total titik)`. Hasilnya ditampilkan sebagai jumlah topping dalam pizza dan nilai π hingga 10 digit desimal.