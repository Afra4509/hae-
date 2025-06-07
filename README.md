# Identifikasi Lengkap Komponen Programming dalam Aplikasi NutriTrack

## A. Tipe Data

### 1. **Numeric (Bilangan Desimal)**
```r
# Data median tinggi badan WHO
median_tb = c(49.9, 58.4, 65.7, 70.6, 75.7, 78.4, 80.7, 87.8, 94.9, 102.9, 110.0,
              49.1, 57.3, 64.3, 69.8, 74.0, 76.6, 79.2, 86.4, 93.9, 101.6, 108.4)
```
**Kegunaan**: Menyimpan nilai median tinggi badan dalam cm sesuai standar WHO untuk perhitungan Z-score.

```r
# Data standar deviasi
sd_tb = rep(c(1.8, 2.4, 2.7, 2.9, 3.3, 3.2, 3.3, 3.4, 3.8, 4.3, 4.9), 2)
```
**Kegunaan**: Menyimpan nilai standar deviasi untuk menghitung sebaran normal dalam analisis stunting.

```r
# Data prevalensi stunting per provinsi
prevalensi = c(6.2, 3.0, 8.1, 2.5, 2.7, 1.4, 3.9, 2.8, 3.3, 3.1, 1.6, 4.9, 8.6, 7.7, 
               5.8, 2.9, 3.5, 12.7, 14.8, 8.7, 11.1, 8.2, 9.0, 6.7, 1.7, 10.4, 7.3, 
               10.3, 5.4, 23.9, 5.4, 8.7, 9.3, 9.9, 4.4, 12.7, 10.1, 7.8)
```
**Kegunaan**: Menyimpan persentase prevalensi stunting di setiap provinsi untuk analisis geografis.

```r
# Perhitungan Z-Score dalam server logic
z_score <- (height() - median_height) / sd_height
results$zscore <- round(z_score, 2)
```
**Kegunaan**: Menghitung dan menyimpan nilai Z-Score hasil perhitungan status gizi anak dengan pembulatan 2 desimal.

### 2. **Integer (Bilangan Bulat)**
```r
# Usia dalam bulan
age_months = rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2)
```
**Kegunaan**: Menyimpan rentang usia balita dalam bulan untuk standar pertumbuhan WHO.

```r
# Jumlah balita per provinsi
jml_balita = c(394129, 946365, 377410, 368260, 209492, 588096, 107916, 532246, ...)
```
**Kegunaan**: Menyimpan jumlah populasi balita di setiap provinsi untuk analisis demografis.

```r
# Data total nasional
jml_balita = 15904224,
jml_stunting = 728559 + 238660,
pendek = 728559,
sangat_pendek = 238660
```
**Kegunaan**: Menyimpan agregasi data stunting nasional untuk statistik keseluruhan.

```r
# Index pencarian dalam server logic
age_idx <- which(abs(who_data$age_months - age()) == min(abs(who_data$age_months - age())))
closest_age_idx[1]
```
**Kegunaan**: Menyimpan indeks untuk mencari umur terdekat di data WHO dan mengambil indeks pertama.

### 3. **Character (Teks/String)**
```r
# Kategori jenis kelamin
sex = rep(c("Male", "Female"), each = 11)
```
**Kegunaan**: Menyimpan kategori gender untuk diferensiasi standar pertumbuhan.

```r
# Nama provinsi
provinsi = c("ACEH", "SUMATERA UTARA", "SUMATERA BARAT", "RIAU", "JAMBI", ...)
```
**Kegunaan**: Menyimpan identifier wilayah geografis Indonesia untuk mapping data stunting.

```r
# Konfigurasi tema dashboard
skin = "blue"
title = span(icon("child-reaching"), "NutriTrack | Deteksi Dini Stunting")
```
**Kegunaan**: Mengatur tampilan visual dan branding aplikasi.

```r
# Status gizi dalam server logic
results$status <- "Normal"
results$color <- "#28a745"
```
**Kegunaan**: Menyimpan status gizi anak dan kode warna hex untuk visualisasi status.

