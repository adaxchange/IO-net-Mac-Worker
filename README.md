# IO-net-Mac-Worker

> Solana üzerinde inşa edilen 'internet of gpus' dePIN projesi IO net için worker kuralım.

> Sağ yukarıdan starlayarak repoya destek verebilirsiniz.

> Sayfanın en alt kısmında sık sorulan soruları ve yapılması gerekenleri cevapladım göz atabilirsiniz.

> İlk olarak kurulum yapabilmek için Mac cihazlarımızın silikon işlemcilerden M1 ve sonrası olması yeterli.

> Worker konusunu iki bakımdan inceleyebiliriz: Airdrop ve İş.
  
> Bilgisayarımıza kurduğumuz nodeler sayesinde bilgisayarımızın donanımını başka kişilere kiralamış oluyoruz; bu iş oluyor. Worker'ın çalışma amacı da bu.

  # Kurduğumuz worker'ler iş alırsa IO-net projesinden daha fazla airdrop kazanacağız.
> Worker'in iş alması veya aldığı işi tamamlayabilmesi için işlemci gücü yeterli olmuyor. Burada devreye ram, internet hızı faktörleri devreye girer.
  
> Mac cihazlarda iş alınıp tamamlanabilmesi için önerilen internet upload hızı 250mbit ve ram ise 16GB.
  
> Fakat bunlar gözünüzü korkutmasın. Worker kurmanın tek amacı iş alabilmek değil, burada da airdrop devreye giriyor.
#
#



> Airdrop alabilmek için worker kurmuş olmamız yeterli olacak. Fakat bazı kriterler elbette var.

> Öncelikle donanım özellikleri olarak bir çarpan sistemi var. Şanslıyız ki Mac cihazlar bu listenin başlarında.
  
> Sonrasında insanlar internet hızlarına göre tierlere ayrılacak ve çarpan olacak.
  
  # En önemli kriter ise Uptime yani worker'in çalışma süresi. Bu yüzden erken çalıştırmak ve uzun süre açık tutmak çok önemli.
  #
  # Worker kurulumu
  İlk olarak [buraya](https://cloud.io.net/cloud/home) girip kayıt olalım.
  
  Sonrasında sol üstte io cloud yazan yere gelip oradan worker'i seçelim.
  
  Üst kısımdan 'Connect new worker' kısmına girelim.
  
  Operating sistem olarak mac OS'yi, supplier olarak io.neti seçtikten sonra cihazımıza bir isim verelim. Ne olduğu farketmez.
  
  Device type olarak cpu'yu seçelim.

  Sayfa kenarda açık kalsın, biz [docker](https://www.docker.com/products/docker-desktop/) sayfasına gidip Download for Mac - Apple Chip diyelim.

  Docker'i indirip kuralım.

  Kurduktan sonra uygulamaya girdiğimizde 'Another application changed your Desktop configurations. This may cause unexpected behaviour and errors.' hatasıyla karşılaşabiliriz. Bir şey yapmamıza gerek yok kalsın.

  Şimdi Mac'imizin uygulamalar kısmına terminal yazalım ve terminal'e girelim.

  Girdikten sonra kenarda bıraktığımız io.net sitesine tekrar geçelim ve oradaki kodların bir tanesini yapıştırıp enterleyip diğerine geçeceğiz.

  Aşağıdaki kodların birini yazıp enterleyip sonra diğerine geçiniz lütfen.

  ```console
  curl -L https://github.com/ionet-official/io_launch_binaries/raw/main/launch_binary_mac -o launch_binary_mac

  chmod +x launch_binary_mac

  Son olarak da size verilen 'Run the command to connect the device' kısmındaki kodu yapıştırıp enterleyin.

  VE BU 3. YANİ SON KODU LÜTFEN BİLGİSAYARINIZDA NOT DEFTERİNDE SAKLAYIN. SONRADAN WORKER'I RESTART ETMEMİZ GEREKTİĞİNDE VESAİRE BİZE GEREKECEK.
```

  Worker kurma işlemimiz bitmiştir. İo'net sitesinde sayfayı yenileyerek durumu kontrol edebilirsiniz. Maksimum yarım saat içerisinde yeşile dönmeli ve 'Running' yazmalı. Turuncu bir şekilde 'Idle' olarak güzüküyorsanız worker'ınız hazır ve boşta demektir.

  Ayrıca indirdiğimiz docker uygulamasında da container kısmında 2, images kısmında 3 farklı şey olmalı. Bunları da kontrol ediniz yarım saat sonra.

  # RESTART

> Worker'imiz internet kopma sorunları veya başka sorunlar nedeniyle 'Failed' 'Inactive' konumuna geçebilir. Böyle olduğu takdirde bir süre bekleyip düzelmezse workeri yeniden başlatmamız gerekiyor.

Bunun için ilk olarak docker uygulamasına girip Containers ve Images kısmındaki her şeyi silelim. Daha sonrasında sol alttaki üç noktadan dockeri restartlayalım.

Daha sonrasında pc'yi restartlayalım ve size yukarıda not defterinde saklayın dediğim 3. kodu terminali açıp tekrar yapıştırın. Sadece 3. kodu. Ve bir süre sonra worker'iniz tekrar aktif hale gelecektir.

# WORKER'I TAMAMEN SİLMEK

> Worker'i bazı durumlarda tamamen silmemiz gerekebilir. Bu durumlar workeri bir türlü kuramadığımız ve hatalardan kurtulamadığımız zamanlar olabilir.

Bunun için io.net sitesinde workerinize gelip 'terminate' kısmından dockeri terminate ediniz.

Sonrasında docker uygulamamıza gelip containers ve image kısmındaki her şeyi silelim.

Terminale aşağıdaki kodu girip enterleyelim.

docker stop && $(docker ps -aq) && docker rm -fv $(docker ps -aq) && docker system prune -af

Son olarak docker uygulamasında sol alt köşeden restartlayalım, pcyi restartlayalım ve bütün kurma işlemlerini baştan gerçekleştirelim. Tertemiz bir yeniden kurulum.

# BAZI YAPILMASI GEREKENLER VE SIK SORULAN SORULAR

> Proje sitesinde arayüz sorunları yaşandığından uptime skorları ve benzeri fonksiyonlar çalışmayabiliyorlar. Burada önemli olan sizin yeşil olmanız.

> Nisan ayının başında arayüzün düzeltilmesi ve airdrop puanlarımızın hesaplanıp sitede gösterilmesi planlanıyor.

> Workerimizin kesilmemesi için bilgisayarımız 7/24 açık kalmalı. Şimdi bunun için bazı ayarlar yapalım.

Sistem Ayarları - Kilitli Ekran menüsüne gelip oradaki ekran koruyucu ve ekranı kapatma ayarlarını 'Asla' yapalım.

Sonrasında Sistem Ayarları - Pil menüsüne gelip 'Seçenekler' diyelim. Uyku durumuna geçmesini engelleyi açıp, sabit diskleri uyku moduna geçiri 'Asla' yapalım.

> Birden fazla cihazım var ve birden fazla worker kurmak istiyorum ne yapmalıyım? Birden fazla worker kurabilirsiniz fakat bu workerleri lütfen sadece bir tane io.net hesabının altında kurun.

> Evet mac cihazlar şu anda iş alamıyor kısa bir süre sonra gerçekleşecek güncellemeyle iş almaya başlayacaklar.

 Karşılaşılan hatalar geldikçe buraya eklenecektir. Komüniteye katılmak için [discord](https://discord.com/invite/ionetofficial) sunucusuna gelebilirsiniz.
