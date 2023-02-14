# CSE 15L Week 5 Lab Report by *Addy*

## 8 Examples of Using the `grep` Command
> `grep` is a command that takes in a string and file argument and searches through the file to find lines containing that string and returns the path and line containing the desired string.

---

## Example 1.1: Search through directories rather than files with `-r`
```
grep -r "motels" ./written_2
./written_2/non-fiction/OUP/Kauffman/ch1.txt:Similar phenomena may occur in an econosphere. Small and large avalanches of extinction and speciation events occur in our technologies. A colleague, Brian Arthur, is fond of pointing out that when the car came in, the horse, buggy, buggy whip, saddlery, smithy, and Pony Express went out of business. The car paved the way for an oil and gas industry, paved roads, motels, fast-food restaurants, and suburbia. The Austrian economist Joseph Schumpeter wrote about this kind of turbulence in capitalist economies. These Schumpeterian gales of creative destruction appear to occur in small and large avalanches. Perhaps the avalanches arise in power laws. And, like species, most firms die young; some make it to old age = Storre, in Sweden, is over nine hundred years old. The distribution of firm lifetimes is again a power law.
./written_2/non-fiction/OUP/Kauffman/ch9.txt:But the econosphere has similar extinction and speciation events. Consider my favorite example: The introduction of the automobile drove the horse, as a mode of transport, extinct. With the horse went the barn, the buggy, the stable, the smithy, the saddlery, the Pony Express. With the car came paved roads, an oil and gas industry, motels, fast-food restaurants, and suburbia. The Austrian economist, Joseph Schumpeter, called these gales of creative destruction, where old goods die and new ones are born. One bets that Schumpeterian gales of creative destruction come in a power law distribution, with many small avalanches and few large ones. More, if species and genera have a power law distribution of lifetimes, what of firms? Firms do show a similar power law distribution of lifetimes. Most firms die young, some last a long time. We may bet that technologies show similar avalanches of speciation and extinction events and lifetime distributions.
./written_2/travel_guides/berlitz1/HandRLasVegas.txt:        available hotels and motels, call the Las Vegas Convention and Visitors
./written_2/travel_guides/berlitz1/WhereToMalaysia.txt:        and other sports. (There are also small inns and motels in the region
./written_2/travel_guides/berlitz1/WhereToMalaysia.txt:        resort hotels and motels. If you are traveling there by road (rather
./written_2/travel_guides/berlitz1/HandRLosAngeles.txt:        except on executive floors and at some budget motels that offer morning
./written_2/travel_guides/berlitz2/California-WhereToGo.txt:Don’t be put off by the name Death Valley. It is a legacy of the bitter hardships endured by Gold Rush hopefuls who set out to cross the desert from Arizona and Nevada. Some never made it. Today’s travelers, however, are well catered to, with motels and campsites at Furnace Creek and Stovepipe Wells. Begin at the Furnace Creek Visitor Center, where you can pick up maps and information on the road conditions, hiking trails, and general desert safety. Driving is the only way to get around, but remember that distances are great and gasoline stations few and far between. Make sure your car is in good mechanical condition and that the tank is full before you begin each day’s tour. Also, you would be well advised to carry spare water, just in case the radiator boils over.
./written_2/travel_guides/berlitz2/Canada-WhereToGo.txt:The true marvel of Niagara is how nature manages to triumph over tawdry commercialism, perhaps less strident on the Canadian than on the American side of the border marked by the Falls. No amount of pushy peddlers or tacky pink honeymoon motels (if you do stay overnight, ask to see one of the hilarious bridal suites) can diminish the spectacle of that mass of white water taking its awesome plunge on the way from Lake Erie towards Lake Ontario and the Atlantic.
```
In the code above, I am using `grep`'s `--recursive` search option. `-r` allows the user to input a directory rather than a file, for which `grep` will search through the directory and its sub-folders files in order to find lines within files that match the desired string. Searching for `"motels"` returned for example, `./written_2/travel_guides/berlitz1/WhereToMalaysia.txt` along with the lines of text within that file containing the string `motels`. As you can see, the `-r` option is useful for searching through large directories without having to write a `grep` command for each text file. It can find instances of a `string` amongst many directories and files.

