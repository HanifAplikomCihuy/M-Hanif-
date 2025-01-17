﻿# M Hanif Maulana_23030630076_EMT Plot 3D
Nama: M Hanif Maulana Hartono


NIM: 23030630076


Kelas: Matematika B 2023


# Menggambar Plot 3D dengan EMT

Ini adalah pengenalan plot 3D dalam Euler. Kita memerlukan plot 3D
untuk memvisualisasikan fungsi dari dua variabel.


Euler menggambar fungsi-fungsi tersebut dengan menggunakan algoritma
penyortiran untuk menyembunyikan bagian-bagian yang berada di latar
belakang. Secara umum, Euler menggunakan proyeksi sentral. Proyeksi
default adalah dari kuadran positif x-y menuju asal x=y=z=0, namun
dengan sudut=0°, pandangan diarahkan dari arah sumbu y. Sudut pandang
dan ketinggian dapat diubah.


Euler dapat membuat plot:


permukaan dengan bayangan dan garis level atau rentang level,


kumpulan titik-titik (clouds of points),


kurva parametrik,


permukaan implisit.


Plot 3D dari suatu fungsi menggunakan plot3d. Cara termudah adalah
memplot ekspresi dalam x dan y. Parameter r menentukan jangkauan plot
di sekitar (0,0).


\>aspect(1.5); plot3d("x^2+sin(y)",-5,5,0,6\*pi):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-001.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-001.png)

\>plot3d("x^2+x\*sin(y)",-5,5,0,6\*pi):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-002.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-002.png)

Silakan lakukan modifikasi agar gambar "talang bergelombang" tersebut tidak lurus melainkan melengkung/melingkar, baik
melingkar secara mendatar maupun melingkar turun/naik (seperti papan peluncur pada kolam renang. Temukan rumusnya.


# Fungsi dua Variabel

Untuk grafik fungsi, gunakan


* 
ekspresi sederhana dalam x dan y,

* 
nama fungsi dari dua variabell

* 
atau matriks data.


Defaultnya adalah kisi kawat yang diisi dengan warna berbeda di kedua
sisi. Perhatikan bahwa jumlah default interval kisi adalah 10, tetapi
plot menggunakan jumlah default persegi panjang 40x40 untuk membangun
permukaan. Ini dapat diubah.


* 
n=40, n=[40,40]: jumlah garis kisi di setiap arah

* 
grid=10, grid=[10,10]: jumlah garis grid di setiap arah.


Kami menggunakan default n = 40 dan grid = 10.


\>plot3d("x^2+y^2"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-003.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-003.png)

Interaksi pengguna dimungkinkan dengan parameter &gt;user. Pengguna dapat
menekan tombol berikut.


* 
Kiri, kanan, atas, bawah: putar sudut pandang

* 
+,-: memperbesar atau memperkecil

* 
A: menghasilkan anaglyph (lihat di bawah)

* 
L: Beralih Memutar Sumber Cahaya (lihat di bawah)

* 
spasi: atur ulang ke default

* 
return: mengakhiri interaksi


\>plot3d("exp(-x^2+y^2)",\>user, ...  
\>     title="Turn with the vector keys (press return to finish)"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-004.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-004.png)

Rentang plot untuk fungsi dapat ditentukan dengan


* 
a,b: jangka-x

* 
C,D: Rentang-Y

* 
r: kuadrat simetris di sekitar (0,0).

* 
n: jumlah subinterval untuk plot.


Ada beberapa parameter untuk menskalakan fungsi atau mengubah tampilan
grafik.


fscale: menskalakan nilai fungsi (defaultnya adalah &lt;fscale).


Skala: Angka atau vektor 1x2 untuk menskalakan ke arah X dan Y.


frame: jenis bingkai (default 1).


\>plot3d("exp(-(x^2+y^2)/5)",r=10,n=80,fscale=4,scale=1.2,frame=3,\>user):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-005.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-005.png)

Pandangan dapat diubah dengan berbagai cara.


* 
jarak: jarak pandang ke plot.

* 
Zoom: Nilai zoom.

* 
Sudut: Sudut ke sumbu Y negatif dalam radian.

* 
Height: Tinggi tampilan dalam radian.


Nilai default dapat diperiksa atau diubah dengan fungsi view(). Ini
mengembalikan parameter dalam urutan di atas.


\>view


    [5,  2.6,  2,  0.4]

Jarak yang lebih dekat membutuhkan lebih sedikit zoom. Efeknya lebih
seperti lensa sudut lebar.


Dalam contoh berikut, angle=0 dan height=0 terlihat dari sumbu y
negatif. Label sumbu untuk y disembunyikan dalam kasus ini.


\>plot3d("x^2+y",distance=3,zoom=1,angle=pi/2,height=0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-006.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-006.png)

Plot selalu terlihat ke tengah kubus plot. Anda dapat memindahkan
pusat dengan parameter center.


\>plot3d("x^4+y^2",a=0,b=1,c=-1,d=1,angle=-20°,height=20°, ...  
\>     center=[0.4,0,0],zoom=5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-007.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-007.png)

Plot diskalakan agar sesuai dengan kubus unit untuk dilihat. Jadi
tidak perlu mengubah jarak atau zoom tergantung pada ukuran plot.
Namun, label mengacu pada ukuran sebenarnya.


Jika Anda mematikan ini dengan scale=false, Anda perlu berhati-hati,
bahwa plot masih sesuai dengan jendela plot, dengan mengubah jarak
pandang atau zoom, dan memindahkan pusatnya.


\>plot3d("5\*exp(-x^2-y^2)",r=2,<fscale,<scale,distance=13,height=50°, ...  
\>     center=[0,0,-2],frame=3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-008.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-008.png)

Plot kutub juga tersedia. Parameter polar=true menggambar plot kutub.
Fungsi harus tetap merupakan fungsi dari x dan y. Parameter "fscale"
menskalakan fungsi dengan skala sendiri. Jika tidak, fungsi diskalakan
agar sesuai dengan kubus.


\>plot3d("1/(x^2+y^2+1)",r=5,\>polar, ...  
\>   fscale=2,\>hue,n=100,zoom=4,\>contour,color=blue):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-009.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-009.png)

\>function f(r) := exp(-r/2)\*cos(r); ...  
\>   plot3d("f(x^2+y^2)",\>polar,scale=[1,1,0.4],r=pi,frame=3,zoom=4):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-010.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-010.png)

