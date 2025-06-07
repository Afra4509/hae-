# Identifikasi Lengkap Komponen Programming dalam Aplikasi NutriTrack Line 1-612

## a. Tipe Data

### 1. **Numeric (Bilangan Desimal)**
```r
# Baris 13-15: Data median tinggi badan WHO
median_tb = c(49.9, 58.4, 65.7, 70.6, 75.7, 78.4, 80.7, 87.8, 94.9, 102.9, 110.0,
              49.1, 57.3, 64.3, 69.8, 74.0, 76.6, 79.2, 86.4, 93.9, 101.6, 108.4)
```
**Kegunaan**: Menyimpan nilai median tinggi badan dalam cm sesuai standar WHO untuk perhitungan Z-score.

```r
# Baris 16: Data standar deviasi
sd_tb = rep(c(1.8, 2.4, 2.7, 2.9, 3.3, 3.2, 3.3, 3.4, 3.8, 4.3, 4.9), 2)
```
**Kegunaan**: Menyimpan nilai standar deviasi untuk menghitung sebaran normal dalam analisis stunting.

```r
# Baris 22-26: Data prevalensi stunting per provinsi
prevalensi = c(6.2, 3.0, 8.1, 2.5, 2.7, 1.4, 3.9, 2.8, 3.3, 3.1, 1.6, 4.9, 8.6, 7.7, 
               5.8, 2.9, 3.5, 12.7, 14.8, 8.7, 11.1, 8.2, 9.0, 6.7, 1.7, 10.4, 7.3, 
               10.3, 5.4, 23.9, 5.4, 8.7, 9.3, 9.9, 4.4, 12.7, 10.1, 7.8)
```
**Kegunaan**: Menyimpan persentase prevalensi stunting di setiap provinsi untuk analisis geografis.

### 2. **Integer (Bilangan Bulat)**
```r
# Baris 11: Usia dalam bulan
age_months = rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2)
```
**Kegunaan**: Menyimpan rentang usia balita dalam bulan untuk standar pertumbuhan WHO.

```r
# Baris 19-21: Jumlah balita per provinsi
jml_balita = c(394129, 946365, 377410, 368260, 209492, 588096, 107916, 532246, ...)
```
**Kegunaan**: Menyimpan jumlah populasi balita di setiap provinsi untuk analisis demografis.

```r
# Baris 30-33: Data total nasional
jml_balita = 15904224,
jml_stunting = 728559 + 238660,
pendek = 728559,
sangat_pendek = 238660
```
**Kegunaan**: Menyimpan agregasi data stunting nasional untuk statistik keseluruhan.

### 3. **Character (Teks/String)**
```r
# Baris 12: Kategori jenis kelamin
sex = rep(c("Male", "Female"), each = 11)
```
**Kegunaan**: Menyimpan kategori gender untuk diferensiasi standar pertumbuhan.

```r
# Baris 17-18: Nama provinsi
provinsi = c("ACEH", "SUMATERA UTARA", "SUMATERA BARAT", "RIAU", "JAMBI", ...)
```
**Kegunaan**: Menyimpan identifier wilayah geografis Indonesia untuk mapping data stunting.

```r
# Baris 34: Label total
provinsi = "TOTAL"
```
**Kegunaan**: Memberikan label untuk baris total dalam dataset.

```r
# Baris 44-45: Konfigurasi tema dashboard
skin = "blue"
title = span(icon("child-reaching"), "NutriTrack | Deteksi Dini Stunting")
```
**Kegunaan**: Mengatur tampilan visual dan branding aplikasi.

### 4. **Logical (Boolean)**
```r
# Baris 183: Kontrol pengurutan data
checkboxInput("sort_data", "Urutkan dari Tertinggi", value = TRUE)
```
**Kegunaan**: Menyimpan status TRUE/FALSE untuk mengontrol pengurutan data pada visualisasi.

```r
# Baris 68: Status header solid
solidHeader = TRUE
```
**Kegunaan**: Mengatur style header box dalam dashboard (solid atau transparan).

## b. Struktur Data