## Example 1.2
```
grep -r "scary" ./written_2/travel_guides
./written_2/travel_guides/berlitz1/WhereToHongKong.txt:        raised expressways. The scary traffic is a real experience — vehicles
```
In the code above, I've given the directory `./written_2/travel_guides` for `grep -r` to search through. `grep` searches through all the files contained within the `travel_guides` sub-directory and finds matching instances of the string `"scary"` within those files. The resulting output contained the given path along with the relative path to the file containing the string `"scary"`: `./written_2/travel_guides/berlitz1/WhereToHongKong.txt` along with the corresponding line of text: `raised expressways. The scary traffic is a real experience — vehicles`. With the `-r` option, I can search through any specified directory in order to find many instances of a string. Since `grep -r` doesn't stop searching through a file until the end, it will return all instances of the word within the same file similar to `CTRL-F` on a document app.

Source: I found the `-r` option from the `grep` general commands manual accessed by typing `man grep` into the terminal.

---

## Example 2.1: Find files containing a specific string and return their paths with `-l`
```
grep -l "parrot" ./written_2/travel_guides/berlitz2/*.txt
./written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
./written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt
./written_2/travel_guides/berlitz2/Bermuda-WhatToDo.txt
./written_2/travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
./written_2/travel_guides/berlitz2/Cancun-WhereToGo.txt
./written_2/travel_guides/berlitz2/Cuba-WhatToDo.txt
./written_2/travel_guides/berlitz2/Portugal-WhatToDo.txt
./written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt
./written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt
```
In the code above, I am using `grep`'s `--files-with-matches` (`-l`) option. The `-l` option returns only the file paths corresponding to instances of the desired string `"parrot"` being found within the `./written_2/travel_guides/berlitz2/*.txt` files. `-l` is useful if you only want the file paths containing a string, which can be less confusing since there won't be repetitive paths or a large chunk of text. `-l` only searches through a file until it finds the first instance of the string, meaning it won't return the same path multiple times.

## Example 2.2
```
grep -r -l "sunny" ./written_2
./written_2/travel_guides/berlitz1/HistoryJamaica.txt
./written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt
./written_2/travel_guides/berlitz1/IntroMadrid.txt
./written_2/travel_guides/berlitz1/IntroLosAngeles.txt
./written_2/travel_guides/berlitz1/WhereToItaly.txt
./written_2/travel_guides/berlitz1/WhereToJapan.txt
./written_2/travel_guides/berlitz1/WhereToEdinburgh.txt
./written_2/travel_guides/berlitz1/WhereToFrance.txt
./written_2/travel_guides/berlitz1/WhatToMallorca.txt
./written_2/travel_guides/berlitz1/IntroFWI.txt
./written_2/travel_guides/berlitz1/HandRIsrael.txt
./written_2/travel_guides/berlitz1/WhereToIbiza.txt
./written_2/travel_guides/berlitz1/WhereToLosAngeles.txt
./written_2/travel_guides/berlitz1/WhatToJamaica.txt
./written_2/travel_guides/berlitz1/WhereToHongKong.txt
./written_2/travel_guides/berlitz2/Amsterdam-WhereToGo.txt
./written_2/travel_guides/berlitz2/Amsterdam-WhatToDo.txt
./written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
./written_2/travel_guides/berlitz2/Boston-WhereToGo.txt
./written_2/travel_guides/berlitz2/California-WhereToGo.txt
./written_2/travel_guides/berlitz2/China-WhereToGo.txt
./written_2/travel_guides/berlitz2/Algarve-WhatToDo.txt
./written_2/travel_guides/berlitz2/CanaryIslands-WhereToGo.txt
./written_2/travel_guides/berlitz2/Algarve-WhereToGo.txt
./written_2/travel_guides/berlitz2/Nepal-WhatToDo.txt
./written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt

grep -r -l "sunny" ./written_2 | wc -l
      26
```
In the code above, I'm searching through the `./written_2` directory and its subfolders using `-r`. `-l` makes `grep` search through each file up until the point that it finds the first instance of the desired string `"sunny"` and returns the file path. When combined with the `wc` command, you can easily find the number of files that contain the string `sunny`. 

Source: I found the `-l` option from the `grep` general commands manual accessed by typing `man grep` into the terminal.

---

