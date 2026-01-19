# Bilgi Guvenligi Soru Havuzu

## 2.1 CIA Uclusu (10 Soru)

### Soru 2.1.1
**Konu:** CIA Tanimi
**S:** CIA uclusunun aciilimi nedir?
**C:** Confidentiality (Gizlilik), Integrity (Butunluk), Availability (Erisilebilirlik)

### Soru 2.1.2
**Konu:** Confidentiality
**S:** Confidentiality (Gizlilik) ne anlama gelir?
**C:** Bilgiye sadece yetkili kisilerin erisebilmesi

### Soru 2.1.3
**Konu:** Integrity
**S:** Integrity (Butunluk) ne anlama gelir?
**C:** Verinin izinsiz degistirilmemesi, dogrulugu ve tamliginin korunmasi

### Soru 2.1.4
**Konu:** Availability
**S:** Availability (Erisilebilirlik) ne anlama gelir?
**C:** Sistemin her zaman calisir durumda olmasi

### Soru 2.1.5
**Konu:** Confidentiality Koruma
**S:** Confidentiality icin hangi koruma yontemleri kullanilir?
**C:** Sifreleme, Erisim Kontrolu, Kimlik Dogrulama

### Soru 2.1.6
**Konu:** Integrity Koruma
**S:** Integrity icin hangi koruma yontemleri kullanilir?
**C:** Hash, Dijital Imza, Checksum

### Soru 2.1.7
**Konu:** Availability Koruma
**S:** Availability icin hangi koruma yontemleri kullanilir?
**C:** Yedekleme, DDoS Korumasi, Felaket Kurtarma, HA

### Soru 2.1.8
**Konu:** CIA Tehdit
**S:** Veri sizintisi CIA'nin hangi unsurunu tehdit eder?
**C:** Confidentiality (Gizlilik)

### Soru 2.1.9
**Konu:** CIA Tehdit
**S:** Veri manipulasyonu CIA'nin hangi unsurunu tehdit eder?
**C:** Integrity (Butunluk)

### Soru 2.1.10
**Konu:** CIA Tehdit
**S:** DDoS saldirisi CIA'nin hangi unsurunu hedefler?
**C:** Availability (Erisilebilirlik)

---

## 2.2 OWASP Top 10 (12 Soru)

### Soru 2.2.1
**Konu:** OWASP Top 10 #1
**S:** OWASP Top 10 (2021) listesinde 1. sirada ne var?
**C:** Broken Access Control (Yetkisiz kaynak erisimi)

### Soru 2.2.2
**Konu:** OWASP Top 10 #2
**S:** OWASP Top 10'da "Cryptographic Failures" ne anlama gelir?
**C:** Zayif veya eksik sifreleme kullanimi

### Soru 2.2.3
**Konu:** OWASP Top 10 #3
**S:** OWASP Top 10'da Injection hangi sirada?
**C:** 3. sirada

### Soru 2.2.4
**Konu:** OWASP Top 10 #3
**S:** Injection saldirisi ne demektir?
**C:** Zararli kod enjeksiyonu (SQL, XSS, Command)

### Soru 2.2.5
**Konu:** OWASP Top 10 #4
**S:** "Insecure Design" ne anlama gelir?
**C:** Tasarim hatalari, guvenlik dusunulmeden yazilim gelistirme

### Soru 2.2.6
**Konu:** OWASP Top 10 #5
**S:** "Security Misconfiguration" ne anlama gelir?
**C:** Yanlis yapilandirma (varsayilan sifreler, gereksiz servisler vb.)

### Soru 2.2.7
**Konu:** OWASP Top 10 #6
**S:** "Vulnerable and Outdated Components" ne demektir?
**C:** Eski ve zafiyetli bilesenler kullanmak

### Soru 2.2.8
**Konu:** OWASP Top 10 #7
**S:** "Identification and Authentication Failures" ne demektir?
**C:** Kimlik dogrulama hatalari (zayif sifre, brute force korumasi yok)

