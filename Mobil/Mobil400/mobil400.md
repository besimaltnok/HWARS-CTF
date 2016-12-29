### Hacking Wars CTF - Mobile400 - MSN

Bu yazıda sizlere Hacking Wars CTF inde yer alan mobile 400 MSN sorusunun çözümünden bahsediyor olacağım.

APK dosyasını indirip telefona kurduysanız aşağıdaki gibi bir ekran ile karşılaşmışsınızdır.

--Resim eklenecek

Buraya ilgili verileri yazıp bir proxy aracılığı ile dinlemeye çalıştıysanız. Büyük ihtimal hiçbir veri görmeyeceksiniz. SSLPinning için gerekli bir araç kullansanız dahi yaptığınız işlem başarısız olacaktır.

Bu nedenle APK dosyasını decompile edip incelemek istedim. Bunun için aşağıdaki komutu kullandım.

* Komut : apktool d msn.apk

Bu işlem sonunda aşağıdaki içeriğe sahip bir klasör elde etmeniz gerekecektir.

--Resim eklenecek

Kodları incelemek için bir editör kullanabilirsiniz. Benim tercihim sublime oldu.

--Resim eklenecek-sublime

İnceleme sonucunda güvenli bir ieltişim kullanamak amacı ile kendi sertifikalarını kullandıklarını görebilirsniz.

--Resim eklenecek

Bunu görmenizin diğer bir yoluda direk assest klasörü altına bakmanızdır. Çünkü sertifikalar genelde burada saklanmaktadır.

--Resim eklenecek

Şimdi bu bilgiyi elde ettikten sonra yapmamaız gereken şey onların kullandıkları formatta burp aracona ait sertikayı üretmek ve aynı isimde oluşturulan bu sertifikayı orjinali ile değiştirerek apk dosyasını tekrar derlemek. Bunun için ilk olarak Firefox tarayaıcımıza import ettiğimiz sertifika dosyamızı aynı isimde çıkarıyoruz.

*  Tercihler - Gelişmiş - Sertifikalar - Sertitikaları göster

Burdan gerekli sertitika export edilir. (X.509(PEM))

--Resim eklenecek

Elde edilen sertitika assest kalsöründeki sertifika ile değiştirilir ve APK dosyası tekrar derlenir.

* Komut : apktool b msn -o hacking.apk

Ancak bunu bu şekilde yüklemeye çalışırsanız APK dosyası çalışmayacaktır. Bu nedenle APK dosyasını imzalamanız gerekmektedir. Bunun için  de aşağıda tanımlanan komut kullanılabilir.

* Komut : java -jar APktool/signapk.jar APktool/certificate.pem APktool/key.pk8 hacking.apk wars.apk

Bu işlemden sonra dosyayı cihazınıza yükleyin ve cihazın proxy ayarlarını yapın.

Proxy ayarları için aşağıdaki adımları takip edebilirsiniz.

-Resimler eklenecek