### 4. **Logical (Boolean)**
```r
# Kontrol pengurutan data
checkboxInput("sort_data", "Urutkan dari Tertinggi", value = TRUE)
```
**Kegunaan**: Menyimpan status TRUE/FALSE untuk mengontrol pengurutan data pada visualisasi.

```r
# Status header solid
solidHeader = TRUE
```
**Kegunaan**: Mengatur style header box dalam dashboard (solid atau transparan).

```r
# Pengecekan input kosong dalam server logic
is.null(input$age_input) || input$age_input == ""
```
**Kegunaan**: Mengecek apakah input kosong (TRUE/FALSE) untuk validasi form.

## B. Struktur Data

### 1. **Data Frame**
```r
# Dataset standar WHO
who_data <- data.frame(
  age_months = rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2),
  sex = rep(c("Male", "Female"), each = 11),
  median_tb = c(...),
  sd_tb = rep(c(...), 2)
)
```
**Kegunaan**: Menyimpan referensi standar pertumbuhan WHO dalam format tabular terstruktur untuk lookup Z-score.

```r
# Dataset stunting Indonesia
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
# Data total nasional
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

```r
# Data tren nasional dalam server logic
trend_data <- data.frame(
  tahun = c(2018, 2019, 2021, 2022),
  prevalensi = c(30.8, 27.7, 24.4, 21.6)
)
```
**Kegunaan**: Menyimpan data tren prevalensi stunting nasional untuk visualisasi grafik.

### 2. **Vector**
```r
# Vector integer untuk usia
c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60)
```
**Kegunaan**: Menyimpan sekuens usia dalam bulan untuk referensi kurva pertumbuhan.

```r
# Vector karakter untuk gender
c("Male", "Female")
```
**Kegunaan**: Menyimpan dua kategori jenis kelamin untuk klasifikasi standar WHO.

```r
# Vector numeric untuk median tinggi badan
c(49.9, 58.4, 65.7, 70.6, 75.7, 78.4, 80.7, 87.8, 94.9, 102.9, 110.0,
  49.1, 57.3, 64.3, 69.8, 74.0, 76.6, 79.2, 86.4, 93.9, 101.6, 108.4)
```
**Kegunaan**: Menyimpan nilai referensi tinggi badan normal untuk setiap usia dan gender.

```r
# Vector untuk visualisasi dalam server logic
age_range <- seq(0, 60, by = 1)
color_scale <- ifelse(sorted_data$prevalensi >= 30, 'red',
                      ifelse(sorted_data$prevalensi >= 25, 'orange', 'yellow'))
```
**Kegunaan**: Membuat rentang umur untuk grafik dan menentukan warna berdasarkan prevalensi stunting.

### 3. **List (dalam struktur UI)**
```r
# Menu navigasi
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
# Pilihan radio button
choices = c("Laki-laki" = "Male", "Perempuan" = "Female")
```
**Kegunaan**: Menyimpan pasangan label-value untuk input jenis kelamin.

```r
# Pilihan dropdown chart
choices = c("Persentase Stunting" = "percentage", 
            "Jumlah Kasus Stunting" = "cases",
            "Jumlah Balita" = "toddlers")
