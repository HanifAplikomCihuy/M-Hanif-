# M Hanif Maulana_23030630076_EMT Plot 2D
M Hanif Maulana Hartono


Matematika B 2023


23030630076


# Menggambar Grafik 2D dengan EMT

Notebook ini menjelaskan tentang cara menggambar berbagaikurva dan
grafik 2D dengan software EMT. EMT menyediakan fungsi plot2d() untuk
menggambar berbagai kurva dan grafik dua dimensi (2D).


## Plot Dasar

Ada fungsi yang sangat mendasar dari plot. Ada koordinat layar, yang
selalu berkisar dari 0 hingga 1024 di setiap sumbu, tidak peduli
apakah layarnya persegi atau tidak. Semut ada koordinat plot, yang
dapat diatur dengan setplot(). Pemetaan antara koordinat tergantung
pada jendela plot saat ini. Misalnya, shrinkwindow() default
menyisakan ruang untuk label sumbu dan judul plot.


Dalam contoh ini, kita hanya menggambar beberapa garis acak dalam
berbagai warna. Untuk lebih detail tentang fungsi ini, pelajari fungsi
inti dari EMT.


\>clg; // clear screen

\>window(0,0,1024,1024); // use all of the window

\>setplot(0,1,0,1); // set plot coordinates

\>hold on; // start overwrite mode

\>n=100; X=random(n,2); Y=random(n,2);  // get random points

\>colors=rgb(random(n),random(n),random(n)); // get random colors

\>loop 1 to n; color(colors[#]); plot(X[#],Y[#]); end; // plot

\>hold off; // end overwrite mode

\>insimg; // insert to notebook


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-001.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-001.png)

\>reset;


Kita perlu untuk menahan grafik, karena perintah plot() akan menghapus
jendela plot.


Untuk menghapus semua yang telah kita lakukan, dapat menggunakan
reset().


Untuk menampilkan gambar hasil plot di layar notebook, perintah
plot2d() dapat diakhiri dengan titik dua (:). Cara lain adalah
perintah plot2d() diakhiri dengan titik koma (;), kemudian menggunakan
perintah insimg() untuk menampilkan gambar hasil plot.


Untuk contoh lain, dapat kita gambarkan plot sebagai sisipan di plot
lain. Ini dilakukan dengan mendefinisikan jendela plot yang lebih
kecil. Perhatikan bahwa jendela ini tidak menyediakan ruang untuk
label sumbu di luar jendela plot. Kita harus menambahkan beberapa
margin untuk ini sesuai kebutuhan. Perhatikan bahwa kami menyimpan dan
memulihkan jendela penuh, dan menahan plot saat ini saat kita memplot
inset.


\>plot2d("x^3-x");

\>xw=200; yw=100; ww=300; hw=300;

\>ow=window();

\>window(xw,yw,xw+ww,yw+hw);

\>hold on;

\>barclear(xw-50,yw-10,ww+60,ww+60);

\>plot2d("x^4-x",grid=6):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-002.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-002.png)

\>hold off;

\>window(ow);


Plot dengan banyak angka dicapai dengan cara yang sama. Ada fungsi
figure() utilitas untuk ini.


## Aspek Plot

Plot default menggunakan jendela plot persegi. Anda dapat mengubah ini
dengan fungsi aspek(). Jangan lupa untuk mengatur ulang aspek nanti.
Anda juga dapat mengubah default ini di menu dengan "Set Aspect" ke
rasio aspek tertentu atau ke ukuran jendela grafis saat ini.


Tetapi Anda juga dapat mengubahnya untuk satu plot. Untuk ini, ukuran
area plot saat ini diubah, dan jendela diatur sehingga label memiliki
cukup ruang.


\>aspect(2); // rasio panjang dan lebar 2:1

\>plot2d(["sin(x)","cos(x)"],0,2pi):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-003.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-003.png)

\>`aspect();


    Syntax error in expression, or unfinished expression!
    Error in:
    `aspect(); ...
    ^

\>reset;


Fungsi reset() mengembalikan default plot termasuk rasio aspek.


# Plot 2D di Euler

EMT Math Toolbox memiliki plot dalam 2D, baik untuk data maupun
fungsi. EMT menggunakan fungsi plot2d. Fungsi ini dapat memplot fungsi
dan data.


Dimungkinkan untuk membuat plot di Maxima menggunakan Gnuplot atau
dengan Python menggunakan Math Plot Lib.


Euler dapat memplot plot 2D dari


* 
ekspresi

* 
fungsi, variabel, atau kurva parameter,

* 
vektor nilai x-y,

* 
awan titik di pesawat,

* 
kurva implisit dengan level atau wilayah level.

* 
Fungsi kompleks


Gaya plot mencakup berbagai gaya untuk garis dan titik, plot batang
dan plot berbayang.


# Plot Ekspresi atau Variabel

Ekspresi tunggal dalam "x" (mis. "4*x^2") atau nama fungsi (mis. "f")
menghasilkan grafik fungsi.


Berikut adalah contoh paling dasar, yang menggunakan rentang default
dan menetapkan rentang y yang tepat agar sesuai dengan plot fungsi.


Catatan: Jika Anda mengakhiri baris perintah dengan titik dua ":",
plot akan dimasukkan ke dalam jendela teks. Jika tidak, tekan TAB
untuk melihat plot jika jendela plot tertutup.


\>plot2d("x^2"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-004.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-004.png)

\>aspect(1.5); plot2d("x^3-x"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-005.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-005.png)

\>a:=5.6; plot2d("exp(-a\*x^2)/a"); insimg(30); // menampilkan gambar hasil plot setinggi 25 baris


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-006.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-006.png)

Dari beberapa contoh sebelumnya dapat dilihat bahwa aslinya gambar
plot menggunakan sumbu X dengan rentang nilai dari -2 sampai dengan 2.
Untuk mengubah rentang nilai X dan Y, Anda dapat menambahkan
nilai-nilai batas X (dan Y) di belakang ekspresi yang digambar.


Rentang plot diatur dengan parameter yang ditetapkan sebagai berikut


* 
a,b: rentang x (default -2,2)

* 
c,d: rentang y (default: skala dengan nilai)

* 
r: alternatifnya radius di sekitar pusat plot

* 
cx,cy: koordinat pusat plot (default 0,0)


\>plot2d("x^3-x",-1,2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-007.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-007.png)

\>plot2d("sin(x)",-2\*pi,2\*pi): // plot sin(x) pada interval [-2pi, 2pi]


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-008.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-008.png)

\>plot2d("cos(x)","sin(3\*x)",xmin=0,xmax=2pi):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-009.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-009.png)

Alternatif untuk titik dua adalah perintah insimg(baris), yang
menyisipkan plot yang menempati sejumlah baris teks tertentu.


Dalam opsi, plot dapat diatur untuk muncul


* 
di jendela terpisah yang dapat diubah ukurannya,

* 
di jendela buku catatan.


Lebih banyak gaya dapat dicapai dengan perintah plot tertentu.


Bagaimanapun, tekan tombol tabulator untuk melihat plot, jika
disembunyikan.


Untuk membagi jendela menjadi beberapa plot, gunakan perintah
figure(). Dalam contoh, kami memplot x^1 hingga x^4 menjadi 4 bagian
jendela. figure(0) mengatur ulang jendela default.


\>reset;

\>figure(2,2); ...  
\>   for n=1 to 4; figure(n); plot2d("x^"+n); end; ...  
\>   figure(0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-010.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-010.png)

Di plot2d(), ada gaya alternatif yang tersedia dengan grid=x. Untuk
gambaran umum, kami menunjukkan berbagai gaya kisi dalam satu gambar
(lihat di bawah untuk perintah figure()). Gaya kisi=0 tidak
disertakan. Ini menunjukkan tidak ada grid dan tidak ada bingkai.


\>figure(3,3); ...  
\>   for k=1:9; figure(k); plot2d("x^3-x",-2,1,grid=k); end; ...  
\>   figure(0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-011.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-011.png)

Jika argumen ke plot2d() adalah ekspresi yang diikuti oleh empat
angka, angka-angka ini adalah rentang x dan y untuk plot.


Atau, a, b, c, d dapat ditentukan sebagai parameter yang ditetapkan
sebagai a=... dll.


Dalam contoh berikut, kita mengubah gaya kisi, menambahkan label, dan
menggunakan label vertikal untuk sumbu y.


\>aspect(1.5); plot2d("sin(x)",0,2pi,-1.2,1.2,grid=3,xl="x",yl="sin(x)"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-012.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-012.png)

\>plot2d("sin(x)+cos(2\*x)",0,4pi):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-013.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-013.png)

Gambar yang dihasilkan dengan memasukkan plot ke dalam jendela teks
disimpan di direktori yang sama dengan buku catatan, secara default di
subdirektori bernama "gambar". Mereka juga digunakan oleh ekspor HTML.


Anda cukup menandai gambar apa saja dan menyalinnya ke clipboard
dengan Ctrl-C. Tentu saja, Anda juga dapat mengekspor grafik saat ini
dengan fungsi di menu File.


