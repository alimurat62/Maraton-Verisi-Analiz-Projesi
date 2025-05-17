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

- **Veri Yükleme ve Genel Bilgi**  
  2010-2019 yılları arasında 96 maraton yarışına ait yaklaşık 2 milyon satır, 7 sütun (Yarış adı, yıl, koşucu adı, cinsiyet, yaş, bitirme süresi (saniye), yaş aralığı) içeren veri yüklendi.

- **Eksik Değerlerin Düzenlenmesi**  
  - `Name` sütunundaki 2 eksik değer `'Unknown'` olarak dolduruldu.  
  - `Gender` sütunundaki 8 eksik değer mod ile tamamlandı.  
  - `Age` sütunundaki mantıksal sınır dışı (13-100 aralığı dışındaki) değerler `NaN` yapıldı ve yaş aralığına göre medyan ile dolduruldu.

- **Uç Değer (Outlier) Analizi**  
  - Bitirme süresi sütununda IQR yöntemi ile aşırı uç değerler tespit edildi.  
  - İki farklı işlem uygulandı: uç değerlerin çıkarılması ve winsorizing (uç değerlerin sınırlandırılması).  
  - Orijinal, temizlenmiş ve winsorize edilmiş veri setleri ortalama ve dağılım açısından karşılaştırıldı ve görselleştirildi.

---

## 2. Keşifsel Veri Analizi (EDA)

- **Dağılım Görselleştirmeleri**  
  Bitirme süresi, yaş ve cinsiyet dağılımları histogram ve sayım grafiklerle sunuldu. Katılımcıların çoğu 13-100 yaş aralığında ve erkek katılımcı sayısı kadınlardan fazlaydı.

- **Bitirme Süresi Analizleri**  
  Cinsiyet ve yaş aralıklarına göre ortalama bitirme süreleri hesaplanıp görselleştirildi.

- **Zaman Serisi İncelemeleri**  
  Yıllara göre maraton sayıları, katılımcı sayıları ve ortalama bitirme süreleri analiz edilerek zaman içindeki trendler ortaya kondu. Cinsiyet bazlı yıllık katılımcı değişimleri ayrıca incelendi.

---

## 3. Yarış Bazlı Analizler

- **3.1 En Popüler 10 Yarışa Göre Ortalama Bitirme Süresi**  
  En çok katılımcıya sahip 10 maraton için ortalama süreler hesaplandı ve karşılaştırıldı.

- **3.2 En Hızlı ve En Yavaş 3 Yarış**  
  Ortalama süreye göre en hızlı ve en yavaş 3 yarış seçilip grafiklerle gösterildi.

- **3.3 İlk 10 Yarış İçin Katılımcı Sayısı**  
  En popüler yarışlardaki toplam katılımcılar sunuldu.

- **3.4 En Popüler 10 Yarış İçin Cinsiyet Dağılımı**  
  Kadın ve erkek katılımcı sayıları yığılmış çubuk grafikle görselleştirildi.

- **3.5 En Popüler 10 Yarış İçin Yaş Ortalaması**  
  Yarışlara göre katılımcı yaş ortalamaları karşılaştırıldı.

- **3.6 En Hızlı ve En Yavaş Yarışların Yıllara Göre Değişimi**  
  Seçilen yarışların yıllık ortalama bitirme süreleri çizgi grafiklerle incelendi.

---

## 4. Koşucu Profili Analizleri

- **4.1 Elit ve Zayıf Performans Karşılaştırmaları**  
  En hızlı %1 ve en yavaş %1 koşucular belirlendi ve bitirme süreleri histogram üzerinde işaretlendi.

- **4.2 En Hızlı ve En Yavaş Koşucuların Yarış Bazında Performans Karşılaştırması**  
  Bu grupların yarış bazında ortalama süreleri karşılaştırıldı.

- **4.3 Yaş ve Cinsiyete Göre En Hızlı %1 Koşucuların Performansı**  
  Yaş aralığı ve cinsiyet bazında elit koşucuların performansları barplotlarla gösterildi.