### 1. **Data Frame**
```r
# Baris 10-16: Dataset standar WHO
who_data <- data.frame(
  age_months = rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2),
  sex = rep(c("Male", "Female"), each = 11),
  median_tb = c(...),
  sd_tb = rep(c(...), 2)
)
```
**Kegunaan**: Menyimpan referensi standar pertumbuhan WHO dalam format tabular terstruktur untuk lookup Z-score.

```r
# Baris 19-27: Dataset stunting Indonesia
stunting_data_indonesia <- data.frame(
  provinsi = c("ACEH", "SUMATERA UTARA", ...),
  jml_balita = c(394129, 946365, ...),
  jml_stunting = c(24603, 28089, ...),
  pendek = c(18641, 19631, ...),
  sangat_pendek = c(5962, 8458, ...),
  prevalensi = c(6.2, 3.0, 8.1, ...),
  tahun = rep(2023, 38)
)
```
**Kegunaan**: Menyimpan data komprehensif stunting per provinsi dalam struktur relational database.

```r
# Baris 30-36: Data total nasional
total_row <- data.frame(
  provinsi = "TOTAL",
  jml_balita = 15904224,
  jml_stunting = 728559 + 238660,
  pendek = 728559,
  sangat_pendek = 238660,
  prevalensi = 6.1,
  tahun = 2023
)
```
**Kegunaan**: Menyimpan data agregat nasional dalam format yang konsisten dengan data provinsi.

### 2. **Vector**
```r
# Baris 11: Vector integer untuk usia
c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60)
```
**Kegunaan**: Menyimpan sekuens usia dalam bulan untuk referensi kurva pertumbuhan.

```r
# Baris 12: Vector karakter untuk gender
c("Male", "Female")
```
**Kegunaan**: Menyimpan dua kategori jenis kelamin untuk klasifikasi standar WHO.

```r
# Baris 13-15: Vector numeric untuk median tinggi badan
c(49.9, 58.4, 65.7, 70.6, 75.7, 78.4, 80.7, 87.8, 94.9, 102.9, 110.0,
  49.1, 57.3, 64.3, 69.8, 74.0, 76.6, 79.2, 86.4, 93.9, 101.6, 108.4)
```
**Kegunaan**: Menyimpan nilai referensi tinggi badan normal untuk setiap usia dan gender.

### 3. **List (dalam struktur UI)**
```r
# Baris 85-90: Menu navigasi
sidebarMenu(
  id = "tabs",
  menuItem("Kalkulator Stunting", tabName = "calculator", icon = icon("calculator")),
  menuItem("Rekomendasi Gizi", tabName = "nutrition", icon = icon("bowl-food")),
  menuItem("Data Stunting Indonesia", tabName = "data", icon = icon("map")),
  menuItem("Tentang Aplikasi", tabName = "about", icon = icon("circle-info"))
)
```
**Kegunaan**: Mengorganisir item menu dalam struktur list untuk navigasi multi-tab.

```r
# Baris 107-111: Pilihan radio button
choices = c("Laki-laki" = "Male", "Perempuan" = "Female")
```
**Kegunaan**: Menyimpan pasangan label-value untuk input jenis kelamin.

```r
# Baris 174-177: Pilihan dropdown chart
choices = c("Persentase Stunting" = "percentage", 
            "Jumlah Kasus Stunting" = "cases",
            "Jumlah Balita" = "toddlers")
```
**Kegunaan**: Menyimpan opsi visualisasi data dengan key-value mapping.

### 4. **Named List (lapply structure)**
```r
# Baris 235-240: List untuk generate cards nutrisi
lapply(list(
  list("Protein", "egg", "Telur, ikan, ayam, daging, tempe, tahu, kacang-kacangan"),
  list("Kalsium", "bone", "Susu, keju, yogurt, ikan teri, sayuran hijau"),
  list("Zat Besi", "leaf", "Daging merah, bayam, kacang-kacangan, sayuran hijau"),
  list("Cairan", "glass-water", "Minimal 8-10 gelas air putih per hari")
), function(x) { ... })
```
**Kegunaan**: Menyimpan data terstruktur untuk generate multiple UI components dengan pola yang sama.

