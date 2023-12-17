For this analysis, we first search Scopus for all publications associated with the Laboratory Phonology Journal (SOURCE-ID ( 19700200915)[1]. This search returned 152 publications between 2015 and 2023.

We then search the text of the abstracts of each publication for mention of the names of languages and the countries of affiliation for each author. The code for this search is in the ExtractLangs.ipynb notebook.

In this notebook, we used a regular expression [2] to extract all sequences of words which begin with capital letters, (e.g. “Santo Domingo Spanish”) and manually reduced this list to a list of languages. This list is in the Jupyter Notebook in the raw_langs list. We searched for all tokens which begin with non- symbols or accented Latin symbols to ensure languages such as !Kung and ǂʼAmkoe were not excluded, and found no languages among these tokens. For each publication, we save the title, author list, countries of author affiliations, and languages found in the abstract into the LabPhon_extract.csv file.

We then categorize the languages studied and countries of affiliations by region; Global North and Global South. We use the UNCTAD definition of a “developed country” for the Global North, and “developing country” for the Global South [3]. We classified languages according to the region in which the variety is spoken, for example, Andalusian Spanish was classified as a Global North language, while Venezuelan Spanish was classified as a Global South language. We classified the indigenous languages of the Global North (e.g. Greek Thrace Romani, Māori, Warlpiri and other Australian indigenous languages) as languages of the Global South, while the majority language varieties of the same region (Greek, New Zealand English, Australian English) were classified as languages of the Global North. Since the authors of publications often have affiliations in multiple countries, and that publications often study multiple languages, we classified affiliations and languages studied as follows 1) exclusively from the Global North, and 2) at least one from the Global South. We performed these classifications manually, and saved our results in the LabPhon_extract_labelled.csv file.

We compare the results from our analysis with population and higher education statistics. We calculated population from the Global North and South using [4], and we used [5] for statistics on higher education by country. We performed our calculations for population and higher education in the PopulationAndUniStats.xlsx file.

From our data set, we counted the occurrences of each country to create a world map in R showing the representation for each country. The counts were calculated in the ExtractLangs.ipynb notebook. The R code to plot the map is available in the file world_map.Rmd, and the output of this this file is available at world_map.pdf. 


[1] https://www.scopus.com/results/results.uri?sort=plf-f&src=s&sid=91e517f77e75028d715ae9a95341f258&sot=a&sdt=a&sl=23&s=SOURCE-ID+%2819700200915%29&origin=sourceinfo&zone=CSCYpreview&txGid=202b844e34cf5185a6d32aca45f24ee8&sessionSearchId=91e517f77e75028d715ae9a95341f258&limit=10

[2] lang_re = re.compile('[A-Z]\w*(?:[ \-][A-Z]\w*)*')

[3] https://unctad.org/system/files/official-document/tdstat47_en.pdf

[4]  "Total population, both sexes combined (thousands)". UNdata. United Nations Statistics Division. 11 July 2022. Retrieved 10 February 2023.

[5] https://www.webometrics.info/en/world
