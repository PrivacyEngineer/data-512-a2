# Bias in Data

### Name: Francisco Javier Salido Magos.

Date: October 31st, 2018.

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

- A dataset, provided in a single csv file (../raw_data/page_data.csv), from a project entitled "Politicians by Country from the English-language Wikipedia." by Oliver Keyes (https://figshare.com/articles/Untitled_item/5513449). We only use the data from this project. Each row in the csv file corresponds to an article written about a politician, and has three attributes: 1) "country", containing the country the article is associated with, 2) "page", containing the Wikipedia page title, and "rev_id" that contains the edit ID for the last edit to the Wikipedia page (this field is referred to by a different name in the Figshare page: "last_edit"). Note that country names are inconsistent, and that some of the countries mentioned don't exist any longer. How we dealt with this is described on the Jupyter notebook found in (../src/hcds-a2-bias.ipynb). The dataset included in this project was downloaded from Figshare on 10/27/2018. Note that over time these IDs get updated and some of them are no longer recognized by ORES.

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

## License

This assignment's code is released under a MIT license.

The data sources:

- The Figdata containing the article dataset was released under the CC-BY-SA 4.0 license.
- No details are provided on the license for the 2018 World Population Data Set in the Population Reference Bureau web site. At the bottom of every page in the site, however, there's a notice: "All rights reserved."
- Text in the ORES webpage is provided under the CC-BY-SA 3.0 license which we understand to extend to the use of data obtained through the API.