Fungsi atau ekspresi dalam plot2d dievaluasi secara adaptif. Untuk
kecepatan lebih, matikan plot adaptif dengan &lt;adaptive dan tentukan
jumlah subinterval dengan n=... Ini hanya diperlukan dalam kasus yang
jarang terjadi.


\>plot2d("sign(x)\*exp(-x^2)",-1,1,<adaptive,n=10000):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-014.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-014.png)

\>plot2d("x^x",r=1.2,cx=1,cy=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-015.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-015.png)

Perhatikan bahwa x^x tidak didefinisikan untuk x&lt;=0. Fungsi plot2d
menangkap kesalahan ini, dan mulai merencanakan segera setelah fungsi
didefinisikan. Ini berfungsi untuk semua fungsi yang mengembalikan NAN
keluar dari jangkauan definisinya.


\>plot2d("log(x)",-0.1,2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-016.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-016.png)

Parameter square=true (atau &gt;square) memilih y-range secara otomatis
sehingga hasilnya adalah jendela plot persegi. Perhatikan bahwa secara
default, Euler menggunakan ruang persegi di dalam jendela plot.


\>plot2d("x^3-x",\>square):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-017.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-017.png)

\>plot2d(''integrate("sin(x)\*exp(-x^2)",0,x)'',0,2): // plot integral


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-018.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-018.png)

Jika Anda membutuhkan lebih banyak ruang untuk label-y, panggil
shrinkwindow() dengan parameter yang lebih kecil, atau tetapkan nilai
positif untuk "lebih kecil" di plot2d().


\>plot2d("gamma(x)",1,10,yl="y-values",smaller=6,<vertical):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-019.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-019.png)

Ekspresi simbolik juga dapat digunakan, karena disimpan sebagai
ekspresi string sederhana.


\>x=linspace(0,2pi,1000); plot2d(sin(5x),cos(7x)):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-020.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-020.png)

\>a:=5.6; expr &= exp(-a\*x^2)/a; // define expression

\>plot2d(expr,-2,2): // plot from -2 to 2


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-021.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-021.png)

\>plot2d(expr,r=1,thickness=2): // plot in a square around (0,0)


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-022.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-022.png)

\>plot2d(&diff(expr,x),\>add,style="--",color=red): // add another plot


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-023.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-023.png)

\>plot2d(&diff(expr,x,2),a=-2,b=2,c=-2,d=1): // plot in rectangle


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-024.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-024.png)

\>plot2d(&diff(expr,x),a=-2,b=2,\>square): // keep plot square


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-025.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-025.png)

\>plot2d("x^2",0,1,steps=1,color=red,n=10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-026.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-026.png)

\>plot2d("x^2",\>add,steps=2,color=blue,n=10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-027.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-027.png)

# Fungsi dalam satu Parameter

Fungsi plot yang paling penting untuk plot planar adalah plot2d().
Fungsi ini diimplementasikan dalam bahasa Euler dalam file "plot.e",
yang dimuat di awal program.


Berikut adalah beberapa contoh menggunakan fungsi. Seperti biasa di
EMT, fungsi yang berfungsi untuk fungsi atau ekspresi lain, Anda dapat
meneruskan parameter tambahan (selain x) yang bukan variabel global ke
fungsi dengan parameter titik koma atau dengan koleksi panggilan.


\>function f(x,a) := x^2/a+a\*x^2-x; // define a function

\>a=0.3; plot2d("f",0,1;a): // plot with a=0.3


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-028.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-028.png)

\>plot2d("f",0,1;0.4): // plot with a=0.4


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-029.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-029.png)

\>plot2d({{"f",0.2}},0,1): // plot with a=0.2


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-030.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-030.png)

\>plot2d({{"f(x,b)",b=0.1}},0,1): // plot with 0.1


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-031.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-031.png)

\>function f(x) := x^3-x; ...  
\>   plot2d("f",r=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-032.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-032.png)

Berikut adalah ringkasan dari fungsi yang diterima


* 
ekspresi atau ekspresi simbolik dalam x

* 
fungsi atau fungsi simbolis dengan nama sebagai "f"

* 
fungsi simbolis hanya dengan nama f


Fungsi plot2d() juga menerima fungsi simbolis. Untuk fungsi simbolis,
nama saja yang berfungsi.


\>function f(x) &= diff(x^x,x)


    
                                x
                               x  (log(x) + 1)
    

\>plot2d(f,0,2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-033.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-033.png)

Tentu saja, untuk ekspresi atau ekspresi simbolik, nama variabel sudah
cukup untuk memplotnya.


\>expr &= sin(x)\*exp(-x)


    
                                  - x
                                 E    sin(x)
    

\>plot2d(expr,0,3pi):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-034.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-034.png)

\>function f(x) &= x^x;

\>plot2d(f,r=1,cx=1,cy=1,color=blue,thickness=2);

\>plot2d(&diff(f(x),x),\>add,color=red,style="-.-"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-035.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-035.png)

Untuk gaya garis ada berbagai pilihan.


* 
gaya="...". Pilih dari "-", "--", "-.", ".", ".-.", "-.-".

* 
warna: Lihat di bawah untuk warna.

* 
ketebalan: Default adalah 1.


Warna dapat dipilih sebagai salah satu warna default, atau sebagai
warna RGB.


* 
0.15: indeks warna default.

* 
konstanta warna: putih, hitam, merah, hijau, biru, cyan, zaitun,
* abu-abu muda, abu-abu, abu-abu tua, oranye, hijau muda, pirus, biru
* muda, oranye terang, kuning

* 
rgb(merah, hijau, biru): parameter adalah real dalam [0,1].


\>plot2d("exp(-x^2)",r=2,color=red,thickness=3,style="--"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-036.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-036.png)

Berikut adalah tampilan warna EMT yang telah ditentukan sebelumnya.


\>aspect(2); columnsplot(ones(1,16),lab=0:15,grid=0,color=0:15):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-037.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-037.png)

Tapi Anda bisa menggunakan warna apa saja.


\>columnsplot(ones(1,16),grid=0,color=rgb(0,0,linspace(0,1,15))):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-038.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-038.png)

# Menggambar Beberapa Kurva pada bidang koordinat yang sama

Plot lebih dari satu fungsi (multiple function) ke dalam satu jendela
dapat dilakukan dengan berbagai cara. Salah satu metode menggunakan
&gt;add untuk beberapa panggilan ke plot2d secara keseluruhan, tetapi
panggilan pertama. Kami telah menggunakan fitur ini dalam contoh di
atas.


\>aspect(); plot2d("cos(x)",r=2,grid=6); plot2d("x",style=".",\>add):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-039.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-039.png)

\>aspect(1.5); plot2d("sin(x)",0,2pi); plot2d("cos(x)",color=blue,style="--",\>add):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-040.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-040.png)

Salah satu kegunaan &gt;add adalah untuk menambahkan titik pada kurva.


\>plot2d("sin(x)",0,pi); plot2d(2,sin(2),\>points,\>add):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-041.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-041.png)

Kami menambahkan titik persimpangan dengan label (pada posisi "cl"
untuk kiri tengah), dan memasukkan hasilnya ke dalam notebook. Kami
juga menambahkan judul ke plot.


\>plot2d(["cos(x)","x"],r=1.1,cx=0.5,cy=0.5, ...  
\>     color=[black,blue],style=["-","."], ...  
\>     grid=1);

\>x0=solve("cos(x)-x",1);  ...  
\>     plot2d(x0,x0,\>points,\>add,title="Intersection Demo");  ...  
\>     label("cos(x) = x",x0,x0,pos="cl",offset=20):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-042.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-042.png)

Dalam demo berikut, kami memplot fungsi sinc(x)=sin(x)/x dan ekspansi
Taylor ke-8 dan ke-16. Kami menghitung ekspansi ini menggunakan Maxima
melalui ekspresi simbolis.


Plot ini dilakukan dalam perintah multi-baris berikut dengan tiga
panggilan ke plot2d(). Yang kedua dan yang ketiga memiliki set flag
&gt;add, yang membuat plot menggunakan rentang sebelumnya.


Kami menambahkan kotak label yang menjelaskan fungsi.


\>$taylor(sin(x)/x,x,0,4)


$$\frac{x^4}{120}-\frac{x^2}{6}+1$$\>plot2d("sinc(x)",0,4pi,color=green,thickness=2); ...  
\>     plot2d(&taylor(sin(x)/x,x,0,8),\>add,color=blue,style="--"); ...  
\>     plot2d(&taylor(sin(x)/x,x,0,16),\>add,color=red,style="-.-"); ...  
\>     labelbox(["sinc","T8","T16"],styles=["-","--","-.-"], ...  
\>       colors=[black,blue,red]):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-044.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-044.png)

Dalam contoh berikut, kami menghasilkan Bernstein-Polinomial.


\>plot2d("(1-x)^10",0,1); // plot first function

