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
On Dry Land
Spectator Sports
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

```
$ grep -c -v "the" written_2/travel_guides/berlitz2/Bali-WhatToDo.txt
```