## Example 3.1: Ignore case-sensitivity with `-i`
```
grep -i "THIS" ./written_2/travel_guides/berlitz2/Athens-History.txt
The actual history of the city-state of Athens is just as fascinating as its mythology. From around 2000 b.c. wandering bands filtered into Greece from Asia Minor. Known as Achaeans, they were the first Greek-speaking people in the area, and over the centuries they built many imposing fortresses and developed the rich Mycenaean civilization, based in the Peloponnese. The citadel at Mycenae, seat of this most powerful of early Greek cultures, was erected to the south of Athens. Surrounded by a pair of precipitous ravines, the imposing walls of the citadel were some forty feet high and twenty feet thick, virtually impregnable.
The moving power behind this unrivaled time of greatness, which has come to be known as the Golden Age, was Pericles. This liberal-inclined aristocrat was, in effect, the supreme ruler of Athens and its empire for 30 years until his death in 429 b.c.
During all this, the Athenian political system allowed the average citizen a greater degree of participation in public life than ever before anywhere, and perhaps since. Of course, the number of citizens (free adult males) was small — probably not above 30,000 — while the population as a whole, including women, children, resident aliens, and slaves, might have been ten times as great.
As Athens prospered, intense economic and ideological rivalry developed with Athens’ ally during the Persian Wars, Sparta. In 431 b.c. the Peloponnesian War broke out between them resulting in 27 years of debilitating conflict, involving most of the Greek world. Yet literature and art continued to flourish in spite of the incessant fighting, and during this time Athens built two of the loveliest temples on the Acropolis, the Erechtheion and the temple to Athena Nike (see pages 34 and 35).
Yet culturally and intellectually Athens still remained unsurpassed through the fourth century b.c. Aristotle, one of the world’s greatest philosophers, held forth at his own school of the Lyceum; Menander wrote comic plays; Praxiteles sculpted scores of superb statues, including that of Hermes, one of the greatest Greek sculptures, now in the museum at Olympia. This age, in fact, had an even more lasting influence than that exerted by Athens during its great “Classical” fifth century. Rome and Byzantium looked to it for inspiration, as Europe did in the Medieval and Renaissance periods.
From the 12th to 14th centuries Athens found itself governed by a number of European nobles from Florence, Catalonia, and Burgundy. In 1456 Athens and Attica were taken by the Turks in their rampage across the disintegrating Byzantine Empire. The following four centuries of Ottoman rule are known as Greece’s darkest age. Athens was all but forgotten. Through this difficult period, only the Orthodox Church could provide the Greek people with any sense of identity and continuity. 
In 1967 a military dictatorship seized power in Greece. During the seven-year “reign of the colonels,” as the succeeding years are known, political parties were dissolved, the press was censored, and left-wing sympathizers were exiled, tortured, and imprisoned. In November 1973 a student protest at the Athens Polytechnic was brutally crushed. This action spelled the end of public tolerance of the regime, which collapsed eight months later when the junta attempted to overthrow the Cypriot president, Archbishop Makarios, provoking the Turkish invasion of Cyprus. Constantine Karamanlis, the former conservative premier, was recalled from exile in Paris to restore democracy. The reforms that followed brought the abolition of the monarchy, and a new constitution for a republican government was drawn up in 1975.
In the 1990s Athens was awarded the 2004 Olympic Games. This, and Greece’s agreement to join the Euro currency zone in 2002, has resulted in a great deal of infrastructure and economic development, which has not been without its problems. Traffic in the city is still in gridlock, stadium construction is behind schedule, and the Greek economy has yet to meet the requirements for monetary union, but government rhetoric is upbeat as both deadlines approach. The history of Athens reflects the ingenuity and vigor of the Greek spirit that will, no doubt, meet whatever challenges the modern world has in store for it.
```
In the code above, I used the `--ignore-case` option `-i` in order to search for all instances of the string `"THE"` within the file path `./written_2/travel_guides/berlitz2/Athens-History.txt` regardless of whether it is capitalized or not. By default, `grep` is case-sensitive, meaning it searches EXACTLY for the string you input. `-i` is useful since a word like `the` is commonly used at the start of a sentence and in the middle of a sentence. You can find all of the instances of `the` within a file.

