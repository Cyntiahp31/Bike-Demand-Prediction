# Bike-Sharing
Link Canva: https://www.canva.com/design/DAGGTm5lVNE/U4u82vInGHAlufgh53yang/view?utm_content=DAGGTm5lVNE&utm_campaign=designshare&utm_medium=link&utm_source=editor

Link Video: https://drive.google.com/file/d/1Rn3j3iZd55on9FhpYlO0HlGIPT4vxcOB/view?usp=sharing

**Context**

Sistem bike sharing adalah penyediaan sepeda dan/atau sepeda listrik bagi penduduk kota, sehingga mereka dapat menyewa sepeda untuk jarak dekat atau jauh. Secara khusus, bike sharing digunakan untuk pergi ke tempat kerja, ke gym, ke sekolah, bertemu teman, dll. Oleh karena itu, banyak stasiun yang tersebar secara strategis di seluruh kota, yaitu dekat dengan tempat-tempat umum yang paling sering dikunjungi, sehingga memungkinkan orang untuk dengan mudah dan terjangkau menyewa dan mengembalikan sepeda dari satu lokasi ke lokasi lainnya. Pelanggan dapat menyewa sepeda dari satu stasiun, mengendarainya, dan cukup mengembalikannya di stasiun yang dekat tempat tujuan. Alhasil, pengguna tak perlu khawatir tentang parkir atau perawatan sepeda. (source: [PBSC](https://www.pbsc.com/blog/2022/01/what-is-a-bike-share-program-and-how-does-it-work))

Untuk menggunakan layanan bike share, pengguna dapat memilih untuk membeli langganan dan mengambil sepeda kapan pun mereka butuhkan atau mereka dapat memilih untuk membayar di setiap perjalanan. Meskipun skema penyewaan sepeda membutuhkan biaya, skema ini tetap merupakan solusi yang sangat terjangkau dibandingkan dengan sarana transportasi perkotaan lainnya. Jika dibandingkan, biaya keanggotaan bike sharing umumnya lebih rendah dibandingkan dengan biaya langganan transportasi umum, dan juga jauh lebih murah dibandingkan dengan biaya pembelian dan perawatan mobil. (source: [PBSC](https://www.pbsc.com/blog/2022/01/what-is-a-bike-share-program-and-how-does-it-work))

Dalam era di mana keberlanjutan menjadi perhatian utama, sistem berbagi sepeda juga membantu konsumen untuk mengadopsi gaya hidup yang lebih ramah lingkungan. Dengan menyediakan alternatif transportasi yang lebih berkelanjutan dan berbasis pada penggunaan berbagi sumber daya, sistem ini membantu mengurangi polusi udara dan emisi karbon, serta mendorong gaya hidup yang lebih aktif dan sehat. Dengan demikian, bisnis bike sharing tidak hanya menyediakan layanan transportasi yang praktis dan efisien, tetapi juga membantu masyarakat perkotaan untuk berpindah dari penggunaan kendaraan pribadi menuju opsi transportasi yang lebih berkelanjutan dan ramah lingkungan.

**Problem Statement**

Namun, sulit bagi perusahaan untuk dapat memprediksi permintaan sepeda per jam. Hal ini disebabkan oleh pengaruh eksternal seperti kondisi cuaca, musim, kelembaban, dan suhu lingkungan yang perubahannya sulit ditebak. Adanya pengaruh dari waktu dan status hari libur juga mengakibatkan demand sepeda berfluktuasi dari waktu ke waktu. Untuk mengatasinya, sangat penting bagi perusahaan bike sharing untuk memiliki sistem yang dapat memprediksi berapa banyak sepeda yang akan disewa pada jam dan kondisi tertentu. Ini memungkinkan perusahaan untuk menyesuaikan distribusi sepeda secara real-time, sehingga dapat memenuhi permintaan pengguna dengan lebih efektif dan efisien. Dalam konteks ini, prediksi permintaan sepeda per jam dapat digunakan untuk menyesuaikan layanan dan sumber daya dengan kebutuhan pengguna, yang alhasil meningkatkan kepuasan pengguna. Maka dari itu, dalam penelitian ini, kita akan me

**Goals**

Tujuan utama dari analisis ini adalah:

- Menganalisis pola penggunaan sepeda berdasarkan waktu, cuaca, dan faktor lainnya.
- Mengidentifikasi faktor-faktor kunci yang mempengaruhi jumlah penyewaan sepeda.
- Membangun model prediksi untuk meramalkan jumlah penyewaan sepeda di masa depan.
- Meningkatkan efisiensi operasional dengan memanfaatkan data prediksi untuk mengelola sumber daya secara lebih efektif.
- Mengurangi biaya pemeliharaan dan operasional melalui perencanaan yang lebih baik berdasarkan prediksi permintaan.
- Mengoptimalkan pendapatan perusahaan dengan memastikan ketersediaan sepeda sesuai dengan permintaan dan mengurangi biaya operasional terkait redistribusi sepeda.
- Meningkatkan kepuasan pelanggan, yang pada akhirnya dapat meningkatkan loyalitas pelanggan dan jumlah pengguna yang kembali.

**Evaluation Metrics**

Kita akan menggunakan metrics RMSLE dan standar deviasinya sebagai metrics utama. Karena, pada bisnis penyewaan sepeda, kesalahan relatif sering kali lebih penting dari besarannya. Misalnya, overestimation atau underestimation jumlah sepeda yang dibutuhkan pada waktu tertentu bisa memiliki dampak yang sama-sama besar. Hal ini tentunya sangat berguna dalam kasus rental sepeda, di mana ketika sepeda yang disediakan kurang, profit dan kepuasan pelanggan tentunya menurun, serta ketika prediksi lebih tinggi daripada demand, biaya logistik akan bertambah.

RMSLE dengan efektif meminimalisir efek berlebih dari kesalahan besar pada nilai-nilai besar karena mengukur kesalahan relatif, bukan perbedaan absolut seperti MAE. Kemudian, karena RMSLE mengukur perbedaan dalam skala logaritmik sehingga, kesalahan besar pada nilai-nilai besar tidak akan mendominasi keseluruhan kesalahan sebanyak dalam RMSE. Ini bermanfaat untuk data yang nilainya berdistribusi right-skewed atau di mana kesalahan pada nilai-nilai kecil dan besar sama-sama penting. Selain itu, RMSLE lebih dipilih daripada MAPE karena mengurangi pengaruh kesalahan besar pada prediksi tinggi, yang merupakan fitur kritis dalam mengoptimalkan sumber daya dan mengelola persediaan sepeda secara efisien. RMSLE mendorong model untuk menjadi akurat dalam memprediksi proporsi daripada perbedaan mutlak, yang sangat berguna dalam menghindari biaya logistik yang tidak perlu atau kekurangan pasokan yang dapat menurunkan kepuasan pelanggan.

**Analytics Approach**

**Kita akan melakukan analisis regresi di mana variabel targetnya adalah jumlah sepeda yang dirental dalam satu jam, sedangkan variabel independennya antara lain jam, musim, cuaca, temperatur, dan lain-lain**. Tahapan pertama dalam analisis ini adalah memahami data beserta atribut yang ada. Kemudian, bersihkan data dari anomali dan missing values. Lalu peroleh insight dari data melalui exploratory data analysis. Kemudian, kita lakukan pengolahan data agar data kategorik dapat diproses oleh model machine learning. Setelah data siap, kita akan melakukan proses pemodelan machine learning yang akan memprediksi hourly demand dari sepeda rental berdasarkan variabel-variabel yang ada. Untuk mengetahui *goodness-of-fit* dari model yang telah kita buat, kita akan menggunakan beberapa metrics. Metrics utama yang dipilih akan dilihat berdasarkan hasil analisis pada EDA. Terakhir kita juga akan membuat rekomendasi yang sesuai untuk permasalahan yang ada agar dapat diterapkan oleh pelaku bisnis serta memprediksi kenaikan keuntungan apabila perusahaan menerapkan rekomendasi tersebut.
