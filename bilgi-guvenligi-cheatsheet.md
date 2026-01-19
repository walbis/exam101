# Bilgi Güvenliği Cheat Sheet

## CIA Üçlüsü (Temel Prensip)

```
┌─────────────────────────────────────────────────────────────────────┐
│                         CIA ÜÇLÜSÜ                                  │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│    CONFIDENTIALITY          INTEGRITY           AVAILABILITY        │
│       (Gizlilik)           (Bütünlük)          (Erişilebilirlik)    │
│                                                                     │
│    Yetkisiz erişimi      Verinin doğruluğu    Sistemin çalışır     │
│    engelleme             ve tamlığını         durumda olması       │
│                          koruma                                     │
│                                                                     │
│    Şifreleme             Hash                 Yedekleme             │
│    Erişim Kontrolü       Dijital İmza         DDoS Koruması         │
│    Kimlik Doğrulama      Checksum             Felaket Kurtarma      │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Detaylı Açıklama

| Prensip | Türkçe | Tanım | Tehdit | Koruma |
|---------|--------|-------|--------|--------|
| **C**onfidentiality | Gizlilik | Bilgiye sadece yetkili kişiler erişebilmeli | Veri sızıntısı, Sniffing | Şifreleme, ACL |
| **I**ntegrity | Bütünlük | Veri izinsiz değiştirilmemeli | Veri manipülasyonu | Hash, Dijital imza |
| **A**vailability | Erişilebilirlik | Sistem her zaman çalışır olmalı | DDoS, Donanım arızası | Yedekleme, HA |

---

## OWASP Top 10 (2021)

```
┌────┬──────────────────────────────────────────────────────────────┐
│ #  │  Güvenlik Açığı                    │  Açıklama               │
├────┼────────────────────────────────────┼─────────────────────────┤
│ 1  │ Broken Access Control              │ Yetkisiz kaynak erişimi │
│ 2  │ Cryptographic Failures             │ Zayıf/eksik şifreleme   │
│ 3  │ Injection (SQL, XSS, Command)      │ Zararlı kod enjeksiyonu │
│ 4  │ Insecure Design                    │ Tasarım hataları        │
│ 5  │ Security Misconfiguration          │ Yanlış yapılandırma     │
│ 6  │ Vulnerable/Outdated Components     │ Eski/zafiyetli bileşen  │
│ 7  │ Identification/Auth Failures       │ Kimlik doğrulama hatası │
│ 8  │ Software/Data Integrity Failures   │ Bütünlük kontrol eksik  │
│ 9  │ Security Logging/Monitoring Fail   │ Yetersiz loglama        │
│ 10 │ SSRF (Server-Side Request Forgery) │ Sunucu taraflı istek    │
└────┴────────────────────────────────────┴─────────────────────────┘
```

---

## Yaygın Saldırı Türleri

### Network Saldırıları

```
┌─────────────────────────────────────────────────────────────────────┐
│  Saldırı          │  Açıklama                 │  Hedef CIA         │
├───────────────────┼───────────────────────────┼────────────────────┤
│ DDoS              │ Aşırı trafik ile çökertme │ Availability       │
│ DoS               │ Tek kaynaktan saldırı     │ Availability       │
│ Man-in-the-Middle │ İletişime araya girme     │ Confidentiality    │
│ Sniffing          │ Ağ trafiğini dinleme      │ Confidentiality    │
│ ARP Spoofing      │ ARP tablosunu zehirleme   │ Confidentiality    │
│ DNS Spoofing      │ DNS yanıtlarını değiştir  │ Integrity          │
│ IP Spoofing       │ Kaynak IP'yi taklit       │ Integrity          │
└───────────────────┴───────────────────────────┴────────────────────┘
```

### Web Saldırıları

```
┌─────────────────────────────────────────────────────────────────────┐
│  Saldırı              │  Açıklama                │  Örnek           │
├───────────────────────┼──────────────────────────┼──────────────────┤
│ SQL Injection         │ DB'ye zararlı SQL        │ ' OR '1'='1      │
│ XSS (Cross-Site)      │ Sayfaya script enjekte   │ <script>alert(1) │
│ CSRF                  │ Kullanıcı adına istek    │ Sahte form       │
│ Directory Traversal   │ Dosya sistemi erişimi    │ ../../../etc/    │
│ Command Injection     │ OS komutu çalıştırma     │ ; rm -rf /       │
│ File Inclusion        │ Harici dosya dahil etme  │ LFI/RFI          │
└───────────────────────┴──────────────────────────┴──────────────────┘
```

### Sosyal Mühendislik

```
┌─────────────────────────────────────────────────────────────────────┐
│  Saldırı          │  Açıklama                                       │
├───────────────────┼─────────────────────────────────────────────────┤
│ Phishing          │ Sahte e-posta/site ile kimlik bilgisi çalma     │
│ Spear Phishing    │ Hedefli phishing (belirli kişi/kurum)           │
│ Whaling           │ Üst düzey yöneticilere yönelik phishing         │
│ Vishing           │ Telefon ile dolandırıcılık                      │
│ Smishing          │ SMS ile phishing                                │
│ Pretexting        │ Sahte senaryo ile bilgi toplama                 │
│ Baiting           │ Sahte USB/CD bırakarak tuzak kurma              │
│ Tailgating        │ Yetkili birinin arkasından girme                │
└───────────────────┴─────────────────────────────────────────────────┘
```

---

## Şifreleme (Cryptography)

### Simetrik vs Asimetrik

```
┌─────────────────────────────────────────────────────────────────────┐
│            │  Simetrik               │  Asimetrik                   │
├────────────┼─────────────────────────┼──────────────────────────────┤
│ Anahtar    │  1 anahtar (aynı)       │  2 anahtar (public/private)  │
│ Hız        │  Hızlı                  │  Yavaş                       │
│ Kullanım   │  Veri şifreleme         │  Anahtar değişimi, imza      │
│ Örnekler   │  AES, DES, 3DES, RC4    │  RSA, ECC, DSA               │
│ Sorun      │  Anahtar dağıtımı       │  Performans                  │
└────────────┴─────────────────────────┴──────────────────────────────┘
```

### Hash Fonksiyonları

```
┌─────────────────────────────────────────────────────────────────────┐
│  Özellik              │  Açıklama                                   │
├───────────────────────┼─────────────────────────────────────────────┤
│ Tek yönlü             │ Tersine çevrilemez                          │
│ Sabit çıktı           │ Girdi ne olursa olsun aynı uzunluk          │
│ Deterministik         │ Aynı girdi = aynı çıktı                     │
│ Çığ etkisi            │ Küçük değişiklik = tamamen farklı çıktı     │
├───────────────────────┼─────────────────────────────────────────────┤
│  Algoritma            │  Çıktı Uzunluğu       │  Güvenlik           │
├───────────────────────┼───────────────────────┼─────────────────────┤
│ MD5                   │  128 bit              │  Zayıf (kullanma)   │
│ SHA-1                 │  160 bit              │  Zayıf              │
│ SHA-256               │  256 bit              │  Güçlü              │
│ SHA-512               │  512 bit              │  Çok güçlü          │
│ bcrypt                │  Değişken             │  Parola için ideal  │
└───────────────────────┴───────────────────────┴─────────────────────┘
```

### Dijital İmza

```
1. Gönderici mesajın HASH'ini alır
2. Hash'i kendi PRIVATE KEY ile şifreler (imza)
3. Mesaj + İmza'yı gönderir
4. Alıcı, imzayı göndericinin PUBLIC KEY ile açar
5. Mesajın hash'ini hesaplar ve karşılaştırır
6. Eşleşirse: Bütünlük + Kimlik doğrulanır
```

---

## Kimlik Doğrulama (Authentication)

### Faktörler

```
┌─────────────────────────────────────────────────────────────────────┐
│  Faktör              │  Açıklama              │  Örnek              │
├──────────────────────┼────────────────────────┼─────────────────────┤
│ Something you KNOW   │ Bildiğin bir şey       │ Parola, PIN         │
│ Something you HAVE   │ Sahip olduğun şey      │ Token, Akıllı kart  │
│ Something you ARE    │ Olduğun şey            │ Parmak izi, Retina  │
│ Somewhere you ARE    │ Bulunduğun yer         │ GPS, IP lokasyonu   │
└──────────────────────┴────────────────────────┴─────────────────────┘