```
**Kegunaan**: Menyimpan opsi visualisasi data dengan key-value mapping.

```r
# List reaktif dalam server logic
results <- reactiveValues(
  zscore = NULL,
  status = NULL,
  color = NULL,
  status_text = NULL
)
```
**Kegunaan**: List reaktif untuk menyimpan hasil analisis gizi anak yang dapat diupdate secara dinamis.

### 4. **Named List (lapply structure)**
```r
# List untuk generate cards nutrisi
lapply(list(
  list("Protein", "egg", "Telur, ikan, ayam, daging, tempe, tahu, kacang-kacangan"),
  list("Kalsium", "bone", "Susu, keju, yogurt, ikan teri, sayuran hijau"),
  list("Zat Besi", "leaf", "Daging merah, bayam, kacang-kacangan, sayuran hijau"),
  list("Cairan", "glass-water", "Minimal 8-10 gelas air putih per hari")
), function(x) { ... })
```
**Kegunaan**: Menyimpan data terstruktur untuk generate multiple UI components dengan pola yang sama.

## C. Variable

### 1. **Input Variables (User Interface)**
```r
# Variable nama anak
textInput("name", "Nama Anak", placeholder = "Masukkan nama anak")
```
**Kegunaan**: Variable `name` menyimpan input nama anak dari user untuk personalisasi hasil analisis.

```r
# Variable usia anak
textInput("age_input", "Usia (bulan)", placeholder = "Contoh: 12 atau usia anak 12")
```
**Kegunaan**: Variable `age_input` menyimpan usia anak dalam bulan untuk perhitungan Z-score.

```r
# Variable jenis kelamin
awesomeRadio("sex", "Jenis Kelamin", choices = c("Laki-laki" = "Male", "Perempuan" = "Female"))
```
**Kegunaan**: Variable `sex` menyimpan pilihan gender untuk menentukan standar WHO yang sesuai.

```r
# Variable tinggi badan
textInput("height_input", "Tinggi Badan (cm)", placeholder = "Contoh: 60 atau tb anak 60")
```
**Kegunaan**: Variable `height_input` menyimpan tinggi badan anak untuk analisis status gizi.

### 2. **Control Variables**
```r
# Variable ID menu
id = "tabs"
```
**Kegunaan**: Variable `tabs` mengontrol navigasi antar halaman dalam dashboard.

```r
# Variable tombol aksi
actionBttn("calculate", "Analisis Status Gizi", ...)
```
**Kegunaan**: Variable `calculate` trigger untuk memulai perhitungan status gizi anak.

```r
# Variable tipe chart
selectInput("chart_type", "Tampilkan Berdasarkan:", ...)
```
**Kegunaan**: Variable `chart_type` mengontrol jenis visualisasi data yang ditampilkan.

```r
# Variable sorting
checkboxInput("sort_data", "Urutkan dari Tertinggi", value = TRUE)
```
**Kegunaan**: Variable `sort_data` mengontrol pengurutan data dari tinggi ke rendah atau sebaliknya.

### 3. **Configuration Variables**
```r
# Variable tema aplikasi
skin = "blue"
```
**Kegunaan**: Variable `skin` menentukan color scheme dashboard (blue theme).

```r
# Variable lebar title
titleWidth = 350
```
**Kegunaan**: Variable `titleWidth` mengatur lebar area judul dashboard dalam pixel.

```r
# Variable lebar sidebar
width = 300
```
**Kegunaan**: Variable `width` menentukan lebar panel sidebar navigasi.

### 4. **Reactive Variables (Server Logic)**
```r
# Variable reaktif untuk input processing
age <- reactive({...})
height <- reactive({...})
```
**Kegunaan**: Variable reaktif menyimpan dan memproses input umur dan tinggi badan anak.

```r
# Variable perhitungan
median_height <- who_data$median_tb[closest_age_idx]
sd_height <- who_data$sd_tb[closest_age_idx]
z_score <- (height() - median_height) / sd_height
```
**Kegunaan**: Variable menyimpan nilai median, standar deviasi, dan hasil perhitungan Z-Score.

### 5. **Output Variables**
```r
# Variable output nama anak
textOutput("child_name")
```
**Kegunaan**: Variable `child_name` menampilkan nama anak yang diinput user di hasil analisis.

```r
# Variable tabel hasil
tableOutput("results_table")
```
**Kegunaan**: Variable `results_table` menampilkan tabel hasil perhitungan status gizi.

```r
# Variable plot pertumbuhan
plotlyOutput("growth_plot")
```
**Kegunaan**: Variable `growth_plot` menampilkan kurva pertumbuhan interaktif.

```r
# Variable status dalam server logic
results$status
results$status_text
```
**Kegunaan**: Variable menyimpan status gizi dan penjelasan status untuk ditampilkan ke user.

## D. Operasi Aritmatika

### 1. **Penjumlahan (+)**
```r
# Total kasus stunting
jml_stunting = 728559 + 238660
```
**Kegunaan**: Menghitung total kasus stunting nasional dengan menjumlahkan kategori pendek dan sangat pendek.

### 2. **Pengurangan (-) dan Pembagian (/) - Rumus Z-Score**
```r
# Perhitungan Z-Score (Rumus Utama)
z_score <- (height() - median_height) / sd_height
```
**Kegunaan**: Operasi pengurangan dan pembagian untuk menghitung status gizi berdasarkan standar WHO.

```r
# Pencarian nilai terdekat
abs(who_data$age_months - age())
```
**Kegunaan**: Operasi pengurangan dan nilai absolut untuk mencari umur terdekat di data WHO.

### 3. **Pembulatan**
```r
# Pembulatan hasil Z-Score
results$zscore <- round(z_score, 2)
```
**Kegunaan**: Membulatkan Z-Score ke 2 desimal untuk tampilan yang lebih user-friendly.

### 4. **Sequence Generation**
```r
# Rentang angka untuk visualisasi
age_range <- seq(0, 60, by = 1)
```
**Kegunaan**: Membuat rentang angka 0-60 dengan interval 1 untuk grafik pertumbuhan.

### 5. **Pengulangan/Repetisi (rep)**
```r
# Mengulang usia untuk 2 gender
rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2)
```
**Kegunaan**: Mengulangi sequence usia 2 kali (untuk laki-laki dan perempuan) dalam dataset WHO.

```r
# Mengulang standar deviasi
rep(c(1.8, 2.4, 2.7, 2.9, 3.3, 3.2, 3.3, 3.4, 3.8, 4.3, 4.9), 2)
```
**Kegunaan**: Mengulangi nilai SD untuk kedua jenis kelamin dalam perhitungan Z-score.

```r
# Mengulang tahun
rep(2023, 38)
```
**Kegunaan**: Memberikan label tahun 2023 untuk semua 38 provinsi dalam dataset.

### 6. **Operasi dalam Fungsi c() - Concatenation**
```r
# Menggabungkan data median untuk laki-laki dan perempuan
c(49.9, 58.4, ..., 110.0,    # Data laki-laki
  49.1, 57.3, ..., 108.4)    # Data perempuan