## c. Variable

### 1. **Input Variables (User Interface)**
```r
# Baris 101: Variable nama anak
textInput("name", "Nama Anak", placeholder = "Masukkan nama anak")
```
**Kegunaan**: Variable `name` menyimpan input nama anak dari user untuk personalisasi hasil analisis.

```r
# Baris 102: Variable usia anak
textInput("age_input", "Usia (bulan)", placeholder = "Contoh: 12 atau usia anak 12")
```
**Kegunaan**: Variable `age_input` menyimpan usia anak dalam bulan untuk perhitungan Z-score.

```r
# Baris 105: Variable jenis kelamin
awesomeRadio("sex", "Jenis Kelamin", choices = c("Laki-laki" = "Male", "Perempuan" = "Female"))
```
**Kegunaan**: Variable `sex` menyimpan pilihan gender untuk menentukan standar WHO yang sesuai.

```r
# Baris 106: Variable tinggi badan
textInput("height_input", "Tinggi Badan (cm)", placeholder = "Contoh: 60 atau tb anak 60")
```
**Kegunaan**: Variable `height_input` menyimpan tinggi badan anak untuk analisis status gizi.

### 2. **Control Variables**
```r
# Baris 84: Variable ID menu
id = "tabs"
```
**Kegunaan**: Variable `tabs` mengontrol navigasi antar halaman dalam dashboard.

```r
# Baris 108: Variable tombol aksi
actionBttn("calculate", "Analisis Status Gizi", ...)
```
**Kegunaan**: Variable `calculate` trigger untuk memulai perhitungan status gizi anak.

```r
# Baris 174: Variable tipe chart
selectInput("chart_type", "Tampilkan Berdasarkan:", ...)
```
**Kegunaan**: Variable `chart_type` mengontrol jenis visualisasi data yang ditampilkan.

```r
# Baris 183: Variable sorting
checkboxInput("sort_data", "Urutkan dari Tertinggi", value = TRUE)
```
**Kegunaan**: Variable `sort_data` mengontrol pengurutan data dari tinggi ke rendah atau sebaliknya.

### 3. **Configuration Variables**
```r
# Baris 43: Variable tema aplikasi
skin = "blue"
```
**Kegunaan**: Variable `skin` menentukan color scheme dashboard (blue theme).

```r
# Baris 46: Variable lebar title
titleWidth = 350
```
**Kegunaan**: Variable `titleWidth` mengatur lebar area judul dashboard dalam pixel.

```r
# Baris 49: Variable lebar sidebar
width = 300
```
**Kegunaan**: Variable `width` menentukan lebar panel sidebar navigasi.

### 4. **Output Variables**
```r
# Baris 128: Variable output nama anak
textOutput("child_name")
```
**Kegunaan**: Variable `child_name` menampilkan nama anak yang diinput user di hasil analisis.

```r
# Baris 135: Variable tabel hasil
tableOutput("results_table")
```
**Kegunaan**: Variable `results_table` menampilkan tabel hasil perhitungan status gizi.

```r
# Baris 163: Variable plot pertumbuhan
plotlyOutput("growth_plot")
```
**Kegunaan**: Variable `growth_plot` menampilkan kurva pertumbuhan interaktif.

## d. Operasi Aritmatika

### 1. **Penjumlahan (+)**
```r
# Baris 32: Total kasus stunting
jml_stunting = 728559 + 238660
```
**Kegunaan**: Menghitung total kasus stunting nasional dengan menjumlahkan kategori pendek dan sangat pendek.

### 2. **Pengulangan/Repetisi (rep)**
```r
# Baris 11: Mengulang usia untuk 2 gender
rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2)
```
**Kegunaan**: Mengulangi sequence usia 2 kali (untuk laki-laki dan perempuan) dalam dataset WHO.

```r
# Baris 16: Mengulang standar deviasi
rep(c(1.8, 2.4, 2.7, 2.9, 3.3, 3.2, 3.3, 3.4, 3.8, 4.3, 4.9), 2)
```
**Kegunaan**: Mengulangi nilai SD untuk kedua jenis kelamin dalam perhitungan Z-score.

