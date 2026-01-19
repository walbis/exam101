# Scripting & İşletim Sistemi Cheat Sheet

## Linux Bash Komutları

### Dosya ve Dizin İşlemleri

```
┌─────────────────────────────────────────────────────────────────────┐
│  Komut         │  Açıklama                    │  Örnek              │
├────────────────┼──────────────────────────────┼─────────────────────┤
│ ls             │ Dizin içeriğini listele      │ ls -la              │
│ cd             │ Dizin değiştir               │ cd /home/user       │
│ pwd            │ Mevcut dizini göster         │ pwd                 │
│ mkdir          │ Dizin oluştur                │ mkdir yeni_klasor   │
│ rmdir          │ Boş dizin sil                │ rmdir klasor        │
│ rm             │ Dosya/dizin sil              │ rm -rf klasor       │
│ cp             │ Kopyala                      │ cp kaynak hedef     │
│ mv             │ Taşı/Yeniden adlandır        │ mv eski.txt yeni.txt│
│ touch          │ Boş dosya oluştur            │ touch dosya.txt     │
│ cat            │ Dosya içeriğini göster       │ cat dosya.txt       │
│ head           │ İlk n satırı göster          │ head -10 dosya.txt  │
│ tail           │ Son n satırı göster          │ tail -20 dosya.txt  │
│ less           │ Sayfalı görüntüle            │ less dosya.txt      │
│ find           │ Dosya ara                    │ find / -name "*.txt"│
│ locate         │ Hızlı dosya ara              │ locate dosya.txt    │
└────────────────┴──────────────────────────────┴─────────────────────┘
```

### ls Parametreleri
```bash
ls          # Basit liste
ls -l       # Detaylı liste (long format)
ls -a       # Gizli dosyalar dahil (all)
ls -la      # Detaylı + gizli
ls -lh      # Boyut insan okunur (human readable)
ls -lt      # Zamana göre sırala
ls -lS      # Boyuta göre sırala
ls -R       # Alt dizinler dahil (recursive)
```

---

## Dosya İzinleri (KRİTİK!)

### İzin Yapısı
```
-rwxr-xr-x   1   user   group   4096   Jan 15 10:30   dosya.txt
│└┬┘└┬┘└┬┘   │    │       │      │        │             │
│ │  │  │    │    │       │      │        │             └── Dosya adı
│ │  │  │    │    │       │      │        └── Tarih
│ │  │  │    │    │       │      └── Boyut (byte)
│ │  │  │    │    │       └── Grup
│ │  │  │    │    └── Sahip (owner)
│ │  │  │    └── Hard link sayısı
│ │  │  └── Others (diğerleri) izinleri
│ │  └── Group (grup) izinleri
│ └── Owner (sahip) izinleri
└── Tür (- dosya, d dizin, l link)
```

### İzin Değerleri (Octal)

```
┌──────────────────────────────────────────────────┐
│  Harf  │  Değer  │  Anlamı                       │
├────────┼─────────┼───────────────────────────────┤
│   r    │    4    │  Read (okuma)                 │
│   w    │    2    │  Write (yazma)                │
│   x    │    1    │  Execute (çalıştırma)         │
│   -    │    0    │  İzin yok                     │
└────────┴─────────┴───────────────────────────────┘
```

### Yaygın İzin Kombinasyonları

```
┌────────────────────────────────────────────────────────────────────┐
│  Octal  │  Sembolik    │  Anlamı                                   │
├─────────┼──────────────┼───────────────────────────────────────────┤
│  777    │ rwxrwxrwx    │ Herkes her şeyi yapabilir (TEHLİKELİ!)    │
│  755    │ rwxr-xr-x    │ Sahip full, diğerleri oku+çalıştır        │
│  750    │ rwxr-x---    │ Sahip full, grup oku+çalıştır             │
│  700    │ rwx------    │ Sadece sahip                              │
│  666    │ rw-rw-rw-    │ Herkes okur+yazar                         │
│  644    │ rw-r--r--    │ Sahip okur+yazar, diğerleri sadece okur   │
│  640    │ rw-r-----    │ Sahip okur+yazar, grup okur               │
│  600    │ rw-------    │ Sadece sahip okur+yazar                   │
│  400    │ r--------    │ Sadece sahip okur                         │
└─────────┴──────────────┴───────────────────────────────────────────┘
```