```
**Kegunaan**: Menggabungkan dua set data median tinggi badan menjadi satu vector.

## E. Operasi Logika

### 1. **Conditional Rendering (==)**
```r
# Kondisi tampil panel
conditionalPanel(
  condition = "input.tabs == 'calculator'",
  # Panel hanya muncul jika tab calculator aktif
)
```
**Kegunaan**: Menampilkan form input hanya ketika user berada di tab "Kalkulator Stunting".

### 2. **Perbandingan untuk Klasifikasi Stunting**
```r
# Perbandingan untuk Status Gizi
if(z_score >= -2) {
  results$status <- "Normal"
} else if(z_score >= -3 && z_score < -2) {
  results$status <- "Stunting"  
} else {
  results$status <- "Stunting Berat"
}
```
**Kegunaan**: Mengklasifikasikan status gizi anak berdasarkan threshold Z-score WHO dengan operator >= dan &&.

### 3. **Boolean Logic dalam UI Controls**
```r
# Status header box
solidHeader = TRUE
```
**Kegunaan**: Mengatur style box dengan header solid (TRUE) atau transparan (FALSE).

```r
# Default selection
selected = "Male"
value = TRUE
```
**Kegunaan**: Menetapkan pilihan default jenis kelamin laki-laki dan mengatur checkbox aktif secara default.

### 4. **Pengecekan Input Kosong**
```r
# OR operator untuk validasi input
is.null(input$age_input) || input$age_input == ""
```
**Kegunaan**: Mengecek apakah input kosong atau NULL dengan operator OR (||).

### 5. **Filtering Data**
```r
# Operator == untuk memfilter data
who_filtered <- who_data[who_data$sex == input$sex, ]
```
**Kegunaan**: Memfilter data WHO berdasarkan jenis kelamin yang dipilih user.

### 6. **ifelse untuk Pewarnaan Chart**
```r
# Nested ifelse untuk conditional coloring
color_scale <- ifelse(sorted_data$prevalensi >= 30, 'red',
                      ifelse(sorted_data$prevalensi >= 25, 'orange', 'yellow'))
