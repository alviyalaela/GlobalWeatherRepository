# ⛅ Global Weather Analysis 
![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Weather%20Cover.webp?raw=True)
# Project Overview

Proyek ini bertujuan untuk menganalisis data cuaca global dan memahami bagaimana berbagai faktor meteorologis seperti suhu, kelembapan, curah hujan, kecepatan angin, dan tekanan udara saling memengaruhi kondisi iklim di berbagai negara.
Analisis dilakukan dengan menggunakan teknik Exploratory Data Analysis (EDA) dan visualisasi data untuk menemukan pola dan tren yang signifikan dalam data cuaca.

## Tujuan Analisa
1. Memahami distribusi data cuaca (suhu, kelembapan, curah hujan, tekanan, dan kecepatan angin).
2. Mengidentifikasi tren perubahan suhu dan curah hujan berdasarkan waktu dan wilayah.
3. Menemukan hubungan antar variabel cuaca (misalnya, hubungan antara suhu dan kelembapan).
4. Membuat visualisasi interaktif untuk membantu memahami pola cuaca secara lebih mendalam.


# Library dan Dependency
- pandas
- matplotlib
- numpy 
- seaborn 
- sklearn

  
# Dataset Overview
Dataset yang digunakan dalam project ini berasal dari [Kaggle - Weather Data Insights](https://www.kaggle.com/code/nithinreddy90/weather-data-insights). Dataset ini menyediakan informasi cuaca harian dari berbagai ibu kota di seluruh dunia.
Berbeda dengan data prakiraan (forecast), dataset ini berisi data aktual yang mencerminkan kondisi cuaca nyata di berbagai wilayah global.

Data dikumpulkan sejak 29 Agustus 2023 dan memiliki lebih dari 40 fitur cuaca yang mencakup:

| #  | Column                       | Non-Null Count | Dtype   |
| -- | ---------------------------- | -------------- | ------- |
| 0  | country                      | 97435 non-null | object  |
| 1  | location_name                | 97435 non-null | object  |
| 2  | latitude                     | 97435 non-null | float64 |
| 3  | longitude                    | 97435 non-null | float64 |
| 4  | timezone                     | 97435 non-null | object  |
| 5  | last_updated_epoch           | 97435 non-null | int64   |
| 6  | last_updated                 | 97435 non-null | object  |
| 7  | temperature_celsius          | 97435 non-null | float64 |
| 8  | temperature_fahrenheit       | 97435 non-null | float64 |
| 9  | condition_text               | 97435 non-null | object  |
| 10 | wind_mph                     | 97435 non-null | float64 |
| 11 | wind_kph                     | 97435 non-null | float64 |
| 12 | wind_degree                  | 97435 non-null | int64   |
| 13 | wind_direction               | 97435 non-null | object  |
| 14 | pressure_mb                  | 97435 non-null | float64 |
| 15 | pressure_in                  | 97435 non-null | float64 |
| 16 | precip_mm                    | 97435 non-null | float64 |
| 17 | precip_in                    | 97435 non-null | float64 |
| 18 | humidity                     | 97435 non-null | int64   |
| 19 | cloud                        | 97435 non-null | int64   |
| 20 | feels_like_celsius           | 97435 non-null | float64 |
| 21 | feels_like_fahrenheit        | 97435 non-null | float64 |
| 22 | visibility_km                | 97435 non-null | float64 |
| 23 | visibility_miles             | 97435 non-null | float64 |
| 24 | uv_index                     | 97435 non-null | float64 |
| 25 | gust_mph                     | 97435 non-null | float64 |
| 26 | gust_kph                     | 97435 non-null | float64 |
| 27 | air_quality_Carbon_Monoxide  | 97435 non-null | float64 |
| 28 | air_quality_Ozone            | 97435 non-null | float64 |
| 29 | air_quality_Nitrogen_dioxide | 97435 non-null | float64 |
| 30 | air_quality_Sulphur_dioxide  | 97435 non-null | float64 |
| 31 | air_quality_PM2.5            | 97435 non-null | float64 |
| 32 | air_quality_PM10             | 97435 non-null | float64 |
| 33 | air_quality_us-epa-index     | 97435 non-null | int64   |
| 34 | air_quality_gb-defra-index   | 97435 non-null | int64   |
| 35 | sunrise                      | 97435 non-null | object  |
| 36 | sunset                       | 97435 non-null | object  |
| 37 | moonrise                     | 97435 non-null | object  |
| 38 | moonset                      | 97435 non-null | object  |
| 39 | moon_phase                   | 97435 non-null | object  |
| 40 | moon_illumination            | 97435 non-null | int64   |

dtypes: float64(23), int64(7), object(11)

memory usage: 30.5+ MB

## Data Preparation
Data mentah akan melalui proses cleaning dan data reformation sebelum dilakukan analisis lebih lanjut. Hasil pemeriksaan menunjukkan bahwa tidak terdapat missing value pada dataset, sehingga proses dapat dilanjutkan ke tahap reformasi data tanpa perlu imputasi atau penghapusan data.
| #  | Column                       | Missing Values |
| -- | ---------------------------- | -------------- |
| 0  | country                      | 0              |
| 1  | location_name                | 0              |
| 2  | latitude                     | 0              |
| 3  | longitude                    | 0              |
| 4  | timezone                     | 0              |
| 5  | last_updated_epoch           | 0              |
| 6  | last_updated                 | 0              |
| 7  | temperature_celsius          | 0              |
| 8  | temperature_fahrenheit       | 0              |
| 9  | condition_text               | 0              |
| 10 | wind_mph                     | 0              |
| 11 | wind_kph                     | 0              |
| 12 | wind_degree                  | 0              |
| 13 | wind_direction               | 0              |
| 14 | pressure_mb                  | 0              |
| 15 | pressure_in                  | 0              |
| 16 | precip_mm                    | 0              |
| 17 | precip_in                    | 0              |
| 18 | humidity                     | 0              |
| 19 | cloud                        | 0              |
| 20 | feels_like_celsius           | 0              |
| 21 | feels_like_fahrenheit        | 0              |
| 22 | visibility_km                | 0              |
| 23 | visibility_miles             | 0              |
| 24 | uv_index                     | 0              |
| 25 | gust_mph                     | 0              |
| 26 | gust_kph                     | 0              |
| 27 | air_quality_Carbon_Monoxide  | 0              |
| 28 | air_quality_Ozone            | 0              |
| 29 | air_quality_Nitrogen_dioxide | 0              |
| 30 | air_quality_Sulphur_dioxide  | 0              |
| 31 | air_quality_PM2.5            | 0              |
| 32 | air_quality_PM10             | 0              |
| 33 | air_quality_us-epa-index     | 0              |
| 34 | air_quality_gb-defra-index   | 0              |
| 35 | sunrise                      | 0              |
| 36 | sunset                       | 0              |
| 37 | moonrise                     | 0              |
| 38 | moonset                      | 0              |
| 39 | moon_phase                   | 0              |
| 40 | moon_illumination            | 0              |

dtype: int64

Tahap data reformation dilakukan untuk menambah informasi baru yang lebih berguna dalam analisis, seperti waktu, zona, dan lokasi geografis.
Beberapa kolom baru yang ditambahkan adalah sebagai berikut:

1. **month** – diekstraksi dari kolom last_updated menggunakan pd.to_datetime() untuk mendapatkan nilai bulan dari tanggal pencatatan.

```bash
   df['last_updated'] = pd.to_datetime(df['last_updated'], errors='coerce')
   df['month'] = df['last_updated'].dt.month
   ```

2. **hour** – diambil dari jam pada kolom last_updated, untuk membantu analisis tren cuaca berdasarkan waktu.

```bash
   df['hour'] = pd.to_datetime(df['last_updated'], errors='coerce').dt.hour
   ```
3. **region** – diekstraksi dari kolom timezone, dengan memisahkan bagian sebelum tanda / untuk mengelompokkan data berdasarkan wilayah global (seperti Europe, Asia, America, dll).
Nilai teks kemudian diformat agar lebih rapi menggunakan .str.replace() dan .str.title().
```bash
   df['region'] = df['timezone'].str.split('/').str[0].str.replace('_', ' ').str.title()
   ```

4. **country** – diambil dari bagian setelah tanda / pada kolom timezone, yang merepresentasikan negara atau kota spesifik tempat data cuaca diambil.
```bash
   df['country'] = df['timezone'].str.split('/').str[1]
   ```


# Explanatory Data Analysis

- **Analisis 1: Cuaca yang Paling Sering Muncul Per Region**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Most%20Frequent%20Weather%20per%20Region.png?raw=true)

