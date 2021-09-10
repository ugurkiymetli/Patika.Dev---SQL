
# Patika.Dev SQL Ödevleri
<a href='#Ödev 1'>Ödev 1</a><br>
<a href='#Ödev 2'>Ödev 2</a><br>
<a href='#Ödev 3'>Ödev 3</a><br>
<a href='#Ödev 4'>Ödev 4</a><br>
<a href='#Ödev 5'>Ödev 5</a><br>
<a href='#Ödev 6'>Ödev 6</a><br>
<a href='#Ödev 7'>Ödev 7</a><br>
<a href='#Ödev 8'>Ödev 8</a><br>
<a href='#Notlar' >Notlar</a><br>
## <p id = 'Ödev 1' > Ödev 1 </p> 
1.`film` tablosunda bulunan `title` ve `description` sütunlarındaki verileri sıralayınız.

```sql
SELECT title, description FROM film;
```

---

2.`film` tablosunda bulunan tüm sütunlardaki verileri `film` uzunluğu (`length`) 60'dan *büyük* **VE** 75'ten *küçük* olma koşullarıyla sıralayınız.

```sql
SELECT * FROM film 
WHERE length > 60 AND length < 75;
```

---

3.`film` tablosunda bulunan tüm sütunlardaki verileri `rental_rate` 0.99 **VE** `replacement_cost` 12.99 **VEYA** 28.99 olma koşullarıyla sıralayınız.

```sql
SELECT * FROM film 
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99) ;
```

---

4.`customer` tablosunda bulunan `first_name` sütunundaki değeri '**Mary**' olan müşterinin `last_name` sütunundaki değeri nedir?

```sql
SELECT last_name FROM customer
WHERE first_name = 'Mary';
```
*Cevap*
|       | last_name |
| ----------- | ----------- |
| 1      | **Smith**       |

---

5.`film` tablosundaki uzunluğu (`length`) 50'den *büyük* **OLMAYIP** aynı zamanda `rental_rate` değeri 2.99 **VEYA** 4.99 **OLMAYAN** verileri sıralayınız.

```sql
SELECT * FROM film
WHERE NOT length > 50 AND NOT (rental_rate = 2.99 or rental_rate = 4.99);
```

---

## <p id = 'Ödev 2' > Ödev 2 </p>
1.`film` tablosunda bulunan tüm sütunlardaki verileri `replacement_cost` değeri 12.99'dan *büyük eşit*  **VE** 16.99'dan *küçük* olma koşuluyla sıralayınız ( *BETWEEN - AND yapısını kullanınız.*)

```sql
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

---

2.`actor` tablosunda bulunan `first_name` ve `last_name` sütunlardaki verileri `first_name` 'Penelope' **veya** 'Nick' **veya** 'Ed' değerleri olması koşuluyla sıralayınız. ( *IN operatörünü kullanınız.*)

```sql
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope','Ed','Nick');
```

---

3.`film` tablosunda bulunan tüm sütunlardaki verileri `rental_rate` 0.99, 2.99, 4.99 **VE** `replacement_cost` 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( *IN operatörünü kullanınız.*)

```sql
SELECT * FROM film
WHERE rental_rate  IN (0.99, 2.99, 4.99) 
AND replacement_cost IN (12.99, 15.99, 28.99 ) ;
```

---

## <p id = 'Ödev 3' > Ödev 3 </p>
1.`country` tablosunda bulunan `country` sütunundaki ülke isimlerinden 'A' karakteri ile *başlayıp* 'a' karakteri ile *sonlananları* sıralayınız.
```sql
SELECT  * FROM country
WHERE country LIKE 'A%a'; 
```

---

2.`country` tablosunda bulunan `country` sütunundaki ülke isimlerinden en az *6* karakterden oluşan *ve* sonu 'n' karakteri ile *sonlananları* sıralayınız.
```sql
SELECT  * FROM country
WHERE country LIKE '______%n'; 
```

---

3.`film` tablosunda bulunan `title` sütunundaki film isimlerinden en az *4* adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
```sql
SELECT  * FROM film
WHERE title ILIKE '%T%T%T%T%'; 
```

---

4.`film` tablosunda bulunan tüm sütunlardaki verilerden `title` 'C' karakteri ile başlayan ve uzunluğu (`length`) 90 dan *büyük* olan ve `rental_rate` 2.99 olan verileri sıralayınız.
```sql
SELECT  * FROM film
WHERE title LIKE 'C%' 
		AND length > 90
		AND rental_rate = 2.99; 
