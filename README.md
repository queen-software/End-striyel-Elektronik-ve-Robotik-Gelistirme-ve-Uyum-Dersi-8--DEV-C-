    # End-striyel-Elektronik-ve-Robotik-Gelistirme-ve-Uyum-Dersi-8--DEV-C++
   ## Fotoresistör
    int ldr =A0;
    int kirmizi_led=2;
    int sari_led=3;
    int mavi_led=4;
    void setup()
    {
      pinMode(kirmizi_led, OUTPUT);
       pinMode(sari_led, OUTPUT);
       pinMode(mavi_led, OUTPUT);
      pinMode(ldr,INPUT);
      Serial.begin(9600);
      
    }
    
    void loop()
    {
    double parlaklik =analogRead(ldr);
      Serial.print("Parlaklık : ");
      Serial.println(parlaklik);
      if(parlaklik<226){
        digitalWrite(kirmizi_led,HIGH);
    
      }else if(parlaklik>226&&parlaklik <=453){
        digitalWrite(sari_led,HIGH);
      }else{
        digitalWrite(mavi_led,HIGH);
      }
    }









    int ldr = A0;
    int ledler[] = {2, 3, 4};
    
    void setup() {
      for (int i = 0; i < 3; i++)pinMode(ledler[i], OUTPUT);
      Serial.begin(9600);
    }
    
    void loop() {
      int parlaklik = analogRead(ldr);
      Serial.println(parlaklik);
    
      int seviye;
      if (parlaklik < 226) seviye = 0;       // kırmızı
      else if (parlaklik <= 453) seviye = 1; // sarı
      else seviye = 2;                       // mavi
    
      for (int i = 0; i < 3; i++)
        digitalWrite(ledler[i], i == seviye ? HIGH : LOW);
    
      delay(100);
    }


## TMP VE LCD EKRAN
    #include <Wire.h>
    #include <LiquidCrystal_I2C.h>
    
    // LCD adresi (I2C Scanner ile kontrol et), 16x2 boyut
    LiquidCrystal_I2C lcd(0x27, 16, 2);
    
    int sensorPin = A1;  // TMP36 çıkışı
    float voltage, temperature;
    
    void setup() {
      lcd.init();     // LCD başlat
      lcd.backlight();       // Arka ışığı aç
      lcd.setCursor(0, 0);
      lcd.print("Sicaklik Olcme");
      delay(2000);
      lcd.clear();
    }
    
    void loop() {
      int sensorValue = analogRead(sensorPin);
      voltage = sensorValue * (5.0 / 1023.0);       // ADC → Volt
      temperature = (voltage - 0.5) * 100.0;       // TMP36 formülü
    
      lcd.setCursor(0, 0);
      lcd.print("Sicaklik:       ");               // Önce boşlukla temizle
      lcd.setCursor(0, 1);
      lcd.print(temperature, 1);                    // 1 ondalık göster
      lcd.print((char)223);                         // Derece sembolü
      lcd.print("C");
    
      delay(1000);
    }
   
    
<img width="1495" height="809" alt="image" src="https://github.com/user-attachments/assets/699bdb0e-4c9f-4995-aa24-02b4f7e29078" />

    
    







    
