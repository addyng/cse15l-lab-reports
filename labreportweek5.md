# CSE 15L Week 5 Lab Report by *Addy*

## 8 Examples of Using the `grep` Command
> `grep` is a command that takes in a string and file argument and searches through the file to find lines containing that string and returns the path and line containing the desired string.

## Example 1.1: Search through directories rather than files with `-r`
```
grep -r "Lucayans" written_2/ > grep-results.txt
cat grep-results.txt
written_2//travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2//travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```
In the code above, I am using `grep`'s recursive search option. `-r` allows the user to input a directory rather than a file, for which `grep` will search through the directory and its sub-folders files in order to find lines within files that match the desired string. Searching for `"Lucayans"` returned `written_2//travel_guides/berlitz2/Bahamas-History.txt` along with the lines of text within that file containing the string `Lucayans`. As you can see, the `-r` option is useful for searching through large directories without having to write a `grep` command for each text file. It can find instances of a `string` amongst many directories and files.

## Example 1.2
```
grep -r "scary" written_2/travel_guides > grep-results.txt
cat grep-results.txt
written_2/travel_guides/berlitz1/WhereToHongKong.txt:        raised expressways. The scary traffic is a real experience — vehicles
```
In the code above, I've given the directory `written_2/travel_guides` for `grep -r` to search through. `grep` searches through all the files contained within the `travel_guides` sub-directory and finds matching instances of the string `"scary"` within those files. The resulting output contained the given path along with the relative path to the file containing the string `"scary"`: `written_2/travel_guides/berlitz1/WhereToHongKong.txt:` along with the corresponding line of text: `raised expressways. The scary traffic is a real experience — vehicles`. With the `-r` option, I can search through any specified directory in order to find many instances of a string. Since `grep -r` doesn't stop searching through a file until the end, it will return all instances of the word within the same file similar to `CTRL-F` on a document app.

Source: I found the `-r` option from the `grep` general commands manual accessed by typing `man grep` into the terminal.

---

## Example 2.1: Find files containing a specific string and return their respective paths with `-l`
```
grep -r -l "parrot" written_2/ > grep-results.txt
cat grep-results.txt 
written_2//non-fiction/OUP/Berk/ch2.txt
written_2//travel_guides/berlitz1/WhatToFWI.txt
written_2//travel_guides/berlitz1/WhatToMallorca.txt
written_2//travel_guides/berlitz1/WhereToMadeira.txt
written_2//travel_guides/berlitz1/HistoryFWI.txt
written_2//travel_guides/berlitz1/IntroJapan.txt
written_2//travel_guides/berlitz2/Berlin-WhereToGo.txt
written_2//travel_guides/berlitz2/Cuba-WhatToDo.txt
written_2//travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2//travel_guides/berlitz2/Bermuda-WhatToDo.txt
written_2//travel_guides/berlitz2/Portugal-WhatToDo.txt
written_2//travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2//travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
written_2//travel_guides/berlitz2/Vallarta-WhereToGo.txt
written_2//travel_guides/berlitz2/Cancun-WhereToGo.txt
```
In the code above, I am using `grep`'s recursive search (-r) and files-with-matches (-l) option. In conjunction with `-r`, the `-l` option returns only the file path corresponding to instances of the desired string `"parrot"` being found within the `written_2/` directory. `-l` is useful if you only want the file paths containing a string, which can be less confusing since there won't be repetitive paths or a large chunk of text. `-l` only searches through a file until it finds the first instance of the string, meaning it won't return the same path multiple times.

