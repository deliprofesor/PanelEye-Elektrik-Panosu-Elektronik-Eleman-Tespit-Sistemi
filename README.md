# PanelEye-Elektrik-Panosu-Elektronik-Eleman-Tespit-Sistemi
# PanelEye – Elektrik Panosu Elektronik Eleman Tespit Sistemi

PanelEye, endüstriyel elektrik panolarında bulunan elektronik elemanların **otomatik olarak tespit edilmesini**, sınıflandırılmasını ve görsel olarak işaretlenmesini sağlayan bir görüntü işleme ve yapay zeka tabanlı analiz sistemidir.

##  Proje Amacı

Endüstriyel otomasyon ortamlarında, elektrik panolarının kontrolü sırasında;

- Hatalı montaj,
- Eksik bileşen,
- Yanlış yerleştirme,
- Yanlış bağlantı

gibi sorunlar kritik önem taşır. **PanelEye**, bu kontrolleri manuel süreçlerden çıkararak, gerçek zamanlı ve yüksek doğrulukta otomatik bir denetim sistemi sunar.

##  Kullanılan Teknolojiler

| Teknoloji     | Açıklama |
|---------------|----------|
| Python        | Projenin ana geliştirme dili |
| OpenCV        | Görüntü işleme ve filtreleme işlemleri |
| YOLOv5        | Elektronik elemanların nesne tespiti (custom model) |
| DeepSORT      | Tespit edilen elemanların takibi |
| PyQt5         | Kullanıcı arayüzü geliştirme |
| Matplotlib    | Isı haritaları ve sonuç görselleştirme |
| MQTT          | Gerçek zamanlı veri aktarımı (isteğe bağlı) |

##  Model Eğitimi

Model, endüstriyel elektrik panolarında bulunan elemanların (sigorta, kontaktör, röle, PLC modülü, vb.) görüntüleriyle eğitilmiştir. Aşağıdaki adımlar izlenmiştir:

1. **Veri Toplama:** Gerçek elektrik panolarından yüksek çözünürlüklü görüntüler alındı.
2. **Veri Etiketleme:** LabelImg ile her bir bileşen etiketlendi.
3. **Model Eğitimi:** YOLOv5 kullanılarak sınıflandırma ve nesne tespiti modeli eğitildi.
4. **Model Testi:** Saha görüntüleri ile model doğrulandı (mAP@0.5 > %95).

##  Sistem Mimarisi

```mermaid
flowchart TD
  A[Görüntü Alımı] --> B[Görüntü Ön İşleme]
  B --> C[Nesne Tespiti (YOLOv5)]
  C --> D[Takip ve Eşleme (DeepSORT)]
  D --> E[Sonuçların Görselleştirilmesi ve Raporlama]
  E --> F[İsteğe Bağlı: MQTT ile Uyarı Gönderimi]