### chmod Kullanımı

```bash
# Octal ile
chmod 755 dosya.sh      # rwxr-xr-x
chmod 644 dosya.txt     # rw-r--r--
chmod 600 gizli.txt     # rw-------

# Sembolik ile
chmod u+x dosya.sh      # Sahibe çalıştırma ekle
chmod g-w dosya.txt     # Gruptan yazma çıkar
chmod o=r dosya.txt     # Diğerlerini sadece okuma yap
chmod a+r dosya.txt     # Herkese okuma ekle

# u=user(owner), g=group, o=others, a=all
# +=ekle, -=çıkar, ==ayarla
```

### chown ve chgrp

```bash
chown user dosya.txt           # Sahibi değiştir
chown user:group dosya.txt     # Sahip ve grubu değiştir
chown -R user klasor/          # Recursive
chgrp group dosya.txt          # Grubu değiştir
```

---

## Süreç (Process) Yönetimi

```
┌────────────────────────────────────────────────────────────────────┐
│  Komut          │  Açıklama                                        │
├─────────────────┼──────────────────────────────────────────────────┤
│ ps              │ Süreçleri listele                                │
│ ps aux          │ Tüm süreçler (detaylı)                           │
│ ps -ef          │ Tüm süreçler (full format)                       │
│ top             │ Canlı süreç izleme                               │
│ htop            │ Gelişmiş canlı izleme                            │
│ kill PID        │ Süreç sonlandır (SIGTERM)                        │
│ kill -9 PID     │ Zorla sonlandır (SIGKILL)                        │
│ killall isim    │ İsme göre sonlandır                              │
│ bg              │ Arka plana gönder                                │
│ fg              │ Ön plana getir                                   │
│ nohup           │ Oturum kapansa da çalışsın                       │
│ &               │ Arka planda başlat                               │
│ jobs            │ Arka plan işleri listele                         │
└─────────────────┴──────────────────────────────────────────────────┘
```

### Sinyaller
```
SIGTERM (15): Normal sonlandırma isteği (varsayılan)
SIGKILL (9):  Zorla sonlandır (engellenemez)
SIGHUP (1):   Yapılandırmayı yeniden yükle
SIGINT (2):   Interrupt (Ctrl+C)
SIGSTOP (19): Durdur
SIGCONT (18): Devam et
```

---

## Metin İşleme

```
┌────────────────────────────────────────────────────────────────────┐
│  Komut          │  Açıklama                    │  Örnek            │
├─────────────────┼──────────────────────────────┼───────────────────┤
│ grep            │ Metin ara                    │ grep "hata" log   │
│ grep -i         │ Büyük/küçük harf duyarsız    │ grep -i "ERROR"   │
│ grep -r         │ Recursive ara                │ grep -r "TODO" ./ │
│ grep -v         │ Eşleşmeyenleri göster        │ grep -v "^#"      │
│ grep -c         │ Eşleşme sayısını göster      │ grep -c "error"   │
│ sed             │ Stream editor               │ sed 's/eski/yeni/'│
│ awk             │ Metin işleme dili            │ awk '{print $1}'  │
│ cut             │ Sütun kes                    │ cut -d: -f1       │
│ sort            │ Sırala                       │ sort dosya.txt    │
│ uniq            │ Tekrarları kaldır            │ uniq dosya.txt    │
│ wc              │ Satır/kelime/karakter say    │ wc -l dosya.txt   │
│ tr              │ Karakter dönüştür            │ tr 'a-z' 'A-Z'    │
└─────────────────┴──────────────────────────────┴───────────────────┘
```

