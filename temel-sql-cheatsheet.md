# Temel SQL Cheat Sheet

## SQL Sorgu Yürütme Sırası

```
┌─────────────────────────────────────────────────────────────────────┐
│   Yazım Sırası          │   Yürütme Sırası                         │
├─────────────────────────┼───────────────────────────────────────────┤
│   1. SELECT             │   1. FROM                                 │
│   2. FROM               │   2. JOIN                                 │
│   3. WHERE              │   3. WHERE                                │
│   4. GROUP BY           │   4. GROUP BY                             │
│   5. HAVING             │   5. HAVING                               │
│   6. ORDER BY           │   6. SELECT                               │
│                         │   7. DISTINCT                             │
│                         │   8. ORDER BY                             │
│                         │   9. LIMIT/TOP                            │
└─────────────────────────┴───────────────────────────────────────────┘
```

**Ezber:** FROM → WHERE → GROUP → HAVING → SELECT → ORDER

---

## SELECT Temelleri

### Temel Sözdizimi
```sql
SELECT kolon1, kolon2, ...
FROM tablo
WHERE kosul
ORDER BY kolon ASC|DESC;
```

### Örnekler
```sql
-- Tüm kolonları getir
SELECT * FROM personel;

-- Belirli kolonları getir
SELECT ad, soyad, maas FROM personel;

-- Tekrarsız değerler
SELECT DISTINCT departman FROM personel;

-- Alias (takma isim)
SELECT ad AS isim, maas AS aylik_ucret FROM personel;

-- Hesaplama
SELECT ad, maas, maas * 12 AS yillik_maas FROM personel;

-- Birleştirme (Concatenation)
SELECT ad || ' ' || soyad AS tam_isim FROM personel;  -- Oracle/PostgreSQL
SELECT CONCAT(ad, ' ', soyad) AS tam_isim FROM personel;  -- MySQL/SQL Server
```

---

## WHERE Koşulları

### Karşılaştırma Operatörleri
```sql
=       Eşit
<>      Eşit değil (bazı sistemlerde !=)
>       Büyük
<       Küçük
>=      Büyük veya eşit
<=      Küçük veya eşit
```

### Mantıksal Operatörler
```sql
AND     Her iki koşul da doğru olmalı
OR      En az bir koşul doğru olmalı
NOT     Koşulun tersini al
```

### Özel Operatörler

```sql
-- BETWEEN: Aralık kontrolü
SELECT * FROM personel WHERE maas BETWEEN 5000 AND 10000;

-- IN: Liste kontrolü
SELECT * FROM personel WHERE departman IN ('IT', 'HR', 'Finans');

-- LIKE: Desen eşleştirme
SELECT * FROM personel WHERE ad LIKE 'A%';      -- A ile başlayan
SELECT * FROM personel WHERE ad LIKE '%an';     -- an ile biten
SELECT * FROM personel WHERE ad LIKE '%li%';    -- içinde li geçen
SELECT * FROM personel WHERE ad LIKE '_li';     -- 3 harf, son 2'si li

-- Joker Karakterler:
-- %  : Sıfır veya daha fazla karakter
-- _  : Tam olarak bir karakter
```

---

## NULL Kontrolü (KRİTİK!)

```
┌─────────────────────────────────────────────────────────────────────┐
│                    ÖNEMLİ: NULL KURALLARI                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ❌ YANLIŞ:  WHERE kolon = NULL                                    │
│   ❌ YANLIŞ:  WHERE kolon <> NULL                                   │
│   ❌ YANLIŞ:  WHERE kolon == NULL                                   │
│                                                                     │
│   ✅ DOĞRU:   WHERE kolon IS NULL                                   │
│   ✅ DOĞRU:   WHERE kolon IS NOT NULL                               │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Neden?
```
NULL = "Değer yok/Bilinmiyor" anlamındadır.
NULL bir değer değildir, bu yüzden = ile karşılaştırılamaz.
NULL ile yapılan tüm karşılaştırmalar UNKNOWN döner.

NULL = NULL    →  UNKNOWN (FALSE gibi davranır)
NULL <> NULL   →  UNKNOWN
5 = NULL       →  UNKNOWN
5 <> NULL      →  UNKNOWN
```

### Örnekler
```sql
-- Telefonu olmayanları bul
SELECT * FROM musteriler WHERE telefon IS NULL;

