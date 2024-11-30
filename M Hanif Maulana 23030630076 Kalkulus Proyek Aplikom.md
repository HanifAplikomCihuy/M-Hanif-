# Kalkulus dengan EMT
M Hanif Maulana


23030630076


Matematika B 2023


---

Materi Kalkulus mencakup di antaranya:


* 
Fungsi (fungsi aljabar, trigonometri, eksponensial, logaritma,
* komposisi fungsi)

* 
Limit Fungsi,

* 
Turunan Fungsi,

* 
Integral Tak Tentu,

* 
Integral Tentu dan Aplikasinya,

* 
Barisan dan Deret (kekonvergenan barisan dan deret).


EMT (bersama Maxima) dapat digunakan untuk melakukan semua perhitungan
di dalam kalkulus, baik secara numerik maupun analitik (eksak).


## Mendefinisikan Fungsi

Terdapat beberapa cara mendefinisikan fungsi pada EMT, yakni:


* 
Menggunakan format nama_fungsi := rumus fungsi (untuk fungsi
* numerik),

* 
Menggunakan format nama_fungsi &amp;= rumus fungsi (untuk fungsi
* simbolik, namun dapat dihitung secara numerik),

* 
Menggunakan format nama_fungsi &amp;&amp;= rumus fungsi (untuk fungsi
* simbolik murni, tidak dapat dihitung langsung),

* 
Fungsi sebagai program EMT.


Setiap format harus diawali dengan perintah function (bukan sebagai
ekspresi).


Berikut adalah adalah beberapa contoh cara mendefinisikan fungsi.


\>function f(x) := 2\*x^2+exp(sin(x)) // fungsi numerik

\>f(0), f(1), f(pi)


    1
    4.31977682472
    20.7392088022

\>function g(x) := sqrt(x^2-3\*x)/(x+1)

\>g(3)


    0

\>g(0)


    0

\>g(1)


    Floating point error!
    Error in sqrt
    Try "trace errors" to inspect local variables after errors.
    g:
        useglobal; return sqrt(x^2-3*x)/(x+1) 
    Error in:
    g(1) ...
        ^

Nb: Floating point error karena untuk x=1, g(x) akan bernilai imajiner


yaitu


\>f(g(5)) // komposisi fungsi


    2.20920171961

\>g(f(5))


    0.950898070639

\>f(0:10) // nilai-nilai f(1), f(2), ..., f(10)


    [1,  4.31978,  10.4826,  19.1516,  32.4692,  50.3833,  72.7562,
    99.929,  130.69,  163.51,  200.58]

\>fmap(0:10) // sama dengan f(0:10), berlaku untuk semua fungsi


    [1,  4.31978,  10.4826,  19.1516,  32.4692,  50.3833,  72.7562,
    99.929,  130.69,  163.51,  200.58]

Misalkan kita akan mendefinisikan fungsi


Fungsi tersebut tidak dapat didefinisikan sebagai fungsi numerik
secara "inline" menggunakan format :=, melainkan didefinisikan sebagai
program. Perhatikan, kata "map" digunakan agar fungsi dapat menerima
vektor sebagai input, dan hasilnya berupa vektor. Jika tanpa kata
"map" fungsinya hanya dapat menerima input satu nilai.


\>function map f(x) ...


      if x>0 then return x^3
      else return x^2
      endif;
    endfunction
</pre>
\>f(1)


    1

\>f(-2)


    4

\>f(-5:5)


    [25,  16,  9,  4,  1,  0,  1,  8,  27,  64,  125]

\>aspect(1.5); plot2d("f(x)",-5,5):

\>function f(x) &= 2\*E^x // fungsi simbolik


    
                                        x
                                     2 E
    

\>function g(x) &= 3\*x+1


    
                                   3 x + 1
    

\>function h(x) &= f(g(x)) // komposisi fungsi


    
                                     3 x + 1
                                  2 E
    

# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, hitung beberapa nilainya, baik
untuk satu nilai maupun vektor. Gambar grafik tersebut.


