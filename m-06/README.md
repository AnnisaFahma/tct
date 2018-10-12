# Membuat Endpoint untuk bisa diakses di GET 

Pada praktik kali ini saya menggunakan Node js, sehinga langkah untuk membuat Endpoint tersebut seperti dibawah ini :

+ ## Instalasi Node js, dengan cara : 

1. Download Node.JS Installer pada website resminya di https://nodejs.org/download/
2. Jalankan file msi yang sudah didownload.
3. Ikuti petunjuk dan User Agreement. Dan tunggu sampai installasi selesai
4. Sekarang kalian restart computer kalian agar node js dapat terinstall dengan sempurna

Nahh.. Jika sudah mengikuti tahap-tahap diatas, maka sekarang NodeJS sudah terinstall
Untuk mengetahuinya bisa buka command prompt, dan ketikan kode berikut :

	node -v
	(digunakan untuk melihat versi node js yang terinstal)
	
	npm -v
    (untuk melihat versi npm yang terinstall)
	
jika sudah maka sekarang saatnya untuk:
 
+ ## Menginstall FrameWork Express dengan cara berikut ini :

1. Menentukan dimana kita akan menginstal express, disni saya menggunakan direktori C:\nodejs\ untuk meletakkan hasil instalasi express
2. Memasukkan perintah instalan express dengan menggunakan 

	npm install -g express

Jika proses instalasi selesai, Kemudian dilajutkan untuk menginstal express generator secara global dengan perintah :

	npm install -g express–generator

3. Membuat file project express baru dengan memasukkan perintah seeperti dibawah ini :

	express tct -e
	(project saya beri nama tct)
	
4. Setelah selai maka langkah selanjutnya adalah menginsatal dependencies dengan memasukkan perintah:

	cd tct && npm install 
	(cd tct karena project saya namanya tct)
	
5. Mengaktifkan npm dengan sintak 

	npm start
	
6. Setelah itu memastikan bahwa express telah terinstal yaitu dengan memasukkan alamn localhost:3000 di browser. Jika berhasil maka hasilnya akan seperti ini

![hasil](https://github.com/AnnisaFahma/tct/blob/master/images/ex3.jpg)

## _jika sudah berhasil maka yang selanjutnya saya lakukkan adalah membuat file yg digunakan untuk mengkoneksikan ke server, file ini saya namai server.js_
   _adapun sintaknya adalah seperti berikut ini:_

	const express = require('express')
	const app = express()
	const port = 3000
	//ketiga sintak diatas itu digunakan untuk menjelaskan setiap variabel yang akan berfungsi untuk menghubungkan ke framework Express

	app.get('/', function (req, res) {
	res.jsonp({ User: 'Annisa Fahma Aziza Y' , NIM: '163210007' , Jurusan: 'Komputerisasi Akuntansi' });
	//sintak ini berfungsi untuk mengirimkan respon berupa file json yang berisi (user : Annisa Fahma Aziza Y)
	//dan sintak yang res.jsonp({ User: 'Annisa Fahma Aziza Y' , NIM: '163210007' , Jurusan: 'Komputerisasi Akuntansi' });  ==> _INI MERUPAKAN ENDPOINT YANG SAYA BUAT HARI INI DENGAN MENGGUNAKAN NODE JS_

	app.listen(port, () => console.log(`Example app listening on port ${port}!`))
	//sintak ini berfungsi untuk membuka port server dengan menggunakan fungsi console.log yang nantinya akan mendebug sintak yang kita masukkan
	
setelah dibuat maka kita kembali masuk ke command line lagi untuk melihat apakah sudah berhasil atau belum, dengan menggunakan sintak 

	node server.js
	
dan jika hasilnya sudah seperti dibawah ini itu artinya sudah berhasil 

![hasil](https://github.com/AnnisaFahma/tct/blob/master/images/ex4.jpg)

Lalu kita buka browser dengan sintak seperti dibawah ini, untuk melihat hasil atau respon yang dihasilkan

	localhost:3000
	
dan jika hasilnya sudah seperti dibawah ini itu artinya sudah berhasil 

![hasil](https://github.com/AnnisaFahma/tct/blob/master/images/ex5.jpg)

SEKIAN PRAKTIK HARI INI 
	
