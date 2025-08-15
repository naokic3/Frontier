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

  

  
