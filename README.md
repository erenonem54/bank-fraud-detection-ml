# Banka İçin Fraud Detection Projesi

Bu proje, kredi kartı işlemleri üzerinde gerçekleşen dolandırıcılık (fraud) girişimlerini tespit etmek amacıyla hazırlanmıştır.  
Çalışmada, Kaggle platformunda yayınlanan ve **284.807 işlem** içeren gerçek dünya kredi kartı veri seti kullanılmıştır.

Projenin temel amacı; **normal ve şüpheli işlemleri ayırt edebilen**, yüksek doğrulukla çalışan ve özellikle **fraud işlemlerini mümkün olduğunca kaçırmayan** bir makine öğrenmesi modeli geliştirmektir.

---

## 📊 Veri Seti Hakkında

- **Toplam işlem sayısı:** 284.807  
- **Toplam özellik (sütun) sayısı:** 31  
- **Hedef değişken:** `Class`  
  - `0` → Normal işlem  
  - `1` → Fraud (dolandırıcılık) işlemi  

- `V1–V28` sütunları, güvenlik ve gizlilik nedeniyle **PCA (Principal Component Analysis)** ile dönüştürülmüş anonim özelliklerdir.
- Fraud oranı yaklaşık **%0.17** olup veri seti **yüksek derecede dengesizdir**.

Bu nedenle model değerlendirmesinde accuracy metriği tek başına yeterli değildir.

---

## 🧠 Kullanılan Modeller ve Sonuçlar

Projede üç farklı makine öğrenmesi modeli eğitilmiş ve performansları karşılaştırılmıştır.

---

### 1️⃣ Logistic Regression

Basit ve yorumlanabilir bir model olması nedeniyle başlangıç noktası olarak tercih edilmiştir.

**Sonuçlar (Fraud sınıfı):**
- Precision: **0.8267**
- Recall: **0.6327**
- F1-score: **0.7168**

Confusion Matrix sonuçlarına göre model, **98 fraud işlemin 36 tanesini kaçırmıştır**.  
Bu durum, fraud tespiti gibi kritik problemlerde **yüksek risk** oluşturmaktadır.

➡️ Bu nedenle Logistic Regression, tek başına yeterli bir çözüm olarak değerlendirilmemiştir.

---

### 2️⃣ Random Forest

Birden fazla karar ağacının birlikte çalıştığı güçlü bir **ensemble öğrenme** yöntemidir.

**Sonuçlar (Fraud sınıfı):**
- Precision: **0.9419**
- Recall: **0.8265**
- F1-score: **0.8804**

Confusion Matrix sonuçlarına göre model, **98 fraud işlemin 81 tanesini doğru tespit etmiştir**.  
Yanlış alarm oranı düşük, genel performansı ise oldukça yüksektir.

➡️ Random Forest, güçlü ve dengeli bir performans sunmuştur.

---

### 3️⃣ XGBoost

Gradient boosting tabanlı, dengesiz veri setlerinde yüksek performans gösteren gelişmiş bir ensemble algoritmasıdır.  
Model eğitiminde sınıf dengesizliği problemi, `scale_pos_weight = 577.29` parametresi ile ele alınmıştır.

**Sonuçlar (Fraud sınıfı):**
- Precision: **0.8542**
- Recall: **0.8367**
- F1-score: **0.8454**
- PR-AUC: **0.8763**

Confusion Matrix sonuçlarına göre model, **98 fraud işlemin 82 tanesini doğru şekilde yakalamıştır**.  
Precision–Recall dengesi göz önüne alındığında, modelin dengesiz veri koşullarında başarılı olduğu görülmektedir.

---

## 📈 Değerlendirme Metrikleri

Fraud tespiti probleminin dengesiz yapısı nedeniyle aşağıdaki metrikler kullanılmıştır:

- **Confusion Matrix**
- **Precision, Recall ve F1-score**
- **PR-AUC** (özellikle XGBoost için)

PR-AUC metriği, fraud sınıfının doğru tespit edilme başarısını ölçmek açısından temel değerlendirme kriteri olarak kullanılmıştır.

---

## ✅ Sonuç ve Değerlendirme

Elde edilen sonuçlar karşılaştırıldığında:

- Logistic Regression modeli, fraud işlemleri yakalama konusunda yetersiz kalmıştır.
- Random Forest modeli, yüksek precision ve güçlü genel performans sergilemiştir.
- **XGBoost modeli**, en yüksek recall ve PR-AUC değeri ile fraud işlemlerini kaçırmama açısından en dengeli sonuçları sunmuştur.

Bu doğrultuda, **XGBoost modeli**, dengesiz veri setlerinde fraud tespiti problemi için **final model** olarak değerlendirilmiştir.

---

## 📁 Dosyalar

- `Bank_Fraud_Detection_Project.ipynb`  
  → Projenin tüm adımlarının yer aldığı Jupyter / Google Colab notebook  
- Confusion Matrix, ROC ve PR eğrileri notebook içerisinde üretilmektedir.

---

## 👥 Geliştiriciler

Bu proje, üniversite kapsamında bir **grup çalışması** olarak hazırlanmıştır.
