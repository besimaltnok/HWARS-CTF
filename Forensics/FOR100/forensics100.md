### Hacking Wars CTF - Forensics - Exploit Broker

Bu yazıda yarışma da bize verilen bir pcap dosyasını analiz edeceğiz. Soruda bizden, 8.8 BTC aktarılan hesabı bulmamız isteniyordu.

Bu kapsamda bir pcap dosyası analiz ederken neler ile karşı karşıya olduğunuzu anlamak adına kullanabileceğiniz bir kaç araç vardır, benim önerebileceğim.

Ancak bilmemiz gerekn şey şu: 
 * Protocol hierarchy
  - Bu bilgi, pcap dosyası içerisinde ki genel yapı ve içerik hakkında bilgi vermektedir.
 * Pcap ieçrisinde ki dosyalar
 * Ziyaret edilen url adresleri gibi bilgiler analiz aşaması için çok önemlidir.
 
 
 Bu nedenle bende ziyaret edilen URL adreslerini analiz ettim.
 
 * 0day.today
 * blockchain.info gibi bilgileri elde ettim.
 
 0day today üzerinden herhangi bir veriye erişim olmicaktı. Asıl odaklanmamız gereken adres blockchain.info adresiydi.
 
 Biraz daha ilerlemek adına: trafik içerisinde yer alan dosyaları export edebilirdik. 
 Bu işlem için 3 yöntem kullanabilirsiniz: 
 
 İlk yöntem foremost aracı ile bilgileri çıkarmak:
  * Komut: foremost -T dosyaismi
  
 <img src="/Mobil/Mobil400/Resimler/foremost.png"/>
 
 
 İkinci yöntem wireshar aracı ile:
  * Bunun için File -> Export Objects -> HTTP yolunu takip edebiliriz.
  
  <img src="/Mobil/Mobil400/Resimler/export.png"/>
 
 
 Üçüncü yöntem olarak da "NetworkMiner" aracını tercih edebilirsiniz. Yapmanız gerekn tek şey analiz edilmesini istedğiniz dosyayı sürüklemektir.
 
  <img src="/Mobil/Mobil400/Resimler/networkminer.png"/>
  
  
 
 Son yöntemde görüldüğü üzere bir qr code var . Bu qr okutulduğunda şöyle bir değer elde edilecektir.
 
 <img src="/Mobil/Mobil400/Resimler/BTC.png"/>
 
 
 Ancak aradığımız değer bu değil. Bu değeri google üzerinden arattığımızda bitcoinchain.com üzerinden bu hesaba ait transfer işlemlerini görebiliyorduk. Bu transfer işlemleri incelenip belirtilen değerde aktarım yapılan hesap tespit edilebiliyordu.
 
 
 
 
 
 
