# Banka İçin Fraud Detection Projesi

Bu proje, kredi kartı işlemleri üzerinde sahte (fraud) işlemleri tespit etmek amacıyla geliştirilmiş makine öğrenmesi tabanlı bir karar destek sistemidir.

# Projenin Amacı
Amaç, geçmiş işlem verileri üzerinden öğrenen bir model ile, yeni işlemlerin fraud (dolandırıcılık) olasılığını tahmin etmektir.

# Veri Seti
- Toplam işlem: 105.066
- Özellik sayısı: 31
- Hedef değişken: Class
  - 0 → Normal işlem
  - 1 → Fraud işlem

Fraud oranı yaklaşık %0.22 olup veri seti oldukça dengesizdir.

# Kullanılan Yöntemler
Projede iki model test edilmiştir:
- Logistic Regression
- Random Forest

# Logistic Regression
Fraud Recall: %50  
Bu model, fraud işlemlerin yalnızca yarısını tespit edebilmiştir.

# Random Forest
- Fraud Recall: %78
- Fraud Precision: %94
- F1-score: %85

Bu nedenle en başarılı model olarak Random Forest seçilmiştir.

# Ek Analiz
Model performansı ROC Eğrisi ve AUC değeri ile de değerlendirilmiştir. AUC değerinin 1’e yakın olması modelin genel performansının yüksek olduğunu göstermektedir.

# Çalıştırma
Notebook dosyası Google Colab üzerinde çalışacak şekilde hazırlanmıştır.

Gerekli kütüphaneler:
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

# Gelecekte yapılabilecek Çalışmalar
- SMOTE ile veri dengeleme
- XGBoost modeli denemeleri