-- Telefonu olanları bul
SELECT * FROM musteriler WHERE telefon IS NOT NULL;

-- NULL değerini başka değerle değiştir
SELECT ad, COALESCE(telefon, 'Telefon yok') FROM musteriler;  -- Standart
SELECT ad, ISNULL(telefon, 'Telefon yok') FROM musteriler;    -- SQL Server
SELECT ad, NVL(telefon, 'Telefon yok') FROM musteriler;       -- Oracle
SELECT ad, IFNULL(telefon, 'Telefon yok') FROM musteriler;    -- MySQL
```

---

## JOIN Türleri (KRİTİK!)

### Görsel Açıklama

```
       A           B                 SONUÇ
    ┌─────┐     ┌─────┐
    │  1  │     │  1  │     INNER JOIN: Sadece kesişim (1)
    │  2  │     │  3  │     LEFT JOIN:  A'nın tamamı + kesişim (1,2)
    │     │     │     │     RIGHT JOIN: B'nin tamamı + kesişim (1,3)
    └─────┘     └─────┘     FULL JOIN:  Her ikisinin tamamı (1,2,3)
```

### Detaylı Tablo

```
┌─────────────────────────────────────────────────────────────────────┐
│  JOIN Türü      │  Ne Döner?                                       │
├─────────────────┼───────────────────────────────────────────────────┤
│ INNER JOIN      │ SADECE her iki tabloda eşleşen kayıtlar          │
│ LEFT JOIN       │ Sol tablonun TAMAMI + sağdan eşleşenler          │
│ RIGHT JOIN      │ Sağ tablonun TAMAMI + soldan eşleşenler          │
│ FULL OUTER JOIN │ Her iki tablonun TAMAMI (eşleşmeyenler NULL)     │
│ CROSS JOIN      │ Kartezyen çarpım (her satır x her satır)         │
│ SELF JOIN       │ Tablonun kendisiyle birleşimi                    │
└─────────────────┴───────────────────────────────────────────────────┘
```

### Pratik Örnek

**Personel Tablosu:**
| id | isim | dept_id |
|----|------|---------|
| 1 | Ali | 10 |
| 2 | Ayşe | 20 |
| 3 | Can | NULL |

**Departman Tablosu:**
| id | dept_ad |
|----|---------|
| 10 | IT |
| 20 | HR |
| 30 | Finans |

```sql
-- INNER JOIN: Sadece departmanı olan personel (Ali, Ayşe)
SELECT p.isim, d.dept_ad
FROM personel p
INNER JOIN departman d ON p.dept_id = d.id;

-- Sonuç:
-- Ali  | IT
-- Ayşe | HR
-- (Can yok çünkü dept_id NULL)
-- (Finans yok çünkü eşleşen personel yok)


-- LEFT JOIN: Tüm personel, departmanı varsa göster
SELECT p.isim, d.dept_ad
FROM personel p
LEFT JOIN departman d ON p.dept_id = d.id;

-- Sonuç:
-- Ali  | IT
-- Ayşe | HR
-- Can  | NULL   (personel var ama departmanı yok)


-- RIGHT JOIN: Tüm departmanlar, personeli varsa göster
SELECT p.isim, d.dept_ad
FROM personel p
RIGHT JOIN departman d ON p.dept_id = d.id;

-- Sonuç:
-- Ali  | IT
-- Ayşe | HR
-- NULL | Finans  (departman var ama personeli yok)


-- FULL OUTER JOIN: Her ikisinin tamamı
SELECT p.isim, d.dept_ad
FROM personel p
FULL OUTER JOIN departman d ON p.dept_id = d.id;

