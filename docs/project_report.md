# Financial Time Series Analysis of Consumer Confidence Using VAR

## 1. Projenin Amacı

Bu çalışmanın temel amacı, tüketici güven endeksi (TGE) ile çeşitli makroekonomik değişkenler arasındaki dinamik ilişkileri incelemektir. Özellikle tüketici güveninin zaman içerisindeki hareketlerinin hangi makroekonomik faktörlerden etkilendiği ve bu etkilerin zaman içerisinde nasıl yayıldığı analiz edilmiştir.

Çalışma kapsamında aşağıdaki sorulara cevap aranmıştır:

- Tüketici güveni hangi makroekonomik değişkenlerden etkilenmektedir?
- Ekonomik şoklar tüketici güveni üzerinde ne kadar süre etkilidir?
- Tüketici güveninin değişimi büyük ölçüde kendi dinamiklerinden mi kaynaklanmaktadır?
- Makroekonomik değişkenler arasındaki etkileşimler sistem dinamikleri içerisinde nasıl ortaya çıkmaktadır?

Bu soruların incelenmesi için **Vector Autoregression (VAR)** modeli kullanılmıştır.

---

# 2. Kullanılan Veri Seti

Çalışmada Türkiye ekonomisine ait çeşitli makroekonomik göstergeler kullanılmıştır.

Analizde kullanılan başlıca değişkenler:

- Tüketici Güven Endeksi (TGE)
- USD Döviz Kuru
- Reel Efektif Döviz Kuru
- BIST Endeksi
- İşsizlik Oranı
- Enflasyon
- Sanayi Üretim Endeksi

Veri seti 2004–2018 dönemini kapsayan zaman serilerinden oluşmaktadır.

Bu değişkenler Türkiye ekonomisinin farklı yönlerini temsil etmektedir:

| Değişken | Temsil ettiği alan |
|--------|----------------|
| TGE | tüketici beklentileri |
| USD | finansal piyasalar |
| Reel kur | uluslararası rekabet |
| BIST | sermaye piyasaları |
| İşsizlik | işgücü piyasası |
| Enflasyon | fiyat istikrarı |
| Sanayi üretimi | reel ekonomik aktivite |

---

# 3. Veri İşleme Süreci

Zaman serisi analizlerinde veri hazırlama aşaması kritik öneme sahiptir. Bu nedenle analiz öncesinde çeşitli veri işleme adımları uygulanmıştır.

## 3.1 Veri Temizleme

Veri seti incelenmiş ve aşağıdaki işlemler gerçekleştirilmiştir:

- Eksik değerlerin kontrol edilmesi
- Tarih formatlarının düzenlenmesi
- Veri tiplerinin dönüştürülmesi
- Gereksiz değişkenlerin temizlenmesi

## 3.2 Zaman Serisi Yapısına Uyum

Makroekonomik veri setleri genellikle **trend ve durağanlık sorunları** içerir. Bu nedenle veri seti zaman serisi analizine uygun hale getirilmiştir.

Bu kapsamda:

- log dönüşümleri uygulanmıştır
- değişkenler yüzde değişim veya fark serilerine dönüştürülmüştür

Bu işlemler serilerin istatistiksel özelliklerini stabilize etmek için yapılmıştır.

---

# 4. Durağanlık Analizi (Stationarity)

Zaman serisi modellerinin büyük bölümü durağanlık varsayımına dayanır. Durağan olmayan seriler ile yapılan regresyonlar **spurious regression** sorununa yol açabilir.

Bu nedenle serilerin durağan olup olmadığı **Augmented Dickey Fuller (ADF) testi** ile incelenmiştir.

ADF test sonuçları bazı serilerin seviyede durağan olmadığını göstermiştir. Bu nedenle ilgili serilere fark alma işlemi uygulanarak seriler durağan hale getirilmiştir.

Bu işlem VAR modelinin sağlıklı şekilde kurulabilmesi için gerekli bir adımdır.