### Pipe ve Yönlendirme

```bash
# Pipe (|): Bir komutun çıktısını diğerine gönder
cat dosya.txt | grep "hata" | wc -l

# Yönlendirme
command > dosya.txt      # Çıktıyı dosyaya yaz (üzerine yaz)
command >> dosya.txt     # Çıktıyı dosyaya ekle (append)
command < dosya.txt      # Dosyadan girdi al
command 2> hata.txt      # Hata çıktısını dosyaya yaz
command 2>&1             # Hata çıktısını normal çıktıya yönlendir
command &> dosya.txt     # Her iki çıktıyı dosyaya yaz
```

---

## Ağ Komutları

```
┌────────────────────────────────────────────────────────────────────┐
│  Komut          │  Açıklama                                        │
├─────────────────┼──────────────────────────────────────────────────┤
│ ping            │ Bağlantı kontrolü                                │
│ ifconfig        │ Ağ arayüzleri (eski)                             │
│ ip addr        │ Ağ arayüzleri (yeni)                              │
│ netstat         │ Ağ bağlantıları                                  │
│ ss              │ Socket istatistikleri                            │
│ traceroute      │ Paket yolunu göster                              │
│ nslookup        │ DNS sorgula                                      │
│ dig             │ DNS sorgula (detaylı)                            │
│ curl            │ URL'den veri çek                                 │
│ wget            │ Dosya indir                                      │
│ scp             │ Güvenli kopyalama                                │
│ ssh             │ Güvenli shell bağlantısı                         │
└─────────────────┴──────────────────────────────────────────────────┘
```

---

## Disk ve Bellek

```
┌────────────────────────────────────────────────────────────────────┐
│  Komut          │  Açıklama                                        │
├─────────────────┼──────────────────────────────────────────────────┤
│ df -h           │ Disk kullanımı (human readable)                  │
│ du -sh *        │ Dizin boyutları                                  │
│ free -h         │ Bellek kullanımı                                 │
│ mount           │ Bağlı dosya sistemleri                           │
│ fdisk -l        │ Disk bölümleri                                   │
│ lsblk           │ Blok cihazları listele                           │
└─────────────────┴──────────────────────────────────────────────────┘
```

---

## Kullanıcı ve Grup Yönetimi

```
┌────────────────────────────────────────────────────────────────────┐
│  Komut              │  Açıklama                                    │
├─────────────────────┼──────────────────────────────────────────────┤
│ whoami              │ Mevcut kullanıcı                             │
│ id                  │ Kullanıcı/grup bilgisi                       │
│ users               │ Oturum açmış kullanıcılar                    │
│ who                 │ Oturum bilgisi (detaylı)                     │
│ useradd             │ Kullanıcı ekle                               │
│ userdel             │ Kullanıcı sil                                │
│ usermod             │ Kullanıcı düzenle                            │
│ passwd              │ Parola değiştir                              │
│ groupadd            │ Grup ekle                                    │
│ groupdel            │ Grup sil                                     │
│ su                  │ Kullanıcı değiştir                           │
│ sudo                │ Root yetkisiyle çalıştır                     │
└─────────────────────┴──────────────────────────────────────────────┘
```

### Önemli Dosyalar
```
/etc/passwd     # Kullanıcı bilgileri
/etc/shadow     # Şifreli parolalar
/etc/group      # Grup bilgileri
/etc/sudoers    # Sudo yetkiler
```

---

## PowerShell Temelleri

### Temel Cmdlet'ler

