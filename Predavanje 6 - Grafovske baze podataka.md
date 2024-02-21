---
tags:
  - note
  - "#nbp"
index: "6"
---
21-02-24  10:54 PM
Status: #todo
Root (optional): [[Contents|Root]]
# Predavanje 6 - Grafovske baze podataka

- povezanost podataka - name of the game;
- GGG - Giant Global Graph - ceo Web jedna velika baza podataka;
- polustruktuiranost/nestruktuiranost podataka;
- broj veza izmedju entiteta moze drasticno da varira;
- RDBMS - entity first != GraphDB - relationship first;
- **property graph** - svaki cvor/poteg ima property-e;
- specijalizovane graf baze podataka
	- triplestore (RDF), mrezne baze podataka;
- rdbms => jednostavan lookup, nije optimizovana za joinove;
- graf baze => kompleksne strukture sa puno veza;

## Neo4j

- graf svojstava (property graph);
- Full ACID;
- embedded resenje u javi;
- server resenje;
- High availability - enterprise resenje;
- recommender sistemi, analiziranje podataka iz click stream-a;
- cvorovi
  ![[Pasted image 20240221233004.png]]
- relacija
  ![[Pasted image 20240221233017.png]]
- putanja - kolekcija cvorova koji su medjusobno povezani relacijama;
- rezultat upita jeste putanja;
- admin panel na 7474, REST API, podrska za streaming;
- Cypher - QL;
	- SparQL - Triplestore baze podataka;
	- START, MATCH, WHERE, RETURN, CREATE, DELETE, SET, FOREACH, WITH, ...;
- koriste se indeksi za lookup pretragu grafa (indeksi za svojstva);
- lucene indeks za full-text pretragu;
- tipicna primena:
	- drustvene mreze;
	- recommender sistemi;
	- knowledge grafovi;
	- fraud detection sistemi;
	- supply chain management;
	- upravljanje identitetom i pravima pristupa;
	- evidencija o mreznoj infrastrukturi;
	- upravljanje domenskim (master) modelom;

---
# References

- [Video 11](https://www.youtube.com/watch?v=zudAcuDZQdI&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=11);

---
# Table of contents
```table-of-contents
```
