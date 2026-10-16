# SQL-inlämning — Diskografi

**Namn:** [Ditt namn]  
**Artist:** [Din valda artist]  
**Datum:** [Datum]

---

> Lägg länk till eller bild på ditt ER-diagram här: https://dbdiagram.io/e/6ad0cde0aebfe7a21ffc360b/6ad24407fe5cc8bda2db3ada
> `[ER-diagram](er_diagram.png)`

---

## 1. Skapa databasen — CREATE TABLE

CREATE TABLE Artist (
    Name TEXT,
    Artist_ID TEXT PRIMARY KEY,
    Birth_year INTEGER,
    City TEXT,
    Genre TEXT,
    Number_of_Albums INTEGER
);

CREATE TABLE Albums (
    Artist_ID TEXT,
    Album_name TEXT,
    Album_ID INTEGER PRIMARY KEY,
    Year INTEGER,
    Sales_Millions INTEGER,
    Runtime_Minutes INTEGER,
    FOREIGN KEY (Artist_ID)
        REFERENCES Artist(Artist_ID)
);

CREATE TABLE Songs (
    Song_Title TEXT PRIMARY KEY,
    Album_ID INTEGER,
    Length_Seconds INTEGER,
    FOREIGN KEY (Album_ID)
        REFERENCES Albums(Album_ID)
);

---

## 2. Seeda med data — INSERT

INSERT INTO Artist (Name, Artist_ID, Birth_year, City, Genre, Number_of_Albums) 
VALUES 
    ('Michael Jackson', 'MJ', 1958, 'Indiana', 'POP', 10);

INSERT INTO Albums
    (Artist_ID, Album_name, Album_ID, Year, Sales_Millions, Runtime_Minutes)
	
VALUES
    ('MJ', 'Off the Wall', 1, 1979, 20, 42),
    ('MJ', 'Thriller', 2, 1982, 70, 42),
    ('MJ', 'Bad', 3, 1987, 35, 48),
    ('MJ', 'Dangerous', 4, 1991, 32, 77),
    ('MJ', 'HIStory', 5, 1995, 20, 148);

 INSERT INTO Songs (Song_Title, Album_ID, Length_Seconds)
VALUES  
	('Heal the World', 4, 383),
	('Earth Song', 5, 423),
	('Thriller', 2, 358),
    ('Beat It', 2, 258),
	('Dont Stop Til You Get Enough', 1, 356),
	('Bad', 3, 247),
	('Scream', 5, 276),
	('You Are Not Alone', 5, 353),
	('Black or White', 4, 205),
    ('Remember the Time', 4, 239),
	('Baby Be Mine', 2, 260),
    ('The Girl Is Mine', 2, 222),
	('Off the Wall', 1, 244),
	('Rock with You', 1, 220),
	('Wanna Be Startin Somethin', 2, 362),
	('The Way You Make Me Feel', 3, 298),
    ('Man in the Mirror', 3, 319);



---

## 3. Söka — SELECT

```sql
--- query 1: Lista alla album, sorterade efter år ---

SELECT * FROM Albums ORDER BY Year

--- query 2: Lista alla låtar på ett specifikt album ---

SELECT * FROM Songs WHERE Album_ID  = '3'

--- query 3: Antal låtar per album ---

SELECT Album_ID, COUNT(*) AS Song_Count
FROM Songs
GROUP BY Album_ID;

--- query 4: Längsta låten ---

SELECT* FROM Songs ORDER BY Length_Seconds DESC LIMIT 1

--- query 5: Alla låtar sorterade alfabetiskt ---

SELECT* FROM SONGS ORDER BY Song_Title


## 4. Lägg till en ny rad — INSERT

```sql
--- lägg till ett nytt album eller en ny låt ---

```

---

## 5. Ta bort en rad — DELETE

```sql
--- ta bort en rad ur valfri tabell ---

```

---

## 6. Uppdatera en rad — UPDATE

```sql
--- uppdatera minst en rad i valfri tabell ---



## 7. VG-queries (om du siktar på VG)

```sql
--- query 6: Snittlängd på låtar per album ---

SELECT Album_ID, AVG(Length_Seconds) AS Average_Length
FROM Songs
GROUP BY Album_ID;

--- query 7: Albumet med flest låtar ---

SELECT Album_ID, COUNT(*) AS Song_Count
FROM Songs
GROUP BY Album_ID 
ORDER BY Song_Count DESC LIMIT 1;

--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---

SELECT Songs.*, Albums.Album_name
FROM Songs
JOIN Albums ON Songs.Album_ID = Albums.Album_ID
WHERE Songs.Length_Seconds > 240;

```
