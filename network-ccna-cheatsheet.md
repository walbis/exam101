# Network (CCNA) Cheat Sheet

## OSI Model - 7 Katman

```
┌─────────────────────────────────────────────────────────────────┐
│ Katman │  İsim          │  Protokol/Cihaz      │  Veri Birimi  │
├────────┼────────────────┼──────────────────────┼───────────────┤
│   7    │ Application    │ HTTP, FTP, DNS, SMTP │    Data       │
│   6    │ Presentation   │ SSL/TLS, JPEG, ASCII │    Data       │
│   5    │ Session        │ NetBIOS, RPC         │    Data       │
│   4    │ Transport      │ TCP, UDP             │   Segment     │
│   3    │ Network        │ IP, ICMP, Router     │    Packet     │
│   2    │ Data Link      │ Ethernet, Switch     │    Frame      │
│   1    │ Physical       │ Kablo, Hub           │    Bits       │
└─────────────────────────────────────────────────────────────────┘
```

**Ezber Tekniği:** "**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing" (7→1)

---

## TCP/IP Model - 4 Katman

```
┌────────────────────┬─────────────────────┐
│    TCP/IP          │     OSI Karşılığı   │
├────────────────────┼─────────────────────┤
│ Application        │ 7, 6, 5             │
│ Transport          │ 4                   │
│ Internet           │ 3                   │
│ Network Access     │ 2, 1                │
└────────────────────┴─────────────────────┘
```

---

## Önemli Port Numaraları

```
┌────────────────────────────────────────────┐
│  Port  │  Protokol  │  Açıklama           │
├────────┼────────────┼─────────────────────┤
│   20   │  FTP-Data  │  Dosya transferi    │
│   21   │  FTP       │  FTP kontrol        │
│   22   │  SSH       │  Güvenli shell      │
│   23   │  Telnet    │  Güvensiz shell     │
│   25   │  SMTP      │  E-posta gönderme   │
│   53   │  DNS       │  Alan adı çözümleme │
│   67   │  DHCP Srv  │  DHCP Sunucu        │
│   68   │  DHCP Clt  │  DHCP İstemci       │
│   80   │  HTTP      │  Web (güvensiz)     │
│  110   │  POP3      │  E-posta alma       │
│  143   │  IMAP      │  E-posta (gelişmiş) │
│  443   │  HTTPS     │  Web (güvenli)      │
│  3389  │  RDP       │  Remote Desktop     │
└────────────────────────────────────────────┘
```

**Ezber:** "21-22-23" = FTP-SSH-Telnet (sırayla)

---

## Subnetting Hızlı Referans

### CIDR Notasyonu

```
┌─────────────────────────────────────────────────────────┐
│ CIDR  │  Subnet Mask      │  Host Sayısı  │ Kullanılabilir │
├───────┼───────────────────┼───────────────┼────────────────┤
│  /8   │ 255.0.0.0         │  16,777,216   │  16,777,214    │
│  /16  │ 255.255.0.0       │  65,536       │  65,534        │
│  /20  │ 255.255.240.0     │  4,096        │  4,094         │
│  /21  │ 255.255.248.0     │  2,048        │  2,046         │
│  /22  │ 255.255.252.0     │  1,024        │  1,022         │
│  /23  │ 255.255.254.0     │  512          │  510           │
│  /24  │ 255.255.255.0     │  256          │  254           │
│  /25  │ 255.255.255.128   │  128          │  126           │
│  /26  │ 255.255.255.192   │  64           │  62            │
│  /27  │ 255.255.255.224   │  32           │  30            │
│  /28  │ 255.255.255.240   │  16           │  14            │
│  /29  │ 255.255.255.248   │  8            │  6             │
│  /30  │ 255.255.255.252   │  4            │  2             │
│  /31  │ 255.255.255.254   │  2            │  2 (p2p link)  │
│  /32  │ 255.255.255.255   │  1            │  1 (host)      │
└─────────────────────────────────────────────────────────┘
```

### Formül
```
Toplam IP = 2^(32-CIDR)
Kullanılabilir = Toplam - 2 (network + broadcast)

Örnek: /26
Toplam = 2^(32-26) = 2^6 = 64 IP
Kullanılabilir = 64 - 2 = 62 IP
```

### Hızlı Hesaplama (Son Oktet)
```
/25 → 128 IP → 0, 128
/26 → 64 IP  → 0, 64, 128, 192
/27 → 32 IP  → 0, 32, 64, 96, 128, 160, 192, 224
/28 → 16 IP  → 0, 16, 32, 48... (16'şar artış)
```

---

## IP Adresi Sınıfları

```
┌─────────────────────────────────────────────────────────────┐
│ Sınıf │  Başlangıç   │    Bitiş        │  Varsayılan Mask  │
├───────┼──────────────┼─────────────────┼───────────────────┤
│   A   │  1.0.0.0     │  126.255.255.255│  255.0.0.0 (/8)   │
│   B   │  128.0.0.0   │  191.255.255.255│  255.255.0.0 (/16)│
│   C   │  192.0.0.0   │  223.255.255.255│  255.255.255.0(/24│
│   D   │  224.0.0.0   │  239.255.255.255│  Multicast        │
│   E   │  240.0.0.0   │  255.255.255.255│  Experimental     │
└─────────────────────────────────────────────────────────────┘
```

### Özel (Private) IP Aralıkları
```
10.0.0.0 - 10.255.255.255      (Class A)
172.16.0.0 - 172.31.255.255    (Class B)
192.168.0.0 - 192.168.255.255  (Class C)
```

