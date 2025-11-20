# Praktikum Lab IV Basic Analog Electronic
## Post-Lab LCD & Sensor Suhu LM35

Identitas
- Nama : Walfihen
- Npm : 24100171514007
- TRKJ 24
- Fakultas Teknologi Industri
- Universitas Bung Hatta

## Tujuan Praktikum
- Memahami pengertian dan prinsip kerja LCD.
- Mengamati cara kerja sensor suhu LM35.
- Menampilkan data suhu dari LM35 ke display LCD.
- Menghubungkan LCD dan LM35 dalam sistem berbasis mikrokontroler.

## Dasar Teori
### 1. Pengertian LCD
LCD (Liquid Crystal Display) adalah layar yang menggunakan **kristal cair** untuk mengatur cahaya dan menampilkan teks atau gambar. LCD bekerja berdasarkan perubahan orientasi kristal cair yang mengatur jumlah cahaya yang melewati panel.

### 2. Cara Kerja LCD
LCD terdiri dari beberapa lapisan:
1. Backlight
2. Filter Polarisasi
3. Kristal Cair
4. Filter Warna RGB

Kristal cair diatur oleh arus listrik sehingga menentukan tampilan huruf/angka.

### 3.Pengertian Sensor Suhu LM35
LM35 adalah **sensor suhu analog** yang menghasilkan tegangan sebanding dengan suhu.  
Karakteristik LM35:
- Output: **10 mV per 1°C**
- Akurasi tinggi (±0.5°C)
- Rentang pengukuran: -55°C sampai 150°C
- Tidak memerlukan kalibrasi

Contoh konversi analog:  
Jika ADC membaca 310 mV → suhu = **31°C**

### 4. Cara Kerja LM35
- LM35 menghasilkan tegangan analog (0–1,5 V).
- Mikrokontroler membaca nilai analog tersebut melalui pin ADC.
- Nilai digital dikonversi ke Celsius dengan rumus:  
  **Suhu (°C) = (ADC_value × 5V / 1024) / 0.01V**

### 5. Alat dan Bahan
- Unit LCD ( modul LCD 16x2)
- Sensor suhu LM35
- Kabel jumper 
- Breadboard 
- Arduino Uno
- Laptop / PC

### 6. Langkah Kerja
1. Merangkai LCD sesuai diagram pin.
2. Merangkai sensor LM35 pada A0 Arduino.
3. Menghubungkan Arduino ke laptop.
4. Mengupload program pembacaan suhu.
5. Mengamati tampilan suhu di LCD.
6. Mencatat hasil pengamatan setiap 10 detik.
### code Program :
int sensorPin = A0;   // LM35 terhubung ke pin A0

void setup() {
  Serial.begin(9600); // Mulai Serial Monitor
}

void loop() {
  // 1. Baca nilai analog (0–1023)
  int nilaiADC = analogRead(sensorPin);

  // 2. Konversi ADC -> Tegangan
  float volt = nilaiADC * (5.0 / 1023.0);

  // 3. Konversi Tegangan -> Suhu (LM35 = 10mV per °C)
  float suhu = volt * 100.0;

  // 4. Tampilkan hasil
  Serial.print("ADC: ");
  Serial.print(nilaiADC);

  Serial.print(" | Volt: ");
  Serial.print(volt);

  Serial.print(" V | Suhu: ");
  Serial.print(suhu);
  Serial.println(" C");

  delay(500); // jeda 0.5 detik
}

### Gambar Rangkaian LCD
![alt text](https://github.com/walfihen/Post-Lab-LCD/blob/aea3b2be15bb95940cf02ffe6433aa5c831e8127/Sreenshoot/post-lab%20lcd%20(rangkaian).jpg?raw=true)

### Gambar Rangkaian Sensor Suhu LM35
![alt text](https://github.com/walfihen/Post-Lab-LCD/blob/a86216423eafbf16fa1688ce8cacfd93a4eb2bb1/Sreenshoot/rangkaian%20sensor%20suhu.jpg?raw=true)

### 7. Hasil Pengamatan
![alt text](https://github.com/walfihen/Post-Lab-LCD/blob/2a9a80becdcc0ea44bf9f88b97ef2093e253e10a/Sreenshoot/post-lab%20LCD.jpg?raw=true)Kesimpulan

### 8.Kesimpulan
- LCD dapat menampilkan data suhu dari LM35 dengan baik.
- LM35 memiliki keakuratan cukup tinggi tanpa kalibrasi.
- Kombinasi LCD dan LM35 sangat cocok untuk sistem monitoring suhu.






