
# Patika.Dev SQL Ödevleri
<a href='#Ödev 1'>Ödev 1</a><br>
<a href='#Ödev 2'>Ödev 2</a><br>
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



