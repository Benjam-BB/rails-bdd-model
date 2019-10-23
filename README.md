# README

This README would normally document whatever steps are necessary to get the
application up and running.

Réponses aux questions
========

## Questions faciles

   1. Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?

Al_s = Album.all
 Al_s.size
   (0.3ms)  SELECT COUNT(*) FROM "albums"
 => 347

   2. Qui est l'auteur de la chanson "White Room" ?

2.5.1 :009 > white_room = Track.find_by(title: "White Room")
2.5.1 :010 > white_room.artist
 => "Eric Clapton"

   3. Quelle chanson dure exactement 188133 milliseconds ?
2.5.1 :011 > dur = Track.find_by(duration: 188133)
2.5.1 :012 > dur.title
 => "Perfect"

   4. Quel groupe a sorti l'album "Use Your Illusion II" ?
2.5.1 :001 > albim = Album.find_by(title: "Use Your Illusion II")
2.5.1 :002 > albim.artist
 => "Guns N Roses"

 ## Questions Moyennes


   1. Combien y a t'il d'albums dont le titre contient "Great" ? (indice)

2.5.1 :007 > great = Album.where("title like ?", "%great%")
2.5.1 :009 > great.size
   (0.5ms)  SELECT COUNT(*) FROM "albums" WHERE (title like '%great%')
 => 13

   2. Supprime tous les albums dont le nom contient "music".

Album.where("title like ?", "%music%").destroy_all

3. Combien y a t'il d'albums écrits par AC/DC ?
acdc = Album.where(artist: "AC/DC")
2.5.1 :018 > acdc.count
   (0.4ms)  SELECT COUNT(*) FROM "albums" WHERE "albums"."artist" = ?  [["artist", "AC/DC"]]
 => 2

4. Combien de chanson durent exactement 158589 millisecondes ?

    2.5.1 :020 > Track.where(duration: 158589).count
   (0.3ms)  SELECT COUNT(*) FROM "tracks" WHERE "tracks"."duration" = ?  [["duration", 158589]]
 => 0

## Questions Difficiles


   1. puts en console tous les titres de AC/DC.
allbum = Album.all

    2.5.1 :007 > allbum.each do |album|
2.5.1 :008 >     if album.artist == "AC/DC"
2.5.1 :009?>     puts album.title
2.5.1 :010?>     end
2.5.1 :011?>   end
  Album Load (2.7ms)  SELECT "albums".* FROM "albums"
For Those About To Rock We Salute You
Let There Be Rock

2. puts en console tous les titres de l'album "Let There Be Rock".

2.5.1 :018 > Track.where(album: "Let There Be Rock").each do |album|
2.5.1 :019 >     puts album.title
2.5.1 :020?>   end
  Track Load (0.3ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."album" = ?  [["album", "Let There Be Rock"]]
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie

3. Calcule le prix total de cet album ainsi que sa durée totale.

2.5.1 :014 > Track.where(album: "Let There Be Rock").map {|c| c.price}.sum
  Track Load (0.3ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."album" = ?  [["album", "Let There Be Rock"]]
 => 7.92

4. Calcule le coût de l'intégralité de la discographie de "Deep Purple".

2.5.1 :015 > Track.where(artist: "Deep Purple").map {|c| c.price}.sum
  Track Load (2.3ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."artist" = ?  [["artist", "Deep Purple"]]
 => 90.09

5. Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
Track.where(artist: "Eric Clapton").map {|c| c.update(artist: "Britney Spears")}





Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


