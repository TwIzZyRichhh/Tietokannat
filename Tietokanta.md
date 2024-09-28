Kuulemma viikko 1 tehtäviä ei tarvinnut pistää tänne, mutta ne ovat kaikki tehty
Viikko 2

1.Tee kysely, joka tulostaa kaikki sarakkeet goal-talusta.
select * from goal



2.Tee kysely, joka tulostaa nimen ja tyypin kaikista Suomessa sijaitsevista lentokentistä. Suomen maatunnus on: FI
select name airport_type from airport where iso_country = "FI"

3.Tee kysely, joka tulostaa suomalaisten lentokenttien nimet aakkosjärjestyksessä. Suomen maatunnus: FI
select name from airport where iso_country = "FI" order by name;

4.Tee kysely, joka tulostaa nimen ja tyypin kaikista Suomessa sijaitsevista lentokentistä. Järjestä tulos ensisijaisesti tyypin mukaan ja toissijaisesti nimen mukaan.
select name, type from airport where iso_country = "FI" order by type, name;

5.Tee kysely, joka tulostaa kaikki F-kirjaimella alkavat maan nimet country-taulusta.
select name from country where name like "F%";

6.Tee kysely, joka tulostaa kaikki country-taulun maiden nimet, joissa esiintyy F-kirjain.
select name from country where name like "%F%";

7.Missä locationissa Vesa sijaitsee?
select location from game where screen_name ="Vesa"

8.Kuinkan paljon Ilkka on kuluttanut CO2 budjettia?
select co2_consumed from game where screen_name="Ilkka";

9.Kuinka paljon alkuperäinen CO2 budjetti on (tulosta CO2 budjetin arvo vain kerran)?
select distinct co2_budget from game;

Where osan teht
1.Tee kysely, joka listaa maan nimen ja lentokentän nimen. Valitse maaksi Islanti ja anna country-taulun name-kentälle alias ”country name” ja airport taulun name-kentälle alias ”airport name”.
select country.name as "country name", airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "Iceland";

2.Listaa Ranskan isojen lentokenttien nimet. Anna kentän nimelle alias "airport name".
select airport.name as "airport name"
from airport, country
where airport.iso_country = country.iso_country and country.name = "France" and airport.type = "large_airport";

3.Tee kysely, joka listaa kaikki Antarktiksella sijaitsevien lentokenttien nimet ja vastaava maan nimi. 

Käytä aliaksia country_name ja airport_name. SQLLite ei salli kahdesta sanasta koostuvaa aliasta. MariaDB sallii jos aliaksen ympärillä on lainausmerkit.

select country.name as country_name, airport.name as airport_name
from airport, country
where airport.iso_country = country.iso_country and country.continent = "AN";

4.Kuinka korkealla Heini on paraikaa merenpinnasta mitattuna?
select elevation_ft
from airport, game
where location = ident and screen_name = "Heini";

5.Kuinka korkealla Heini on paraikaa merenpinnasta mitattuna? Anna tulos metreissä, ja anna tulokselle alias elevation_m. Yksi jalka on 0,3048 metriä. Älä käytä muuttujaa. Voit kuitenkin tehdä laskutoimituksen ilman muuttujaa.
select elevation_ft * 0.3048 as elevation_m
from airport, game
where location = ident and screen_name = "Heini";

6.Minkä nimisellä lentokentällä Ilkka on?
select name
from airport, game
where location = ident and screen_name = "Ilkka";

7.Minkä nimisessä maassa Ilkka on?
select country.name
from airport, game, country
where location = ident and airport.iso_country = country.iso_country  and screen_name = "Ilkka";

8.Minkä nimiset säätila-tavoitteet Heini on saavuttanut?
select name
from goal, goal_reached, game
where game.id = game_id and goal.id = goal_id and screen_name = "Heini";

9.Minkä nimisellä lentokentällä Ilkka saavutti säätilan clouds?
select airport.name
from airport, game, goal, goal_reached
where ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";

10.Minkä nimisessä maassa Ilkka saavutti säätilan clouds?
select country.name
from country, airport, game, goal, goal_reached
where airport.iso_country = country.iso_country and ident = location and game.id = game_id and goal.id = goal_id and screen_name = "Ilkka" and goal.name = "CLOUDS";

Viikko 3
