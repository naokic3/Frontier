Abstract
  I am proposing a theory to model patterns of human settlement and migration. A key feature is I am studying human spread over complex landscapes modeled as networks. An advantageof this is humans communicate and plan, taking advantage of network structures.




3. Data and Methods
3.1 Study Area
  The study was conducted across 3108 counties and county equivalents of the United States. This area includes a diverse set of interconnected nodes, providing an ideal geography to model complex diffusion patterns.
  The analysis excludes Alaska, Hawaii, Puerto Rico, U.S. Virgin Islands, Guam, American Samoa, Northern Mariana Islands and other territories due to their geographic distance and, which is out of the scope of this model
3.2 Geospatial Data
  County boundaries are defined by the U.S. Census Bureau's 2010 TIGER/Line Shapefiles, as the historical population data used has been calculated using these boundaries.
  Each county is identified by its Federal Information Processing Standard (FIPS) code. This dataset provides geometric information to define county boundaries and spatial relationships.
3.3 



3.4 Graph Structure
  We modeled the 3,108 counties of the contiguous U.S. as a directed, weighted graph G=(V,E). The vertices V represent the counties, and an edge (i,j)∈E exists if the corresponding counties share a border.
  The graph is sparse, with 18474 edges and a density of ρ≈0.0019. The graph has an average total degree of 11.89 and a 

  Nodes(Vertices):
      - 

  Edges(Links):

3.5 Data types
  Node Features:
      Land Cover Category: 9 land cover types are introduced as variables in the model. Each are their own variable, based on percentage cover of the county. This data is categorized into 9 land           cover types: Forest, Grassland, Shrub, Wetland, Water, Crop, Barren, Urban, and Pasture Land, in the order of most common to least common.(1790) Provides estimated land cover statistics by         year for 1630 to present. 
  Li, X., Tian, H., Lu, C., & Pan, S. (2023). Four-century history of land transformation by humans in the United States (1630–2020): annual and 1 km grid data for the HIStory of LAND changes (HISLAND-US). Earth System Science Data, 15(2), 1005–1035. https://doi.org/10.5194/essd-15-1005-2023
DATASET Li, X., Tian, H., Pan, S., & Lu, C. (2022). Land use and land cover changes in the contiguous United States from 1630 to 2020 (Version v1.1). Zenodo. https://doi.org/10.5281/zenodo.7055086

      Caloric Suitability of land: This measure estimates "the potential (rather than actual) ... caloric yield per hectare per year, under low level of inputs and rain-fed agriculture, capturing           cultivation methods that characterized early stages of development, while removing potential concerns that caloric yields.. Moreover, the estimates are based on agro-climatic constraints             that are largely orthogonal to human intervention, mitigating further possible endogeneity." 
        > Galor, Oded, and Ömer Özak. 2016. “The Agricultural Origins of Time Preference.” American Economic Review 106 (10): 3064–103. https://doi.org/10.1257/aer.20150020.

ELEVATION DATA

Raster data from USGS 3DEP 1 arc-second (approx. 30m precision). Data is converted from float32 to int16 for compression. 








Model Structure (PIGNN)

Dependent Variable: I Used Population growth rate over the decade, which can be expressed as . If fitted regression on county population based on previous population, results in a spurious regression problem due to shared trends. By transforming raw population data into rate of change, the dependent variable becomes a stationary time series, allowing my model to meaningfully test my hypothesis. 


Edge Features: Population ratio 



Unbalanced panel problem: Our dataset exhibits an endogenous entry problem, where a countries entry as a populated state is dependent on the frontier's expansion, and not random. As a result, a naive approach which treats the data as a balanced panel would yield biased coefficients and poor model performance. 

To solve this, we employ a two-stage model: 
- Selection Model: A binary classifier (GNN) which models the entry of counties as populated states,
  predicting when  each county becomes a possible location for settlement within the next timestep.
- Population Model: A model that estimates 


Counties far away from the frontier don't have population growth until they are reached. One needs to explain how and when counties "become inhabited " and start behaving according to the model. If one does not deal with this endogenous entry problem, for instance if we treated the dataset as a balanced panel with all counties in the dataset for all years, but unreached counties having zero population for many years, the model training will result in biased coefficients and reduced fit and performance.  We deal with this by modeling the entry of counties into the dataset by binary classifier. This model is best explained using an analogy of a cup that holds water. The Cup, the space that the water can take over, is the classifier which decides whether or not the county is able to be inhabited. It defines the "cup" or area which people can diffuse to at any given moment. The fluid is the main model which dictates the diffusion and flow of people, the "water" that fills this dynamic cup.



GNN within a Spatial Regression, to find adjacency matrix weights
Geographical Graph Attention Networks: Spatial Deep Learning Models for Spatial Prediction and Exploratory Spatial Data Analysis

County entry classifier






  

  