```
**Kegunaan**: Menentukan warna chart berdasarkan tingkat prevalensi stunting dengan logika bersarang.

## F. Percabangan (Branching)

### 1. **Conditional Panel - Tab Switching**
```r
# Percabangan berdasarkan tab aktif
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
# Percabangan konten berdasarkan tab
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

### 3. **If-Else untuk Status Gizi**
```r
# Percabangan untuk menentukan status gizi
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
```
**Kegunaan**: Menentukan status gizi, warna indikator, dan teks penjelasan berdasarkan nilai Z-Score WHO.

### 4. **Conditional Content dalam Tab**
```r
# Percabangan dalam tab box
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

### 5. **Conditional Display**
```r
# Percabangan untuk menampilkan nama anak
if(input$name == "") {
  return("Status Gizi Anak")
} else {
  return(paste("Status Gizi:", input$name))
}
```
**Kegunaan**: Menampilkan nama anak jika diisi, atau teks default jika kosong.

### 6. **Dropdown Selection - Value-based Branching**
```r
# Percabangan visualisasi
selectInput("chart_type", "Tampilkan Berdasarkan:",
  choices = c("Persentase Stunting" = "percentage", 
              "Jumlah Kasus Stunting" = "cases",
              "Jumlah Balita" = "toddlers"),
  selected = "percentage")
```
**Kegunaan**: User dapat memilih jenis data yang ingin divisualisasikan dalam chart.

# G. Pengulangan (Loops/Iteration) - Identifikasi Lengkap

## 1. **rep() - Numeric Repetition**

### Mengulang Sequence Usia
```r
# Mengulang sequence usia untuk 2 gender
rep(c(0, 3, 6, 9, 12, 15, 18, 24, 36, 48, 60), 2)
```
**Kegunaan**: Mengulangi pola usia dalam bulan sebanyak 2 kali untuk membuat dataset yang mencakup laki-laki dan perempuan dalam standar WHO.

### Mengulang Elemen dengan Pattern
```r
# Mengulang setiap elemen berurutan
rep(c("Male", "Female"), each = 11)
```
**Kegunaan**: Mengulang "Male" sebanyak 11 kali, kemudian "Female" sebanyak 11 kali untuk mapping gender dengan rentang usia yang sesuai.

```r
# Mengulang standar deviasi untuk kedua gender
rep(c(1.8, 2.4, 2.7, 2.9, 3.3, 3.2, 3.3, 3.4, 3.8, 4.3, 4.9), 2)
```
**Kegunaan**: Mengulangi nilai standar deviasi tinggi badan untuk laki-laki dan perempuan dalam perhitungan Z-score WHO.

### Mengulang Nilai Konstan
```r
# Mengulang tahun untuk semua provinsi
tahun = rep(2023, 38)
```
**Kegunaan**: Memberikan label tahun 2023 untuk semua 38 provinsi Indonesia dalam dataset stunting.

## 2. **lapply() - List Iteration untuk UI Generation**

### Iterasi untuk Cards Nutrisi Dasar
```r
# Membuat cards informasi nutrisi secara otomatis
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
**Kegunaan**: Membuat 4 card informasi nutrisi secara otomatis dengan struktur HTML yang sama namun konten berbeda untuk setiap nutrisi penting.