```r
# Baris 27: Mengulang tahun
rep(2023, 38)
```
**Kegunaan**: Memberikan label tahun 2023 untuk semua 38 provinsi dalam dataset.

### 3. **Operasi dalam Fungsi c() - Concatenation**
```r
# Baris 13-15: Menggabungkan data median untuk laki-laki dan perempuan
c(49.9, 58.4, ..., 110.0,    # Data laki-laki
  49.1, 57.3, ..., 108.4)    # Data perempuan
```
**Kegunaan**: Menggabungkan dua set data median tinggi badan menjadi satu vector.

### 4. **Perhitungan Z-Score (Implicit dalam server logic)**
```r
# Formula yang akan digunakan di server:
# z_score = (tinggi_anak - median_who) / sd_who
```
**Kegunaan**: Menghitung deviasi tinggi anak dari standar WHO untuk klasifikasi stunting.

## e. Operasi Logika

### 1. **Conditional Rendering (==)**
```r
# Baris 93-94: Kondisi tampil panel
conditionalPanel(
  condition = "input.tabs == 'calculator'",
  # Panel hanya muncul jika tab calculator aktif
)
```
**Kegunaan**: Menampilkan form input hanya ketika user berada di tab "Kalkulator Stunting".

### 2. **Perbandingan untuk Klasifikasi Stunting**
```r
# Logika yang akan diimplementasi di server:
# if (z_score >= -2) → status = "Normal"
# else if (z_score >= -3 && z_score < -2) → status = "Stunting"
# else if (z_score < -3) → status = "Stunting Berat"
```
**Kegunaan**: Mengklasifikasikan status gizi anak berdasarkan threshold Z-score WHO.

### 3. **Boolean Logic dalam UI Controls**
```r
# Baris 68, 143, 149: Status header box
solidHeader = TRUE
```
**Kegunaan**: Mengatur style box dengan header solid (TRUE) atau transparan (FALSE).

```r
# Baris 105: Default selection
selected = "Male"
```
**Kegunaan**: Menetapkan pilihan default jenis kelamin laki-laki.

```r
# Baris 183: Default checkbox state
value = TRUE
```
**Kegunaan**: Mengatur checkbox "Urutkan dari Tertinggi" aktif secara default.

### 4. **Logical AND/OR dalam Conditional**
```r
# Dalam server logic untuk filter data:
# if (input$table_search != "" && nchar(input$table_search) > 0)
```
**Kegunaan**: Memfilter tabel hanya jika search box tidak kosong DAN memiliki karakter.

## f. Percabangan (Branching)

### 1. **Conditional Panel - Tab Switching**
```r
# Baris 93-112: Percabangan berdasarkan tab aktif
conditionalPanel(
  condition = "input.tabs == 'calculator'",
  hr(),
  div(class = "sidebar-header", "Data Anak"),
  textInput("name", "Nama Anak", ...),
  textInput("age_input", "Usia (bulan)", ...),
  awesomeRadio("sex", "Jenis Kelamin", ...),
  textInput("height_input", "Tinggi Badan (cm)", ...),
  actionBttn("calculate", "Analisis Status Gizi", ...)
)
```
**Kegunaan**: Menampilkan form input data anak HANYA jika user memilih tab "Kalkulator Stunting".

### 2. **Tab Items - Multi-way Branching**
```r
# Baris 119-121: Percabangan konten berdasarkan tab
tabItems(
  tabItem(tabName = "calculator", 
    # Konten halaman kalkulator
  ),
  tabItem(tabName = "nutrition", 
    # Konten halaman rekomendasi gizi
  ),
  tabItem(tabName = "data", 
    # Konten halaman data stunting
  ),
  tabItem(tabName = "about", 
    # Konten halaman tentang aplikasi
  )
)
```
**Kegunaan**: Menentukan konten mana yang akan ditampilkan berdasarkan tab yang dipilih user.