### Soru 2.2.9
**Konu:** OWASP Top 10 #8
**S:** "Software and Data Integrity Failures" ne demektir?
**C:** Yazilim ve veri butunluk kontrolu eksikligi

### Soru 2.2.10
**Konu:** OWASP Top 10 #9
**S:** "Security Logging and Monitoring Failures" ne demektir?
**C:** Yetersiz loglama ve izleme

### Soru 2.2.11
**Konu:** OWASP Top 10 #10
**S:** SSRF'nin acilimi nedir?
**C:** Server-Side Request Forgery (Sunucu tarafli istek sahteciligi)

### Soru 2.2.12
**Konu:** OWASP Top 10
**S:** SQL Injection hangi OWASP kategorisinde?
**C:** Injection (#3)

---

## 2.3 Network Saldirilari (10 Soru)

### Soru 2.3.1
**Konu:** DDoS
**S:** DDoS saldirisinin acilimi ve tanimi nedir?
**C:** Distributed Denial of Service - Cok sayida kaynaktan asiri trafik ile sistemi cokertme

### Soru 2.3.2
**Konu:** DoS
**S:** DoS ve DDoS arasindaki fark nedir?
**C:** DoS tek kaynaktan, DDoS dagitik (cok sayida) kaynaktan gelir

### Soru 2.3.3
**Konu:** MITM
**S:** Man-in-the-Middle saldirisi ne yapar?
**C:** Iletisime araya girerek veri calar veya degistirir

### Soru 2.3.4
**Konu:** MITM
**S:** MITM CIA'nin hangi unsurunu tehdit eder?
**C:** Confidentiality (Gizlilik)

### Soru 2.3.5
**Konu:** Sniffing
**S:** Sniffing ne demektir?
**C:** Ag trafigini dinleme/yakalama

### Soru 2.3.6
**Konu:** Sniffing
**S:** Sniffing hangi CIA unsurunu tehdit eder?
**C:** Confidentiality (Gizlilik)

### Soru 2.3.7
**Konu:** ARP Spoofing
**S:** ARP Spoofing ne yapar?
**C:** ARP tablosunu zehirleyerek trafigi yonlendirir

### Soru 2.3.8
**Konu:** DNS Spoofing
**S:** DNS Spoofing ne yapar?
**C:** DNS yanitlarini degistirerek yanlis siteye yonlendirir

### Soru 2.3.9
**Konu:** DNS Spoofing
**S:** DNS Spoofing hangi CIA unsurunu hedefler?
**C:** Integrity (Butunluk)

### Soru 2.3.10
**Konu:** IP Spoofing
**S:** IP Spoofing ne yapar?
**C:** Kaynak IP adresini taklit ederek saldiri yapar

---

## 2.4 Web Saldirilari (10 Soru)

### Soru 2.4.1
**Konu:** SQL Injection
**S:** SQL Injection nedir?
**C:** Veritabanina zararli SQL kodu enjekte etme

### Soru 2.4.2
**Konu:** SQL Injection
**S:** SQL Injection ornegi nedir?
**C:** ' OR '1'='1 (veya benzer mantiksal manipulasyonlar)

### Soru 2.4.3
**Konu:** XSS
**S:** XSS'nin acilimi nedir?
**C:** Cross-Site Scripting

### Soru 2.4.4
**Konu:** XSS
**S:** XSS saldirisi ne yapar?
**C:** Web sayfasina zararli JavaScript enjekte eder

### Soru 2.4.5
**Konu:** CSRF
**S:** CSRF'nin acilimi nedir?
**C:** Cross-Site Request Forgery

### Soru 2.4.6
**Konu:** CSRF
**S:** CSRF saldirisi ne yapar?
**C:** Kullanici adina istenmeyen istekler gonderir

### Soru 2.4.7
**Konu:** Directory Traversal
**S:** Directory Traversal saldirisi ne yapar?
**C:** ../ kullanarak dosya sistemine yetkisiz erisim saglar

### Soru 2.4.8
**Konu:** Command Injection
**S:** Command Injection ne yapar?
**C:** Isletim sistemi komutu calistirir

### Soru 2.4.9
**Konu:** LFI
**S:** LFI'nin acilimi nedir?
**C:** Local File Inclusion (Yerel dosya dahil etme)

### Soru 2.4.10
**Konu:** RFI
**S:** RFI'nin acilimi nedir?
**C:** Remote File Inclusion (Uzak dosya dahil etme)

---

## 2.5 Sosyal Muhendislik (10 Soru)

### Soru 2.5.1
**Konu:** Phishing
**S:** Phishing nedir?
**C:** Sahte e-posta/site ile kimlik bilgisi calma

### Soru 2.5.2
**Konu:** Spear Phishing
**S:** Spear Phishing nedir?
**C:** Belirli bir kisi veya kuruma yonelik hedefli phishing

### Soru 2.5.3
**Konu:** Whaling
**S:** Whaling nedir?
**C:** Ust duzey yoneticilere yonelik phishing

### Soru 2.5.4
**Konu:** Vishing
**S:** Vishing nedir?
**C:** Telefon ile dolandiricilik (Voice + Phishing)

### Soru 2.5.5
**Konu:** Smishing
**S:** Smishing nedir?
**C:** SMS ile phishing saldirisi

### Soru 2.5.6
**Konu:** Pretexting
**S:** Pretexting nedir?
**C:** Sahte senaryo olusturarak bilgi toplama

### Soru 2.5.7
**Konu:** Baiting
**S:** Baiting nedir?
**C:** Sahte USB/CD birakarak tuzak kurma

### Soru 2.5.8
**Konu:** Tailgating
**S:** Tailgating nedir?
**C:** Yetkili birinin arkasindan fiziksel olarak girme

### Soru 2.5.9
**Konu:** Tailgating
**S:** Tailgating ne tur bir saldiridir?
**C:** Sosyal muhendislik (fiziksel guvenlik ihlali)

### Soru 2.5.10
**Konu:** Sosyal Muhendislik
**S:** Sosyal muhendisligin ortak ozelligi nedir?
**C:** Insan faktorunu kullanarak guvenlik atlatma

---

## 2.6 Simetrik Sifreleme (5 Soru)

### Soru 2.6.1
**Konu:** Simetrik Tanim
**S:** Simetrik sifreleme nedir?
**C:** Sifreleme ve desifreleme icin ayni anahtarin kullanildigi yontem

### Soru 2.6.2
**Konu:** Simetrik Anahtar
**S:** Simetrik sifreleme kac anahtar kullanir?
**C:** 1 anahtar

### Soru 2.6.3
**Konu:** Simetrik Algoritmalar
**S:** Simetrik sifreleme ornekleri nelerdir?
**C:** AES, DES, 3DES, RC4

### Soru 2.6.4
**Konu:** AES
**S:** AES hangi sifreleme turu?
**C:** Simetrik sifreleme

### Soru 2.6.5
**Konu:** Simetrik Dezavantaj
**S:** Simetrik sifrelemedeki temel sorun nedir?
**C:** Anahtar dagitimi (anahtari guvenli sekilde iletmek zor)

---

## 2.7 Asimetrik Sifreleme (5 Soru)

### Soru 2.7.1
**Konu:** Asimetrik Tanim
**S:** Asimetrik sifreleme nedir?
**C:** Public (acik) ve Private (ozel) olmak uzere 2 farkli anahtar kullanan yontem

### Soru 2.7.2
**Konu:** Asimetrik Anahtar
**S:** Asimetrik sifreleme kac anahtar kullanir?
**C:** 2 anahtar (public ve private)

### Soru 2.7.3
**Konu:** Asimetrik Algoritmalar
**S:** Asimetrik sifreleme ornekleri nelerdir?
**C:** RSA, ECC, DSA

### Soru 2.7.4
**Konu:** RSA
**S:** RSA hangi sifreleme turu?
**C:** Asimetrik sifreleme

### Soru 2.7.5
**Konu:** Asimetrik Kullanim
**S:** Asimetrik sifreleme ne icin kullanilir?
**C:** Anahtar degisimi, dijital imza

---

## 2.8 Hash Fonksiyonlari (6 Soru)

### Soru 2.8.1
**Konu:** Hash Tanim
**S:** Hash fonksiyonu nedir?
**C:** Girdiyi sabit uzunlukta, tek yonlu ciktiya donusturen fonksiyon

### Soru 2.8.2
**Konu:** Hash Ozellik
**S:** Hash fonksiyonu tersine cevrilebilir mi?
**C:** Hayir, tek yonludur

### Soru 2.8.3
**Konu:** MD5
**S:** MD5'in cikti uzunlugu ve guvenlik durumu nedir?
**C:** 128 bit, zayif (kullanilmamali)

### Soru 2.8.4
**Konu:** SHA-1
**S:** SHA-1'in cikti uzunlugu ve guvenlik durumu nedir?
**C:** 160 bit, zayif

### Soru 2.8.5
**Konu:** SHA-256
**S:** SHA-256'nin cikti uzunlugu ve guvenlik durumu nedir?
**C:** 256 bit, guclu

### Soru 2.8.6
**Konu:** bcrypt
**S:** bcrypt ne icin kullanilir?
**C:** Parola hashleme icin ideal

---

## 2.9 Dijital Imza (3 Soru)

### Soru 2.9.1
**Konu:** Dijital Imza Islemi
**S:** Dijital imza nasil olusturulur?
**C:** Mesajin hash'i, gonderenin private key'i ile sifrelenir

### Soru 2.9.2
**Konu:** Dijital Imza Dogrulama
**S:** Dijital imza nasil dogrulanir?
**C:** Imza, gonderenin public key'i ile acilir, hesaplanan hash ile karsilastirilir

### Soru 2.9.3
**Konu:** Dijital Imza Sagladiklari
**S:** Dijital imza neyi saglar?
**C:** Butunluk (Integrity), Kimlik dogrulama, Inkar edilemezlik

---

## 2.10 Kimlik Dogrulama Faktorleri (4 Soru)

### Soru 2.10.1
**Konu:** Know
**S:** "Something you know" ne demektir?
**C:** Bildigin bir sey (Parola, PIN)

### Soru 2.10.2
**Konu:** Have
**S:** "Something you have" ne demektir?
**C:** Sahip oldugun sey (Token, Akilli kart, Telefon)

### Soru 2.10.3
**Konu:** Are
**S:** "Something you are" ne demektir?
**C:** Oldugun sey (Parmak izi, Retina, Yuz tanima - Biyometrik)

### Soru 2.10.4
**Konu:** Where
**S:** "Somewhere you are" ne demektir?
**C:** Bulundugun yer (GPS, IP lokasyonu)

---

## 2.11 MFA ve 2FA (2 Soru)

### Soru 2.11.1
**Konu:** MFA
**S:** MFA ne demektir?
**C:** Multi-Factor Authentication - 2 veya daha fazla faktorle kimlik dogrulama

### Soru 2.11.2
**Konu:** 2FA
**S:** 2FA ne demektir?
**C:** Two-Factor Authentication - Tam olarak 2 faktorle kimlik dogrulama

---

## 2.12 AAA (3 Soru)

### Soru 2.12.1
**Konu:** AAA Tanim
**S:** AAA'nin acilimi nedir?
**C:** Authentication, Authorization, Accounting

### Soru 2.12.2
**Konu:** Authentication
**S:** AAA'da Authentication ne yapar?
**C:** Kim oldugunu dogrular

### Soru 2.12.3
**Konu:** Authorization ve Accounting
**S:** AAA'da Authorization ve Accounting ne yapar?
**C:** Authorization: Ne yapabilecegini belirler, Accounting: Ne yaptigini kaydeder

---

## 2.13 Erisim Kontrol Modelleri (5 Soru)

### Soru 2.13.1
**Konu:** DAC
**S:** DAC ne demektir?
**C:** Discretionary Access Control - Sahibi izinleri belirler (Unix dosya izinleri)

### Soru 2.13.2
**Konu:** MAC
**S:** MAC ne demektir?
**C:** Mandatory Access Control - Sistem etiketlere gore karar verir (SELinux, Askeri)

### Soru 2.13.3
**Konu:** RBAC
**S:** RBAC ne demektir?
**C:** Role-Based Access Control - Rol bazli erisim kontrolu

### Soru 2.13.4
**Konu:** ABAC
**S:** ABAC ne demektir?
**C:** Attribute-Based Access Control - Ozellik bazli erisim kontrolu

### Soru 2.13.5
**Konu:** RBAC Kullanim
**S:** Kurumsal sistemlerde en yaygin kullanilan erisim kontrol modeli hangisi?
**C:** RBAC (Rol bazli)

---

## 2.14 Guvenlik Araclari (10 Soru)

### Soru 2.14.1
**Konu:** Firewall
**S:** Firewall ne ise yarar?
**C:** Ag trafigini kurallara gore filtreler (izin/engel)

### Soru 2.14.2
**Konu:** IDS
**S:** IDS ne demektir ve ne yapar?
**C:** Intrusion Detection System - Saldiri tespit eder

### Soru 2.14.3
**Konu:** IPS
**S:** IPS ne demektir ve ne yapar?
**C:** Intrusion Prevention System - Saldiri tespit eder ve engeller

### Soru 2.14.4
**Konu:** IDS vs IPS
**S:** IDS ve IPS arasindaki fark nedir?
**C:** IDS: Sadece tespit eder, IPS: Tespit eder + Engeller

### Soru 2.14.5
**Konu:** WAF
**S:** WAF ne demektir?
**C:** Web Application Firewall - Web uygulama guvenlik duvari

### Soru 2.14.6
**Konu:** SIEM
**S:** SIEM ne demektir ve ne yapar?
**C:** Security Information and Event Management - Log toplama ve analiz

### Soru 2.14.7
**Konu:** DLP
**S:** DLP ne demektir?
**C:** Data Loss Prevention - Veri kaybi onleme

### Soru 2.14.8
**Konu:** VPN
**S:** VPN ne saglar?
**C:** Sifreli tunel ile guvenli uzak erisim

### Soru 2.14.9
**Konu:** Proxy
**S:** Proxy ne ise yarar?
**C:** Istemci adina istekleri yonlendirir

### Soru 2.14.10
**Konu:** HSM
**S:** HSM ne demektir?
**C:** Hardware Security Module - Donanimsal anahtar korumasi

---

## 2.15 Guvenlik Standartlari (4 Soru)

### Soru 2.15.1
**Konu:** ISO 27001
**S:** ISO 27001 nedir?
**C:** Bilgi Guvenligi Yonetim Sistemi (BGYS) standardi

### Soru 2.15.2
**Konu:** PCI-DSS
**S:** PCI-DSS nedir?
**C:** Kredi karti verisi guvenligi standardi

### Soru 2.15.3
**Konu:** GDPR
**S:** GDPR nedir?
**C:** Avrupa Birligi kisisel veri koruma yonetmeligi

### Soru 2.15.4
**Konu:** KVKK
**S:** KVKK nedir?
**C:** Turkiye kisisel verilerin korunmasi kanunu

---

## OZET

| Konu | Soru Sayisi |
|------|-------------|
| 2.1 CIA Uclusu | 10 |
| 2.2 OWASP Top 10 | 12 |
| 2.3 Network Saldirilari | 10 |
| 2.4 Web Saldirilari | 10 |
| 2.5 Sosyal Muhendislik | 10 |
| 2.6 Simetrik Sifreleme | 5 |
| 2.7 Asimetrik Sifreleme | 5 |
| 2.8 Hash Fonksiyonlari | 6 |
| 2.9 Dijital Imza | 3 |
| 2.10 Kimlik Dogrulama | 4 |
| 2.11 MFA/2FA | 2 |
| 2.12 AAA | 3 |
| 2.13 Erisim Kontrol | 5 |
| 2.14 Guvenlik Araclari | 10 |
| 2.15 Guvenlik Standartlari | 4 |
| **TOPLAM** | **89** |
