# reytingSiniflandirma
 

Film&Dizi Verilerinin İncelenmesi ve Reyting Sınıflandırılması

Özet—Bu projede dizi/film verileri incelenmiş ve sınıflandırma modeli geliştirilmiştir. Python programlama dili kullanılarak numpy, pandas, matplotlib, seaborn, sklearn ve mlxtend kütüphaneleri yoğun olarak tercih edilmiştir. Veriler düzenlenmiş, grafiklerle görselleştirilmiş ve Random Forest Classifier modeli oluşturularak sınıflandırma işlemi gerçekleştirilmiştir.

Bu proje, Global AI Hub ve Aygaz bünyesinde düzenlenen Makine Öğrenmesi Bootcamp'i için Feyza Mıynat tarafından hazırlanmıştır. 

1. Gerekli Kütüphaneleri & Veri Setini Import Etme İşlemi
2. Veri Seti Hakkında Temel Bilgilerin İncelenmesi
3. Keşifsel Veri Analizi
4. Veri Ön İşleme
5. Gözetimli Öğrenme Modeli Kurma (Random Forest Classifier)
6. Gözetimsiz Öğrenme Modelleri Kurma ( k-Means & Apriori Algoritmaları)

başlıkları olmak üzere 6 kısımdan oluşmaktadır. 

Veri setimiz 15,000 satır ve 29 sütundan oluşmaktadır. Sütunlardan 2'si boolean, 2'si float64, 5'i int64, ve 20'si object türündedir.
Özet İstatistikler:
Ortalama sezon sayısı 1.51, bölüm sayısı ise 24.89'dur.
Oylama sayısının ortalaması 12.50, oy ortalaması 2.32'dir.
Popülerlik ortalaması 5.88 ve bölüm süresi ortalaması 22.83 dakikadır.
Eksik Veriler:
name, overview, backdrop_path, homepage, poster_path, ve genres gibi sütunlarda belirgin eksiklikler bulunmaktadır.
Bu veriler veri setinin genel özelliklerini ve eksik veri durumunu özetlemektedir.

Veri ön işleme aşamasında veri setinde ilgili sütunlara label encoding ve scaling işlemleri uygulanmış, kurulacak modele hazırlıklı hale getirilmiştir. 

Random Forest Classifier Modelinin Kullanım Nedeni:
Random Forest Classifier, birçok karar ağacının birleşiminden oluşan bir ansambl modelidir. Bu model, hem doğruluk hem de genelleme yeteneği açısından güçlüdür ve özellikle karmaşık veri setlerinde etkili olabilir. Aşağıdaki nedenlerden dolayı Random Forest tercih edilmiştir:
-Çoklu Karar Ağaçları: Birden fazla karar ağacı kullanarak veriyi daha iyi sınıflandırabilir.
-Overfitting Önleme: Karar ağaçları tek başlarına aşırı öğrenme (overfitting) yapabilirken, Random Forest bu riski azaltır.
-Özellik Önem Dereceleri: Özelliklerin önem derecelerini belirlemekte başarılıdır, bu da özellik mühendisliği ve model açıklaması için faydalıdır.
Hiperparametre optimizasyonu ile modele sağlanan faydalar:
-Doğruluk Skoru Artışı: İkinci model, hiperparametre optimizasyonu ile doğruluk skorunu %68.8'e çıkarmıştır. Bu, modelin genel performansında iyileşme sağladığını göstermektedir.
Sınıflandırma Raporu:
-High Kategorisi: İkinci modelde, "High" kategorisinin precision, recall ve f1-score değerlerinde artış gözlemlenmiştir. Bu, modelin yüksek popülerlikteki örnekleri daha iyi sınıflandırabildiğini gösterir.
-Low Kategorisi: "Low" kategorisinde de performans iyileşmiş, özellikle precision artışı belirgindir.
-Medium Kategorisi: "Medium" kategorisinde, ikinci modelde recall ve f1-score'da bir iyileşme sağlanmıştır ancak precision hala düşük kalmaktadır. Bu, "Medium" kategorisindeki örneklerin hâlâ zayıf sınıflandırıldığını göstermektedir.
Genel Performans: Macro ve weighted average değerlerinde de iyileşme görülmektedir. Bu, modelin genel olarak daha dengeli ve doğru sınıflama sağladığını gösterir.
 
k-Means kümeleme modelinde kullanılacak veriler üzerinde ölçeklendirme işlemi yapılmış, ardından kmeans modeli oluşturulmuş ve scatter grafiği ile görselleştirilmiştir. 
Apriori modelinde ise df['genres'] sütunundaki türler, virgüllerle ayrılarak bir liste haline getirildi. Bu liste, türleri sütunlar olarak temsil eden bir DataFrame'e (df_genres) dönüştürüldü. TransactionEncoder kullanılarak, türlerin ikili bir matris formatına dönüştürülmesi sağlandı. apriori algoritması ile türlerin bulunma sıklığı hesaplandı ve destek (support) değerine göre filtreleme yapıldı. Elde edilen sık kullanılan öğe kümeleri ile association_rules fonksiyonu kullanılarak, türler arasındaki ilişkiler ve güven değerlerine göre kurallar oluşturuldu.

Proje kapsamında veri setinin analizi yapılmış, eksik veriler ve türlerin sıklıkları değerlendirilmiştir. Random Forest Classifier modeli ile doğruluk skoru %67.2 olarak elde edilmiş, hiperparametre optimizasyonu sonrası bu skor %68.8'e yükseltilmiştir. Ayrıca, türlerin sıklığı ve türler arasındaki ilişkiler apriori ve association_rules algoritmaları kullanılarak analiz edilmiştir. "Documentary" türü en yüksek sıklığa sahipken, belirli türler arasında güçlü ilişkiler tespit edilmiştir.

Kaynak veri seti: https://www.kaggle.com/datasets/asaniczka/full-tmdb-tv-shows-dataset-2023-150k-shows
Proje Linki (Kaggle): https://www.kaggle.com/code/feyzamynat/aygazbootcamp

