# Temel SQL Soru Havuzu

## 3.1 Sorgu Yurutme Sirasi (4 Soru)

### Soru 3.1.1
**Konu:** Yurutme Sirasi
**S:** SQL sorgusunda ilk calistirilan clause hangisidir?
**C:** FROM

### Soru 3.1.2
**Konu:** Yurutme Sirasi
**S:** SQL sorgu yurutme sirasini sirala.
**C:** FROM -> JOIN -> WHERE -> GROUP BY -> HAVING -> SELECT -> DISTINCT -> ORDER BY -> LIMIT

### Soru 3.1.3
**Konu:** Yurutme Sirasi
**S:** SELECT ve ORDER BY'dan hangisi once calistirilir?
**C:** SELECT once, ORDER BY sonra

### Soru 3.1.4
**Konu:** Yurutme Sirasi
**S:** WHERE ve GROUP BY'dan hangisi once calistirilir?
**C:** WHERE once, GROUP BY sonra

---

## 3.2 SELECT Temelleri (8 Soru)

### Soru 3.2.1
**Konu:** SELECT *
**S:** Bir tablodan tum kolonlari getirmek icin ne kullanilir?
**C:** SELECT * FROM tablo

### Soru 3.2.2
**Konu:** SELECT Kolonlar
**S:** Sadece ad ve soyad kolonlarini getirmek icin sorgu nasil yazilir?
**C:** SELECT ad, soyad FROM tablo

### Soru 3.2.3
**Konu:** DISTINCT
**S:** Tekrarlayan degerleri elemek icin ne kullanilir?
**C:** SELECT DISTINCT

### Soru 3.2.4
**Konu:** DISTINCT Ornek
**S:** Benzersiz departman isimlerini getirmek icin?
**C:** SELECT DISTINCT departman FROM personel

### Soru 3.2.5
**Konu:** Alias
**S:** Kolona takma isim vermek icin ne kullanilir?
**C:** AS (ornek: SELECT ad AS isim)

### Soru 3.2.6
**Konu:** Hesaplama
**S:** maas kolonunun 12 katiini gostermek icin?
**C:** SELECT maas * 12 AS yillik_maas FROM personel

### Soru 3.2.7
**Konu:** Concatenation
**S:** Oracle/PostgreSQL'de iki kolonu birlestirmek icin?
**C:** || operatoru (ornek: ad || ' ' || soyad)

### Soru 3.2.8
**Konu:** Concatenation
**S:** MySQL/SQL Server'da iki kolonu birlestirmek icin?
**C:** CONCAT fonksiyonu (ornek: CONCAT(ad, ' ', soyad))

---

## 3.3 WHERE Karsilastirma Operatorleri (5 Soru)

### Soru 3.3.1
**Konu:** Esitlik
**S:** SQL'de esitlik kontrolu icin hangi operator kullanilir?
**C:** = (tek esittir)

### Soru 3.3.2
**Konu:** Esit Degil
**S:** SQL'de "esit degil" icin hangi operator kullanilir?
**C:** <> (veya != bazi sistemlerde)

### Soru 3.3.3
**Konu:** Buyuk/Kucuk
**S:** Maasi 5000'den buyuk olanlari getirmek icin?
**C:** WHERE maas > 5000

### Soru 3.3.4
**Konu:** Buyuk Esit
**S:** Yasi 25 veya uzeri olanlari getirmek icin?
**C:** WHERE yas >= 25

### Soru 3.3.5
**Konu:** Kucuk Esit
**S:** Maasi 10000 veya altinda olanlari getirmek icin?
**C:** WHERE maas <= 10000

---

## 3.4 WHERE Mantiksal Operatorler (4 Soru)

### Soru 3.4.1
**Konu:** AND
**S:** AND operatoru ne yapar?
**C:** Her iki kosul da dogru olmali

### Soru 3.4.2
**Konu:** OR
**S:** OR operatoru ne yapar?
**C:** En az bir kosul dogru olmali

### Soru 3.4.3
**Konu:** NOT
**S:** NOT operatoru ne yapar?
**C:** Kosulun tersini alir

### Soru 3.4.4
**Konu:** Birlesik Kosul
**S:** Departmani IT VE maasi 5000'den fazla olanlari getirmek icin?
**C:** WHERE departman = 'IT' AND maas > 5000

---

## 3.5 BETWEEN (3 Soru)

### Soru 3.5.1
**Konu:** BETWEEN Tanim
**S:** BETWEEN operatoru ne ise yarar?
**C:** Aralik kontrolu (iki deger arasinda mi)

### Soru 3.5.2
**Konu:** BETWEEN Dahil
**S:** BETWEEN 10 AND 20 ifadesi 10 ve 20'yi dahil eder mi?
**C:** Evet, dahildir (inclusive)