Pola dominasi Sunny di Africa, Asia, dan Europe konsisten dengan wilayah subtropis/tropis yang cenderung berlangit cerah, sementara Partly cloudy lebih sering di America & Pacific yang mencerminkan pengaruh maritim dan dinamika awan yang lebih aktif. Clear muncul di Australia pada sebagian lokasi, namun total observasinya kecil sehingga generalisasi perlu hati-hati. Temuan ini menjadi konteks dasar untuk memahami perbedaan suhu rata-rata antar-region pada Analisis 2.

- **Analisis 2: Rata-rata Suhu Antar Region**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Average%20Temperature%20per%20Region.png?raw=true)

Terlihat jejak lintang/laut yang jelas: Indian, Africa, Asia, Pacific membentuk klaster hangat-tropis (≈25–27 °C), America transisi (~21 °C), Europe/Atlantic lebih sejuk (~16–17 °C), dan Australia paling rendah (~12 °C). Rentang antar-region besar (selisih ≈15 °C antara Indian dan Australia) menandakan kontras iklim yang kuat. Perbedaan mean ini beresonansi dengan perilaku ekstrem musiman yang akan terlihat pada Analisis 3.

- **Analisis 3: Wilayah dengan Suhu Ter-ekstrem**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Extreme%20Temperatures%20by%20Region.png?raw=True)