## Example 2.2
```
grep -r -l "sunny" written_2/ > grep-results.txt
cat grep-results.txt
written_2//travel_guides/berlitz1/HistoryJamaica.txt
written_2//travel_guides/berlitz1/WhereToLakeDistrict.txt
written_2//travel_guides/berlitz1/IntroMadrid.txt
written_2//travel_guides/berlitz1/IntroLosAngeles.txt
written_2//travel_guides/berlitz1/WhereToItaly.txt
written_2//travel_guides/berlitz1/WhereToJapan.txt
written_2//travel_guides/berlitz1/WhereToEdinburgh.txt
written_2//travel_guides/berlitz1/WhereToFrance.txt
written_2//travel_guides/berlitz1/WhatToMallorca.txt
written_2//travel_guides/berlitz1/IntroFWI.txt
written_2//travel_guides/berlitz1/HandRIsrael.txt
written_2//travel_guides/berlitz1/WhereToIbiza.txt
written_2//travel_guides/berlitz1/WhereToLosAngeles.txt
written_2//travel_guides/berlitz1/WhatToJamaica.txt
written_2//travel_guides/berlitz1/WhereToHongKong.txt
written_2//travel_guides/berlitz2/Amsterdam-WhereToGo.txt
written_2//travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2//travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2//travel_guides/berlitz2/Boston-WhereToGo.txt
written_2//travel_guides/berlitz2/California-WhereToGo.txt
written_2//travel_guides/berlitz2/China-WhereToGo.txt
written_2//travel_guides/berlitz2/Algarve-WhatToDo.txt
written_2//travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
written_2//travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2//travel_guides/berlitz2/Nepal-WhatToDo.txt
written_2//travel_guides/berlitz2/Vallarta-WhereToGo.txt

wc -l grep-results.txt
      26 grep-results.txt
```
In the code above, I'm searching through the `written_2/` directory and its subfolders using `-r`. `-l` makes `grep` search through each file up until the point that it finds the first instance of the desired string `"sunny"` and prints the corresponding file path into `grep-results.txt`. When combined with the `wc` command, you can easily find the number of files that contain the string `sunny`. 

Source: I found the `-l` option from the `grep` general commands manual accessed by typing `man grep` into the terminal.

---

## Example 3.1: Ignore case-sensitivity with `-i`
```
grep -i "THIS" written_2/travel_guides/berlitz2/Athens-History.txt > grep-results.txt
cat grep-results.txt
The actual history of the city-state of Athens is just as fascinating as its mythology. From around 2000 b.c. wandering bands filtered into Greece from Asia Minor. Known as Achaeans, they were the first Greek-speaking people in the area, and over the centuries they built many imposing fortresses and developed the rich Mycenaean civilization, based in the Peloponnese. The citadel at Mycenae, seat of this most powerful of early Greek cultures, was erected to the south of Athens. Surrounded by a pair of precipitous ravines, the imposing walls of the citadel were some forty feet high and twenty feet thick, virtually impregnable.
The moving power behind this unrivaled time of greatness, which has come to be known as the Golden Age, was Pericles. This liberal-inclined aristocrat was, in effect, the supreme ruler of Athens and its empire for 30 years until his death in 429 b.c.
During all this, the Athenian political system allowed the average citizen a greater degree of participation in public life than ever before anywhere, and perhaps since. Of course, the number of citizens (free adult males) was small — probably not above 30,000 — while the population as a whole, including women, children, resident aliens, and slaves, might have been ten times as great.
As Athens prospered, intense economic and ideological rivalry developed with Athens’ ally during the Persian Wars, Sparta. In 431 b.c. the Peloponnesian War broke out between them resulting in 27 years of debilitating conflict, involving most of the Greek world. Yet literature and art continued to flourish in spite of the incessant fighting, and during this time Athens built two of the loveliest temples on the Acropolis, the Erechtheion and the temple to Athena Nike (see pages 34 and 35).
Yet culturally and intellectually Athens still remained unsurpassed through the fourth century b.c. Aristotle, one of the world’s greatest philosophers, held forth at his own school of the Lyceum; Menander wrote comic plays; Praxiteles sculpted scores of superb statues, including that of Hermes, one of the greatest Greek sculptures, now in the museum at Olympia. This age, in fact, had an even more lasting influence than that exerted by Athens during its great “Classical” fifth century. Rome and Byzantium looked to it for inspiration, as Europe did in the Medieval and Renaissance periods.
From the 12th to 14th centuries Athens found itself governed by a number of European nobles from Florence, Catalonia, and Burgundy. In 1456 Athens and Attica were taken by the Turks in their rampage across the disintegrating Byzantine Empire. The following four centuries of Ottoman rule are known as Greece’s darkest age. Athens was all but forgotten. Through this difficult period, only the Orthodox Church could provide the Greek people with any sense of identity and continuity. 
In 1967 a military dictatorship seized power in Greece. During the seven-year “reign of the colonels,” as the succeeding years are known, political parties were dissolved, the press was censored, and left-wing sympathizers were exiled, tortured, and imprisoned. In November 1973 a student protest at the Athens Polytechnic was brutally crushed. This action spelled the end of public tolerance of the regime, which collapsed eight months later when the junta attempted to overthrow the Cypriot president, Archbishop Makarios, provoking the Turkish invasion of Cyprus. Constantine Karamanlis, the former conservative premier, was recalled from exile in Paris to restore democracy. The reforms that followed brought the abolition of the monarchy, and a new constitution for a republican government was drawn up in 1975.
In the 1990s Athens was awarded the 2004 Olympic Games. This, and Greece’s agreement to join the Euro currency zone in 2002, has resulted in a great deal of infrastructure and economic development, which has not been without its problems. Traffic in the city is still in gridlock, stadium construction is behind schedule, and the Greek economy has yet to meet the requirements for monetary union, but government rhetoric is upbeat as both deadlines approach. The history of Athens reflects the ingenuity and vigor of the Greek spirit that will, no doubt, meet whatever challenges the modern world has in store for it.
```
In the code above, I used the --ignore-case option `-i` in order to search for all instances of the string `"THE"` within the file path `written_2/travel_guides/berlitz2/Athens-History.txt` regardless of whether it is capitalized or not. By default, `grep` is case-sensitive, meaning it searches EXACTLY for the string you input. `-i` is useful since a word like `the` is commonly used at the start of a sentence and in the middle of a sentence. You can find all of the instances of `the` within a file.

