**INTRODUCTION**

The COVID-19 pandemic has caused significant disruptions to the lives of people worldwide, and the visualization of its spread through thematic maps has become an essential tool in the fight against the virus. While these maps have helped identify regional hotspots and areas most at risk, they have not yet fully explored the potential of the data. This paper proposes a novel visualization tool that goes beyond the limitations of existing maps, utilizing the idea from Correll et al.'s Surprise Map to identify unusual or informative spatial regions that are not immediately apparent.

Our approach involves constructing a space of initially equi-plausible models and performing Bayesian update steps to re-estimate their plausibility. By doing so, we are able to identify surprising events and visualize them on thematic maps, providing a more complete and insightful story of the pandemic's impact. The tool aims to improve our understanding of the virus and its effects on the United States, contributing to the ongoing fight against it.

By highlighting unusual and informative regions on thematic maps, we hope to provide a more comprehensive understanding of the virus's impact and help identify areas that require more attention. Our work shows the potential of advanced data visualization tools in tackling complex problems such as the COVID-19 pandemic, and we believe that our approach can be applied to other areas of research and analysis as well.


2. Thematic map

2.1 기존 Chropleth map들의 장점

[Trustworthy COVID-19 Mapping: Geo-spatial Data Literacy Aspects of Choropleth Maps]

cartographers have conducted research on the readability and the usability of thematic maps for decades, and they have found many rules for suitable choropleth maps that avoid to misinform or misguide the map reader (e.g., Bertin [1967](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR1 "Bertin J (1967) Sémiologie graphique: Les diagrammes, les réseaux, les cartes. Gauthier-Villars, Paris"); Dibiase et al. [1992](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR5 "Dibiase D, MacEachren AM, Krygier JB, Reeves C (1992) Animation and the role of map design in scientific visualization. Cartogr Geogr Inf Syst. 
https://doi.org/10.1559/152304092783721295"); MacEachren [1995](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR11 "MacEachren AM (1995) How maps work. Guilford Press, New York"); Tyner [2010](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR23 "Tyner JA (2010) Principles of map design. Guilford Press, New York")).

In Monmonier ([1996](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR14 "Monmonier M (1996) How to lie with maps. Am Stat. 
https://doi.org/10.2307/2685420")), cartographic principles are discussed and how maps can be used and misused is illustrated. In Monmonier ([1996](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR14 "Monmonier M (1996) How to lie with maps. Am Stat. 
https://doi.org/10.2307/2685420")) and Campbell and Shin ([2011](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR4 "Campbell JE, Shin M (2011) Essentials of geographic information systems; Saylor Academy: Washington, DC, USA, 
https://digitalcommons.liberty.edu/textbooks/2
. Accessed 6 Jul 2020")), one finds elaborate descriptions of the intricacies of color use, symbol selection and map design as well as layout issues.

absolute numbers of confirmed COVID-19 cases were used for differently sized US states with varying population. To make the COVID-19 cases comparable, one has to normalize them against the total population. A widely used rate is cases per 100,000 inhabitants. Then, comparisons are meaningful, even in less populated states or regions.

In addition to the irritating absolute numbers, Fig. [4](https://link.springer.com/article/10.1007/s42489-020-00057-w#Fig4) is illustrated with red colors, which is known to be able to cause anxiety, fear or danger on the map reader’s side. So, this is an inappropriate choropleth map representation for the map content related to a pandemic, which is an unpleasant topic by itself. Slocum et al. ([2009](https://link.springer.com/article/10.1007/s42489-020-00057-w#ref-CR21 "Slocum TA, McMaster RB, Kessler FC, Howard HH (2009) Thematic cartography and geovisualization, 3rd edn. Prentice Hall, Upper Saddle River")) present examples of appropriate choropleth maps and could be consulted for best practice examples.

2.2 Spatial difference / Temporal Difference

NYT, Johns Hopkins



[Visualizing COVID-19 information for public: Designs, effectiveness, and preference of thematic maps]



[Map Visualization using Spatial and Spatio-Temporal Data: Application to COVID-19 Data]

[The COVID-19 Pandemic Vulnerability Index (PVI) Dashboard: Monitoring County-Level Vulnerability Using Visualization, Statistical Modeling, and Machine Learning]


2.2 Misleading Maps

[States Are Reopening With No Clear Picture of U.S. Coronavirus Cases]
- Changes in testing capacity, reporting discrepancies around fatalities, and overall differences in methodologies have made interpreting data a challenge, especially when trying to compare one geographic region or time period to another.


[From coronavirus to bushfires, misleading maps are distorting reality](https://firstdraftnews.org/articles/from-coronavirus-to-bushfires-misleading-maps-are-distorting-reality/)
- 

[The need for GIScience in mapping COVID-19]
- Securing geo-located health data at a high enough spatial resolution to detect meaningful patterns has proven challenging due to privacy constraints

- Whatever the method of collection, the increase of higher resolution and dynamic geo-located data on COVID-19 can allow researchers to go beyond the simple maps of present to tell a much bigger, more detailed story.



2.3 Tools /apps




2.4 Surprise map에 대한 페이퍼



우리의 Method



3. Dataset

3.1 Data Collection

3.2 Data Preprocessing
