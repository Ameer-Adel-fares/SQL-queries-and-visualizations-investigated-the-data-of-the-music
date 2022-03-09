# SQL-queries-and-visualizations-investigated-the-data-of-the-music
In this project, I queried the Chinook Database
The Chinook Database holds information about a music store. 


/* Query 1 : How many Track in each of the 18 playlist we have ? */
SELECT a.PlaylistId,
       count(b.PlaylistId) track_per_playlist
FROM Playlist a
JOIN PlaylistTrack b ON a.PlaylistId = b.PlaylistId
GROUP BY 1
ORDER BY 2 DESC


/* Query 2 : How many track Per each Genre? */
SELECT a.Name,
       count(b.TrackId) NO_of_track_per_genre
FROM Genre a
JOIN Track b ON a.GenreId = b.GenreId
GROUP BY 1
ORDER BY 2 DESC


/* Query 3: How many track per each Media type */
SELECT a.Name,
       count(b.TrackId) NO_of_track_per_media_type
FROM MediaType a
JOIN Track b ON a.MediaTypeId = b.MediaTypeId
GROUP BY 1
ORDER BY 2 DESC





/* Query 4: Query about  top 10 bands and there song contribution */
SELECT c.ArtistId,
       c.Name,
       count(TrackId) songs,
       d.Name
FROM Track a
JOIN Album b ON a.AlbumId = b.AlbumId
JOIN Artist C ON b.ArtistId = c.ArtistId
JOIN Genre d ON a.GenreId = d.GenreId
WHERE d.Name = 'Rock'
GROUP BY 1
ORDER BY 3 DESC
LIMIT 10