- **4.4 Yaş Gruplarına Göre En Yavaş %1 Koşucuların Performansı**  
  Benzer şekilde, en yavaş koşucuların yaş ve cinsiyet bazında ortalama süreleri incelendi.

---

## 5. Korelasyon ve Etkileşim Analizleri

- **5.1 Aykırı Değerlerin Korelasyon Üzerindeki Etkisi**  
  Yaş ve bitirme süresi arasındaki Pearson ve Spearman korelasyonları, orijinal, aykırı değer çıkarılmış ve winsorize edilmiş veri setleri üzerinde karşılaştırıldı.

- **5.2 Sayısal Değişkenler Arası Korelasyon**  
  Tüm sayısal sütunlar için korelasyon matrisi hesaplandı ve ısı haritası ile görselleştirildi.

- **5.3 Cinsiyetin Bitirme Süresi Üzerindeki Etkisi**  
  ANOVA testi ile erkek ve kadınların ortalama bitirme süreleri arasındaki fark istatistiksel olarak test edildi (farklı veri temizleme yöntemleri ile).

- **5.4 Yaş Aralığının Bitirme Süresi Üzerindeki Etkisi**  
  Yaş grupları arasında bitirme süreleri açısından istatistiksel fark ANOVA testiyle değerlendirildi.

---

## 6. Kümeleme Analizleri

- **6.1 Orijinal Veri ile Kümeleme**  
  Yaş ve bitirme süresi değişkenleri standartlaştırılarak K-Means ile 4 küme oluşturuldu. Küme istatistikleri ve cinsiyet dağılımları incelendi.

- **6.2 Temizlenmiş Veri ile Kümeleme**  
  Aykırı değerlerin çıkarıldığı veri üzerinde kümeleme tekrarlanarak karşılaştırıldı.

- **6.3 Winsorizing Uygulanmış Veri ile Kümeleme**  
  Uç değerlerin sınırlandırıldığı veri setinde kümeleme yapıldı ve sonuçlar değerlendirildi.

- **6.4 Kümeleme Sonrası Yarış Dağılımı**  
  Küme etiketleri yarış bazında analiz edilerek hangi kümelerde hangi yarışların yoğun olduğu incelendi.

- **6.5 Zaman Serisi Analizi ile Küme Dağılımı**  
  Yıllar içindeki küme dağılımı incelenerek performans trendleri ve küme dinamikleri analiz edildi.

- **6.6 Küme Bazında Varyans ve Performans**  
  Kümelerdeki bitirme süresi varyansları ve ortalamalar hesaplandı, performans tutarlılığı değerlendirildi.

- **6.7 Grup Bazlı Hedef Belirleme**  
  Her koşucuya kendi kümesi ortalamasına göre %5 iyileştirme gibi somut performans hedefleri önerildi.

---

## Genel Değerlendirme

Bu proje, veri ön işleme aşamasında eksik ve aykırı değerlerin titizlikle ele alınmasıyla başlamış, ardından kapsamlı keşifsel analizlerle maraton katılımcılarının demografik ve performans özellikleri detaylandırılmıştır. Yarış bazlı ve koşucu profili analizleri ile farklı yarışların ve koşucu gruplarının performans farkları ortaya konmuştur. Korelasyon, ANOVA gibi istatistiksel testler ve K-Means kümeleme ile koşucu segmentasyonları yapılmış, böylece hedef odaklı gelişim planları için zemin hazırlanmıştır.

---


# Teşekkür / Acknowledgements

Bu projede analiz yapmak için Brian Rock tarafından Kaggle'da paylaşılan  
[2010-2019 Fall Marathons veri seti](https://www.kaggle.com/datasets/runningwithrock/2010-2019-fall-marathons) kullanılmıştır.  
Değerli veri setini paylaştığı için Brian Rock'a teşekkür ederim.

---

This project utilizes the [2010-2019 Fall Marathons dataset](https://www.kaggle.com/datasets/runningwithrock/2010-2019-fall-marathons) shared by Brian Rock on Kaggle.  
I sincerely thank Brian Rock for making this valuable dataset publicly available.