```
┌────────────────────────────────────────────────────────────────────┐
│  Cmdlet               │  Alias      │  Açıklama                    │
├───────────────────────┼─────────────┼──────────────────────────────┤
│ Get-ChildItem         │ ls, dir     │ Dizin içeriği listele        │
│ Set-Location          │ cd          │ Dizin değiştir               │
│ Get-Location          │ pwd         │ Mevcut dizin                 │
│ New-Item              │ ni          │ Dosya/dizin oluştur          │
│ Remove-Item           │ rm, del     │ Dosya/dizin sil              │
│ Copy-Item             │ cp, copy    │ Kopyala                      │
│ Move-Item             │ mv, move    │ Taşı                         │
│ Get-Content           │ cat, type   │ Dosya içeriği                │
│ Set-Content           │ sc          │ Dosyaya yaz                  │
│ Add-Content           │ ac          │ Dosyaya ekle                 │
│ Get-Process           │ ps          │ Süreçler                     │
│ Stop-Process          │ kill        │ Süreç sonlandır              │
│ Get-Service           │ gsv         │ Servisler                    │
│ Start-Service         │ sasv        │ Servis başlat                │
│ Stop-Service          │ spsv        │ Servis durdur                │
│ Get-Help              │ help        │ Yardım                       │
│ Get-Command           │ gcm         │ Komut ara                    │
│ Get-Member            │ gm          │ Nesne özellikler             │
│ Select-Object         │ select      │ Özellik seç                  │
│ Where-Object          │ where, ?    │ Filtrele                     │
│ ForEach-Object        │ foreach, %  │ Her öğe için                 │
│ Sort-Object           │ sort        │ Sırala                       │
│ Measure-Object        │ measure     │ Ölç (say, topla vb.)         │
└───────────────────────┴─────────────┴──────────────────────────────┘
```

### PowerShell Örnekler

```powershell
# Dizin içeriği
Get-ChildItem -Path C:\Users -Recurse

# Dosya ara
Get-ChildItem -Path C:\ -Filter "*.log" -Recurse

# Süreçleri filtrele
Get-Process | Where-Object {$_.CPU -gt 10}

# Servisleri listele
Get-Service | Where-Object {$_.Status -eq 'Running'}

# Dosya içinde ara
Select-String -Path "*.txt" -Pattern "hata"

# Pipeline örneği
Get-Process | Sort-Object CPU -Descending | Select-Object -First 5
```

### PowerShell vs Bash Karşılaştırma

```
┌────────────────────────────────────────────────────────────────────┐
│  Bash           │  PowerShell            │  Açıklama               │
├─────────────────┼────────────────────────┼─────────────────────────┤
│ ls              │ Get-ChildItem          │ Dizin listele           │
│ cd              │ Set-Location           │ Dizin değiştir          │
│ pwd             │ Get-Location           │ Mevcut dizin            │
│ cat             │ Get-Content            │ Dosya oku               │
│ rm              │ Remove-Item            │ Sil                     │
│ cp              │ Copy-Item              │ Kopyala                 │
│ mv              │ Move-Item              │ Taşı                    │
│ grep            │ Select-String          │ Metin ara               │
│ ps              │ Get-Process            │ Süreçler                │
│ kill            │ Stop-Process           │ Süreç sonlandır         │
│ find            │ Get-ChildItem -Recurse │ Dosya ara               │
│ echo            │ Write-Output           │ Çıktı yaz               │
│ |               │ |                      │ Pipe (aynı)             │
│ >               │ >                      │ Yönlendirme (aynı)      │
└─────────────────┴────────────────────────┴─────────────────────────┘
```

---

## Shell Scripting Temelleri

### Bash Script Yapısı

```bash
#!/bin/bash
# Bu bir yorum satırı

# Değişken tanımlama
isim="Ali"
sayi=42

# Değişken kullanma
echo "Merhaba $isim"
echo "Sayı: $sayi"

# Girdi alma
read -p "Adınız: " kullanici
echo "Hoşgeldin $kullanici"

# Koşul
if [ $sayi -gt 10 ]; then
    echo "Sayı 10'dan büyük"
elif [ $sayi -eq 10 ]; then
    echo "Sayı 10'a eşit"
else
    echo "Sayı 10'dan küçük"
fi

# Döngü (for)
for i in 1 2 3 4 5; do
    echo "Sayı: $i"
done

# Döngü (while)
sayac=0
while [ $sayac -lt 5 ]; do
    echo "Sayaç: $sayac"
    ((sayac++))
done

# Fonksiyon
selamla() {
    echo "Merhaba $1"
}
selamla "Dünya"
```