### Soru 3.5.3
**Konu:** BETWEEN Ornek
**S:** Maasi 5000 ile 10000 arasinda olanlari getirmek icin?
**C:** WHERE maas BETWEEN 5000 AND 10000

---

## 3.6 IN (3 Soru)

### Soru 3.6.1
**Konu:** IN Tanim
**S:** IN operatoru ne ise yarar?
**C:** Degerin bir liste icinde olup olmadigini kontrol eder

### Soru 3.6.2
**Konu:** IN Ornek
**S:** Departmani IT, HR veya Finans olanlarý getirmek icin?
**C:** WHERE departman IN ('IT', 'HR', 'Finans')

### Soru 3.6.3
**Konu:** NOT IN
**S:** Departmani IT ve HR olmayanlari getirmek icin?
**C:** WHERE departman NOT IN ('IT', 'HR')

---

## 3.7 LIKE (5 Soru)

### Soru 3.7.1
**Konu:** % Joker
**S:** LIKE'da % joker karakteri ne anlama gelir?
**C:** Sifir veya daha fazla karakter

### Soru 3.7.2
**Konu:** _ Joker
**S:** LIKE'da _ joker karakteri ne anlama gelir?
**C:** Tam olarak bir karakter

### Soru 3.7.3
**Konu:** LIKE Baslayan
**S:** A ile baslayan isimleri bulmak icin?
**C:** WHERE isim LIKE 'A%'

### Soru 3.7.4
**Konu:** LIKE Biten
**S:** 'an' ile biten isimleri bulmak icin?
**C:** WHERE isim LIKE '%an'

### Soru 3.7.5
**Konu:** LIKE Iceren
**S:** Icinde 'li' gecen isimleri bulmak icin?
**C:** WHERE isim LIKE '%li%'

---

## 3.8 NULL Kontrolu (6 Soru)

### Soru 3.8.1
**Konu:** NULL Kontrolu
**S:** NULL degerleri nasil kontrol edilir?
**C:** IS NULL veya IS NOT NULL

### Soru 3.8.2
**Konu:** NULL Yanlis Kullanim
**S:** WHERE kolon = NULL dogru mu?
**C:** YANLIS! IS NULL kullanilmali

### Soru 3.8.3
**Konu:** NULL Neden
**S:** Neden = NULL kullanilmaz?
**C:** NULL bir deger degil, "deger yok" anlamina gelir. NULL ile yapilan karsilastirmalar UNKNOWN doner.

### Soru 3.8.4
**Konu:** IS NULL Ornek
**S:** Telefonu olmayanlari bulmak icin?
**C:** WHERE telefon IS NULL

### Soru 3.8.5
**Konu:** IS NOT NULL
**S:** Telefonu olanlari bulmak icin?
**C:** WHERE telefon IS NOT NULL

### Soru 3.8.6
**Konu:** COALESCE
**S:** NULL degerini baska degerle degistirmek icin?
**C:** COALESCE (standart), ISNULL (SQL Server), NVL (Oracle), IFNULL (MySQL)

---

## 3.9 INNER JOIN (4 Soru)

### Soru 3.9.1
**Konu:** INNER JOIN Tanim
**S:** INNER JOIN ne doner?
**C:** SADECE her iki tabloda eslesen kayitlar

### Soru 3.9.2
**Konu:** INNER JOIN Sozdizimi
**S:** INNER JOIN sozdizimi nasil yazilir?
**C:** SELECT ... FROM tablo1 INNER JOIN tablo2 ON tablo1.kolon = tablo2.kolon

### Soru 3.9.3
**Konu:** INNER JOIN Davranis
**S:** INNER JOIN'de eslesmeyen kayitlar ne olur?
**C:** Sonuca dahil edilmez

### Soru 3.9.4
**Konu:** INNER JOIN Kullanim
**S:** "Sadece eslesenleri getir" denirse hangi JOIN?
**C:** INNER JOIN

---

## 3.10 LEFT JOIN (3 Soru)

### Soru 3.10.1
**Konu:** LEFT JOIN Tanim
**S:** LEFT JOIN ne doner?
**C:** Sol tablonun TAMAMI + sagdan eslesenler

### Soru 3.10.2
**Konu:** LEFT JOIN Eslesmeme
**S:** LEFT JOIN'de sag tabloda eslesme yoksa ne olur?
**C:** Sag tablo kolonlari NULL doner

### Soru 3.10.3
**Konu:** LEFT JOIN Kullanim
**S:** "Tum personeli getir, departmani varsa goster" icin hangi JOIN?
**C:** LEFT JOIN (personel LEFT JOIN departman)

