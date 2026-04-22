# Tárolt függvények

## E-mail cím ellenőrzése

Azt ellenőrizzük, hogy ".com" domain-beli e-mail címről van-e szó:

```
CREATE DEFINER=`hallgato`@`%` FUNCTION `chk_email`(s varchar(200)) RETURNS tinyint(1)
    DETERMINISTIC
BEGIN
	return s like '_%@_%.com'; 
END
```

## Szám leírása betűvel

```
CREATE DEFINER=`hallgato`@`%` FUNCTION `betuvel1`(szam int) RETURNS varchar(200) CHARSET utf8mb4 COLLATE utf8mb4_general_ci
BEGIN
	if szam = 0 then
		return 'nulla';
	end if;
    if szam = 1 then 
		return 'egy';
	end if;
    if szam = 2 then
		return 'ketto';
	end if;
    if szam = 3 then
		return 'harom';
	end if;
    if szam = 4 then 
		return 'negy';
	end if;
    if szam = 5 then
		return 'ot';
	end if;
    if szam = 6 then 
		return 'hat';
	end if;
    if szam = 7 then
		return 'het';
	end if;
    if szam = 8 then
		return 'nyolc';
	end if;
    if szam = 9 then 
		return 'kilenc';
	end if;
    return 'hiba';
END
```

```
CREATE DEFINER=`hallgato`@`%` FUNCTION `betuvel2`(szam int) RETURNS varchar(200) CHARSET utf8mb4 COLLATE utf8mb4_general_ci
    DETERMINISTIC
BEGIN
	if szam < 10 then 
		return betuvel1(szam);
	end if;
	if szam = 10 then 
		return "tiz";
	end if;
    if szam > 10 and szam < 20 then
		return concat("tizen", betuvel1(szam%10));
	end if;
    if szam = 20 then
		return "husz";
	end if;
    if szam > 20 and szam < 30 then
		return concat("huszon", betuvel1(szam%10));
	end if;
    if szam = 30 then 
		return 'harminc';
	end if;
    if szam > 30 and szam < 40 then 
		return concat('harmic', betuvel1(szam%10));
	end if;
	if szam = 40 then 
		return 'negyven';
	end if;
    if szam > 40 and szam < 50 then 
		return concat('negyven', betuvel1(szam%10));
	end if;
	if szam = 50 then 
		return 'otven';
	end if;
    if szam > 50 and szam < 60 then 
		return concat('otven', betuvel1(szam%10));
	end if;
	if szam = 60 then 
		return 'hatvan';
	end if;
    if szam > 60 and szam < 70 then 
		return concat('hatvan', betuvel1(szam%10));
	end if;
	if szam = 70 then 
		return 'hetven';
	end if;
    if szam > 70 and szam < 80 then 
		return concat('hetven', betuvel1(szam%10));
	end if;
    if szam = 80 then 
		return 'nyolcvan';
	end if;
    if szam > 80 and szam < 90 then 
		return concat('nyolcvan', betuvel1(szam%10));
	end if;
	if szam = 90 then 
		return 'kilencven';
	end if;
    if szam > 90 and szam < 100 then 
		return concat('kilencven', betuvel1(szam%10));
	end if;
    return 'hiba';
END
```

```
CREATE DEFINER=`hallgato`@`%` FUNCTION `betuvel3`(szam int) RETURNS varchar(200) CHARSET utf8mb4 COLLATE utf8mb4_general_ci
    DETERMINISTIC
BEGIN
	if szam < 100 then 
		return betuvel2(szam);
	end if;
	if szam % 100 = 0 then 
		return concat(betuvel1(floor(szam/100)),'szaz');
	else
		return concat(betuvel1(floor(szam/100)),'szaz', 
               betuvel2(szam % 100));
	end if;
    return "hiba";
END
```

```
CREATE DEFINER=`hallgato`@`%` FUNCTION `betuvel4`(szam int) RETURNS varchar(200) CHARSET utf8mb4 COLLATE utf8mb4_general_ci
    DETERMINISTIC
BEGIN
	if szam < 1000 or szam > 9999 then
		return 'hiba';
	end if;
	if szam % 1000 = 0 then 
		return concat(betuvel1(floor(szam/1000)),'ezer');
	else
		if szam > 2000 then 
			return concat(betuvel1(floor(szam / 1000)), 
			'ezer-', betuvel3(szam % 1000));
		else 
        	return concat(betuvel1(floor(szam / 1000)), 
			'ezer', betuvel3(szam % 1000));
		end if;
	end if;
END
```

```
CREATE DEFINER=`hallgato`@`%` FUNCTION `betuvel`(szam int) RETURNS varchar(200) CHARSET utf8mb4 COLLATE utf8mb4_general_ci
    DETERMINISTIC
BEGIN
	if szam >=0 and szam < 10 then 
		return betuvel1(szam);
	end if;
	if szam >=10 and szam < 100 then 
		return betuvel2(szam);
	end if;
	if szam >=100 and szam < 1000 then 
		return betuvel3(szam);
	end if;
	if szam >=1000 and szam < 10000 then 
		return betuvel4(szam);
	end if;
    return 'hiba';
END
```