Parameter rotate memutar fungsi dalam x di sekitar sumbu x.


* 
rotate=1: Menggunakan sumbu x

* 
rotate=2: Menggunakan sumbu z


\>plot3d("x^2+1",a=-1,b=1,rotate=true,grid=5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-011.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-011.png)

\>plot3d("x^2+1",a=-1,b=1,rotate=2,grid=5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-012.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-012.png)

\>plot3d("sqrt(25-x^2)",a=0,b=5,rotate=1):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-013.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-013.png)

\>plot3d("x\*sin(x)",a=0,b=6pi,rotate=2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-014.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-014.png)

Berikut adalah plot dengan tiga fungsi.


\>plot3d("x","x^2+y^2","y",r=2,zoom=3.5,frame=3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-015.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-015.png)

# Plot Kontur

Untuk plot, Euler menambahkan garis kisi. Sebagai gantinya,
dimungkinkan untuk menggunakan garis level dan rona satu warna atau
rona berwarna spektral. Euler dapat menggambar ketinggian fungsi pada
plot dengan bayangan. Di semua plot 3D Euler dapat menghasilkan
anaglyph merah/cyan.


* 
&gt;hue: Mengaktifkan bayangan terang alih-alih kabel.

* 
&gt;contour: Plot garis kontur otomatis pada plot.

* 
level=... (atau level): Vektor nilai untuk garis kontur.


Defaultnya adalah level="auto", yang menghitung beberapa garis level
secara otomatis. Seperti yang Anda lihat di plot, level sebenarnya
adalah rentang level.


Gaya default dapat diubah. Untuk plot kontur berikut, kami menggunakan
kisi yang lebih halus untuk 100x100 poin, menskalakan fungsi dan plot,
dan menggunakan sudut pandang yang berbeda.


\>plot3d("exp(-x^2-y^2)",r=2,n=100,level="thin", ...  
\>    \>contour,\>spectral,fscale=1,scale=1.1,angle=45°,height=20°):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-016.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-016.png)

\>plot3d("exp(x\*y)",angle=100°,\>contour,color=green):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-017.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-017.png)

Bayangan default menggunakan warna abu-abu. Tetapi rentang warna
spektral juga tersedia.


* 
&gt;spektral: Menggunakan skema spektral default

* 
color=...: Menggunakan warna khusus atau skema spektral


Untuk plot berikut, kami menggunakan skema spektral default dan
meningkatkan jumlah titik untuk mendapatkan tampilan yang sangat
halus.


\>plot3d("x^2+y^2",\>spectral,\>contour,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-018.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-018.png)

Alih-alih garis level otomatis, kita juga dapat mengatur nilai garis
level. Ini akan menghasilkan garis level tipis, bukan rentang level.


\>plot3d("x^2-y^2",0,5,0,5,level=-1:0.1:1,color=redgreen):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-019.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-019.png)

Dalam plot berikut, kita menggunakan dua pita level yang sangat luas
dari -0,1 hingga 1, dan dari 0,9 hingga 1. Ini dimasukkan sebagai
matriks dengan batas level sebagai kolom.


Selain itu, kami melapisi kisi dengan 10 interval di setiap arah.


\>plot3d("x^2+y^3",level=[-0.1,0.9;0,1], ...  
\>     \>spectral,angle=30°,grid=10,contourcolor=gray):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-020.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-020.png)

Dalam contoh berikut, kita memplot himpunan, di mana


lateks: f(x,y) = x^y-y^x = 0


Kami menggunakan satu garis tipis untuk garis level.


\>plot3d("x^y-y^x",level=0,a=0,b=6,c=0,d=6,contourcolor=red,n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-021.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-021.png)

Sangat mungkin untuk menunjukkan bidang kontur di bawah plot. Warna
dan jarak ke plot dapat ditentukan.


\>plot3d("x^2+y^4",\>cp,cpcolor=green,cpdelta=0.2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-022.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-022.png)

Berikut adalah beberapa gaya lagi. Kita selalu mematikan bingkai, dan
menggunakan berbagai skema warna untuk plot dan kisi.


\>figure(2,2); ...  
\>   expr="y^3-x^2"; ...  
\>   figure(1);  ...  
\>     plot3d(expr,<frame,\>cp,cpcolor=spectral); ...  
\>   figure(2);  ...  
\>     plot3d(expr,<frame,\>spectral,grid=10,cp=2); ...  
\>   figure(3);  ...  
\>     plot3d(expr,<frame,\>contour,color=gray,nc=5,cp=3,cpcolor=greenred); ...  
\>   figure(4);  ...  
\>     plot3d(expr,<frame,\>hue,grid=10,\>transparent,\>cp,cpcolor=gray); ...  
\>   figure(0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-023.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-023.png)

Ada beberapa skema spektral lainnya, bernomor dari 1 hingga 9. Tetapi
Anda juga dapat menggunakan color=value, di mana nilai


* 
spektral: untuk rentang dari biru hingga merah

* 
putih: untuk kisaran yang lebih redup

* 
kuningbiru, unguhijau, birukuning, hijau merah

* 
birukuning, hijauungu, kuningbiru, merah hijau


\>figure(3,3); ...  
\>   for i=1:9;  ...  
\>     figure(i); plot3d("x^2+y^2",spectral=i,\>contour,\>cp,<frame,zoom=4);  ...  
\>   end; ...  
\>   figure(0):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-024.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-024.png)

Sumber cahaya dapat diubah dengan l dan tombol kursor selama interaksi
pengguna. Itu juga dapat diatur dengan parameter.


* 
cahaya: arah untuk cahaya

* 
AMB: Cahaya sekitar antara 0 dan 1


Perhatikan bahwa program ini tidak membuat perbedaan antara sisi plot.
Tidak ada bayangan. Untuk ini Anda membutuhkan Povray.


\>plot3d("-x^2-y^2", ...  
\>     hue=true,light=[0,1,1],amb=0,user=true, ...  
\>     title="Press l and cursor keys (return to exit)"):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-025.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-025.png)

Parameter warna mengubah warna permukaan. Warna garis level juga dapat
diubah.


\>plot3d("-x^2-y^2",color=rgb(0.2,0.2,0),hue=true,frame=false, ...  
\>     zoom=3,contourcolor=red,level=-2:0.1:1,dl=0.01):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-026.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-026.png)

Warna 0 memberikan efek pelangi khusus.