MFA (Multi-Factor Authentication): 2 veya daha fazla faktör
2FA (Two-Factor Authentication): Tam olarak 2 faktör
```

### Parola Güvenliği

```
✓ En az 12 karakter
✓ Büyük/küçük harf, rakam, özel karakter
✓ Sözlük kelimesi kullanma
✓ Her hesap için farklı parola
✓ Parola yöneticisi kullan
✓ Düzenli değiştir (veya breach durumunda)
✗ Kişisel bilgi kullanma (doğum tarihi vb.)
```

---

## Güvenlik Kavramları

### AAA (Authentication, Authorization, Accounting)

```
Authentication  → Kim olduğunu doğrula
Authorization   → Ne yapabileceğini belirle
Accounting      → Ne yaptığını kaydet
```

### Erişim Kontrol Modelleri

```
┌─────────────────────────────────────────────────────────────────────┐
│  Model   │  Açıklama                        │  Örnek               │
├──────────┼──────────────────────────────────┼──────────────────────┤
│ DAC      │ Sahibi izinleri belirler         │ Unix dosya izinleri  │
│ MAC      │ Sistem etiketlere göre karar     │ SELinux, Askeri      │
│ RBAC     │ Rol bazlı erişim                 │ Kurumsal sistemler   │
│ ABAC     │ Attribute bazlı (çok faktörlü)   │ Modern bulut         │
└──────────┴──────────────────────────────────┴──────────────────────┘
```

### Defense in Depth (Katmanlı Güvenlik)

```
    ┌─────────────────────────────┐
    │        Fiziksel             │  ← Kapılar, kameralar
    ├─────────────────────────────┤
    │        Network              │  ← Firewall, IDS/IPS
    ├─────────────────────────────┤
    │        Host                 │  ← Antivirus, hardening
    ├─────────────────────────────┤
    │        Application          │  ← WAF, secure coding
    ├─────────────────────────────┤
    │        Data                 │  ← Şifreleme, yedekleme
    └─────────────────────────────┘