\>for i=1 to 10; plot2d("bin(10,i)\*x^i\*(1-x)^(10-i)",\>add); end;

\>insimg;


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-045.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-045.png)

Metode kedua menggunakan pasangan matriks nilai-x dan matriks nilai-y
yang berukuran sama.


Kami menghasilkan matriks nilai dengan satu Polinomial Bernstein di
setiap baris. Untuk ini, kita cukup menggunakan vektor kolom i. Lihat
pengantar tentang bahasa matriks untuk mempelajari lebih detail.


\>x=linspace(0,1,500);

\>n=10; k=(0:n)'; // n is row vector, k is column vector

\>y=bin(n,k)\*x^k\*(1-x)^(n-k); // y is a matrix then

\>plot2d(x,y):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-046.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-046.png)

Perhatikan bahwa parameter warna dapat berupa vektor. Kemudian setiap
warna digunakan untuk setiap baris matriks.


\>x=linspace(0,1,200); y=x^(1:10)'; plot2d(x,y,color=1:10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-047.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-047.png)

Metode lain adalah menggunakan vektor ekspresi (string). Anda kemudian
dapat menggunakan larik warna, larik gaya, dan larik ketebalan dengan
panjang yang sama.


\>plot2d(["sin(x)","cos(x)"],0,2pi,color=4:5): 


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-048.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-048.png)

\>plot2d(["sin(x)","cos(x)"],0,2pi): // plot vector of expressions


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-049.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-049.png)

Kita bisa mendapatkan vektor seperti itu dari Maxima menggunakan
makelist() dan mxm2str().


\>v &= makelist(binomial(10,i)\*x^i\*(1-x)^(10-i),i,0,10) // make list


    
                   10            9              8  2             7  3
           [(1 - x)  , 10 (1 - x)  x, 45 (1 - x)  x , 120 (1 - x)  x , 
               6  4             5  5             4  6             3  7
    210 (1 - x)  x , 252 (1 - x)  x , 210 (1 - x)  x , 120 (1 - x)  x , 
              2  8              9   10
    45 (1 - x)  x , 10 (1 - x) x , x  ]
    

\>mxm2str(v) // get a vector of strings from the symbolic vector


    (1-x)^10
    10*(1-x)^9*x
    45*(1-x)^8*x^2
    120*(1-x)^7*x^3
    210*(1-x)^6*x^4
    252*(1-x)^5*x^5
    210*(1-x)^4*x^6
    120*(1-x)^3*x^7
    45*(1-x)^2*x^8
    10*(1-x)*x^9
    x^10

\>plot2d(mxm2str(v),0,1): // plot functions


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-050.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-050.png)

Alternatif lain adalah dengan menggunakan bahasa matriks Euler.


Jika ekspresi menghasilkan matriks fungsi, dengan satu fungsi di
setiap baris, semua fungsi ini akan diplot ke dalam satu plot.


Untuk ini, gunakan vektor parameter dalam bentuk vektor kolom. Jika
array warna ditambahkan, itu akan digunakan untuk setiap baris plot.


\>n=(1:10)'; plot2d("x^n",0,1,color=1:10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-051.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-051.png)

Ekspresi dan fungsi satu baris dapat melihat variabel global.


Jika Anda tidak dapat menggunakan variabel global, Anda perlu
menggunakan fungsi dengan parameter tambahan, dan meneruskan parameter
ini sebagai parameter titik koma.


Berhati-hatilah, untuk meletakkan semua parameter yang ditetapkan di
akhir perintah plot2d. Dalam contoh kita meneruskan a=5 ke fungsi f,
yang kita plot dari -10 hingga 10.


\>function f(x,a) := 1/a\*exp(-x^2/a); ...  
\>   plot2d("f",-10,10;5,thickness=2,title="a=5"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-052.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-052.png)

Atau, gunakan koleksi dengan nama fungsi dan semua parameter tambahan.
Daftar khusus ini disebut koleksi panggilan, dan itu adalah cara yang
lebih disukai untuk meneruskan argumen ke fungsi yang dengan
sendirinya diteruskan sebagai argumen ke fungsi lain.


Dalam contoh berikut, kami menggunakan loop untuk memplot beberapa
fungsi (lihat tutorial tentang pemrograman untuk loop).


\>plot2d({{"f",1}},-10,10); ...  
\>   for a=2:10; plot2d({{"f",a}},\>add); end:


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-053.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-053.png)

Kami dapat mencapai hasil yang sama dengan cara berikut menggunakan
bahasa matriks EMT. Setiap baris matriks f(x,a) adalah satu fungsi.
Selain itu, kita dapat mengatur warna untuk setiap baris matriks. Klik
dua kali pada fungsi getspectral() untuk penjelasannya.


\>x=-10:0.01:10; a=(1:10)'; plot2d(x,f(x,a),color=getspectral(a/10)):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-054.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-054.png)

## Label Teks

Dekorasi sederhana bisa


* 
judul dengan judul="..."

* 
x- dan y-label dengan xl="...", yl="..."

* 
label teks lain dengan label("...",x,y)


Perintah label akan memplot ke dalam plot saat ini pada koordinat plot
(x,y). Itu bisa mengambil argumen posisi.


\>plot2d("x^3-x",-1,2,title="y=x^3-x",yl="y",xl="x"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-055.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-055.png)

\>expr := "log(x)/x"; ...  
\>     plot2d(expr,0.5,5,title="y="+expr,xl="x",yl="y"); ...  
\>     label("(1,0)",1,0); label("Max",E,expr(E),pos="lc"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-056.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-056.png)

Ada juga fungsi labelbox(), yang dapat menampilkan fungsi dan teks.
Dibutuhkan vektor string dan warna, satu item untuk setiap fungsi.


\>function f(x) &= x^2\*exp(-x^2);  ...  
\>   plot2d(&f(x),a=-3,b=3,c=-1,d=1);  ...  
\>   plot2d(&diff(f(x),x),\>add,color=blue,style="--"); ...  
\>   labelbox(["function","derivative"],styles=["-","--"], ...  
\>      colors=[black,blue],w=0.4):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-057.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-057.png)

Kotak ditambatkan di kanan atas secara default, tetapi &gt; kiri
menambatkannya di kiri atas. Anda dapat memindahkannya ke tempat yang
Anda suka. Posisi jangkar adalah sudut kanan atas kotak, dan angkanya
adalah pecahan dari ukuran jendela grafik. Lebarnya otomatis.


Untuk plot titik, kotak label juga berfungsi. Tambahkan parameter
&gt;points, atau vektor flag, satu untuk setiap label.


Dalam contoh berikut, hanya ada satu fungsi. Jadi kita bisa
menggunakan string sebagai pengganti vektor string. Kami mengatur
warna teks menjadi hitam untuk contoh ini.


\>n=10; plot2d(0:n,bin(n,0:n),\>addpoints); ...  
\>   labelbox("Binomials",styles="[]",\>points,x=0.1,y=0.1, ...  
\>   tcolor=black,\>left):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-058.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-058.png)

Gaya plot ini juga tersedia di statplot(). Seperti di plot2d() warna
dapat diatur untuk setiap baris plot. Ada lebih banyak plot khusus
untuk keperluan statistik (lihat tutorial tentang statistik).


\>statplot(1:10,random(2,10),color=[red,blue]):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-059.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-059.png)

Fitur serupa adalah fungsi textbox().


Lebar secara default adalah lebar maksimal dari baris teks. Tapi itu
bisa diatur oleh pengguna juga.


\>function f(x) &= exp(-x)\*sin(2\*pi\*x); ...  
\>   plot2d("f(x)",0,2pi); ...  
\>   textbox(latex("\\text{Example of a damped oscillation}\\ f(x)=e^{-x}sin(2\\pi x)"),w=0.85):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-060.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-060.png)

Label teks, judul, kotak label, dan teks lainnya dapat berisi string
Unicode (lihat sintaks EMT untuk mengetahui lebih lanjut tentang
string Unicode).


\>plot2d("x^3-x",title=u"x &rarr; x&sup3; - x"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-061.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-061.png)

Label pada sumbu x dan y bisa vertikal, begitu juga sumbunya.


\>plot2d("sinc(x)",0,2pi,xl="x",yl=u"x &rarr; sinc(x)",\>vertical):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-062.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-062.png)

## LaTeX

Anda juga dapat memplot rumus LaTeX jika Anda telah menginstal sistem
LaTeX. Saya merekomendasikan MiKTeX. Jalur ke biner "lateks" dan
"dvipng" harus berada di jalur sistem, atau Anda harus mengatur LaTeX
di menu opsi.


Perhatikan, bahwa penguraian LaTeX lambat. Jika Anda ingin menggunakan
LaTeX dalam plot animasi, Anda harus memanggil latex() sebelum loop
sekali dan menggunakan hasilnya (gambar dalam matriks RGB).


Dalam plot berikut, kami menggunakan LaTeX untuk label x dan y, label,
kotak label, dan judul plot.


