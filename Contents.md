---
tags:
  - "#contents"
  - "#root"
aliases:
  - Root
---
![[Pasted image 20240220232318.png]]

```dataview
TABLE
FROM #note
WHERE index != null AND index != "-1"
SORT index ASC
```

```dataview
TABLE
FROM #answer
WHERE index != null AND index != "-1"
SORT index ASC
```

1. ~~Karakteristike podataka na Web-u. Primeri struktuiranih i polustruktuiranih podataka.~~
2. ~~Web aplikacija i relacione baze podataka. Prednosti korišćenja I nedostaci.~~
3. ~~Distribuirane baze podataka: pojam, skalabilnost i zahtevi koje moraju da zadovolje.~~
4. ~~CAP torema, CAE trade-off, BASE, poređenje BASE i ACID.~~
5. ~~Pojam NoSQL baza podataka, karakteristike, dobre i loše strane.~~
6. ~~Taksonomija NoSQL baza podataka.~~
7. Osnovne karakteristike document baza podataka. Objasniti na primeru MongoDB baze podataka.
8. ~~Osnovne karakteristike Column-store baze podataka. Objasniti na primeru Google BigTable modela podataka.~~
9. ~~Osnovne karakteristike Column-store baze podataka. Objasniti na primeru Cassandra modela podataka.~~
10. Osnovne karakteristike graf baza podataka. Objasniti na primeru Neo4J baze podataka.
11. ~~Osnovne karakteristike key-value baza podataka. Objasniti na primeru Redis baze podataka.~~
12. ~~Osnovne karakteristike key-value baza podataka. Objasniti na primeru Dynamo modela podataka.~~
13. Objasniti pojam BigData.
14. ==HADOOP – pojam i osnovne karakteristike.==
15. ==HADOOP ekosistem – osnovni elementi, arhitektura i gde se primenjuje.==
16. ~~HDFS – osnovni pojmovi.~~
17. ~~Pojam MapReduce tehnike.~~
18. ~~HBASE – osnovne karakteristike, model podataka, primeri korišćenja, dobre i loše strane korišćenja.~~
19. Objasniti pojam vremenskih serija podataka.
20. Objasniti pojam time series baza podata.
21. Primeri time series baza podataka (focus na InfluxDB bazi podataka).
22. Objasnite pojam pretraživanja informacija.
23. Objasnite pojam invertovanog indeksa.
24. Lucene biblioteke – namena i osnovne karakteristike.
25. Elasticsearch – namena i osnovne karaktersitike.
26. ==Objasniti pojam semantičkog Web-a.==
27. ==Objasniti pojam ontologija.==
28. ==Triplestore- pojam, osnovne karakteristike i namena.==