Juga, carilah fungsi beberapa (dua) variabel. Lakukan hal sama seperti
di atas.


1. Untuk fungsi




tentukan nilai


a. k(-4)


b. k(4)


\>function k(x) := x^2 -4

\>k(-4), k(4)


    12
    12

\>plot2d("k",-4,4):


2. Untuk fungsi




hitunglah masing-masing nilai.


a. z(6)


b. z(2)


\>function z(x) := (x^2-16)/(x-4)

\>z(6), z(2)


    10
    6

\>plot2d("z",-4,6):


3. Untuk fungsi




tentukan nilai r(4), r(-6), r(8)


\>function f(x) := x^3-3\*x^2+2\*x-4

\>f(4), f(-6), f(8)


    20
    -340
    332

\>plot2d("x^3-3\*x^2+2\*x-4",-2,9):


4. Tentukan nilai f(200) dari fungsi berikut


\>function f(x) := sqrt(x-64)

\>f(200)


    11.6619037897

\>plot2d("sqrt(x-64)",0,200):


5. Untuk fungsi




cari nilai fog(-4), gof(0)


\>function f(x) := x^2-3\*x+2; $f(x)

\>function g(x) := x+3; $g(x)

\>f(g(-4)), g(f(0))


    6
    5

\>plot2d("(x+3)^2-3\*(x+3)+2",-2,2):


6. Tentukan nilai dari




dengan x=1 dan y=3


\>function f(x,y):= x^2+y^2+2\*x-2\*y+1

\>f(1,3)


    7

\>plot3d("x^2+y^2+2\*x-2\*y+1"):


# Menghitung Limit

Perhitungan limit pada EMT dapat dilakukan dengan menggunakan fungsi Maxima, yakni "limit".
Fungsi "limit" dapat digunakan untuk menghitung limit fungsi dalam bentuk ekspresi maupun
fungsi yang sudah didefinisikan sebelumnya. Nilai limit dapat dihitung pada sebarang nilai
atau pada tak hingga (-inf, minf, dan inf). Limit kiri dan limit kanan juga dapat dihitung,
dengan cara memberi opsi "plus" atau "minus". Hasil limit dapat berupa nilai, "und' (tak
definisi), "ind" (tak tentu namun terbatas), "infinity" (kompleks tak hingga).


Perhatikan beberapa contoh berikut. Perhatikan cara menampilkan perhitungan secara lengkap,
tidak hanya menampilkan hasilnya saja.