### 3. **Conditional Content dalam Tab**
```r
# Baris 201-206: Percabangan dalam tab box
tabBox(
  width = 12,
  id = "nutritionTabs",
  tabPanel(title = span(icon("baby"), "0-6 Bulan"), ...),
  tabPanel(title = span(icon("baby-carriage"), "6-12 Bulan"), ...),
  tabPanel(title = span(icon("child"), "1-3 Tahun"), ...),
  tabPanel(title = span(icon("children"), "3-5 Tahun"), ...)
)
```
**Kegunaan**: Membagi rekomendasi gizi berdasarkan kelompok usia dengan konten yang berbeda.

### 4. **Dropdown Selection - Value-based Branching**
```r
# Baris 174-177: Percabangan visualisasi
selectInput("chart_type", "Tampilkan Berdasarkan:",
  choices = c("Persentase Stunting" = "percentage", 
              "Jumlah Kasus Stunting" = "cases",
              "Jumlah Balita" = "toddlers"),
  selected = "percentage")
```
**Kegunaan**: User dapat memilih jenis data yang ingin divisualisasikan dalam chart.

## g. Pengulangan (Loops/Iteration)

### 1. **rep() - Numeric Repetition**
```r
# Baris 11: Mengulang sequence usia
rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2)
```
**Kegunaan**: Mengulangi pola usia 2 kali untuk membuat dataset laki-laki dan perempuan.

```r
# Baris 12: Mengulang setiap elemen
rep(c("Male", "Female"), each = 11)
```
**Kegunaan**: Mengulang "Male" 11 kali, kemudian "Female" 11 kali untuk mapping gender-usia.

```r
# Baris 27: Mengulang nilai konstan
tahun = rep(2023, 38)
```
**Kegunaan**: Memberikan label tahun 2023 untuk semua 38 provinsi Indonesia.

### 2. **lapply() - List Iteration untuk UI Generation**
```r
# Baris 235-245: Iterasi untuk membuat cards nutrisi
lapply(list(
  list("Protein", "egg", "Telur, ikan, ayam, daging, tempe, tahu, kacang-kacangan"),
  list("Kalsium", "bone", "Susu, keju, yogurt, ikan teri, sayuran hijau"),
  list("Zat Besi", "leaf", "Daging merah, bayam, kacang-kacangan, sayuran hijau"),
  list("Cairan", "glass-water", "Minimal 8-10 gelas air putih per hari")
), function(x) {
  div(class = "col-md-6",
      div(class = "food-card",
          icon(x[[2]], class = "fa-2x food-icon"),
          h5(x[[1]]),
          p(x[[3]])
      )
  )
})
```
**Kegunaan**: Membuat 4 card informasi nutrisi secara otomatis dengan struktur HTML yang sama.

```r
# Baris 290-300: Iterasi untuk menu MPASI
lapply(list(
  list("Bubur susu + ikan", "fish", "Beras/tepung beras + ASI/susu formula + ikan hancur + wortel"),
  list("Pure buah", "apple-whole", "Pisang, alpukat, atau pepaya yang dihaluskan"),
  list("Bubur ayam", "drumstick-bite", "Beras + ayam cincang + bayam + wortel + kaldu ayam"),
  list("Bubur kacang hijau", "seedling", "Kacang hijau + gula aren sedikit + santan")
), function(x) {
  div(class = "col-md-6",
      div(class = "food-card",
          icon(x[[2]], class = "fa-2x food-icon"),
          h5(x[[1]]),
          p(x[[3]])
      )
  )
})
```
**Kegunaan**: Generate 4 card contoh menu MPASI dengan template yang konsisten.

### 3. **Implicit Loops dalam Vector Creation**
```r
# Baris 19-21: Membuat vector dengan 38 elemen
jml_balita = c(394129, 946365, 377410, 368260, 209492, 588096, 107916, 532246, 
               97246, 118145, 361697, 3087192, 1940103, 163458, 2213827, 760984, 
               176827, 441000, 421347, 357582, 113911, 259391, 196073, 45742, 
               131656, 167399, 564938, 157178, 84718, 89544, 132847, 80164, 
               28128, 45583, 35146, 24201, 55031, 29252)
```
**Kegunaan**: Menyimpan data jumlah balita untuk ke-38 provinsi Indonesia dalam satu operasi.