## Example 3.2
```
grep -r -l -i "THE" written_2/
written_2//non-fiction/OUP/Berk/ch2.txt
written_2//non-fiction/OUP/Berk/ch1.txt
written_2//non-fiction/OUP/Berk/CH4.txt
written_2//non-fiction/OUP/Berk/ch7.txt
written_2//non-fiction/OUP/Abernathy/ch2.txt
written_2//non-fiction/OUP/Abernathy/ch3.txt
written_2//non-fiction/OUP/Abernathy/ch1.txt
written_2//non-fiction/OUP/Abernathy/ch7.txt
written_2//non-fiction/OUP/Abernathy/ch6.txt
written_2//non-fiction/OUP/Abernathy/ch8.txt
written_2//non-fiction/OUP/Abernathy/ch9.txt
written_2//non-fiction/OUP/Abernathy/ch15.txt
written_2//non-fiction/OUP/Abernathy/ch14.txt
written_2//non-fiction/OUP/Rybczynski/ch2.txt
written_2//non-fiction/OUP/Rybczynski/ch3.txt
written_2//non-fiction/OUP/Rybczynski/ch1.txt
written_2//non-fiction/OUP/Kauffman/ch3.txt
written_2//non-fiction/OUP/Kauffman/ch1.txt
written_2//non-fiction/OUP/Kauffman/ch4.txt
written_2//non-fiction/OUP/Kauffman/ch5.txt
written_2//non-fiction/OUP/Kauffman/ch7.txt
written_2//non-fiction/OUP/Kauffman/ch6.txt
written_2//non-fiction/OUP/Kauffman/ch8.txt
written_2//non-fiction/OUP/Kauffman/ch9.txt
written_2//non-fiction/OUP/Kauffman/ch10.txt
written_2//non-fiction/OUP/Fletcher/ch2.txt
written_2//non-fiction/OUP/Fletcher/ch1.txt
written_2//non-fiction/OUP/Fletcher/ch5.txt
written_2//non-fiction/OUP/Fletcher/ch6.txt
written_2//non-fiction/OUP/Fletcher/ch9.txt
written_2//non-fiction/OUP/Fletcher/ch10.txt
written_2//non-fiction/OUP/Castro/chR.txt
written_2//non-fiction/OUP/Castro/chP.txt
written_2//non-fiction/OUP/Castro/chQ.txt
written_2//non-fiction/OUP/Castro/chB.txt
written_2//non-fiction/OUP/Castro/chC.txt
written_2//non-fiction/OUP/Castro/chA.txt
written_2//non-fiction/OUP/Castro/chV.txt
written_2//non-fiction/OUP/Castro/chW.txt
written_2//non-fiction/OUP/Castro/chM.txt
written_2//non-fiction/OUP/Castro/chZ.txt
written_2//non-fiction/OUP/Castro/chL.txt
written_2//non-fiction/OUP/Castro/chN.txt
written_2//non-fiction/OUP/Castro/chY.txt
written_2//non-fiction/OUP/Castro/chO.txt
written_2//travel_guides/berlitz1/HandRLasVegas.txt
written_2//travel_guides/berlitz1/HistoryJapan.txt
written_2//travel_guides/berlitz1/IntroMalaysia.txt
written_2//travel_guides/berlitz1/HandRIstanbul.txt
written_2//travel_guides/berlitz1/HistoryJamaica.txt
written_2//travel_guides/berlitz1/HandRJamaica.txt
written_2//travel_guides/berlitz1/HandRHongKong.txt
written_2//travel_guides/berlitz1/HistoryEgypt.txt
written_2//travel_guides/berlitz1/IntroEdinburgh.txt
written_2//travel_guides/berlitz1/HistoryIsrael.txt
written_2//travel_guides/berlitz1/IntroDublin.txt
written_2//travel_guides/berlitz1/HistoryIndia.txt
written_2//travel_guides/berlitz1/IntroFrance.txt
written_2//travel_guides/berlitz1/IntroMadeira.txt
written_2//travel_guides/berlitz1/WhatToLakeDistrict.txt
written_2//travel_guides/berlitz1/IntroIbiza.txt
written_2//travel_guides/berlitz1/HistoryItaly.txt
written_2//travel_guides/berlitz1/WhereToGreek.txt
written_2//travel_guides/berlitz1/WhereToLakeDistrict.txt
written_2//travel_guides/berlitz1/HistoryDublin.txt
written_2//travel_guides/berlitz1/IntroIsrael.txt
written_2//travel_guides/berlitz1/WhatToIbiza.txt
written_2//travel_guides/berlitz1/HistoryFrance.txt
written_2//travel_guides/berlitz1/WhatToHawaii.txt
written_2//travel_guides/berlitz1/HistoryMallorca.txt
written_2//travel_guides/berlitz1/HistoryJerusalem.txt
written_2//travel_guides/berlitz1/HandRLisbon.txt
written_2//travel_guides/berlitz1/WhereToIndia.txt
written_2//travel_guides/berlitz1/HistoryMadrid.txt
written_2//travel_guides/berlitz1/HistoryHongKong.txt
written_2//travel_guides/berlitz1/IntroMadrid.txt
written_2//travel_guides/berlitz1/IntroLosAngeles.txt
written_2//travel_guides/berlitz1/HistoryIstanbul.txt
written_2//travel_guides/berlitz1/WhereToItaly.txt
written_2//travel_guides/berlitz1/HistoryLasVegas.txt
written_2//travel_guides/berlitz1/HistoryGreek.txt
written_2//travel_guides/berlitz1/HandRMallorca.txt
written_2//travel_guides/berlitz1/JungleMalaysia.txt
written_2//travel_guides/berlitz1/WhatToMadeira.txt
written_2//travel_guides/berlitz1/WhatToFWI.txt
written_2//travel_guides/berlitz1/WhereToMalaysia.txt
written_2//travel_guides/berlitz1/WhatToMalaysia.txt
written_2//travel_guides/berlitz1/WhatToDublin.txt
written_2//travel_guides/berlitz1/WhereToJapan.txt
written_2//travel_guides/berlitz1/HistoryHawaii.txt
written_2//travel_guides/berlitz1/WhatToFrance.txt
written_2//travel_guides/berlitz1/WhereToEgypt.txt
written_2//travel_guides/berlitz1/WhereToEdinburgh.txt
written_2//travel_guides/berlitz1/WhatToIsrael.txt
written_2//travel_guides/berlitz1/HandRLosAngeles.txt
written_2//travel_guides/berlitz1/HistoryMadeira.txt
written_2//travel_guides/berlitz1/IntroJerusalem.txt
written_2//travel_guides/berlitz1/HandRMadeira.txt
written_2//travel_guides/berlitz1/WhereToIsrael.txt
written_2//travel_guides/berlitz1/HandRIbiza.txt
written_2//travel_guides/berlitz1/WhereToFrance.txt
written_2//travel_guides/berlitz1/WhereToDublin.txt
written_2//travel_guides/berlitz1/IntroLasVegas.txt
written_2//travel_guides/berlitz1/IntroIstanbul.txt
written_2//travel_guides/berlitz1/WhereToMallorca.txt
written_2//travel_guides/berlitz1/WhatToMallorca.txt
written_2//travel_guides/berlitz1/IntroHongKong.txt
written_2//travel_guides/berlitz1/IntroFWI.txt
written_2//travel_guides/berlitz1/IntroJamaica.txt
written_2//travel_guides/berlitz1/IntroGreek.txt
written_2//travel_guides/berlitz1/HandRIsrael.txt
written_2//travel_guides/berlitz1/WhatToEdinburgh.txt
written_2//travel_guides/berlitz1/WhereToMadeira.txt
written_2//travel_guides/berlitz1/WhatToGreek.txt
written_2//travel_guides/berlitz1/HandRLakeDistrict.txt
written_2//travel_guides/berlitz1/WhereToIbiza.txt
written_2//travel_guides/berlitz1/WhereToHawaii.txt
written_2//travel_guides/berlitz1/HandRMadrid.txt
written_2//travel_guides/berlitz1/HistoryMalaysia.txt
written_2//travel_guides/berlitz1/IntroItaly.txt
written_2//travel_guides/berlitz1/WhatToIndia.txt
written_2//travel_guides/berlitz1/WhereToLosAngeles.txt
written_2//travel_guides/berlitz1/HandRJerusalem.txt
written_2//travel_guides/berlitz1/HistoryIbiza.txt
written_2//travel_guides/berlitz1/HistoryEdinburgh.txt
written_2//travel_guides/berlitz1/HistoryFWI.txt
written_2//travel_guides/berlitz1/IntroIndia.txt
written_2//travel_guides/berlitz1/WhatToItaly.txt
written_2//travel_guides/berlitz1/HistoryLakeDistrict.txt
written_2//travel_guides/berlitz1/WhereToMadrid.txt
written_2//travel_guides/berlitz1/WhereToJerusalem.txt
written_2//travel_guides/berlitz1/IntroEgypt.txt
written_2//travel_guides/berlitz1/HandRHawaii.txt
written_2//travel_guides/berlitz1/WhatToJapan.txt
written_2//travel_guides/berlitz1/WhatToJamaica.txt
written_2//travel_guides/berlitz1/IntroLakeDistrict.txt
written_2//travel_guides/berlitz1/IntroMallorca.txt
written_2//travel_guides/berlitz1/WhatToHongKong.txt
written_2//travel_guides/berlitz1/WhatToEgypt.txt
written_2//travel_guides/berlitz1/WhereToHongKong.txt
written_2//travel_guides/berlitz1/WhereToFWI.txt
written_2//travel_guides/berlitz1/WhatToIstanbul.txt
written_2//travel_guides/berlitz1/WhereToIstanbul.txt
written_2//travel_guides/berlitz1/IntroJapan.txt
written_2//travel_guides/berlitz1/WhatToLasVegas.txt
written_2//travel_guides/berlitz1/WhatToLosAngeles.txt
written_2//travel_guides/berlitz2/Portugal-History.txt
written_2//travel_guides/berlitz2/Berlin-WhereToGo.txt
written_2//travel_guides/berlitz2/Costa-History.txt
written_2//travel_guides/berlitz2/Amsterdam-WhereToGo.txt
written_2//travel_guides/berlitz2/Costa-WhereToGo.txt
written_2//travel_guides/berlitz2/Amsterdam-WhatToDo.txt
written_2//travel_guides/berlitz2/CostaBlanca-WhatToDo.txt
written_2//travel_guides/berlitz2/Barcelona-History.txt
written_2//travel_guides/berlitz2/Portugal-WhereToGo.txt
written_2//travel_guides/berlitz2/Boston-WhereToGo.txt
written_2//travel_guides/berlitz2/Poland-WhatToDo.txt
written_2//travel_guides/berlitz2/California-WhereToGo.txt
written_2//travel_guides/berlitz2/Cuba-WhatToDo.txt
written_2//travel_guides/berlitz2/Berlin-History.txt
written_2//travel_guides/berlitz2/Bahamas-WhereToGo.txt
written_2//travel_guides/berlitz2/Cancun-WhatToDo.txt
written_2//travel_guides/berlitz2/Bali-History.txt
written_2//travel_guides/berlitz2/Crete-WhereToGo.txt
written_2//travel_guides/berlitz2/Athens-History.txt
written_2//travel_guides/berlitz2/Berlin-WhatToDo.txt
written_2//travel_guides/berlitz2/Canada-WhereToGo.txt
written_2//travel_guides/berlitz2/Bali-WhereToGo.txt
written_2//travel_guides/berlitz2/Budapest-WhereoGo.txt
written_2//travel_guides/berlitz2/Barcelona-WhereToGo.txt
written_2//travel_guides/berlitz2/Athens-WhereToGo.txt
written_2//travel_guides/berlitz2/Paris-WhereToGo.txt
written_2//travel_guides/berlitz2/China-WhereToGo.txt
written_2//travel_guides/berlitz2/Bermuda-WhatToDo.txt
written_2//travel_guides/berlitz2/California-History.txt
written_2//travel_guides/berlitz2/Vallarta-History.txt
written_2//travel_guides/berlitz2/Budapest-WhatToDo.txt
written_2//travel_guides/berlitz2/Cancun-History.txt
written_2//travel_guides/berlitz2/PuertoRico-WhatToDo.txt
written_2//travel_guides/berlitz2/Vallarta-WhatToDo.txt
written_2//travel_guides/berlitz2/Bali-WhatToDo.txt
written_2//travel_guides/berlitz2/CostaBlanca-History.txt
written_2//travel_guides/berlitz2/CstaBlanca-WhereToGo.txt
written_2//travel_guides/berlitz2/NewOrleans-History.txt
written_2//travel_guides/berlitz2/PuertoRico-History.txt
written_2//travel_guides/berlitz2/Algarve-Intro.txt
written_2//travel_guides/berlitz2/Nepal-History.txt
written_2//travel_guides/berlitz2/China-History.txt
written_2//travel_guides/berlitz2/Canada-History.txt
written_2//travel_guides/berlitz2/Crete-History.txt
written_2//travel_guides/berlitz2/Portugal-WhatToDo.txt
written_2//travel_guides/berlitz2/Bahamas-Intro.txt
written_2//travel_guides/berlitz2/Amsterdam-History.txt
written_2//travel_guides/berlitz2/Bahamas-WhatToDo.txt
written_2//travel_guides/berlitz2/Barcelona-WhatToDo.txt
written_2//travel_guides/berlitz2/Algarve-WhatToDo.txt
written_2//travel_guides/berlitz2/PuertoRico-WhereToGo.txt
written_2//travel_guides/berlitz2/Cuba-WhereToGo.txt
written_2//travel_guides/berlitz2/Costa-WhatToDo.txt
written_2//travel_guides/berlitz2/Beijing-History.txt
written_2//travel_guides/berlitz2/Nepal-WhereToGo.txt
written_2//travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
written_2//travel_guides/berlitz2/Bermuda-history.txt
written_2//travel_guides/berlitz2/CanaryIslands-History.txt
written_2//travel_guides/berlitz2/Amsterdam-Intro.txt
written_2//travel_guides/berlitz2/Crete-WhatToDo.txt
written_2//travel_guides/berlitz2/Algarve-WhereToGo.txt
written_2//travel_guides/berlitz2/Athens-Intro.txt
written_2//travel_guides/berlitz2/Algarve-History.txt
written_2//travel_guides/berlitz2/Poland-History.txt
written_2//travel_guides/berlitz2/Beijing-WhereToGo.txt
written_2//travel_guides/berlitz2/CanaryIslands-WhatToDo.txt
written_2//travel_guides/berlitz2/California-WhatToDo.txt
written_2//travel_guides/berlitz2/Budapest-History.txt
written_2//travel_guides/berlitz2/China-WhatToDo.txt
written_2//travel_guides/berlitz2/Athens-WhatToDo.txt
written_2//travel_guides/berlitz2/Nepal-WhatToDo.txt
written_2//travel_guides/berlitz2/Bermuda-WhereToGo.txt
written_2//travel_guides/berlitz2/Paris-WhatToDo.txt
written_2//travel_guides/berlitz2/Cuba-History.txt
written_2//travel_guides/berlitz2/Vallarta-WhereToGo.txt
written_2//travel_guides/berlitz2/Bahamas-History.txt
written_2//travel_guides/berlitz2/Beijing-WhatToDo.txt
written_2//travel_guides/berlitz2/Cancun-WhereToGo.txt
```
In the code above, I used the `-r`, `-l`, and `-i` option in order to find all file paths containing the string `"THE"` regardless of case-sensivitiy within all files in the `written_2` directory. `-r` made `grep` search through all the directories and sub-directories, then `l` in conjunction with `-i` searched only for the first instance of `"THE"` in any capitalized form within all the files and returned the respective file paths. When used in conjunction with other options, `-i` can help find all the instances of a string regardless of case-sensitivity.

Source: I found the `-i` option from the `grep` general commands manual accessed by typing `man grep` into the terminal.

## Example 4.1 - Using -o https://stackoverflow.com/questions/1546711/can-grep-show-only-words-that-match-search-pattern to only return the word
