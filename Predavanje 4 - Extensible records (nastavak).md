---
tags:
  - note
  - "#nbp"
index: "4"
---
21-02-24  06:05 PM
Status: #todo
Root (optional): [[Contents|Root]]
# Predavanje 4 - Extensible records (nastavak)

## Bigtable - Google (nastavak)

- rasuta, distribuirana, perzistentna, multi-dimenzionalna mapa;
- particije - tableti - po internet domenima;
- vrste
	- kljucevi vrsta su proizvoljni stringovi, maksimalna velicina 64KB;
	- podaci su leksikografski sortirani po kljucu vrste (prostorna lokalnost);
	- leksikografski bliske vrste se nalaze na jednom serveru ili su distribuirane u okviru malog broja servera;
	- pristup kolonama u vrsti je atomican;
- kolone, familije kolona
	- kljucevi kolona su proizvoljni stringovi;
	- broj kolona je neogranicen;
	- familiji kolona se pridruzuje informacija o tipu podatka;
	- podaci u familiji kolona se kompresuju i cuvaju zajedno;
	- kontrola pristupa je implementirana na nivou familije kolona;
- timestamp
	- svaka celija moze da ima vise vrednosti;
	- timestamp se moze rucno promeniti/dodeliti;
	- verzije - top N, nakon nekog datuma (timestamp-a), automatski garbage collection;
- tableti
	- opseg vrsta je dinamicki particionisan u tablete;
	- range scan operacije su jako efikasne;
	- kljucevi vrsta se biraju tako da povecavaju lokalnost operacija pristupa podacima - bliski podaci treba da budu u istom tabletu;
	- velicina tableta je otprilike 100-200GB, nakon toga se vrsi kompresija podataka;
- arhitektura bigtable sistema![[Pasted image 20240221182333.png]]
	- koristi se GFS;
	- Chubby distribuirani lock servis;
	- Map reduce;
	- jedan master;
	- veliki broj tablet servera;
- master server
	- samo jedan
	- operacije sa metapodacima;
	- load balancing;
	- garbage collection;
	- upravlja semom baze;
	- klijent pristupa direktno tabletima;
	- master server ne upravlja lokacijom tableta;
- tablet server
	- veliki broj;
	- upravljaju read/write/split operacijama;
- lokacija tableta (search do podatka) - B+ stablo
	- root chubby file;
	- prvi nivo - root metadata tablet - lokacija metadata tableta;
	- drugi nivo - metadata tablet - lokacija tableta;
	- klijenti kesiraju lokacije tableta;
	- root metadata tablet se nalazi na zasebnom serveru kako ne bi predstavvljao usko grlo (svi zahtevi prvo idu ka njemu);
	- bloom filter - citanje;

[[8. Osnovne karakteristike Column-store baze podataka. Objasniti na primeru Google BigTable modela podataka.]]

## Cassandra - Facebook

- Amazon Dynamo arhitektura (p2p prsten cvorova i operacije) + Google Bigtable model podataka;
- High (write) performance, CQL, Column oriented, tunable consistency, fault tolerance, elastic scalability, distributed, decentralized (p2p concept from dynamo);
- (C)AP (C is tunable - 1, 2, 3, quorum, all, local_quorum, each_quorum, local_one, any);
- arhitektura 2 data centra (follow the sun princip) i replikacija podataka![[Pasted image 20240221191413.png]]
- sistem je rack aware - replikovani podaci se nalaze u razlicitim rack-ovima i nastoji se da postoji po jedna replika u svakom data centre-u;
- dinamicko particionisanje - hash mehanizam (za razliku od Bigtable - tableti organizovani u B+ stablo) - consistent hashing;
- write/read/compaction == BigTable;
- write![[Pasted image 20240221192753.png]] ![[Pasted image 20240221193544.png]]
- read![[Pasted image 20240221193620.png]] ![[Pasted image 20240221193640.png]]

---
# References

- [Video 8](https://www.youtube.com/watch?v=A6nbQWxC2kg&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=8);

---
# Table of contents
```table-of-contents
```
