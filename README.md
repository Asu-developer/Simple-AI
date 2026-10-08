# 🚗 Simple-AI

**Simple-AI**, yapay zekâ ve bilgisayarlı görü kullanarak yol görüntülerindeki nesneleri tespit etmeyi amaçlayan küçük ve deneysel bir yapay zekâ projesidir.

Proje, **ImageAI** kütüphanesi ve **YOLOv3** modeli kullanılarak görüntüler üzerinde nesne tespiti gerçekleştirir. Tespit edilen nesneler arasından yol kullanıcıları belirlenerek basit bir yol güvenliği analizi yapılır.

> 🚧 Bu proje eğitim ve deneysel amaçlarla geliştirilmiştir.

---

## ✨ Özellikler

- 🧠 YOLOv3 ile gerçek nesne tespiti
- 📷 Görüntüler üzerinde otomatik analiz
- 🚗 Araç ve yol kullanıcılarının tespiti
- 👤 İnsan tespiti
- 🚲 Bisiklet tespiti
- 🚌 Otobüs tespiti
- 🚚 Kamyon tespiti
- 🚆 Tren tespiti
- 🛣️ Yol görüntülerine yönelik basit analiz
- ⚠️ Temel yol güvenliği uyarıları

### Desteklenen nesneler

Proje özellikle aşağıdaki nesne türlerini analiz eder:

```text
car
bus
train
truck
person
bicycle
```

---

## 🛠️ Kullanılan Teknolojiler

| Teknoloji | Kullanım |
|---|---|
| 🐍 Python | Ana programlama dili |
| 🧠 YOLOv3 | Nesne tespiti |
| 👁️ ImageAI | Bilgisayarlı görü ve model yönetimi |
| 📓 Google Colab | Geliştirme / deney ortamı |

---

## 📂 Proje Yapısı

```text
Simple-AI/
│
├── AiMain.py       # Ana yapay zekâ ve nesne tespit kodu
├── README.md       # Proje dokümantasyonu
├── LICENSE         # MIT lisansı
│
├── yol.jpg         # Örnek giriş görüntüsü
├── yolv3.pt        # YOLOv3 model dosyası
└── output_image.jpg # İşlenmiş çıktı görüntüsü
```

> Model ve görüntü dosyalarının projede bulunması kullanılan çalışma yöntemine bağlıdır.

---

## 🚀 Kurulum

Projeyi klonlayın:

```bash
git clone https://github.com/Asu-developer/Simple-AI.git
cd Simple-AI
```

Gerekli Python paketini yükleyin:

```bash
pip install ImageAI
```

YOLOv3 modelini indirin:

```bash
wget https://github.com/OlafenwaMoses/ImageAI/releases/download/3.0.0-pretrained/yolov3.pt
```

Windows kullanıyorsanız modeli ilgili indirme sayfasından manuel olarak da indirebilirsiniz.

---

## ▶️ Kullanım

Model yüklendikten sonra `AiMain.py` çalıştırılabilir:

```bash
python AiMain.py
```

Program görüntüyü analiz ederek tespit edilen nesneleri belirler.

Örneğin:

```text
0) car
1) car
0) person
1) bicycle
```

şeklinde yol kullanıcılarını listeleyebilir.

---

## 🔍 Nasıl Çalışıyor?

Projenin temel çalışma mantığı şu şekildedir:

```text
             Görüntü
                │
                ▼
        ┌───────────────┐
        │   YOLOv3      │
        │ Object        │
        │ Detection     │
        └───────┬───────┘
                │
                ▼
        Tespit Edilen
           Nesneler
                │
                ▼
        ┌───────────────┐
        │ Nesne Analizi  │
        └───────┬───────┘
                │
                ▼
     ┌─────────────────────┐
     │ Yol Kullanıcıları   │
     │                     │
     │ Car / Bus / Truck   │
     │ Person / Bicycle    │
     │ Train               │
     └──────────┬──────────┘
                │
                ▼
        Yol Güvenliği
           Uyarıları
```