Di belahan utara (Asia, Europe, America), maksimum muncul pada Jun–Jul dan minimum pada Jan–Feb; Asia paling ekstrem, dari sekitar −25 °C (Feb, Ulaanbaatar) hingga ~49 °C (Jun, Kuwait), tipikal iklim kontinental. Di belahan selatan (Australia, sebagian Africa & Indian), puncak panas Jan–Feb dan titik terdingin Jun (mis. Sydney/Antananarivo). Wilayah maritim (Pacific/Atlantic) ber-amplitudo lebih kecil dan puncak sering tertunda (Pacific memuncak Sep). Rentang ekstrem ini berimplikasi langsung pada kenyamanan manusia yang tercermin di perbandingan feels-like vs suhu pada Analisis 4.

- **Analisis 4: Perbandingan Temperature Asli dengan Temperature 'Feels Like'**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Feels-like%20VS%20Actual%20Temperature.png?raw=true)

Pada suhu sangat rendah (≤0 °C), feels-like < suhu (wind-chill); pada 0–20 °C perbedaannya kecil; mulai ≳25 °C—terutama saat kelembapan tinggi—feels-like > suhu (heat index), dan deviasi kian besar di >35 °C (indikasi clipping di ~50 °C). Pola kenyamanan ini membantu menjelaskan segmentasi iklim/cuaca ketika negara dikelompokkan pada Analisis 5.

- **Analisis 5: Clustering Negara dengan Iklim/Cuaca yang Mirip**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Country%20Climate%20Clusters.png?raw=true)

Muncul empat tipe: tropis-lembap/monsoon (suhu tinggi stabil, RH & precip tinggi, UV kuat), panas-kering/subtropis-mediterania (suhu & UV tinggi, RH & precip rendah), maritim/oceanic (dipengaruhi laut, amplitudo kecil–sedang, angin relatif kuat, suhu moderat), dan temperate/continental campuran (suhu menengah, musim lebih kontras). Segmentasi ini selaras dengan pola UV musiman pada Analisis 6 dan risiko kesehatan pada Analisis 7.

