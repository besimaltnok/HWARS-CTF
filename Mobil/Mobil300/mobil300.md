### Hacking Wars CTF - Mobile300 - OTP

Bu soruda da Meryem AKDOĞAN isimli takım arkadaşımın emeği büyüktür. O olmasaydı bu soru gitmiş olabilirdi :)

Bu soruda uygulamanın ilk olarak istenilen android versiyonunda çalıştırılması gerekiyordu. Uygulamanın Manifest dosyasında da bunu görebilirdiniz.
Bu nedenle soruda bir versiyon bağımlılığı vardı v eherkeste soru doğru adımlar ile çözülse de farklı sonuçlar ortaya çıkarıyordu.

Ancak daha sonra yarışma ekibi tarafından bu sorun giderildi.

Sorun giderildikten sonra uygulamayı cihaza kurup çalışıtırdığınızda aşağıdaki gibi bir ekran ile karşılaşacaktınız ve yaptığınız her "click" işlemi için farklı sonuçlar doğacaktı.
Bu aşamadan sonra tekrar kaynak kod üzerinde çalışma yaptığınızda "counter" isimli bir değerin okunduğu ve size çıktı verdiğini anlıyordunuz.

 <img src="/Mobil/Mobil400/Resimler/ilk2.jpg"/>

Uygulamanın kurulu olduğu cihazdan oluşturduğu dosyalar çekilip incelendiğinde shared_preferences üzerinde bu değişkenin tutulduğu görülmekteydi.

 * Dosyaları şekmek için:
  - Komut : adb pull /data/data/com.ctf.mobile2
  
 <img src="/Mobil/Mobil400/Resimler/adbpull.jpg"/>

 * Dosyanın ilk hali:
 
<img src="/Mobil/Mobil400/Resimler/2.jpg"/>

İstenildiği gibi bu değer 666666 yapıp tekrar cihaza aktarmamız gerekiyordu.

 * Dosya düzenlendikten sonra: 
 
<img src="/Mobil/Mobil400/Resimler/666666.jpg"/>

 * Dosyaları atmak için:
  - Komut : adb push "atılacak_dosyanın_tam_yolu" /data/data/com.ctf.mobile2
  
 <img src="/Mobil/Mobil400/Resimler/adbpush.jpg"/>

Bu değişiklik yapıldıktan sonra cihaz kapatılıp tekrar açıldığında ve uygulama başlatıldığında : üretilen değer aradığımız flag olacaktı.

* Flag : 

<img src="/Mobil/Mobil400/Resimler/son666666.jpg" width="350" height="300"/>