\>plot2d("exp(-x)\*sin(x)/x",a=0,b=2pi,c=0,d=1,grid=6,color=blue, ...  
\>     title=latex("\\text{Function $\\Phi$}"), ...  
\>     xl=latex("\\phi"),yl=latex("\\Phi(\\phi)")); ...  
\>   textbox( ...  
\>     latex("\\Phi(\\phi) = e^{-\\phi} \\frac{\\sin(\\phi)}{\\phi}"),x=0.8,y=0.5); ...  
\>   label(latex("\\Phi",color=blue),1,0.4):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-063.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-063.png)

Seringkali, kami menginginkan spasi dan label teks non-konformal pada
sumbu x. Kita dapat menggunakan xaxis() dan yaxis() seperti yang akan
kita tunjukkan nanti.


Cara termudah adalah dengan membuat plot kosong dengan bingkai
menggunakan grid=4, lalu menambahkan grid dengan ygrid() dan xgrid().
Dalam contoh berikut, kami menggunakan tiga string LaTeX untuk label
pada sumbu x dengan xtick().


\>plot2d("sinc(x)",0,2pi,grid=4,<ticks); ...  
\>   ygrid(-2:0.5:2,grid=6); ...  
\>   xgrid([0:2]\*pi,<ticks,grid=6);  ...  
\>   xtick([0,pi,2pi],["0","\\pi","2\\pi"],\>latex):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-064.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-064.png)

Tentu saja, fungsi juga dapat digunakan.


\>function map f(x) ...


    if x>0 then return x^4
    else return x^2
    endif
    endfunction
</pre>
Parameter "peta" membantu menggunakan fungsi untuk vektor. Untuk


plot, itu tidak perlu. Tetapi untuk mendemonstrasikan vektorisasi itu


berguna, kami menambahkan beberapa poin kunci ke plot di x=-1, x=0 dan
x=1.


Pada plot berikut, kami juga memasukkan beberapa kode LaTeX. Kami
menggunakannya untuk


dua label dan kotak teks. Tentu saja, Anda hanya akan dapat
menggunakan


LaTeX jika Anda telah menginstal LaTeX dengan benar.


\>plot2d("f",-1,1,xl="x",yl="f(x)",grid=6);  ...  
\>   plot2d([-1,0,1],f([-1,0,1]),\>points,\>add); ...  
\>   label(latex("x^3"),0.72,f(0.72)); ...  
\>   label(latex("x^2"),-0.52,f(-0.52),pos="ll"); ...  
\>   textbox( ...  
\>     latex("f(x)=\\begin{cases} x^3 & x\>0 \\\\ x^2 & x \\le 0\\end{cases}"), ...  
\>     x=0.7,y=0.2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-065.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-065.png)

## Interaksi pengguna

Saat memplot fungsi atau ekspresi, parameter &gt;user memungkinkan
pengguna untuk memperbesar dan menggeser plot dengan tombol kursor
atau mouse. Pengguna dapat


* 
perbesar dengan + atau -

* 
pindahkan plot dengan tombol kursor

* 
pilih jendela plot dengan mouse

* 
atur ulang tampilan dengan spasi

* 
keluar dengan kembali


Tombol spasi akan mengatur ulang plot ke jendela plot asli.


Saat memplot data, flag &gt;user hanya akan menunggu penekanan tombol.


\>plot2d({{"x^3-a\*x",a=1}},\>user,title="Press any key!"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-066.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-066.png)

\>plot2d("exp(x)\*sin(x)",user=true, ...  
\>     title="+/- or cursor keys (return to exit)"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-067.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-067.png)

Berikut ini menunjukkan cara interaksi pengguna tingkat lanjut (lihat
tutorial tentang pemrograman untuk detailnya).


Fungsi bawaan mousedrag() menunggu event mouse atau keyboard. Ini
melaporkan mouse ke bawah, mouse dipindahkan atau mouse ke atas, dan
penekanan tombol. Fungsi dragpoints() memanfaatkan ini, dan
memungkinkan pengguna menyeret titik mana pun dalam plot.


Kita membutuhkan fungsi plot terlebih dahulu. Sebagai contoh, kita
interpolasi dalam 5 titik dengan polinomial. Fungsi harus diplot ke
area plot tetap.


\>function plotf(xp,yp,select) ...


      d=interp(xp,yp);
      plot2d("interpval(xp,d,x)";d,xp,r=2);
      plot2d(xp,yp,>points,>add);
      if select>0 then
        plot2d(xp[select],yp[select],color=red,>points,>add);
      endif;
      title("Drag one point, or press space or return!");
    endfunction
</pre>
Perhatikan parameter titik koma di plot2d (d dan xp), yang diteruskan
ke evaluasi fungsi interp(). Tanpa ini, kita harus menulis fungsi
plotinterp() terlebih dahulu, mengakses nilai secara global.


Sekarang kita menghasilkan beberapa nilai acak, dan membiarkan
pengguna menyeret poin.


\>t=-1:0.5:1; dragpoints("plotf",t,random(size(t))-0.5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-068.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-068.png)

Ada juga fungsi, yang memplot fungsi lain tergantung pada vektor
parameter, dan memungkinkan pengguna menyesuaikan parameter ini.


Pertama kita membutuhkan fungsi plot.


\>function plotf([a,b]) := plot2d("exp(a\*x)\*cos(2pi\*b\*x)",0,2pi;a,b);


Kemudian kita membutuhkan nama untuk parameter, nilai awal dan matriks
rentang nx2, opsional baris judul.


Ada slider interaktif, yang dapat mengatur nilai oleh pengguna. Fungsi
dragvalues() menyediakan ini.


\>dragvalues("plotf",["a","b"],[-1,2],[[-2,2];[1,10]], ...  
\>     heading="Drag these values:",hcolor=black):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-069.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-069.png)

Dimungkinkan untuk membatasi nilai yang diseret ke bilangan bulat.
Sebagai contoh, kita menulis fungsi plot, yang memplot polinomial
Taylor derajat n ke fungsi kosinus.


\>function plotf(n) ...


    plot2d("cos(x)",0,2pi,>square,grid=6);
    plot2d(&"taylor(cos(x),x,0,@n)",color=blue,>add);
    textbox("Taylor polynomial of degree "+n,0.1,0.02,style="t",>left);
    endfunction
</pre>
Sekarang kami mengizinkan derajat n bervariasi dari 0 hingga 20 dalam
20 pemberhentian. Hasil dragvalues() digunakan untuk memplot sketsa
dengan n ini, dan untuk memasukkan plot ke dalam buku catatan.


\>nd=dragvalues("plotf","degree",2,[0,20],20,y=0.8, ...  
\>      heading="Drag the value:"); ...  
\>   plotf(nd):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-070.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-070.png)

Berikut ini adalah demonstrasi sederhana dari fungsi tersebut.
Pengguna dapat menggambar di atas jendela plot, meninggalkan jejak
poin.


\>function dragtest ...


      plot2d(none,r=1,title="Drag with the mouse, or press any key!");
      start=0;
      repeat
        {flag,m,time}=mousedrag();
        if flag==0 then return; endif;
        if flag==2 then
          hold on; mark(m[1],m[2]); hold off;
        endif;
      end
    endfunction
</pre>
\>dragtest // lihat hasilnya dan cobalah lakukan!


## Gaya Plot 2D

Secara default, EMT menghitung tick sumbu otomatis dan menambahkan
label ke setiap tick. Ini dapat diubah dengan parameter grid. Gaya
default sumbu dan label dapat dimodifikasi. Selain itu, label dan
judul dapat ditambahkan secara manual. Untuk mengatur ulang ke gaya
default, gunakan reset().


\>aspect();

\>figure(3,4); ...  
\>    figure(1); plot2d("x^3-x",grid=0); ... // no grid, frame or axis

\> figure(2); plot2d("x^3-x",grid=1); ... // x-y-axis

\> figure(3); plot2d("x^3-x",grid=2); ... // default ticks

\> figure(4); plot2d("x^3-x",grid=3); ... // x-y- axis with labels inside

\> figure(5); plot2d("x^3-x",grid=4); ... // no ticks, only labels

\> figure(6); plot2d("x^3-x",grid=5); ... // default, but no margin

\> figure(7); plot2d("x^3-x",grid=6); ... // axes only

\> figure(8); plot2d("x^3-x",grid=7); ... // axes only, ticks at axis

\> figure(9); plot2d("x^3-x",grid=8); ... // axes only, finer ticks at axis

\> figure(10); plot2d("x^3-x",grid=9); ... // default, small ticks inside

\> figure(11); plot2d("x^3-x",grid=10); ...// no ticks, axes only

\> figure(0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-071.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-071.png)

Parameter &lt;frame mematikan frame, dan framecolor=blue mengatur frame
ke warna biru.


Jika Anda ingin centang sendiri, Anda dapat menggunakan style=0, dan
menambahkan semuanya nanti.


\>aspect(1.5); 

\>plot2d("x^3-x",grid=0); // plot

\>frame; xgrid([-1,0,1]); ygrid(0): // add frame and grid


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-072.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-072.png)