\>plot3d("x^2/(x^2+y^2+1)",color=0,hue=true,grid=10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-027.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-027.png)

Permukaannya juga dapat dibuat menjadi transparan


\>plot3d("x^2+y^2",\>transparent,grid=10,wirecolor=red):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-028.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-028.png)

# Plot Implisit

Ada juga plot implisit dalam tiga dimensi. Euler menghasilkan potongan
melalui objek. Fitur plot3d termasuk plot implisit. Plot ini
menunjukkan himpunan nol fungsi dalam tiga variabel.


Solusi dari


lateks: f(x,y,z) = 0


dapat divisualisasikan dalam potongan sejajar dengan bidang XY, XZ dan
YZ.


* 
implisit=1: potong sejajar dengan bidang y-z

* 
implisit=2: potong sejajar dengan bidang x-z

* 
implisit=4: potong sejajar dengan bidang x-y


Tambahkan nilai-nilai ini, jika Anda suka. Dalam contoh kita memplot


lateks: M = { (x,y,z) : x^2+y^3+zy=1 }


\>plot3d("x^2+y^3+z\*y-1",r=5,implicit=3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-029.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-029.png)

\>c=1; d=1;

\>plot3d("((x^2+y^2-c^2)^2+(z^2-1)^2)\*((y^2+z^2-c^2)^2+(x^2-1)^2)\*((z^2+x^2-c^2)^2+(y^2-1)^2)-d",r=2,<frame,\>implicit,\>user): 


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-030.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-030.png)

\>plot3d("x^2+y^2+4\*x\*z+z^3",\>implicit,r=2,zoom=2.5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-031.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-031.png)

# Meplot Data 3D

Sama seperti plot2d, plot3d menerima data. Untuk objek 3D, Anda perlu
menyediakan matriks nilai x, y- dan z, atau tiga fungsi atau ekspresi
fx(x,y), fy(x,y), fz(x,y).


lateks: gamma(t,s) = (x(t,s),y(t,s),z(t,s))


Karena x,y,z adalah matriks, kita berasumsi bahwa (t,s) berjalan
melalui kisi persegi. Hasilnya, Anda dapat memplot gambar persegi
panjang di luar angkasa.


Anda dapat menggunakan bahasa matriks Euler untuk menghasilkan
koordinat secara efektif.


Dalam contoh berikut, kita menggunakan vektor nilai t dan vektor kolom
nilai s untuk membuat parameter permukaan bola. Dalam gambar kita
dapat menandai wilayah, dalam kasus kita wilayah kutub.


\>t=linspace(0,2pi,180); s=linspace(-pi/2,pi/2,90)'; ...  
\>   x=cos(s)\*cos(t); y=cos(s)\*sin(t); z=sin(s); ...  
\>   plot3d(x,y,z,\>hue, ...  
\>   color=blue,<frame,grid=[10,20], ...  
\>   values=s,contourcolor=red,level=[90°-24°;90°-22°], ...  
\>   scale=1.4,height=50°):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-032.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-032.png)

Berikut adalah contoh, yang merupakan grafik dari suatu fungsi.


\>t=-1:0.1:1; s=(-1:0.1:1)'; plot3d(t,s,t\*s,grid=10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-033.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-033.png)

Namun, kita bisa membuat segala macam permukaan. Berikut adalah
permukaan yang sama dengan fungsi


lateks: x = y , z


\>plot3d(t\*s,t,s,angle=180°,grid=10):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-034.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-034.png)

Dengan lebih banyak usaha, kita dapat menghasilkan banyak permukaan.


Dalam contoh berikut kita membuat tampilan berbayang dari bola yang
terdistorsi. Koordinat yang biasa untuk bola adalah


lateks: gamma(t,s) = (cos(t)cos(s),sin(t)sin(s),cos(s))


dengan


lateks: 0 le t le 2pi, quad frac{-pi}{2} le s le frac{pi}{2}.


Kami menyimpan ini dengan faktor


lateks: d(t,s) = frac{cos(4t)+cos(8s)}{4}.


\>t=linspace(0,2pi,320); s=linspace(-pi/2,pi/2,160)'; ...  
\>   d=1+0.2\*(cos(4\*t)+cos(8\*s)); ...  
\>   plot3d(cos(t)\*cos(s)\*d,sin(t)\*cos(s)\*d,sin(s)\*d,hue=1, ...  
\>     light=[1,0,1],frame=0,zoom=5):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-035.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-035.png)

Tentu saja, point cloud juga dimungkinkan. Untuk memplot data titik di
ruang, kita membutuhkan tiga vektor untuk koordinat titik.


Gayanya sama seperti di plot2d dengan points=true;


\>n=500;  ...  
\>     plot3d(normal(1,n),normal(1,n),normal(1,n),points=true,style="."):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-036.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-036.png)

Dimungkinkan juga untuk memplot kurva dalam 3D. Dalam hal ini, lebih
mudah untuk menghitung titik-titik kurva terlebih dahulu. Untuk kurva
dalam bidang kita menggunakan urutan koordinat dan parameter
wire=true.


\>t=linspace(0,8pi,500); ...  
\>   plot3d(sin(t),cos(t),t/10,\>wire,zoom=3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-037.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-037.png)

\>t=linspace(0,4pi,1000); plot3d(cos(t),sin(t),t/2pi,\>wire, ...  
\>   linewidth=3,wirecolor=blue):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-038.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-038.png)

\>X=cumsum(normal(3,100)); ...  
\>    plot3d(X[1],X[2],X[3],\>anaglyph,\>wire):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-039.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-039.png)

EMT juga dapat merencanakan dalam mode anaglyph. Untuk melihat plot
seperti itu, Anda membutuhkan kacamata merah/cyan.


\> plot3d("x^2+y^3",\>anaglyph,\>contour,angle=30°):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-040.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-040.png)

Seringkali, skema warna spektral digunakan untuk plot. Ini menekankan
ketinggian fungsi.


\>plot3d("x^2\*y^3-y",\>spectral,\>contour,zoom=3.2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-041.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-041.png)

Euler juga dapat memplot permukaan berparameter, ketika parameternya
adalah nilai x, y, dan z dari gambar kisi persegi panjang di ruang.


Untuk demo berikut, kami mengatur parameter u- dan v-, dan
menghasilkan koordinat ruang dari ini.


