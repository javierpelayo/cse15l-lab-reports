# Lab Report 3

## -v, --invert-match flag

`grep -v *pattern* *file*`

Adding the -v flag will pick the lines that dont include the provided string in the line.

Example 1:

```
$ grep -v "the" written_2/travel_guides/berlitz2/Bali-WhatToDo.txt > grep-not-the.txt
$ cat grep-not-the.txt

What to Do
Sports
Watersports
On Dry Land Spectator Sports
Entertainment
Traditional Music, Puppetry, and Dance Performances
Dances of Bali
Festivals and Events
Shopping
Bali FORCHILDREN
```

This finds every line that does not contain the string "the" whether like " the " or "these", either way it excludes these lines and gives the inverse of the lines containing those strings. This is useful if you want to filter out lines that contain certain keywords, making it easier to narrow down to other lines if you're not sure what it is exactly that you're looking for.

Example 2:

```
$ grep -v "Bahama" written_2/travel_guides/berlitz2/Bali-WhatToDo.txt > grep-not-bahama.txt
$ cat grep-not-bahama.txt

Some of the islands are only a few hundred square meters in size, but together they make up an area of 5,380 sq miles (14,000 sq km), slightly smaller than the area of the Hawaiian Islands. Only 100 of the islands are inhabited; many of these have become private playgrounds for the rich and super-rich. Even fewer — 37 to be exact — have settlements or towns. This leaves many hundreds of cays that are totally natural, untouched by the destructive influence of humans and offering pristine habitats to hundreds of bird and animal species.

The warning on Spanish maps unfortunately did little to stop ships from running aground or foundering on the treacherous shoals; even today treasure lost centuries ago is still being discovered and salvaged.
On the smaller and more remote islands — called the Out Islands or Family Islands — intimate resorts cater to your every need and make it possible for you to forget about schedules, deadlines, and traffic jams. The most difficult decision you’ll have to make is what to pick from the extensive dinner menu. While the clubs and casinos may not play on into the night, during the day you’ll be worn out by walks along the beach and other strenuous activities, such as collecting sea shells, enjoying long lunches, and applying sunblock. The whole trip could prove to be exhausting!

This not only provides excitement for divers, who can watch shark feeding in the wild on some Bahamian islands, but also to fishermen. The vast numbers of large fish species, including record breaking marlin and bonefish, make for some of the most challenging and thrilling sport-fishing in the world.

The Bahamian people are among the friendliest you’ll ever meet, and they are eager to share the homeland they love with visitors. The population is a fascinating mixture of descendants of the Loyalist settlers who left America after the American Revolution, freedom lovers who escaped religious persecution, and ex-slaves set free following emancipation. This mixture, which could have produced a society fraught with problems, has evolved into a gentle, sociable, and happy people, proud of their homeland and the progress they have made since independence in 1973. With a stable economy, good health, and no taxes, it’s no wonder that a smile comes naturally to all Bahamians. All the communities still have strong religious faith, the pretty churches are full on Sundays, and a conversation about some future event always ends with “…God willing” or “…with the Lord’s blessing.”

```

This outputs all the lines in the file that don't contain the keyword "Bahama", we could simply change the string to just "Bah" and maybe even add an `-i` flag to ignore the case to filter out even more information containing anything specifically containing Bahamas as a keyword.

## -c, --count flag

`grep -c *pattern* *file*`

This will count the number of lines where the pattern occurs.

Example 1:

```
$ grep -c "the" written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
$ 42
```

This counts the number of lines that contain the pattern, in this case "the" occurred in 42 lines in the file Bali-WhatToDo.txt

Example 2:

```
$ grep -c "where" written_2/travel_guides/berlitz1/WhatToIndia.txt
$ 5
```

In this case, the pattern match for "where" only occurred in 5 lines in the file WhatToIndia.txt

## -C NUM, --context=num

`grep -C NUM *pattern* *file*`

This command will give print a NUM of lines before and a NUM of lines after the line that is found with the matching pattern.

This helps us give context to where the matching pattern is situated within a file if we need to look at some lines before or after.

Example 1:

```
$ grep -C 2 "tolerant" written_2/travel_guides/berlitz2/CostaBlanca-History.txt
Moorish Domination
In a.d. 711, the Arab chief Tariq landed at Gibraltar with 12,000 Berber troops. Thus began an 800-year epoch of Christian opposition to the newly arrived Muslims. The Moors—the name commonly given to all Muslims in Spain—carried all before them. Within ten years their green-crescent standard flew over most of Spain. Kartajanah, Mursiyah, and Xativa are still known by their Moorish names.
The Moors were relatively tolerant rulers who taxed non-believers rather than trying to convert them. They introduced the manufacture of paper, which is carried on today in Játiva. They laid out a system of irrigation still in use in the Guadalest Valley and filled the huertas (orchards) of the Costa Blanca with oranges, peaches, and pomegranates. Rice, cotton, and sugar cane were also first cultivated on Spanish soil by the Moors.
Numerous Moorish fortifications on the Costa Blanca survive to this day, and the pottery of the region still reflects the influence of Moorish craftsmen. Learning was considerably advanced by the Moors, and a medical treatise written by an Arab physician in Crevillente is recognized today as revolutionary for its time.
The Tide Turns
```

Notice that we have 5 lines, where the third line is the line that has the matching pattern and so we have two lines before it and two lines after it, giving us context.

Example 2:

```
$ grep -C 5 "bailar al cuartel" written_2/non-fiction/OUP/Castro/chA.txt
y hasta el mismo coronel la respetaba.
Y se oía que decía aquel que tanto la quería. . . .
Y si Adelita fuera mi novia,
y si Adelita fuera mi mujer,
le compraría un vestido de seda
para llevarla a bailar al cuartel.
Y si Adelita se fuera con otro
la seguiría por tierra y por mar
si por mar en un buque de guerra
si por tierra en un tren militar.
(On the loftiest of the sierras
```

In this example we are given five lines of context before and after the line that matches the pattern provided.

## -l, --files-with-matches

`grep -l *pattern* *files*`

This command will print the file name that contains the matching pattern, especially useful when searching multiple files

Example 1:

```
$ grep -l "Lucayans" written_2/*/*/*.txt
written_2/travel_guides/berlitz/Bahamas-History.txt
```

Notice that we searched all txt files that reside in written_2 and its subdirectories and we only found one such file that contains the pattern.

Example 2:

```
$ grep -l "mathematics" written_2/*/*/*.txt
written_2/travel_guides/berlitz1/WhereToFrance.txt
written_2/travel_guides/berlitz1/WhereToIstanbul.txt
written_2/travel_guides/berlitz2/Beijing-History.txt
written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
written_2/travel_guides/berlitz2/China-History.txt
```

In this case only five files contains the pattern provided.

All of these flags were found using the "man" command which gives us a manual for specific commands.