---
## İKKO Değişkeni Üzerine Not

ADF birim kök testleri sonucunda değişkenlerin büyük bölümünde durağanlık sağlanmıştır. 
Ancak İKKO (İmalat Kapasite Kullanım Oranı) değişkeninin logaritmik farkı alındıktan sonra 
dahi p-değerinin yaklaşık 0.33 seviyesinde kaldığı görülmektedir.

Bu durum, ilgili serinin mevcut dönüşüm altında durağanlık koşulunu sağlamadığını 
göstermektedir.

Bu aşamada iki alternatif yaklaşım mümkündür:

- Serinin modelden çıkarılması
- Daha yüksek dereceden fark alma veya alternatif dönüşümlerin denenmesi

Bu çalışmada model yapısını basitleştirmek ve VAR modelinin temel varsayımlarını 
koruyabilmek amacıyla İKKO değişkeni modelden çıkarılmıştır. Bununla birlikte bu 
tercih, kapasite kullanım oranının tüketici güveni üzerindeki olası etkilerinin 
analiz dışında kalmasına yol açabileceği için ekonomik yorum açısından sınırlılık 
oluşturabilir.

Alternatif bir yaklaşım olarak ikinci dereceden fark alma veya eşbütünleşme 
yaklaşımları (örneğin VECM) ilerleyen çalışmalar için değerlendirilebilir.

---

# 5. Model Seçimi

Bu çalışmada **Vector Autoregression (VAR)** modeli tercih edilmiştir.

VAR modeli şu sebeplerle uygun görülmüştür:

- Makroekonomik değişkenler arasında karşılıklı etkileşimler vardır.
- Değişkenler arasında açık bir nedensellik yönü önceden belirlenemeyebilir.
- VAR modeli tüm değişkenleri sistem içerisinde birlikte ele alır.

Bu özellikleri nedeniyle VAR modeli makroekonomik analizlerde yaygın olarak kullanılmaktadır.

---

# 6. Gecikme Uzunluğu Seçimi

VAR modelinin kurulmasında en önemli adımlardan biri **lag length selection** sürecidir.

Bu çalışmada gecikme sayısı aşağıdaki bilgi kriterleri kullanılarak belirlenmiştir:

- Akaike Information Criterion (AIC)
- Bayesian Information Criterion (BIC)
- HQIC

Bilgi kriterlerinin karşılaştırılması sonucunda model için uygun gecikme sayısı belirlenmiştir.

---

# 7. VAR Modelinin Tahmini

Belirlenen gecikme uzunluğu kullanılarak VAR modeli tahmin edilmiştir.

VAR modelinin temel mantığı şu şekildedir:

Her değişken geçmiş değerleri ve sistemdeki diğer değişkenlerin geçmiş değerleri ile açıklanır.

Bu yaklaşım makroekonomik değişkenlerin karşılıklı dinamiklerini analiz etmeye olanak sağlar.

---

# 8. Granger Nedensellik Analizi

VAR modeli kurulduktan sonra değişkenler arasında öngörü gücü olup olmadığını test etmek amacıyla **Granger Causality Test** uygulanmıştır.

Granger nedensellik testi şu soruya cevap verir:

> Bir değişkenin geçmiş değerleri başka bir değişkenin geleceğini tahmin etmede anlamlı bir katkı sağlıyor mu?

Bu analiz makro değişkenler arasındaki yönlü ilişkileri incelemek için kullanılmıştır.

---

# 9. Impulse Response Analysis (IRF)

Impulse Response Function analizi sistemdeki bir değişkende meydana gelen şokun diğer değişkenler üzerindeki zaman içindeki etkisini incelemek için kullanılır.

Bu analiz sayesinde:

- Ekonomik şokların etkisinin yönü
- Etkinin büyüklüğü
- Etkinin ne kadar süre devam ettiği

incelenmiştir.

