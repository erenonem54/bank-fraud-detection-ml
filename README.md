# Banka İçin Fraud Detection Projesi

Bu proje, kredi kartı işlemleri üzerinde gerçekleşen dolandırıcılık (fraud) girişimlerini tespit etmek amacıyla hazırlanmıştır. Çalışmada Kaggle üzerinde yayınlanan 284.807 satırlık gerçek kredi kartı veri seti kullanılmıştır.

Projenin temel amacı, normal ve şüpheli işlemleri ayırabilen, yüksek doğrulukla çalışan ve fraud işlemleri mümkün olduğunca kaçırmayan bir makine öğrenmesi modeli geliştirmektir.

---

## 📊 Veri Seti Hakkında

- Toplam işlem sayısı: **284.807**
- Toplam sütun sayısı: **31**
- Hedef değişken: `Class`
  - `0` → Normal işlem  
  - `1` → Fraud işlem
- V1–V28 sütunları güvenlik nedeniyle PCA ile dönüştürülmüş anonim özelliklerdir.
- Fraud oranı yaklaşık **%0.17** olup veri seti oldukça dengesizdir.

---

## 🚀 Kullanılan Modeller

Projede iki farklı makine öğrenmesi yöntemi denenmiştir:

### **1. Logistic Regression**
- Basit ve yorumlanabilir bir model olduğundan başlangıç noktası olarak tercih edilmiştir.
- Ancak fraud işlemlerin yalnızca yaklaşık %63’ünü yakalayabildiği için yeterli bulunmamıştır.

### **2. Random Forest**
- Birden fazla karar ağacının birlikte çalıştığı güçlü bir ensemble yöntemidir.
- Fraud sınıfında **%82’nin üzerinde recall** elde edilmiştir.
- Yanlış alarm oranı düşüktür.
- ROC–AUC skoru yaklaşık **0.96** olup modelin ayrım gücü oldukça yüksektir.

Bu sonuçlar doğrultusunda **final model olarak Random Forest seçilmiştir.**

---

## 🧪 Yapılan Adımlar

- Veri setinin yüklenmesi ve ilk inceleme  
- Eksik değer kontrolü  
- Sınıf dengesizliğinin analiz edilmesi  
- Train-test ayrımı  
- Logistic Regression eğitimi ve değerlendirilmesi  
- Random Forest eğitimi ve değerlendirilmesi  
- Confusion Matrix, ROC eğrisi ve AUC skorunun hesaplanması  
- Modellerin karşılaştırılması  

---

## 📈 Sonuç

Random Forest modeli, fraud işlemleri tespit etmede daha yüksek başarı göstermiştir.  
Özellikle dengesiz veri setlerinde daha güçlü performans sunması nedeniyle proje için uygun bir çözüm olmuştur.

---

## 📂 Dosyalar

- `Bank_Fraud_Detection_Project.ipynb` → Projenin tüm adımlarının yer aldığı Jupyter/Colab notebook
- Gerekli görseller (Confusion Matrix, ROC grafiği) notebook içinde oluşturulmaktadır.

---

## 💡 Gelecek Çalışmalar

- Veri dengesizliğini azaltmak için SMOTE gibi yöntemler kullanılabilir.
- XGBoost veya LightGBM gibi daha gelişmiş modeller denenebilir.
- Model gerçek zamanlı bir API sistemine dönüştürülebilir.
- Özellik mühendisliği genişletilerek daha kapsamlı bir analiz yapılabilir.

---

## 👥 Geliştiriciler
Bu proje, üniversite kapsamında bir grup çalışması olarak hazırlanmıştır.

---

Her türlü katkıya ve geliştirmeye açıktır.  
Teşekkürler!