\>u=linspace(-1,1,10); v=linspace(0,2\*pi,50)'; ...  
\>   X=(3+u\*cos(v/2))\*cos(v); Y=(3+u\*cos(v/2))\*sin(v); Z=u\*sin(v/2); ...  
\>   plot3d(X,Y,Z,\>anaglyph,<frame,\>wire,scale=2.3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-042.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-042.png)

Berikut adalah contoh yang lebih rumit, yang megah dengan kacamata
merah/cyan.


\>u:=linspace(-pi,pi,160); v:=linspace(-pi,pi,400)';  ...  
\>   x:=(4\*(1+.25\*sin(3\*v))+cos(u))\*cos(2\*v); ...  
\>   y:=(4\*(1+.25\*sin(3\*v))+cos(u))\*sin(2\*v); ...  
\>    z=sin(u)+2\*cos(3\*v); ...  
\>   plot3d(x,y,z,frame=0,scale=1.5,hue=1,light=[1,0,-1],zoom=2.8,\>anaglyph):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-043.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-043.png)

# Plot Statistik

Plot bar juga dimungkinkan. Untuk ini, kami harus menyediakan


* 
x: vektor baris dengan n+1 elemen

* 
y: vektor kolom dengan elemen n+1

* 
z: matriks nilai nxn.


z bisa lebih besar, tetapi hanya nilai nxn yang akan digunakan.


Dalam contoh, pertama-tama kita menghitung nilainya. Kemudian kita
sesuaikan x dan y, sehingga vektor berpusat pada nilai yang digunakan.


\>x=-1:0.1:1; y=x'; z=x^2+y^2; ...  
\>   xa=(x|1.1)-0.05; ya=(y\_1.1)-0.05; ...  
\>   plot3d(xa,ya,z,bar=true):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-044.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-044.png)

Dimungkinkan untuk membagi plot permukaan menjadi dua bagian atau
lebih.


\>x=-1:0.1:1; y=x'; z=x+y; d=zeros(size(x)); ...  
\>   plot3d(x,y,z,disconnect=2:2:20):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-045.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-045.png)

Jika memuat atau menghasilkan matriks data M dari file dan perlu
memplotnya dalam 3D, Anda dapat menskalakan matriks ke [-1,1] dengan
skala(M), atau menskalakan matriks dengan skala &gt;z. Ini dapat
dikombinasikan dengan faktor penskalaan individu yang diterapkan
tambahan.


\>i=1:20; j=i'; ...  
\>   plot3d(i\*j^2+100\*normal(20,20),\>zscale,scale=[1,1,1.5],angle=-40°,zoom=1.8):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-046.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-046.png)

\>Z=intrandom(5,100,6); v=zeros(5,6); ...  
\>   loop 1 to 5; v[#]=getmultiplicities(1:6,Z[#]); end; ...  
\>   columnsplot3d(v',scols=1:5,ccols=[1:5]):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-047.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-047.png)

# Permukaan Benda Putar

\>plot2d("(x^2+y^2-1)^3-x^2\*y^3",r=1.3, ...  
\>   style="#",color=red,<outline, ...  
\>   level=[-2;0],n=100):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-048.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-048.png)

\>ekspresi &= (x^2+y^2-1)^3-x^2\*y^3; $ekspresi


$$\left(y^2+x^2-1\right)^3-x^2\,y^3$$Kita ingin memutar kurva jantung di sekitar sumbu y. Berikut adalah
ekspresi, yang mendefinisikan hati:


lateks: f(x,y)=(x^2+y^2-1)^3-x^2.y^3.


Selanjutnya kita atur


lateks: x=r.cos(a),quad y=r.sin(a).


\>function fr(r,a) &= ekspresi with [x=r\*cos(a),y=r\*sin(a)] | trigreduce; $fr(r,a)


$$\left(r^2-1\right)^3+\frac{\left(\sin \left(5\,a\right)-\sin \left(
 3\,a\right)-2\,\sin a\right)\,r^5}{16}$$Ini memungkinkan untuk mendefinisikan fungsi numerik, yang memecahkan
r, jika a diberikan. Dengan fungsi itu kita dapat memplot jantung yang
diputar sebagai permukaan parametrik.


\>function map f(a) := bisect("fr",0,2;a); ...  
\>   t=linspace(-pi/2,pi/2,100); r=f(t);  ...  
\>   s=linspace(pi,2pi,100)'; ...  
\>   plot3d(r\*cos(t)\*sin(s),r\*cos(t)\*cos(s),r\*sin(t), ...  
\>   \>hue,<frame,color=red,zoom=4,amb=0,max=0.7,grid=12,height=50°):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-051.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-051.png)

Berikut ini adalah plot 3D dari gambar di atas yang diputar di sekitar
sumbu z. Kami mendefinisikan fungsi, yang menggambarkan objek.


\>function f(x,y,z) ...


    r=x^2+y^2;
    return (r+z^2-1)^3-r*z^3;
     endfunction
</pre>
\>plot3d("f(x,y,z)", ...  
\>   xmin=0,xmax=1.2,ymin=-1.2,ymax=1.2,zmin=-1.2,zmax=1.4, ...  
\>   implicit=1,angle=-30°,zoom=2.5,n=[10,100,60],\>anaglyph):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-052.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-052.png)

# Special 3D Plots

The plot3d function is nice to have, but it does not satisfy all
needs. Besides more basic routines, it is possible to get a framed
plot of any object you like.


Though Euler is not a 3D program, it can combine some basic objects.
We try to visualize a paraboloid and its tangent.


\>function myplot ...


      y=-1:0.01:1; x=(-1:0.01:1)';
      plot3d(x,y,0.2*(x-0.1)/2,<scale,<frame,>hue, ..
        hues=0.5,>contour,color=orange);
      h=holding(1);
      plot3d(x,y,(x^2+y^2)/2,<scale,<frame,>contour,>hue);
      holding(h);
    endfunction
</pre>
Sekarang framedplot() menyediakan bingkai, dan mengatur tampilan.


\>framedplot("myplot",[-1,1,-1,1,0,1],height=0,angle=-30°, ...  
\>     center=[0,0,-0.7],zoom=3):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-053.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-053.png)

Dengan cara yang sama, Anda dapat memplot bidang kontur secara manual.
Perhatikan bahwa plot3d() mengatur jendela ke fullwindow() secara
default, tetapi plotcontourplane() mengasumsikan itu.