```bash
Cluster 0:
Abidjan, Algiers, Almaty, Amsterdam, Andorra, Argentina, Asuncion, Belgrade, Berlin, Bogota

Cluster 1:
Bangkok, Belize, Bissau, Brunei, Colombo, Conakry, Dhaka, Dili, El_Salvador, Fiji

Cluster 2:
Accra, Addis_Ababa, Aden, Amman, Antananarivo, Ashgabat, Asmara, Athens, Baghdad, Bahrain

Cluster 3:
Antigua, Apia, Auckland, Baku, Banjul, Barbados, Cape_Verde, Copenhagen, Dakar, Dominica
```

- **Analisis 6: Rata-rata UV Index tiap Bulan by Region**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/Average%20UV%20by%20Region%20%C3%97%20Month.png?raw=true)

Heatmap UV menegaskan puncak Mei–Jul di belahan utara (Asia/Europe) dan Jan–Feb di belahan selatan (Australia/Indian). Indian cenderung tinggi hampir sepanjang tahun (puncak Feb dan kembali naik Okt), Africa tinggi stabil dengan sedikit pelemahan tengah tahun, sedangkan America/Atlantic rendah–menengah dengan tonjolan kecil Mei–Juni. Australia/Pacific paling rendah dan relatif datar. Kekuatan UV ini langsung berkorelasi dengan tingkat risiko kesehatan menurut kategori WHO pada Analisis 7.

- **Analisis 7: Risiko Kesehatan (Kategori WHO) + Stacked Bar per Region**

![image](https://github.com/alviyalaela/GlobalWeatherRepository/blob/main/Asset/UV%20Risk%20Categories%20(WHO)%20per%20Region.png?raw=true)

Sesuai kategori WHO—Low (0–2), Moderate (3–5), High (6–7), Very High (8–10), Extreme (≥11)—Indian dan Africa memiliki porsi Very High–Extreme tertinggi (prioritas proteksi maksimal), Asia/Europe didominasi Moderate–High dengan puncak musiman ke Very High, sedangkan America, Pacific, Australia umumnya Low sepanjang tahun. Kesimpulannya, hotspot mitigasi UV berada di Indian & Africa; wilayah transisi di Asia/Europe; dan risiko relatif rendah di America/Pacific/Australia.

# Kesimpulan

Analisis menunjukkan pola yang konsisten lintas-region: wilayah tropis & maritim (Indian, Africa, Asia, Pacific) cenderung hangat dengan variabilitas musiman lebih kecil, sementara wilayah kontinental/lintang sedang (Europe, America, sebagian Asia) menampilkan rentang suhu paling lebar dan ekstrem musim panas–dingin yang jelas. Dominasi kondisi Sunny di Africa–Asia–Europe selaras dengan rata-rata suhu lebih tinggi dan—bersama rendahnya awan—berkaitan dengan risiko UV yang lebih besar. Perbandingan feels-like vs suhu menegaskan dua risiko utama: wind-chill pada suhu rendah dan heat index pada suhu hangat-lembap (kelembapan tinggi menaikkan feels-like di atas suhu aktual). Hasil clustering mengonfirmasi segmentasi ini ke tipe tropis-lembap, panas-kering/mediterania, maritim, dan temperate/continental, yang kemudian tercermin pada peta musiman UV dan kategori WHO, dengan Indian & Africa paling sering berada pada Very High–Extreme, sedangkan America/Pacific/Australia didominasi Low–Moderate. Secara keseluruhan, temuan ini memenuhi tujuan analisa: memetakan distribusi cuaca, mengungkap tren musiman & ekstrem, menilai hubungan antarvariabel (terutama suhu–kelembapan melalui feels-like), dan menyajikan visual yang membantu pembacaan pola serta implikasi kesehatannya

## Author 👨‍💻 
[Alviya Laela Lestari (202110370311400)](https://github.com/alviyalaela)

