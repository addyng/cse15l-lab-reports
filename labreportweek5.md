# CSE 15L Week 5 Lab Report by *Addy*

## 8 Examples of Using the `grep` Command
> `grep` is a command that takes in a string and file argument and searches through the file to find lines containing that string and returns the path and line containing the desired string.

## Example 1.1: Finding the respective lines within text files containing a specific string
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

## Example 2.1: Finding files containing a specific string and returning their respective paths
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

