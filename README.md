# goruntudenduygutanima

# Giriş

Farklı kategorilerde yüz ifadeleri bulunan görsel bir veri seti kullanıldı. 8 duygu kategorisinde toplam 153 veri bulunmakta. Modelimi bu yüz ifadelerini tanıyabilecek şekilde kurguladım. 


# Metrikler
<img width="1029" height="619" alt="image" src="https://github.com/user-attachments/assets/6194d0d9-bc28-4814-8045-6b874ded35a2" />


Bu çalışmada, görsellerden duygu tanıma yapan basit bir CNN modeli kurup uçtan uca çalıştırmayı hedefledim. Görüntüler RGB’ye çevrilip float32 formatında 0–1 aralığına ölçekleniyor; giriş boyutu IMG_SIZE × IMG_SIZE × 3. 

Test Loss: 2.0447

Test Accuracy: 0.1538 (≈ %15.38)

Eğitim loglarında validation accuracy uzun süre ~0.0769 civarında seyretti; bu da modelin validasyonda sınıfları ayırt etmekte zorlandığını gösteriyor.

Veri sayısının az olması, modelin dengeli çalışmasını biraz zorlaştırıyor. Keras 3 ile tam modeli .keras formatında kaydetmek, .h5’te karşıma çıkan serileştirme hatalarını çözmeye çalıştım.

# Ekler

Yüklenen görsel: RGB’ye çevrilir → IMG_SIZE’a yeniden ölçeklenir → float32 → /255.0 → (1, H, W, 3) şeklinde modele verilir.

Çıktı: sınıf olasılıkları + en yüksek olasılıklı etiket.
Classification report (macro/micro metrikler, sınıf bazlı precision/recall)

Karışıklık matrisi (ham ve normalize) görselleştirildi

Doğru/yanlış tahmin gridleri (teşhis için çok faydalı) raporlarını kullandım.

# Sonuç ve Gelecek Çalışmalar

Modeli çalıştırdığımda başta farklı sonuçlar alıyordum ancak sonra gerçekleştirdiğim revizelerin ardından sonuçlar, veri ölçeği ve dengesizlik nedeniyle hedeflenen doğruluğa ulaşamadı; model zaman zaman “Neutral” sınıfına çökme eğilimi gösterdi. Yine de bu süreç, doğru önişleme, dengesizlik yönetimi ve Keras’ın modern kayıt/yükleme pratikleri açısından sağlam bir temel oluşturdu. Bir sonraki aşamada daha önce eğitilmiş modelleri de tanımlayarak tutarlılığını daha iyi ölçmeye, gerçek zamanlı verilerle modeli eğitmeyi amaçlıyorum.

# Linkler

Görselden Duygu Tanımlama: https://www.kaggle.com/code/nilayyanardag/g-rselden-duygu-tan-mlama
