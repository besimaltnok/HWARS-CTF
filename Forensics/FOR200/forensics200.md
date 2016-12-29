### Hacking Wars CTF - Forensics200 - Hash Killer

Merhaba arkadaşlar bu yazıda sizlere Forensics 200 sorusunun çözümünü anlatacağım. İlk olarak ilgili dosyayı indirip, ne dosyası olduğuna bakıyoruz.

* Komut: file 1d350a83d153f8b3ac43effc10b3713e9bd4758a 
 - Sonuç: 1d350a83d153f8b3ac43effc10b3713e9bd4758a: 7-zip archive data, version 0.4
 
Dosyanın türünü öğrendiğimize göre zipten çıkarmaya çalışalım.

* Komut: 7za 1d350a83d153f8b3ac43effc10b3713e9bd4758a.7z

<img src="/Mobil/Mobil400/Resimler/parola.png"/>

Görüldüğü üzere bir parola gerekmektedir. Bu parolayı elde etmek için aşağıda adımları izleyebilirsiniz.

* rarcrack yazılımı indirilir ve kurulur.
  - https://sourceforge.net/projects/rarcrack/
  - https://www.youtube.com/watch?v=oWDNqCs4HLM
* Daha sonra program kurulumu bitiminde oluşturulan XML dosyası düzenleneir.
 - "current" tagı içerisinde parola kırma işlemine nasıl başlanacağını gösteriyoruz.
 - "abc" tagı içerisinde de kullanılacak karakterleri tanımlıyoruz.
 - Verilen ipucundan yola çıkarak 4 harfli hepsi küçük olacak şekilde bir deneme başlatıyoruz 
 
 <img src="/Mobil/Mobil400/Resimler/brute.png"/>
 
  - Çalıştırılacak komut:
   - rarcrack 1d350a83d153f8b3ac43effc10b3713e9bd4758a --threads 12 --type 7z
 
 Bu işlem sonunda yolo diye bir parola bulunacak ve aşağıdaki komutla dosyayı açacağız.
 
 * Komut: 7za 1d350a83d153f8b3ac43effc10b3713e9bd4758a.7z -pyolo
 
 <img src="/Mobil/Mobil400/Resimler/open.png"/>
 
 Elde edilen dosyayı açıp baktığımızda 40 tane şifreli değer olduğunu görüyoruz.
 
  * cat crackme.txt | wc -l 
   - Sonuc : 40
   
 Sorunun da başlığından yola çıkarak bu değerleri https://hashkiller.co.uk sitesinde SHA1 decrypt kısmına atıyoruz.
 
 Sonuç: 
 
 <img src="/Mobil/Mobil400/Resimler/sha1.png"/>
 
 


