# UJIAN AKHIR SEMESTER
## ANGGOTA KELOMPOK
<div align='center'>
 
![Teams](https://img.shields.io/badge/Anggota%20Kelompok-Kelompok%205-purple)
 
<br>
 
![1197050051](https://img.shields.io/badge/122-Rifky%20Zaini%20Faroj-blue)
![1197050049](https://img.shields.io/badge/123-Rifqi%20Syekhi%20Marsaputra-blue)
![1197050085](https://img.shields.io/badge/130-Salma%20Khoirunnisa-blue)
![1197050119](https://img.shields.io/badge/137-Sumitra%20Adriansyah-blue)
![1197050079](https://img.shields.io/badge/144-Youmil%20Akbar-blue)
![1197050079](https://img.shields.io/badge/147-Yuqa%20Sakif%20Ardiansyah-blue)
 
<br> 
 
Jurusan Teknik Informatika UIN Sunan Gunung Djati Bandung

Deskripsi Umum
Penggaris Digital adalah perangkat yang dapat digunakan untuk mengukur jarak menggunakan sensor. Ada beberapa cara untuk mengimplementasikan Sensor jarak tetapi modul yang digunakan dalam proyek ini adalah Sensor HC-S04. Dengan menghubungkan Sensor HC-S04 dengan Arduino, Anda bisa mengukur jarak menggunakan sensor tanpa mengukur manual.

Sensor ultrasonic dengan tipe HCSR04 adalah suatu komponen yang dapat diaplikasikan sebagai pengukuran jarak daru suatu benda. Taksiran dari jarak yang dapat ditempuk oleh komponen ini adalah 2 – 450 cm. Komponin ini memiliki dua pin digital yang berfungsi untuk menghubungkan jarak yang telah terbaca. Cara kerja atau prinsip kerja yang dilakukan oleh sensor ultrasonic ini yaitu dengan mengirimkan pulsa ultrasonic sebesar 40 kHz, selanjutnya pulsa echo akan dipantulkan kembali, serta menghitung waktu yang didapatkan dengan satuan microsecond. 


Alat dan Bahan
NO	NAMA ALAT DAN BAHAN	JUMLAH 
1	Laptop/pc ( Arduino IDE)	1
2	HC-S04 Ultrasonic distance measuring transducer sensor module 	1
3	Breadboard minisolderless 400 400 p	1
4	LCD 1602 Char Blue Backlight with 12 c serial interface module	1
5	Jumper cable 20 cm male to female dopont for breadboard	1
7	Jumper cable kabel 30 cm male to female dupont for breadboard 	1
9	Buzzer speaker active 5v for arduino uno mega mini nano	1

Rangkaian
1.	Siapkan alat alat 
2.	Arduino, HC-SR04 ULTRASONIC DISTANCE MEASURING TRANSDUCER SENSOR MODULE, BREADBOARD MINI SOLDERLESS 400 400P, LCD 1602 CHAR BLUE BACKLIGHT WITH I2C SERIAL INTERFACE MODULE, JUMPER CABLE MALE TO FEMALE + MALE TO MALE, BUZZER SPEAKER ACTIVE 3V 3.3V
3.	Hubungkan kabel LCD GND --> -BREADBOARD // VCC --> 5V ARDUINO // SDA --> A4 ARDUINO // SCL --> A5 ARDUINO
4.	Kemudian HC-SR04 ULTRASONIC GND --> -BREADBOARD // ECHO --> 12 ARDUINO // TRIG --> 11 ARDUINO // VCC --> + BREADBOARD
5.	BUZZER SPEAKER (+) --> 3.3V ARDUINO // (-) --> -BREADBOARD
6.	(+)BREADBOARD --> 5V ARDUINO // (-)BREADBOARD --> GND ARDUINO


Source Code
Install terlebih dahulu Arduino IDE-nya, lalu buka aplikasinya, untuk codingan dari rangkaian ini adalah sebagai berikut.

#include <HCSR04.h>                 //Library HCSR04
#include <LiquidCrystal_I2C.h>      //Library LCD I2C
LiquidCrystal_I2C lcd(0x27,16,2);   //Alamat I2C
HCSR04 hc(11,12);                   //initialisation class HCSR04 (trig pin , echo pin)

void setup() {
  lcd.init ();                      //Mulai LCD
  lcd.setBacklight(HIGH);
}

void loop() {
  lcd.setCursor(1,0);
  pinMode(10, OUTPUT);
  lcd.print("DIGITAL  RULER");

  lcd.setCursor(4,1);
  lcd.print(hc.dist());        	//Baca dan tampilkan jarak
  lcd.print(" CM");
  if (hc.dist() > 50) {
   digitalWrite(10, HIGH);
   delay(100);
   digitalWrite(10, LOW);
} else {
   digitalWrite(10, LOW);
}

  delay(1500);
  lcd.clear(); 
}

Output
Output dari rangkaian di atas adalah ketika kita menaruh benda misal 30cm dari sensor maka sensor akan mendeteksi dan mengeluarkan bunyi (buzzer) bahwa penggaris digital ini bekerja, nanti di layar LCD akan ada output “DIGITAL RULER” “Jarak: 30cm”. Kadang jarak yang dihitung ini tidak seakurat di hitung manual pakai penggaris.


Referensi
Nugraha, Fandhi (2015). Tugas Sensor Ultrasonik HC-SR04.

Sakti,Elang. Cara Kerja Sensor Ultrasonik, Rangkaian, & Aplikasinya, dari https://www.elangsakti.com/2015/05/sensor-ultrasonik.html

L, Tokheira Roger, (1995), Elektronika Digital, edisi Kedua, Erlangga, Jakarta.

McRobert, M. 2011. Beginning Arduino. Edisi Ke-2. Apress. USA.

Sri Widodo Thomas, Dr. Ir. 2002. Elektronika Dasar. Erlangga, Jakarta.