-- Sonuç:
-- Ali  | IT
-- Ayşe | HR
-- Can  | NULL
-- NULL | Finans
```

### JOIN Seçim Rehberi

```
Soru: "Sadece eşleşenleri getir"           → INNER JOIN
Soru: "Tüm [sol tablo] + eşleşenler"       → LEFT JOIN
Soru: "Tüm [sağ tablo] + eşleşenler"       → RIGHT JOIN
Soru: "Her iki tablonun tamamı"            → FULL OUTER JOIN
```

---

## Aggregate (Toplama) Fonksiyonları

```sql
COUNT(*)        -- Toplam satır sayısı
COUNT(kolon)    -- NULL olmayan değer sayısı
SUM(kolon)      -- Toplam
AVG(kolon)      -- Ortalama
MIN(kolon)      -- En küçük
MAX(kolon)      -- En büyük
```

### Örnekler
```sql
-- Toplam personel sayısı
SELECT COUNT(*) FROM personel;

-- Departman bazında sayı
SELECT departman, COUNT(*) AS personel_sayisi
FROM personel
GROUP BY departman;

-- Ortalama maaş
SELECT AVG(maas) AS ortalama_maas FROM personel;

-- En yüksek ve en düşük maaş
SELECT MIN(maas) AS en_dusuk, MAX(maas) AS en_yuksek FROM personel;
```

---

## GROUP BY ve HAVING

### GROUP BY: Grupla
```sql
SELECT departman, COUNT(*), AVG(maas)
FROM personel
GROUP BY departman;
```

### HAVING: Grup sonrası filtrele
```sql
-- 5'ten fazla personeli olan departmanlar
SELECT departman, COUNT(*) AS sayi
FROM personel
GROUP BY departman
HAVING COUNT(*) > 5;
```

### WHERE vs HAVING

```
┌─────────────────────────────────────────────────────────────────────┐
│  WHERE                        │  HAVING                            │
├───────────────────────────────┼────────────────────────────────────┤
│ GROUP BY'dan ÖNCE çalışır     │ GROUP BY'dan SONRA çalışır         │
│ Satırları filtreler           │ Grupları filtreler                 │
│ Aggregate fonksiyon KULLANAMAZ│ Aggregate fonksiyon KULLANABİLİR   │
└───────────────────────────────┴────────────────────────────────────┘
```

```sql
-- WHERE: Maaşı 5000'den fazla olanları grupla
SELECT departman, AVG(maas)
FROM personel
WHERE maas > 5000
GROUP BY departman;

-- HAVING: Ortalama maaşı 5000'den fazla olan grupları getir
SELECT departman, AVG(maas) AS ort
FROM personel
GROUP BY departman
HAVING AVG(maas) > 5000;

-- İkisi birlikte
SELECT departman, AVG(maas) AS ort
FROM personel
WHERE yas > 25            -- Önce 25 yaş üstü filtrele
GROUP BY departman        -- Sonra grupla
HAVING AVG(maas) > 5000;  -- Ortalaması yüksek grupları al
```

---

## ORDER BY: Sıralama

```sql
-- Artan sıra (varsayılan)
SELECT * FROM personel ORDER BY maas ASC;

-- Azalan sıra
SELECT * FROM personel ORDER BY maas DESC;

-- Çoklu sıralama
SELECT * FROM personel ORDER BY departman ASC, maas DESC;

-- Kolon numarasıyla
SELECT ad, soyad, maas FROM personel ORDER BY 3 DESC;  -- 3. kolon = maas
```

---

## Alt Sorgular (Subqueries)

```sql
-- WHERE içinde alt sorgu
SELECT * FROM personel
WHERE maas > (SELECT AVG(maas) FROM personel);

-- FROM içinde alt sorgu
SELECT dept, ort_maas
FROM (SELECT departman AS dept, AVG(maas) AS ort_maas
      FROM personel
      GROUP BY departman) AS alt;

-- IN ile alt sorgu
SELECT * FROM personel
WHERE dept_id IN (SELECT id FROM departman WHERE aktif = 1);

-- EXISTS ile alt sorgu
SELECT * FROM personel p
WHERE EXISTS (SELECT 1 FROM siparisler s WHERE s.personel_id = p.id);
```

---

## Veri Manipülasyonu (DML)

### INSERT
```sql
-- Tek satır
INSERT INTO personel (ad, soyad, maas)
VALUES ('Ali', 'Yılmaz', 5000);

-- Çoklu satır
INSERT INTO personel (ad, soyad, maas)
VALUES ('Ali', 'Yılmaz', 5000),
       ('Ayşe', 'Kaya', 6000),
       ('Can', 'Demir', 5500);