Untuk judul plot dan label sumbu, lihat contoh berikut.


\>plot2d("exp(x)",-1,1);

\>textcolor(black); // set the text color to black

\>title(latex("y=e^x")); // title above the plot

\>xlabel(latex("x")); // "x" for x-axis

\>ylabel(latex("y"),\>vertical); // vertical "y" for y-axis

\>label(latex("(0,1)"),0,1,color=blue): // label a point


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-073.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-073.png)

Sumbu dapat digambar secara terpisah dengan xaxis() dan yaxis().


\>plot2d("x^3-x",<grid,<frame);

\>xaxis(0,xx=-2:1,style="-\>"); yaxis(0,yy=-5:5,style="-\>"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-074.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-074.png)

Teks pada plot dapat diatur dengan label(). Dalam contoh berikut, "lc"
berarti tengah bawah. Ini mengatur posisi label relatif terhadap
koordinat plot.


\>function f(x) &= x^3-x


    
                                     3
                                    x  - x
    

\>plot2d(f,-1,1,\>square);

\>x0=fmin(f,0,1); // compute point of minimum

\>label("Rel. Min.",x0,f(x0),pos="lc"): // add a label there


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-075.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-075.png)

Ada juga kotak teks.


\>plot2d(&f(x),-1,1,-2,2); // function

\>plot2d(&diff(f(x),x),\>add,style="--",color=red); // derivative

\>labelbox(["f","f'"],["-","--"],[black,red]): // label box


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-076.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-076.png)

\>plot2d(["exp(x)","1+x"],color=[black,blue],style=["-","-.-"]):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-077.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-077.png)

\>gridstyle("-\>",color=gray,textcolor=gray,framecolor=gray);  ...  
\>    plot2d("x^3-x",grid=1);   ...  
\>    settitle("y=x^3-x",color=black); ...  
\>    label("x",2,0,pos="bc",color=gray);  ...  
\>    label("y",0,6,pos="cl",color=gray); ...  
\>    reset():


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-078.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-078.png)

Untuk kontrol lebih, sumbu x dan sumbu y dapat dilakukan secara
manual.


Perintah fullwindow() memperluas jendela plot karena kita tidak lagi
membutuhkan tempat untuk label di luar jendela plot. Gunakan
shrinkwindow() atau reset() untuk mengatur ulang ke default.


\>fullwindow; ...  
\>    gridstyle(color=darkgray,textcolor=darkgray); ...  
\>    plot2d(["2^x","1","2^(-x)"],a=-2,b=2,c=0,d=4,<grid,color=4:6,<frame); ...  
\>    xaxis(0,-2:1,style="-\>"); xaxis(0,2,"x",<axis); ...  
\>    yaxis(0,4,"y",style="-\>"); ...  
\>    yaxis(-2,1:4,\>left); ...  
\>    yaxis(2,2^(-2:2),style=".",<left); ...  
\>    labelbox(["2^x","1","2^-x"],colors=4:6,x=0.8,y=0.2); ...  
\>    reset:


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-079.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-079.png)

Berikut adalah contoh lain, di mana string Unicode digunakan dan sumbu
di luar area plot.


\>aspect(1.5); 

\>plot2d(["sin(x)","cos(x)"],0,2pi,color=[red,green],<grid,<frame); ...  
\>    xaxis(-1.1,(0:2)\*pi,xt=["0",u"&pi;",u"2&pi;"],style="-",\>ticks,\>zero);  ...  
\>    xgrid((0:0.5:2)\*pi,<ticks); ...  
\>    yaxis(-0.1\*pi,-1:0.2:1,style="-",\>zero,\>grid); ...  
\>    labelbox(["sin","cos"],colors=[red,green],x=0.5,y=0.2,\>left); ...  
\>    xlabel(u"&phi;"); ylabel(u"f(&phi;)"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-080.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-080.png)

# Merencanakan Data 2D

Jika x dan y adalah vektor data, data ini akan digunakan sebagai
koordinat x dan y dari suatu kurva. Dalam hal ini, a, b, c, dan d,
atau radius r dapat ditentukan, atau jendela plot akan menyesuaikan
secara otomatis dengan data. Atau, &gt;persegi dapat diatur untuk menjaga
rasio aspek persegi.


Memplot ekspresi hanyalah singkatan untuk plot data. Untuk plot data,
Anda memerlukan satu atau beberapa baris nilai x, dan satu atau
beberapa baris nilai y. Dari rentang dan nilai-x, fungsi plot2d akan
menghitung data yang akan diplot, secara default dengan evaluasi
fungsi yang adaptif. Untuk plot titik gunakan "&gt;titik", untuk garis
campuran dan titik gunakan "&gt;tambahan".


Tapi Anda bisa memasukkan data secara langsung.


* 
Gunakan vektor baris untuk x dan y untuk satu fungsi.

* 
Matriks untuk x dan y diplot baris demi baris.


Berikut adalah contoh dengan satu baris untuk x dan y.


\>x=-10:0.1:10; y=exp(-x^2)\*x; plot2d(x,y):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-081.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-081.png)

Data juga dapat diplot sebagai titik. Gunakan poin=true untuk ini.
Plotnya bekerja seperti poligon, tetapi hanya menggambar
sudut-sudutnya.


* 
style="...": Pilih dari "[]", "&lt;&gt;", "o", ".", "..", "+", "*", "[]#",
* "&lt; &gt;#", "o#", "..#", "#", "|".


Untuk memplot set poin gunakan &gt;points. Jika warna adalah vektor
warna, setiap titik


mendapat warna yang berbeda. Untuk matriks koordinat dan vektor kolom,
warna berlaku untuk baris matriks.


Parameter &gt;addpoints menambahkan titik ke segmen garis untuk plot
data.


\>xdata=[1,1.5,2.5,3,4]; ydata=[3,3.1,2.8,2.9,2.7]; // data

\>plot2d(xdata,ydata,a=0.5,b=4.5,c=2.5,d=3.5,style="."); // lines

\>plot2d(xdata,ydata,\>points,\>add,style="o"): // add points


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-082.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-082.png)

\>p=polyfit(xdata,ydata,1); // get regression line

\>plot2d("polyval(p,x)",\>add,color=red): // add plot of line


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-083.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-083.png)

# Menggambar Daerah Yang Dibatasi Kurva

Plot data benar-benar poligon. Kita juga dapat memplot kurva atau
kurva terisi.


* 
terisi=benar mengisi plot.

* 
style="...": Pilih dari "#", "/", "\", "\/".

* 
fillcolor: Lihat di atas untuk warna yang tersedia.


Warna isian ditentukan oleh argumen "fillcolor", dan pada &lt;outline
opsional mencegah menggambar batas untuk semua gaya kecuali yang
default.


\>t=linspace(0,2pi,1000); // parameter for curve

\>x=sin(t)\*exp(t/pi); y=cos(t)\*exp(t/pi); // x(t) and y(t)

\>figure(1,2); aspect(16/9)

\>figure(1); plot2d(x,y,r=10); // plot curve

\>figure(2); plot2d(x,y,r=10,\>filled,style="/",fillcolor=red); // fill curve

\>figure(0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-084.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-084.png)

Dalam contoh berikut kami memplot elips terisi dan dua segi enam
terisi menggunakan kurva tertutup dengan 6 titik dengan gaya isian
berbeda.


\>x=linspace(0,2pi,1000); plot2d(sin(x),cos(x)\*0.5,r=1,\>filled,style="/"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-085.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-085.png)

\>t=linspace(0,2pi,6); ...  
\>   plot2d(cos(t),sin(t),\>filled,style="/",fillcolor=red,r=1.2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-086.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-086.png)

\>t=linspace(0,2pi,6); plot2d(cos(t),sin(t),\>filled,style="#"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-087.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-087.png)

Contoh lainnya adalah segi empat, yang kita buat dengan 7 titik pada
lingkaran satuan.


\>t=linspace(0,2pi,7);  ...  
\>    plot2d(cos(t),sin(t),r=1,\>filled,style="/",fillcolor=red):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-088.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-088.png)

Berikut ini adalah himpunan nilai maksimal dari empat kondisi linier
yang kurang dari atau sama dengan 3. Ini adalah A[k].v&lt;=3 untuk semua
baris A. Untuk mendapatkan sudut yang bagus, kita menggunakan n yang
relatif besar.


\>A=[2,1;1,2;-1,0;0,-1];

\>function f(x,y) := max([x,y].A');

\>plot2d("f",r=4,level=[0;3],color=green,n=111):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-089.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-089.png)

Poin utama dari bahasa matriks adalah memungkinkan untuk menghasilkan
tabel fungsi dengan mudah.


\>t=linspace(0,2pi,1000); x=cos(3\*t); y=sin(4\*t);


Kami sekarang memiliki vektor x dan y nilai. plot2d() dapat memplot
nilai-nilai ini


sebagai kurva yang menghubungkan titik-titik. Plotnya bisa diisi. Pada
kasus ini


