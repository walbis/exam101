# Scripting/OS Soru Havuzu

## 4.1 Dosya/Dizin Komutlari (10 Soru)

### Soru 4.1.1
**Konu:** ls
**S:** Dizin icerigini listeleyen Linux komutu hangisidir?
**C:** ls

### Soru 4.1.2
**Konu:** cd
**S:** Dizin degistirmek icin hangi komut kullanilir?
**C:** cd (change directory)

### Soru 4.1.3
**Konu:** pwd
**S:** Mevcut dizini gosteren komut hangisidir?
**C:** pwd (print working directory)

### Soru 4.1.4
**Konu:** mkdir
**S:** Yeni dizin olusturmak icin hangi komut kullanilir?
**C:** mkdir

### Soru 4.1.5
**Konu:** rmdir
**S:** Bos dizin silmek icin hangi komut kullanilir?
**C:** rmdir

### Soru 4.1.6
**Konu:** rm
**S:** Dosya ve dizin silmek icin hangi komut kullanilir?
**C:** rm (rm -r ile recursive, rm -rf ile zorla)

### Soru 4.1.7
**Konu:** cp
**S:** Dosya kopyalamak icin hangi komut kullanilir?
**C:** cp (copy)

### Soru 4.1.8
**Konu:** mv
**S:** Dosya tasimak veya yeniden adlandirmak icin hangi komut kullanilir?
**C:** mv (move)

### Soru 4.1.9
**Konu:** touch
**S:** Bos dosya olusturmak icin hangi komut kullanilir?
**C:** touch

### Soru 4.1.10
**Konu:** rm -rf
**S:** rm -rf ne yapar?
**C:** Recursive (alt dizinler dahil) ve Force (onay sormadan) siler

---

## 4.2 Dosya Goruntuleme (4 Soru)

### Soru 4.2.1
**Konu:** cat
**S:** Dosya icerigini tamamen gosteren komut hangisidir?
**C:** cat

### Soru 4.2.2
**Konu:** head
**S:** Dosyanin ilk n satirini gosteren komut hangisidir?
**C:** head (head -10 dosya.txt)

### Soru 4.2.3
**Konu:** tail
**S:** Dosyanin son n satirini gosteren komut hangisidir?
**C:** tail (tail -20 dosya.txt)

### Soru 4.2.4
**Konu:** less
**S:** Dosyayi sayfali olarak gosteren komut hangisidir?
**C:** less

---

## 4.3 Dosya Arama (3 Soru)

### Soru 4.3.1
**Konu:** find
**S:** Dosya arama komutu hangisidir?
**C:** find (find / -name "*.txt")

### Soru 4.3.2
**Konu:** locate
**S:** Hizli dosya arama komutu hangisidir?
**C:** locate (veritabani kullanir)

### Soru 4.3.3
**Konu:** find Ornek
**S:** /home dizininde .log uzantili dosyalari bulmak icin?
**C:** find /home -name "*.log"

---

## 4.4 ls Parametreleri (4 Soru)

### Soru 4.4.1
**Konu:** ls -l
**S:** ls -l ne yapar?
**C:** Detayli liste (long format) - izinler, sahip, boyut, tarih gosterir

### Soru 4.4.2
**Konu:** ls -a
**S:** ls -a ne yapar?
**C:** Gizli dosyalar dahil (all) - . ile baslayan dosyalari da gosterir

### Soru 4.4.3
**Konu:** ls -la
**S:** ls -la ne yapar?
**C:** Detayli liste + gizli dosyalar

### Soru 4.4.4
**Konu:** ls -lh
**S:** ls -lh ne yapar?
**C:** Boyutlari insan okunur formatta gosterir (human readable - KB, MB, GB)

---

## 4.5 Dosya Izin Yapisi (5 Soru)

### Soru 4.5.1
**Konu:** Izin Sirasi
**S:** -rwxr-xr-x izin yapisinda sirasi nedir?
**C:** Owner (sahip) - Group (grup) - Others (diger)