\>x=-1:0.02:1.1; y=x'; z=x^2-y^4;

\>function myplot (x,y,z) ...  
\>  
<pre class="udf">      zoom(2);
      wi=fullwindow();
      plotcontourplane(x,y,z,level="auto",<scale);
      plot3d(x,y,z,>hue,<scale,>add,color=white,level="thin");
      window(wi);
      reset();
    endfunction
</pre>
\>myplot(x,y,z):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-054.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-054.png)

*Animasi


Euler dapat menggunakan bingkai untuk menghitung animasi sebelumnya.


Salah satu fungsi, yang memanfaatkan teknik ini adalah putar. Itu
dapat mengubah sudut pandang dan menggambar ulang plot 3D. Fungsi
memanggil addpage() untuk setiap plot baru. Akhirnya itu
menganimasikan plot.


Silakan pelajari sumber rotasi untuk melihat lebih jelasnya.


\>function testplot () := plot3d("x^2+y^3"); ...  
\>   rotate("testplot"); testplot():


    User interrupted!
    animate:
        end;
    Try "trace errors" to inspect local variables after errors.
    rotate:
        animate(d);

# Menggambar Povray

Dengan bantuan file Euler povray.e, Euler dapat menghasilkan file
Povray. Hasilnya sangat bagus untuk dilihat.


Anda perlu menginstal Povray (32bit atau 64bit) dari
  <a href="http://www.povray.org/, dan menempatkan sub-direktori "bin" Povray ke jalur lingkungan, atau mengatur variabel "defaultpovray" dengan jalur penuh menunjuk ke "pvengine.exe".">http://www.povray.org/, dan menempatkan sub-direktori "bin" Povray ke jalur lingkungan, atau mengatur variabel "defaultpovray" dengan jalur penuh menunjuk ke "pvengine.exe".</a>


Antarmuka Povray Euler menghasilkan file Povray di direktori beranda
pengguna, dan memanggil Povray untuk mengurai file-file ini. Nama file
default adalah current.pov, dan direktori default adalah eulerhome(),
biasanya c:UsersUsernameEuler. Povray menghasilkan file PNG, yang
dapat dimuat oleh Euler ke dalam notebook. Untuk membersihkan
file-file ini, gunakan povclear().


Fungsi pov3d memiliki semangat yang sama dengan plot3d. Ini dapat
menghasilkan grafik fungsi f(x,y), atau permukaan dengan koordinat
X,Y,Z dalam matriks, termasuk garis level opsional. Fungsi ini memulai
raytracer secara otomatis, dan memuat adegan ke dalam notebook Euler.


Selain pov3d(), ada banyak fungsi, yang menghasilkan objek Povray.
Fungsi-fungsi ini mengembalikan string, yang berisi kode Povray untuk
objek. Untuk menggunakan fungsi ini, mulai file Povray dengan
povstart(). Kemudian gunakan writeln(...) untuk menulis objek ke file
adegan. Terakhir, akhiri file dengan povend(). Secara default,
raytracer akan dimulai, dan PNG akan dimasukkan ke dalam buku catatan
Euler.


Fungsi objek memiliki parameter yang disebut "tampilan", yang
membutuhkan string dengan kode Povray untuk tekstur dan hasil akhir
objek. Fungsi povlook() dapat digunakan untuk menghasilkan string ini.
Ini memiliki parameter untuk warna, transparansi, Phong Shading, dll.


Perhatikan bahwa alam semesta Povray memiliki sistem koordinat lain.
Antarmuka ini menerjemahkan semua koordinat ke sistem Povray. Jadi
Anda dapat terus berpikir dalam sistem koordinat Euler dengan z
menunjuk secara vertikal ke atas, sumbu x x , y , z dalam pengertian
tangan kanan.


Anda perlu memuat file povray.


\>load povray;


Pastikan, direktori bin Povray ada di jalur. Jika tidak, edit variabel
berikut sehingga berisi jalur ke povray yang dapat dieksekusi.


\>defaultpovray="C:\\Program Files\\POV-Ray\\v3.7\\bin\\pvengine.exe"


    C:\Program Files\POV-Ray\v3.7\bin\pvengine.exe

Untuk kesan pertama, kami memplot fungsi sederhana. Perintah berikut
menghasilkan file povray di direktori pengguna Anda, dan menjalankan
Povray untuk ray tracing file ini.


Jika Anda memulai perintah berikut, GUI Povray akan terbuka,
menjalankan file, dan ditutup secara otomatis. Karena alasan keamanan,
Anda akan ditanya, apakah Anda ingin mengizinkan file exe berjalan.
Anda dapat menekan batal untuk menghentikan pertanyaan lebih lanjut.
Anda mungkin harus menekan OK di jendela Povray untuk mengakui dialog
start-up Povray.


\>plot3d("x^2+y^2",zoom=2):


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-055.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-055.png)

\>pov3d("x^2+y^2",zoom=3);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-056.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-056.png)

Kita dapat membuat fungsi transparan dan menambahkan hasil akhir lain.
Kita juga dapat menambahkan garis level ke plot fungsi.


\>pov3d("x^2+y^3",axiscolor=red,angle=-45°,\>anaglyph, ...  
\>     look=povlook(cyan,0.2),level=-1:0.5:1,zoom=3.8);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-057.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-057.png)

Terkadang perlu untuk mencegah penskalaan fungsi, dan menskalakan
fungsi dengan tangan.


Kami memplot himpunan titik di bidang kompleks, di mana produk jarak
ke 1 dan -1 sama dengan 1.


\>pov3d("((x-1)^2+y^2)\*((x+1)^2+y^2)/40",r=2, ...  
\>     angle=-120°,level=1/40,dlevel=0.005,light=[-1,1,1],height=10°,n=50, ...  
\>     <fscale,zoom=3.8);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-058.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-058.png)

# Merencanakan dengan Koordinat

Alih-alih fungsi, kita dapat merencanakan dengan koordinat. Seperti
dalam plot3d, kita membutuhkan tiga matriks untuk mendefinisikan
objek.


Dalam contoh kita memutar fungsi di sekitar sumbu z.


\>function f(x) := x^3-x+1; ...  
\>   x=-1:0.01:1; t=linspace(0,2pi,50)'; ...  
\>   Z=x; X=cos(t)\*f(x); Y=sin(t)\*f(x); ...  
\>   pov3d(X,Y,Z,angle=40°,look=povlook(red,0.1),height=50°,axis=0,zoom=4,light=[10,5,15]);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-059.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-059.png)