ini menghasilkan hasil yang bagus karena aturan lilitan, yang
digunakan untuk


isi.


\>plot2d(x,y,<grid,<frame,\>filled):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-090.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-090.png)

Sebuah vektor interval diplot terhadap nilai x sebagai daerah terisi


antara nilai interval bawah dan atas.


Hal ini dapat berguna untuk memplot kesalahan perhitungan. Tapi itu
bisa


juga digunakan untuk memplot kesalahan statistik.


\>t=0:0.1:1; ...  
\>    plot2d(t,interval(t-random(size(t)),t+random(size(t))),style="|");  ...  
\>    plot2d(t,t,add=true):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-091.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-091.png)

Jika x adalah vektor yang diurutkan, dan y adalah vektor interval,
maka plot2d akan memplot rentang interval yang terisi dalam bidang.
Gaya isian sama dengan gaya poligon.


\>t=-1:0.01:1; x=~t-0.01,t+0.01~; y=x^3-x;

\>plot2d(t,y):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-092.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-092.png)

Dimungkinkan untuk mengisi wilayah nilai untuk fungsi tertentu. Untuk


ini, level harus berupa matriks 2xn. Baris pertama adalah batas bawah


dan baris kedua berisi batas atas.


\>expr := "2\*x^2+x\*y+3\*y^4+y"; // define an expression f(x,y)

\>plot2d(expr,level=[0;1],style="-",color=blue): // 0 <= f(x,y) <= 1


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-093.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-093.png)

Kami juga dapat mengisi rentang nilai seperti


\>plot2d("(x^2+y^2)^2-x^2+y^2",r=1.2,level=[-1;0],style="/"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-094.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-094.png)

\>plot2d("cos(x)","sin(x)^3",xmin=0,xmax=2pi,\>filled,style="/"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-095.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-095.png)

# Grafik Fungsi Parametrik

Nilai-x tidak perlu diurutkan. (x,y) hanya menggambarkan kurva. Jika x
diurutkan, kurva tersebut merupakan grafik fungsi.


Dalam contoh berikut, kami memplot spiral


Kita perlu menggunakan banyak titik untuk tampilan yang halus atau
fungsi adaptif() untuk mengevaluasi ekspresi (lihat fungsi adaptif()
untuk lebih jelasnya).


\>t=linspace(0,1,1000); ...  
\>   plot2d(t\*cos(2\*pi\*t),t\*sin(2\*pi\*t),r=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-096.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-096.png)

Atau, dimungkinkan untuk menggunakan dua ekspresi untuk kurva. Berikut
ini plot kurva yang sama seperti di atas.


\>plot2d("x\*cos(2\*pi\*x)","x\*sin(2\*pi\*x)",xmin=0,xmax=1,r=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-097.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-097.png)

\>t=linspace(0,1,1000); r=exp(-t); x=r\*cos(2pi\*t); y=r\*sin(2pi\*t);

\>plot2d(x,y,r=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-098.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-098.png)

Dalam contoh berikutnya, kami memplot kurva


dengan


\>t=linspace(0,2pi,1000); r=1+sin(3\*t)/2; x=r\*cos(t); y=r\*sin(t); ...  
\>   plot2d(x,y,\>filled,fillcolor=red,style="/",r=1.5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-099.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-099.png)

# Menggambar Grafik Bilangan Kompleks

Array bilangan kompleks juga dapat diplot. Kemudian titik-titik grid
akan terhubung. Jika sejumlah garis kisi ditentukan (atau vektor garis
kisi 1x2) dalam argumen cgrid, hanya garis kisi tersebut yang
terlihat.


Matriks bilangan kompleks akan secara otomatis diplot sebagai kisi di
bidang kompleks.


Dalam contoh berikut, kami memplot gambar lingkaran satuan di bawah
fungsi eksponensial. Parameter cgrid menyembunyikan beberapa kurva
grid.


\>aspect(); r=linspace(0,1,50); a=linspace(0,2pi,80)'; z=r\*exp(I\*a);...  
\>   plot2d(z,a=-1.25,b=1.25,c=-1.25,d=1.25,cgrid=10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-100.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-100.png)

\>aspect(1.25); r=linspace(0,1,50); a=linspace(0,2pi,200)'; z=r\*exp(I\*a);

\>plot2d(exp(z),cgrid=[40,10]):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-101.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-101.png)

\>r=linspace(0,1,10); a=linspace(0,2pi,40)'; z=r\*exp(I\*a);

\>plot2d(exp(z),\>points,\>add):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-102.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-102.png)

Sebuah vektor bilangan kompleks secara otomatis diplot sebagai kurva
pada bidang kompleks dengan bagian real dan bagian imajiner.


Dalam contoh, kami memplot lingkaran satuan dengan


\>t=linspace(0,2pi,1000); ...  
\>   plot2d(exp(I\*t)+exp(4\*I\*t),r=2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-103.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-103.png)

# Plot Statistik

Ada banyak fungsi yang dikhususkan pada plot statistik. Salah satu
plot yang sering digunakan adalah plot kolom.


Jumlah kumulatif dari nilai terdistribusi 0-1-normal menghasilkan
jalan acak.


\>plot2d(cumsum(randnormal(1,1000))):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-104.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-104.png)

Menggunakan dua baris menunjukkan jalan dalam dua dimensi.


\>X=cumsum(randnormal(2,1000)); plot2d(X[1],X[2]):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-105.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-105.png)

\>columnsplot(cumsum(random(10)),style="/",color=blue):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-106.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-106.png)

Itu juga dapat menampilkan string sebagai label.


\>months=["Jan","Feb","Mar","Apr","May","Jun", ...  
\>     "Jul","Aug","Sep","Oct","Nov","Dec"];

\>values=[10,12,12,18,22,28,30,26,22,18,12,8];

\>columnsplot(values,lab=months,color=red,style="-");

\>title("Temperature"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-107.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-107.png)

\>k=0:10;

\>plot2d(k,bin(10,k),\>bar):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-108.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-108.png)

\>plot2d(k,bin(10,k)); plot2d(k,bin(10,k),\>points,\>add):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-109.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-109.png)

\>plot2d(normal(1000),normal(1000),\>points,grid=6,style=".."):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-110.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-110.png)

\>plot2d(normal(1,1000),\>distribution,style="O"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-111.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-111.png)

\>plot2d("qnormal",0,5;2.5,0.5,\>filled):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-112.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-112.png)

Untuk memplot distribusi statistik eksperimental, Anda dapat
menggunakan distribution=n dengan plot2d.


\>w=randexponential(1,1000); // exponential distribution

\>plot2d(w,\>distribution): // or distribution=n with n intervals


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-113.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-113.png)

Atau Anda dapat menghitung distribusi dari data dan memplot hasilnya
dengan &gt;bar di plot3d, atau dengan plot kolom.


\>w=normal(1000); // 0-1-normal distribution

\>{x,y}=histo(w,10,v=[-6,-4,-2,-1,0,1,2,4,6]); // interval bounds v

\>plot2d(x,y,\>bar):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-114.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-114.png)

Fungsi statplot() menyetel gaya dengan string sederhana.


\>statplot(1:10,cumsum(random(10)),"b"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-115.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-115.png)

\>n=10; i=0:n; ...  
\>   plot2d(i,bin(n,i)/2^n,a=0,b=10,c=0,d=0.3); ...  
\>   plot2d(i,bin(n,i)/2^n,points=true,style="ow",add=true,color=blue):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-116.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-116.png)

Selain itu, data dapat diplot sebagai batang. Dalam hal ini, x harus
diurutkan dan satu elemen lebih panjang dari y. Bilah akan memanjang
dari x[i] ke x[i+1] dengan nilai y[i]. Jika x memiliki ukuran yang
sama dengan y, maka akan diperpanjang satu elemen dengan spasi
terakhir.


Gaya isian dapat digunakan seperti di atas.


\>n=10; k=bin(n,0:n); ...  
\>   plot2d(-0.5:n+0.5,k,bar=true,fillcolor=lightgray):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-117.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-117.png)

Data untuk plot batang (bar=1) dan histogram (histogram=1) dapat
dinyatakan secara eksplisit dalam xv dan yv, atau dapat dihitung dari
distribusi empiris dalam xv dengan &gt;distribusi (atau distribusi=n).
Histogram nilai xv akan dihitung secara otomatis dengan &gt;histogram.
Jika &gt;genap ditentukan, nilai xv akan dihitung dalam interval bilangan
bulat.


\>plot2d(normal(10000),distribution=50):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-118.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-118.png)

\>k=0:10; m=bin(10,k); x=(0:11)-0.5; plot2d(x,m,\>bar):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-119.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-119.png)

\>columnsplot(m,k):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-120.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-120.png)

\>plot2d(random(600)\*6,histogram=6):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-121.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-121.png)

Untuk distribusi, ada parameter distribusi=n, yang menghitung nilai
secara otomatis dan mencetak distribusi relatif dengan n sub-interval.


\>plot2d(normal(1,1000),distribution=10,style="\\/"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-122.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-122.png)

