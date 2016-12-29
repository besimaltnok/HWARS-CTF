### Hacking Wars CTF - Mobile500 - 2048

Bu soruda takım arkadaşım Meryem AKDOĞAN'ın çok faydası oldu :)

Bu soru çok ilginç ve güzel hazırlanmış bir soruydu benim için :) Çoğumuz oyunu kurup oynadık. 

Ancak ben ilk olarak dosyayının kurulduktan sonra telefon üzerinde oluşturmuş olduğu dosyaları kontrol ettim. Ancak hiçbir veriye ulaşamadım. Bu nedenle network trafiğini de dinledim ancak belki benim cihazımdan dolayıdır, görmem gereken bir veriyi göremedim.

Bu nedenle uygulama üzerinde statik analiz yapmaya karar verdim ve ilk olarak uygulamayı virustotalde tarattım.
Bulduğum sonuçlar şüphe uyandırdı.

<img src="/Mobil/Mobil400/Resimler/virustotal.png" width="350" height="200"/>

Metasploit yazılımın kalıntıları vardı belli ki bir shell gömülmüştü. Bu nedenle bundan sonraki çalışmaları o yönde yoğunlaştırmak gerekiyordu.

Kaynak kod üzerinde analiz yapmak için aşağıdaki adımlar ile kaynak kodu elde ettim.

* Komut : dex2jar 2048.apk
* Komut : java --jar jd-gui.jar

<img src="/Mobil/Mobil400/Resimler/payload.png" width="350" height="200"/>

Kod üzerinde biraz çalışma yapıktan sonra uygulamanın bağlantı kurduğu adresi tespit ettik. Daha sonra bu adres için whois sorgusu gibi bir çok araştırma yaptık. Önce uygulamada yer alan adresin gerçek olup olmayacağı konusunda kararsız kaldık bu nedenle aktif analiz işlemi yapmadık :)
Ancak daha sonra bir risk alıp uygulama da bağlantı kurulan adres için bir port taraması başlattık :)

* Komut : sudo nmap -sS -sV -Pn 2048gamer.com -p-

<img src="/Mobil/Mobil400/Resimler/port.png" width="350" height="200"/>

Tarama sonucunda 2048 nolu porun açık olduğunu gördük. Tarayıcıdan 2048gamer.com:2048 adresini ziyaret ettiğimizde flag karşınıza çıkacaktı.