-- Başka tablodan
INSERT INTO personel_yedek
SELECT * FROM personel WHERE departman = 'IT';
```

### UPDATE
```sql
UPDATE personel
SET maas = 6000
WHERE id = 1;

UPDATE personel
SET maas = maas * 1.10  -- %10 zam
WHERE departman = 'IT';
```

### DELETE
```sql
DELETE FROM personel WHERE id = 1;

DELETE FROM personel WHERE departman = 'Test';

-- Tüm tabloyu temizle (dikkat!)
DELETE FROM personel;  -- Log tutar
TRUNCATE TABLE personel;  -- Hızlı, log tutmaz
```

---

## Flashcardlar

### Soru 1
**S:** NULL değerleri nasıl kontrol edilir?
**C:** IS NULL veya IS NOT NULL (= NULL YANLIŞ!)

### Soru 2
**S:** Sadece her iki tabloda eşleşen kayıtları getiren JOIN?
**C:** INNER JOIN

### Soru 3
**S:** Sol tablonun tamamını + eşleşenleri getiren JOIN?
**C:** LEFT JOIN

### Soru 4
**S:** GROUP BY sonrası filtreleme için ne kullanılır?
**C:** HAVING

### Soru 5
**S:** WHERE mi önce çalışır GROUP BY mi?
**C:** WHERE önce (FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY)

### Soru 6
**S:** Tekrarlayan değerleri elemek için?
**C:** SELECT DISTINCT

### Soru 7
**S:** LIKE'da sıfır veya daha fazla karakter için joker?
**C:** % (yüzde işareti)

### Soru 8
**S:** COUNT(*) ile COUNT(kolon) farkı?
**C:** COUNT(*) tüm satırları, COUNT(kolon) NULL olmayanları sayar

### Soru 9
**S:** NULL değerini başka değerle değiştirmek için?
**C:** COALESCE, ISNULL, NVL, IFNULL (DBMS'e göre)

### Soru 10
**S:** IN operatörü ne işe yarar?
**C:** Değerin bir liste içinde olup olmadığını kontrol eder

### Soru 11
**S:** BETWEEN 10 AND 20 neyi kapsar?
**C:** 10 ve 20 dahil aradaki değerler (inclusive)

### Soru 12
**S:** ORDER BY varsayılan sıralaması?
**C:** ASC (artan)

### Soru 13
**S:** Tablodaki en yüksek değeri bulmak için?
**C:** MAX(kolon)

### Soru 14
**S:** Bir kolondaki benzersiz değer sayısını bulmak için?
**C:** SELECT COUNT(DISTINCT kolon)

### Soru 15
**S:** 'A' ile başlayan isimleri bulmak için LIKE?
**C:** WHERE isim LIKE 'A%'

### Soru 16
**S:** TRUNCATE ve DELETE farkı?
**C:** TRUNCATE hızlı ve log tutmaz, DELETE log tutar ve WHERE kullanabilir

### Soru 17
**S:** Self JOIN ne demek?
**C:** Tablonun kendisiyle birleştirilmesi

### Soru 18
**S:** Aggregate fonksiyon WHERE'de kullanılabilir mi?
**C:** Hayır, HAVING'de kullanılmalı

### Soru 19
**S:** Kartezyen çarpım için hangi JOIN?
**C:** CROSS JOIN

### Soru 20
**S:** FULL OUTER JOIN ne döner?
**C:** Her iki tablonun tamamı (eşleşmeyenler NULL olarak)

---

## Sınav İpuçları

1. **NULL sorusu:** Her zaman IS NULL kullan, = NULL YANLIŞ!
2. **JOIN sorusu:** "Sadece eşleşenler" = INNER, "Tamamı" = LEFT/RIGHT/FULL
3. **WHERE vs HAVING:** WHERE satır filtreler, HAVING grup filtreler
4. **Sıralama:** Varsayılan ASC (artan)
5. **LIKE joker:** % = çok karakter, _ = tek karakter
6. **COUNT:** COUNT(*) NULL dahil, COUNT(kolon) NULL hariç
