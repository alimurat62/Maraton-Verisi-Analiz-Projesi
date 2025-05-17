# Maraton Verisi Analiz Projesi

## Proje Özeti
2010-2019 yılları arasında gerçekleştirilen 96 farklı maraton yarışına ait yaklaşık 2 milyon satırlık veri kullanılarak yapılan kapsamlı analiz projesidir. Veri ön işleme, keşifsel veri analizi (EDA), yarış bazlı analizler, koşucu profili incelemeleri, korelasyon ve etkileşim analizleri ile kümeleme analizleri adım adım gerçekleştirilmiştir. Elde edilen bulgular, maraton performansının demografik ve yarış bazlı faktörlerle ilişkisini ortaya koymakta ve ileri analizler için sağlam bir temel oluşturmaktadır.

---

## İçindekiler

1. [Veri Ön İşleme](#veri-ön-işleme)  
2. [Keşifsel Veri Analizi (EDA)](#keşifsel-veri-analizi-eda)  
3. [Yarış Bazlı Analizler](#yarış-bazlı-analizler)  
4. [Koşucu Profili Analizleri](#koşucu-profili-analizleri)  
5. [Korelasyon ve Etkileşim Analizleri](#korelasyon-ve-etkileşim-analizleri)  
6. [Kümeleme Analizleri](#kümeleme-analizleri)  
7. [Genel Değerlendirme](#genel-değerlendirme)  

---

## 1. Veri Ön İşleme

### 1.1 Veri Yükleme ve Genel Bilgi  
2010-2019 yılları arasında düzenlenen 96 farklı maraton yarışına ait yaklaşık 2 milyon satırlık veri seti yüklendi. Veri setinde toplam 7 sütun bulunmaktadır:  
- **Race:** Yarış adı  
- **Year:** Yarışın düzenlendiği yıl  
- **Name:** Koşucunun adı  
- **Gender:** Koşucunun cinsiyeti  
- **Age:** Koşucunun yaşı  
- **Finish:** Bitirme süresi (saniye cinsinden)  
- **Age Bracket:** Yaş aralığı kategorisi

### 1.2 Eksik Değerlerin Tespiti ve Düzenlenmesi  
- **Name** sütununda 2 eksik değer tespit edildi. Bu boşluklar `Unknown` olarak dolduruldu.  
- **Gender** sütununda 8 eksik değer bulundu; bu eksikler sütunun mod (en sık gözlenen değer) ile tamamlandı.  
- **Age** sütunundaki mantıksal tutarsızlıklar (negatif, aşırı küçük veya büyük yaşlar) tespit edildi. 13 ile 100 arası yaş sınırı kabul edildi, bu aralığın dışındaki yaş değerleri NaN yapıldı.  
- Eksik yaşlar, ait oldukları yaş aralığı grubunun medyan yaşı ile dolduruldu.

### 1.3 Uç Değer (Outlier) Analizi  
- Bitirme süresi (Finish) sütununda aşırı uç değerler tespit edildi.  
- IQR (Interquartile Range) yöntemi kullanılarak alt ve üst sınırlar belirlendi. Bu sınırların dışındaki değerler aykırı olarak kabul edildi.  
- Aykırı değerler üzerinde iki ayrı işlem yapıldı:  
  - Aykırı değerler tamamen veri setinden çıkarıldı.  
  - Winsorizing yöntemi uygulanarak uç değerler alt ve üst sınırlarla kırpıldı.  
- Orijinal, temizlenmiş ve winsorize edilmiş veri setlerinin ortalama ve dağılım özellikleri karşılaştırılarak görselleştirildi.

---

## 2. Keşifsel Veri Analizi (EDA)

### 2.1 Dağılım Görselleştirmeleri  
- Bitirme süresi, yaş ve cinsiyet dağılımları histogramlar ve sayım grafikleri ile görselleştirildi.  
- Yaş dağılımı, maraton koşucularının ağırlıklı olarak 13-100 yaş aralığında olduğunu gösterdi.  
- Cinsiyet dağılımında erkek katılımcıların kadınlara göre daha fazla olduğu tespit edildi.

### 2.2 Bitirme Süresi Analizleri  
- Cinsiyet bazında ortalama bitirme süreleri hesaplandı ve karşılaştırıldı; erkek ve kadın koşucular arasında anlamlı süre farklılıkları gözlendi.  
- Yaş aralıklarına göre ortalama bitirme süreleri hesaplandı ve grafikle sunuldu.  
- Hem cinsiyet hem de yaş aralığına göre gruplanmış ortalama süreler detaylı analiz edildi.

### 2.3 Zaman Serisi İncelemeleri  
- Yıllara göre düzenlenen maraton sayıları ve katılımcı sayıları analiz edildi.  
- Yıllık ortalama bitirme sürelerinde zamanla değişim ve trendler gözlemlendi.  
- Cinsiyet bazında yıllık ortalama bitirme süreleri karşılaştırıldı.  
- Yıl bazında cinsiyet dağılımları analiz edilerek kadın ve erkek katılımcı sayılarının yıllar içindeki değişimi ortaya kondu.

---

## 3. Yarış Bazlı Analizler

### 3.1 En Popüler 10 Yarışa Göre Ortalama Bitirme Süresi  
- Veri setinde en yüksek katılımcıya sahip 10 yarış seçildi.  
- Bu yarışların katılımcılarına ait ortalama bitirme süreleri hesaplanarak, yarışlar ortalama sürelerine göre sıralandı.  
- Sonuçlar yatay çubuk grafiklerle görselleştirildi.  
- Böylece en popüler yarışların performans seviyeleri karşılaştırılmış oldu.

### 3.2 En Hızlı ve En Yavaş 3 Yarış  
- Tüm maratonların ortalama bitirme süreleri hesaplandı.  
- En hızlı (ortalama en kısa süreye sahip) ve en yavaş (ortalama en uzun süreye sahip) 3’er yarış seçildi.  
- Bu 6 yarışın ortalama süreleri renk kodlu yatay çubuk grafiklerle karşılaştırıldı.

### 3.3 İlk 10 Yarış İçin Katılımcı Sayısı  
- En popüler 10 yarış için toplam katılımcı sayıları hesaplandı ve yarış isimlerine göre dikey çubuk grafikle sunuldu.  
- Böylece hangi yarışların daha fazla katılımcı çektiği net şekilde görüldü.

### 3.4 En Popüler 10 Yarış İçin Cinsiyet Dağılımı  
- Bu yarışlarda kadın ve erkek katılımcı sayıları ayrı ayrı hesaplandı.  
- Cinsiyet dağılımı yığılmış çubuk grafiklerle görselleştirildi.  
- Analiz, yarışlardaki cinsiyet dengesi hakkında bilgi verdi.

### 3.5 En Popüler 10 Yarış İçin Yaş Ortalaması  
- Yarışlardaki koşucuların ortalama yaşları hesaplandı.  
- Yaş ortalamaları dikey çubuk grafiklerle yarışlara göre karşılaştırıldı.  
- Katılımcı yaş profilleri yarışlara göre analiz edildi.

### 3.6 En Hızlı ve En Yavaş Yarışların Yıllara Göre Değişimi  
- En hızlı ve en yavaş yarışların yıllık ortalama bitirme süreleri çizgi grafiklerle analiz edildi.  
- Zaman içindeki performans trendleri ve değişimler görselleştirildi.

---

## 4. Koşucu Profili Analizleri

### 4.1 Elit ve Zayıf Performans Karşılaştırmaları  
- Koşucuların bitirme süreleri içinde en hızlı %1 (elit) ve en yavaş %1 (zayıf) gruplar belirlendi.  
- Bu grupların ortalama bitirme süreleri hesaplandı ve karşılaştırıldı.  
- Histogram üzerinde elit ve zayıf grupların süreleri vurgulandı.

### 4.2 En Hızlı ve En Yavaş Koşucuların Yarış Bazında Performans Karşılaştırması  
- En hızlı %1 ve en yavaş %1 koşucuların yarışlara göre ortalama bitirme süreleri hesaplandı.  
- Yan yana çubuk grafiklerle bu iki grubun yarış bazında performans farkları görselleştirildi.

### 4.3 Yaş ve Cinsiyete Göre En Hızlı %1 Koşucuların Performansı  
- En hızlı %1 koşucuların yaş ve cinsiyet bazında ortalama bitirme süreleri analiz edildi.  
- Yaş aralıklarına göre kadın ve erkek elit koşucuların performansları barplotlarla sunuldu.  
- Bu analiz, elit performansın demografik faktörlerle ilişkisini gösterdi.

### 4.4 Yaş Gruplarına Göre En Yavaş %1 Koşucuların Performansı  
- Benzer şekilde, en yavaş %1 koşucuların yaş ve cinsiyet bazında ortalama bitirme süreleri hesaplandı ve görselleştirildi.  
- Düşük performansın yaş ve cinsiyetle ilişkisi incelendi.

---

## 5. Korelasyon ve Etkileşim Analizleri

### 5.1 Aykırı Değerlerin Korelasyona Etkisi  
- Yaş (Age) ile bitirme süresi (Finish) arasındaki ilişki Pearson ve Spearman korelasyon yöntemleriyle analiz edildi.  
- Analiz, orijinal, aykırı değerlerin çıkarıldığı ve winsorizing uygulanmış üç farklı veri setinde gerçekleştirildi.  
- Sonuçlar, aykırı değerlerin korelasyon katsayıları üzerindeki etkisini ortaya koydu.  
- Spearman korelasyonu aykırı değerlere karşı daha az duyarlıdır ve bu çalışma bunu destekledi.

### 5.2 Sayısal Sütunlar Arası Korelasyon  
- Tüm sayısal değişkenler arasındaki korelasyon matrisi hesaplandı.  
- Isı haritası (heatmap) ile görselleştirilerek pozitif ve negatif ilişkiler detaylıca incelendi.

### 5.3 Cinsiyetin Bitirme Süresi Üzerindeki Etkisi  
- Cinsiyetin bitirme süresi üzerindeki etkisi ANOVA testi ile değerlendirildi.  
- Erkek ve kadın koşucuların ortalama bitirme süreleri istatistiksel olarak karşılaştırıldı.  
- Test orijinal, aykırı değer temizlenmiş ve winsorize edilmiş veri setleri için ayrı ayrı uygulandı.

### 5.4 Yaş Aralığının Bitirme Süresi Üzerindeki Etkisi  
- Yaş grupları arasında bitirme süreleri açısından anlamlı fark olup olmadığı ANOVA testi ile incelendi.  
- Yaş faktörünün maraton performansına etkisi detaylı şekilde analiz edildi.

---

## 6. Kümeleme Analizleri

### 6.1 Orijinal Veri Setinde Kümeleme  
- Yaş ve bitirme süresi değişkenleri seçildi.  
- Standartlaştırma sonrası K-Means algoritması ile 4 küme oluşturuldu.  
- Her kümenin yaş ve bitirme süresi ortalamaları, medyanları ve katılımcı sayıları hesaplandı.  
- Cinsiyet dağılımları grafiklerle analiz edildi.  
- Bu segmentasyon, koşucuları performans ve yaş profiline göre gruplandırdı.

### 6.2 Temizlenmiş Veri Setinde Kümeleme  
- Aykırı değerlerin çıkarıldığı veri setinde aynı kümeleme işlemi yapıldı.  
- Sonuçlar orijinal veri ile karşılaştırılarak aykırı değerlerin küme yapısına etkisi incelendi.

### 6.3 Winsorizing Uygulanmış Veri Setinde Kümeleme  
- Uç değerlerin sınırlandırıldığı veri setinde kümeleme tekrarlanarak daha dengeli sonuçlar elde edildi.  
- Sayısal ve görsel analizlerle sonuçlar değerlendirildi.

### 6.4 Kümeleme Sonrası Yarış Bazında Dağılım  
- Kümeler ile yarışlar bazında gruplandırma yapıldı.  
- Her kümede hangi yarışların yoğun olduğu analiz edildi.  
- Bu, kümelerin yarış tercihi açısından farklılaşıp farklılaşmadığını gösterdi.

### 6.5 Zaman Serisi Analizi ile Küme Dağılımı  
- Yıllara göre küme dağılımları incelendi.  
- Zaman içinde küme sayılarının değişimi ve performans trendleri gözlemlendi.

### 6.6 Küme Bazında Varyans ve Performans Değerlendirmesi  
- Her kümedeki bitirme süresi varyansı hesaplandı.  
- Küme içi performans tutarlılığı ve ortalama süreler karşılaştırıldı.

### 6.7 Grup Bazlı Hedef Belirleme  
- Her koşucu için, ait olduğu kümenin ortalama performansına göre bireysel hedefler önerildi.  
- Örnek: Mevcut bitirme süresini %5 oranında iyileştirme gibi somut hedefler.  
- Böylece kişiye özel gelişim planları oluşturuldu.

---

# Genel Değerlendirme ve Sonuçlar

Yapılan kapsamlı veri ön işleme adımları sayesinde eksik ve aykırı değerler titizlikle ele alınarak analizlerin doğruluğu artırılmıştır. Keşifsel veri analizi ile maraton katılımcılarının yaş, cinsiyet ve performans özellikleri detaylıca incelenmiş; yıllara göre katılımcı ve yarış sayılarındaki değişim trendleri ortaya konmuştur.

Yarış bazlı analizler en popüler yarışların performans seviyelerini, katılımcı profillerini ve yıllara göre değişimleri detaylandırmıştır. Koşucu profili analizleri elit ve zayıf performans gruplarının demografik farklılıklarını netleştirmiştir.

Korelasyon ve istatistiksel testler, yaş ve cinsiyet faktörlerinin performansa etkilerini detaylandırmış, aykırı değerlerin analiz sonuçlarına etkisi ortaya konmuştur.

Kümeleme analizleri ile koşucular benzer yaş ve performans profillerine göre segmentlere ayrılarak her gruba özgü analizler ve hedefler geliştirilmiştir.

---


# Teşekkür / Acknowledgements

Bu projede analiz yapmak için Brian Rock tarafından Kaggle'da paylaşılan  
[2010-2019 Fall Marathons veri seti](https://www.kaggle.com/datasets/runningwithrock/2010-2019-fall-marathons) kullanılmıştır.  
Değerli veri setini paylaştığı için Brian Rock'a teşekkür ederim.

---

This project utilizes the [2010-2019 Fall Marathons dataset](https://www.kaggle.com/datasets/runningwithrock/2010-2019-fall-marathons) shared by Brian Rock on Kaggle.  
I sincerely thank Brian Rock for making this valuable dataset publicly available.