### Iterasi untuk Menu MPASI 6-12 Bulan
```r
# Generate cards menu MPASI
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
**Kegunaan**: Generate 4 card contoh menu MPASI dengan template yang konsisten untuk memberikan variasi makanan balita usia 6-12 bulan.

### Iterasi untuk Menu Balita 1-3 Tahun
```r
# Membuat cards menu untuk balita 1-3 tahun
lapply(list(
  list("Nasi tim ayam", "bowl-rice", "Nasi + ayam + sayuran + kaldu"),
  list("Sup ikan", "fish", "Ikan + wortel + kentang + buncis + kaldu"),
  list("Bubur kacang merah", "seedling", "Kacang merah + santan + gula aren"),
  list("Finger foods", "cookie", "Buah potong, roti, biskuit untuk melatih motorik")
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
**Kegunaan**: Membuat variasi menu untuk balita usia 1-3 tahun dengan mempertimbangkan perkembangan kemampuan makan dan kebutuhan gizi.

### Iterasi untuk Menu Balita 3-5 Tahun
```r
# Generate cards untuk anak pra-sekolah
lapply(list(
  list("Nasi lengkap", "plate-wheat", "Nasi + lauk + sayur + buah"),
  list("Bekal sekolah", "lunch-box", "Sandwich + buah + susu + camilan sehat"),
  list("Makan keluarga", "users", "Menu yang sama dengan keluarga, porsi disesuaikan"),
  list("Camilan sehat", "apple-whole", "Buah segar, yogurt, kacang-kacangan")
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
**Kegunaan**: Membuat rekomendasi makanan untuk anak pra-sekolah yang sudah bisa makan seperti orang dewasa dengan porsi yang disesuaikan.

### Loop untuk UI Ranking Provinsi
```r
# Loop dinamis untuk ranking provinsi
top_provinces_ui <- lapply(1:5, function(i) {
  province <- top_5$provinsi[i]
  value <- value_column[i]
  prevalensi <- top_5$prevalensi[i]
  
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
```
**Kegunaan**: Loop untuk membuat 5 elemen UI peringkat provinsi dengan prevalensi stunting tertinggi secara dinamis, termasuk nomor urut, nama provinsi, nilai, dan badge persentase.

## 3. **which() dan Operasi Pencarian Index**

### Loop Internal dalam which()
```r
# Pencarian index dengan iterasi internal
age_idx <- which(abs(who_data$age_months - age()) == min(abs(who_data$age_months - age())))
```
**Kegunaan**: Loop internal dalam fungsi which() untuk mencari semua indeks yang memenuhi kondisi pencarian umur terdekat dalam dataset WHO.

### Loop untuk Filtering Data
```r
# Filter data berdasarkan jenis kelamin
who_filtered <- who_data[who_data$sex == input$sex, ]
```
**Kegunaan**: Iterasi implicit untuk memfilter baris data WHO yang sesuai dengan jenis kelamin yang dipilih user.

### Intersection dengan Loop
```r
# Operasi set dengan iterasi
closest_age_idx <- intersect(age_idx, sex_idx)
if(length(closest_age_idx) > 0) {
  closest_age_idx[1]
} else {
  age_idx[1]
}
```
**Kegunaan**: Mencari intersection antara index usia dan jenis kelamin, kemudian mengambil index pertama jika ditemukan kecocokan.

## 4. **Implicit Loops dalam Vector Operations**

### Vector Creation dengan Multiple Elements
```r
# Membuat vector dengan 38 elemen (semua provinsi Indonesia)
jml_balita = c(394129, 946365, 377410, 368260, 209492, 588096, 107916, 532246, 
               97246, 118145, 361697, 3087192, 1940103, 163458, 2213827, 760984, 
               176827, 441000, 421347, 357582, 113911, 259391, 196073, 45742, 
               131656, 167399, 564938, 157178, 84718, 89544, 132847, 80164, 
               28128, 45583, 35146, 24201, 55031, 29252)
```
**Kegunaan**: Menyimpan data jumlah balita untuk ke-38 provinsi Indonesia dalam satu operasi vector dengan iterasi implicit.

### Vector Operations dengan Perhitungan
```r
# Operasi vector untuk semua provinsi
prevalensi = c(6.2, 3.0, 8.1, 2.5, 2.7, 1.4, 3.9, 2.8, 3.3, 3.1, 1.6, 4.9, 8.6, 7.7, 
               5.8, 2.9, 3.5, 12.7, 14.8, 8.7, 11.1, 8.2, 9.0, 6.7, 1.7, 10.4, 7.3, 
               10.3, 5.4, 23.9, 5.4, 8.7, 9.3, 9.9, 4.4, 12.7, 10.1, 7.8)
```
**Kegunaan**: Menyimpan persentase prevalensi stunting untuk semua provinsi dengan operasi vector yang melakukan iterasi pada setiap elemen.

## 5. **seq() - Sequence Generation dengan Loop**

### Membuat Rentang untuk Visualisasi
```r
# Sequence untuk grafik pertumbuhan
age_range <- seq(0, 60, by = 1)
```
**Kegunaan**: Membuat sequence angka dari 0 hingga 60 dengan interval 1 untuk sumbu X pada grafik kurva pertumbuhan WHO.

### Sequence untuk Data Processing
```r
# Rentang index untuk lapply
lapply(1:5, function(i) { ... })
```
**Kegunaan**: Membuat sequence 1 sampai 5 untuk iterasi dalam lapply, menghasilkan 5 elemen ranking teratas.

## 6. **rbind() - Row-wise Iteration**

### Menggabungkan Data dengan Iterasi Baris
```r
# Menambahkan total nasional ke dataset
stunting_data_indonesia <- rbind(stunting_data_indonesia, total_row)
```
**Kegunaan**: Menggabungkan data frame provinsi dengan baris total nasional menggunakan iterasi baris untuk membuat dataset lengkap.

### Data Frame Binding dengan Multiple Rows
```r
# Membuat data frame dengan rbind multiple
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
**Kegunaan**: Membuat baris agregat yang akan digabungkan dengan dataset utama melalui operasi rbind.

## 7. **Conditional Loops dalam Server Logic**

### Loop dengan Reactive Context
```r
# Reactive expression dengan loop internal
observe({
  # Loop untuk update UI berdasarkan input
  if(!is.null(input$chart_type)) {
    # Iterasi untuk update chart berdasarkan pilihan
    switch(input$chart_type,
           "percentage" = { ... },
           "cases" = { ... },
           "toddlers" = { ... })
  }
})
```
**Kegunaan**: Melakukan iterasi reaktif untuk mengupdate visualisasi chart berdasarkan pilihan user dengan switching yang berulang.

### Loop dalam Data Sorting
```r
# Sorting dengan iterasi internal
sorted_data <- stunting_data_indonesia[order(stunting_data_indonesia$prevalensi, 
                                           decreasing = input$sort_data), ]
```
**Kegunaan**: Operasi sorting yang melakukan iterasi internal untuk mengurutkan data berdasarkan prevalensi stunting.

## 8. **Nested Loops dalam ifelse()**

### Multiple Conditional dengan Loop
```r
# Nested ifelse untuk pewarnaan chart
color_scale <- ifelse(sorted_data$prevalensi >= 30, 'red',
                      ifelse(sorted_data$prevalensi >= 25, 'orange', 
                             ifelse(sorted_data$prevalensi >= 20, 'yellow', 'green')))
```
**Kegunaan**: Melakukan iterasi pada setiap elemen vector prevalensi untuk menentukan warna berdasarkan threshold yang berbeda dengan nested conditions.

### Loop untuk Status Classification
```r
# Iterasi untuk klasifikasi status gizi
status_classification <- sapply(z_scores, function(z) {
  if(z >= -2) return("Normal")
  else if(z >= -3) return("Stunting")
  else return("Stunting Berat")
})
```
**Kegunaan**: Melakukan iterasi pada vector Z-scores untuk mengklasifikasikan status gizi setiap anak dengan sapply loop.
