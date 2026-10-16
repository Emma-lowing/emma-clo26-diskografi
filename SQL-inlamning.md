# SQL-inlämning — Diskografi

**Namn:** [Ditt namn]  
**Artist:** [Din valda artist]  
**Datum:** [Datum]

---

> Lägg länk till eller bild på ditt ER-diagram här:
> `[ER-diagram](er_diagram.png)`

---

## 1. Skapa databasen — CREATE TABLE

```sql
--- skriv din SQL-kod här ---
CREATE TABLE Artists (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

CREATE TABLE Albums (
id INTEGER PRIMARY KEY,
title TEXT NOT NULL,
release_year INTEGER,
artist_id INTEGER NOT NULL,
FOREIGN KEY (artist_id) REFERENCES Artists(id)
);

CREATE TABLE Songs (
    id INTEGER PRIMARY KEY,
    title TEXT NOT NULL,
    duration_seconds INTEGER,
    album_id INTEGER NOT NULL,
    FOREIGN KEY (album_id) REFERENCES Albums(id)
);


CREATE TABLE Genres (
id INTEGER PRIMARY KEY,
name TEXT NOT NULL
);


CREATE TABLE SongGenres (
    song_id INTEGER NOT NULL,
    genre_id INTEGER NOT NULL,
    PRIMARY KEY (song_id, genre_id),
    FOREIGN KEY (song_id) REFERENCES Songs(id),
    FOREIGN KEY (genre_id) REFERENCES Genres(id)
);
```

---

## 2. Seeda med data — INSERT

```sql
--- skriv din SQL-kod här ---
INSERT INTO Artists (name)
VALUES ('Taylor Swift');


INSERT INTO Albums (title, release_year, artist_id)
VALUES ('Fearless', 2008, 1);

INSERT INTO Albums (title, release_year, artist_id)
VALUES ('Red', 2012, 1);

INSERT INTO Albums (title, release_year, artist_id)
VALUES ('1989', 2014, 1);

INSERT INTO Albums (title, release_year, artist_id)
VALUES ('folklore', 2020, 1);

INSERT INTO Albums (title, release_year, artist_id)
VALUES ('Midnights', 2022, 1);

--Skrivet manuellt.
INSERT INTO Songs (title, duration_seconds, album_id)
VALUES
('Fearless', 241, 1),
('Fifteen', 294, 1),
('Love Story', 235, 1),
('Hey Stephen', 254, 1),
('White Horse', 234, 1),
('You Belong With Me', 231, 1),
('Breathe (feat. Colbie Caillat)', 263, 1),
('Tell Me Why', 200, 1),
('You''re Not Sorry', 261, 1),
('The Way I Loved You', 244, 1),
('Forever & Always', 225, 1),
('The Best Day', 245, 1),
('Change', 280, 1);

INSERT INTO Songs (title, duration_seconds, album_id)
VALUES
('State of Grace', 295, 2),
('Red', 223, 2),
('Treacherous', 242, 2),
('I Knew You Were Trouble', 219, 2),
('All To Well', 329, 2),
('22', 232, 2),
('I Almost Do', 244, 2),
('We Are Never Ever Getting Back Together', 193, 2),
('Stay Stay Stay', 205, 2),
('The Last Time (feat. Gary Lightbody)', 299, 2),
('Holy Ground', 202, 2),
('Sad Beautiful Tragic', 284, 2),
('The Lucky One', 240, 2),
('Everything Has Changed (feat. Ed Sheeran)', 245, 2),
('Starlight', 220, 2),
('Begin Again', 237, 2);

--Ai hjälp för att effektivisera.
INSERT INTO Songs (title, duration_seconds, album_id)
VALUES
('Welcome to New York', 212, 3),
('Blank Space', 231, 3),
('Style', 230, 3),
('Out of the Woods', 235, 3),
('All You Had to Do Was Stay', 193, 3),
('Shake It Off', 219, 3),
('I Wish You Would', 207, 3),
('Bad Blood', 211, 3),
('Wildest Dreams', 220, 3),
('How You Get the Girl', 247, 3),
('This Love', 250, 3),
('I Know Places', 195, 3),
('Clean', 270, 3);

INSERT INTO Songs (title, duration_seconds, album_id)
VALUES
('the 1', 210, 4),
('cardigan', 239, 4),
('the last great american dynasty', 231, 4),
('exile (feat. Bon Iver)', 285, 4),
('my tears ricochet', 255, 4),
('mirrorball', 209, 4),
('seven', 208, 4),
('august', 261, 4),
('this is me trying', 195, 4),
('illicit affairs', 190, 4),
('invisible string', 252, 4),
('mad woman', 237, 4),
('epiphany', 289, 4),
('betty', 294, 4),
('peace', 234, 4),
('hoax', 220, 4);

INSERT INTO Songs (title, duration_seconds, album_id)
VALUES
('Lavender Haze', 202, 5),
('Maroon', 218, 5),
('Anti-Hero', 200, 5),
('Snow on the Beach (feat. Lana Del Rey)', 256, 5),
('You''re on Your Own, Kid', 194, 5),
('Midnight Rain', 174, 5),
('Question...?', 210, 5),
('Vigilante Shit', 164, 5),
('Bejeweled', 194, 5),
('Labyrinth', 247, 5),
('Karma', 204, 5),
('Sweet Nothing', 188, 5),
('Mastermind', 191, 5);

INSERT INTO Genres (name)
VALUES
('Pop'),
('Country'),
('Folk'),
('Alternative');

--Skrivet manuellt.
INSERT INTO SongGenres (song_id, genre_id)
VALUES
(1, 1),
(1, 2),
(2, 2),
(3, 1),
(3, 2),

(14, 1),
(15, 1),
(15, 2),
(16, 1),
(16, 2),

(30, 1),
(31, 1),
(32, 1),

(43, 3),
(43, 4),
(44, 3),
(44, 4),
(45, 3),
(45, 4),

(59, 1),
(60, 1),
(60, 4),
(61, 1);

--Ai hjälp för att effektivisera.
INSERT INTO SongGenres (song_id, genre_id)
VALUES
(4, 2),
(4, 1),
(5, 2),
(6, 2),
(6, 1),
(7, 2),
(7, 1),
(8, 2),
(9, 2),
(9, 1),
(10, 2),
(10, 1),
(11, 2),
(11, 1),
(12, 2),
(13, 2),
(13, 1);

INSERT INTO SongGenres (song_id, genre_id)
VALUES
(17, 1),
(18, 2),
(18, 1),
(19, 1),
(20, 2),
(21, 1),
(22, 2),
(22, 1),
(23, 4),
(23, 1),
(24, 1),
(25, 2),
(25, 3),
(26, 2),
(26, 1),
(27, 1),
(27, 3),
(28, 1),
(29, 2);

INSERT INTO SongGenres (song_id, genre_id)
VALUES
(33, 1),
(34, 1),
(35, 1),
(36, 1),
(37, 1),
(38, 1),
(39, 1),
(40, 1),
(40, 4),
(41, 1),
(42, 1),
(42, 4);

INSERT INTO SongGenres (song_id, genre_id)
VALUES
(46, 3),
(46, 4),
(47, 4),
(48, 4),
(48, 1),
(49, 3),
(49, 4),
(50, 4),
(50, 1),
(51, 4),
(52, 3),
(52, 4),
(53, 3),
(54, 3),
(54, 4),
(55, 4),
(56, 3),
(56, 2),
(57, 3),
(57, 4),
(58, 3),
(58, 4);

INSERT INTO SongGenres (song_id, genre_id)
VALUES
(62, 1),
(62, 4),
(63, 1),
(63, 4),
(64, 1),
(64, 4),
(65, 1),
(66, 1),
(66, 4),
(67, 1),
(68, 1),
(68, 4),
(69, 1),
(70, 1),
(71, 1);




```

