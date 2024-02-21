---
tags:
  - note
  - "#nbp"
index: "2"
---
21-02-24  01:39 AM
Status: #todo
Root (optional): [[Contents|Root]]
# Predavanje 2 - Key-value stores

## NoSQL

- NoSQL - pokret a ne specifikacija;
- Google - [Bigtable whitepaper](https://cloud.google.com/bigtable/docs) (2006) - wide column;
- [Dynamo whitepaper](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf) - KV store, Amazon;
- [**Cassandra**](https://cassandra.apache.org/_/index.html) - Facebook, wide columnd;
- [Voldemort](http://www.project-voldemort.com/voldemort/) - KV store, LinkedIn;
- Tipicna primena NoSQL resenja:
	- Velike kolicine podataka;
	- Veliki broj upita;
	- Schema evolution (flexibility);

[[5. Pojam NoSQL baza podataka, karakteristike, dobre i loše strane.]]

- Dobre strane NoSQL:
	- fleksibilnost;
	- skalabilnost;
	- eventually consistent;
	- jeftine;
	- prilagodjene potrebama Web aplikacija;
- Lose strane:
	- tehnologija jos uvek nije stabilna;
	- ne postoje zajednicki standardi;
	- losa podrska za transakcije;
	- losa podrska za pretrazivanje podataka;
	- zahtev promene nacina razmisljanja - query-driven pristup;
	- vrlo tesko naci dva identicna scenarija primene;
- Taksonomija
	- KV store,
	- Extensible records/Wide column store,
	- Document stores,
	- Graph dbs;

[[6. Taksonomija NoSQL baza podataka.]]

- KV stores - kljuc: blob;
- Column stores - Bigtable klonovi;
	- rasuta, distribuirana, multidimenzionalna sortirana mapa;
- Document store - Kljuc: Document;
	- Document vs Blob - Document store vs KV store;
- Graph store - modeliran po grafu, cvorovi/potezi se identifikuju pomocu kljuceva a value moze biti mapa/dokument;

## KV stores

- ideja je u osnovi svega - koristi ideju kao i najmocnija struktura podataka - hash mapa (tablica);
- prednosti:
	- pretraga po kljucu - konzistentna;
	- jednostavno horizontalno skaliranje - sharding;
	- fleksibilnost seme;
	- memorijska efikasnost;
	- OR mismatch ne postoji;
	- sprega sa RDBMS, najcesce u ulozi kesa;
- nedostaci:
	- nepostojanje kompleksnih upita;
	- nepostojanje stranih kljuceva;
	- aplikativna logika za kreiranje spojeva/relacija;
	- nedostatak standardizacije;
- poznata resenja - redis, memchached, dynamo, ...

## Redis

[[11. Osnovne karakteristike key-value baza podataka. Objasniti na primeru Redis baze podataka.]]

- REDIS - **RE**mote **DI**ctionary **S**erver;
- besplatan, OSS, kompletno razvijen ANSI C-om (portabilan, efikasan), ...
- value moze da bude i struktura podataka (ne mora biti BLOB);
- in-memory baza podataka - brza ali volatile;
- perzistencija (non-volatile mehanizmi) - RDB/snapshoting i AOF, odnosno njihova kombinacija;
- gubimo durability;
- redis je single threaded proces - jedna nit obradjuje zahteve i to po FIFO principu;
	- nema potrebe za zakljucavanje;
	- Atomicity, Consistency, Isolation, ~~Durability~~;
- Redis koristi _binary safe_ kljuceve, 512MB je maks. velicina kljuca;
- ==sema imenovanja kljuceva== - namespace separation, not to short, readable;
- value strukture podataka:
	- stringovi, liste, skupovi, sortirani skupovi, bitmape, hyperloglogs, ...
	- strings (string), sets (set), sorted sets (zset), hashes (hash), lists (list), bitmaps, bitfields, hyperloglogs, geospatial indexes, streams, ...

### Data structures

- String
	- ono sto bi bio blob;
	- binary safe;
	- SET, GET, INCR, INCRBY, DECR, DECRBY, GETSET, MSET, MGET, ...;
	- reprezentativan use case - Blob cache;
- Lista 
	- lancana lista stringova;
	- LPUSH/RPUSH, LPOP/RPOP, LRANGE, LTRIM, LLEN, LREM, LINSERT, ...;
	- reprezentativan use case - top N, producer-consumer komunikacija izmedju dva procesa;
- Set
	- neuredjena kolekcija stringova;
	- SADD, SISMEMBER, SMEMBERS, SREM, SRANDMEMBERS, SPOP, SINTER, SUNION, SDIFF, ...;
	- reprezentativan use case - primer seme imenovanja;
- Hash
	- kolekcija KV parova;
	- reprezentativan use case - pogodni za predstavljanje objekata;
	- HSET/HGET,  HMSET/HMGET, HLEN, HKEYS, HGETALL, ...;
- Sorted set (Zset)
	- setovi sa skorom - svaka vrednost u skupu ima dodeljen score;
	- ZADD, ZREM, ZRANGE, ...;
	- reprezentativan use case - leaderboard (sortiranje po nekom numerickom kriterijumu), ...;
- Bitmap
	- string na koji mogu da se primenjuju bitwise operacije;
	- maks velicina 512MB;
	- SETBIT/GETBIT, BITOP, BITCOUNT,  BITPOS, ...;
	- reprezentativan use case - usteda memorije za cuvanje gomile flegova;
- Operacije nezavisne od tipa - EXISTS, DEL, TYPE - skupe pretrage O(n);
- EXPIRE/PERSIST - zadavanje timeout ogranicenja postojanja podatka;
- MULTI + EXEC - **redis transakcija** - naredbe jednog korisnika se izvrsavaju sekvencijalno - operacije drugog korisnika tek nakon zavrsetka;

---
# References

- [Video 4](https://www.youtube.com/watch?v=JPR3dkVtfnM&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=4);
- [Video 5](https://www.youtube.com/watch?v=G4_wl4VuWpk&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=5);

---
# Table of contents
```table-of-contents
```
