Pengantar Struktur Data 

>> .Kami akan mulai dengan ikhtisar singkat dan tidak komprehensif dari struktur data fundamental di panda untuk memulai. Perilaku mendasar tentang tipe data, pengindeksan, dan pelabelan / pelurusan sumbu berlaku di semua objek. Untuk memulai, impor NumPy dan muat panda ke ruang nama Anda:

 ## In [1]:  import numpy as np

## In [2]:  import pandas as pd

Berikut adalah prinsip dasar yang harus diingat: penyelarasan data bersifat intrinsik . Tautan antara label dan data tidak akan rusak kecuali dilakukan secara eksplisit oleh Anda.

Kami akan memberikan intro singkat ke struktur data, kemudian mempertimbangkan semua kategori fungsionalitas dan metode yang luas di bagian terpisah.

Seri 
Series adalah larik berlabel satu dimensi yang mampu menyimpan semua tipe data (bilangan bulat, string, angka floating point, objek Python, dll.). Label sumbu secara kolektif disebut sebagai indeks . Metode dasar untuk membuat Seri adalah memanggil:

 >>>  s = pd . Series ( data , index = index )
Di sini, data bisa banyak hal berbeda:

sebuah Python dict
sebuah ndarray
nilai skalar (seperti 5)
Indeks yang diteruskan adalah daftar label sumbu. Jadi, ini memisahkan menjadi beberapa kasus tergantung pada data apa itu :

Dari ndarray

Jika data adalah ndarray, indeks harus memiliki panjang yang sama dengan data . Jika tidak ada indeks yang dilewatkan, yang akan dibuat memiliki nilai [0, ..., len(data) - 1] .

 >>.In [3]:  s = pd . Series ( np . random . randn ( 5 ), index = [ 'a' , 'b' , 'c' , 'd' , 'e' ])

>>.In [4]:  s
Out[4]:  
a    0.4691
b   -0.2829
c   -1.5091
d   -1.1356
e    1.2121
dtype: float64

In [5]:  s . index
                                                                                    Out[5]: Index(['a', 'b', 'c', 'd', 'e'], dtype='object')

In [6]:  pd . Series ( np . random . randn ( 5 ))
                                                                                                                                             Out[6]: 
0   -0.1732
1    0.1192
2   -1.0442
3   -0.8618
4   -2.1046
dtype: float64
