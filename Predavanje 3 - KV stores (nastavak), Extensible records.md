---
tags:
  - note
  - "#nbp"
index: "3"
---
21-02-24  03:05 PM
Status: #todo
Root (optional): [[Contents|Root]]
# Predavanje 3 - KV stores (nastavak), Extensible records

## Redis (nastavak)

- Redis Pub/Sub
	- Message Q mehanizam;
	- PUBLISH, SUBSCRIBE, UNSUBSCRIBE;
- Redis replikacija - Master/slave mehanizam replikacije;
	- svaki slejv je read-copy - skaliramo operaciju citanja;
	- arhitektura - master w. no pers., slave with AOF;
- Redis cluster - automatsko particionisanje podataka na vise instanci - horizontalno skaliranje (fragmentacija);
- klaster + replikacija - cesta kombinacija;![[Pasted image 20240221152548.png]]
- Redis sentinel - sistem za monitoring Redis klastera - monitoring, notifikacija, automatski failover (failover - slave preuzima ulogu mastera);
- Tipicne redis primene:
	- session cache;
	- full-page cache;
	- red poruka;
	- brojaci;
	- leaderboards, scoreboards;
	- pub/sub;
	- real-time analytics;
	- distributed locks - apache zookeeper kao bolja alternativa, Redlock algoritam;
	- graf baza, 

## DynamoDB - Amazon

- DHT - distributed hash table;
- p2p arhitektura;
- pretraga po primarnom kljucu;
- definisanje nivoa konzistentnosti;
- inkrementalna skalabilnost - laka zbog p2p;
- prsten cvorova, virtuelni cvorovi;
- n kopija;
- vector clock mehanizam - write operacija je optimizovana;
- dynamo r/w operacije - nalik na *konsenzus* algoritam:
	- zahtev stize do koordinatora (najmanje opterecen ili geografski najblizi);
	- koordinator generise verziju podatka i vector clock + quorum protocol => write je zavrsen;
	- read - razresavanje konflikata i read-repair;
	- write optimizovaniji od read-a;
- podesiva konzistentnost - ONE, QUORUM, ALL;
- hinted handoff - write operacija uvek prolazi;
- gossip (epidemic) protocol - kao heartbeats princip kod RAFT-a;

[[12. Osnovne karakteristike key-value baza podataka. Objasniti na primeru Dynamo modela podataka.]]

## Voldemort - LinkedIn

- OSS - nalik na Dynamo, ne previse popularan;

# Extensible records/Wide column stores

- kratka digresija - column store - data warehouse i OLAP;
- sve se nalazi u jednom rekordu (vrsti), koji je ekstenzibilan;
- Google Bigtable - rasuta, distribuirana, perzistentna multi-dimenzionalna sortirana mapa (tablica, hash);
	- row key, column key, timestamp;

---
# References

- [Video 6](https://www.youtube.com/watch?v=1naxyAGYk5w&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=6);
- [Video 7]();

---
# Table of contents
```table-of-contents
```