In the following example, we plot a damped wave. We generate the wave with the matrix language of Euler.


We also show, how an additional object can be added to a pov3d scene. For the generation of objects, see the following
examples. Note that plot3d scales the plot, so that it fits into the unit cube.


\>r=linspace(0,1,80); phi=linspace(0,2pi,80)'; ...  
\>   x=r\*cos(phi); y=r\*sin(phi); z=exp(-5\*r)\*cos(8\*pi\*r)/3;  ...  
\>   pov3d(x,y,z,zoom=6,axis=0,height=30°,add=povsphere([0.5,0,0.25],0.15,povlook(red)), ...  
\>     w=500,h=300);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-060.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-060.png)

Dengan metode bayangan Povray yang canggih, sangat sedikit titik yang
dapat menghasilkan permukaan yang sangat halus. Hanya di batas dan
dalam bayang-bayang, triknya mungkin menjadi jelas.


Untuk ini, kita perlu menambahkan vektor normal di setiap titik
matriks.


\>Z &= x^2\*y^3


    
                                     2  3
                                    x  y
    

Persamaan permukaan adalah [x,y,Z]. Kami menghitung dua turunan untuk
x dan y dari ini dan mengambil produk silang sebagai normal.


\>dx &= diff([x,y,Z],x); dy &= diff([x,y,Z],y);


Kita mendefinisikan normal sebagai produk silang dari turunan ini, dan
mendefinisikan fungsi koordinat.


\>N &= crossproduct(dx,dy); NX &= N[1]; NY &= N[2]; NZ &= N[3]; N,


    
                                   3       2  2
                           [- 2 x y , - 3 x  y , 1]
    

Kita hanya menggunakan 25 poin


\>x=-1:0.5:1; y=x';

\>pov3d(x,y,Z(x,y),angle=10°, ...  
\>     xv=NX(x,y),yv=NY(x,y),zv=NZ(x,y),<shadow);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-061.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-061.png)

Berikut ini adalah simpul Trefoil yang dilakukan oleh A. Busser di
Povray. Ada versi yang ditingkatkan dari ini dalam contoh.


Lihat: ContohSimpul Trefoil | Simpul Trefoil


Untuk tampilan yang bagus dengan tidak terlalu banyak titik, kami
menambahkan vektor normal di sini. Kami menggunakan Maxima untuk
menghitung normal untuk kami. Pertama, tiga fungsi untuk koordinat
sebagai ekspresi simbolis.


\>X &= ((4+sin(3\*y))+cos(x))\*cos(2\*y); ...  
\>   Y &= ((4+sin(3\*y))+cos(x))\*sin(2\*y); ...  
\>   Z &= sin(x)+2\*cos(3\*y);


Kemudian dua vektor turunan ke x dan y.


\>dx &= diff([X,Y,Z],x); dy &= diff([X,Y,Z],y);


Sekarang versi normal, yang merupakan produk silang dari dua turunan.


\>dn &= crossproduct(dx,dy);


Sekarang kita mengevaluasi semua ini secara numerik.


\>x:=linspace(-%pi,%pi,40); y:=linspace(-%pi,%pi,100)';


Vektor normal adalah evaluasi ekspresi simbolis dn[i] untuk i=1,2,3.
Sintaks untuk ini adalah &amp;"expression"(parameter). Ini adalah
alternatif dari metode pada contoh sebelumnya, di mana kita
mendefinisikan ekspresi simbolis NX, NY, NZ terlebih dahulu.


\>pov3d(X(x,y),Y(x,y),Z(x,y),\>anaglyph,axis=0,zoom=5,w=450,h=350, ...  
\>     <shadow,look=povlook(blue), ...  
\>     xv=&"dn[1]"(x,y), yv=&"dn[2]"(x,y), zv=&"dn[3]"(x,y));


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-062.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-062.png)

Kita juga dapat menghasilkan grid dalam 3D.


\>povstart(zoom=4); ...  
\>   x=-1:0.5:1; r=1-(x+1)^2/6; ...  
\>   t=(0°:30°:360°)'; y=r\*cos(t); z=r\*sin(t); ...  
\>   writeln(povgrid(x,y,z,d=0.02,dballs=0.05)); ...  
\>   povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-063.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-063.png)

Dengan povgrid(), kurva adalah hal yang mungkin dibuat.


\>povstart(center=[0,0,1],zoom=3.6); ...  
\>   t=linspace(0,2,1000); r=exp(-t); ...  
\>   x=cos(2\*pi\*10\*t)\*r; y=sin(2\*pi\*10\*t)\*r; z=t; ...  
\>   writeln(povgrid(x,y,z,povlook(red))); ...  
\>   writeAxis(0,2,axis=3); ...  
\>   povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-064.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-064.png)

# Objek Povray

Di atas, kami menggunakan pov3d untuk memplot permukaan. Antarmuka
povray di Euler juga dapat menghasilkan objek Povray. Objek-objek ini
disimpan sebagai string di Euler, dan perlu ditulis ke file Povray.


Kita memulai output dengan povstart().


\>povstart(zoom=4);


Pertama kita mendefinisikan tiga silinder, dan menyimpannya dalam
string di Euler.


Fungsi povx() dll hanya mengembalikan vektor [1,0,0], yang dapat
digunakan sebagai gantinya.


\>c1=povcylinder(-povx,povx,1,povlook(red)); ...  
\>   c2=povcylinder(-povy,povy,1,povlook(yellow)); ...  
\>   c3=povcylinder(-povz,povz,1,povlook(blue)); ...  
\>  
String berisi kode Povray, yang tidak perlu kita pahami pada saat itu.


\>c2


    cylinder { &lt;0,0,-1&gt;, &lt;0,0,1&gt;, 1
     texture { pigment { color rgb &lt;0.941176,0.941176,0.392157&gt; }  } 
     finish { ambient 0.2 } 
     }

Seperti yang Anda lihat, kami menambahkan tekstur ke objek dalam tiga
warna berbeda.


Itu dilakukan oleh povlook(), yang mengembalikan string dengan kode
Povray yang relevan. Kita dapat menggunakan warna Euler default, atau
menentukan warna kita sendiri. Kita juga dapat menambahkan
transparansi, atau mengubah cahaya sekitar.