### Nesne tespiti

`detectOnRoad()` fonksiyonu verilen görüntüyü YOLOv3 modeli ile analiz eder:

```python
detections = detector.detectObjectsFromImage(
    input_image=image,
    output_image_path="output_image.jpg",
    minimum_percentage_probability=40
)
```

`minimum_percentage_probability=40` değeri, belirli bir güven seviyesinin altındaki tespitlerin filtrelenmesini sağlar.

---

## 🛣️ Yol Güvenliği

Proje, temel yol güvenliği konusunda kullanıcıya bilgilendirici mesajlar da verebilir.

Örneğin:

```text
SafetyAI size iyi yolculuklar diler.

Emniyet kemerlerinizi bağlayınız.

Hız Sınırlarına dikkat ediniz.

Yaya geçitlerinde yayalara yol veriniz.

Kırmızı Işıklarda durduğunuz gibi sarıda da durunuz.
```

Bu mesajlar **bilgilendirme amaçlıdır** ve profesyonel sürüş güvenliği sistemlerinin yerine geçmez.

---

## 🧪 Örnek Kullanım

Bir yol görüntüsü:

```text
yol.jpg
```

modele gönderildiğinde sistem görüntüdeki nesneleri tespit eder ve ilgili nesneleri filtreler.

Örnek çıktı:

```text
Tespit edilenler:

0) car
1) car
2) truck
0) person
1) bicycle
```

Ayrıca analiz sonucunda işlenmiş görüntü:

```text
output_image.jpg
```

olarak oluşturulur.

---

## 📌 Gelecek Geliştirmeler

Proje daha gelişmiş bir yol güvenliği sistemine dönüştürülebilir.

Planlanabilecek özellikler:

- [ ] Gerçek zamanlı kamera desteği
- [ ] Video üzerinde nesne takibi
- [ ] Trafik ışığı tespiti
- [ ] Hız tahmini
- [ ] Şerit tespiti
- [ ] Yaya geçidi tespiti
- [ ] Plaka tespiti
- [ ] Tehlikeli durum algılama
- [ ] Gerçek zamanlı sesli uyarılar
- [ ] Web arayüzü
- [ ] Mobil uygulama desteği
- [ ] Daha güncel YOLO modellerine geçiş
- [ ] Nesne takip algoritmalarının eklenmesi

---

## ⚠️ Sınırlamalar

Bu proje küçük ve deneysel bir çalışmadır.

Nesne tespitinin doğruluğu;

- görüntü kalitesine,
- ışık koşullarına,
- kamera açısına,
- nesnenin görüntü içerisindeki boyutuna,
- kullanılan YOLOv3 modelinin eğitim verilerine

bağlı olarak değişebilir.

Bu nedenle proje çıktıları **kritik güvenlik kararları için tek başına kullanılmamalıdır.**

---

## 🤝 Katkıda Bulunma

Projeyi geliştirmek isterseniz:

1. Repository'yi fork edin.
2. Yeni bir branch oluşturun.

```bash
git checkout -b feature/yeni-ozellik
```

3. Değişikliklerinizi yapın.
4. Commit oluşturun.

```bash
git commit -m "Yeni özellik eklendi"
```

5. Branch'inizi gönderin.

```bash
git push origin feature/yeni-ozellik
```

6. Pull Request oluşturun.

---

## 📄 Lisans

Bu proje **MIT License** ile lisanslanmıştır.

Detaylar için [`LICENSE`](LICENSE) dosyasına bakabilirsiniz.

---

## 👨‍💻 Geliştirici

**Asu-developer**

GitHub:  
https://github.com/Asu-developer

---

## ⭐ Destek

Projeyi faydalı bulduysanız GitHub üzerinde ⭐ bırakabilirsiniz.

Katkılar, öneriler ve geliştirme fikirleri memnuniyetle karşılanır.

---

**Simple-AI — Yapay zekâ ile daha güvenli yollar için küçük bir adım. 🚗🤖**