## Example 3.2
```
grep -r -l -i "GIGANTIC" ./written_2
./written_2/travel_guides/berlitz1/HistoryJapan.txt
./written_2/travel_guides/berlitz1/HistoryIndia.txt
./written_2/travel_guides/berlitz1/WhereToIndia.txt
./written_2/travel_guides/berlitz1/WhereToItaly.txt
./written_2/travel_guides/berlitz1/WhereToMalaysia.txt
./written_2/travel_guides/berlitz1/WhereToJapan.txt
./written_2/travel_guides/berlitz1/WhereToIsrael.txt
./written_2/travel_guides/berlitz1/WhereToFrance.txt
./written_2/travel_guides/berlitz1/WhereToLosAngeles.txt
./written_2/travel_guides/berlitz1/WhereToHongKong.txt
./written_2/travel_guides/berlitz2/Berlin-WhereToGo.txt
./written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
./written_2/travel_guides/berlitz2/California-WhereToGo.txt
./written_2/travel_guides/berlitz2/Bahamas-WhereToGo.txt
./written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
./written_2/travel_guides/berlitz2/Paris-WhereToGo.txt
./written_2/travel_guides/berlitz2/China-WhereToGo.txt
./written_2/travel_guides/berlitz2/CstaBlanca-WhereToGo.txt
./written_2/travel_guides/berlitz2/CanaryIslands-WhereToGo.txt

grep -r -l -i "GIGANTIC" ./written_2 | wc -l
      19
```
In the code above, I used the `-r`, `-l`, and `-i` option in order to find all file paths containing the string `"GIGANTIC"` regardless of case-sensitivity within all files in the `./written_2` directory. `-r` made `grep` search through all the directories and sub-directories, then `-l` in conjunction with `-i` searched only for the first instance of `"GIGANTIC"` in any capitalized form within all the files and returned the respective file paths. When used in conjunction with other options, `-i` can help find all the instances of a string regardless of case-sensitivity. With `wc -l`, you can easily find the number of files that contain the word `"GIGANTIC"` disregarding case-sensitivity.

Source: I found the `-i` option from the `grep` general commands manual accessed by typing `man grep` into the terminal.

---

## Example 4.1 - Return the exact desired word from a file with `-o`
```
grep -o "the" ./written_2/travel_guides/berlitz1/HandRLasVegas.txt
the
the
the
the
the
the
the
the
the
```
In the code above, I used the `--only-matching` option, `-o`, which makes `grep` only return the matching string within the file. As shown, the txt file `HandRLasVegas.txt` contained 9 instances of the string `"the"`. `-o` is useful for counting the number of times a string appears in a file when used with the `wc` command.

## Example 4.2
```
grep -r -i -o "PALM TREE" ./written_2
./written_2/travel_guides/berlitz1/WhereToGreek.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToGreek.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToIndia.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToIndia.txt:palm tree
./written_2/travel_guides/berlitz1/IntroLosAngeles.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToItaly.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToItaly.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToItaly.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToItaly.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToJapan.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToJapan.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToJapan.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToFrance.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToFrance.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToMallorca.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToMallorca.txt:palm tree
./written_2/travel_guides/berlitz1/IntroFWI.txt:palm tree
./written_2/travel_guides/berlitz1/IntroIndia.txt:palm tree
./written_2/travel_guides/berlitz1/WhatToJamaica.txt:palm tree
./written_2/travel_guides/berlitz1/WhatToJamaica.txt:palm tree
./written_2/travel_guides/berlitz1/WhatToJamaica.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToHongKong.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToFWI.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToFWI.txt:palm tree
./written_2/travel_guides/berlitz1/WhereToFWI.txt:palm tree
./written_2/travel_guides/berlitz2/Costa-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/California-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/California-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Bali-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Bali-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Bali-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Bali-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Bali-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Barcelona-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Barcelona-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/China-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/CstaBlanca-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/PuertoRico-WhereToGo.txt:palm tree
./written_2/travel_guides/berlitz2/Vallarta-WhereToGo.txt:palm tree

grep -r -i -o "PALM TREE" ./written_2 | wc -l
      39
```
In the code above, I used `-r`, `-i`, and `-o`. `-r` made `grep` search through all the files found in `./written_2` and its sub-directories, then `i` and `o` found all instances of `"palm tree"` (ignoring case-sensitivity) within the files. Since `-o` returns one line with the path and string for each instance of `"palm tree"`, I can use `wc -l` to get the number of times `"palm tree"` was written across all the files. `-o` is also useful for finding what files contain a desired string without returning a confusing block of before and after text.

Source: I was trying to figure out how to remove the large amount of before and after text and stumbled upon this [StackoverFlow Link](https://stackoverflow.com/questions/1546711/can-grep-show-only-words-that-match-search-pattern) about the `-o` option. I also used `man grep` to learn more about the option.
