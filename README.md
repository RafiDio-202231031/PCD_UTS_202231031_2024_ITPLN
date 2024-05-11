#1
-
<br>import cv2 </br>
<br>import numpy as np</br>
<br>import matplotlib.pyplot as plt</br>
<br>import matplotlib.image as img</br>
<br>%matplotlib inline</br>
<br>Penjelasan:</br>
<br>1.import cv2 ni mengimpor modul OpenCV, yang digunakan untuk pemrosesan gambar </br>
<br>2.import numpy as np Ini berfungsi mengimpor modul NumPy, yang digunakan untuk operasi numerik dan array</br>
<br>3.import matplotlib.pyplot as plt Ini berfungsi untuk mengimpor modul pyplot dari Matplotlib, yang digunakan untuk membuat visualisasi seperti plot, grafik, dan gambar</br>
<br>4.mport matplotlib.image as img Ini berfungsi untuk mengimpor submodul image dari Matplotlib, yang digunakan untuk membaca dan menampilkan gambar
%matplotlib inline Ini adalah perintah khusus untuk Jupyter Notebook yang memberitahu Matplotlib untuk menampilkan plot secara langsung di dalam notebook, bukan dalam jendela popup terpisah</br>

#2
-
<br>color_gambar=img.imread('saya.jpg')</br>
<br>plt.imshow(color_gambar)</br>
<br>Penjelasan:</br>
<br>1.color_gambar=img.imread('saya.jpg') berfungsi untuk membaca gambar yang disebut 'saya.jpg' menggunakan fungsi img.imread() dari modul Matplotlib. </br>
<br>2.plt.imshow(color_gambar): Ini menampilkan gambar yang telah dibaca sebelumnya menggunakan fungsi imshow dari modul matplotlib.pyplot yang telah diimpor sebelumnya sebagai plt. </br>
<br>Gambar ditampilkan di output notebook Jupyter karena perintah %matplotlib inline yang telah Anda jalankan sebelumnya.</br>

#3
-
<br>r = color_gambar[:, :, 0] </br>
<br>g = color_gambar[:, :, 1] </br>
<br>b = color_gambar[:, :, 2]</br>

<br>f, (c1, c2, c3, c4) = plt.subplots(1, 4, figsize = (20,10))</br>

<br>c1.set_title('Gambar Real')</br>
<br>c1.imshow(color_gambar) </br>
<br>c1.axis('off')</br>

<br>c2.set_title('Red') </br>
<br>c2.imshow(r, cmap="gray") </br>
<br>c2.axis('off')</br>

<br>c3.set_title('Green') </br>
<br>c3.imshow(g, cmap="gray") </br>
<br>c3.axis('off')</br>

<br>c4.set_title('Blue') </br>
<br>c4.imshow(b, cmap="gray")</br>
<br>c4.axis('off')</br>
<br>penjelasan:</br>
<br>1.r = color_gambar[:, :, 0], g = color_gambar[:, :, 1], b = color_gambar[:, :, 2] Ini mengambil saluran warna merah, hijau, dan biru (R, G, B) dari gambar berwarna. Pada array numpy, dimensi pertama mewakili baris, dimensi kedua mewakili kolom, dan dimensi ketiga mewakili saluran warna.
  f, (c1, c2, c3, c4) = plt.subplots(1, 4, figsize = (20,10)): Ini membuat gambar subplot dengan 1 baris dan 4 kolom, dan ukuran figur (figure size) 20x10.</br>
<br>2.c1.set_title('Gambar Real'), c2.set_title('Red'), c3.set_title('Green'), c4.set_title('Blue') Ini berfungsi menetapkan judul untuk masing-masing subplot.</br>
<br>3.c1.imshow(color_gambar), c2.imshow(r, cmap="gray"), c3.imshow(g, cmap="gray"), c4.imshow(b, cmap="gray") Ini berfungsi menampilkan gambar asli dan saluran warna merah, hijau, dan biru (dalam skala abu-abu) di subplot yang sesuai. 
  Pengaturan cmap="gray" digunakan untuk menampilkan gambar dalam skala abu-abu.</br>
<br>4.c1.axis('off'), c2.axis('off'), c3.axis('off'), c4.axis('off') Ini berfungsi menonaktifkan sumbu pada setiap subplot, sehingga sumbu x dan y tidak ditampilkan.</br>

#4
-
<br>color_gambar = cv2.imread('saya.jpg')</br>
<br>penjelasan:</br>
<br>1.color_gambar = cv2.imread('saya.jpg') bertujuan untuk membaca sebuah gambar yang disimpan dalam file dengan nama 'saya.jpg'. </br>
#5
_
<br>color_gambar= cv2.cvtColor(color_gambar,cv2.COLOR_BGR2RGB)</br>
<br>penjelasan:</br>
<br>1.color_gambar = cv2.cvtColor(color_gambar, cv2.COLOR_BGR2RGB) bertujuan untuk mengonversi gambar yang telah dibaca sebelumnya menggunakan OpenCV (yang dibaca dalam format BGR) ke format RGB.</br>

