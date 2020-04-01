# Git LFS
version https://git-lfs.github.com/spec/v1
oid sha256:48b40e065118d2bd96a436368c04817b6d59b5f4b8c737d984426fafc076636b
size 6293

# IF3210-2020-Unity-13517013

## Deskripsi
**Zombie Hunter** adalah game *2d infinite platformer* dengan tujuan mengumpulkan *score* sebanyak-banyaknya dengan membunuh sebanyak mungkin *zombie*.<br/>
Game berlatarkan di hutan dengan nuansa gelap dengan panjang yang tak terbatas. *Zombie* akan muncul secara **acak** untuk **mengejar** dan **menyerang** pemain.<br/>
Pemain bisa membunuh zombie dengan **menginjak** mereka / dengan **menembakkan** 2 tipe senjata yang memiliki kecepatan, ukuran, dan damage yang berbeda.<br/>
Selalu ingat bahwa zombie adalah mahluk yang berbahaya, sehingga jika anda **menyentuh** mereka maka anda akan **terkena damage**. 

## Cara kerja
1. Karakter digerakan dengan **A/D** (Gerak horizontal) dan **Space** (Lompat) serta Karakter selalu menghadap kursor jika kursor bergerak (bisa diubah di setting).
2. Pemain dapat menembak dengan menekan **tombol kiri/kanan mouse**. Tombol kiri akan menembakan ***laser* kecil dengan *cooldown* singkat dan *damage* kecil**. Tombol kanan akan menembakan ***laser* besar dengan *cooldown* lebih lama dan *damage* lebih besar**.
3. *Laser* yang ditembakan pada awalnya akan bergerak menyamping keluar dari tangan pemain kemudian bergerak ke tempat *mouse* **sebelumnya** saat ingin menembak. 
4. Jika pengaturan *Mouse Control Player Direction* dinyalakan, pemain akan menghadap ke arah kursor (kanan jika kursor di sisi kanan layar, kiri jika sebaliknya).
5. Jika pengaturan tersebut dimatikan, bisa menyebabkan meningkatnya kesulitan permainan karena jika pemain mengklik sisi kanan layar tapi karakter sedang menghadap kiri maka ada kemungkinan peluru terbang menabrak karakter. 
6. Karakter berinteraksi dengan lingkungannya **mengikuti hukum fisika** seperti halnya dunia nyata.
7. Ada **suara tembakan** ketika Karakter menembakan senjatanya.
8. Kamera selalu bergerak **mengikuti** Karakter.
9. Karakter dan *zombie* memiliki **animasi** bergerak, menembak (khusus pemain), lompat (khusus pemain), menyerang (khusus *zombie*), dan mati.
10. *Zombie* akan muncul di **rentang nilai X -100 hingga 100** blok dari pemain dan akan **mengejar** pemain jika berada sekitar 50 blok dari pemain.
11. Darah pemain akan berkurang jika **bersentuhan di samping** dengan *zombie* atau **diinjak** oleh *zombie*. Jika **pemain yang menginjak *zombie*** maka darah *zombie* yang akan berkurang.
12. Peluru (*laser*) akan mengurangi darah pemain dan *zombie* dengan nilai yang sama. Berhati hatilah saat menembak!
13. Pemain pada awalnya memiliki darah bernilai **100** dan divisualisasikan di **pojok kiri atas layar**. *Zombie* pada awalnya juga memiliki **100** darah dan divisualisasikan **di atas *zombie* tersebut**. Jika darah pemain mencapai 100, maka game akan **berakhir**.
14. Peta berbentuk 2d dengan panjang tak terbatas (***procedurally generated*** ketika pemain bergerak). Di belakang peta ada objek seperti **rumput** dan **pohon** yang berfungsi sebagai **hiasan**.
15. *Background* peta berupa pemandangan bukit dengan awan dan langit serta menggunakan konsep ***parallax*** untuk memberikan **efek 3D** ke pemain.
16. Untuk setiap *zombie* yang dibunuh, pemain akan mendapatkan **10 poin** ke *score*. *Score* tersebut akan dikirim ke *server* ketika game berakhir.
17. Pada awalnya, game akan menampilkan ***main menu***. ***Main menu*** berisi tombol untuk :
    -  **memulai game**
    -  **mengisi username**
    -  pindah ke ***menu setting***
    -  pindah ke ***menu scoreboard***. 
18. ***Menu setting*** berisi 2 pengaturan yaitu :
    - *Sound effect* dinyalakan / tidak
    - Arah pemain mengikuti mouse / tidak
19. Pengaturan yang dipilih pemain akan disimpan dengan menggunakan ***PlayerPrefs* *Unity***.
20. Untuk optimisasi, saat pemain menembakkan senjatanya dan saat bergerak, game akan menggunakan konsep **Object Pooling** terkait dengan objek peluru dan background.
### Object Pooling
**Object Pooling** adalah konsep dimana kita membuat beberapa *instance* objek pada awalnya kemudian me-*reuse* *instance* tersebut tiap dibutuhkan.<br/>
Dalam game ini, **Object Pooling** digunakan saat pemain menembak peluru dan untuk efek *parallax *background*.<br/>
Saat pemain menembak peluru, akan dicek terlebih dahulu di *pool* apakah ada objek peluru yang sedang *free*, jika ada maka objek tersebut diset posisi dan kecepatan awalnya, kemudian diaktifkan agar muncul dalam game. Setelah menabrak sesuatu / *lifetime* nya habis, peluru akan kembali di set menjadi non-aktif dan siap digunakan kembali.<br/>
Saat pemain bergerak, background akan bergerak mengikuti pemain untuk memberi ilusi panjang tak terbatas. Dikarenakan menggunakan efek *parallax* perlu dibuat beberapa *instance background*. Jika kita membuat dan mendestroy tiap kita bergerak, maka itu akan boros. Sehingga, *instance background* yang diluar kamera akan dipindahkan ke posisi baru searah dengan pemain (me-*reuse instance background*). 
## Library & Asset yang digunakan
### Library :
- Tidak menggunakan library external
### Asset :
- Forest tileset (https://mamanezakon.itch.io/forest-tileset)
- Robot sprite (https://www.gameart2d.com/the-robot---free-sprites.html)
- Zombie sprite (https://www.gameart2d.com/the-zombies-free-sprites.html)
- Healthbar Image & Mask (https://github.com/SecSamDev/HealthBarSAO)
- Healthbar asset pack (https://adwitr.itch.io/pixel-health-bar-asset-pack-2?download)
- Laser sprite (https://opengameart.org/content/lasers-and-beams)
- Free Pixel Font - Thaleah (https://assetstore.unity.com/packages/2d/fonts/free-pixel-font-thaleah-140059)
- Free Sound Effects Pack (https://assetstore.unity.com/packages/audio/sound-fx/free-sound-effects-pack-155776)
## Screenshot aplikasi
### Menu
#### Main Menu
![](img/01_main_menu.png)
#### Scoreboard Menu
![](img/02_scoreboard_menu.png)
#### Setting Menu
![](img/03_setting_menu.png)
### Gameplay
#### Awal
![](img/04_game_awal.png)
#### Game Over
![](img/05_game_over.png)
#### Melompat
![](img/06_game_jump.png)
#### Menembak peluru 1 (Left Mouse Button)
![](img/07_game_shoot1.png)
#### Menembak peluru 2(Right Mouse Button)
![](img/08_game_shoot2.png)
#### Zombie menyerang pemain
![](img/09_game_zombie_attack.png)
#### Menembak sambil berlari
![](img/10_game_shoot_run.png)
### Unity
## Procedurally Generated World
![](img/11_unity_2d.PNG)