---

## 3.11 RIGHT JOIN (3 Soru)

### Soru 3.11.1
**Konu:** RIGHT JOIN Tanim
**S:** RIGHT JOIN ne doner?
**C:** Sag tablonun TAMAMI + soldan eslesenler

### Soru 3.11.2
**Konu:** RIGHT JOIN Eslesmeme
**S:** RIGHT JOIN'de sol tabloda eslesme yoksa ne olur?
**C:** Sol tablo kolonlari NULL doner

### Soru 3.11.3
**Konu:** RIGHT JOIN Kullanim
**S:** "Tum departmanlari getir, personeli varsa goster" icin hangi JOIN?
**C:** RIGHT JOIN (personel RIGHT JOIN departman)

---

## 3.12 FULL OUTER JOIN (2 Soru)

### Soru 3.12.1
**Konu:** FULL OUTER JOIN Tanim
**S:** FULL OUTER JOIN ne doner?
**C:** Her iki tablonun TAMAMI (eslesme olmayan satirlar NULL ile)

### Soru 3.12.2
**Konu:** FULL OUTER JOIN Kullanim
**S:** "Her iki tablodaki tum kayitlar" icin hangi JOIN?
**C:** FULL OUTER JOIN

---

## 3.13 CROSS JOIN ve SELF JOIN (2 Soru)

### Soru 3.13.1
**Konu:** CROSS JOIN
**S:** CROSS JOIN ne doner?
**C:** Kartezyen carpim (her satir x her satir)

### Soru 3.13.2
**Konu:** SELF JOIN
**S:** SELF JOIN ne demektir?
**C:** Tablonun kendisiyle birlestirilmesi

---

## 3.14 Aggregate Fonksiyonlar (6 Soru)

### Soru 3.14.1
**Konu:** COUNT(*)
**S:** COUNT(*) ne yapar?
**C:** Toplam satir sayisini doner (NULL dahil)

### Soru 3.14.2
**Konu:** COUNT(kolon)
**S:** COUNT(kolon) ne yapar?
**C:** NULL olmayan deger sayisini doner

### Soru 3.14.3
**Konu:** COUNT Fark
**S:** COUNT(*) ve COUNT(kolon) arasindaki fark?
**C:** COUNT(*) tum satirlari, COUNT(kolon) NULL olmayanlari sayar

### Soru 3.14.4
**Konu:** SUM ve AVG
**S:** SUM ve AVG ne yapar?
**C:** SUM: Toplam, AVG: Ortalama

### Soru 3.14.5
**Konu:** MIN ve MAX
**S:** MIN ve MAX ne yapar?
**C:** MIN: En kucuk, MAX: En buyuk

### Soru 3.14.6
**Konu:** COUNT DISTINCT
**S:** Benzersiz deger sayisini bulmak icin?
**C:** COUNT(DISTINCT kolon)

---

## 3.15 GROUP BY (4 Soru)

### Soru 3.15.1
**Konu:** GROUP BY Tanim
**S:** GROUP BY ne ise yarar?
**C:** Satirlari gruplara ayirir

### Soru 3.15.2
**Konu:** GROUP BY Ornek
**S:** Departman bazinda personel sayisi icin?
**C:** SELECT departman, COUNT(*) FROM personel GROUP BY departman

### Soru 3.15.3
**Konu:** GROUP BY Kural
**S:** GROUP BY kullanildiginda SELECT'te ne olmali?
**C:** Ya gruplanan kolon, ya da aggregate fonksiyon

### Soru 3.15.4
**Konu:** GROUP BY Coklu
**S:** Birden fazla kolona gore gruplamak icin?
**C:** GROUP BY kolon1, kolon2

---

## 3.16 HAVING (3 Soru)

### Soru 3.16.1
**Konu:** HAVING Tanim
**S:** HAVING ne ise yarar?
**C:** GROUP BY sonrasi gruplari filtreler

### Soru 3.16.2
**Konu:** HAVING Ornek
**S:** 5'ten fazla personeli olan departmanlari getirmek icin?
**C:** SELECT departman, COUNT(*) FROM personel GROUP BY departman HAVING COUNT(*) > 5

### Soru 3.16.3
**Konu:** HAVING Ozellik
**S:** HAVING'de aggregate fonksiyon kullanilabilir mi?
**C:** Evet, kullanilabilir

---

## 3.17 WHERE vs HAVING (3 Soru)

