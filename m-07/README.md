# Membuat / mempersiapkan Daas dengan menggunakan Database

Pada praktik kali ini saya menggunakan javaScript dengan software database _mysql_

Adapun langkah -langkah yang saya lakukkan adaah sebagai berikut :

## 1. Install dulu mysql package

Kita harus menginstall package mysql dulu dikarenakan Kita membutuhkan modul mysql untuk menghubungkan Nodejs dengan MySQL.
Modul ini tidak dibawa secara default oleh Nodejs. Karena itu, kita harus menginstalnya.
Adapun perintah yang digunakan untuk menginstal module tersebut adalah sebagai berikut :

		npm install mysql
		
## 2. Install body parser package

Package body-parser ini dipake untuk ngeparsing setiap request yang masuk melalui HTTP, baik itu dengan x-www-form-urlencoded, 
raw json, dan form data. Package ini akan memudahkan method parsing dari apa saja yang disubmit melalui rest api kita.

Adapun perintah yang digunakan untuk menginstal module body parser tersebut adalah sebagai berikut :

		npm install --save express mysql body-parser
		
## 3. Membuat database dan tabel yang akan ditampilkan 

+ Database yang saya buat adalah : mahasiswa
+ Table yang saya buat adalah : datadiri dengan 3 kolom yaitu --> (id, name, address)

Sehingga tabel yang saya buat hasilnya seperti dibawah ini :

![tabel](https://github.com/AnnisaFahma/tct/blob/master/images/table2.jpg)

## 4. Membuat file file yang akan digunakan seperti : 
+ file server.js (untuk koneksi webserver)
+ file conn.js (untuk koneksi ke database mysql)
+ file controller.js (digunakan untuk memasukkan query yang akan digunakan untuk pengambilan data dari tabel _datadiri_ (kali ini data yang saya ambil adalah data dari mahasiswa yang id nya "001")
+ file res.js (digunakan untuk parameter apa yang akan di send atau dikirim dan valuenya itu seperti apa)
+ file routes.js (digunakna untuk memebuat _endpoint_ yang akan kita gunakan didalam REST APL kita)

Alasan saya memisahkan file-file tersebut adalah suapaya saya tidak bingung fungsi dari masing masing file tersebut,
karena jika saya jadikan satu  saya masih bingung untuk memahami fungsi dari setiap perintah yang ada.

Adapun file-file tersebut querynya adalah sebagai berikut :

### + file server.js

		var express = require('express'),
		app = express(),
		port = process.env.PORT || 3000,
		bodyParser = require('body-parser'),
		controller = require('./controller');

		app.use(bodyParser.urlencoded({ extended: true }));
		app.use(bodyParser.json());

		var routes = require('./routes');
		routes(app);

		app.listen(port);
		console.log('Learn Node JS With Kiddy, RESTful API server started on: ' + port);
		
### + file conn.js
		
		var mysql = require('mysql');

		var con = mysql.createConnection({
		host: "localhost",
		user: "root",
		password: "",
		database: "mahasiswa"
		});

		con.connect(function (err){
			if(err) throw err;
		});

		module.exports = con;
		
### + file controller.js

		'use strict';

		var response = require('./res');
		var connection = require('./conn');

			exports.users = function(req, res) {
			connection.query('SELECT * FROM datadiri where id="001"', function (error, rows, fields){
				if(error){
					console.log(error)
				} else{
					response.ok(rows, res)
				}
			});
		};

		exports.index = function(req, res) {
			response.ok("Hello from the Node JS RESTful side!", res)
		};

		
### + file res.js

		'use strict';

		exports.ok = function(values, res) {
		var data = {
			'status': 200,
			'values': values
		};
		res.json(data);
		res.end();
		};

### + file routes.js

		'use strict';

		module.exports = function(app) {
			var todoList = require('./controller');

			app.route('/')
				.get(todoList.index);

			app.route('/users')
				.get(todoList.users);
		};

Sekarang waktunya kita coba dengan menggunakan query dibawah ini pada Cpmmand Line, yang sebelumnya telah masuk di Folder tempat kita menyimpan file _sever.js_

		node server.js
		
Jika hasilnya seperti dibawah ini, itu artinya sudah berhasil :

![hasilcmd](https://github.com/AnnisaFahma/tct/blob/master/images/konek1.jpg)

Sekarang coba kita buka browser dan ketikkan :

		localhost:3000
		
Jika hasilnya seperti dibawah ini, itu artinya sudah berhasil :

![hasilcmd](https://github.com/AnnisaFahma/tct/blob/master/images/konek2.jpg)

Dilanjutkan dengan mengetikkan :

		localhost:3000/users
		(untuk menampilkan respon json yang iainya adalah data dari tabel yang sudah saya buat)
		
Jika hasilnya seperti dibawah ini, itu artinya sudah berhasil :

![hasilcmd](https://github.com/AnnisaFahma/tct/blob/master/images/konek3.jpg)

Yang ditampilkan hanya satu Field saja idkarenakan tadi yang saya panggil hanya mahasiswa dengan id = 001

_SEKIAN PRAKTIK HARI INI :)_

### 5. 