```

---

## Güvenlik Araçları

```
┌─────────────────────────────────────────────────────────────────────┐
│  Araç        │  Açıklama                                            │
├──────────────┼──────────────────────────────────────────────────────┤
│ Firewall     │ Ağ trafiğini filtreler (izin/engel)                  │
│ IDS          │ Saldırı tespit eder (Intrusion Detection)            │
│ IPS          │ Saldırı tespit eder ve engeller (Prevention)         │
│ WAF          │ Web uygulama güvenlik duvarı                         │
│ SIEM         │ Log toplama ve analiz (Security Information Event)   │
│ DLP          │ Veri kaybı önleme (Data Loss Prevention)             │
│ Antivirus    │ Zararlı yazılım tespiti                              │
│ VPN          │ Şifreli tünel (Virtual Private Network)              │
│ Proxy        │ İstemci adına istekleri yönlendirir                  │
│ HSM          │ Donanımsal anahtar koruması                          │
└──────────────┴──────────────────────────────────────────────────────┘
```

---

## Flashcardlar

### Soru 1
**S:** CIA'da "C" ne anlama gelir?
**C:** Confidentiality (Gizlilik)

### Soru 2
**S:** DDoS saldırısı CIA'nın hangi unsurunu hedefler?
**C:** Availability (Erişilebilirlik)

### Soru 3
**S:** SQL Injection hangi OWASP kategorisinde?
**C:** Injection (#3)

### Soru 4
**S:** Simetrik şifrelemede kaç anahtar var?
**C:** 1 (aynı anahtar şifreleme/deşifreleme için)

### Soru 5
**S:** Hash fonksiyonu tersine çevrilebilir mi?
**C:** Hayır, tek yönlüdür

### Soru 6
**S:** Phishing nedir?
**C:** Sahte e-posta/site ile kimlik bilgisi çalma

### Soru 7
**S:** IDS ve IPS arasındaki fark?
**C:** IDS: Tespit eder, IPS: Tespit eder + Engeller

### Soru 8
**S:** 2FA'da hangi faktörler kullanılır?
**C:** Bildiğin şey + Sahip olduğun şey (veya biyometrik)

### Soru 9
**S:** AES hangi şifreleme türü?
**C:** Simetrik şifreleme

### Soru 10
**S:** RSA hangi şifreleme türü?
**C:** Asimetrik şifreleme

### Soru 11
**S:** MD5 güvenli mi?
**C:** Hayır, collision zafiyeti var, kullanılmamalı

### Soru 12
**S:** MITM saldırısı ne yapar?
**C:** İletişime araya girerek veri çalar/değiştirir

### Soru 13
**S:** XSS ne tür bir saldırı?
**C:** Web sayfasına zararlı JavaScript enjekte etme

### Soru 14
**S:** Firewall ne işe yarar?
**C:** Ağ trafiğini kurallara göre filtreler

### Soru 15
**S:** Dijital imza neyi sağlar?
**C:** Bütünlük (Integrity) + Kimlik doğrulama + İnkar edilemezlik

### Soru 16
**S:** RBAC ne demek?
**C:** Role-Based Access Control (Rol bazlı erişim kontrolü)

### Soru 17
**S:** Veri bütünlüğünü doğrulamak için ne kullanılır?
**C:** Hash fonksiyonu veya checksum

### Soru 18
**S:** Sniffing hangi CIA unsurunu tehdit eder?
**C:** Confidentiality (Gizlilik)

### Soru 19
**S:** Tailgating ne tür bir saldırı?
**C:** Sosyal mühendislik (yetkili birinin arkasından fiziksel giriş)

### Soru 20
**S:** VPN ne sağlar?
**C:** Şifreli tünel ile güvenli uzak erişim

---

## Güvenlik Standartları ve Çerçeveler

```
┌─────────────────────────────────────────────────────────────────────┐
│  Standart      │  Açıklama                                          │
├────────────────┼────────────────────────────────────────────────────┤
│ ISO 27001      │ Bilgi Güvenliği Yönetim Sistemi (BGYS)             │
│ PCI-DSS        │ Kredi kartı verisi güvenliği                       │
│ GDPR           │ AB kişisel veri koruma                             │
│ KVKK           │ TR kişisel veri koruma                             │
│ HIPAA          │ ABD sağlık verisi güvenliği                        │
│ SOC 2          │ Hizmet organizasyonu kontrolleri                   │
│ NIST           │ ABD güvenlik çerçevesi                             │
└────────────────┴────────────────────────────────────────────────────┘
```

---

## Sınav İpuçları

1. **CIA sorusu gelirse:** Şifreleme=C, Hash=I, Yedekleme=A
2. **DDoS:** Her zaman Availability hedefler
3. **Simetrik/Asimetrik:** Anahtar sayısını sor (1 veya 2)
4. **OWASP:** Injection #3, Access Control #1
5. **Hash:** Tek yönlü, şifreleme DEĞİL
6. **IDS vs IPS:** IPS "Prevention" = Engelleme
