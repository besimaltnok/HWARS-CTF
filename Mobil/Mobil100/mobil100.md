### Hacking Wars CTF - Mobile100 - APK Internals

Bu yazıda sizlere Mobile 100 sorusunda izlenen yöntemden bajsedeceğim.

İlk olarak dosyanın java kodlarına erişmemiz gerekmektedir. Çünkü APK dosyasını çalıştırdığımızda bize kaynak kodu ile ilgili bir bilgi vermekteydi.

- Resim eklenecek

Kaynak koda erişmek için ihtiyacımız olan araçlar : 

* Dex2Jar
* JD-GUI   : https://github.com/java-decompiler/jd-gui/releases/download/v1.4.0/jd-gui-1.4.0.jar

Daha sonra aşağıdaki komut çalıştırılarak .jar dosyası elde edilir.

* Komut : dex2jar mobile1.apk

Bu işlemden sonra elde edilen dosya jd-gui ile açılır. Ama ondan önce jd-gui çalıştırmamız gerekmektedir.

* Komut : java --jar jd-gui.jar

-- Resim eklenecek

Bu işlemden sonra Display.class incelendiğinde, aşadıdaki giib bir string görüceksiniz. Aslında çok karmaşaya girmeden bunu alıp decode ettiğinizde bir resim url adresi ile karşılaşacaksınız.

-- Resim eklenecek

Bu resim  Pablo Neruda'ya ait ve bunu pablo.neruda şeklinde yazdığınızda sonuca ulaşmış olacaktınız.

-- Resim eklenecek