---

## Switching Kavramları

### VLAN (Virtual LAN)
```
- Broadcast domain'i mantıksal olarak ayırır
- Varsayılan VLAN: 1
- Native VLAN: Tag'siz trafiğin gittiği VLAN
- Access Port: Tek VLAN'a bağlı (son kullanıcı)
- Trunk Port: Birden fazla VLAN taşır (switch-switch arası)
```

### Trunk Protokolü
```
802.1Q: Standart, VLAN tag'i ekler (4 byte)
ISL: Cisco'ya özel (artık kullanılmıyor)
```

### STP (Spanning Tree Protocol)
```
Amaç: Layer 2 loop'ları önlemek
Çalışma: Fazla linkleri bloklar, tek yol bırakır

Port Durumları:
- Blocking: Veri almaz/göndermez
- Listening: BPDU dinler
- Learning: MAC tablosu öğrenir
- Forwarding: Aktif veri iletimi
- Disabled: Port kapalı

Root Bridge: En düşük Bridge ID'ye sahip switch
```

### EtherChannel
```
Amaç: Birden fazla fiziksel linki tek mantıksal link yapar
Protokoller:
- PAgP: Cisco'ya özel
- LACP: Standart (802.3ad)
```

---

## Routing Kavramları

### Static Route
```
ip route [hedef-network] [subnet-mask] [next-hop]

Örnek:
ip route 192.168.2.0 255.255.255.0 10.0.0.2
ip route 0.0.0.0 0.0.0.0 10.0.0.1  (Default route)
```

### OSPF (Open Shortest Path First)
```
- Link-state routing protokolü
- Metric: Cost (bant genişliğine göre)
- Area 0: Backbone area (tüm area'lar bağlanmalı)
- DR/BDR: Designated Router seçimi
- Hello: 10 saniye, Dead: 40 saniye

Formül: Cost = 100 Mbps / Bandwidth
- 100 Mbps = Cost 1
- 10 Mbps = Cost 10
- 1 Gbps = Cost 0.1 (genelde 1 yapılır)
```

### Administrative Distance
```
┌─────────────────────────────────────┐
│  Kaynak              │  AD Değeri  │
├──────────────────────┼─────────────┤
│ Connected            │      0      │
│ Static               │      1      │
│ EIGRP Summary        │      5      │
│ EIGRP                │     90      │
│ OSPF                 │    110      │
│ RIP                  │    120      │
│ Unknown              │    255      │
└─────────────────────────────────────┘
```

---

## Flashcardlar

### Soru 1
**S:** OSI modelinde MAC adresleri hangi katmanda çalışır?
**C:** Data Link (Katman 2)

### Soru 2
**S:** /27 subnet'te kaç kullanılabilir IP var?
**C:** 30 (32-2=30)

### Soru 3
**S:** HTTP hangi portu kullanır?
**C:** 80 (HTTPS: 443)

### Soru 4
**S:** VLAN'lar arası iletişim için ne gerekli?
**C:** Router veya Layer 3 Switch

### Soru 5
**S:** STP'nin amacı nedir?
**C:** Layer 2 loop'ları önlemek

### Soru 6
**S:** OSPF'in metric'i nedir?
**C:** Cost (bant genişliğine dayalı)

### Soru 7
**S:** 192.168.x.x hangi IP sınıfı?
**C:** Class C (private)

### Soru 8
**S:** DNS hangi portu kullanır?
**C:** 53

### Soru 9
**S:** Trunk port ne işe yarar?
**C:** Birden fazla VLAN trafiğini taşır

### Soru 10
**S:** 10.0.0.0/8 kaç IP içerir?
**C:** 16,777,216 (2^24)

### Soru 11
**S:** TCP ve UDP arasındaki fark?
**C:** TCP: Bağlantı odaklı, güvenilir | UDP: Bağlantısız, hızlı

### Soru 12
**S:** ARP ne işe yarar?
**C:** IP adresini MAC adresine çevirir

### Soru 13
**S:** DHCP ne işe yarar?
**C:** Otomatik IP adresi dağıtır

### Soru 14
**S:** Default gateway nedir?
**C:** Farklı ağlara gitmek için kullanılan router adresi

### Soru 15
**S:** NAT ne işe yarar?
**C:** Private IP'leri public IP'ye çevirir (internet erişimi için)

---

## Cisco Komut Referansı

### Temel Komutlar
```
enable                    → Privileged mode
configure terminal        → Global config mode
show running-config       → Aktif konfigürasyon
show ip interface brief   → IP özeti
show vlan brief           → VLAN özeti
copy running-config startup-config → Kaydet
```

### VLAN Yapılandırma
```
vlan 10
 name SALES
!
interface fa0/1
 switchport mode access
 switchport access vlan 10
!
interface fa0/24
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```

### IP Yapılandırma
```
interface fa0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
```

---

## Sınav İpuçları

1. **Subnetting sorusu gelirse:** 2'nin kuvvetlerini bil (2,4,8,16,32,64,128,256)
2. **Port sorusu gelirse:** 21-22-23 = FTP-SSH-Telnet
3. **OSI katmanı sorulursa:** "Hangi cihaz?" → Switch=L2, Router=L3
4. **VLAN sorusu:** Access=Son kullanıcı, Trunk=Switch arası
5. **OSPF:** Her zaman Area 0 (backbone) gerekli
