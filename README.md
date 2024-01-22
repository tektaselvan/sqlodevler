## Ödev 1

1- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

Sorgu:

select title, description from film; 


2- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

Sorgu:

select * from film where length > 60 and length < 75;

3- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

Sorgu:

select * from film where rental_rate = 0.99 and replacement_cost = 12.99 or replacement_cost = 28.99;


4- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

Sorgu:

select * from customer first_name = 'Mary';


5- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

Sorgu:

select * from film where length < 50 and not (not (rental_rate = 2.99 or rental_rate = 4.99));


## Ödev 2

1- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

Sorgu:

select * from film 
where BETWEEN (replacement_cost => 12.99  and replacement_cost < 16.99);

2- .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

Sorgu:

select first_name, last_name from actor where 
first_name IN ('Penelope', 'Nick', 'Ed');

3- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

Sorgu:

select * from film 
where rental_rate IN(0.99, 2.99, 4.99) AND replacement_cost IN(12.99, 15.99, 28.99);

## Ödev 3 | LIKE ILIKE

1- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
Sorgu:
select * from Country where country LIKE 'A%' and country LIKE '%a';

2- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
Sorgu:
select * from country where LEN(country) = 6 and country LIKE '%a';

3- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.
Sorgu:
SELECT * FROM film WHERE name LIKE '%t%t%t%t%';

4- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
Sorgu:
select * from film where title LIKE 'C%' and lenght>90 and rental_rate = 2.99;

## Ödev 4 | DISTINCT ve COUNT

1- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

Sorgu:

Select distinct replacement_cost from film;

2- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

Sorgu:

Select Count(distinct replacement_cost) from film;

3- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

Sorgu:

select count(*) from film where title LIKE 'T%' and rating = 'G';

4- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

Sorgu:

select count(*) from country where lenght(country) = 5;

5- city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

select count(*) from city where city ILIKE '%r';

## Ödev 5 | LIMIT AND OFFSET

1- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

Sorgu:

select * from film where title LIKE '%n' order by lenght desc limit 5;

2- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

Sorgu:

select * from film where title LIKE '%n' order by lenght asc offset 5 limit 5;

3- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

Sorgu:

select * from customer where store_id = 1 order by last_name desc limit 4;

## Ödev 6 

1- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

Sorgu:

select AVG(rental_rate) from film;

2- film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

Sorgu:

select Count(*) from film where title LIKE 'C%';

3- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

Sorgu: 

select * from film where rental_rate = 0.99 order by lenght desc limit 1; veya select max(length) from film where rental_rate = 0.99;


4- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

Sorgu:

select count(DISTINCT replacement_cost) from film where length > 150;

## Ödev 7 | GROUP BY AND HAVING

1- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

Sorgu:

select  rating,  COUNT(*) from  film group by rating;

2- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

Sorgu:

select replacement_cost, COUNT(*) film group by replacement_cost having COUNT(*) > 50;

3- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

Sorgu:

select store_id, COUNT(*) from customer group by store_id;

4- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

Sorgu:

select country_id, COUNT(*) from city group by country_id order by COUNT(*) DESC LIMIT 1;

## Ödev 8 UPDATE | DELETE

1- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

Sorgu:

CREATE TABLE employee(
id INTEGER ,
name  VARCHAR(50),
birthday DATE,
email VARCHAR(100)
)

2- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

Sorgu:

insert into employee (id, name, email, birthday) values (1, 'Mirabelle', 'mdedomenico0@nationalgeographic.com', '2023-01-18');
insert into employee (id, name, email, birthday) values (2, 'Johnathan', 'jbarosch1@washington.edu', '2023-01-21');
insert into employee (id, name, email, birthday) values (3, 'Wini', 'wpeirazzi2@seesaa.net', '2023-04-22');

3- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

Sorgu:


UPDATE  employee SET name= 'Winnie  De Pooh' WHERE name='Wini'

UPDATE  employee SET name= '*' WHERE name='Astrix'

4- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

Sorgu:

DELETE FROM employee WHERE name='Please%'

DELETE FROM employee WHERE LENGTH(name)>8

## Ödev 9 INNER JOIN

1- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

Sorgu:

select 