### Soru 4.5.2
**Konu:** Owner
**S:** Dosya izinlerinde "owner" ne demektir?
**C:** Dosyanin sahibi (olusturan kullanici)

### Soru 4.5.3
**Konu:** Group
**S:** Dosya izinlerinde "group" ne demektir?
**C:** Dosyanin ait oldugu grup

### Soru 4.5.4
**Konu:** Others
**S:** Dosya izinlerinde "others" ne demektir?
**C:** Diger tum kullanicilar (sahip ve grup disindakiler)

### Soru 4.5.5
**Konu:** Dosya Turu
**S:** ls -l ciktisinda ilk karakter ne gosterir?
**C:** Dosya turu (- dosya, d dizin, l link)

---

## 4.6 Izin Degerleri (5 Soru)

### Soru 4.6.1
**Konu:** r Degeri
**S:** "r" (read) izninin sayisal degeri kactir?
**C:** 4

### Soru 4.6.2
**Konu:** w Degeri
**S:** "w" (write) izninin sayisal degeri kactir?
**C:** 2

### Soru 4.6.3
**Konu:** x Degeri
**S:** "x" (execute) izninin sayisal degeri kactir?
**C:** 1

### Soru 4.6.4
**Konu:** rwx Degeri
**S:** "rwx" izninin toplam sayisal degeri kactir?
**C:** 7 (4+2+1)

### Soru 4.6.5
**Konu:** rw- Degeri
**S:** "rw-" izninin toplam sayisal degeri kactir?
**C:** 6 (4+2+0)

---

## 4.7 Yaygin Izin Kombinasyonlari (8 Soru)

### Soru 4.7.1
**Konu:** 777
**S:** 777 izni ne anlama gelir?
**C:** rwxrwxrwx - Herkes her seyi yapabilir (TEHLIKELI!)