\>povlook(rgb(0.1,0.2,0.3),0.1,0.5)


     texture { pigment { color rgbf &lt;0.101961,0.2,0.301961,0.1&gt; }  } 
     finish { ambient 0.5 } 
    

Sekarang kita mendefinisikan objek persimpangan, dan menulis hasilnya
ke file.


\>writeln(povintersection([c1,c2,c3]));


Persimpangan tiga silinder sulit divisualisasikan, jika Anda belum
pernah melihatnya sebelumnya.


\>povend;


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-065.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-065.png)

Fungsi berikut menghasilkan fraktal secara rekursif.


Fungsi pertama menunjukkan, bagaimana Euler menangani objek Povray
sederhana. Fungsi povbox() mengembalikan string, yang berisi koordinat
kotak, tekstur, dan finish.


\>function onebox(x,y,z,d) := povbox([x,y,z],[x+d,y+d,z+d],povlook());

\>function fractal (x,y,z,h,n) ...  
\>  
<pre class="udf">     if n==1 then writeln(onebox(x,y,z,h));
     else
       h=h/3;
       fractal(x,y,z,h,n-1);
       fractal(x+2*h,y,z,h,n-1);
       fractal(x,y+2*h,z,h,n-1);
       fractal(x,y,z+2*h,h,n-1);
       fractal(x+2*h,y+2*h,z,h,n-1);
       fractal(x+2*h,y,z+2*h,h,n-1);
       fractal(x,y+2*h,z+2*h,h,n-1);
       fractal(x+2*h,y+2*h,z+2*h,h,n-1);
       fractal(x+h,y+h,z+h,h,n-1);
     endif;
    endfunction
</pre>
\>povstart(fade=10,<shadow);

\>fractal(-1,-1,-1,2,4);

\>povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-066.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-066.png)

Perbedaan memungkinkan memotong satu objek dari yang lain. Seperti
persimpangan, ada bagian dari objek CSG Povray.


\>povstart(light=[5,-5,5],fade=10);


Untuk demonstrasi ini, kita mendefinisikan objek di Povray, alih-alih
menggunakan string di Euler. Definisi segera ditulis ke file.


Koordinat kotak -1 hanya berarti [-1,-1,-1].


\>povdefine("mycube",povbox(-1,1));


Kita dapat menggunakan objek ini di povobject(), yang mengembalikan
string seperti biasa.


\>c1=povobject("mycube",povlook(red));


Kami menghasilkan kubus kedua, dan memutar dan menskalakannya sedikit.


\>c2=povobject("mycube",povlook(yellow),translate=[1,1,1], ...  
\>     rotate=xrotate(10°)+yrotate(10°), scale=1.2);


Kemudian kita mengambil perbedaan dari kedua objek tersebut.


\>writeln(povdifference(c1,c2));


Sekarang tambahkan tiga sumbu.


\>writeAxis(-1.2,1.2,axis=1); ...  
\>   writeAxis(-1.2,1.2,axis=2); ...  
\>   writeAxis(-1.2,1.2,axis=4); ...  
\>   povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-067.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-067.png)

# Fungsi Implisit

Povray dapat memplot himpunan di mana f(x,y,z)=0, seperti parameter
implisit di plot3d. Namun, hasilnya terlihat jauh lebih baik.


Sintaks untuk fungsinya sedikit berbeda. Anda tidak dapat menggunakan
output dari ekspresi Maxima atau Euler.


lateks:
((x^2+y^2-c^2)^2+(z^2-1)^2)*((y^2+z^2-c^2)^2+(x^2-1)^2)*((z^2+x^2-c^2)^2+(y^2-1)^2)=d


\>povstart(angle=70°,height=50°,zoom=4);

\>c=0.1; d=0.1; ...  
\>   writeln(povsurface("(pow(pow(x,2)+pow(y,2)-pow(c,2),2)+pow(pow(z,2)-1,2))\*(pow(pow(y,2)+pow(z,2)-pow(c,2),2)+pow(pow(x,2)-1,2))\*(pow(pow(z,2)+pow(x,2)-pow(c,2),2)+pow(pow(y,2)-1,2))-d",povlook(red))); ...  
\>   povend();


    Error : Povray error!
    
    Error generated by error() command
    
    povray:
        error("Povray error!");
    Try "trace errors" to inspect local variables after errors.
    povend:
        povray(file,w,h,aspect,exit); 

\>povstart(angle=25°,height=10°); 

\>writeln(povsurface("pow(x,2)+pow(y,2)\*pow(z,2)-1",povlook(blue),povbox(-2,2,"")));

\>povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-068.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-068.png)

\>povstart(angle=70°,height=50°,zoom=4);


Create the implicit surface. Note the different syntax in the
expression.


\>writeln(povsurface("pow(x,2)\*y-pow(y,3)-pow(z,2)",povlook(green))); ...  
\>   writeAxes(); ...  
\>   povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-069.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-069.png)

# Objek Mesh

Dalam contoh ini, kami menunjukkan cara membuat objek mesh, dan
menggambarnya dengan informasi tambahan.


Kami ingin memaksimalkan xy dalam kondisi x+y=1 dan menunjukkan
sentuhan tangensial dari garis level.


\>povstart(angle=-10°,center=[0.5,0.5,0.5],zoom=7);


Kita tidak dapat menyimpan objek dalam string seperti sebelumnya,
karena terlalu besar. Jadi kita mendefinisikan objek dalam file Povray
menggunakan #declare. Fungsi povtriangle() melakukan ini secara
otomatis. Ini dapat menerima vektor normal seperti pov3d().


Berikut ini mendefinisikan objek mesh, dan langsung menulisnya ke
dalam file.


\>x=0:0.02:1; y=x'; z=x\*y; vx=-y; vy=-x; vz=1;

\>mesh=povtriangles(x,y,z,"",vx,vy,vz);


Sekarang kita mendefinisikan dua cakram, yang akan berpotongan dengan
permukaan.


\>cl=povdisc([0.5,0.5,0],[1,1,0],2); ...  
\>   ll=povdisc([0,0,1/4],[0,0,1],2);


Tulis permukaan dikurangi dua cakram.


\>writeln(povdifference(mesh,povunion([cl,ll]),povlook(green)));


Tulis dua perpotongannya


\>writeln(povintersection([mesh,cl],povlook(red))); ...  
\>   writeln(povintersection([mesh,ll],povlook(gray)));


Tulis poin maksimal.


