# AI-Law-Minicourse-HW
## Notes

### Step 1

Import all necessary packages from anaconda into the phyton kernel. 
The software is crawling on the Supreme Court ruling opinion repository, so a user-header is necessary to avoid being flagged as unwanted bot.

I'm not sure where the variable "root_url" is created, probably it's a global variable from an inmported package or python allows creation and assignemnt simultaniouly (without defining the variable). 	
Assign the URL of the repository of Supreme Court ruling opinons to that variable.

Next, the software creates a one-dimensional array "years" with the URLs of the years to explore.
The Methode "Beautiful_soup_grabber" pulls the data from a given website into a nested data structure.
The Methode "year_getter" then usese "beautiful_soup_grabber" and the array "years" in a loop to get the data for every document in the repository. The result is a data_frame table.

A new variable is then filled with the results from "year_getter".

The results are tested and converted afterwards.



### Step 2
It reads in the output from the previous step and splits it up to prevent caselaw from blocking your ip for "spaming")

The methode "supcourtdescr" collects case details from URLs with a loop.

All case details are added to the table.

Saves the result in a pickle file.


### Step 3
This step cleans the data from unnecessary or "harmful" words.

For this reasons, it loads a lot of lists with common stopwords, statenames, names,....
Then a list ("homespun_words") with all words that should be stopwords specific for this task is created.

All lists are then commbined to the list "STOPLIST".

The Method "tokenizeText" uses a loop to delete all stopwords. 

But I'm not sure where that method is used and what the the second last line is actually doing. Probably there is some source code missing.

In the end, the results are saved in a pickle file.


### Step 4
The method "modeler" runs a modell and then prints out the topwords with the methode "print_top_words" to show the results.
It tests the methods LDA, NMF and LSA and adjusts some features within.
NMF proofed to be the best fit for this task because it allows do differentiate different fields of law and not just "law" and "not law" like LSA.


### Step 5
1. The model is run against the entire dataframe to get the different topics.
2. The results are then used to create a document-score for each topic. It a product of two matrices, not a probability. But nontehless, the highest number means that it is most likely in this category.
3. The next step simply creates a dictonary to look up the top words for each topics.
4. This dictonary is used to look up these words in each item (=document)
5. The data is visualisied. For that reason, a few changes are necessary (reduce the number of topics, add dummy numbers,...). Finally, the number of cases for each topic and year is used to creat an impressive graphic.

### Fin!
