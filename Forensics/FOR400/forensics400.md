### Hacking Wars CTF - Forensics - Memo

Bu soruda da elimizde bir tane dosya vardı. Her zaman soruların isimlerinin bir ipucu olduğunu biliyorum :) Bu nedenle sorunun aslında bir Memory Dump olduğunu tahmin etmek zor olmadı.

Bu dump üzerinde analiz yapabilmek için volatility yazılımı kullandım. Kali işletim sistemi içerisinde kurulu gelen bir araçtır. Siz isterseniz farklı sistemlere de kurabilirsiniz.

Bu tarz analizlerde yapmanızı önerdiğim şey; ilk olarak çalışan process lerin listesini çıkarmanızdır. Bu sayede sistem için dump alındığı sırada nelerin çalıştığı hakkında bir bilginiz olacak ve analiz için diğer adımlarınızı daha verimli atacaksınızdır.

Çalışan process bilgilerini listelemek için:
 * volaitlity --profile=Win7SP1x64 pslit -f win 
  - "-f" : Analiz edilecek dosyayı tanımlar
  - "pslist": Çalışan processleri listeler

Listelenen process bilgilerini analiz ettiğinizde ms paint programına ait bir process göreceksiniz ve benim en çok dikkatimi çeken bu oldu, diğerlerine göre.

* Process name: mspaint.exe
* Process id: 936

Bu process için bir memory dump alıyoruz.

* Komut: volaitlity --profile=Win7SP1x64 -f win memdump -p 936 --dump-dir=/root/Desktop/dump/

Bu işlem sonucunda "936.dmp" isminde bir dosya elde edeceğiz. Bundan sonra yapmamız gereken şey, elde edilen bu dosyanın uzantısını ".data" diye değiştirip GİMP ile açmak olacaktır.

* Komut: mv 936.dmp 936.data

Dosyayı gimp ile açıp yükseklik, genişlik ve göreli konum (offset) değerleri ile oynadığımızda aşağıdaki gibi bir flag ile karşılaşıyoruz.

<img src="/Mobil/Mobil400/Resimler/mspaint.png"/>


NOT: İsterseniz örnek olması açısından aşağıdaki yazıyı da inceleyebilirsiniz.
 - https://w00tsec.blogspot.com.tr/2015/02/extracting-raw-pictures-from-memory.html
