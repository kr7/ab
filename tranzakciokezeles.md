# Tranzakciókezelés

Tekintsük az alábbi kódot, amelyben egyik számláról a másikra történő átutalást végzünk:

```
create table szamlak 
  ( szamlaszam decimal(10),
    egyenleg decimal(8,2),
    primary key (ugyfelkod) );
    

insert into szamlak values
(1, 100), (2, 200);


select * from szamlak;

start transaction;

update szamlak set egyenleg = egyenleg-50 
where szamlaszam = '1';

update szamlak set egyenleg = egyenleg+50 
where szamlaszam = '2';

commit;
```

Mi történik, ha az első update után kilépünk a MySQL kliensből és újraindítjuk a gépet? Milyen állapotban találjuk az adatbázist az újraindítás után?
