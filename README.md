# Ses Sentezi
 1. PROJENİN AMACI VE ÖZETİ:
 Bu projenin amacı, kullanıcının girdi olarak sağladığı bir dizi notayı ses dalgaları ile temsil edip bu ses dalgalarını sentezleyerek melodiyi oluşturmaktır. Bu işlem, kullanıcıya melodinin sesini dinleme ve aynı zamanda ses dalgasının grafiksel bir gösterimini gözlemleme fırsatı sunar.
 
 2. KULLANILAN YÖNTEMİN TEORİSİ:
 Projede kullanılan temel yöntem, sinüs dalgası sentezi olarak bilinen bir ses sentezleme tekniğidir. Bu teknik, seslerin çeşitli frekanslardaki sinüs dalgalarının birleşimi olduğu temelinde çalışır. Her bir nota, belirli bir frekansta bir sinüs dalgası ile temsil edilir. Ses sentezlemek için, notaların belirtilen süreler boyunca çalınmasını sağlayan sinüs dalgaları oluşturulur ve birleştirilir.

 Bu teknik, dijital ses işlemenin temel prensiplerinden biri olan Fourier teorisine dayanmaktadır. Fourier teorisi, herhangi bir sinyalin farklı frekansta sinüs ve kosinüs dalgalarının toplamı olarak ifade edilebileceğini belirtir.

 a. SES SENTEZİ:
 Bu projede, dalga biçimi sentezi yöntemlerinden biri olan "Additive Synthesis" (Toplamsal Ses Sentezi) kullanılmıştır. Toplamsal sentez, farklı frekans ve genliklere sahip bir dizi sinüs dalgasının toplanması ile sesin oluşturulduğu bir yöntemdir. Bu projede, her bir nota için belirli bir frekansa sahip bir sinüs dalgası oluşturulmuş ve bu sinüs dalgaları toplanarak melodiyi oluşturmuştur.
 
 b. FİZİKSEL MODEL:
 Fiziksel modellemeye gelince, bu projede belirgin bir fiziksel modelleme yöntemi kullanılmamıştır. Fiziksel modelleme, genellikle belirli bir müzik aletinin veya ses olayının fiziksel özelliklerini ve davranışlarını simüle etmek için kullanılır. Bu projede ise sinüs dalgalarının frekansları doğrudan belirlenmiş nota frekanslarından alınmıştır ve her bir nota belirli bir süre boyunca çalınmıştır. Dolayısıyla, bu projede belirgin bir fiziksel modelleme yöntemi kullanılmamıştır. Ancak, genel anlamda ses dalgalarının fiziksel özellikleri ve sesin nasıl üretildiği ve iletilmesiyle ilgili temel prensipler bu projede uygulanmıştır.
 
 Özetlemek gerekirse, bu projede "Additive Synthesis" kullanılmış, ancak belirgin bir fiziksel modelleme yöntemi kullanılmamıştır. Bunun yerine, ses dalgalarının temel fiziksel prensipleri ve sinüs dalgaları kullanılarak sesin nasıl üretileceği ile ilgili temel prensipler uygulanmıştır.

  3. PROJEDE İZLENEN PROSEDÜRLER VE AÇIKLAMALAR:
  A. Kütüphanelerin İmport Edilmesi: Projede gerekli olan kütüphaneler import edilmiştir. Bu kütüphaneler arasında numpy (sayısal hesaplama yapmak için), sounddevice (sesi çalmak için), matplotlib (ses dalgasını görselleştirmek için) ve scipy (sesi .wav dosyası olarak kaydetmek için) bulunmaktadır.
 
  a. Numpy:
  Numpy (Numerical Python), geniş bir matematiksel hesaplama araçlarına sahip olan bir Python kütüphanesidir. Numpy, çok boyutlu dizileri, matrisleri ve bu veri yapıları üzerinde çalışmak için gelişmiş matematiksel ve mantıksal işlemleri destekler. Bu projede, Numpy'nin çeşitli özelliklerini kullanıyoruz. İşte bazıları:
   * np.linspace: Belirtilen başlangıç ve bitiş noktaları arasında eşit aralıklı sayılar oluşturur. Bu, sinüs dalgası oluştururken zaman serisi oluşturmak için kullanılır.
   * np.sin: Her bir öğenin sinüsünü hesaplar. Sinüs dalgası oluşturmak için kullanılır.
   * np.append: İki dizi veya iki öğeyi birleştirir. Melodinin oluşturulmasında, her nota
 için oluşturulan ses dalgaları bir araya getirilir.
   * np.max, np.abs: Maksimum ve mutlak değer işlemleri için kullanılır. Ses dalgasını
 normalleştirmek için kullanılır.
 
  b. Sounddevice:
  Sounddevice, Python'da ses kaydı ve oynatma işlemlerini gerçekleştirmek için kullanılan bir kütüphanedir. Bu projede, oluşturduğumuz ses dalgasını çalmak için sd.play fonksiyonunu kullanıyoruz.
 
  c. Matplotlib:
  Matplotlib, Python'da grafik oluşturmayı sağlayan bir kütüphanedir. 2D ve 3D grafikler, dağılım grafikleri, histogramlar, bar grafikleri ve daha birçok şey oluşturmak için kullanılabilir. Bu projede, oluşturulan ses dalgasının zaman serisini görselleştirmek için kullanılıyoruz.
 
  d. Scipy:
  Scipy (Scientific Python), bilimsel ve teknik hesaplamaları desteklemek için geniş bir kütüphaneye sahip bir Python modülüdür. Scipy, Numpy dizileri üzerinde çalışır ve Numpy paketini tamamlar. Bu projede ise scipy'nin wavfile modülünü kullanıyoruz. Bu modül, ses dosyalarını okuma ve yazma işlevlerini sağlar. Projemizde, sentezlediğimiz sesi bir .wav dosyası olarak kaydetmek için bu modülü kullanıyoruz.
 
  B. Örnekleme Hızının Tanımlanması: Örnekleme hızı (sample rate), sesin saniyede kaç kez örneklendiğini belirler. Genelde ses dosyaları için kullanılan standart bir örnekleme hızı olan 44100 Hz kullanılmıştır.
  
  C. Nota Frekanslarının Sözlüğünün Oluşturulması: Nota adları ve frekansları arasındaki ilişkiyi belirleyen bir Python sözlüğü oluşturulmuştur. Bu sözlük, kullanıcının gireceği notaların frekanslarını bulmak için kullanılır.
   * 'A', 'B', 'C', 'D', 'E', 'F', ve 'G': Müzikal notaları temsil eder.
    * 'A': La notasını
    * 'B': Si notasını
    * 'C': Do notasını
    * 'D': Re notasını 
    * 'E': Mi notasını 
    * 'F': Fa notasını 
    * 'G': Sol notasını
  * Rakamlar (örneğin 4, 5, 6): Oktavı belirtir. Büyüdükçe, sesin frekansı da iki katına çıkar. Örneğin, A4 notasının frekansı 440 Hz'dir, A5'in frekansı ise 880 Hz'dir.
  * '#' (diyez işareti): Bir notanın yarım ton yukarısını ifade eder. Örneğin, 'A#4' A4 notusunun yarım ton yukarısıdır ve frekansı A4'ten daha yüksektir.
  * 'b' (bemol işareti, burada görünmüyor ancak genel müzik notasyonunda kullanılır): Bir notanın yarım ton aşağısını ifade eder.
  
  Bu etiketler, batı müziği notalarını temsil eder. Her bir harf, bir müzik notasını temsil eder ve sonrasında gelen sayılar ve semboller, notanın hangi oktavda olduğunu ve hangi varyasyonunu belirtir. farklı notaların ve tonların belirli frekanslara karşılık geldiği bir sistem oluşturur. Bu proje özelinde, kullanıcıdan alınan notaların frekans değerlerini belirlemek ve bu frekanslarla ses dalgaları oluşturmak için kullanılırlar.
 
  D. Kullanıcıdan Nota ve Süre Girişinin Alınması: Kullanıcının çalmak istediği notalar ve bu notaların süreleri, kullanıcıdan alınır ve uygun veri yapılarına dönüştürülür.
 
  E. Melodinin Oluşturulması: Her bir nota ve süresi için sinüs dalgası sentezlenir ve bu dalga genel melodiye eklenir.
  
  F. Ses Dalgasının Normalleştirilmesi: Oluşturulan ses dalgası, kulaklık veya hoparlörler üzerinden çalındığında  herhangi bir hasara neden olmayacak şekilde normalleştirilir.
  
  G. Sesin Çalınması: Melodinin sesi, sounddevice kütüphanesi kullanılarak çalınır.
  
  H. Ses Dalgasının Görselleştirilmesi: Oluşturulan ses dalgası, matplotlib kütüphanesi kullanılarak bir grafik üzerinde görselleştirilir.
  
  I. Sesin .wav Dosyası Olarak Kaydedilmesi: scipy kütüphanesinin wavfile modülü kullanılarak ses, bir .wav dosyası olarak kaydedilir. Bu, sesin daha sonra tekrar çalınabilmesini sağlar.
 
 Her bir adım, belirli bir amaca hizmet eder ve projenin genel hedefi olan ses sentezlemeyi gerçekleştirmek için bir araya gelir.