\>writeln(povpoint([1/2,1/2,1/4],povlook(gray),size=2\*defaultpointsize));


Tambahkan sumbu dan selesaikan.


\>writeAxes(0,1,0,1,0,1,d=0.015); ...  
\>   povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-070.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-070.png)

# Anaglyph di Povray

Untuk menghasilkan anaglyph untuk kacamata merah/cyan, Povray harus
berlari dua kali dari posisi kamera yang berbeda. Ini menghasilkan dua
file Povray dan dua file PNG, yang dimuat dengan fungsi
loadanaglyph().


Tentu saja, Anda memerlukan kacamata merah/cyan untuk melihat contoh
berikut dengan benar.


Fungsi pov3d() memiliki sakelar sederhana untuk menghasilkan anaglyph.


\>pov3d("-exp(-x^2-y^2)/2",r=2,height=45°,\>anaglyph, ...  
\>     center=[0,0,0.5],zoom=3.5);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-071.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-071.png)

Jika Anda membuat adegan dengan objek, Anda perlu memasukkan pembuatan
adegan ke dalam fungsi, dan menjalankannya dua kali dengan nilai yang
berbeda untuk parameter anaglyph.


\>function myscene ...


      s=povsphere(povc,1);
      cl=povcylinder(-povz,povz,0.5);
      clx=povobject(cl,rotate=xrotate(90°));
      cly=povobject(cl,rotate=yrotate(90°));
      c=povbox([-1,-1,0],1);
      un=povunion([cl,clx,cly,c]);
      obj=povdifference(s,un,povlook(red));
      writeln(obj);
      writeAxes();
    endfunction
</pre>
Fungsi povanaglyph() melakukan semua ini. Parameternya seperti pada
povstart() dan povend() digabungkan.


\>povanaglyph("myscene",zoom=4.5);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-072.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-072.png)

# Mendefinisikan Objek sendiri

Antarmuka povray Euler berisi banyak objek. Tetapi Anda tidak terbatas
pada ini. Anda dapat membuat objek sendiri, yang menggabungkan objek
lain, atau merupakan objek yang benar-benar baru.


Kami mendemonstrasikan torus. Perintah Povray untuk ini adalah
"torus". Jadi kita mengembalikan string dengan perintah ini dan
parameternya. Perhatikan bahwa torus selalu berpusat di titik asal.


\>function povdonat (r1,r2,look="") ...


      return "torus {"+r1+","+r2+look+"}";
    endfunction
</pre>
Inilah torus pertama kami.


\>t1=povdonat(0.8,0.2)


    torus {0.8,0.2}

Mari kita gunakan objek ini untuk membuat torus kedua, diterjemahkan
dan diputar.


\>t2=povobject(t1,rotate=xrotate(90°),translate=[0.8,0,0])


    object { torus {0.8,0.2}
     rotate 90 *x 
     translate &lt;0.8,0,0&gt;
     }

Sekarang kita menempatkan benda-benda ini ke dalam sebuah adegan.
Untuk tampilan, kami menggunakan Phong Shading.


\>povstart(center=[0.4,0,0],angle=0°,zoom=3.8,aspect=1.5); ...  
\>   writeln(povobject(t1,povlook(green,phong=1))); ...  
\>   writeln(povobject(t2,povlook(green,phong=1))); ...  
\>  
 &gt;povend();  

memanggil program Povray. Namun, jika terjadi kesalahan, itu tidak
menampilkan kesalahan. Oleh karena itu, Anda harus menggunakan


&gt;povend(&lt;keluar);


jika ada yang tidak berhasil. Ini akan membuat jendela Povray terbuka.


\>povend(h=320,w=480);


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-073.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-073.png)

Berikut adalah contoh yang lebih rumit. Kami menyelesaikan


lateks: Kapak le b, quad x ge 0, quad c.x to text{Maks.}


dan menunjukkan titik yang layak dan optimal dalam plot 3D.


\>A=[10,8,4;5,6,8;6,3,2;9,5,6];

\>b=[10,10,10,10]';

\>c=[1,1,1];


Pertama, mari kita periksa, apakah contoh ini memiliki solusi sama
sekali.


\>x=simplex(A,b,c,\>max,\>check)'


    [0,  1,  0.5]

Ya, ini memiliki solusi


Selanjutnya kita mendefinisikan dua objek. Yang pertama adalah pesawat


lateks: a cdot x le b


\>function oneplane (a,b,look="") ...


      return povplane(a,b,look)
    endfunction
</pre>
Kemudian kita mendefinisikan persimpangan semua setengah ruang dan
kubus.


\>function adm (A, b, r, look="") ...


      ol=[];
      loop 1 to rows(A); ol=ol|oneplane(A[#],b[#]); end;
      ol=ol|povbox([0,0,0],[r,r,r]);
      return povintersection(ol,look);
    endfunction
</pre>
Kita sekarang dapat merencanakan adegan.


\>povstart(angle=120°,center=[0.5,0.5,0.5],zoom=3.5); ...  
\>   writeln(adm(A,b,2,povlook(green,0.4))); ...  
\>   writeAxes(0,1.3,0,1.6,0,1.5); ...  
\>  
Berikut ini adalah lingkaran di sekitar yang optimal.


\>writeln(povintersection([povsphere(x,0.5),povplane(c,c.x')], ...  
\>     povlook(red,0.9)));


Dan kesalahan ke arah yang optimal.


\>writeln(povarrow(x,c\*0.5,povlook(red)));


Kami menambahkan teks ke layar. Teks hanyalah objek 3D. Kita perlu
menempatkan dan memutarnya sesuai dengan pandangan kita.


\>writeln(povtext("Linear Problem",[0,0.2,1.3],size=0.05,rotate=5°)); ...  
\>   povend();


![images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-074.png](images/M%20Hanif%20Maulana_23030630076_EMT%20Plot%203D-074.png)

# Lebih Banyak Contoh

Anda dapat menemukan beberapa contoh lagi untuk Povray di Euler dalam
file berikut.


  <a href="Examples/Dandelin Spheres.html">Examples/Dandelin Spheres</a>  

  <a href="Examples/Donat Math.html">Examples/Donat Math</a>  

  <a href="Examples/Trefoil Knot.html">Examples/Trefoil Knot</a>  

  <a href="Examples/Optimization by Affine Scaling.html">Examples/Optimization by Affine Scaling</a>  

