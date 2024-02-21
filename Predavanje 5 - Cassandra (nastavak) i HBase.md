---
tags:
  - note
  - "#nbp"
index: "5"
---
	21-02-24  07:42 PM
Status: #todo
Root (optional): [[Contents|Root]]
# Predavanje 5 - Cassandra (nastavak) i HBase

## Cassandra model podatak

- podsetnik o arhitekturi
	- quorum protokol - kao kod DynamoDB;
	- forsira se write operacija;
	- commit log, memory cache, flush u sstable, bloom filteri za search, ...
- model podataka - keyspace, column family, row key, column key;
- analogija sa RDBMS-om
	- database = keyspace;
	- table = column family;
	- primary key = row key;
	- column name = column key;
	- column value = column value;
- efikasne su operacije citanja po kljucu ili opsegu kljuceva (zbog sortiranosti);
- kljuc kolone/vrste predstavlja sam po sebi podatak;
- keyspace atributi
	- faktor replikacije - minimum 3;
	- faktor distribucije replikacija;
	- column families;
- kljuc = keyspace => column family => row key => column key;
- superkolone - zastareo koncept - kolone koje se sastoje od kolona;
- kolona kao struktura podataka:![[Pasted image 20240221195559.png]]
	- key 64KB, value 2GB (ali ne preterivati!), clock (long podatak);
- tipovi vrsta - wide rows, skinny rows;
- komparatori za sortiranje kolona - Ascii, Byte, ...;
- super kolona kao struktura podataka:![[Pasted image 20240221195819.png]]
- prica o modeliranju podataka - izbegavanje skinny rows pristupa + join, pristupom wide column, and ~~join~~;
- UUID/GUID - 128bit broj u formi stringa;
- PRIMARY KEY = partitioning key (vrlo bitan, koristi se za consistent hashing), clustering key (kljuc vrste);
- standardni use-case
	- katalozi proizvoda;
	- playliste;
	- recommender/personalization sistemi;
	- podaci prikupljeni sa senzora (IoT);
	- timeseries;
	- fraud detection;
	- kesiranje podataka;
- kada ne treba koristiti kasandru
	- stroga konzistentnost;
	- transakcije - ACID;
	- funkcije agregacije - analiticki upiti (COUNT, AVG, ...);
	- kompleksna pretraga - bez primarnog kljuca;
	- veliki broj citanja;
	- puno azuriranja i brisanja;
- query driven development i chebotko diagram - redundantnost podataka;
- CQL vs Thrift API;

## HBase - Apache

- HDFS - Hadoop Distributed File System;
	- Podrzava MapReduce operacije;
	- Stvoren za batch, offline obradu;
- HBase - sloj iznad HDFS-a koji omogucava njegovo funkcionisanje kao servera - slanje upita kroz mrezu i dobijanje odgovora;

[[14. HADOOP – pojam i osnovne karakteristike.]]
[[15. HADOOP ekosistem – osnovni elementi, arhitektura i gde se primenjuje.]]
[[16. HDFS – osnovni pojmovi.]]
[[17. Pojam MapReduce tehnike.]]
[[18. HBASE – osnovne karakteristike, model podataka, primeri korišćenja, dobre i loše strane korišćenja.]]

---
# References

- [Video 9](https://www.youtube.com/watch?v=JRAPw7G9440&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=9);
- [Video 10](https://www.youtube.com/watch?v=C45AOFpn0to&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=10);

---
# Table of contents
```table-of-contents
```
