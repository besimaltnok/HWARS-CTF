### Hacking Wars CTF - Mobile400 - MSN

Bu yazıda sizlere Hacking Wars CTF inde yer alan mobile 400 MSN sorusunun çözümünden bahsediyor olacağım.

APK dosyasını indirip telefona kurduysanız aşağıdaki gibi bir ekran ile karşılaşmışsınızdır.

<img src="/Mobil/Mobil400/Resimler/ilkkurulum.png" width="350" height="300"/>

Buraya ilgili verileri yazıp bir proxy aracılığı ile dinlemeye çalıştıysanız. Büyük ihtimal hiçbir veri görmeyeceksiniz. SSLPinning için gerekli bir araç kullansanız dahi yaptığınız işlem başarısız olacaktır. Bunun nedeni kullanılacak sertifikanın tanımlanmış olma olasılığıdır.

Bu nedenle APK dosyasını decompile edip incelemek istedim. Bunun için aşağıdaki komutu kullandım.

* Komut : apktool d msn.apk

Bu işlem sonunda aşağıdaki içeriğe sahip bir klasör elde etmeniz gerekecektir.

<img src="/Mobil/Mobil400/Resimler/apk.png"/>

İnceleme sonucunda güvenli bir ieltişim kullanamak amacı ile kendi sertifikalarını kullandıklarını görebilirsniz.Bununiçin de assest klasörü altına bakmanız gerekecektir. Çünkü sertifikalar genelde burada saklanmaktadır.

<img src="/Mobil/Mobil400/Resimler/sertifikaresmi.png" height=150/>

Şimdi bu bilgiyi elde ettikten sonra yapmamaız gereken şey onların kullandıkları formatta burp aracona ait sertikayı üretmek ve aynı isimde oluşturulan bu sertifikayı orjinali ile değiştirerek apk dosyasını tekrar derlemek. Bunun için ilk olarak Firefox tarayaıcımıza import ettiğimiz sertifika dosyamızı aynı isimde çıkarıyoruz.

*  Tercihler - Gelişmiş - Sertifikalar - Sertitikaları göster

Burdan gerekli sertitika export edilir. (X.509(PEM))

<img src="/Mobil/Mobil400/Resimler/burpsertitikası.png" width="350" height="200"/>

Elde edilen sertitika assest kalsöründeki sertifika ile değiştirilir ve APK dosyası tekrar derlenir.

* Komut : apktool b msn -o hacking.apk

Ancak bunu bu şekilde yüklemeye çalışırsanız APK dosyası çalışmayacaktır. Bu nedenle APK dosyasını imzalamanız gerekmektedir. Bunun için  de aşağıda tanımlanan komut kullanılabilir.

* Komut : java -jar APktool/signapk.jar APktool/certificate.pem APktool/key.pk8 hacking.apk wars.apk

Bu işlemden sonra dosyayı cihazınıza yükleyin ve cihazın proxy ayarlarını yapın.

Proxy ayarları için aşağıdaki adımları takip edebilirsiniz.

<img src="/Mobil/Mobil400/Resimler/proxyayari.png" width="350" height="200"/>