### 4. **Iteration dalam rbind()**
```r
# Baris 38: Menggabungkan data frame
stunting_data_indonesia <- rbind(stunting_data_indonesia, total_row)
```
**Kegunaan**: Menambahkan baris total ke dataset utama dengan iterasi baris.


# Analisis Objek Program NutriTrack Line 613-dst

## A. Tipe Data

### 1. **Character (String)**
```r
input$name == ""
# Menyimpan nama anak sebagai teks

input$sex == "Male"
# Menyimpan jenis kelamin ("Male" atau "Female")

results$status <- "Normal"
# Menyimpan status gizi anak ("Normal", "Stunting", "Stunting Berat")

results$color <- "#28a745"
# Menyimpan kode warna hex untuk visualisasi status
```

### 2. **Numeric**
```r
z_score <- (height() - median_height) / sd_height
# Menyimpan nilai Z-Score hasil perhitungan status gizi

results$zscore <- round(z_score, 2)
# Menyimpan Z-Score yang dibulatkan 2 desimal

age_num <- as.numeric(gsub("[^0-9.]", "", age_str))
# Konversi teks input umur menjadi angka
```

### 3. **Integer**
```r
age_idx <- which(abs(who_data$age_months - age()) == min(abs(who_data$age_months - age())))
# Indeks untuk mencari umur terdekat di data WHO

closest_age_idx[1]
# Mengambil indeks pertama dari hasil pencarian
```

### 4. **Logical (Boolean)**
```r
input$sort_data
# TRUE/FALSE untuk mengurutkan data provinsi

is.null(input$age_input) || input$age_input == ""
# Mengecek apakah input kosong (TRUE/FALSE)
```

## B. Struktur Data

### 1. **Data Frame**
```r
who_data
# Data frame berisi standar pertumbuhan WHO dengan kolom:
# - age_months: umur dalam bulan
# - sex: jenis kelamin
# - median_tb: median tinggi badan
# - sd_tb: standar deviasi tinggi badan

stunting_data_indonesia
# Data frame prevalensi stunting per provinsi dengan kolom:
# - provinsi: nama provinsi
# - prevalensi: persentase stunting
# - jml_balita: jumlah balita
# - jml_stunting: jumlah kasus stunting
# - tahun: tahun data
```

### 2. **List**
```r
results <- reactiveValues(
  zscore = NULL,
  status = NULL,
  color = NULL,
  status_text = NULL
)
# List reaktif untuk menyimpan hasil analisis gizi anak

trend_data <- data.frame(
  tahun = c(2018, 2019, 2021, 2022),
  prevalensi = c(30.8, 27.7, 24.4, 21.6)
)
# Data frame untuk tren nasional stunting
```

### 3. **Vector**
```r
age_range <- seq(0, 60, by = 1)
# Vector numerik berisi rentang umur 0-60 bulan

color_scale <- ifelse(sorted_data$prevalensi >= 30, 'red',
                      ifelse(sorted_data$prevalensi >= 25, 'orange', 'yellow'))
# Vector karakter berisi kode warna berdasarkan prevalensi
```

## C. Variable

### 1. **Variable Input**
```r
age <- reactive({...})
# Variable reaktif menyimpan umur anak dari input pengguna

height <- reactive({...})
# Variable reaktif menyimpan tinggi badan anak

input$sex
# Variable menyimpan jenis kelamin yang dipilih pengguna
```

### 2. **Variable Perhitungan**
```r
median_height <- who_data$median_tb[closest_age_idx]
# Variable menyimpan median tinggi badan standar WHO

sd_height <- who_data$sd_tb[closest_age_idx]
# Variable menyimpan standar deviasi tinggi badan WHO

z_score <- (height() - median_height) / sd_height
# Variable menyimpan hasil perhitungan Z-Score
```

### 3. **Variable Output**
```r
results$status
# Variable menyimpan status gizi ("Normal", "Stunting", "Stunting Berat")

results$status_text
# Variable menyimpan penjelasan status gizi untuk ditampilkan
```