### Soru 3.17.1
**Konu:** Calisma Sirasi
**S:** WHERE mi once calisir HAVING mi?
**C:** WHERE once calisir (GROUP BY'dan once)

### Soru 3.17.2
**Konu:** Filtreleme Farki
**S:** WHERE ve HAVING arasindaki temel fark?
**C:** WHERE satirlari filtreler, HAVING gruplari filtreler

### Soru 3.17.3
**Konu:** Aggregate Fonksiyon
**S:** WHERE'de aggregate fonksiyon kullanilabilir mi?
**C:** Hayir, HAVING'de kullanilmali

---

## 3.18 ORDER BY (3 Soru)

### Soru 3.18.1
**Konu:** ORDER BY Varsayilan
**S:** ORDER BY varsayilan siralama yonu nedir?
**C:** ASC (artan)

### Soru 3.18.2
**Konu:** ORDER BY DESC
**S:** Maasa gore azalan siralamak icin?
**C:** ORDER BY maas DESC

### Soru 3.18.3
**Konu:** ORDER BY Coklu
**S:** Once departmana gore artan, sonra maasa gore azalan siralamak icin?
**C:** ORDER BY departman ASC, maas DESC

---

## 3.19 Alt Sorgular (4 Soru)

### Soru 3.19.1
**Konu:** Alt Sorgu WHERE
**S:** Ortalama maastan fazla alanlari getirmek icin?
**C:** WHERE maas > (SELECT AVG(maas) FROM personel)

### Soru 3.19.2
**Konu:** Alt Sorgu IN
**S:** Aktif departmanlardaki personeli getirmek icin?
**C:** WHERE dept_id IN (SELECT id FROM departman WHERE aktif = 1)

### Soru 3.19.3
**Konu:** EXISTS
**S:** EXISTS ne yapar?
**C:** Alt sorgu sonuc donerse TRUE, donmezse FALSE

### Soru 3.19.4
**Konu:** Alt Sorgu FROM
**S:** Alt sorgu FROM clause'unda kullanilabilir mi?
**C:** Evet, turetilmis tablo (derived table) olarak

---

## 3.20 INSERT (2 Soru)

### Soru 3.20.1
**Konu:** INSERT Sozdizimi
**S:** Tek satir eklemek icin sozdizimi?
**C:** INSERT INTO tablo (kolon1, kolon2) VALUES (deger1, deger2)

### Soru 3.20.2
**Konu:** INSERT Coklu
**S:** Birden fazla satir eklemek icin?
**C:** INSERT INTO tablo (kolon) VALUES (d1), (d2), (d3)

---

## 3.21 UPDATE (2 Soru)

### Soru 3.21.1
**Konu:** UPDATE Sozdizimi
**S:** UPDATE sozdizimi nasil yazilir?
**C:** UPDATE tablo SET kolon = deger WHERE kosul

### Soru 3.21.2
**Konu:** UPDATE Hesaplama
**S:** Tum personele %10 zam yapmak icin?
**C:** UPDATE personel SET maas = maas * 1.10

---

## 3.22 DELETE vs TRUNCATE (3 Soru)

### Soru 3.22.1
**Konu:** DELETE Sozdizimi
**S:** DELETE sozdizimi nasil yazilir?
**C:** DELETE FROM tablo WHERE kosul

### Soru 3.22.2
**Konu:** TRUNCATE
**S:** TRUNCATE ne yapar?
**C:** Tablodaki tum verileri hizlica siler

### Soru 3.22.3
**Konu:** DELETE vs TRUNCATE
**S:** DELETE ve TRUNCATE arasindaki farklar?
**C:** DELETE: WHERE kullanabilir, log tutar, yavas | TRUNCATE: Tum tablo, log tutmaz, hizli

---

## OZET

| Konu | Soru Sayisi |
|------|-------------|
| 3.1 Sorgu Yurutme Sirasi | 4 |
| 3.2 SELECT Temelleri | 8 |
| 3.3 WHERE Karsilastirma | 5 |
| 3.4 WHERE Mantiksal | 4 |
| 3.5 BETWEEN | 3 |
| 3.6 IN | 3 |
| 3.7 LIKE | 5 |
| 3.8 NULL Kontrolu | 6 |
| 3.9 INNER JOIN | 4 |
| 3.10 LEFT JOIN | 3 |
| 3.11 RIGHT JOIN | 3 |
| 3.12 FULL OUTER JOIN | 2 |
| 3.13 CROSS/SELF JOIN | 2 |
| 3.14 Aggregate | 6 |
| 3.15 GROUP BY | 4 |
| 3.16 HAVING | 3 |
| 3.17 WHERE vs HAVING | 3 |
| 3.18 ORDER BY | 3 |
| 3.19 Alt Sorgular | 4 |
| 3.20 INSERT | 2 |
| 3.21 UPDATE | 2 |
| 3.22 DELETE/TRUNCATE | 3 |
| **TOPLAM** | **74** |
