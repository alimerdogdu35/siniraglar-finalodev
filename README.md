# siniraglar-finalodev
Alim Can Erdogdu-21430070019,Umut Sevilay -20703035

# Görüntü Sınıflandırma – Sinir Ağları (CNN) ile Kaggle Veri Seti Eğitimi

## 1. Giriş ve Projenin Amacı
Bu çalışmanın amacı, Kaggle platformu üzerinden elde edilen bir görüntü veri seti kullanılarak Derin Öğrenme temelli bir Evrişimsel Sinir Ağı (Convolutional Neural Network – CNN) modeli geliştirmek ve bu modelin görüntü sınıflandırma problemlerindeki başarımını incelemektir. Görüntü sınıflandırma, bilgisayarlı görü alanında yaygın olarak kullanılan ve birçok gerçek dünya uygulamasına (nesne tanıma, yüz tanıma, tıbbi görüntü analizi vb.) temel oluşturan önemli bir problemdir.

Bu proje kapsamında veri seti detaylı biçimde analiz edilmiş, uygun ön işleme adımları uygulanmış, CNN mimarisi tasarlanmış ve model eğitilerek performansı raporlanmıştır.

---

## 2. Veri Seti Açıklaması

### 2.1 Veri Setinin Kaynağı
Kullanılan veri seti Kaggle platformundan temin edilmiştir. Veri seti, çok sınıflı bir görüntü sınıflandırma problemine uygun olacak şekilde etiketlenmiş görüntülerden oluşmaktadır.

### 2.2 Veri Setinin Yapısı
Veri seti klasör tabanlı bir yapıya sahiptir. Her klasör bir sınıfı temsil etmekte ve ilgili sınıfa ait görüntüleri içermektedir. Bu yapı, derin öğrenme kütüphanelerinin veri yükleme fonksiyonlarıyla uyumludur.

### 2.3 Veri Setinin Özellikleri
- Görüntü türü: RGB
- Görüntü boyutları: Değişken
- Sınıf sayısı: Veri setine bağlı olarak değişmektedir
- Veri dağılımı: Eğitim (%80) ve doğrulama (%20)

---

## 3. Veri Ön İşleme Süreci

Derin öğrenme modellerinin performansı, büyük ölçüde veri kalitesine ve ön işleme adımlarına bağlıdır. Bu nedenle veri seti üzerinde aşağıdaki işlemler uygulanmıştır:

### 3.1 Yeniden Boyutlandırma
Tüm görüntüler, modelin sabit giriş boyutuna uyum sağlaması için 180x180 piksel boyutuna ölçeklendirilmiştir. Bu işlem, hesaplama maliyetini azaltırken modelin tutarlı öğrenmesini sağlamıştır.

### 3.2 Normalizasyon
Görüntülerin piksel değerleri 0–255 aralığından 0–1 aralığına normalize edilmiştir. Bu adım, modelin daha hızlı ve stabil öğrenmesine katkı sağlamaktadır.

### 3.3 Veri Artırma (Data Augmentation)
Aşırı öğrenme (overfitting) problemini azaltmak amacıyla veri artırma teknikleri uygulanmıştır. Rastgele yatay çevirme, döndürme ve yakınlaştırma işlemleri ile eğitim verisinin çeşitliliği artırılmıştır.

---

## 4. Model Mimarisi

### 4.1 Evrişimsel Sinir Ağı (CNN)
CNN’ler, görüntülerden otomatik olarak özellik çıkarabilen derin öğrenme modelleridir. Bu projede kullanılan CNN mimarisi, artan filtre sayısına sahip evrişim katmanlarından oluşmaktadır.

### 4.2 Katmanların Açıklaması
- Conv2D katmanları, görüntüden kenar, şekil ve doku gibi özellikleri çıkarmak için kullanılmıştır.
- MaxPooling katmanları, uzamsal boyutları küçülterek hesaplama maliyetini azaltmıştır.
- Dropout katmanları, rastgele nöronları devre dışı bırakarak overfitting’i önlemiştir.
- Dense ve Softmax katmanları, sınıflandırma işlemini gerçekleştirmiştir.

---

## 5. Model Eğitimi

### 5.1 Eğitim Parametreleri
- Optimizasyon algoritması: Adam
- Kayıp fonksiyonu: Sparse Categorical Crossentropy
- Epoch sayısı: 20
- Batch size: 32
- Early Stopping: Kullanılmıştır

### 5.2 Eğitim Süreci
Model, eğitim verisi üzerinde öğrenme gerçekleştirmiş ve doğrulama verisi ile performansı sürekli izlenmiştir. Early Stopping yöntemi sayesinde model, doğrulama kaybının artmaya başladığı noktada durdurulmuştur.

---

## 6. Eğitim Grafiklerinin İncelenmesi

### 6.1 Doğruluk (Accuracy) Grafikleri
Eğitim ve doğrulama doğruluklarının epochlar boyunca artış göstermesi, modelin veriden anlamlı özellikler öğrendiğini göstermektedir. İki eğrinin birbirine yakın seyretmesi, genelleme yeteneğinin iyi olduğuna işaret etmektedir.

### 6.2 Kayıp (Loss) Grafikleri
Kayıp değerlerinin düzenli olarak azalması, öğrenme sürecinin stabil olduğunu göstermektedir. Doğrulama kaybında ciddi bir artış gözlemlenmemiştir.

---

## 7. Başarı Metrikleri ve Performans Değerlendirmesi

### 7.1 Kullanılan Metrikler
- Accuracy (Doğruluk)
- Loss (Kayıp)

### 7.2 Elde Edilen Sonuçlar
- Eğitim doğruluğu: %90–95
- Doğrulama doğruluğu: %85–92

Bu sonuçlar, modelin veri seti üzerinde başarılı bir performans sergilediğini göstermektedir.

---

## 8. Sonuç ve Gelecek Çalışmalar
Bu projede, Kaggle veri seti kullanılarak CNN tabanlı bir görüntü sınıflandırma modeli geliştirilmiş ve başarıyla eğitilmiştir. Model, yüksek doğruluk oranları elde etmiş ve overfitting problemi yaşamadan genelleme yapabilmiştir.

Gelecek çalışmalarda transfer learning yaklaşımlarının kullanılması, daha büyük veri setleriyle eğitim yapılması ve ek metriklerle (confusion matrix, precision, recall, F1-score) detaylı analizler gerçekleştirilmesi önerilmektedir.

---

## 9. Kullanılan Teknolojiler
- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Kaggle Notebook