## D. Operasi Aritmatika

### 1. **Perhitungan Z-Score (Rumus Utama)**
```r
z_score <- (height() - median_height) / sd_height
# Operasi: pengurangan, pembagian untuk menghitung status gizi
```

### 2. **Pembulatan**
```r
results$zscore <- round(z_score, 2)
# Membulatkan Z-Score ke 2 desimal untuk tampilan
```

### 3. **Pencarian Nilai Terdekat**
```r
abs(who_data$age_months - age())
# Operasi pengurangan dan nilai absolut untuk mencari umur terdekat di data WHO
```

### 4. **Sequence Generation**
```r
age_range <- seq(0, 60, by = 1)
# Membuat rentang angka 0-60 dengan interval 1 untuk grafik
```

## E. Operasi Logika

### 1. **Pengecekan Input Kosong**
```r
is.null(input$age_input) || input$age_input == ""
# OR operator untuk mengecek input kosong atau NULL
```

### 2. **Perbandingan untuk Status Gizi**
```r
if(z_score >= -2) {
  results$status <- "Normal"
} else if(z_score >= -3 && z_score < -2) {
  results$status <- "Stunting"  
} else {
  results$status <- "Stunting Berat"
}
# Operasi >= (lebih besar sama dengan) dan && (AND) untuk menentukan kategori stunting
```

### 3. **Filtering Data**
```r
who_filtered <- who_data[who_data$sex == input$sex, ]
# Operator == untuk memfilter data berdasarkan jenis kelamin
```

## F. Percabangan

### 1. **If-Else untuk Status Gizi**
```r
if(z_score >= -2) {
  results$status <- "Normal"
  results$color <- "#28a745"  # hijau
  results$status_text <- "Tinggi badan anak sesuai dengan standar WHO untuk usia ini."
} else if(z_score >= -3 && z_score < -2) {
  results$status <- "Stunting"
  results$color <- "#ffc107"  # kuning
  results$status_text <- "Tinggi badan anak sedikit di bawah standar WHO untuk usia ini."
} else {
  results$status <- "Stunting Berat"
  results$color <- "#dc3545"  # merah
  results$status_text <- "Tinggi badan anak signifikan di bawah standar WHO untuk usia ini."
}
# Percabangan untuk menentukan status gizi berdasarkan Z-Score WHO
```

### 2. **Conditional Display**
```r
if(input$name == "") {
  return("Status Gizi Anak")
} else {
  return(paste("Status Gizi:", input$name))
}
# Percabangan untuk menampilkan nama anak atau teks default
```

### 3. **ifelse untuk Pewarnaan Chart**
```r
color_scale <- ifelse(sorted_data$prevalensi >= 30, 'red',
                      ifelse(sorted_data$prevalensi >= 25, 'orange', 'yellow'))
# Nested ifelse untuk menentukan warna berdasarkan tingkat prevalensi stunting
```

## G. Pengulangan

### 1. **lapply untuk UI Generation**
```r
top_provinces_ui <- lapply(1:5, function(i) {
  province <- top_5$provinsi[i]
  value <- value_column[i]
  prevalensi <- top_5$prevalensi[i]
  
  # Generate UI element untuk setiap provinsi
  div(
    class = "ranking-item",
    div(class = "ranking-number", span(i)),
    div(class = "ranking-content", 
        h4(province),
        div(class = "ranking-details",
            span(value_format(value), class = "ranking-value"),
            tags$span(class = paste0("label label-", badge_color), 
                      paste0(prevalensi, "%"))
        )
    )
  )
})
# Loop untuk membuat 5 elemen UI peringkat provinsi dengan prevalensi tertinggi
```

### 2. **which() untuk Pencarian Index**
```r
age_idx <- which(abs(who_data$age_months - age()) == min(abs(who_data$age_months - age())))
# Loop internal dalam which() untuk mencari semua indeks yang memenuhi kondisi
```

### 3. **Iterasi dalam Filtering**
```r
closest_age_idx <- intersect(age_idx, sex_idx)
# Operasi set yang melakukan iterasi untuk mencari irisan dua vector
```