#6
-
<br>histogram_blue= cv2.calcHist([b],[0],None,[256],[0,256])</br>
<br>histogram_green= cv2.calcHist([g],[0],None,[256],[0,256])</br>
<br>histogram_red= cv2.calcHist([r],[0],None,[256],[0,256])</br>
<br>histogram_warna = cv2.calcHist([color_gambar],[0,1,2],None,[256,256,256],[0,256,0,256,0,256])</br>
<br>penjelasan:</br>
<br>1.histogram_blue = cv2.calcHist([b], [0], None, [256], [0, 256]) Ini adalah perintah untuk menghitung histogram dari saluran warna biru (b). 
  Fungsi calcHist dari OpenCV digunakan untuk menghitung histogram.</br>
<br>2.histogram_green = cv2.calcHist([g], [0], None, [256], [0, 256]) Ini adalah perintah yang serupa dengan sebelumnya, tetapi untuk saluran warna hijau (g). 
  code ini menghasilkan histogram untuk saluran warna hijau dengan parameter yang sama seperti yang telah dijelaskan sebelumnya.</br>
<br>3.histogram_red = cv2.calcHist([r], [0], None, [256], [0, 256]) Ini adalah perintah yang serupa dengan sebelumnya, tetapi untuk saluran warna merah (r). </br>
  Ini menghasilkan histogram untuk saluran warna merah dengan parameter yang sama seperti yang telah dijelaskan sebelumnya.
<br>4.histogram_warna = cv2.calcHist([color_gambar], [0,1,2], None, [256,256,256], [0,256,0,256,0,256]) Ini adalah perintah untuk menghitung histogram dari seluruh gambar berwarna (color_gambar). </br>

#7
-
<br>plt.figure (figsize=(12,8))</br>

<br>plt.subplot(2,2,1)</br>
<br>plt.plot(histogram_blue,color='b')</br>
<br>plt.title('Histogram Blue')</br>
<br>plt.xlim([0,256])</br>

<br>plt.subplot(2,2,2)</br>
<br>plt.plot(histogram_green,color='g')</br>
<br>plt.title('Histogram Green')</br>
<br>plt.xlim([0,256])</br>

<br>plt.subplot(2,2,3)</br>
<br>plt.plot(histogram_red,color='r')</br>
<br>plt.title('Histogram Red')</br>
<br>plt.xlim([0,256])</br>

<br>plt.subplot(2,2,3)</br>
<br>plt.plot(histogram_='r')</br>
<br>plt.title('Histogram Red')</br>
<br>plt.xlim([0,256])</br>

<br>plt.subplot(2, 2, 4)</br>
<br>plt.plot(histogram_warna.flatten(), color='gray')</br>
<br>plt.title('Histogram Abu-abu')</br>
<br>plt.xlim([0, 256])</br>
<br>Penjelasan:</br>
<br>1.plt.figure(figsize=(12,8)) Ini membuat sebuah gambar (figure) baru dengan ukuran 12x8 inci menggunakan Matplotlib.</br>
<br>2.plt.subplot(2,2,1), plt.subplot(2,2,2), plt.subplot(2,2,3), plt.subplot(2,2,4) Ini berfungsi membuat subplot-grid dengan 2 baris dan 2 kolom. 
Dengan perintah ini, kita membuat empat subplot yang akan diisi nanti dengan histogram warna biru, hijau, merah, dan histogram keseluruhan gambar.</br>
<br>3.plt.plot(histogram_blue, color='b'), plt.plot(histogram_green, color='g'), plt.plot(histogram_red, color='r'): Ini menggambar plot dari histogram warna biru, hijau, dan merah. 
Parameter color='b', color='g', dan color='r' digunakan untuk menentukan warna plot sesuai dengan saluran warna yang sesuai.</br>
<br>4.plt.title('Histogram Blue'), plt.title('Histogram Green'), plt.title('Histogram Red') Ini memberikan judul untuk setiap subplot yang menunjukkan warna yang diplot.</br>
<br>5.plt.xlim([0,256]) Ini menetapkan rentang sumbu x dari 0 hingga 256 pada setiap subplot untuk menampilkan seluruh rentang nilai intensitas warna (0-255).</br>
<br>6.plt.subplot(2,2,3) Ini merupakan kesalahan, karena subplot yang ketiga sudah digunakan sebelumnya. Seharusnya menjadi plt.subplot(2,2,4) untuk membuat subplot keempat.</br>