---

## 3. Söka — SELECT

```sql
--- query 1: Lista alla album, sorterade efter år ---
SELECT title, release_year
FROM Albums
ORDER BY release_year ASC;

--- query 2: Lista alla låtar på ett specifikt album ---
SELECT title
FROM Songs
WHERE album_id = 5;

--- query 3: Antal låtar per album ---
SELECT ALbums.title, COUNT(Songs.title) AS number_of_songs
FROM Albums
JOIN Songs
ON Albums.id = Songs.album_id
GROUP BY Albums.id, Albums.title;

--- query 4: Längsta låten ---
SELECT title, duration_seconds
FROM Songs
ORDER BY duration_seconds DESC
LIMIT 1;

--- query 5: Alla låtar sorterade alfabetiskt ---
SELECT title
FROM Songs
ORDER BY title ASC;
```

---

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
UPDATE Songs
SET title = 'All Too Well'
WHERE id = 18;

```

---

## 7. VG-queries (om du siktar på VG)

```sql
--- query 6: Snittlängd på låtar per album ---
SELECT Albums.title, ROUND(AVG(duration_seconds), 2) AS average_song_length_in_seconds
FROM Albums
JOIN Songs
ON Albums.id = Songs.album_id
GROUP BY Albums.id, Albums.title;

--- query 7: Albumet med flest låtar ---
WITH AlbumCounts AS(
SELECT Albums.title, COUNT(Songs.id) AS number_of_songs
FROM Albums
JOIN Songs
ON Albums.id = Songs.album_id
GROUP BY Albums.id, Albums.title
) 
SELECT title, number_of_songs
FROM AlbumCounts
WHERE number_of_songs = (
    SELECT MAX(number_of_songs)
    FROM AlbumCounts
);

--- query 8: Alla låtar längre än 4 minuter (240 sekunder), med albumtitel ---
SELECT Songs.title, duration_seconds, Albums.title
FROM Songs
JOIN Albums
ON Albums.id = Songs.album_id
WHERE duration_seconds > 240
ORDER BY duration_seconds DESC;
--Jag valde att lägga till "ORDER BY duration_seconds DESC" för att det ska se snyggare ut
```