Dengan parameter even=true, ini akan menggunakan interval integer.


\>plot2d(intrandom(1,1000,10),distribution=10,even=true):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-123.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-123.png)

Perhatikan bahwa ada banyak plot statistik, yang mungkin berguna.
Silahkan lihat tutorial tentang statistik.


\>columnsplot(getmultiplicities(1:6,intrandom(1,6000,6))):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-124.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-124.png)

\>plot2d(normal(1,1000),\>distribution); ...  
\>     plot2d("qnormal(x)",color=red,thickness=2,\>add):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-125.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-125.png)

Ada juga banyak plot khusus untuk statistik. Sebuah boxplot
menunjukkan kuartil dari distribusi ini dan banyak dari


outlier. Menurut definisi, outlier dalam boxplot adalah data yang
melebihi 1,5 kali kisaran 50% tengah plot.


\>M=normal(5,1000); boxplot(quartiles(M)):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-126.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-126.png)

# Fungsi Implisit

Plot implisit menunjukkan garis level yang menyelesaikan f(x,y)=level,
di mana "level" dapat berupa nilai tunggal atau vektor nilai. Jika
level="auto", akan ada garis level nc, yang akan menyebar antara
fungsi minimum dan maksimum secara merata. Warna yang lebih gelap atau
lebih terang dapat ditambahkan dengan &gt;hue untuk menunjukkan nilai
fungsi. Untuk fungsi implisit, xv harus berupa fungsi atau ekspresi
dari parameter x dan y, atau, sebagai alternatif, xv dapat berupa
matriks nilai.


Euler dapat menandai garis level


dari fungsi apapun.


Untuk menggambar himpunan f(x,y)=c untuk satu atau lebih konstanta c,
Anda dapat menggunakan plot2d() dengan plot implisitnya di dalam
bidang. Parameter untuk c adalah level=c, di mana c dapat berupa
vektor garis level. Selain itu, skema warna dapat digambar di latar
belakang untuk menunjukkan nilai fungsi untuk setiap titik dalam plot.
Parameter "n" menentukan kehalusan plot.


\>aspect(1.5); 

\>plot2d("x^2+y^2-x\*y-x",r=1.5,level=0,contourcolor=red):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-127.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-127.png)

\>expr := "2\*x^2+x\*y+3\*y^4+y"; // define an expression f(x,y)

\>plot2d(expr,level=0): // Solutions of f(x,y)=0


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-128.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-128.png)

\>plot2d(expr,level=0:0.5:20,\>hue,contourcolor=white,n=200): // nice


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-129.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-129.png)

\>plot2d(expr,level=0:0.5:20,\>hue,\>spectral,n=200,grid=4): // nicer


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-130.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-130.png)

Ini berfungsi untuk plot data juga. Tetapi Anda harus menentukan
rentangnya untuk label sumbu.


\>x=-2:0.05:1; y=x'; z=expr(x,y);

\>plot2d(z,level=0,a=-1,b=2,c=-2,d=1,\>hue):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-131.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-131.png)

\>plot2d("x^3-y^2",\>contour,\>hue,\>spectral):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-132.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-132.png)

\>plot2d("x^3-y^2",level=0,contourwidth=3,\>add,contourcolor=red):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-133.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-133.png)

\>z=z+normal(size(z))\*0.2;

\>plot2d(z,level=0.5,a=-1,b=2,c=-2,d=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-134.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-134.png)

\>plot2d(expr,level=[0:0.2:5;0.05:0.2:5.05],color=lightgray):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-135.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-135.png)

\>plot2d("x^2+y^3+x\*y",level=1,r=4,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-136.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-136.png)

\>plot2d("x^2+2\*y^2-x\*y",level=0:0.1:10,n=100,contourcolor=white,\>hue):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-137.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-137.png)

Juga dimungkinkan untuk mengisi set


dengan rentang tingkat.


Dimungkinkan untuk mengisi wilayah nilai untuk fungsi tertentu. Untuk
ini, level harus berupa matriks 2xn. Baris pertama adalah batas bawah
dan baris kedua berisi batas atas.


\>plot2d(expr,level=[0;1],style="-",color=blue): // 0 <= f(x,y) <= 1


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-138.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-138.png)

Plot implisit juga dapat menunjukkan rentang level. Kemudian level
harus berupa matriks 2xn dari interval level, di mana baris pertama
berisi awal dan baris kedua adalah akhir dari setiap interval. Atau,
vektor baris sederhana dapat digunakan untuk level, dan parameter dl
memperluas nilai level ke interval.


\>plot2d("x^4+y^4",r=1.5,level=[0;1],color=blue,style="/"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-139.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-139.png)

\>plot2d("x^2+y^3+x\*y",level=[0,2,4;1,3,5],style="/",r=2,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-140.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-140.png)

\>plot2d("x^2+y^3+x\*y",level=-10:20,r=2,style="-",dl=0.1,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-141.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-141.png)

\>plot2d("sin(x)\*cos(y)",r=pi,\>hue,\>levels,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-142.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-142.png)

Dimungkinkan juga untuk menandai suatu wilayah


Ini dilakukan dengan menambahkan level dengan dua baris.


\>plot2d("(x^2+y^2-1)^3-x^2\*y^3",r=1.3, ...  
\>     style="#",color=red,<outline, ...  
\>     level=[-2;0],n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-143.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-143.png)

Dimungkinkan untuk menentukan level tertentu. Misalnya, kita dapat
memplot solusi persamaan seperti


\>plot2d("x^3-x\*y+x^2\*y^2",r=6,level=1,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-144.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-144.png)