\>$showev('limit(1/(2\*x-1),x,0))

\>$showev('limit((x^2-3\*x-10)/(x-5),x,5))

\>$showev('limit(sin(x)/x,x,0))

\>plot2d("sin(x)/x",-pi,pi):

\>$showev('limit(sin(x^3)/x,x,0))

\>$showev('limit(log(x), x, minf))

\>$showev('limit((-2)^x,x, inf))

\>$showev('limit(t-sqrt(2-t),t,2,minus))

\>$showev('limit(t-sqrt(2-t),t,5,plus)) // Perhatikan hasilnya

\>plot2d("x-sqrt(2-x)",-2,5):

\>$showev('limit((x^2-9)/(2\*x^2-5\*x-3),x,3))

\>$showev('limit((1-cos(x))/x,x,0))

\>$showev('limit((x^2+abs(x))/(x^2-abs(x)),x,0))

\>$showev('limit((1+1/x)^x,x,inf))

\>$showev('limit((1+k/x)^x,x,inf))

\>$showev('limit((1+x)^(1/x),x,0))

\>$showev('limit((x/(x+k))^x,x,inf))


\>$showev('limit(sin(1/x),x,0))

\>$showev('limit(sin(1/x),x,inf))

\>plot2d("sin(1/x)",-5,5):


# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, hitung nilai limit fungsi
tersebut di beberapa nilai dan di tak hingga. Gambar grafik fungsi
tersebut untuk mengkonfirmasi nilai-nilai limit tersebut.


1. Hitunglah nilai limit berikut.


\>$showev('limit((x-8),x,3))


2. Hitunglah nilai limit berikut.


\>$showev('limit((x^2-4)/(x=2),x,2))


3. Hitunglah nilai limit berikut dan gambarlah grafiknya.


\>$showev('limit((t^2-1)/sin(t-1),t,1))

\>(plot2d("(x^2-1)/sin(x-1)", -10,10)):


4. Tentukan nilai limit berikut.


\>$showev('limit((sqrt(1-2\*x))/((4\*x+2)^2), x, -1))


5. Tentukan nilai limit berikut.


\>$showev('limit(((t-sin(t))^2)/(t^2),t,0))

\>(plot2d("((x-sin(x))^2)/(x^2)",-5,5)):

\>  


# Turunan Fungsi

Definisi turunan:


Berikut adalah contoh-contoh menentukan turunan fungsi dengan
menggunakan definisi turunan (limit).


\>$showev('limit(((x+h)^n-x^n)/h,h,0)) // turunan x^n


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut benar, sehingga benar turunan fungsinya benar.  Tulis
penjelasan Anda di komentar ini.


Sebagai petunjuk, ekspansikan (x+h)^n dengan menggunakan teorema
binomial.


## BUKTI



Untuk




Dengan




maka




Jadi, terbukti benar bahwa


---

\>$showev('limit((sin(x+h)-sin(x))/h,h,0)) // turunan sin(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda
di komentar ini.


Sebagai petunjuk, ekspansikan sin(x+h) dengan menggunakan rumus jumlah
dua sudut.


## Bukti

Jadi, terbukti benar bahwa


---

\>$showev('limit((log(x+h)-log(x))/h,h,0)) // turunan log(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda
di komentar ini.


Sebagai petunjuk, gunakan sifat-sifat logaritma dan hasil limit pada
bagian sebelumnya di atas.


## Bukti



Jadi, terbukti benar bahwa


---

\>$showev('limit((1/(x+h)-1/x)/h,h,0)) // turunan 1/x

\>$showev('limit((E^(x+h)-E^x)/h,h,0)) // turunan f(x)=e^x


    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Maxima is asking
    Acceptable answers are: yes, y, Y, no, n, N, unknown, uk
    Is x an integer?
    
    Use assume!
    Error in:
     $showev('limit((E^(x+h)-E^x)/h,h,0)) // turunan f(x)=e^x ...
                                         ^

Maxima bermasalah dengan limit:


Oleh karena itu diperlukan trik khusus agar hasilnya benar.


\>$showev('limit((E^h-1)/h,h,0))

\>$factor(E^(x+h)-E^x)

\>$showev('limit(factor((E^(x+h)-E^x)/h),h,0)) // turunan f(x)=e^x

\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x


Di sini Maxima juga bermasalah terkait limit:


Dalam hal ini diperlukan asumsi nilai x.


\>&assume(x\>0); $showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x

\>&forget(x\>0) // jangan lupa, lupakan asumsi untuk kembali ke semula


    
                                   [x &gt; 0]
    

\>&forget(x<0)


    
                                   [x &lt; 0]
    

\>&facts()


    
                                      []
    

\>$showev('limit((asin(x+h)-asin(x))/h,h,0)) // turunan arcsin(x)

\>$showev('limit((tan(x+h)-tan(x))/h,h,0)) // turunan tan(x)

\>function f(x) &= sinh(x) // definisikan f(x)=sinh(x)


    
                                   sinh(x)
    

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


Hasilnya adalah cosh(x), karena


\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]):


# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, tentukan turunannya dengan
menggunakan definisi turunan (limit), seperti contoh-contoh tersebut.
Gambar grafik fungsi asli dan fungsi turunannya pada sumbu koordinat
yang sama.


1. Tentukan nilai turunan berikut dan sketsakan grafiknya.


\>function f(x) &= 4\*x^2+8; $f(x)

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); &df(x)//df(x)=f'(x)


    
                                     8 x
    

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[red,green]):


2. Carilah turunan dari fungsi berikut


\>function f(x) &= (x-1)/(x-2); $f(x)

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-10,10,color=[blue,red]):


3. Carilah turunan dari fungsi berikut


\>function f(x) &= 3/sqrt(x-2); $f(x)

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)function f(x) &= 3/sqrt(x-2); $f(x)

\>plot2d(["f(x)","df(x)"],-10,10,color=[yellow,red]):


4. Carilah turunan fungsi berikut.


\>function f(x) &= (4\*sin(x)+6\*cos(x)); $f(x)

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); &df(x)


    
                          - 2 (3 sin(x) - 2 cos(x))
    

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,yellow]):


5. Tentukan turunan dan grafik fungsi berikut.


\>function f(x) &= (sin(x)+cos(x))/(cos(x)); $f(x)

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,yellow]):

\>    


# Integral

EMT dapat digunakan untuk menghitung integral, baik integral tak tentu
maupun integral tentu. Untuk integral tak tentu (simbolik) sudah tentu
EMT menggunakan Maxima, sedangkan untuk perhitungan integral tentu EMT
sudah menyediakan beberapa fungsi yang mengimplementasikan algoritma
kuadratur (perhitungan integral tentu menggunakan metode numerik).


Pada notebook ini akan ditunjukkan perhitungan integral tentu dengan
menggunakan Teorema Dasar Kalkulus:


$$\int_a^b f(x)\ dx = F(b)-F(a), \quad \text{ dengan  } F'(x) = f(x).$$Fungsi untuk menentukan integral adalah integrate. Fungsi ini dapat
digunakan untuk menentukan, baik integral tentu maupun tak tentu (jika
fungsinya memiliki antiderivatif). Untuk perhitungan integral tentu
fungsi integrate menggunakan metode numerik (kecuali fungsinya tidak
integrabel, kita tidak akan menggunakan metode ini).


\>$showev('integrate(x^n,x))


    Answering "Is n equal to -1?" with "no"

$$\int {x^{n}}{\;dx}=\frac{x^{n+1}}{n+1}$$\>$showev('integrate(1/(1+x),x))


$$\int {\frac{1}{x+1}}{\;dx}=\log \left(x+1\right)$$\>$showev('integrate(1/(1+x^2),x))


$$\int {\frac{1}{x^2+1}}{\;dx}=\arctan x$$\>$showev('integrate(1/sqrt(1-x^2),x))


$$\int {\frac{1}{\sqrt{1-x^2}}}{\;dx}=\arcsin x$$\>$showev('integrate(sin(x),x,0,pi))


$$\int_{0}^{\pi}{\sin x\;dx}=2$$\>$showev('integrate(sin(x),x,a,b))


$$\int_{a}^{b}{\sin x\;dx}=\cos a-\cos b$$\>$showev('integrate(x^n,x,a,b))


    Answering "Is n positive, negative or zero?" with "positive"

$$\int_{a}^{b}{x^{n}\;dx}=\frac{b^{n+1}}{n+1}-\frac{a^{n+1}}{n+1}$$\>$showev('integrate(x^2\*sqrt(2\*x+1),x))


$$\int {x^2\,\sqrt{2\,x+1}}{\;dx}=\frac{\left(2\,x+1\right)^{\frac{7
 }{2}}}{28}-\frac{\left(2\,x+1\right)^{\frac{5}{2}}}{10}+\frac{\left(
 2\,x+1\right)^{\frac{3}{2}}}{12}$$\>$showev('integrate(x^2\*sqrt(2\*x+1),x,0,2))


$$\int_{0}^{2}{x^2\,\sqrt{2\,x+1}\;dx}=\frac{2\,5^{\frac{5}{2}}}{21}-
 \frac{2}{105}$$\>$ratsimp(%)


$$\int_{0}^{2}{x^2\,\sqrt{2\,x+1}\;dx}=\frac{2\,5^{\frac{7}{2}}-2}{
 105}$$\>$showev('integrate((sin(sqrt(x)+a)\*E^sqrt(x))/sqrt(x),x,0,pi^2))


$$\int_{0}^{\pi^2}{\frac{\sin \left(\sqrt{x}+a\right)\,e^{\sqrt{x}}}{
 \sqrt{x}}\;dx}=\left(-e^{\pi}-1\right)\,\sin a+\left(e^{\pi}+1
 \right)\,\cos a$$\>$factor(%)


$$\int_{0}^{\pi^2}{\frac{\sin \left(\sqrt{x}+a\right)\,e^{\sqrt{x}}}{
 \sqrt{x}}\;dx}=\left(-e^{\pi}-1\right)\,\left(\sin a-\cos a\right)$$\>function map f(x) &= E^(-x^2)


    
                                        2
                                     - x
                                    E
    

\>$showev('integrate(f(x),x))


$$\int {e^ {- x^2 }}{\;dx}=\frac{\sqrt{\pi}\,\mathrm{erf}\left(x
 \right)}{2}$$Fungsi f tidak memiliki antiturunan, integralnya masih memuat integral
lain.


$$erf(x) = \int \frac{e^{-x^2}}{\sqrt{\pi}} \ dx.$$Kita tidak dapat menggunakan teorema Dasar kalkulus untuk menghitung
integral tentu fungsi tersebut jika semua batasnya berhingga. Dalam
hal ini dapat digunakan metode numerik (rumus kuadratur).


Misalkan kita akan menghitung:


$$\int_{0}^{\pi}{e^ {- x^2 }\;dx}$$\>x=0:0.1:pi-0.1; plot2d(x,f(x+0.1),\>bar); plot2d("f(x)",0,pi,\>add):


![images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-017.png](images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-017.png)

Integral tentu


$$\int_{0}^{\pi}{e^ {- x^2 }\;dx}$$dapat dihampiri dengan jumlah luas persegi-persegi panjang di bawah
kurva y=f(x) tersebut. Langkah-langkahnya adalah sebagai berikut.


\>t &= makelist(a,a,0,pi-0.1,0.1); // t sebagai list untuk menyimpan nilai-nilai x

\>fx &= makelist(f(t[i]+0.1),i,1,length(t)); // simpan nilai-nilai f(x)

\>// jangan menggunakan x sebagai list, kecuali Anda pakar Maxima!


Hasilnya adalah:


$$\int_{0}^{\pi}{e^ {- x^2 }\;dx}=0.8362196102528469$$Jumlah tersebut diperoleh dari hasil kali lebar sub-subinterval (=0.1)
dan jumlah nilai-nilai f(x) untuk x = 0.1, 0.2, 0.3, ..., 3.2.


\>0.1\*sum(f(x+0.1)) // cek langsung dengan perhitungan numerik EMT


    0.836219610253

Untuk mendapatkan nilai integral tentu yang mendekati nilai
sebenarnya, lebar sub-intervalnya dapat diperkecil lagi, sehingga
daerah di bawah kurva tertutup semuanya, misalnya dapat digunakan
lebar subinterval 0.001. (Silakan dicoba!)


Meskipun Maxima tidak dapat menghitung integral tentu fungsi tersebut
untuk batas-batas yang berhingga, namun integral tersebut dapat
dihitung secara eksak jika batas-batasnya tak hingga. Ini adalah salah
satu keajaiban di dalam matematika, yang terbatas tidak dapat dihitung
secara eksak, namun yang tak hingga malah dapat dihitung secara eksak.


\>$showev('integrate(f(x),x,0,inf))


$$\int_{0}^{\infty }{e^ {- x^2 }\;dx}=\frac{\sqrt{\pi}}{2}$$Berikut adalah contoh lain fungsi yang tidak memiliki antiderivatif,
sehingga integral tentunya hanya dapat dihitung dengan metode numerik.


\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('integrate(f(x),x,0,1))


$$\int_{0}^{1}{x^{x}\;dx}=\int_{0}^{1}{x^{x}\;dx}$$\>x=0:0.1:1-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,1,\>add):


![images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-022.png](images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-022.png)

Maxima gagal menghitung integral tentu tersebut secara langsung
menggunakan perintah integrate. Berikut kita lakukan seperti contoh
sebelumnya untuk mendapat hasil atau pendekatan nilai integral tentu
tersebut.


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));


$$\int_{0}^{1}{x^{x}\;dx}=0.7834935879025506$$Apakah hasil tersebut cukup baik? perhatikan gambarnya.


# Latihan

* 
Bukalah buku Kalkulus.

* 
Cari dan pilih beberapa (paling sedikit 5 fungsi berbeda
* tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian definisikan di
* EMT pada baris-baris perintah berikut (jika perlu tambahkan lagi).

* 
Untuk setiap fungsi, tentukan anti turunannya (jika ada), hitunglah
* integral tentu dengan batas-batas yang menarik (Anda tentukan
* sendiri), seperti contoh-contoh tersebut.

* 
Lakukan hal yang sama untuk fungsi-fungsi yang tidak dapat
* diintegralkan (cari sedikitnya 3 fungsi).

* 
Gambar grafik fungsi dan daerah integrasinya pada sumbu koordinat
* yang sama.

* 
Gunakan integral tentu untuk mencari luas daerah yang dibatasi oleh
* dua kurva yang berpotongan di dua titik. (Cari dan gambar kedua kurva
* dan arsir (warnai) daerah yang dibatasi oleh keduanya.)

* 
Gunakan integral tentu untuk menghitung volume benda putar kurva y=
* f(x) yang diputar mengelilingi sumbu x dari x=a sampai x=b, yakni


$$V = \int_a^b \pi (f(x)^2\ dx.$$(Pilih fungsinya dan gambar kurva dan benda putar yang dihasilkan.
Anda dapat mencari contoh-contoh bagaimana cara menggambar benda hasil
perputaran suatu kurva.)


- Gunakan integral tentu untuk menghitung panjang kurva y=f(x) dari
x=a sampai x=b dengan menggunakan rumus:


$$S = \int_a^b \sqrt{1+(f'(x))^2} \ dx.$$(Pilih fungsi dan gambar kurvanya.)


1. Tentukan panjang kurva dan volume benda putar kurva y=f(x) yang
diputar mengelilingi sumbu x dari x=0 sampai x=4


$$f(x)= x^3$$\>function f(x)&=x^3; $f(x)


$$x^3$$\>$showev('integrate(pi\*(f(x))^2,x,0,4))


$$\pi\,\int_{0}^{4}{x^6\;dx}=\frac{16384\,\pi}{7}$$turunan fungsi f(x)


\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$3\,x^2$$panjang kurva


\>$showev('integrate(sqrt((1+df(x)^2)),x,0,4))


$$\int_{0}^{4}{\sqrt{9\,x^4+1}\;dx}=\int_{0}^{4}{\sqrt{9\,x^4+1}\;dx}$$grafik benda putar mengelilingi sumbu x


\> plot3d("x^3",2,0,2,rotate=2):


![images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-031.png](images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-031.png)

2. Tentukan panjang kurva dan volume benda putar kurva y=f(x) yang
diputar mengelilingi sumbu x dari x=-1 sampai x=2


$$f(x) = 3x^2+2x+1$$volume benda putar


\>function f(x)&=3\*x^2+2\*x+1; $f(x) 


$$3\,x^2+2\,x+1$$\>$showev('integrate(pi\*(f(x))^2,x,-1,2))


$$\pi\,\int_{-1}^{2}{\left(3\,x^2+2\,x+1\right)^2\;dx}=\frac{717\,\pi
 }{5}$$menentukan turunan fungsi f(x)


\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$6\,x+2$$menentukan panjang kurva


\>$showev('integrate(sqrt((1+df(x)^2)),x,-1,2))


$$\int_{-1}^{2}{\sqrt{\left(6\,x+2\right)^2+1}\;dx}=\frac{
 {\rm asinh}\; 14+14\,\sqrt{197}}{12}+\frac{{\rm asinh}\; 4+4\,\sqrt{
 17}}{12}$$menggambar plot benda putar mengelilingi sumbu x


\>plot3d("3x^2+2x+1",2,-1,2,rotate=2):


![images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-037.png](images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-037.png)

3. Integral tentu dengan batas [-1,1] dari fungsi berikut


$$f(x)=x^2+8x-9$$\>function map f(x) &= (x^2+8\*x-9); $f(x)


$$x^2+8\,x-9$$mencari nilai dari integral tentu fungsi f(x) dengan batas [-1,1]


\>$showev('integrate(f(x), x, -1, 1))


$$\int_{-1}^{1}{x^2+8\,x-9\;dx}=-\frac{52}{3}$$4. Tentukan panjang kurva dan volume benda putar kurva y=f(x) yang
diputar mengelilingi sumbu x dari x=0 sampai x=2


$$f(x)= 4x^2+1$$\>$showev('integrate(pi\*(f(x))^2,x,0,2))


$$\pi\,\int_{0}^{2}{\left(x^2+8\,x-9\right)^2\;dx}=\frac{1006\,\pi}{
 15}$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$2\,x+8$$menentukan pangjang kurva


\>$showev('integrate(sqrt((1+df(x)^2)),x,0,2))


$$\int_{0}^{2}{\sqrt{\left(2\,x+8\right)^2+1}\;dx}=\frac{
 {\rm asinh}\; 12+12\,\sqrt{145}}{4}-\frac{{\rm asinh}\; 8+8\,\sqrt{
 65}}{4}$$menggambar plot


\>plot3d("4x^2+1",2,0,2,rotate=2):


![images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-045.png](images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-045.png)

5. Tentukan integral fungsi berikut.


$$f(x)= \frac{\sqrt{2x}}{x}+\frac{3}{x^5}$$\>function f(x) &= (sqrt(2\*x))/x +3/x^5 ; $f(x)


$$\frac{\sqrt{2}}{\sqrt{x}}+\frac{3}{x^5}$$\>$showev('integrate((((sqrt(2\*x))/x) +(3/x^5)),x))


$$\int {\frac{\sqrt{2}}{\sqrt{x}}+\frac{3}{x^5}}{\;dx}=2^{\frac{3}{2}
 }\,\sqrt{x}-\frac{3}{4\,x^4}$$\>x=0:0.1:5-0.1; plot2d(x,f(x+0.1),\>bar); plot2d("f(x)",0,5,\>add):


![images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-049.png](images/M%20Hanif%20Maulana%2023030630076%20Kalkulus%20Proyek%20Aplikom-049.png)

# Barisan dan Deret

(Catatan: bagian ini belum lengkap. Anda dapat membaca contoh-contoh
pengguanaan EMT dan Maxima untuk menghitung limit barisan, rumus
jumlah parsial suatu deret, jumlah tak hingga suatu deret konvergen,
dan sebagainya. Anda dapat mengeksplor contoh-contoh di EMT atau
perbagai panduan penggunaan Maxima di software Maxima atau dari
Internet.)


Barisan dapat didefinisikan dengan beberapa cara di dalam EMT, di
antaranya:


* 
dengan cara yang sama seperti mendefinisikan vektor dengan
* elemen-elemen beraturan (menggunakan titik dua ":");

* 
menggunakan perintah "sequence" dan rumus barisan (suku ke -n);

* 
menggunakan perintah "iterate" atau "niterate";

* 
menggunakan fungsi Maxima "create_list" atau "makelist" untuk
* menghasilkan barisan simbolik;

* 
menggunakan fungsi biasa yang inputnya vektor atau barisan;

* 
menggunakan fungsi rekursif.


EMT menyediakan beberapa perintah (fungsi) terkait barisan, yakni:


* 
sum: menghitung jumlah semua elemen suatu barisan

* 
cumsum: jumlah kumulatif suatu barisan

* 
differences: selisih antar elemen-elemen berturutan


EMT juga dapat digunakan untuk menghitung jumlah deret berhingga
maupun deret tak hingga, dengan menggunakan perintah (fungsi) "sum".
Perhitungan dapat dilakukan secara numerik maupun simbolik dan eksak.


Berikut adalah beberapa contoh perhitungan barisan dan deret
menggunakan EMT.


\>1:10 // barisan sederhana


    [1,  2,  3,  4,  5,  6,  7,  8,  9,  10]

\>1:2:30


    [1,  3,  5,  7,  9,  11,  13,  15,  17,  19,  21,  23,  25,  27,  29]

\>sum(1:2:30), sum(1/(1:2:30))


    225
    2.33587263431

\>$'sum(k, k, 1, n) = factor(ev(sum(k, k, 1, n),simpsum=true)) // simpsum:menghitung deret secara simbolik


$$\sum_{k=1}^{n}{k}=\frac{n\,\left(n+1\right)}{2}$$\>$'sum(1/(3^k+k), k, 0, inf) = factor(ev(sum(1/(3^k+k), k, 0, inf),simpsum=true))


$$\sum_{k=0}^{\infty }{\frac{1}{3^{k}+k}}=\sum_{k=0}^{\infty }{\frac{
 1}{3^{k}+k}}$$Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum(1/x^2, x, 1, inf)= ev(sum(1/x^2, x, 1, inf),simpsum=true) // ev: menghitung nilai ekspresi


$$\sum_{x=1}^{\infty }{\frac{1}{x^2}}=\frac{\pi^2}{6}$$\>$'sum((-1)^(k-1)/k, k, 1, inf) = factor(ev(sum((-1)^(x-1)/x, x, 1, inf),simpsum=true))


$$\sum_{k=1}^{\infty }{\frac{\left(-1\right)^{k-1}}{k}}=-\sum_{x=1}^{
 \infty }{\frac{\left(-1\right)^{x}}{x}}$$Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum((-1)^k/(2\*k-1), k, 1, inf) = factor(ev(sum((-1)^k/(2\*k-1), k, 1, inf),simpsum=true))


$$\sum_{k=1}^{\infty }{\frac{\left(-1\right)^{k}}{2\,k-1}}=\sum_{k=1
 }^{\infty }{\frac{\left(-1\right)^{k}}{2\,k-1}}$$\>$ev(sum(1/n!, n, 0, inf),simpsum=true)


$$\sum_{n=0}^{\infty }{\frac{1}{n!}}$$Di sini masih gagal, hasilnya tidak dihitung, harusnya hasilnya e.


\>&assume(abs(x)<1); $'sum(a\*x^k, k, 0, inf)=ev(sum(a\*x^k, k, 0, inf),simpsum=true), &forget(abs(x)<1);


$$a\,\sum_{k=0}^{\infty }{x^{k}}=\frac{a}{1-x}$$Deret geometri tak hingga, dengan asumsi rasional antara -1 dan 1.


\> 


# Deret Taylor

Deret Taylor suatu fungsi f yang diferensiabel sampai tak hingga di
sekitar x=a adalah:


$$f(x) = \sum_{k=0}^\infty \frac{(x-a)^k f^{(k)}(a)}{k!}.$$\>$'e^x =taylor(exp(x),x,0,10) // deret Taylor e^x di sekitar x=0, sampai suku ke-11


$$e^{x}=\frac{x^{10}}{3628800}+\frac{x^9}{362880}+\frac{x^8}{40320}+
 \frac{x^7}{5040}+\frac{x^6}{720}+\frac{x^5}{120}+\frac{x^4}{24}+
 \frac{x^3}{6}+\frac{x^2}{2}+x+1$$\>$'log(x)=taylor(log(x),x,1,10)// deret log(x) di sekitar x=1


$$\log x=x-\frac{\left(x-1\right)^{10}}{10}+\frac{\left(x-1\right)^9
 }{9}-\frac{\left(x-1\right)^8}{8}+\frac{\left(x-1\right)^7}{7}-
 \frac{\left(x-1\right)^6}{6}+\frac{\left(x-1\right)^5}{5}-\frac{
 \left(x-1\right)^4}{4}+\frac{\left(x-1\right)^3}{3}-\frac{\left(x-1
 \right)^2}{2}-1$$