Analiz sonuçları makroekonomik şokların tüketici güveni üzerindeki etkilerinin genellikle **kısa süreli olduğunu ve birkaç dönem içerisinde sönümlendiğini** göstermektedir.

---

# 10. Forecast Error Variance Decomposition (FEVD)

FEVD analizi bir değişkenin tahmin hatası varyansının hangi değişkenlerden kaynaklandığını gösterir.

Bu analiz sayesinde tüketici güven endeksindeki değişimlerin hangi faktörlerden kaynaklandığı ölçülmüştür.

Analiz sonuçları şu bulguları ortaya koymuştur:

- tüketici güveni büyük ölçüde kendi iç dinamiklerinden etkilenmektedir
- döviz kuru şokları sınırlı fakat ölçülebilir bir etki yaratmaktadır
- diğer makro değişkenlerin etkisi görece daha küçüktür

---

# 11. Model Tanı Testleri (Residual Diagnostics)

VAR modelinin güvenilirliğini değerlendirmek için model artıklarına çeşitli tanı testleri uygulanmıştır.

Bu kapsamda:

- **Whiteness (Portmanteau) testi**
- **Normality testi**

gerçekleştirilmiştir.

Sonuçlara göre model artıklarında **anlamlı bir seri korelasyon tespit edilmemiştir**.

Normal dağılım varsayımı tam olarak sağlanmamış olsa da makroekonomik zaman serilerinde bu durum oldukça yaygındır ve genellikle modelin geçerliliğini ciddi şekilde etkilemez.

---

# 12. Temel Bulgular

Analiz sonuçları aşağıdaki temel bulguları ortaya koymaktadır:

- tüketici güveni büyük ölçüde kendi dinamikleri tarafından belirlenmektedir
- döviz kuru şokları tüketici güveni üzerinde sınırlı fakat ölçülebilir etki yaratmaktadır
- makroekonomik şokların etkisi genellikle kısa süreli olmaktadır
- sistem dinamikleri zaman içerisinde dengeye dönmektedir

---

# 13. Modelin Avantajları

Bu çalışmada kullanılan VAR yaklaşımının çeşitli avantajları bulunmaktadır:

- değişkenler arası karşılıklı etkileşimleri modelleyebilme
- nedensellik yönünün önceden belirlenmesini gerektirmemesi
- sistem dinamiklerini analiz edebilme
- IRF ve FEVD gibi güçlü analiz araçları sunması

---

# 14. Modelin Sınırlılıkları

Her ekonometrik modelde olduğu gibi VAR modelinin de bazı sınırlılıkları vardır.

Başlıca sınırlılıklar şunlardır:

- yüksek parametre sayısı
- büyük veri ihtiyacı
- yapısal yorumların sınırlı olması
- eşbütünleşme ilişkilerinin ayrı analiz gerektirmesi

---

# 15. Çalışmanın Eksikleri ve Geliştirme Alanları

Bu çalışma bir ekonometrik analiz pipeline’ını göstermeyi amaçlamaktadır. Ancak bazı ileri analizler eklenebilir.

Örneğin:

- Johansen cointegration testi
- VECM modeli
- Structural VAR
- out-of-sample forecasting
- machine learning modelleri ile karşılaştırma

Bu tür analizler modelin açıklayıcılığını daha da artırabilir.

---

# 16. Sonuç

Bu çalışma Türkiye ekonomisine ait çeşitli makroekonomik değişkenler ile tüketici güven endeksi arasındaki dinamik ilişkileri VAR modeli kullanarak incelemiştir.

Analiz sonuçları tüketici güveninin büyük ölçüde kendi dinamiklerinden etkilendiğini, makroekonomik şokların ise sınırlı fakat ölçülebilir etkiler yarattığını göstermektedir.

Model tanı testleri VAR modelinin genel olarak uygun bir spesifikasyona sahip olduğunu göstermektedir.

Bu çalışma aynı zamanda Python kullanılarak gerçekleştirilen bir **ekonometrik analiz pipeline’ı** örneği sunmaktadır.