\>function starplot1 (v, style="/", color=green, lab=none) ...


      if !holding() then clg; endif;
      w=window(); window(0,0,1024,1024);
      h=holding(1);
      r=max(abs(v))*1.2;
      setplot(-r,r,-r,r);
      n=cols(v); t=linspace(0,2pi,n);
      v=v|v[1]; c=v*cos(t); s=v*sin(t);
      cl=barcolor(color); st=barstyle(style);
      loop 1 to n
        polygon([0,c[#],c[#+1]],[0,s[#],s[#+1]],1);
        if lab!=none then
          rlab=v[#]+r*0.1;
          {col,row}=toscreen(cos(t[#])*rlab,sin(t[#])*rlab);
          ctext(""+lab[#],col,row-textheight()/2);
        endif;
      end;
      barcolor(cl); barstyle(st);
      holding(h);
      window(w);
    endfunction
</pre>
Tidak ada kotak atau sumbu kutu di sini. Selain itu, kami menggunakan
jendela penuh untuk plot.


Kami memanggil reset sebelum kami menguji plot ini untuk mengembalikan
default grafis. Ini tidak perlu, jika Anda yakin plot Anda berhasil.


\>reset; starplot1(normal(1,10)+5,color=red,lab=1:10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-145.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-145.png)

Terkadang, Anda mungkin ingin merencanakan sesuatu yang tidak dapat
dilakukan plot2d, tetapi hampir.


Dalam fungsi berikut, kami melakukan plot impuls logaritmik. plot2d
dapat melakukan plot logaritmik, tetapi tidak untuk batang impuls.


\>function logimpulseplot1 (x,y) ...


      {x0,y0}=makeimpulse(x,log(y)/log(10));
      plot2d(x0,y0,>bar,grid=0);
      h=holding(1);
      frame();
      xgrid(ticks(x));
      p=plot();
      for i=-10 to 10;
        if i<=p[4] and i>=p[3] then
           ygrid(i,yt="10^"+i);
        endif;
      end;
      holding(h);
    endfunction
</pre>
Mari kita uji dengan nilai yang terdistribusi secara eksponensial.


\>aspect(1.5); x=1:10; y=-log(random(size(x)))\*200; ...  
\>   logimpulseplot1(x,y):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-146.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-146.png)

Mari kita menganimasikan kurva 2D menggunakan plot langsung. Perintah
plot(x,y) hanya memplot kurva ke jendela plot. setplot(a,b,c,d)
mengatur jendela ini.


Fungsi wait(0) memaksa plot untuk muncul di jendela grafik. Jika
tidak, menggambar ulang terjadi dalam interval waktu yang jarang.


\>function animliss (n,m) ...


    t=linspace(0,2pi,500);
    f=0;
    c=framecolor(0);
    l=linewidth(2);
    setplot(-1,1,-1,1);
    repeat
      clg;
      plot(sin(n*t),cos(m*t+f));
      wait(0);
      if testkey() then break; endif;
      f=f+0.02;
    end;
    framecolor(c);
    linewidth(l);
    endfunction
</pre>
Tekan sembarang tombol untuk menghentikan animasi ini.


\>animliss(2,3); // lihat hasilnya, jika sudah puas, tekan ENTER


# Plot Logaritmik

EMT menggunakan parameter "logplot" untuk skala logaritmik.


Plot logaritma dapat diplot baik menggunakan skala logaritma dalam y
dengan logplot=1, atau menggunakan skala logaritma dalam x dan y
dengan logplot=2, atau dalam x dengan logplot=3.


 - logplot=1: y-logaritma  
 - logplot=2: x-y-logaritma  
 - logplot=3: x-logaritma  

\>plot2d("exp(x^3-x)\*x^2",1,5,logplot=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-147.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-147.png)

\>plot2d("exp(x+sin(x))",0,100,logplot=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-148.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-148.png)

\>plot2d("exp(x+sin(x))",10,100,logplot=2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-149.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-149.png)

\>plot2d("gamma(x)",1,10,logplot=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-150.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-150.png)

\>plot2d("log(x\*(2+sin(x/100)))",10,1000,logplot=3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-151.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-151.png)

Ini juga berfungsi dengan plot data.


\>x=10^(1:20); y=x^2-x;

\>plot2d(x,y,logplot=2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-152.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%202D-152.png)

# Rujukan Lengkap Fungsi 

plot2d() function plot2d (xv, yv, btest, a, b, c, d, xmin, xmax, r, n,
..


logplot, kisi, bingkai, warna bingkai, kotak, warna, ketebalan, gaya,
..


otomatis, tambahkan, pengguna, delta, poin, titik tambahan, gaya
titik, bilah, histogram, ..


distribusi, genap, langkah, sendiri, adaptif, rona, level, kontur, ..


nc, terisi, fillcolor, outline, title, xl, yl, maps, contourcolor, ..


contourwidth, ticks, margin, clipping, cx, cy, insimg, spectral, ..


cgrid, vertikal, lebih kecil, dl, niveau, level)


Fungsi plot serbaguna untuk plot di pesawat (plot 2D). Fungsi ini
dapat melakukan


plot fungsi satu variabel, plot data, kurva bidang, plot batang,
kisi-kisi bilangan kompleks, dan plot implisit fungsi dua variabel.


Parameter


x,y          : persamaan, fungsi atau vektor data


a,b,c,d      : Area plot (default a=-2,b=2)


r            : jika r diset, maka a=cx-r, b=cx+r, c=cy-r, d=cy+r


               r dapat berupa vektor [rx,ry] atau vektor
[rx1,rx2,ry1,ry2].


xmin,xmax    : rentang parameter untuk kurva


auto         : Menentukan y-range secara otomatis (default)


kuadrat      : jika benar, coba pertahankan rentang x-y persegi


n            : jumlah interval (default adaptif)


kisi         :      0 = tidak ada kisi dan label,


                    1 = sumbu saja,


                    2 = grid normal (lihat di bawah untuk jumlah garis
grid)


                    3 = sumbu dalam


                    4 = tidak ada kisi-kisi


                    5 = kisi penuh termasuk margin


                    6 = kutu di bingkai


                    7 = sumbu saja


                    8 = sumbu saja, sub-centang


bingkai      : 0 = tanpa bingkai


framecolor   : warna bingkai dan kisi


margin       : angka antara 0 dan 0,4 untuk margin di sekitar plot


warna        : Warna kurva. Jika ini adalah vektor warna,


            itu akan digunakan untuk setiap baris matriks plot. Dalam
kasus plot titik, itu harus berupa vektor kolom. Jika vektor baris
atau matriks penuh warna digunakan untuk plot titik, itu akan
digunakan untuk setiap titik data.


ketebalan: ketebalan garis untuk kurva


            Nilai ini bisa lebih kecil dari 1 untuk garis yang sangat
tipis.


style        : Plot style untuk garis, spidol, dan isian.


            Untuk poin gunakan


            "[]", "&lt;&gt;", ".", "..", "...",


            "*", "+", "|", "-", "o"


            "[]#", "&lt;&gt;#", "o#" (bentuk terisi)


            "[]w", "&lt;&gt;w", "ow" (tidak transparan)


            Untuk penggunaan garis


            "-", "--", "-.", ".", ".-.", "-.-", "-&gt;"


            Untuk poligon terisi atau plot batang gunakan


            "#", "#O", "O", "/", "\", "\/",


            "+", "|", "-", "t"


poin         : plot titik tunggal alih-alih segmen garis


addpoints    : jika benar, plot segmen garis dan titik


add          : menambahkan plot ke plot yang ada


pengguna     : aktifkan interaksi pengguna untuk fungsi


delta        : ukuran langkah untuk interaksi pengguna


bar          : plot batang (x adalah batas interval, y nilai interval)


histogram    : memplot frekuensi x dalam n subinterval


distribusi=n : memplot distribusi x dengan n subinterval


even         : gunakan nilai antar untuk histogram otomatis.


langkah      : memplot fungsi sebagai fungsi langkah (langkah=1,2)


adaptif      : gunakan plot adaptif (n adalah jumlah langkah minimal)


level        : plot garis level dari fungsi implisit dua variabel


outline      : menggambar batas rentang level.


Jika nilai level adalah matriks 2xn, rentang level akan ditarik


dalam warna menggunakan gaya isian yang diberikan. Jika garis besar
benar, itu


akan digambar dalam warna kontur. Dengan menggunakan fitur ini,
wilayah


f(x,y) antara batas dapat ditandai.


hue          : tambahkan warna hue ke plot level untuk menunjukkan
fungsinya


            nilai


kontur       : Gunakan plot level dengan level otomatis


nc           : jumlah garis level otomatis


judul        : judul plot (default "")


xl, yl       : label untuk sumbu x dan y


lebih kecil  : jika &gt;0, akan ada lebih banyak ruang di sebelah kiri
untuk label.


vertikal     :


  Mengaktifkan atau menonaktifkan label vertikal. Ini mengubah
variabel global


  verticallabels secara lokal untuk satu plot. Nilai 1 hanya set
vertikal


  teks, nilai 2 menggunakan label numerik vertikal pada sumbu y.


terisi       : mengisi plot kurva


fillcolor    : mengisi warna untuk bar dan kurva yang terisi


outline      : batas poligon yang terisi


logplot      : mengatur plot logaritma


            1 = logplot di y,


            2 = plot log di xy,


            3 = logplot dalam x


memiliki     :


  Sebuah string, yang menunjuk ke rutinitas plot sendiri. Dengan &gt;
pengguna, Anda mendapatkan


  interaksi pengguna yang sama seperti di plot2d. Rentang akan diatur


  sebelum setiap panggilan ke fungsi Anda.


peta         : ekspresi peta (0 lebih cepat), fungsi selalu dipetakan.


contourcolor : warna garis kontur


contourwidth : lebar garis kontur


clipping     : mengaktifkan clipping (default adalah true)


judul        :


  Ini dapat digunakan untuk menggambarkan plot. Judul akan muncul di
atas


  jalan cerita. Selain itu, label untuk sumbu x dan y dapat
ditambahkan dengan


  xl="string" atau yl="string". Label lain dapat ditambahkan dengan


  fungsi label() atau labelbox(). Judulnya bisa unicode


  string atau gambar rumus Lateks.


jaringan     :


  Menentukan jumlah garis grid untuk plot grid yang kompleks.


  Harus merupakan pembagi dari ukuran matriks dikurangi 1 (jumlah


  subinterval). cgrid dapat berupa vektor [cx,cy].


 Ringkasan  

 Fungsi dapat merencanakan  

* 
ekspresi, koleksi panggilan atau fungsi dari satu variabel,

* 
kurva parametrik,

* 
data x terhadap data y,

* 
fungsi implisit,

* 
petak batang,

* 
jaringan kompleks,

* 
poligon.


 Jika fungsi atau ekspresi untuk xv diberikan, plot2d() akan  

menghitung


nilai dalam rentang yang diberikan menggunakan fungsi atau ekspresi.
Itu


ekspresi harus berupa ekspresi dalam variabel x. Rentang harus


didefinisikan dalam parameter a dan b kecuali rentang default


[-2,2] harus digunakan. Rentang y akan dihitung secara otomatis,


kecuali c dan d ditentukan, atau radius r, yang menghasilkan kisaran


[-r,r] untuk x dan y. Untuk plot fungsi, plot2d akan menggunakan


evaluasi adaptif fungsi secara default. Untuk mempercepat


plot untuk fungsi yang rumit, matikan ini dengan &lt;adaptif, dan


opsional mengurangi jumlah interval n. Selain itu, plot2d()


akan secara default menggunakan pemetaan. Yaitu, itu akan menghitung
elemen plot


untuk elemen. Jika ekspresi atau fungsi Anda dapat menangani a


vector x, Anda dapat menonaktifkannya dengan &lt;maps untuk evaluasi yang
lebih cepat.


 Perhatikan bahwa plot adaptif selalu dihitung elemen untuk elemen.  



Jika fungsi atau ekspresi untuk xv dan untuk yv ditentukan,


plot2d() akan menghitung kurva dengan nilai xv sebagai koordinat x


dan nilai yv sebagai koordinat y. Dalam hal ini, rentang harus


didefinisikan untuk parameter menggunakan xmin, xmax. Ekspresi yang
terkandung


dalam string harus selalu ekspresi dalam variabel parameter x.


