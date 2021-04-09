# zindi_hotspots_challenge
This repository will contain code for solutions to the Zindi Hotspots challenge
## Description
This <a href="https://zindi.africa/hackathons/umojahack-3-hotspots">competion</a> was conducted by <a href="https://zindi.africa/">Zindi</a> as part of an inter-university Hackathon. For simplicity the challenege description has been made here too, though the original content can be found <a href="https://zindi.africa/hackathons/umojahack-3-hotspots">here</a>.

<p>Each year, thousands of fires blaze across the African continent. Some are natural occurrences, part of a ‘fire cycle’ that can actually benefit some dryland ecosystems. Many are started intentionally, used to clear land or to prepare fields for planting. And some are wildfires, which can rage over large areas and cause huge amounts of damage. Whatever the cause, fires pour vast amounts of CO2 into the atmosphere, along with smoke that degrades air quality for those living downwind.</p>

<p>Figuring out the dynamics that influence where and when these fires will occur can help us to better understand their effects. And predicting how these dynamics will play out in the future, under different climatic conditions, could prove extremely useful. For this challenge, the goal is to do exactly that. We’ve aggregated data on burned areas across the whole of the DRC for each month since 1 April 2000. You’ll be given the burn area data up to the end of 2013, along with some additional information (such as rainfall, temperature, population density etc) that extends into the test period. The challenge is to build a model capable of predicting the burned area in different locations over the 2014 to 2016 test period based on only this information.</p>

**Note that the evalustion information is elaborated on the challenge homepage**

## Data
<p>We’ve split up the DRC into ~3800 equal areas, centered around the locations provided in the lat/lon columns. The target variable, burn_area, is the percentage of the area that has been burned in a given month. Due to the way it’s measured, there may be some overlap of burned areas for two successive months, and so total burned area over a time period isn’t necessarily equal to the sum of the ‘burn_area’ figures for all months. You are not permitted to use external data in this competition.</p>

<p>You do NOT need to use GIS data to solve this challenge.</p>

<p>The files are hosted on the zindi website and can be downloaded via links provided in the description below:</p>

<ul>
  <li><a href="https://zindpublic.blob.core.windows.net/private/uploads/competition_datafile/file/304/train.csv?sp=r&sv=2015-04-05&sr=b&st=2020-08-08T11%3A28%3A33Z&se=2020-08-08T11%3A44%3A33Z&sig=f1zGDvuNF3u1fiKDNTGtHZ%2F8oTnj5Bw5W2RjxKzOs%2BA%3D">Train.csv</a></li> Is the dataset that you will use to train your model. This provides the details for 3821 area squares across the DRC for each month of the year starting from 1 April 2000 to 1 December 2013.
  <li><a href="https://zindpublic.blob.core.windows.net/private/uploads/competition_datafile/file/305/test.csv?sp=r&sv=2015-04-05&sr=b&st=2020-08-08T11%3A33%3A56Z&se=2020-08-08T11%3A49%3A56Z&sig=quF2Sh2gScbQv0mXMricwQKSsyArYvD7TKC49YDNHJw%3D">Test.csv</a></li>
  Is the dataset on which you will apply your model to. This dataset contains the same variables as the test data except there is no target (‘burn_area’). This is what you are predicting. The test sets covers 3821 area squares across the DRC for each month of the year starting from 1 January 2014 to 31 December 2016.
  <li><a href="https://zindpublic.blob.core.windows.net/private/uploads/competition_datafile/file/306/SampleSubmission.csv?sp=r&sv=2015-04-05&sr=b&st=2020-08-08T11%3A34%3A33Z&se=2020-08-08T11%3A50%3A33Z&sig=LnioLdh4fbfX%2FGNu4zL8GMzKMFrrsnimSsBc3ZoLC%2FY%3D">SampleSubmission.csv</a></li>
  Is an example of what your submission file should look like. The order of the rows does not matter, but the names of the IDs must be correct. The IDs take the form of [area ID]_yyyy-mm-dd. There are 3821 area squares each with a unique ID ranging from 0 to 3820.
  <li><a href="https://zindpublic.blob.core.windows.net/private/uploads/competition_datafile/file/307/VariableDefinitionsHotspot.csv?sp=r&sv=2015-04-05&sr=b&st=2020-08-08T11%3A35%3A19Z&se=2020-08-08T11%3A51%3A19Z&sig=VoWlYf2vEbdJokO%2BLtcPmoEkwjmyXHOmCywYMPQ%2F6GA%3D">VariableDescription.csv</a></li>
  Descriptions of the variables in the train and test set. You can find the sources of the variables in the below links.
  <li><a href="https://github.com/ML-Practise/zindi_hotspots_challenge/blob/master/Hotspots_Starter.ipynb">StarterNotebook.ipynb</a></li>
  This starter notebook will help you make your first submission onto the leaderboard. Here is a link to the Google Colab Notebook.
  <li><a href="https://zindpublic.blob.core.windows.net/private/uploads/competition_datafile/file/309/Hotspots_R_Starter.R?sp=r&sv=2015-04-05&sr=b&st=2020-08-08T11%3A50%3A26Z&se=2020-08-08T12%3A06%3A26Z&sig=TvUrwO71GB29HVMVXTsRDvbNx%2BNdeE%2FGo7PJuS7Irwg%3D">StarterNotebook.R</a></li>
  this starter notebook will help you make your first submission onto the leaderboard.
</ul>
<p>You can also download this files from the official competition <a href="https://zindi.africa/hackathons/umojahack-3-hotspots/data">page</a> if the links are broken.</p>

<p>The additional data included in the test and train files is as follows:</p>
<ul>
  <li>Climate: All columns climate_[variable] derived from https://developers.google.com/earth-engine/datasets/catalog/IDAHO_EPSCOR_TERRACLIMATE - see the image bands listed for more information.</li>
  <li>Land Cover: The percentage of the area falling into each of the LC_Type4 land cover types https://developers.google.com/earth-engine/datasets/catalog/MODIS_006_MCD12Q1 - see for details.</li>
  <li>UN-Adjusted Population Density (estimated number of persons per square kilometer) from https://developers.google.com/earth-engine/datasets/catalog/CIESIN_GPWv411_GPW_UNWPP-Adjusted_Population_Density</li>
  <li>Mean elevation in meters, from https://developers.google.com/earth-engine/datasets/catalog/USGS_GMTED2010</li>
  <li>Monthly Precipitation Estimates - https://developers.google.com/earth-engine/datasets/catalog/TRMM_3B43V7</li>
</ul>

<p>The discussion board for this challenge can be accessed <a href="https://zindi.africa/hackathons/umojahack-3-hotspots/discussions">here<a>. It's worth checking out as participants post important questions, solutions and hints that may be useful as you undertake the challenge.</p>
  <p>The repository contains a <a href="https://github.com/ML-Practise/zindi_hotspots_challenge/blob/master/Hotspots_Starter.ipynb">starter ipython notebook</a> but you can visit the competition's <a href="https://zindi.africa/hackathons/umojahack-3-hotspots/data">data page</a> to get the starter notebook written with R.</p>