### Bash Karşılaştırma Operatörleri

```
┌────────────────────────────────────────────────────────────────────┐
│  Sayısal              │  String                │  Dosya            │
├───────────────────────┼────────────────────────┼───────────────────┤
│ -eq  Eşit             │ =   Eşit               │ -e  Var mı        │
│ -ne  Eşit değil       │ !=  Eşit değil         │ -f  Dosya mı      │
│ -gt  Büyük            │ -z  Boş mu             │ -d  Dizin mi      │
│ -lt  Küçük            │ -n  Boş değil mi       │ -r  Okunabilir mi │
│ -ge  Büyük veya eşit  │                        │ -w  Yazılabilir mi│
│ -le  Küçük veya eşit  │                        │ -x  Çalıştırılabilir│
└───────────────────────┴────────────────────────┴───────────────────┘
```

---

## Flashcardlar

### Soru 1
**S:** Dosya izinlerini değiştiren Linux komutu?
**C:** chmod

### Soru 2
**S:** 644 izni ne anlama gelir?
**C:** rw-r--r-- (sahip okur+yazar, diğerleri sadece okur)

### Soru 3
**S:** 755 izni ne anlama gelir?
**C:** rwxr-xr-x (sahip full, diğerleri okur+çalıştırır)

### Soru 4
**S:** Süreçleri listeleyen Linux komutu?
**C:** ps (veya ps aux, top)

### Soru 5
**S:** Dosya içinde metin arayan komut?
**C:** grep

### Soru 6
**S:** Bir süreci zorla sonlandırmak için?
**C:** kill -9 PID

### Soru 7
**S:** PowerShell'de dosya listeleyen cmdlet?
**C:** Get-ChildItem (alias: ls, dir)

### Soru 8
**S:** PowerShell'de süreçleri gösteren cmdlet?
**C:** Get-Process (alias: ps)

### Soru 9
**S:** Linux'ta dizin oluşturma komutu?
**C:** mkdir

### Soru 10
**S:** "r" izin değeri nedir?
**C:** 4

### Soru 11
**S:** "w" izin değeri nedir?
**C:** 2

### Soru 12
**S:** "x" izin değeri nedir?
**C:** 1

### Soru 13
**S:** Bash'te pipe operatörü?
**C:** | (dikey çizgi)

### Soru 14
**S:** Çıktıyı dosyaya yazmak için?
**C:** > (üzerine yazar) veya >> (ekler)

### Soru 15
**S:** Dosya sahibini değiştiren komut?
**C:** chown

### Soru 16
**S:** Mevcut dizini gösteren komut?
**C:** pwd (Linux) / Get-Location (PowerShell)

### Soru 17
**S:** Hata çıktısını yönlendirmek için?
**C:** 2> (örn: command 2> hata.txt)

### Soru 18
**S:** Tüm çıktıları (stdout+stderr) yönlendirmek için?
**C:** &> veya 2>&1

### Soru 19
**S:** Bash script'in ilk satırı ne olmalı?
**C:** #!/bin/bash (shebang)

### Soru 20
**S:** PowerShell'de yardım almak için?
**C:** Get-Help cmdlet-ismi

---

## Sınav İpuçları

1. **İzin sorusu:** r=4, w=2, x=1 toplamı
2. **644 vs 755:** 644=dosya (çalıştırma yok), 755=script (çalıştırma var)
3. **grep:** Metin arama (g/re/p = global regular expression print)
4. **chmod vs chown:** chmod=izin, chown=sahiplik
5. **ps vs top:** ps anlık, top canlı izleme
6. **PowerShell:** Get-* okur, Set-* yazar, New-* oluşturur, Remove-* siler
