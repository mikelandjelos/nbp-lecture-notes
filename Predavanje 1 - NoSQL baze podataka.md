---
tags:
  - note
  - nbp
index: "1"
---
20-02-24  11:50 PM
Status: #done
Root (optional): [[Contents|Root]]
# Predavanje 1 - NoSQL baze podataka

## Uvod

- mrezni i hijerarhijski modeli, nestandardizovana resenja;
- **STANDARDIZACIJA**!!!
- relacione baze podataka (RDBMS) - standardizovane, dobar teorijski model (relacioni);
- objektno-orijentisane i objektno-relacione baze podataka - nije uspelo da dodje do izrazaja;
- zatim dosao na red NoSQL - ponovna pojava mreznih i hijerarhijskih modela pored relacionih;
- NewSQL = NoSQL + RDBMS?
- => recikliranje vec poznatih stvari za kreiranje novih resenja;

## AC(I)D

- Atomicity, Consistency, Isolation, Durability;
- pojam **transakcije** - niz naredbi za manipulaciju podacima povezanih u logicku celinu;
- Atomicity - atomicnost - sve ili nista;
- Consistency - konzistentnost - zadovoljena sva definisana pravila i protokoli;
- Isolation - izolacija - nijedna transakcija nema pristup drugoj transakciji koja nije zavrsena;
	- nivoi izolacije - serijabilne transakcije, read only transakcije, read uncommited, ...
- Durability - trajnost - kada se transakcija zavrsi, izmene su trajne (cak i u slucaju kraha sistema);

## Podaci na Web-u

[[1. Karakteristike podataka na Web-u. Primeri struktuiranih i polustruktuiranih podataka.]]

- Karakteristike:
	- velika kolicina podataka;
	- povezanost podataka - relacije;
	- polustruktuiranost podataka;
	- arhitektura aplikacija koje koriste podatke;
- Web 2.0 => sadrzaj sajtova generisan od strane korisnika, umesto od strane organizacija (sajtovi nisu vise prezentacione prirode);
	- explosion of data - transactional data => human documents => social interactions => machine data (IoT);
- mainframe apps => database as integration hub => decoupled services (microservices apps);
- graf pada performansi aplikacija koje koriste RDBMS sa porastom kompleksnosti podataka koje koriste (salary list *good*, semantic trading *bad*);
- zahtevi Web aplikacija
	- veliki broj transakcija po jedinici vremena, 
	- dinamicka analiza velikih kolicina podataka,
	- kratko i predvidivo vreme odziva,
	- skalabilnost po niskoj ceni,
	- visok nivo dostupnosti,
	- fleksibilna sema,
	- geografska distribuiranost;
- Web aplikacijama nisu nepohodne
	- transakcije,
	- kompleksni SQL upiti,
	- stroga konzistentnost,
	- integritet podataka;

[[2. Web aplikacija i relacione baze podataka. Prednosti korišćenja I nedostaci.]]

## Skalabilnost

- ACID - manje, horizontalno skalabilne aplikacije;
- nedostaci RDBMSa - neskalabilnost ACID, dodatni overhed, nefleksibilnost seme;
- koncept ***skalabilnosti*** - nastavak normalnog funkcionisanja aplikacije pri dodavanju novih resursa (novi cvorovi, jaca procesorska snaga, memorija, link, ...)
	- ***scaling up*** - povecanje resursa _jednog racunara_ - automatsko skaliranje, skupo, ali brzo 'udara u plafon' i ***SPOF***;
	- terminologija - availability, downtime, high availability (5 nines, redundancy hw+sw, fault tolerance/detection, repair/recovery, automated&unattended);
		- redundancy - RPO, RTO;
	- ***scaling out*** - dodavanje novih node-ova - fleksibilno, ali kompleksno resenje;
		- horizontalna skalabilnost
		- vertikalna skalabilnost

## Distribuirane baze podataka

- Distribuirane baze podataka:
	- vise cvorova;
	- jedna baza;
	- fragmentacija;
	- replikacija;
	- skalabilnost;
	- performanse;
	- high availability;
	- otpornost na greske (fault tolerance);
	- ponasa se kao centralizovana baza;

[[3. Distribuirane baze podataka - pojam, skalabilnost i zahtevi koje moraju da zadovolje]]

- horizontalna i vertikalna fragmentacija;
- vertikalna (funkcionalna) - PROJECT i JOIN;
- horizontalna - RESTRICT (LIMIT, FILTER) i UNION;
- hibridna - vertikalna + horizontalna - cesto u mikroservisnim (DB per microservice) arhitekturama;
- najcesca je horizontalna skalabilnost;
- replikacija - azuriranje u vise nodova;
- sharen nothing arhitektura (+ share everything, share disks);
- dobre strane distribuiranih baza:
	- bolja kontrola;
	- bolje performanse;
	- povecana dostupnost;
	- lakse skaliranje;
- nedostaci
	- kompleksnost;
	- cena;
	- sigurnost;
	- otezana kontrola integriteta;

[[4. CAP torema, CAE trade-off, BASE, poređenje BASE i ACID.]]

- CAP - Consistency, Availability, Partition-tolerance;
- CAP theorem - prihvatljivo je zadovoljiti 2/3 zahteva (moze sva 3 ali je jako++ skupo);
	- CA sistemi - single site cluster resenja, 2PC commit;
	- CP sistemi - sharded databases resenja (horiz. part.);
	- AP sistemi - najcesce, DNS, kes, master/slave repl., eventualna konzistentnost;
- CAE trade-off
	- Cost-efficiency
	- High availability
	- Elasticity
- BASE 
	- Basically Available - sistem garantuje odgovor (moguce i nekonzistentan)
	- Soft state - stanje sistema se menja tokom vremena (cak i kad nema ulaznih podataka)
	- Eventually consistent - sistem konvergira ka konzistentnost
- ACID vs BASE - rigidnost vs fleksibilnost;

---
# References

- [Video 2](https://www.youtube.com/watch?v=y85XuURveyw&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=2);
- [Video 3](https://www.youtube.com/watch?v=QoutEJPi_VQ&list=PLWLPHZCdUNsM6typP_eWIviyyN14BCotR&index=3);

---
# Table of contents
```table-of-contents
```