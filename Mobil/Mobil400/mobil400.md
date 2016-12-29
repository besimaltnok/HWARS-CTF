### Hacking Wars CTF - Mobile400 - MSN

Bu yazıda sizlere Hacking Wars CTF inde yer alan mobile 400 MSN sorusunun çözümünden bahsediyor olacağım.

APK dosyasını indirip telefona kurduysanız aşağıdaki gibi bir ekran ile karşılaşmışsınızdır.

<img src="/Mobil/Mobil400/Resimler/ilkkurulum.png" width="350" height="300"/>

Buraya ilgili verileri yazıp bir proxy aracılığı ile dinlemeye çalıştıysanız, büyük ihtimal hiçbir veri görmeyeceksiniz. 

Ben size burda kullanabilecceğiniz iki method önerebilirim. Ancak ben ikincisini kullandım.

İlki bazı moduller kullanarak SSLUnPinning yapmaktır. Bu işlem için de Xposed Freamwork içerisinde bulabileceğiniz SSLUnpinning modülünü kullanabilirsiniz. 

Xposed Freamwork kurulumu ve modüller hakkında bilgiler:

 * Xposed Freamwork için gerekli apk dosyası ve modülleri hakkında bilgiye aşağıdaki adreslerden erişebilirsiniz:
  - http://repo.xposed.info/module/de.robv.android.xposed.installer
  - http://www.meryemakdoğan.com/xposed-ve-modulleri/
  
<img src="/Mobil/Mobil400/Resimler/ssl.png"/>


Diğer bir yöntemde bu işlemi manuel yöntemler ile yapmaktır.Bu işlem için amacımız kendi sertifikamızı apk dosyasına yerleştirmektir.

Bu nedenle APK dosyasını decompile edip incelemek istedim. Bunun için aşağıdaki komutu kullandım.

* Komut : apktool d msn.apk

Bu işlem sonunda aşağıdaki içeriğe sahip bir klasör elde etmeniz gerekecektir.

<img src="/Mobil/Mobil400/Resimler/apk.png"/>

İnceleme sonucunda güvenli bir iletişim kullanmak amacı ile kendi sertifikalarını kullandıklarını görebilirsniz.Bunun için de assest klasörü altına bakmanız gerekecektir. Çünkü sertifikalar genelde burada saklanmaktadır.

<img src="/Mobil/Mobil400/Resimler/sertifikaresmi.png" height=150/>

Şimdi bu bilgiyi elde ettikten sonra yapmamız gereken şey onların kullandıkları formatta burp aracına ait sertikayı üretmek ve aynı isimde oluşturulan bu sertifikayı orjinali ile değiştirerek apk dosyasını tekrar derlemek. Bunun için ilk olarak Firefox tarayıcımıza import ettiğimiz sertifika dosyamızı aynı isimde çıkarıyoruz. 

Bu işlem için aşağıdaki yol izlenebilir :

*  Tercihler - Gelişmiş - Sertifikalar - Sertifikaları göster

Burdan gerekli sertifika export edilir. (X.509(PEM))

<img src="/Mobil/Mobil400/Resimler/burpsertitikası.png" width="350" height="200"/>

Elde edilen sertifika assest kalsöründeki sertifika ile değiştirilir ve APK dosyası tekrar derlenir.

* Komut : apktool b msn -o hacking.apk

Ancak bunu bu şekilde yüklemeye çalışırsanız APK dosyası çalışmayacaktır. Bu nedenle APK dosyasını imzalamanız gerekmektedir. Bunun için  de aşağıda tanımlanan komut kullanılabilir.

* Komut : java -jar APktool/signapk.jar APktool/certificate.pem APktool/key.pk8 hacking.apk wars.apk

Bu işlemden sonra dosyayı cihazınıza yükleyin ve cihazın proxy ayarlarını yapın.

Proxy ayarları için aşağıdaki adımları takip edebilirsiniz.

<img src="/Mobil/Mobil400/Resimler/proxyayari.png" width="350" height="200"/>

Eğer tüm işlemleri sorunsuz yerine getirdiyseniz : Yolladığınız isteğe dönen cevapta flag için gerekli bilginin geldiğin göreceksinizdir.

<img src="/Mobil/Mobil400/Resimler/flag.jpg" width="400" height="300"/>

