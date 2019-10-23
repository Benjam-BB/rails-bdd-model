# README

This README would normally document whatever steps are necessary to get the
application up and running.

Réponses aux questions
========

## Questions faciles

   1. Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
   
```
Al_s = Album.all
   Al_s.size
 => 347 
 ```

   2. Qui est l'auteur de la chanson "White Room" ?

 ``` 
white_room = Track.find_by(title: "White Room")
white_room.artist
 => "Eric Clapton" 
```
   3. Quelle chanson dure exactement 188133 milliseconds ?
   
``` 
dur = Track.find_by(duration: 188133)
dur.title
 => "Perfect" 
 ```

   4. Quel groupe a sorti l'album "Use Your Illusion II" ?
   
``` 
albim = Album.find_by(title: "Use Your Illusion II")
albim.artist
 => "Guns N Roses"
 ```
 ## Questions Moyennes


   1. Combien y a t'il d'albums dont le titre contient "Great" ? (indice)

```
great = Album.where("title like ?", "%great%")
great.size
 => 13
 ```

   2. Supprime tous les albums dont le nom contient "music".

```
Album.where("title like ?", "%music%").destroy_all
```

3. Combien y a t'il d'albums écrits par AC/DC ?

```
acdc = Album.where(artist: "AC/DC")
acdc.count
 => 2
 ```

4. Combien de chanson durent exactement 158589 millisecondes ?

```
Track.where(duration: 158589).count
 => 0
 ```

## Questions Difficiles


   1. puts en console tous les titres de AC/DC.
   
```
allbum = Album.all
allbum.each do |album|
   if album.artist == "AC/DC"
      puts album.title
   end
end
=> For Those About To Rock We Salute You
 Let There Be Rock
 ```

2. puts en console tous les titres de l'album "Let There Be Rock".

```
Track.where(album: "Let There Be Rock").each do |album|
      puts album.title
 end
=>
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie
```

3. Calcule le prix total de cet album ainsi que sa durée totale.

``` 
Track.where(album: "Let There Be Rock").map {|c| c.price}.sum
 => 7.92
 ```

4. Calcule le coût de l'intégralité de la discographie de "Deep Purple".

```
Track.where(artist: "Deep Purple").map {|c| c.price}.sum
 => 90.09
 ```

5. Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
```
Track.where(artist: "Eric Clapton").map {|c| c.update(artist: "Britney Spears")}
```





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