### Soru 4.7.2
**Konu:** 755
**S:** 755 izni ne anlama gelir?
**C:** rwxr-xr-x - Sahip full, digerler okur+calistirir (script'ler icin)

### Soru 4.7.3
**Konu:** 644
**S:** 644 izni ne anlama gelir?
**C:** rw-r--r-- - Sahip okur+yazar, digerler sadece okur (dosyalar icin)

### Soru 4.7.4
**Konu:** 600
**S:** 600 izni ne anlama gelir?
**C:** rw------- - Sadece sahip okur+yazar (gizli dosyalar icin)

### Soru 4.7.5
**Konu:** 700
**S:** 700 izni ne anlama gelir?
**C:** rwx------ - Sadece sahip full erisim

### Soru 4.7.6
**Konu:** 750
**S:** 750 izni ne anlama gelir?
**C:** rwxr-x--- - Sahip full, grup okur+calistirir

### Soru 4.7.7
**Konu:** 666
**S:** 666 izni ne anlama gelir?
**C:** rw-rw-rw- - Herkes okur+yazar (calistirma yok)

### Soru 4.7.8
**Konu:** 400
**S:** 400 izni ne anlama gelir?
**C:** r-------- - Sadece sahip okur

---

## 4.8 chmod (5 Soru)

### Soru 4.8.1
**Konu:** chmod Tanim
**S:** chmod ne ise yarar?
**C:** Dosya izinlerini degistirir (change mode)

### Soru 4.8.2
**Konu:** chmod Octal
**S:** chmod 755 dosya.sh ne yapar?
**C:** dosya.sh'yi rwxr-xr-x izinleriyle ayarlar

### Soru 4.8.3
**Konu:** chmod Sembolik
**S:** chmod u+x dosya.sh ne yapar?
**C:** Sahibe (user) calistirma (execute) izni ekler

### Soru 4.8.4
**Konu:** chmod g-w
**S:** chmod g-w dosya.txt ne yapar?
**C:** Gruptan yazma iznini kaldirir

### Soru 4.8.5
**Konu:** chmod a+r
**S:** chmod a+r dosya.txt ne yapar?
**C:** Herkese (all) okuma izni ekler

---

## 4.9 chown ve chgrp (3 Soru)

### Soru 4.9.1
**Konu:** chown
**S:** chown ne ise yarar?
**C:** Dosya sahibini degistirir (change owner)

### Soru 4.9.2
**Konu:** chown Ornek
**S:** chown user:group dosya.txt ne yapar?
**C:** Dosyanin hem sahibini hem grubunu degistirir

### Soru 4.9.3
**Konu:** chgrp
**S:** chgrp ne ise yarar?
**C:** Dosya grubunu degistirir (change group)

---

## 4.10 Surec Yonetimi (5 Soru)

### Soru 4.10.1
**Konu:** ps
**S:** ps komutu ne yapar?
**C:** Surecleri listeler

### Soru 4.10.2
**Konu:** ps aux
**S:** ps aux ne yapar?
**C:** Tum surecleri detayli listeler

### Soru 4.10.3
**Konu:** top
**S:** top komutu ne yapar?
**C:** Surecleri canli olarak izler

### Soru 4.10.4
**Konu:** htop
**S:** htop nedir?
**C:** Gelismis (interaktif) canli surec izleme

### Soru 4.10.5
**Konu:** ps vs top
**S:** ps ve top arasindaki fark nedir?
**C:** ps anlik goruntuler, top canli izler

---

## 4.11 Surec Sonlandirma (4 Soru)

### Soru 4.11.1
**Konu:** kill
**S:** kill komutu ne yapar?
**C:** Surece sinyal gonderir (varsayilan: SIGTERM ile sonlandirma ister)

### Soru 4.11.2
**Konu:** kill -9
**S:** kill -9 PID ne yapar?
**C:** Sureci zorla sonlandirir (SIGKILL)

### Soru 4.11.3
**Konu:** killall
**S:** killall ne yapar?
**C:** Isime gore surecleri sonlandirir

### Soru 4.11.4
**Konu:** kill vs kill -9
**S:** kill ve kill -9 arasindaki fark nedir?
**C:** kill normal sonlandirma ister (surec temizlik yapabilir), kill -9 zorla sonlandirir

---

## 4.12 Arka Plan Islemleri (4 Soru)

### Soru 4.12.1
**Konu:** &
**S:** Komut sonuna & koymak ne yapar?
**C:** Komutu arka planda baslatir

### Soru 4.12.2
**Konu:** bg
**S:** bg komutu ne yapar?
**C:** Durmus sureci arka plana gonderir

### Soru 4.12.3
**Konu:** fg
**S:** fg komutu ne yapar?
**C:** Arka plandaki sureci on plana getirir

### Soru 4.12.4
**Konu:** nohup
**S:** nohup ne yapar?
**C:** Oturum kapansa da sureecin calismaya devam etmesini saglar

---

## 4.13 Sinyaller (4 Soru)

### Soru 4.13.1
**Konu:** SIGTERM
**S:** SIGTERM (15) ne yapar?
**C:** Normal sonlandirma istegi (varsayilan, surec temizlik yapabilir)

### Soru 4.13.2
**Konu:** SIGKILL
**S:** SIGKILL (9) ne yapar?
**C:** Zorla sonlandirir (engellenemez)

### Soru 4.13.3
**Konu:** SIGHUP
**S:** SIGHUP (1) ne yapar?
**C:** Yapilandirmayi yeniden yukle

### Soru 4.13.4
**Konu:** SIGINT
**S:** SIGINT (2) ne yapar?
**C:** Interrupt - Ctrl+C ile gonderilen sinyal

---

## 4.14 grep (5 Soru)

### Soru 4.14.1
**Konu:** grep Tanim
**S:** grep ne ise yarar?
**C:** Dosyalarda metin arar (global regular expression print)

### Soru 4.14.2
**Konu:** grep -i
**S:** grep -i ne yapar?
**C:** Buyuk/kucuk harf duyarsiz arama

### Soru 4.14.3
**Konu:** grep -r
**S:** grep -r ne yapar?
**C:** Alt dizinlerde de arar (recursive)

### Soru 4.14.4
**Konu:** grep -v
**S:** grep -v ne yapar?
**C:** Eslesmeyenleri gosterir (invert match)

### Soru 4.14.5
**Konu:** grep -c
**S:** grep -c ne yapar?
**C:** Eslesme sayisini gosterir (count)

---

## 4.15 Diger Metin Araclari (5 Soru)

### Soru 4.15.1
**Konu:** sed
**S:** sed ne ise yarar?
**C:** Stream editor - metin degistirme (sed 's/eski/yeni/')

### Soru 4.15.2
**Konu:** awk
**S:** awk ne ise yarar?
**C:** Metin isleme dili (sutun bazli islemler - awk '{print $1}')

### Soru 4.15.3
**Konu:** cut
**S:** cut ne ise yarar?
**C:** Sutun keser (cut -d: -f1 - : ile ayrilmis 1. alan)

### Soru 4.15.4
**Konu:** sort ve uniq
**S:** sort ve uniq ne ise yarar?
**C:** sort: Siralar, uniq: Tekrarlari kaldirir

### Soru 4.15.5
**Konu:** wc
**S:** wc ne ise yarar?
**C:** Satir/kelime/karakter sayar (wc -l satir sayar)

---

## 4.16 Pipe ve Yonlendirme (6 Soru)

### Soru 4.16.1
**Konu:** Pipe
**S:** | (pipe) operatoru ne yapar?
**C:** Bir komutun ciktisini diger komutun girdisi yapar

### Soru 4.16.2
**Konu:** >
**S:** > operatoru ne yapar?
**C:** Ciktiyi dosyaya yazar (uzerine yazar)

### Soru 4.16.3
**Konu:** >>
**S:** >> operatoru ne yapar?
**C:** Ciktiyi dosyaya ekler (append)

### Soru 4.16.4
**Konu:** <
**S:** < operatoru ne yapar?
**C:** Dosyadan girdi alir

### Soru 4.16.5
**Konu:** 2>
**S:** 2> operatoru ne yapar?
**C:** Hata ciktisini (stderr) dosyaya yazar

### Soru 4.16.6
**Konu:** 2>&1
**S:** 2>&1 ne yapar?
**C:** Hata ciktisini normal ciktiya yonlendirir

---

## 4.17 Ag Komutlari (6 Soru)

### Soru 4.17.1
**Konu:** ping
**S:** ping ne ise yarar?
**C:** Baglanti kontrolu yapar (ICMP paketi gonderir)

### Soru 4.17.2
**Konu:** ifconfig/ip
**S:** ifconfig veya ip addr ne gosterir?
**C:** Ag arayuzlerini ve IP adreslerini gosterir

### Soru 4.17.3
**Konu:** netstat/ss
**S:** netstat veya ss ne gosterir?
**C:** Ag baglantilari ve socket istatistiklerini gosterir

### Soru 4.17.4
**Konu:** traceroute
**S:** traceroute ne yapar?
**C:** Paketin hedefe giderken izledigi yolu gosterir

### Soru 4.17.5
**Konu:** nslookup/dig
**S:** nslookup veya dig ne yapar?
**C:** DNS sorgulama yapar

### Soru 4.17.6
**Konu:** ssh
**S:** ssh ne yapar?
**C:** Guvenli shell baglantisi saglar (Secure Shell)

---

## 4.18 Indirme/Transfer (4 Soru)

### Soru 4.18.1
**Konu:** curl
**S:** curl ne ise yarar?
**C:** URL'den veri ceker (API istekleri, dosya indirme)

### Soru 4.18.2
**Konu:** wget
**S:** wget ne ise yarar?
**C:** Dosya indirir

### Soru 4.18.3
**Konu:** scp
**S:** scp ne ise yarar?
**C:** Guvenli kopyalama (SSH uzerinden dosya transfer)

### Soru 4.18.4
**Konu:** curl vs wget
**S:** curl ve wget arasindaki fark nedir?
**C:** curl daha cok API/veri cekmek icin, wget daha cok dosya indirmek icin

---

## 4.19 Disk/Bellek (5 Soru)

### Soru 4.19.1
**Konu:** df
**S:** df ne gosterir?
**C:** Disk kullanimi (df -h human readable)

### Soru 4.19.2
**Konu:** du
**S:** du ne gosterir?
**C:** Dizin boyutlari (du -sh * ozet boyutlar)

### Soru 4.19.3
**Konu:** free
**S:** free ne gosterir?
**C:** Bellek (RAM) kullanimi (free -h human readable)

### Soru 4.19.4
**Konu:** mount
**S:** mount ne yapar?
**C:** Dosya sistemlerini baglar veya bagli olanlari gosterir

### Soru 4.19.5
**Konu:** lsblk
**S:** lsblk ne gosterir?
**C:** Blok cihazlari (diskler, bolumler) listeler

---

## 4.20 Kullanici Komutlari (6 Soru)

### Soru 4.20.1
**Konu:** whoami
**S:** whoami ne gosterir?
**C:** Mevcut kullanici adini gosterir

### Soru 4.20.2
**Konu:** id
**S:** id ne gosterir?
**C:** Kullanici ve grup bilgilerini gosterir (UID, GID)

### Soru 4.20.3
**Konu:** useradd
**S:** useradd ne yapar?
**C:** Yeni kullanici ekler

### Soru 4.20.4
**Konu:** passwd
**S:** passwd ne yapar?
**C:** Kullanici parolasini degistirir

### Soru 4.20.5
**Konu:** su
**S:** su ne yapar?
**C:** Kullanici degistirir (switch user)

### Soru 4.20.6
**Konu:** sudo
**S:** sudo ne yapar?
**C:** Komutu root (yonetici) yetkisiyle calistirir

---

## 4.21 Onemli Dosyalar (4 Soru)

### Soru 4.21.1
**Konu:** /etc/passwd
**S:** /etc/passwd ne icerir?
**C:** Kullanici bilgileri (kullanici adi, UID, home dizini, shell)

### Soru 4.21.2
**Konu:** /etc/shadow
**S:** /etc/shadow ne icerir?
**C:** Sifreli parolalar (sadece root erisebilir)

### Soru 4.21.3
**Konu:** /etc/group
**S:** /etc/group ne icerir?
**C:** Grup bilgileri

### Soru 4.21.4
**Konu:** /etc/sudoers
**S:** /etc/sudoers ne icerir?
**C:** Sudo yetkileri (kim sudo kullanabilir)

---

## 4.22 PowerShell Cmdlet'ler (8 Soru)

### Soru 4.22.1
**Konu:** Get-ChildItem
**S:** Get-ChildItem ne yapar?
**C:** Dizin icerigini listeler (alias: ls, dir)

### Soru 4.22.2
**Konu:** Set-Location
**S:** Set-Location ne yapar?
**C:** Dizin degistirir (alias: cd)

### Soru 4.22.3
**Konu:** Get-Content
**S:** Get-Content ne yapar?
**C:** Dosya icerigini okur (alias: cat, type)

### Soru 4.22.4
**Konu:** Get-Process
**S:** Get-Process ne yapar?
**C:** Surecleri listeler (alias: ps)

### Soru 4.22.5
**Konu:** Stop-Process
**S:** Stop-Process ne yapar?
**C:** Surec sonlandirir (alias: kill)

### Soru 4.22.6
**Konu:** Get-Service
**S:** Get-Service ne yapar?
**C:** Servisleri listeler

### Soru 4.22.7
**Konu:** Select-String
**S:** Select-String ne yapar?
**C:** Dosyada metin arar (grep benzeri)

### Soru 4.22.8
**Konu:** Where-Object
**S:** Where-Object ne yapar?
**C:** Nesneleri filtreler (alias: where, ?)

---

## 4.23 PowerShell vs Bash (4 Soru)

### Soru 4.23.1
**Konu:** ls Karsiligi
**S:** Bash'te ls'in PowerShell karsiligi nedir?
**C:** Get-ChildItem

### Soru 4.23.2
**Konu:** grep Karsiligi
**S:** Bash'te grep'in PowerShell karsiligi nedir?
**C:** Select-String

### Soru 4.23.3
**Konu:** cat Karsiligi
**S:** Bash'te cat'in PowerShell karsiligi nedir?
**C:** Get-Content

### Soru 4.23.4
**Konu:** Pipe
**S:** Bash ve PowerShell'de pipe operatoru ayni mi?
**C:** Evet, ikisinde de | kullanilir

---

## 4.24 Bash Scripting (5 Soru)

### Soru 4.24.1
**Konu:** Shebang
**S:** Bash script'in ilk satiri ne olmalidir?
**C:** #!/bin/bash (shebang)

### Soru 4.24.2
**Konu:** Degisken
**S:** Bash'te degisken nasil tanimlanir?
**C:** isim="deger" (esittir etrafinda bosluk yok)

### Soru 4.24.3
**Konu:** Degisken Kullanim
**S:** Bash'te degisken nasil kullanilir?
**C:** $isim veya ${isim}

### Soru 4.24.4
**Konu:** if
**S:** Bash'te if-then-fi yapisi nasil yazilir?
**C:** if [ kosul ]; then komut; fi

### Soru 4.24.5
**Konu:** for
**S:** Bash'te for dongusu nasil yazilir?
**C:** for i in liste; do komut; done

---

## 4.25 Bash Karsilastirma Operatorleri (5 Soru)

### Soru 4.25.1
**Konu:** -eq
**S:** Bash'te -eq ne anlama gelir?
**C:** Sayisal esitlik (equal)

### Soru 4.25.2
**Konu:** -ne
**S:** Bash'te -ne ne anlama gelir?
**C:** Sayisal esit degil (not equal)

### Soru 4.25.3
**Konu:** -gt ve -lt
**S:** Bash'te -gt ve -lt ne anlama gelir?
**C:** -gt: buyuk (greater than), -lt: kucuk (less than)

### Soru 4.25.4
**Konu:** -z
**S:** Bash'te -z ne kontrol eder?
**C:** String bos mu (zero length)

### Soru 4.25.5
**Konu:** -f ve -d
**S:** Bash'te -f ve -d ne kontrol eder?
**C:** -f: dosya mi, -d: dizin mi

---

## OZET

| Konu | Soru Sayisi |
|------|-------------|
| 4.1 Dosya/Dizin Komutlari | 10 |
| 4.2 Dosya Goruntuleme | 4 |
| 4.3 Dosya Arama | 3 |
| 4.4 ls Parametreleri | 4 |
| 4.5 Dosya Izin Yapisi | 5 |
| 4.6 Izin Degerleri | 5 |
| 4.7 Izin Kombinasyonlari | 8 |
| 4.8 chmod | 5 |
| 4.9 chown/chgrp | 3 |
| 4.10 Surec Yonetimi | 5 |
| 4.11 Surec Sonlandirma | 4 |
| 4.12 Arka Plan | 4 |
| 4.13 Sinyaller | 4 |
| 4.14 grep | 5 |
| 4.15 Metin Araclari | 5 |
| 4.16 Pipe/Yonlendirme | 6 |
| 4.17 Ag Komutlari | 6 |
| 4.18 Indirme/Transfer | 4 |
| 4.19 Disk/Bellek | 5 |
| 4.20 Kullanici Komutlari | 6 |
| 4.21 Onemli Dosyalar | 4 |
| 4.22 PowerShell Cmdlet | 8 |
| 4.23 PowerShell vs Bash | 4 |
| 4.24 Bash Scripting | 5 |
| 4.25 Bash Operatorler | 5 |
| **TOPLAM** | **117** |