#8
-
<br>1.import cv2, numpy as np, from matplotlib import pyplot as plt: Ini mengimpor modul-modul yang dibutuhkan untuk memproses gambar (OpenCV dan NumPy) serta untuk menampilkan hasilnya (Matplotlib).</br>
<br>2.def increase_brightness(image, value=30): ...: Ini adalah definisi dari sebuah fungsi bernama increase_brightness yang bertujuan untuk meningkatkan kecerahan gambar. Fungsi ini menerima dua parameter image, yang merupakan gambar yang akan ditingkatkan kecerahannya, 
dan value yang merupakan nilai penambahan kecerahan (default=30).</br>
<br>3.def detect_and_highlight_blue(image) Ini adalah definisi dari fungsi detect_and_highlight_blue yang bertujuan untuk mendeteksi dan menyorot warna biru dalam gambar. 
Fungsi ini menerima satu parameter image, yang merupakan gambar yang akan diproses.</br>
<br>4.def detect_and_highlight_red_blue(image): ...: Ini adalah definisi dari fungsi detect_and_highlight_red_blue yang bertujuan untuk mendeteksi dan menyorot warna merah dan biru dalam gambar. 
Fungsi ini menerima satu parameter image, yang merupakan gambar yang akan diproses.</br>
<br>5.def detect_and_highlight_red_green_blue(image): ...: Ini adalah definisi dari fungsi detect_and_highlight_red_green_blue yang bertujuan untuk mendeteksi dan menyorot warna merah, hijau, dan biru dalam gambar.
Fungsi ini menerima satu parameter image, yang merupakan gambar yang akan diproses.</br>
<br>6.image = cv2.imread('saya.jpg'): Ini membaca gambar yang disimpan dalam file dengan nama 'saya.jpg' menggunakan fungsi imread dari OpenCV (cv2) dan memuatnya ke dalam variabel image.</br>
<br>7.brightened_image = increase_brightness(image): Ini memanggil fungsi increase_brightness untuk meningkatkan kecerahan gambar yang telah dibaca sebelumnya dan menyimpan hasilnya dalam variabel brightened_image.</br>
<br>8.blue_detection = detect_and_highlight_blue(brightened_image): Ini memanggil fungsi detect_and_highlight_blue untuk mendeteksi dan menyorot warna biru dalam gambar yang telah ditingkatkan kecerahannya dan menyimpan hasilnya dalam variabel blue_detection.</br>
<br>9.red_blue_detection = detect_and_highlight_red_blue(brightened_image): Ini memanggil fungsi detect_and_highlight_red_blue untuk mendeteksi dan menyorot warna merah dan biru dalam gambar yang telah ditingkatkan kecerahannya dan menyimpan hasilnya dalam variabel red_blue_detection.</br>
<br>10.red_green_blue_detection = detect_and_highlight_red_green_blue(brightened_image): Ini memanggil fungsi detect_and_highlight_red_green_blue untuk mendeteksi dan menyorot warna merah, hijau, dan biru dalam gambar yang telah ditingkatkan kecerahannya dan menyimpan hasilnya dalam variabel red_green_blue_detection.</br>
<br>11.plt.figure(figsize=(10, 8)): Ini membuat sebuah gambar baru (figure) dengan ukuran 10x8 inci menggunakan Matplotlib untuk menampilkan hasil deteksi warna.</br>
<br>12.plt.subplot(221), plt.imshow(cv2.cvtColor(brightened_image, cv2.COLOR_BGR2RGB)), plt.title('Contrast Image'): Ini menambahkan subplot pertama yang menampilkan gambar yang telah ditingkatkan kecerahannya dengan judul 'Contrast Image'.</br>
<br>13.plt.subplot(222), plt.imshow(cv2.cvtColor(blue_detection, cv2.COLOR_BGR2RGB)), plt.title('Blue Color Detection'): Ini menambahkan subplot kedua yang menampilkan hasil deteksi dan penyorotan warna biru dengan judul 'Blue Color Detection'.</br>
<br>14.plt.subplot(223), plt.imshow(cv2.cvtColor(red_blue_detection, cv2.COLOR_BGR2RGB)), plt.title('Red-Blue Color Detection'): Ini menambahkan subplot ketiga yang menampilkan hasil deteksi dan penyorotan warna merah dan biru dengan judul 'Red-Blue Color Detection'.</br>
<br>15.plt.subplot(224), plt.imshow(cv2.cvtColor(red_green_blue_detection, cv2.COLOR_BGR2RGB)), plt.title('Red-Green-Blue Color Detection'): Ini menambahkan subplot keempat yang menampilkan hasil deteksi dan penyorotan warna merah, hijau, dan biru dengan judul 'Red-Green-Blue Color Detection'.</br>
<br>16.plt.show(): Ini menampilkan hasil</br>

#REFENRENSI

<br>1.https://stackoverflow.com/questions/24575680/new-lines-inside-paragraph-in-readme-md</br>
<br>2.https://www.w3schools.com/python/default.asp</br>