```

---

## <p id = 'Ödev 4' > Ödev 4 </p> 
1.`film` tablosunda bulunan `replacement_cost` sütununda bulunan birbirinden *farklı* değerleri sıralayınız.
```sql
SELECT DISTINCT (replacement_cost) FROM film; 
```

---

2.`film` tablosunda bulunan `replacement_cost` sütununda birbirinden *farklı* kaç tane veri vardır?
```sql
SELECT COUNT (DISTINCT (replacement_cost)) FROM film; 
```

---

3.`film` tablosunda bulunan film isimlerinde (`title`) kaç tanesini 'T' karakteri ile *başlar* ve aynı zamanda rating 'G' ye *eşittir*?
```sql
SELECT COUNT (*) FROM film
WHERE title LIKE 'T%' 
AND rating = 'G'; 
```

---

4.`country` tablosunda bulunan ülke isimlerinden (`country`) kaç tanesi 5 karakterden *oluşmaktadır*?
```sql
SELECT COUNT (*) FROM country
WHERE country LIKE '_____'; 
```

---

5.`city` tablosundaki şehir isimlerinin kaçtanesi 'R' veya 'r' karakteri ile *biter*?
```sql
SELECT COUNT (*) FROM city
WHERE city LIKE '%r'; 
```

---

## <p id = 'Ödev 5' > Ödev 5 </p> 
1.`film` tablosunda bulunan ve film ismi (`title`) 'n' karakteri ile biten *en uzun* (`length`) 5 filmi sıralayınız.

```sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5; 
```

---

2.`film` tablosunda bulunan ve film ismi (`title`) 'n' karakteri ile biten *en kısa* (`length`) ikinci 5 filmi sıralayınız.

```sql
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length
LIMIT 5; 
```

---

3.`customer` tablosunda bulunan `last_name` sütununa göre *azalan* yapılan sıralamada *store_id = 1* olmak koşuluyla *ilk 4* veriyi sıralayınız.

```sql
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4; 
```

---

## <p id = 'Ödev 6' > Ödev 6 </p> 
1.`film` tablosunda bulunan `rental_rate` sütunundaki değerlerin *ortalaması* nedir?

```sql
SELECT ROUND(AVG(rental_rate), 3) FROM film; 
```

---

2.`film` tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile *başlar*?

```sql
SELECT COUNT(*) FROM film
WHERE title LIKE 'C%'; 
```

---

3.`film` tablosunda bulunan filmlerden `rental_rate` değeri *0.99'a eşit* olan en uzun (`length`) film kaç dakikadır?

```sql
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99; 
```

---

4.`film` tablosunda bulunan filmlerin uzunluğu *150 dakikadan büyük* olanlarına ait kaç *farklı* `replacement_cost` değeri vardır?

```sql
SELECT COUNT(DISTINCT(replacement_cost)) 
FROM film
WHERE length > 150; 
```

---

## <p id = 'Ödev 7' > Ödev 7 </p> 

1.`film` tablosunda bulunan filmleri `rating` değerlerine göre *gruplayınız*.

```sql
SELECT rating FROM film
GROUP BY rating; 
```

---

2.`film` tablosunda bulunan filmleri `replacement_cost` sütununa göre grupladığımızda *film sayısı 50'den fazla* olan `replacement_cost` değerini ve karşılık gelen film sayısını sıralayınız.

```sql
SELECT replacement_cost,COUNT(*) 
FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50; 
```

---

3.`customer` tablosunda bulunan `store_id` değerlerine karşılık gelen *müşteri sayıları* nelerdir?

```sql
SELECT store_id, COUNT(*) 
FROM customer
GROUP BY store_id;  
```

---

4.`city` tablosunda bulunan şehir verilerini `country_id` sütununa göre *gruplandırdıktan* sonra *en fazla şehir* sayısı barındıran `country_id` bilgisini ve şehir sayısını paylaşınız.

```sql
SELECT country_id, COUNT(city) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1 ;  
```

---


## <p id = 'Ödev 8' > Ödev 8 </p> 

1.`test` veritabanınızda `employee` isimli sütun bilgileri `id (INTEGER)`, `name VARCHAR(50)`, `birthday DATE`, `email VARCHAR(100)` olan bir tablo oluşturalım.
```sql
CREATE TABLE employee (
	id INTEGER,
	name VARCHAR(50), 
	birthday DATE, 
	email VARCHAR(100) );

