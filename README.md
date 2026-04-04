# ⚡ Smart EDA Stress Monitor v2.0

Bu proje, insan derisindeki elektriksel aktivite (Electrodermal Activity - EDA) değişimlerini ölçerek stres seviyesini analiz eden bir biyosensör prototipidir. v2.0 sürümünde, daha kararlı bir sinyal işleme katmanı ve modern bir PCB tasarımı hedeflenmiştir.

This project is a biosensor prototype that analyzes stress levels by measuring changes in Electrodermal Activity (EDA). In version 2.0, a more stable signal processing layer and a modern PCB design were targeted.

---

## 🚀 Öğrenme Yolculuğum / My Learning Journey
Bu proje, donanım tasarımı konusundaki **öğrenme ve gelişim sürecimin** önemli bir parçasıdır. İlk versiyondaki hatalardan ders çıkararak; daha temiz bir layout, optimize edilmiş sinyal yolları ve endüstriyel standartlara yakın bir PCB tasarımı hedefledim. Sürekli deneme ve iyileştirme üzerine kurulu bu süreçte, teorik bilgimi somut bir ürüne dönüştürmeyi amaçladım.

This project is a key part of my **continuous learning journey** in hardware design. By learning from previous iterations, I aimed for a cleaner layout, optimized signal paths, and a production-ready PCB design.

---

## 📸 Proje Görselleri / Project Visuals

### 1. 3D Model Tasarımı / 3D Model Design
![3D Görünüm](3D.png)
*KiCad 3D Viewer kullanılarak hazırlanan, modern bileşen yerleşimine sahip nihai ürün prototipi.*
*Final product prototype with modern component placement prepared using KiCad 3D Viewer.*

### 2. Devre Şeması / Schematic Diagram
![Şema](Schematic.png)
*LM358 Op-Amp sinyal koşullama ve L7805 voltaj regülatör katmanlarını içeren elektriksel tasarım.*
*Electrical design including LM358 Op-Amp signal conditioning and L7805 voltage regulator stages.*

### 3. PCB Yolları ve Yerleşim / PCB Layout & Routing
![PCB Tasarımı](PCB.png)
*Gürültü bağışıklığı için optimize edilmiş, kompakt PCB tasarımı. Sinyal bütünlüğü için ground plane uygulaması yapılmıştır.*
*Compact PCB design optimized for noise immunity, featuring a ground plane for signal integrity.*

---

## 🛠 Teknik Detaylar / Technical Details

### Donanım Bileşenleri / Hardware Components:
- **MCU:** Arduino Nano (ATmega328P)
- **Amplifier:** LM358 Op-Amp (Sinyal yükseltme ve aktif filtreleme için / For signal amplification and active filtering)
- **Power Management:** L7805 Voltage Regulator (Stabil 5V çıkış sağlar / Provides stable 5V output)
- **Sensor:** Deri direnci değişimlerini voltaj bölücü prensibiyle okuyan elektrotlar / Electrodes working with voltage divider principle.

### Tasarım Kararları / Design Decisions:
- **Iterative Improvement:** Tasarım, daha iyi bir estetik ve teknik kararlılık için yeniden revize edilmiştir.
- **Signal Quality:** Hassas analog yollar, paraziti önlemek adına mümkün olduğunca kısa tutulmuştur.

---

## 💻 Yazılım Mantığı / Software Logic

Arduino, LM358'den gelen yükseltilmiş analog veriyi **A0** pini üzerinden okur. / Arduino reads the amplified analog data from the LM358 via the **A0** pin.

```cpp
void setup() {
  Serial.begin(9600); // Seri haberleşme başlatıldı / Serial communication started
}

void loop() {
  int sensorValue = analogRead(A0); // A0 pininden veri oku / Read data from A0 pin
  Serial.println(sensorValue);      // Veriyi gönder / Send data for plotting
  delay(50);                        // Akıcı bir izleme için gecikme / Delay for smooth monitoring
}

