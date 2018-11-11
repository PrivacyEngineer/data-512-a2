# Bias in Data.

### Name: Francisco Javier Salido Magos.

Date: October 29th, 2018.

## Goal

The goal of this project is to learn about the concept of bias in datasets. We do this by analyzing a dataset of articles related to politicians in different countries around the world, looking at coverage, the number of articles per country as compared to the size of its population, and also by looking at the quality of those articles, as ranked by Wikipedia's Objective Revision Evaluation Service (ORES).

We generate five objects:

- A spreadsheet in which each row corresponds to an article about a politician, and contains article name and ID number, country, and population and quality ranking as per ORES.
- A table showing the top 10 countries as ranked by their number of articles to population ratio.
- A table showing the bottom 10 countries as ranked by their number of articles to population ratio.
- A table showing the top 10 countries as ranked by the ratio of Featured Articles (FA) and Good Articles (GA), as ranked by ORES, to total articles for that country.
- A table showing the bottom 10 countries as ranked by the ratio of FA and GA, as ranked by ORES, to total articles for that country.

Once data analysis is completed, we evaluate our results and discuss how these results help us understand bias and present our conclusions.

## Data sources used

To create these objects, we will draw from three data sources:

- A dataset, provided in a single csv file (../raw_data/page_data.csv), from a project entitled "Politicians by Country from the English-language Wikipedia." by Os Keyes (https://figshare.com/articles/Untitled_item/5513449). We only use the data from this project. Each row in the csv file corresponds to an article written about a politician, and has three attributes: 1) "country", containing the country the article is associated with, 2) "page", containing the Wikipedia page title, and "rev_id" that contains the edit ID for the last edit to the Wikipedia page (this field is referred to by a different name in the Figshare page: "last_edit"). Note that country names are inconsistent, and that some of the countries mentioned don't exist any longer. How we dealt with this is described on the Jupyter notebook found in (../src/hcds-a2-bias.ipynb). The dataset included in this project was downloaded from Figshare on 10/27/2018. Note that over time these IDs get updated and some of them are no longer recognized by ORES.

- A dataset in a single csv file found in (../raw_data/WPDS_2018_data.csv), downloaded from a DropBox provided as part of the Homework A2 description. The dataset comes from the Population Reference Bureau (PBR), where it appears under the name "2018 World Population Data Sheet" (https://www.prb.org/international/indicator/population/table/?geos=WORLD). The dataset contains only two fields: "country", for country name, and "Population mid-2018 (millions)", the population of that country in millions.

- A Wikipedia service named "Objective Revision Evaluation Service" (ORES) (https://www.mediawiki.org/wiki/ORES) that estimates of the probability that a given article, identified through an ID number provided in the Figshare dataset, falls within one of six ranking categories. Since our analysis focuses on coverage and overall quality of articles, we're interested only in the ORES quality ranking with the highest probability for each article. Furthermore, our use of the ORES data focuses specifically on those articles ranked with the two highest rankings: Featured Article (FA) and Good Article (GA).

## Resources used

This analysis was prepared using Python 3.5.6 running in a Jupyter Notebook environment.  
Documentation for Python can be found here: https://docs.python.org/3.5/  
Documentation for Jupyter Notebook can be found here: http://jupyter-notebook.readthedocs.io/en/latest/  

The following Python packages were used and their documentation can be found at the accompanying links:

- requests: http://docs.python-requests.org/en/master/
- json: https://docs.python.org/2/library/json.html
- pandas: https://pandas.pydata.org/
- numpy: https://www.numpy.org/

## Files Created

The required file output for Homework A2 is a single csv file that should list all articles in (../raw_data/page_data.csv), with some added information. This output file can be found in (../results/results.csv), and contains one row for each article, and five fields:

- "country", the country with which the corresponding article is associated.
- "article_name", the title of the Wikipedia page where the article is referenced.
- "revision_id", id number for the last edit of the page.
- "population", the population of the country with which the corresponding article is associated.

## Data Processing

Process:

1. Downloaded the two datasets, one from Figshare and one from DropBox.
2. Obtained article rankings from ORES.
3. Evaluated data cleanliness and found inconsistencies and errors in the DropBox data, which were corrected.
4. Built an articles table that included population size for each country and article ranking, as well as all data found in the Figshare dataset.
5. Saved a copy of the above table in ../results/results.csv.
6. Constructed the five tables listed below in the "Visualizations Created" section.

## Visualizations Created

No graphics were created, but there are five tables that summarize our results, and they can be found in the Jupyter notebook:

- A table showing the top 10 countries as ranked by their number of articles to population ratio.
- A table showing the bottom 10 countries as ranked by their number of articles to population ratio.
- A table showing the top 10 countries as ranked by the ratio of Featured Articles (FA) and Good Articles (GA), as ranked by ORES, to total articles for that country.
- A table showing the 42 countries that appear in the dataset but have no articles ranked FA or GA associated with them.
- A table showing the bottom 10 countries that have at least one article ranked as either FA or GA, and rank lowest by their ratio of FA and GA, as ranked by ORES, to total articles for that country.

## Conclusions

The type of bias I was expecting to find in the articles dataset was the overrepresentation of articles written about English-speaking countries, particularly the U.S.A. and U.K., followed by articles about non-English speaking Western European countries, India and China, not only in terms of quantity, but also in terms of quality. This expectation was based primarily on the fact that these are the countries that tend to dominate the news in the U.S.A. Furthermore, I really did not expect to find any articles at all on small, out-of-the way countries, like Swaziland, San Marino or Lichtenstein, about federated states of larger countries, like Daguestan, or about far away islands that are part of former colonial powers, such as Guadeloupe and Martinique.

There were several things that I found surprising about the results. The first was the fact that the Figshare dataset did not seem to be well-curated. I can understand differences of spelling in country names, but the use of demonyms in lieu of actual country names, misspelings in the names of countries that regularly appear in the news, like Hondura instead of Honduras, and references to old languages or to prehispanic ethnic groups, like Incas, were a complete surprise.

In terms of absolute number of articles in the database, the results were largely in line with my expectations as out of the top twenty countries by absolute numbers, only Pakistan, Iran and Nigeria would not fall into my expected list. The surprising facts were that the countries with the largest populations tend to have really low article to population ratios. Five of the top ten countries in population appear in the bottom 10 in article to population ratio: India, China, Indonesia, Ethiopia and Bangladesh, with Brazil, the U.S.A. and Nigeria also ranking quite low.

In terms of article quality, a really surprising data point was Belgium, with 500+ total articles and none that ranked as either FA or GA. Given the fact that Brussels is the seat of the EU parlament and other important EU government bodies, as well as NATO, this was unexpected. Switzerland was another surprise, with 400+ articles and none ranking as high quality. Out of the top ten countries as ranked by FA and GA articles as a proportion of total, the United States is the only country I expected would show up in the list, though I can justify the presence in this list of countries that appear regularly in the news like Saudi Arabia and, perhaps, Vietnam.

Given that the Figshare database claims to contain "most English-language Wikipedia articles within the category 'Category:Politicians by nationality' " I have to conclude that, at least in this area, Wikipedia is not very representative of what goes on in the World in general, or in the English-speaking world in particular. The largest countries in the world, either by population or by economic activity, are largely underrepresented both in terms of quantity and quality. A possible exception to this statement might be the United States, but there are also good points to argue the contrary. Smaller, out-of-the way countries like Tuvalu, San Marino and Palau seem to have an outsized representation when compared to their small populations. Finally, it's important to point out that important countries, in terms of population and of participation in the world economy, like Belgium and Japan, seem to be largely overlooked.

My theory is that this situation could be explained by a combination of factors:

1. Language is definitely a key factor, as would-be-authors in non-English speaking readers are not likely be interested in writing articles about local politicians that no one is going to read.

2. English-speaking writers in relatively large countries, like the U.S.A., U.K. or Canada, are less likely to write in English about what is going on in other parts of the world, with the exception of high-profile conflicts, like those in the middle east.

3. Finally, for larger, English-speaking countries, people are not likely to go to Wikipedia to learn about the comings, goings and platforms of local politicians. Politicians in islands in the Pacific and other small, touristy locations with comparatively large English-speaking populations and limited options in terms of news media may be more likely to leverage Wikipedia as a vehicle to make themselves known and/or communicate with their constituents.

## License

This assignment's code is released under a MIT license.

The data sources:

- The Figdata containing the article dataset was released under the CC-BY-SA 4.0 license.
- No details are provided on the license for the 2018 World Population Data Set in the Population Reference Bureau web site. At the bottom of every page in the site, however, there's a notice: "All rights reserved."
- Text in the ORES webpage is provided under the CC-BY-SA 3.0 license which we understand to extend to the use of data obtained through the API.