```

---

2.Oluşturduğumuz `employee` tablosuna [_Mockaroo_](https://www.mockaroo.com/) servisini kullanarak 50 adet veri ekleyelim.
    - [Oluşturulan veri seti.](https://www.mockaroo.com/49c986e0)

---

3.Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```sql
UPDATE employee
SET 
	name = 'lorem ipsum', 
	birthday = '1980-01-01', 
	email = 'lorem@ipsum.com' 
WHERE id = 1;
-----------------
UPDATE employee  
SET
	name = 'lorem ipsum',
	birthday = '1980-01-01',
	email = 'lorem@ipsum.com'
WHERE name LIKE 'A%';
-----------------
UPDATE employee  
SET
	name = 'lorem ipsum',
	birthday = '1980-01-01',
	email = 'lorem@ipsum.com'
WHERE birthday BETWEEN '1990-01-01' AND '1995-01-01'; 
```

---

4.Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```sql
DELETE FROM employee 
WHERE birthday BETWEEN '1970-01-01' AND '1995-01-01';
-----------------
DELETE FROM employee 
WHERE name LIKE 'A%';
-----------------
DELETE FROM employee 
WHERE name LIKE 'Sa%' AND
birthday < '2000-01-01';
-----------------
DELETE FROM employee 
WHERE email LIKE 'a%' AND
birthday BETWEEN '1981-01-01' AND '2004-01-02';
```

---

### <p id = 'Notlar'> Notlar </p>
- LIKE ve ILIKE kullanımı
    - *%* operatörü sıfır veya birden fazla karakter için yer tutucu işlevi görür.
    - *_* operatörü bir adet karakter için yer tutucu görevi görür.  
    - *[ ]* operatörü parantez içindeki karakter listesi için yer tutucu görevi görür.
    - *!* operatörü parantez içindeki karakter listesi dışındakiler için yer tutucu görevi görür.
    - *#* operatörü bir adet numerik karakter için yer tutucu görevi görür.

| LIKE operatörü                |   Açıklama                                                            |
| -----------                   |   -----------                                                         |
|WHERE Column1 LIKE 'a%'        |	"a" ile başlayan bütün değerleri bulur.                             |
|WHERE Column1 LIKE '%a'        |	"a" ile biten bütün değerleri bulur.                                |
|WHERE Column1 LIKE '%or%'      |	İçinde "or" bulunan bütün değerleri bulur.                          |
|WHERE Column1 LIKE '_r%'       |	İkinci karakteri "r" olan bütün değerleri bulur.                    |
|WHERE Column1 LIKE 'a_%'       |	"a" ile başlayan ve en az 2 karakter olan bütün değerleri bulur.    |
|WHERE Column1 LIKE 'a__%'      |	"a" ile başlayan ve en az 3 karakter olan bütün değerleri bulur.    |
|WHERE Column1 LIKE 'a%o'       |	"a" ile başlayan ve "o" ile biten bütün değerleri bulur.            |
|WHERE Column1 LIKE 'h[oa]t'    |   hot, hat değerlerini bulur. (hit değerini getirmez!)                |
|WHERE Column1 LIKE 'c[a-c]t'   |   cat, cbt, cct, değerlerini bulur.                                   |

- LIMIT ve OFFSET
    - OFFSET ekranda sayfada görüntülenecek ürün miktarını belirleyebilir. ([pagination](https://www.petefreitag.com/item/451.cfm))


