# Can animal movement and remote sensing data help to improve conservation efforts?
Matthias F. Biber, Global Change Ecology, University of Bayreuth, Bayreuth, Germany  
`r format(Sys.Date(), '%d.%m.%Y')`  



<!--
Look at Naidoo2012 and Loarie2009a for nice examples for potential publication.
Convert awei into non-water/water classification and calculate distance to water!
Compare NDVI of dry vs. wet season derived from Landsat!!!
-->

# List of Abbreviations {-}

CO2 = Carbon Dioxide, LULCC = Land Use and Land Cover Change, PA = Protected Area, RS = Remote Sensing, NDVI = Normalised Difference Vegetation Index, SSF = Step Selection Function, MODIS = MODerate resolution Imaging Spectroradiometer, IUCN = International Union for Conservation of Nature, VI = Vegetation Index, AVHRR = Advanced Very High Resolution Radiometer, GIMMS = Global Inventory Modeling and Mapping Studies, WDPA = World Database on Protected Areas, EVI = Enhanced Vegetation Index, NIR = near infrared, SWIR = shortwave infrared, NDMI = Normalised Different Moisture Index, NDWI = Normalised Difference Water Index, MNDWI = Modified Normalised Difference Water Index, AWEI = Automated Water Extraction Index, WI2015 = 2015 Water Index, TM = Thematic Mapper, ETM+ = Enhanced Thematic Mapper Plus, SRTM = Shuttle Radar Topography Mission, IGBP = International Geosphere Biosphere Programme, RSF = Resource Selection Function, Global Positioning System = GPS, AKDE = Autocorrelated Kernel Density Estimator, CCA = Community Conservation Area

# Acknowledgements {-}

Above all, I would like to acknowledge my supervisor, Dr. Martin Wegmann, for his constant support and feedback on this thesis. Thanks also goes to his PhD student Ruben Remelgado for stimulating discussions and ideas on the remote sensing aspect of this work. I would also like to thank my second supervisor Dr. Thomas Mueller. I would like to express my sincere thanks to Dr. Ilya Fischhoff for providing the Laikipia plains and Grevy’s zebra movement data as well as the Laikipia landuse data. I would also like
to thank Dr. Hattie Bartlam-Brooks, Pieter Beck, Gil Bohrer and Stephen Harris for making the data of their study openly accessible on Movebank. Furthermore, I am especially grateful to Sebastian Dörner, Mathias Brunner, Michael Schneider and Laura Matt for their personal support and friendship. Last but not least, I would like to acknowledge Franziska Palm, Yvonne Radstacke, Ben Strachan and Laura Matt for proofreading.

# Motivation

Since the beginning of the Industrial Revolution anthropogenic activities have an increasing effect on the global environment. By now these effects are so profound, that the term "Anthropocene" has been introduced to describe the current ecological epoch [@Crutzen2002; @Steffen2007; @Lewis2015; @Corlett2015]. Fossil fuel emissions and land use change have caused an increase in carbon dioxide (CO$_{2}$) concentrations by 40\% compared to pre-industrial levels. The increase in atmospheric CO$_{2}$ is the largest driver of climate change. Global surface temperature is predicted to be more than 1.5$^{\circ}$C higher by the end of the 21$^{st}$ century relative to the average global surface temperature between 1850 and 1990 [@IPCC2013]. Anthropogenic activities have not only affected the Earth's climate system, but have also considerably changed the world's ecosystems. 

Land use and land cover change (LULCC) are considered to be one of the main effects of anthropogenic activities on the environment [@Foley2005; @Burkhard2012]. LULCC are further acting synergistically to climate change, thus further amplifying the effect on the environment [@Lambin2001; @Opdam2004]. LULCC can occur in the form of agricultural land-clearance, suburban sprawl, and timber harvests among others [@Lambin2001] and lead to the degradation of ecosystem services [@Burkhard2012], which on the long run causes significant harm to human well-being [@MEA2005]. 

Not only humans are affected by the changes in our environment [@Pereira2010]. Biodiversity loss has increased dramatically in the Anthropocene and current extinction rates are estimated to be 1000 times higher than natural background rates of extinction [@DeVos2015]. As a result, [@Dirzo2014] introduced the term "Anthropocene defaunation" to describe the global extinction of faunal species and populations and the decline in abundance of individuals within populations. Nevertheless, the impact of humans on biodiversity is an often underestimated form of global change. 

LULCC are believed to have the strongest impact on biodiversity loss due to the resulting habitat loss and fragmentation [@Fischer2007]. Habitat loss negatively affects species richness, genetic diversity, population abundance and distribution [@Fahrig2003]. Habitat fragmentation negatively affects the fitness and movement of individuals [@Cattarino2016]. It forces some animals to move more often through human-dominated systems [@Nogeire2015] or even leads to a reduction in the dispersal ability of an organism across the landscape [@Opdam2004]. Habitat fragmentation also hampers the ability of an individual to find suitable habitat [@Cattarino2016]. Climate change will further force many organisms to relocate to new climatically suitable habitats [@Hof2011]. If climate change occurs together with habitat fragmentation, it is likely to prevent animals from tracking these changes in the thermal landscape [@Opdam2004]. Mapping the areas, which are important for animal movement, thus plays a key role in conservation planning [@Nogeire2015].

Protected areas (PAs) are the most important tool for *in situ* conservation of animals in their natural ecosystem in order to maintain biodiversity [@Chape2005; @Rodrigues2004]. Around 14.6\% of the Earth's land surface are currently protected [@Butchart2015] and PAs represent a considerable amount of human land use [@Chape2005; @Foley2005]. Nevertheless, they still fail to counteract species extinction. @Butchart2015 estimated that 59-68\% of ecoregions, 77-78\% of important sites for biodiversity, and 57\% of 25380 species have inadequate coverage. However, space for new parks and corridors is becoming more limited [@McKinney2002]. @Wittemyer2008 found that PAs often lead to a displacement in population to the surrounding areas, thus reducing its effectiveness and the conservation of biodiversity. LULCC have also been shown to increase in surrounding areas of PAs [@Hansen2004], which is likely to have a knock-on effect inside the PAs [@Willis2015]. The surrounding areas of PAs were found to become increasingly fragmented [@Nagendra2008b; @Nagendra2009], hence reducing their functioning as ecological corridors, which in turn increases the isolation of PAs [@DeFries2005]. In addition, the establishment of PAs often does not correlate with identified conservation priorities [@Chape2005] or ecological processes, but rather reflects political, jurisdictional, opportunistic, land-cover or land-use boundaries [@DeFries2010]. Management of existing PAs is often insufficient [@Leverington2010] and particularly in the Tropics PAs are under severe threat [@Chape2005]. 

The increasing human pressures on PAs, call for a globally consistent monitoring scheme, which covers large spatial areas, long time periods and is cost-efficient [@Nicholson2006; @Henry2008; @Scholes2008], in order to assess the PAs' effectiveness [@Nagendra2013]. In order to meet the requirements for biodiversity conservation and ecosystem management with regard to global change, it is necessary to observe and correctly predict the habitat use of animals [@DeKnegt2011] and so infer the areas that need to be protected [@Widmann2015]. This requires first of all good monitoring data, but also robust models [@Honrado2016]. As a result, Remote Sensing (RS) and movement ecology have turned into important disciplines in recent years [@Turner2003a].

In the past, RS has been primarily used to monitor abiotic conditions, such as rainfall, temperature, wind, elevation and bathymetry. But, it can also provide relevant information on the occurrence, extent and impact of environmental disturbances, such as flood, drought or fire and help to monitor the status of PAs by providing information on vegetation condition, anthropogenic disturbances and the distribution of invasive species [@Pettorelli2014; @Nagendra2013]. RS has a key advantage compared to other methods, as it can be applied at a variety of spatial and temporal scales and is an efficient, unbiased, non-invasive, quantitative method [@Willis2015]. Remote sensing can detect changes in ecological status or land-cover and can thus improve conservation abilities and assess the effectiveness of management without disturbing the landscape [@Pettorelli2014; @Willis2015; @Wegmann2014].

Movement ecology tries to answer fundamental questions about the movement of an organism, which is driven by the organism's internal state, its motion and navigation capacities and external factors [@Nathan2008]. However, the latter mostly determines an animal's decision to move, as it does not move just for changing its location, but rather for changing the environmental conditions it experiences at its location [@VanMoorter2016]. Animal movement drives many essential ecological processes, such as migration and dispersal, which influence population dynamics, animal behaviour, as well as the distribution and persistence of biodiversity [@Jeltsch2013; @Barton2015; @McClintock2014; @Bauer2014]. The movement of animals can be studied using a variety of methods (telemetry, mark-capture, occupancy analysis, diet analysis or through the development of mechanistic models) [@Driscoll2014] and recent advances in animal tracking devices have tremendously facilitated movement ecology [@Cooke2004a, Wilson2008a, Rutz2009, Urbano2010]. It allows to track multiple individuals over large distances and for extensive time periods (multiple years). 

Together with the vast availability of publicly accessible remotely-sensed environmental data, this has helped us to understand the environmental drivers of movement patterns at various spatial and temporal scales [@Neumann2015a; @Trierweiler2013; @Pettorelli2014]. This tells us if the environment inhibits or fosters movement [@Fahrig2007; @Beyer2016] and how it influences distribution patterns and population dynamics [@Trierweiler2013]. The infered knowledge can then be fed into predictive models and used to inform management and conservation practices [@Avgar2013]. Thus, knowledge about the environment, e.g. derived from RS data, and the movement of an animal can considerably help to conserve and manage biodiversity [@Barton2015; @Neumann2015a; @DeKnegt2011; @Driscoll2014].

# Drivers of habitat selection in migratory plains zebras

## Abstract

Climate and land-use change have a growing influence on the world's ecosystems, in particular in Africa, and increasingly threaten wildlife. The resulting habitat loss and fragmentation can impede animal movement, which is especially true for migratory species. Ungulate migration has declined in recent years, but its drivers are still unclear. Animal movement and remote sensing data was combined to analyse the influence of various vegetation and water indices on the habitat selection of migratory plains zebras in Botswana's Ngamiland. The study area experienced a more or less steady state in Normalised Difference Vegetation Index (NDVI) over the last 33 years. More than half of the study area was covered by PAs. NDVI increased stronger in PAs compared to areas that were not protected. NDVI was always higher in the Okavango Delta compared to the Makgadikgadi Pans. Although zebras are thought to select for areas with high NDVI, they experienced a lower NDVI in the Makgadikgadi grasslands during wet season. Step selection functions (SSFs) showed that NDVI derived from Landsat as well as NDVI derived from the Moderate Resolution Imaging Spectroradiometer (MODIS) were significant drivers of habitat selection across all individuals. Migration seems to be driven by the high nutritional value of the Makgadikgadi grasslands and not seasonal resource limitation. Landsat imagery was shown to provide different environmental information compared to MODIS data. This highlights not only the importance of NDVI for explaining animal movement, but also the importance of Landsat imagery for monitoring habitat extent and fragmentation. Incorporating the animal's behavioural state and memory into SSFs will help to improve our ecological understanding of animal movement in the futurue.

**Keywords:** remote sensing, animal movement, protected areas, conservation, plains zebras, habitat selection, normalised difference vegetation index, step selection functions, Ngamiland, Botswana.

## Introduction

In Africa, the socio-economic development of the past 30 years has led to severe habitat loss and fragmentation. Future biodiversity scenarios predict that Africa is one of the continents with the largest habitat loss by 2050 [@Visconti2011]. All this results in an increased and unprecedented threat to wildlife [@Brooks2002; @Newmark2000; @Newmark2008] and many large mammal populations in Africa have been declining [@Craigie2010]. @Wegmann2014 found that PAs in southern and eastern Africa, e.g. Botswana and Kenya, had a high irreplaceability compared to the PAs in West and North Africa. This is likely due to their larger size or the fact that PAs in southern and eastern Africa host a higher number of large mammal species [@Rondinini2005]. 

Habitat loss, fragmentation and the expansion of infrastructure can impede the movement of animals and so reduce animal interactions, population connectivity and genetic exchange [@Fischer2007; @Kaczensky2011; @Zeller2012; @Tracey2013]. Migratory animals have large area requirements and consequently are particularly susceptible to these anthropogenic changes [@Berger2004; @Bolger2008; @Wilcove2008]. Migration, the seasonal return movement of populations between two areas, is a common global ecological phenomenon [@Dingle2007; @Alerstam2003; @Bolger2008; @Teitelbaum2015]. It helps to maintain biodiversity and the resilience of ecosystems, as it furthers the transfer of energy and genetic information [@Jeltsch2013; @Pettorelli2014; @Bauer2014]. The population numbers and available habitat of many migratory species are declining, due to habitat alteration, range restriction, overexploitation and climate change, while some migrations have already been entirely extinguished or are highly threatened [@Fryxell1988; @Serneels2001a; @Bolger2008; @Berger2004; @Wilcove2008; @Harris2009]. 
The role of long-distance migrations in maintaining local and global patterns of species distributions and ecosystem function is not well understood [@Jeltsch2013] and little is known about how climate change may affect animal movement in the future. All of this makes long-distance migrations extremely difficult to conserve [@Wilcove2008].

Complete migration is rather uncommon as most species only partially migrate, meaning that some individuals in a population undertake seasonal migrations, while others remain in one place for the entire year [@Dingle2007; @Chapman2011]. Individuals within a population can be genetically predisposed to migration [@Berthold1981], or their behaviour might depend on variation in individual, social or environmental factors [@White2007a; @Barton2015]. Partial migration is especially common when resource availability is highly variable through time and density dependence prevails, while more or less static landscapes favour sedentary ranges [@Taylor2007b; @Mueller2008; @Mueller2011; @Boettiger2015].

Migration of animals is mostly driven by seasonal variation in resource availability (e.g. phenology, water availability, weather and climate), specific nutrient demands, intra-specific competition, predation, parasitism or extreme climatic conditions [@Fryxell1988; @Alerstam2003; @Bolger2008]. The importance of different factors varies in space (seasonal versus non-seasonal environments) [@DeKnegt2011] and time (intra- and interannual variation) [@Boone2006], but also differs among species [@Singh2010]. 

In general, the spatial distribution of foraging resources is thought to be the dominant driver of animal movement [@Berger2004; @Schweiger2015]. This has been extensively tested by using spatial and temporal variation in vegetation indices, such as NDVI, as a proxy for food availability [@Fryxell2005; @Pettorelli2005; @Hebblewhite2008; @Mueller2008a; @Boettiger2015; @Trierweiler2013; @Bohrer2014; @Bartlam-Brooks2013; @Neumann2015a; @Teitelbaum2015].

In the Tropics, seasonality is primarily defined by differences in precipitation and not in temperature [@Naidoo2012]. African semi-arid grasslands thus tend to be limited by water availability rather than nutrients [@Breman1983]. Migratory behaviour in these regions is thus more likely driven by the availability of drinking water [@DeBeer2008; @Redfern2005]. Precipitation is considered as one of the main drivers of ungulate migration [@Bolger2008; @Harris2009] and zebras were found to time their migration according to rainfall events [@Bartlam-Brooks2011; @Naidoo2014]. While rainfall itself might supply water to formerly dry areas and so increase space use, it may also increase the heat loss in individuals and so decrease space use [@Rivrud2010; @vanBeest2011]. Rainfall also promotes vegetation growth, thus indirectly providing more foraging resources [@Okitsu2005]. Combining a measure for vegetation with precipitation data improved the prediction of the timing and speed of the migration of plains zebras (*Equus burchelli*) [@Bartlam-Brooks2013].

Forage quality is also an important driver of animal movement [@Berger2004; @Schweiger2015]. African grasslands show substantial seasonal and spatial variation in forage quality [@Breman1983], which is negatively related to annual precipitation and primary production. Furthermore, mortality rates of African herbivores are more strongly related to foraging quality than to resource abundance [@Fryxell1987; @Sinclair1985]. Migratory grazers in the Serengeti, such as wildebeest, were found to move away from resource-rich areas to short grasslands with low annual rainfall at the beginning of the wet season. There they gain access to less abundant, nutrient-rich foraging grounds and avoid predation. During dry season they then return to the resource-rich areas [@Fryxell1988; @Coughenour1991]. 
Nevertheless, during wet season wildebeest and other ungulates still follow rainfall and plant regrowth within the less abundant foraging grounds [@McNaughton1985; @Durant1988].

Migratory behaviour is likely driven by a combination of factors acting synergistically. For example, the cause or timing of wildebeest migration was shown to be influenced by green forage [@Boone2006] or rainfall leading to green forage [@Talbot1963], compensatory vegetative production [@McNaughton1976], areas of fewer diseases or predators [@Darling1960; @Fryxell1988], higher quality water [@Gereta1998], minerals [@Kreulen1975] and resources synchronously, to reduce competition with resident ungulates and swamp predators during the calving season [@Estes1976].

Spatio-temporal variation in resource availability has important ecological and conservation implications, in particular for wide-ranging species, such as ungulates. Human activity increasingly threatens wide-ranging ungulate populations [@Berger2004; @Harris2009]. Due to increasing ecosystem loss and fragmentation there has been a decline in ungulate migrations in grassland and boreal woodland ecosystems in recent years [@Bartlam-Brooks2011; @Bartlam-Brooks2013; @Olson2010]. 

This calls for immediate action to identify and prioritise migration routes for conservation [@Sawyer2009]. Conservation of migratory movements often requires the protection of vast areas, which is a challenging task [@Thirgood2004]. 
In the past, partially protected and poorly understood populations have collapsed [@Bolger2008; @Harris2009]. 

Quantifying migration occurrence, migration parameters and their environmental drivers is essential to understand the animal's movement and so derive conservation measures and monitor changes in migratory behaviour due to anthropogenic effects [@Berger2004; @Bolger2008; @Wilcove2008; @Katzner2012; @Bauer2014; @Naidoo2014]. Therefore, multiple individuals across a variety of environmental conditions need to be studied, so that the population spread and habitat selection of these individuals can be modelled [@Avgar2013]. Migration timing and speed of plains zebras has been modelled by looking at perceptual cues [@Bartlam-Brooks2013], while @Bracis2017 further investigated if the migratory direction is a result of perceptually- or memory-guided changes in resources.

In this chapter, the effectiveness of current protection measures and the habitat selection of plains zebras will be analysed by addressing the following questions:

* Has there been an increase or loss in vegetation over the last 30 years?
* Is vegetation loss greater within and in close proximity to PAs?
* What are the movement characteristics of migratory plains zebras?
* What is the major driver of habitat selection in plains zebras?

## Materials and Methods

### Study Area

The study area was delineated by the extent of our movement data plus a 5 % margin. It lies between 23.4° and 25.4°E Longitude and between -20.9° and -19.2°S Latitude, and covers an area of 39588 km^2^ and extends from the Okavango Delta in the northwest district to the Makgadikgadi grasslands in the central district of Botswana (Fig. 1). The area is characterised by a semi-arid climate (Fig. S1). Temperature is relatively constant through time and space and the mean temperature ranges from 15.5 to 26.2°C over the course of the year. Mean annual rainfall lies between 0 and 104 mm per month and varies between and within seasons. Most of the rainfall (325 mm) occurs during the rainy season (December - April), while during the dry season (April - December) precipitation only reaches 94 mm (Fig. S1) [@Hijmans2005]. The area is generally flat with a low variation in altitude (884 - 1018 m) (Fig. S2).

![](Figures/Studyarea_BWA.png)

**Fig. 1.** Map of Botswana with the study area indicated in red. District boundaries are shown by white dashed lines. The location of all cities with a population of more than 40000 people is shown and the capital city is highlighted in orange. Administrative boundaries were obtained from http://www.gadm.org using the `raster` package [@Bivand2016a]. Locations of cities were obtained from the `maps` package [@Becker2016].

Savanna ecosystems are tropical and subtropical grasslands intermixed with a discontinuous layer of trees and shrubs. They typically form a heterogeneous landscape, which is influenced by rainfall, soil type, grazing, browsing, fire and their interactions [@DeKnegt2008; @Shorrocks2014]. African savannas are dominated by C4 plants, which have a very high photosynthetic efficiency, as they have to overcome periodic burning, seasonal drought and flood. C4 plants are extremely poor quality food for most herbivores, vertebrates or invertebrates, but ungulates can break down cellulose and so are adapted to forage on these plants [@Shorrocks2014].

The Okavango Delta, the world's largest Ramsar Wetland of International Importance, is the only permanent water body in north-western Botswana. It is fed by the Okavango River, the second largest river in southern Africa. The mean annual inflow to the Okavango Delta is 11 x 10^9^ m^3^, which is augmented by 45.5 % of rain. Almost all of the water (96 %) is lost to the atmosphere by evapotranspiration, 2 % flow out of the system as surface flow and the remaining 2 % is lost to groundwater [@Ellery1998]. Between 3000 and 5000 km^2^ of the Delta usually remains inundated during the low flood season in December. In August the Delta extends to 6000 sometimes even up to 12000 km^2^ [@Kgathi2014]. Most ecological processes in the Okavango Delta system are driven by the annual flood pulse, as the availability of resources depends on rainfall and the water flow of the Okavango River. Both have declined between the 1970s and 2000s [@Kgathi2014]. Due to its permanent water resources, rich grasslands and forests and the resulting wildlife biodiversity the Okavango Delta is an attractive area for various interest groups. This leads to a growing human demand of natural resources.

The Makgadikgadi Pans is a complex of salt pans, which lies south of the Okavango Delta at a distance of approximately 250 km. The area lies below 950 meters. Some salt pans are covered with salt-tolerant grasses, but most of them are covered by saline and highly alkaline mud. During the rainy season the pans are partly filled with shallow water, while in the dry season the water rapidly dries out and saltbubbles and encrustations form on the surface [@Cooke1979]. Occassionally the Okavango Delta floods reach the Makgadikgadi Pans [@Varis2008], but this has not happened since 1991 [@White2006]. The lacustrine soils of the Makgadikgadi support grasses with high protein and mineral content which are particularly utilised by ungulates [@Baillieul1979].

### Plains zebra

There are three species of zebras in Africa, the plains zebra (*Equus burchelli*), the Grevy's zebra (*Equus grevyi*) and the mountain zebra (*Equus zebra*). The plains or common zebra is Africa's most abundant and widespread wild horse (shoulder height 1.3 m, weight 175 - 300 kg) and includes several subspecies.

Until 15 years ago, plains zebras were found in nearly all countries of eastern, southern and south-western Africa, since then they have been extirpated from several parts of their range [@Hack2002]. By now, plains zebras are listed as "Near Threatened" on the International Union for Conservation of Nature (IUCN) Red List of Species as there has been a population decline of 24\% over the last 14 years [@King2016]. They can be found in a wide range of savanna habitats, from short or tall grassland, to open woodland in East and Southern Africa, as they typically inhabit grassland areas [@McNaughton1986]. Grass constitutes nearly all of the zebra's diet. They particularly favour *Themeda triandra*, *Cynodon dactylon*, *Eragrostis superba* and *Cenchrus ciliaris*. Occassionaly, they might browse or dig up corms and rhizomes in particular during the dry season [@Grubb1981]. Zebras are hindgut fermenters, which means that cellulose digestion takes place after normal digestion, in the caecum. Hindgut fermenters are less efficient but pass food faster through their digestive system than foregut fermenters. They can therefore use lower quality food and are adaptive rather than selective grazers [@Shorrocks2014]. Zebras have to graze frequently throughout the day and night [@Fischhoff2007a] and are more strongly water dependent than other ungulate species, such as wildebeest. During dry season their distribution is confined to areas where perennial water sources are available [@Kgathi1993], as they have to drink approximately once a day [@Fischhoff2007a]. They typically live in small harems, which consist of one stallion male and one to eight females and their dependent offspring. When the offspring reaches sexual maturity they leave their natal harem and the males join together in bachelor herds. While harems usually remain stable over years, herds (groups of multiple harems) are typically unstable and can change over hours to days. After a gestation period of around one year females produce a single foal (30-35 kg). They usually give birth at the start of the rainy season, when forage availability is high [@Fischhoff2007a; @Fischhoff2007b]. 

### Movement Data

Movement data of seven adult female plains zebras was obtained from the Movebank Data Repository [@Bartlam-Brooks2013a]. Only females were tagged to avoid sex- or age-specific biases. Zebras were tagged in October 2007, August and October 2008. Their position was recorded every hour, apart from one individual (Z3864), which was tracked every 15 minutes. In total, the dataset contained 53776 point locations and covered a time span of 20 months (Table 1). 

**Table 1.** Start and end date of the tracking period, tracking duration (days), total distance (km) and median time interval (min) of each individual zebra.


-------------------------------------------------------------------------------------
 ID    Start date   End date   Duration (days)   Distance (km)   Time interval (min) 
----- ------------ ---------- ----------------- --------------- ---------------------
Z3864  2007-10-25  2008-01-05       72.19            1124                16          

Z3743  2007-10-28  2008-08-28       305.4            3750                59          

Z3866  2007-10-25  2008-10-22       363.6            4087                59          

Z6402  2008-10-24  2009-04-21        179             2210                60          

Z6405  2008-08-27  2009-03-31       216.6            2532                60          

Z6407  2008-08-27  2009-05-27       273.2            3409                59          

Z6399  2008-10-24  2009-06-01       220.2            3035                60          
-------------------------------------------------------------------------------------

<!--
The fence is clearly visible on very high resolution satellite imagery and a digital version of the fence was drawn by hand using the Google Satellite `OpenLayers` plugin in QGIS [@QGISDevelopmentTeam2016] (see Fig. \ref{fig:zebra_overview_bwa}). 

There is a fence east of Nxai Pan NP, which we ignored, see Naidoo et al. 2013.
-->

### Environmental Data

In environmental conservation and ecology vegetation indices (VIs) are commonly used as proxies for vegetation greenness and primary productivity [@Pettorelli2011; @Neumann2015a]. NDVI is calculated as the ratio of red (RED) and near-infrared (NIR) reflectance:

(1) $$ NDVI = \frac{(NIR - RED)}{(NIR + RED)}$$ 

The resulting NDVI values range from -1 to +1. High NDVI values represent healthy vegetation, as it absorbs most light in the RED part and strongly reflects in the NIR part [@Pettorelli2005].

NDVI data derived from the Advanced Very High-Resolution Radiometer (AVHRR) is the only continuous long-term NDVI product and so a valuable tool for analysing long-term changes in vegetation. The Global Inventory Modeling and Mapping Studies (GIMMS) group provides bi-monthly maximum NDVI values on a coarse spatial resolution of 8 x 8 km [@Pinzon2014]. The GIMMS NDVI3g data is not atmospherically corrected, except for two volcanic stratospheric aerosol periods (1982-1984 and 1991-1994), however the data has been corrected for orbital drift by removing common trends between the solar zenith angle and NDVI using the empirical mode decomposition method [@Campo-Bescos2013]. 

Global AVHRR GIMMS NDVI3g binary data from January 1982 to December 2013 were obtained from http://ecocast.arc.nasa.gov/data/pub/gimms/3g.v0/. The data was cropped to the extent of our study area. Following the procedure of @Wegmann2014, the change in NDVI for each pixel within our study area was calculated using linear regressions (Fig. 3).

The spatial extent of all protected areas within the study area was accessed through the World Database on Protected Areas (WDPA) at http://protectedplanet.net. Based on the PA boundary, three zones were differentiated: Protected, 5km Buffer (area outside a PA but less than 5 km from the PA boundary) and Unprotected (Fig. S4). We compared the slope and adjusted R^2^ of change in NDVI for every pixel with a significant linear relationship (p < 0.05) among each of the three zones (Fig. 5).

The Moderate Resolution Imaging Spectroradiometer (MODIS) provides two VI products, NDVI and EVI, on a large spatial (global) and temporal scale (2001 - 2013) and so is ideal for studying animal movement [@Pettorelli2011]. In the past, migratory movement studies have often used spatio-temporal NDVI data. Other VIs, such as the Enhanced Vegetation Index (EVI), have been less commonly used [@Neumann2015a]. The EVI de-couples vegetation and canopy background and reduces influences of the atmosphere [@Huete2002] and is calculated by:

$$ EVI = \frac{2.5\times(NIR - RED)}{(NIR + 6.0\times RED - 7.5\times BLUE + 1.0)}$$

MODIS NDVI & EVI layers and respective quality layers for the entire study area and time span of our movement data were derived from the MOD13Q1 and MYD13Q1 V006 products, which were downloaded from the Land Processes Distributed Active Archive Center (http://lpdaac.usgs.gov/) using the `MODIS` package [@Mattiuzzi2016]. The vegetation index layers were filtered by the quality layer to remove unreliable pixel values. MOD13Q1 and MYD13Q1 products provide 16-day composites, which are shifted in time, at a moderate spatial resolution of 250 m. The two products were combined to increase the temporal resolution, which resulting in 8-day layers for each index from October 2007 to June 2009. 

MODIS MOD09A1 and MYD09A1 V006 surface reflectance layers (7 bands = RED, NIR, BLUE, GREEN, NIR2, shortwave infrared 1 (SWIR1), SWIR2) were obtained in order to derived additional VIs. The data was pre-processed using the same procedure as for the MODIS MOD13Q1 and MYD13Q1 products. The temporal resolution of these two products is twice as high, but the spatial resolution is only half as good. This resulted in 146 layers for each band with a temporal resolution of 4 days and a spatial resolution of 500 m. NDVI and EVI were then calculated using the above mentioned equations, in order to compare the effect of the two different resolutions.

From the surface reflectance layers the Normalised Difference Moisture Index (NDMI) [@Jin2005] was calculated by:

$$ NDMI = \frac{(NIR - SWIR1)}{(NIR + SWIR1)}$$

The different bands were further used to calculate the Normalised Difference Water Index (NDWI~McF~) [@McFeeters1996]:

$$ NDWI_{McF} = \frac{(GREEN - NIR)}{(GREEN + NIR)}$$

The Modified Normalised Difference Water Index (NDWI~Xu~) was calculated following the procedure by @Xu2006a:

$$ NDWI_{Xu} = \frac{(GREEN - SWIR1)}{(GREEN + SWIR1)}$$

Two different versions of the automated water extraction index (AWEI~ns~, AWEI~sh~) were also calculated:

$$ AWEI_{ns} = 4\times(GREEN - SWIR1) - (0.25\times NIR + 2.75\times SWIR2)$$
$$ AWEI_{sh} = BLUE + 2.5\times GREEN - 1.5\times(NIR + SWIR1) - (0.25\times SWIR2)$$

AWEI~sh~ is ideally used in situations where shadows are a major source of accuracy loss, while AWEI~ns~ is proposed for areas where shadows are not a major problem, but surfaces such as snow, ice and high albedo built surfaces are present. In areas where no shadow, no dark urban backgrounds and no high-albedo surfaces occur, either of the two can be used [@Feyisa2014].
And finally the 2015 water index (WI~2015~) [@Fisher2016] was calculated:

$$ WI_{2015} = 1.7204 + 171\times GREEN + 3\times RED - 70\times NIR - 45\times SWIR1 - 71\times SWIR2$$

All seven bands were further used to apply the tasseled cap transformation. This transformation provides a way of reducing the data dimensionality and outputs six new bands, of which the first three usually account for most of the variation [@Crist1984]. These first three bands are commonly labeled as brightness, greenness and wetness and were used as additional VIs. Brightness highlights surfaces with little or no vegetation. Greenness is defined by enhanced absorption of the visible spectrum and high reflectance in infrared. Wetness has been shown to be sensitive to soil and plant moisture [@Crist1984] and vegetation structure [@Jin2005; @Vorovencii2007].

Surface reflectance Landsat 5 Thematic Mapper (TM) and Landsat 7 Enhanced Thematic Mapper Plus (ETM+) images consisting of 6 different bands (BLUE, GREEN, RED, NIR, SWIR1 and SWIR2) were downloaded for the entire study area and time span from EarthExplorer (http://earthexplorer.usgs.gov/). Landsat TM and ETM+ imagery provide freely-accessible high resolution (30 m) data. A mosaick of 5 different scenes, recorded within less than 10 days from each other, was used to cover the entire study area. Landsat images are generally available at a 16-day interval, however surface reflectance images were not available for every time step and so images were only available for irregular time intervals. In total, 54 Landsat 5 TM and 104 Landsat 7 ETM+ scenes were processed resulting in 43 temporal layers. Topographic illumination correction was applied to each image using the NASA Shuttle Radar Trans Mission (SRTM) Global V003 elevation data at a resolution of 30 meters [@NASAJPL2013]. Afterwards, clouds, shadows and adjacent clouds were masked from each image. The mosaicked images were used to calculate the same indices as for the MODIS MOD09A1 and MYD09A1 V006 reflectance data. During the time of the study the LSC-correction of the Landsat 7 ETM+ scenes was switched off, resulting in obscured images. To obtain complete VI scenes at a regular time interval, monthly mean images were calculated and only these were used for further analysis.

SRTM elevation data for the study area was obtained from the NASA Land Processes Distributed Active Archive Center (http://gdex.cr.usgs.gov/gdex/) [@NASAJPL2013]. In addition to topographic illumination correction the elevation data was used to calculate slope and aspect (direction of slope) for each pixel using its eight neighbouring cells [@Horn1981] (Fig. S2).

The annual MODIS Land Cover Type (MCD12Q1 V006) product at a resolution of 500 m was obtained for the entire study area and time span that it is available (2001 - 2013) (Fig. S5). The International Geosphere Biosphere Programme (IGBP) scheme was used, which provides 17 different land cover classes. It is derived through supervised decision-tree classifications using 1370 training sites and has a global accuracy of 75 % [@Cohen2006].

### Movement Analysis

<!--
Movement data was cleaned by removing all locations that were missing one of the two coordinates. Variation in speed and direction over time and between individuals was assessed visually (Fig. \ref{fig:speed_bwa}, \ref{fig:time_speed_bwa}, \ref{fig:speed_hour_bwa}, \ref{fig:speed_month_bwa}, \ref{fig:angle_polar_bwa}). Maps of the movement paths of each individual (Fig. \ref{fig:zebra_individual_bwa}) and maps of the monthly point locations were created (Fig. S8). 
-->

Movement data was categorised into seasons (Fig. S6). Months where precipitation was below the temperature curve, were defined as dry season (April - December), while months with higher precipitation than temperature were defined as rainy season (December - April) (Fig. S1).

Migration is often defined based on the distance travelled, e.g. if the animal is covering a distance which is greater than the daily average [@Cagnacci2016]. Movement data were divided into 4 segments: Southern migration, Northern migration, Southern Range, Northern Range. To define the southern migration, the mean location of all individuals between 20^th^ and 31^st^ October was calculated as a start point and the mean location of all individuals between 25^th^ - 30^th^ November was calculated as end point. These dates were based on the findings of @Bartlam-Brooks2013. For each individual the time when the individual was more than 25 km away from the start point after the 20^th^ of October was derived and used as start of the southern migration. The end of the southern migration was determined as the date when the individual was less than 5 km or the minimum distance away from the end point of the migration. For the northern migration the start point was calculated as the mean location of all individuals between the 1^st^ of March and the 1^st^ of April and the end point was calculated as the mean location between 1^st^ of June and 1^st^ of July. To start their northern migration zebras had to be more than 25 km away from the start point and to end their northern migration they had to be closer than 5km to the end point otherwise the time when the came closest to the end point was used (Table 4). Movement points in between the northern and southern migration were classified into southern or northern range accordingly (Fig. S9).

![](Figures/Angle_Dist_BWA.png)
**Fig. 2.** Histogram of the step length and turning angle of the zebra movement data of Botswana. Exponential (red), lognormal (blue) and halfnormal (green) distribution were fitted to the step length. A van Mises distribution was fitted to the turning angle.

The mean location of the previously defined start and end points of migration were used as departure and destination points. From these we derived a distance to point raster layer at a resolution of 30 m (Fig. S3). The goal layer was used in our step selection function models to avoid autocorrelation due to the migratory behaviour of our zebras.

Autocorrelation of our data was assessed by fitting a variogram for each individual using the `ctmm` package (Fig. S7) [@Fleming2016]. From this we decided to thin our data to a 3 hour interval in order to avoid correlation among subsequent steps. The distribution in step length, the straight line distance between successive locations, and turning angle, the angle subtended by two successive steps, were assessed by fitting various distributions (Fig. \ref{fig:angle_dist_bwa}). A half-normal distribution corresponded best with the step length. 

In order to simulate locations, where zebras did not go but theoretically could have gone, 100 absence points were randomly sampled for every 3 hourly movement step of each individual (Fig. S10) from a half-normal distribution with twice the maximum step length for the steps and a radially symmetric proposal distribution for the turning angle. This resulted in a total of 1100698 points (1089800 absence points, 10898 presence points). 

For each absence and presence point the altitude, slope, aspect and the distance to goal was extracted. For the satellite data (Landsat, M.D09, M.D13), the points that were falling within the corresponding time interval (4 days, 8 days, 1 month) were selected and the values of the calculated indices for the specific time and coordinates were extracted. In total, we ended up with 28 explanatory variables. The Pearson pairwise correlation of these variables was assessed (Fig. S11) and all model combinations of uncorrelated explanatory variables (r < 0.7) were derived (Table S3). 

SSFs offer a way to analyse the interaction of an animal's movement with the environment it encouters. It is composed of a resource-independent movement kernel and a resource selection function (RSF) [@Forester2009]. Selection is defined as use or non-use of a resource unit when encountered. SSFs were fitted using logistic regression with the cosine of the turning angle and the id of each absence and presence step sequence as explanatory variables. 

The variable importance was assessed by fitting SSFs for all model combinations and each individual separately. The mean AIC among individuals was calculated for each model and the model with the best fit, indicated by the model with the lowest Akaike Information Criteria (AIC), was kept (Table S4). Model selection of the remaining model was done by stepwise backward selection, where one by one the least significant variable was dropped until only significant (p < 0.05) variables remain.

<!--
Note: No interaction terms are needed for clogit. I did not test for autocorrelation in the residuals. Cross-validation is still missing. R2 values and coefficients are not mentioned. 
Note: We need to consider species cannot jump from one location to the next but has to be close-by (i.e. altitude example from Björn)

All analyses were performed in R version 3.3.3 [@RCoreTeam2016}, using mainly the R packages `raster` [@Hijmans2016a], `rgdal` [@Bivand2016a], `rgeos` [@Bivand2016a], `RStoolbox` [@Leutner2016], `move` [@Kranstauber2016a] and `ctmm` [@Fleming2016].
-->

## Results

### Vegetation changes

<!--
NDVI showed a highly seasonal pattern (Fig. \ref{fig:ndvi_1yr_mn_bwa}). Looking at the trend in NDVI, 
-->

35.5 % of the study area, in particular the south-eastern corner, showed a significant increase in NDVI over the last 33 years (1981 - 2013). The slope in NDVI only varied between -5.84759e-06 and 8.478647e-06. High adjusted R^2^ values coincided with high slope values, but again adjusted R^2^ was not very high (0 - 0.15, Fig. 3).

![](Figures/Gimms_NDVI_BWA.png)
**Fig. 3.** Slope and adjusted R^2^ of the GIMMS NDVI3g time series for the study area in Botswana. Green lines indicate outline of protected areas and the surrounding 5 km buffer.

86.9 - 91.1 % of the study area was covered by savannas. The remainder was mostly covered by open shrublands (4.3 - 8.6 %) or barren or sparsely vegetated surfaces (3.6 - 3.9 %). The cover of savannas dropped by 4 % from 2008 - 2009, while open shrublands increased by 4 % (Table S2).

From 2001 to 2013 we observed a slight drop in savanna areas and a slight increase in open shrublands, but otherwise land cover appeared to be fairly stable (Fig. 4, Fig. S5).

![](Figures/MLC_Timeseries_BWA.png)
**Fig. 4.** Coverage of each land cover class from 2001 - 2013 for the study area in Botswana.

The study area is covered by seven PAs, which cover 52.2 % of the entire study area. The 5 km buffer zones around the PAs covered 8.8 % of the study area. Five PAs are formally protected, that means the fall within one of the six IUCN protected area management categories [@Dudley2008]. Six PAs have been designated many years ago (1963 - 1996). The Moremi Game Reserve, an exclusive area for wildlife and wilderness conservation, has already been established in 1963, while the Okavango Delta World Heritage Site has only been inscribed in 2014 and is not designated yet. The older protected areas are generally small in size, but have a high conservation priority, while the newer protected areas cover a larger area, but have a lower designation status (Table 2). 

**Table 2.** Summary of the Protected Areas of the study area.


----------------------------------------------------------------------------------
        Name                Designation         IUCN Category   Area (km2)   Year 
--------------------- ------------------------ --------------- ------------ ------
        Maun               Game Sanctuary            IV             85       1975 

        Chobe              National Park             Ib        1.100000e+04  1968 

      Nxai Pan             National Park             Ib            2576      1971 

       Moremi               Game Reserve             Ib            4871      1963 

  Makgadikgadi Pans        National Park             Ib            4902      1992 

Okavango Delta System Ramsar Site, Wetland of   Not Reported   5.537400e+04  1996 
                      International Importance                                    

   Okavango Delta       World Heritage Site    Not Applicable  2.023590e+04  2014 
----------------------------------------------------------------------------------

The Okavango Delta System Ramsar Site actually encompasses the Okavango Delta World Heritage Site, the Maun Game Sanctuary and the Moremi Game Reserve, while the Moremi Game Reserve is also covered by the Okavango Delta World Heritage Site. Hence, there is a significant overlap in protected areas within the study area.

![](Figures/Gimms_Status_NDVI_BWA.png)
**Fig. 5.** Adjusted R^2^ and Slope of the GIMMS NDVI3g time series for each protection status (protected, unprotected and 5 km buffer zone of the study area in Botswana.

Overall, NDVI increased over the last 33 years (1981 - 2013) in each zone. The increase in NDVI was most pronounced and had a stronger fit in protected areas, compared to the buffer zone or unprotected areas (Fig. 5).

The mean percentage land cover of protected and non-protected areas during the time of the study showed that most protected areas are nearly entirely covered by savannas, apart from the Makgadikgadi Pans, which have an especially high proportion of woody savannas (17.6 %) and of barren or sparsely vegetated ground (4.4 %). The non-protected areas also have a lower coverage of savannas (86 %) and similar to the Makgadikgadi Pans have a higher proportion of woody savannas (8.3 %) and barren or sparsely vegetated areas (1.7 %) (Table 3).

**Table 3.** Percentage of land cover for protected and non-protected areas.


--------------------------------------------------------------------------------------------------------------------------------------------
           &nbsp;             Chobe   Makgadikgadi Pans   Maun   Moremi   Nxai Pan   Okavango Delta   Okavango Delta System   Non-protected 
---------------------------- ------- ------------------- ------ -------- ---------- ---------------- ----------------------- ---------------
Barren or sparsely vegetated    -             4            -       -        0.05           -                    -                   2       

     Closed shrublands          -             -            -       -         -             -                    -                   0       

Cropland/Natural vegetation     -             1            -       -        0.09           -                    -                  0.6      
           mosaic                                                                                                                           

         Croplands              -             1            -      0.01      0.08          0.01                  0                  0.3      

         Grasslands            0.2            2            -       3        0.1            2                   0.9                 0.3      

      Open shrublands           -            0.4           -       -         -            0.01                  0                  0.6      

     Permanent wetlands         -             1            -      0.5       0.09          0.3                  0.1                 0.2      

          Savannas             98            69            96      95        95            97                  98                  86       

        Snow and ice            -             2            -       -        0.06           -                    -                   1       

     Urban and built-up         -             1            4       -        0.09           -                   0.1                 0.6      

       Woody savannas           2            18           0.07     1         4            0.7                  0.4                  8       
--------------------------------------------------------------------------------------------------------------------------------------------

### Migratory patterns

In total, zebras were tracked for 1630 days. Tracking duration varied between 72 - 364 days for each individual and on average zebras were tracked for 233 days. Total tracking distance varied between 1124 - 4087 km and on average zebras travelled 2878.40 km ($\pm$ 1014.34 SD) (Table 1). The mean movement rate per zebra varied from 0.13 - 0.19 m/s. Mean step length was 394.82 m ($\pm$ 60.45 SD) and mean direction varied between 2.2 and 6.8°. 

All of the seven plains zebras migrated from the Okavango Delta in the northwest to the Makgadikgadi grasslands in the southeast of Botswana (Fig 6). From June until October they resided in the north-western part of the study area, in October/November they migrated to the Makgadikgadi Pans, where they stayed until April/May when they started moving back to the Okavango Delta (Fig. S8).

![](Figures/Zebra_BWA_Overview.png)
**Fig. 6.** Map of study area in Botswana with movement tracks colour-coded by individual. Protected areas are depicted in lightgreen and their name is stated. Dashed brown line indicates pathway of fence running through the study area.

All individuals migrated south, but one zebra (Z3864) was not tracked for long enough to record its northwards migration. Southern migration started around the beginning of November and lasted for 10 - 36 days. The average southern migration distance was 443.65 km. The start of the northern migration varied among invidiuals and years. In 2008 one individual started to migrate on the 10^th^ of May and took 11 days, the other individual started no the 9^th^ of March and took 84 days. In 2009, one individual started at the beginning of March and three individuals at the end of March and lasted for 20 - 61 days. Mean northern migration distance was 555.56 km (Table 4).

**Table 4.** Summary of migration (direction, start and end date and duration) for each individual.


---------------------------------------------------------------------------
 ID    Direction   Start Date   End Date   Duration (days)   Distance (km) 
----- ----------- ------------ ---------- ----------------- ---------------
Z3864    South     2007-10-25  2007-11-30        36              695.1     

Z3743    South     2007-10-30  2007-11-25        26              760.6     

Z3866    South     2007-11-01  2007-11-30        29              485.4     

Z6402    South     2008-11-05  2008-11-20        14              322.5     

Z6405    South     2008-11-05  2008-11-15        10              239.3     

Z6407    South     2008-11-05  2008-11-16        11              297.4     

Z6399    South     2008-11-01  2008-11-16        15              305.2     

Z3684    North         -           -              -                -       

Z3743    North     2008-05-10  2008-05-21        11              224.2     

Z3866    North     2008-03-09  2008-05-31        84              1047      

Z6402    North     2009-03-31  2009-04-20        20               214      

Z6405    North     2009-03-01  2009-03-25        24              303.8     

Z6407    North     2009-03-26  2009-05-25        60              745.4     

Z6399    North     2009-03-29  2009-05-29        61              799.1     
---------------------------------------------------------------------------

Average movement rate was higher during migration (0.22 m/s $\pm$ 0.28 SD) compared to residency times (0.13 m/s $\pm$ 0.18 SD), while mean absolute turning angle was lower during migration (55.24° $\pm$ 51.30 SD) compared to residency times (60.71° $\pm$ 50.91 SD) (Fig. 7).

![](Figures/State_Move_BWA.png)
**Fig. 7.** Absolute turning angle ($^\circ$) and speed (m/s) for each migration state (Northern Range, Southern Migration, Southern Range and Northern Migration).

Zebras experienced a distinctive difference in altitude throughout their migration (Fig. 8). In their northern range zebras exprienced a mean altitude of 944.69 m ($\pm$ 4.88 SD), while in their southern range zebras experienced an elevation of 906.58 m ($\pm$ 4.56 SD).

![](Figures/Zebra_dem_BWA.png)
**Fig. 8.** Altitude over time experienced by each individual zebra in Botswana.

During migration and residence in the Makgadikgadi Pans zebras experienced a lower NDVI compared to their residence in the Okavango Delta (Fig. 9).

![](Figures/Zebra_ndvi_BWA.png)
**Fig. 9.** NDVI over time experienced by each individual zebra in Botswana.

### Zebra habitat selection

Most of the 28 potential explanatory variables were highly correlated among each other. NDVI and EVI obtained from MODIS MOD13Q1 and MYD13Q1 products (NDVI and EVI) were correlated with the NDVI and EVI derived from MODIS MOD09A1 and MYD09A1 surface reflectance layers (ndvi and evi). Apart from Landsat ndwi~mcf~ none of the Landsat indices was correlated with lower resolution indices. Slope, aspect, distance to goal, brightness and Landsat derived EVI (LS~evi~) were the only variables that were not correlated with any other variable (Fig. S11). 

In total, there were 19 different combinations of uncorrelated explanatory variables, which were used as initial models (Table S3).

The best model (lowest AIC) varied among individals. M2 was the best model for Z3743, Z6405 & Z6407. M3 was the best model for Z3866, M8 the best model for Z6402 & Z6399 and M15 the best model for Z3864. Overall, the best model was M2. M2 included 9 explanatory variables (aspect, awei~ns~, brightness, goal, LS~evi~, LS~ndmi~, LS~ndvi~, ndmi, ndvi and slope) (Table S4).

Aspect and LS~evi~ were removed through stepwise backward selection for every individual. LS~ndvi~ and ndvi showed a significant effect across all individual models (n=7). Brightness was significant for all but one individual and awei~ns~ was significant for 5 individuals. The remaining variables were significant for only some individuals (Table 5).

**Table 5.** p-Values for each component of the final model and each individual.


----------------------------------------------------------------------------
   Variable     Z3864   Z3743    Z3866    Z6402    Z6405    Z6407    Z6399  
-------------- ------- -------- -------- -------- -------- -------- --------
cos(rel.angle)    0       0        0        0        0        0        0    

  brightness   0.00227    0     9.7e-06  0.00163   0.0115     0        -    

   LS_ndvi     1.6e-07 0.000792 5.77e-15 4.43e-07 1.42e-05 3.43e-06 8.84e-13

     ndvi      0.0112     0        0     5.52e-11    0        0     6.54e-11

   awei_ns        -       0     6.66e-16 8.37e-07 0.000781    0        -    

    slope         -     0.0484     -     6.33e-05    -        -        -    

     goal         -       -     7.8e-10     -        -      0.0191     -    

   LS_ndmi        -       -     0.000235 0.00111     -     0.00135  1.07e-06

     ndmi         -       -        -        -     3.24e-05    -     1.03e-08
----------------------------------------------------------------------------

## Discussion

Africa's rapidly growing population leads to increasing agricultural production and mineral exports. Several development corridors have been proposed in sub-Saharan Africa to expand infrastructure, such as roads, railroads, pipelines and port facilities, and so increase the access to new land. As a consequence the environment is being altered at an explosive rate, which severely degrades African ecosystems and wildlife [@Laurance2015]. 

There was a significant increase in NDVI, which is a proxy for vegetation, in some parts of the study area from 1981 to 2013. But, the increase in NDVI was very low, which indicates a more or less steady-state in long-term vegetation trends (Fig. 3). 

The majority of the study area was covered by savannas (Table \ref{table:mlc_percentage_BWA}). Savannas have been used by humans for many centuries, but intensive cattle production and arid-land farming has put increasing pressure on this ecosystem in recent years. This has led to soil erosion and desertification and threatens endangered species, such as elephants and rhinos [@Young1997a]. Savannas are among the ecosystems that are most sensitive to future land use and climate change [@DeKnegt2008]. From 2001 to 2013 a slight decrease in savanna and an increase in open shrublands was observed (Figs. \ref{fig:mlc_ts_bwa} and S5). This could be due to an  increas in land use in the area. Land use in Ngamiland strongly depends on the availability of water, soil and rangeland quality, the distribution of wildlife, the occurrence of plants poisonous to cattle and in the past also on the presence of vector-borne diseases [@Kgathi2014].

More than half of the study area was covered by PAs. PAs are the key tool for protecting biodiversity, but not all PAs are effective and they can have negative impacts on local communities [@Oldekop2015]. For example, the Moremi Game Reserve, the oldest PA within our study area, led to the removal and resettlement of indigenous communities that historically inhabited the area [@Kgathi2014]. Game reserves and national parks account for 6.4 % of the tribal land in Ngamiland, including Moremi Game Reserve and Nxai Pan National Park. While national parks protect the land and its natural resources, game reserves legally only protect the animals and not the land. However, in practice game reserves are given the same treatment as national parks in Botswana [@Kgathi2014]. Global spatial data on protected area coverage, such as the WDPA, can suffer from spatial inaccuracies and lack sufficient spatial and thematic detail for effective monitoring of single protected areas or even regional park networks [@Chape2005; @Nagendra2013]. 

The areas with the highest increase in vegetation were found within Makgadikadi Pans Nationalpark (Fig. 3). NDVI also showed a higher increase and stronger fit in protected areas, compared to the buffer zone or unprotected areas (Fig. 5). This indicates that the protected areas are indeed effective in conserving the ecosystems within them. AVHRR long-term time series provide a unique possibility to monitor land-cover dynamics of PAs [@Wegmann2014], but the resolution of AVHRR is coarse. Semi-arid savannas show patchy distributions at the meter scale [@Kgathi2014], so most dynamics in savannas have probably been overlooked.

Plains zebras can be sedentary or migratory. Sedentary populations typically have a high density and small home range, while migratory populations have low densities. Unfortunately, only data from migratory plains zebras in this region was available.

Zebras migrated from the southeastern Okavango Delta to the Makgadikgadi grasslands (Figs. \ref{fig:zebra_overview_bwa} and S9). Southern migration started around the beginning of November, which corresponds to the results of @Bartlam-Brooks2013, who found that migration started between 27th October and 5th November, while northern migration was from end of March till the end of May. 

Zebras stayed at the Makgadikgadi grasslands only during the wet season, as then the grasslands are hospitable to them and water is temporarily available. NDVI was higher in the Okavango Delta both in the dry and wet season (Fig. S6) and zebras experienced a lower NDVI in the Makgadikgadi grasslands compared to the Okavango Delta (Fig. \ref{fig:zebra_ndvi_bwa}). This explains, why the majority of zebras do not migrate, but reside in the Okavango Delta permanently [@Bartlam-Brooks2013]. It also indicates that the migration is not driven by seasonal resource limitation, but rather by the high nutritional value of the Makgadikgadi grasslands [@Baillieul1979].

The Okavango Delta is much higher in altitude than the Makgadikgadi Pans (Fig. S2). This is also reflected in the altitude the zebras experienced over time (Fig. \ref{fig:dem_bwa}). This suggests that it would be possible to classify our animal trajectories based on changes in habitat use (altitude), which has been recently proposed by @vanToor2016.

The average migration distance was 495.3 km (Table 4). However, we calculated the total distance moved by the animal rather than just the overall distance between start and end location of the migration. The overall distance between the Okavango Delta and the Makgadikgadi Pans is approximately 250 km, which corresponds to the migration distance found in the literature [@Bartlam-Brooks2013].

Zebras generally moved faster and with a lower turning angle during migration compared to residency times (Fig. \ref{fig:state_move_bwa}). @Bartlam-Brooks2013 found that zebras decrease their migration speed with increasing NDVI and that they can even adapt their time of arrival at the migration destination according to the peak in NDVI. Arrival timing at breeding sites determines the reproductive success of an individual and so influences population and ecosystem dynamics, which has implications for management and conservation [@Tibblin2016].

Movement data derived from GPS collars can contain two types of errors, missing location fixes and location errors of successful acquired fixes [@Bjorneraas2010]. Location errors can occur when the accuracy of fixes does not provide a correspondingly accurate measure of the animal’s natural behavior. @Brooks2008a studied the effect of collar weight and fit on the rate of travel of female plains zebras in the Makgadikgadi Pans. Collar effect was activity specific and less pronounced when animals cross large interpatch distances, for example during migration, but strongly interfered with grazing behaviour. Heavier collars (0.6 % of total body mass) reduced the rate of travel by more than 50 % when foraging compared with the collar that was 0.4 % of the total body mass. The collars which were used to derive the movement data of this study weighed < 0.3 % of the total body weight [@Bartlam-Brooks2013], and so are unlikely to have an effect.

The migratory route of all zebras ran closely along the fence, which is running through parts of the study area (Fig. \ref{fig:zebra_overview_bwa}). This suggests that the migration of zebras, similar to African buffalo and African savannah elephant [@Loarie2009a], is affected by the presence of barriers. From 1968 - 2004 the migration of plains zebras was blocked completely by a fence, but within 3 years the original migration route was re-established [@Bartlam-Brooks2011]. Many fences have been erected in the area, mostly to prevent the spread of food and mouth disease from wildlife to cattle. These fences resulted in the entanglement and killing of many animals, as they were often erected across established wildlife migratory routes [@Perkins1996; @Kgathi2014]. Digital maps of barriers, such as fences, human settlements or agricultural areas, can be derived from land cover data and aerial photos, but this has been rarely done in the past [@Neumann2015a].

Migration routes followed a narrow corridor (Fig. \ref{fig:zebra_overview_bwa}), indicating that zebras follow along a traditional route, which would indicate a migration corridor [@Berger2004]. However, most individuals were tracked for less than one year, so it is not clear if zebras follow the same route over multiple years or if it is resource driven. Only the north-western and south-eastern part of the study area are protected, but the migration corridor, which would connect the two areas, is not (Fig. \ref{fig:zebra_overview_bwa}). Traditional conservation efforts have often focused on protecting seasonal ranges, but have less often considered migration corridors. A more detailed understanding of the drivers of migration pathways will help us to protect the migration of zebras in the future.

Migratory animals have large area requirements and so are much more likely to be affected by modifications of the natural landscape, due to climate or land use change, than non-migratory species [@Berger2004; @Bolger2008; @Wilcove2008]. Habitat selection can influence the survival and life-time reproductive success of individuals [@Makelainen2016]. Hence, it is particularly important to understand the drivers of animal migrations in order to conserve them.

RSFs are commonly used to quantify habitat selection, by comparing habitat attributes in sites used by the animals compared to unused, but available sites. We took the extent of our movement data plus a 5 % buffer as available habitat (Fig. \ref{fig:zebra_overview_bwa}). Defining areas as available habitat implies that animals know about this availabiilty and move accordingly. The way of defining available habitat, thus criticially alters the results [@Freitas2008a]. 

Using spatio-temporal environmental information to model animal movement can help to identify decision rules, orientation and navigation mechanisms, as well as the effects of environmental heterogeneity [@Bartlam-Brooks2013]. In this study, spatio-temporal information from 11 different indices with various resolutions (30, 250 and 500 m) and terrain data (altitude, aspect and slope) were considered (Fig. S2). Previous studies have often used vegetation phenology data (NDVI) from multiple dates. Sometimes they were combined with climate, weather and terrain data, but rarely multiple indices have been considered [@Neumann2015a].

Most of the indices were highly correlated among each other (Fig. S11). As was previously shown, NDMI is correlated with wetness [@Jin2005] and greenness is highly correlated with EVI [@Zhang2002].
Spatial autocorrelation is inherent in any form of animal movement data [@Fleming2015a]. The autocorrelation of our data was assessed using variograms (Fig. S6) and our data was split in three hour intervals to overcome this effect. Some spatial autocorrelation might still have been present in the data underlying our models, which could have been removed by coarsening our data even more. But, coarsening the data introduces a strong bias, as only the use of a location, but not the amount of time an individual spends at this location is taken into account [@Lele2013].

SSFs showed that LS~ndvi~ and ndvi were a significant driver in habitat use for each individual. Brightness, awei~ns~, LS~ndmi~, ndmi and slope were also significant for some individuals (Table 5). This confirms that slope and access to water can constrain grazing use of some areas, as has been shown previously [@Bailey1996a], but also again highlights the utility of NDVI as proxy for vegetation patterning [@Pettorelli2011]. NDVI does not only influence migration distance [@Teitelbaum2015], but can also be used to trace step-wise habitat choices of single individuals. Global long-term changes in NDVI may thus force animals to alter the distance, timing and route of their migrations. 

Landsat imagery added another source of environmental information in addition to MODIS data and vice versa. This highlights the importance of Landsat imagery for monitoring vegetation structure and habitat changes on a regional level [@Nagendra2013; @Willis2015], but also shows the importance of medium resolution data to depict large scale vegetation patterns. Coarse and medium resolution data might provide daily observations, but without a suitable spatial resolution for Global Positioning System (GPS) collar-based movement data. Very high resolution data (i.e. SPOT imagery) did not show substantial improvements over Landsat for land cover mapping in Botswana, as dry semi-arid vegetated areas tend to show a lack of near infrared reflectance [@Kgathi2014].

RSFs are commonly used to quantify the habitat use of animal's from movement data in order to derive conservation corridors. But, if the animal's behavioural state is not considered, RSFs may lead to the misallocation of wildlife corridors [@Abrahms2016]. Memory is another often neglected factor that shapes animal movement patterns and SSFs that incorporate spatial memory can improve the estimates of habitat selection [@Oliveira-Santos2016]. In this study no model validation was applied, so the reliability of the outcome is questionable. @Boyce2002 suggested to use k-fold cross validation for evaluating RSF model predictions, in particular for studies with one intensive period of data collection at one location. 

Conservation of animal movement is challenging, as it often means putting large areas under protection and so in conflict with human use [@Thirgood2004]. Migratory species require adequate amounts of both breeding and non-breeding habitat to maintain viable populations and travel routes need to be free of barriers, so animals can move to and from breeding grounds. 

Global habitat degradation and fragmentation calls for increasing attention to identify landscape features that support (corridors) or impede (barriers) animal movement [@Panzacchi2016]. Conservation corridors help to improve the connectivity of vegetation patches. Habitat connectivity allows species to extend their occurrence distribution, which helps to achieve population persistence, but the functional habitat connectivity will vary considerably among species [@Barton2015].

Nevertheless, given the importance and high threat of migratory species, conservation actions need to be spatially prioiritised to fulfill the needs of migratory species [@Barton2015]. Some of the movement behaviours of ungulates have been identified in the past, while others are complex and difficult to protect with generic conservation solutions [@Berger2004; @Wilcove2008]. This puts the partially protected and poorly understood ungulate populations under continued pressure [@Olson2010].

# Occurrence distribution and habitat use of Grevy’s and plains zebras

## Abstract

Ungulate populations are declining inside as well as outside protected areas across Africa. Protected areas often lack enforcement, which makes them highly ineffective and prone to land-use change. Small-scale daily movements of animals are likely to be affected by these changes and can influence predation rate or foraging success and so decrease their survival and reproduction capability. The movement of Grevy's and plains zebras was analysed by comparing their occurrence distributions, movement characteristics and habitat use. The effectiveness of protected areas and the protection coverage of zebra movement was further assessed. The entire study area experienced a significant increase in NDVI from 1981 - 2013 and an increase in savannas, woody savannas and cropland/natural vegetation mosaic was observed from 2011 - 2013. Grevy's zebras had a larger occurrence distribution than plains zebras, while plains zebras moved faster compared to Grevy's zebras. Overlap between occurrence distributions among the two species was low (27.23 %). The two species experienced different NDVI and EVI values per month, while both occurred at similar land cover. This shows that land cover is not as suitable as vegetation indices for detecting small-scale differences in resource use among species, however high resolution land-cover products might provide a suitable alternative. Laikipia is lacking areas which are formally protected and only 26 % of animal-defined corridors fell within PAs. In order to enhance animal movement conservation  corridors should ideally be based on the habitat selection and movement of the organism. 

**Keywords:** remote sensing, animal movement, protected areas, conservation, habitat use, land cover, autocorrelated kernel density estimation, plains zebras, Grevy's zebras, Laikipia, Kenya

## Introduction

In the past, research on animal movement has been primarily looking at the movement behaviour of individual animals [@Nathan2008] and less at population level movement [@Mueller2011]. Studying the underlying mechanisms of the movement of individuals forms the baseline for understanding the population dynamics [@Mueller2008]. This is detrimental in order to predict the influence of anthropogenic environmental change on species' distribution and to come up with conservation strategies [@Demsar2015].

Kenya currently has 23 terrestrial national parks and 26 nature reserves, which together cover 8 % of the total land surface. Kenya's PAs only cover parts of the migratory range of large herbivores and also vary in the protection of dry and wet season ranges of migratory species, such as wildebeest and zebra. Ungulate populations have been found to decline inside as well as outside of PAs across Africa and especially within Kenya, where there has been a sharp decline over the last 30 years [@Western2009]. 

PAs are intended to conserve habitats and species, but the effectiveness of East African PAs varies among protection status [@Pfeifer2012] and size. Generally, small reserves are less efficient in conserving species than large ones. Faunal communities within reserves might experience species depletion if reserves are small in size or isolated from surrounding natural habitat [@Miller1977]. In Kenya, larger parks lack enforcement and so are subject to land cover changes and poaching, which makes them highly ineffective in conserving ungulate species [@Western2009]. But, @Hoffmann2015 found that if conservation efforts would have ceased in 1996 at least 148 species of the 235 recognized ungulate species in the world would have deteriorated by one IUCN Red List category compared to their status in 2008. Furthermore, six of these species would now be listed as extinct or extinct in the wild.

Not only migratory routes are influenced by anthropogenic environmental change, but also small-scale, daily movements can be affected by human infrastructure and land-use change [@Panzacchi2016]. The movement of an animal is driven by the suitability of an area for a particular activity, such as feeding, resting, mating, raising newborns and escaping predators [@Panzacchi2016]. Habitat loss can restrict the movement of an animal and so reduce its breeding and dispersal success as well as its predation rate or foraging success rate [@Fahrig2003] and so indirectly affects its survival and reproduction [@VandeKerk2015]. Thus, there is a strong interest in understanding the driving forces of animal space use and mitigating the effects of habitat fragmentation on animal movement for species' conservation [@Sundaresan2008; @Panzacchi2016]. 

Mammals in general are selective in their habitat use, while African savanna herbivores in particular track resources through space and time [@Bailey1996a]. The distribution and abundance of large grazing mammals are influenced by the seasonal and spatial variation in forage quality and the negatively related vegetation productivity and precipitation [@McNaughton1983; @McNaughton1985; @Breman1983]. Grazers preferentially forage on mineral-enriched grasses, which are particularly important during late-stage pregnancy, lactation, and the growth of young animals [@McNaughton1988, McNaughton1990]. Forage quality is also a better explanatory variable for mortality rates of African herbivores than resource abundance [@Fryxell1987; @Sinclair1985]. In African savannas, food availability changes with the season along a topograpical gradient. Non-migratory species tend to congregate on ridge tops in the wet season and as the dry season sets in, progressively move down the slopes [@Jarman1979]. Slope and distance to water were found to constrain the grazing use of some areas [@Bailey1996a]. Ungulates follow daily movement patterns between foraging sites and are usually active during most time of the day [@Schweiger2015]. Areas which are frequently visited by ungulates can be expected to contain important foraging resources. The movement of ungulates is not only driven by vegetation, but ungulates themselves are also major drivers of landscape dynamics [@McNaughton1979; @McNaughton1997; @DeKnegt2008; @DeJager2009], which can be beneficial to themselves [@Jones1994]. Grazing of ungulate herbivores influences the spatial distribution of food, cover, productivity and soil fertility. Selective foraging by ungulates can further influence plant community composition and nutrient cycling [@DeJager2009], which can contribute to plant regrowth potential [@McNaughton1983; @Coughenour1985]. Ungulates also affect the abundance and population dynamics of other species, ranging from herbivores [@Coughenour1991] to soil decomposers [@Wardle2004], which again have an impact on vegetation composition and structure.

In this chapter, the occurrence distribution, movement characteristics and habitat use of Grevy's and plains zebras will be analysed and the effectiveness of current protection measures will be addressed by answering the following questions:

* Has there been an increase or loss in vegetation over the last 30 years?
* What is the space use of Grevy's and plains zebras? 
* How well do the current PAs cover the space use of the two species?

## Materials and Methods  

### Study area  

The study area was delineated by the extent of our movement data plus a 5 % margin. It lies in the Laikipia district, Kenya, north-west of Mount Kenya and covers an area of 4120 km^2^ (Fig. 10). The study area is situated at an altitude of 1192 - 2104 meters (Fig. S13). The area is characterised by a semi-arid climate (Fig. S12). 

Monthly rainfall ranges from 23 mm in January to 128 mm in April. Total annual rainfall varies from 507 mm in the north to 1021 mm in the south. The mean annual rainfall of the study area is 680 mm (1960-1990, @Hijmans2005). The area usually experiences two rainy seasons (Fig. S12), which vary among years. 

Rainfall is unpredictable in terms of onset, duration and termination. Increasing population size and growing demand for irrigation water has led to a significant decline in river water. Water availability is the most limiting factor for agriculture and climate models predict an increase in variability of inter- and intra-annual precipitation for the future [@Ulrich2012].

Laikipia district is part of the Greater Ewaso ecosystem, a typical semi-arid savanna, which is broadly defined by the watershed of the Ewaso Ngiro River. It is largely unfenced, contains only 2 % of formally protected areas and consists to 39 % of commercial cattle ranches, 34 % of smallholder plots, 8.5 % government owned land, 7 % group ranches, 7 % forest reserves and 4.5 % urban areas [@Georgiadis2003; @Sundaresan2012; @Evans2016a]. The Laikipia district has a population density of 35 persons per km^2^ [@Ayeri2012]. 

Most of the land is used for large commercial livestock ranches [@Sundaresan2008; @Sundaresan2012] and so the majority of the area consists of undeveloped habitat. The provision of water from livestock dams within ranches supports large mammal communities. As a result, Laikipia hosts the only intact savanna mammal community outside a Kenyan national park and contains the second highest abundance of wildlife in Kenya, after Maasai Mara National Reserve [@Evans2016a]. Seventy-five mammal species and 400 bird species can be found in the region [@Shorrocks2014]. 

<!-- Look at [@Young1997] for description on soils. -->

### Grevy's and plains zebras

The grevy's zebra is a large-bodied (350 - 450 kg) grazing ungulate. It is the largest of the three *Equid* species. Once, the species ranged widely across the savannas of northern Kenya, Ethiopia and Somalia. Grevy's zebras have undergone a population decline of 75 % since the 1970s and currently only around 2500 individuals remain in northern Kenya and Ethiopia. Thus, they are listed as "Endangered" under the IUCN Red List of Species [@Moehlman2013]. Reasons for the population declined are habitat degradation, reduced access to waterholes and illegal killing [@Moehlman2002]. The last stronghold of Grevy's zebra is the Ewaso ecosystem in the Laikipia and Samburu districts of northern Kenya. They expanded their range into Laikipia in the beginning of the 1970s, but in this area their ecology has hardly been studied. In Laikipia, the population has grown during the last 12 years, while other parts of their range were lost. Speculated reasons for the population increase are better survival or increased immigration from other areas [@Moehlman2002; @Sundaresan2008; @Sundaresan2012]. 

![](Figures/Studyarea_KEN.png)

**Fig. 10.** Map of Kenya with the study area highlighted in red. District boundaries are shown by white dashed lines. The location of all cities with a population of more than 40000 people is shown and capital city is highlighted in orange. Administrative boundaries were obtained from http://www.gadm.org using the `raster` package [@Bivand2016a]. Locations of cities were obtained from the `maps` package [@Becker2016].

Grevy's zebras live on rangelands often shared by pastoral populations and are uniquely adapted to its arid environment. Generally, they can survive on low quality grass forage and go for several days without drinking. Females form unstable groups, moving among male territories, while bachelors wander. Depending on the reproductive state the forage quality and quantity and habitat openness of locations used varies significantly [@Sundaresan2008]. Lactating females must visit water daily [@Sundaresan2012], which results in partial segregation among females by reproductive state [@Sundaresan2007]. Lactating females, as well as bachelors, further prefer areas with green, short grass and medium-dense bush, which suggests that they need to access certain nutrients [@Sundaresan2008].

In Laikipia, Grevy's zebra co-occur with the closely related and more abundant plains zebra [@Sundaresan2012]. A detailed description of the plains zebra can be found in the preceeding chapter. They occur in more mesic areas than the other African equids, where water is available, in light woodland, open scrub, grassland, dambos and occasionally broken, hilly ground. Plains zebras show a preference for *Acacia* rather than *Commiphora* woodlands [@Grubb1981]. @Fischhoff2007a further found that plains zebras use more woodland habitat at night and if they use grassland they take sharper turns in order to avoid predation from lions. A modelling study on plains zebras in Laikipia district showed that population decline is faster during dry phases than recovery during wet phases and that they are particularly vulnerable to large variation in annual rainfall [@Georgiadis2003].

### Movement Data

Movement data of seven Grevy's zebras and two plains zebras was obtained from Movebank. Additional data from four adult plains zebras (females in 3 harems and 1 bachelor male) was provided by Ilya Fichhoff [@Fischhoff2007a] (Fig. 11). 

![](Figures/Zebra_KEN_Overview.png)

**Fig. 11.** Laikipia zebra movement tracks]{Map of study area with movement tracks colour-coded by individual. Protected areas are depicted in lightgreen.

The nine zebras from Movebank were tagged in June and July 2007 and their position was recorded every hour. The four additional plains zebras have been tracked every 8 minutes from the end of June until the beginning of July 2005. Altogether the dataset contained 37771 point locations from 13 different individuals (7 Grevy's and 6 plains zebras) and covered a total time span of 5 months (Table 6).

**Table 6.** Start and end date of the tracking period, tracking duration (days), total distance (km) and median time interval (min) of each individual zebra.


------------------------------------------------------------------------------------
 ID   Start date   End date   Duration (days)   Distance (km)   Time interval (min) 
---- ------------ ---------- ----------------- --------------- ---------------------
GZ1   2007-06-13  2007-09-09       87.93            617.6               60          

GZ2   2007-06-13  2008-01-04       204.6            1741                60          

GZ3   2007-06-14  2007-09-19       97.05            948.2               60          

GZ4   2007-06-14  2008-06-10       361.6            3450                60          

GZ5   2007-07-09  2007-08-11       32.54             194                60          

GZ6   2007-06-16  2007-07-23       36.79            290.9               60          

GZ7   2007-06-16  2007-10-25       131.2            789.3               60          

PZ1   2007-06-14  2007-07-09       24.82            247.2               60          

PZ2   2007-06-17  2007-12-08       173.9            1578                60          

PZ6   2005-06-24  2005-07-02       7.933            113.6                8          

PZ8   2005-06-24  2005-07-08       13.83            84.68                8          

PZ10  2005-06-24  2005-07-04       9.917             105                 8          

PZ14  2005-06-24  2005-06-27       3.019            41.55                8          
------------------------------------------------------------------------------------

### Environmental Data

GIMMS NDVI3g data was again used to assess the trend in NDVI for each pixel within our study area (Fig. 12), for a detailed description on the methodology see Chapter 1. The spatial extent of all protected areas within the study area was accessed through the World Database on Protected Areas (WDPA) at http://protectedplanet.net. Based on the PA boundary, three zones were differentiated: Protected, 5km Buffer (area outside a PA but less than 5 km from the PA boundary) and Unprotected (Fig. S4) and the trend in NDVI was compared for these three zones (Fig. 14).

MODIS MOD09A1 and MYD09A1 surface reflectance layers were used to calculate NDVI, EVI with a temporal resolution of 4 days and a spatial resolution of 500 m for the course of the study, using the following equations (Eqs. 1 & 2).

The annual MODIS Land Cover Type (MCD12Q1 V006) product at a resolution of 500 m was obtained for the entire study area and time span that it is available (2001 - 2013) (Fig. S16). The International Geosphere Biosphere Programme (IGBP) scheme was used, which provides 17 different land cover classes. It is derived through supervised decision-tree classifications using 1370 training sites and has a global accuracy of 75 % [@Cohen2006]. In addition, a land use map of Laikipia district, with 14 different land use classes, was obtained from Laikipia Wildlife Forum and cropped by the extent of the study area (Fig. S15).

### Movement Analysis

Movement data was cleaned by removing one duplicated data point, which was completely identical to the preceeding one. 

<!-- Movement data was categorised into seasons (Fig. \ref{fig:zebra_season_ken}). Seasons were defined based on precipitation timing and temperature changes. Months where precipitation was below the temperature curve, were defined as dry season (January - February, June - September), while months with higher precipitation than temperature were defined as rainy season (March - May, October - December) (Fig. \ref{fig:climograph_ken}).

Movement data was cleaned by removing all locations that were missing one of the two coordinates and by removing one duplicate, which was completely identical to its preceeding data point. Variation in step length and turning angle, (Fig. \ref{fig:angle_dist_ken}), speed (Fig. \ref{fig:speed_ken}, \ref{fig:time_speed_ken}, \ref{fig:speed_hour_ken}, \ref{fig:speed_month_ken}) and direction (Fig. \ref{fig:angle_polar_ken}), as well as the movement paths (Fig. 2, \ref{fig:zebra_individual_ken}, \ref{fig:zebra_month_ken}) were assessed visually.
-->

Autocorrelation in step length or turning angle was assessed visually using variograms (Fig. S17). Spatial autocorrelation is a source of biological information and can improve home range estimation [@DeSolla1999]. Taking autocorrelation into account, the occurrence distribution was estimated using the autocorrelated kernel density estimator (AKDE) within the `ctmm` package [@Fleming2016]. Accounting for autocorrelation is particular important for finely sampled data to avoid under-estimation of home range sizes [@Fleming2015a], which is the case here. The range overlap of occurrence distributions among individuals and species (Fig. 15, Table S5) and the protection coverage of zebra movement was assessed.
<!-- and periodograms, Fig. S6 & Fig. \ref{fig:perio_ken}-->

<!-- Home range, the area traversed by an animal in its normal activities [@Slavenko2016].
Explain how to derive if individuals reach their home range from variograms!!! -->

<!-- Environmental data extraction -->

<!-- This time for each movement point the altitude, slope and aspect and protection status (protected, unprotected or buffer zone) was obtained. -->
The movement points were subdivided into the different years (2003 - 2005) and the according land cover for that year was extracted for each point. The land use of each movement point was also extracted. The habitat use of the plains and Grevy's zebras was assessed by calculating the percentage of observations at each land cover and land use class (Fig. 17). The step length and absolute turning angle was also compared among each land cover and land use class (Fig. 18).

For the NDVI and EVI data, the movement points, which fell within the 4 day time interval of the corresponding satellite image, were selected and the values of the calculated indices for the specific time and coordinates were extracted. This was than used to extract the monthly value of each index experienced by Grevy's and plains zebras (Fig. 16).

<!-- Animal-defined corridors -->

Corridors are defined as areas characterized by parallel, quick and repeated animal movement paths. A more detailed description of the definition of animal-defined corridors can be found in @LaPoint2013. For each zebra the animal-defined corridors were identified using the `move` package in R and the overlap of corridors with existing PAs was assessed (Fig. S18).

<!-- Again the entire analysis was performed in R version 3.3.3 [@RCoreTeam2016], primarily using the R packages `raster` [@Hijmans2016a], `rgdal` [@Bivand2016a], `rgeos` [@Bivand2016a], `RStoolbox` [@Leutner2016], `move` [@Kranstauber2016a] and `ctmm` [@Fleming2016]. -->

## Results

### Vegetation changes

The entire study area experienced a significant increase in NDVI from 1981 - 2013. The slope and adjusted R^2^ were both particularly high in the north-western part of the study area. Areas of high slope and adjusted R^2^ corresponded to areas where zebras were tracked (Fig. 12).

Laikipia zebra movement tracks]{Map of study area with movement tracks colour-coded by individual. Protected areas are depicted in lightgreen.

![](Figures/Gimms_NDVI_KEN.png)

**Fig. 12.** Protection trend Laikipia]{Slope and adjusted R^2^ of the GIMMS NDVI3g time series for the study area in Kenya. Green lines indicate outline of protected areas and the surrounding 5 km buffer.

The majority of the study area was covered by grasslands (92.3 - 95.2 %). The remaining parts were mostly covered by open shrublands (1.5 - 5.2 %), cropland/natural vegetation mosaic (0.8 - 2.2 %) and croplands (0.1 - 1.1 %). From 2005 to 2008 percentage cover of cropland/natural vegetation mosaic, woody savannas and grasslands decreased, while open shrublands and croplands increased (Table S4).

![](Figures/MLC_Timeseries_KEN.png)
**Fig. 13.** Percentage cover of each land cover class from 2001 - 2013 for the study area in Kenya.

Generally, land cover appeared to be stable over time (2001 - 2013), but, an increase in savannas and cropland/natural vegetation mosaic has been observed in recent years (2011 - 2013) (Fig. 13).

There were 10 different types of land use that occurred in the study area (Community Conservation Area (CCA), Government Land, Large Scale Farms, Mukogodo Group Ranches, Ranches, Rhino Sanctuary, Settlements, Swamp, Trust Land and Urban Settlements) (Fig. S15). 60 % of the study area were covered by ranches, 20 % by settlements and 7 % by trustland, the remaining land use classes only covered a small % of the study area (Table 7).

**Table 7.** Percentage area of each land use class of the study area in Kenya.


---------------------------------------
       Land use         Percentage (%) 
---------------------- ----------------
         CCA                  2        

   Government Land           3.2       

  Large Scale Farms          0.94      

Mukogodo Group Ranches       3.1       

       Ranches                60       

   Rhino Sanctuary           3.6       

     Settlements              19       

        Swamp                0.3       

      Trust Land             7.3       

  Urban Settlements          0.31      
---------------------------------------

The increasing trend in NDVI was highest in the PAs and lowest in the unprotected areas. The fit of the linear regression was highest in the PAs and lowest in the unprotected areas (Fig. 14).

![](Figures/Gimms_Status_NDVI_KEN.png)
**Fig. 14.** Adjusted R^2^ and Slope of the GIMMS NDVI3g time series for each protection status (protected, unprotected and 5 km buffer zone) of the study area in Kenya.

### Space use

<!-- What is the space use of Grevy's and plains zebras? Is there a larger difference in space use within or among species? -->

7 Grevy's zebras were tracked for 952 days and 6 plains zebras were tracked for 233 days. Total tracking distance varied between 42 - 3450 km, on average 1147.29 km ($\pm$ 1136.29 SD) for Grevy's zebras and 361.66 km ($\pm$ 599.84 SD) for plains zebras (Table 6, Fig. 11). The mean speed varied from 0.07 - 0.20 m/s and was higher for plains zebras (0.11 - 0.2 m/s) than Grevy's zebras (0.07 - 0.11 m/s). Mean step length was 238.05 m ($\pm$ 102.47 SD) and mean direction varied from -63.76 to 6.71°. The size of 95 % occurrence distribution varied from 6.00 - 437.2 km^2^. Mean distribution size was higher for Grevy's (204.26 km^2^ $\pm$ 174.52 SD) compared to plains zebras (72.19 km^2^ $\pm$ 47.13 SD) (Table S5). Overlap among individuals varied from 0 - 94.6 %. Overlap among Grevy's zebras ranged from 0 - 94.6 % with an average overlap of 43.85 %, while overlap in plains zebras varied from 0 - 90.26 % with an average of 50.33 %. Overlap between Grevy's and plains zebras' occurrence distribution was 27.23 % (Fig. 15).

![](Figures/AKDE_KEN.png)
**Fig. 15.** Autocorrelated kernel density estimated utilisation distributions per zebra in Kenya. Protected areas are depicted in darkgreen.

<!-- What is the major driver of habitat use in the two species? -->

While Grevy's zebras were tracked throughout the entire year, plains zebras were only tracked from June - December. During this time, plain's zebras utilised areas with higher EVI and NDVI compared to Grevy's zebras (Fig. 16).

![](Figures/vi_month_sp_KEN.png)

**Fig. 16.** EVI and NDVI and per month experienced by plains and Grevy's zebras in Kenya.

Grevy's as well as plains zebras used mostly grasslands. Grevy's zebras also used open shrublands, while plains zebras used natural vegetation mosaic areas. Only PZ10 used savannas and PZ10 and PZ14 both used woody savannas (Fig. 17).

![](Figures/Zebra_KEN_LULC.png)

**Fig. 17.** Percentage of observations per land use and land cover per individual in Kenya.

Of the 10 different types of land use, all types apart from swamp were used by the zebras. All Grevy's zebras and two plains zebras (PZ1 and PZ2) occurred mostly on ranches (Fig. 17). The four other plains zebras (PZ6, PZ8, PZ10, PZ14) were limited in their distribution to the eastern part of Ol Pejeta Community Conservancy (Fig. 11), as it is surrounded by a permanent fence, and occurred mostly on rhino sanctuary ground (Fig. 17). 

Difference in absolute turning angle and speed between species varied among land use and land cover type. Plains zebras moved slower on ranch land and faster on settlements compared to Grevy's zebras, while absolute turning angle was higher for both in plains zebras compared to Grevy's zebras. In grasslands, plains zebras moved faster than grevy's zebras, while it was the other way around in open shrublands. Absolute turning angle of plains zebras was lower in open shrublands and higher in grasslands compared to the one of Grevy's zebras (Fig. 18).

![](Figures/LULC_angle_speed_KEN.png)

**Fig. 18.** Speed and absolute turning angle per land cover and land use class in Kenya.

### Protection coverage

<!-- How well do the current PAs cover the space use of the two species? -->

There are currently five protected areas within the study area. All of them are small in size (150 - 264 km^2^), but have been in place for quite some time (1969 - 2004) (Table 8). Only 20.2 % of the study area was protected and 27.9 % of the study area was covered by the 5km buffer zone.

**Table 8.** Summary of the Protected Areas of the study area.


----------------------------------------------------------------------------------
        Name                Designation         IUCN Category   Area (km2)   Year 
--------------------- ------------------------ --------------- ------------ ------
        Maun               Game Sanctuary            IV             85       1975 

        Chobe              National Park             Ib        1.100000e+04  1968 

      Nxai Pan             National Park             Ib            2576      1971 

       Moremi               Game Reserve             Ib            4871      1963 

  Makgadikgadi Pans        National Park             Ib            4902      1992 

Okavango Delta System Ramsar Site, Wetland of   Not Reported   5.537400e+04  1996 
                      International Importance                                    

   Okavango Delta       World Heritage Site    Not Applicable  2.023590e+04  2014 
----------------------------------------------------------------------------------

Of the existing PAs only Laikipia National Reserve is formally protected, the other four PAs are community conservancies or private ranches (Table 8, Fig. S14).

33 corridors were identified of which only three corridors belonged to a single plains zebra (PZ2), while the rest belonged to five Grevy's zebras (GZ2, GZ4, GZ5, GZ6, GZ7). Only 25.6 % of the corridors fell within PAs (Fig. S18), while 47.8 % of occurrence distribution is currently protected. 44.74 % of Grevy's zebras' occurrence distribution and 49.11 % of plains zebras' occurrence distribution is covered by protected areas (Fig. 15).

## Discussion

<!-- 1. Has there been an increase or loss in vegetation over the last 30 years? -->

The origin of vegetation patterns is important in ecology, as vegetation patterning can affect ecosystem functioning. The majority of the study area was covered by grasslands and the entire study area experienced a significant increase in NDVI from 1981 - 2013 (Fig. 12). Patterning in vegetation varies with rainfall and nutrient availability, but also with herbivory, fire, surface-water processes and soil nutrient-organic matter dynamics [@DeKnegt2008].

Land cover was relatively stable from 2001 to 2013, but an increase in savannas, woody savannas and cropland/natural vegetation mosaic was observed in recent years (2011 - 2013) (Fig. 13). The increase in cropland could reflect increasing land-use due to population expansion. MODIS Land Cover is only available at a resolution of 500 m and the user accuracy for savannas is quite low (< 45 %). Thus, the observed changes have to be taken with great care, even so changes in land-cover classes should be accurate, even if the absolute land-cover classes are not [@Pfeifer2012a].

<!-- 2. What is the space use of Grevy's and plains zebras? -->

Occurrence distribution was larger for Grevy's than plains zebras, but Grevy's zebras were also tracked much longer than plains zebras (Table 6). Four plains zebras were restricted in their occurrence distribution to the eastern part of Ol Pejeta Conservancy (Fig. 11) by the presence off a fence. The space use of an individual is the interplay between its metabolic demand, body size and resource availability. Grevy's zebras are larger than plains zebras and so are likely to have a larger area requirement. Areas with low resource availability usually force the animal to increase its space use in order to increase the amount of resources it can access [@vanBeest2011].

Plains zebras moved faster (0.11 - 0.2 m/s) than Grevy's zebras (0.07 - 0.11 m/s). However, some plains zebras (PZ6, PZ8, PZ10, PZ14) were tracked with a very high sampling rate (8 min) and so their movement could be measured much more precisely, which likely resulted in more accurate speeds. 

Although, Grevy's and plains zebras generally co-occur in this area [@Sundaresan2012], the overlap between their occurrence distributions was low (27.23 %). First-generation hybrids of female plains zebras and male Grevy’s zebras have been found in the Laikipia ecosystem of northern Kenya. They integrate themselves into plains zebra society and thus are no conservation concern, as it is unlikely that they will dilute the Grevy's zebra gene pool [@Cordingley2009]. There is an extensive spatial and temporal overlap between livestock and Grevy's zebras and Grevy's zebra were found to compete with cattle over waterholes [@Low2009; @Sundaresan2008]. Vegetation cover loss and soil erosion have been the result of the transition from a nomadic to a sedentary livestock grazing regime. Waterholes are fenced off to stop wildlife from soiling the water or accessing the waterholes during the day. Thus, conditions for Grevy's and plains zebras are less favourable and the risk of predation is increased [@Sundaresan2012].

<!-- Habitat use -->

Studying habitat use and selection is essential for understanding the biological requirements of animals, which is crucial for conservation and management purposes [@Freitas2008a]. Habitat selection is the process by which individuals choose a specific habitat type among a set of available habitat types [@VanMoorter2016]. These decisions can influence the survival and reproductive success of individuals, which can affect the entire population [@McLoughlin2007; @Matthiopoulos2015]. 

Plains zebras utilised areas with higher NDVI and EVI compared to Grevy's zebras (Fig. 16). This suggests that plains zebras require a higher resource availability compared to Grevy's zebras. This estimate is based on a very low sampling frequency, as only one plains zebras was tracked from July to December (Table 6). 4 plains zebras were tracked in 2005, when a higher NDVI and EVI might have been available. Furthermore, in female plains zebras the forage quality and quantity and habitat openness of locations used varies significantly with reproductive state [@Sundaresan2008].

The study area was covered to 60 % by ranches and 20 % by settlements (Table 7). All Grevy's zebras and the two plains zebras occuring outside Ol Pejeta Community Conservancy (PZ1 and PZ2) occurred mostly on ranches, while the other four plains zebras (PZ6, PZ8, PZ10, PZ14) occurred mostly on rhino sanctuary ground (Fig. 17). However, this is due to the fact that these four zebras were limited in their distribution by a fence. 

Grevy's zebras have lower forage quality and drinking requirements than plains zebras [@Sundaresan2008]. Plains zebras typically inhabit grasslands [@McNaughton1986], while Grevy's zebras live on rangelands often shared by pastoral populations [@Sundaresan2008]. In Laikipia, the majority of Grevy's zebra habitat is owned by local or pastoral communities and Grevy's zebra have to coexist with livestock, including cattle, sheep, goats and camels [@Sundaresan2012].

The majority of the study area was covered by grasslands (92.3 - 95.2 %). The remaining parts were mostly covered by open shrublands (1.5 - 5.2 %), cropland/natural vegetation mosaic (0.8 - 2.2 %) and croplands (0.1 - 1.1 %) (Table S4). Grevy's as well as plains zebras used mostly grasslands. Grevy's zebras also used open shrublands, while plains zebras also used natural vegetation mosaic areas (Fig. 17). This shows that land cover is not as suitable as vegetation indices, such as NDVI and EVI, for detecting differences in resource use among species. But, land cover was only available every year, while NDVI and EVI varied every 4 days, which logically results in a much better representation of vegetation dynamics.

Habitat selection can not only be inferred from RSFs, but also from the intensity of use of habitat conditions in sites experienced by the animal [@Freitas2008a]. Individuals increase their use of high-quality resource areas by decreasing their movement rates. Vice versa, sites with low forage availability or high predation risk may stimulate increased movement rates [@Fryxell2008; @Avgar2013; @VanMoorter2016]. 

Difference in absolute turning angle and speed between species varied among land use and land cover type. Plains zebras moved faster and showed more directional movement than Grevy's zebras in grasslands and vice versa in open shrublands (Fig. 18). This would indicate a preference of Grevy's zebras for open shrublands and a preference of plains zebras for grasslands. For African elephants, @Wittemyer2008a found that during dry season movement was directional towards food and water, while during the wet season movements were more random.

Land cover data of multiple years was used to compare the habitat use among Grevy's and plains zebras. Although, an easy-to-use MODIS Landcover product from 2001 - 2013 exists and regional to global land cover products from Landsat and SPOT are becoming more widely available [@Nagendra2013], the use of land cover data from multiple dates for analysing animal movement is still rare [@Neumann2015a]. There are often discrepancies between these different products, as well as between maps generated at the local scale [@DeFries2005]. Land cover accuracy of the MODIS product was found to be particularly low for savanna ecosystems (< 45 %) [@Cohen2006]. Ecological applications further require a high thematic resolution, but classification accuracy usually decreases with increasing land cover classes [@Neumann2015a]. Fine-scale movement analysis of animals from GPS-collars might further be particular prone to location errors, as the accuracy of fixes needs to correspond to the animal’s movement behaviour [@Bjorneraas2010]. Collar weight and fit can have a significant effect on the rate of travel, as has been shown for plains zebra females in the Makgadikgadi Pans [@Brooks2008a]. Small differences in collar weight or fit can affect the movement behaviour of an animal, which is particularly relevant for fine-scale movement data.

Individual preference for a specific habitat does not always correspond to the residence time in that habitat, but can also be the result of increased revisitation of certain areas, as areas with a long residence time and areas with a high revisitation rate are not necessarily identical. Water holes, for example, are often visited but only for a short period of time [@VanMoorter2016]. The  preference of an individual zebra might be driven by the needs of other individuals in the same harem. Lactating plains zebra females have the habitual role of initiating movement in harems and harems containing lactating females are even more likely to lead herd movements. Phenotype and social relationships of group members are thus likely to affect the speed, distance or direction of the movement of plains zebras [@Fischhoff2007b].

<!-- 3. How well do the current PAs cover the space use of the two species? -->

There are currently five PAs, which cover 20 % of the study area, of which only one (Laikipia National Reserve) is formally protected (Table 8). Biodiversity conservation not only requires a number of PAs, but these also need to be well-connected, effectively managed and ecologically representative [@Dewi2013]. Although PAs are intented to conserve habitats and species, their effectiveness varies among protection status. While National Parks mostly have firm restrictions on resource use and strong law enforcement, law enforcement is typically sporadic in Nature Reserves, as they are often understaffed [@Caro2009]. This leads to different trends in forest loss within and adjacent to PAs depending on their protection status. While conservation efforts in Kenya initially focused on creating PAs for large mammals, the recent focus has shifted towards the support of livelihoods and the alleviation of poverty [@Pfeifer2012]. Data on PAs derived from global databases may suffer from spatial inaccuracies and lack sufficient detail to use for effective monitoring of single protected areas or even regional park networks [@Chape2005; @Nagendra2013]. The higher the proportion of a species' range that is protected, the higher the likelihood that the species is truly covered by a PA, even if the management does not ensure the species' long-term persistence [@Rodrigues2004]. 45 % of Grevy's zebras' and 49 % of plains zebras' occurrence distribution was covered by PAs (Fig. 15). Half of the plains zebras occurred in the eastern part of the Ol Pejeta Community Conservancy, which is surrounded by a fence, and so there occurrence distribution was completely protected.

<!-- Fences -->

Fences have a negative effect on wild ungulate numbers due to restricted migration to surface waters and summer grazing areas [@Coughenour1991]. In Laikipia, fences have mostly been created to prevent elephants from moving out of large private and government-owned ranches and onto smallholder cultivated land [@Evans2016a], but this obviously also affects the movement of zebras.

<!-- Corridors -->

Conservation corridors are useful for maintaining landscape connectivity because they provide a way to facilitate animal movement across fragmented landscapes [@Gilbert-Norton2010]. Animal-defined corridors of only five Grevy's and one plains zebra could be identified of which 26 % fell within PAs (Fig. S18). Most animals were probably not tracked for long enough to be able to identify animal-defined corridors.

Conservation corridors may reduce extinction risk, maintain gene flow and facilitate dispersal [@Corlatti2009; @LaPoint2013]. Corridors might also provide future routes and habitats in response to climate change, but need to be based on the habitat use and the movement of the organisms [@Chetkiewicz2006]. The utility of corridors is species-specific and depends on the width and structure of the corridor. Improving the habitat quality between suitable patches can sometimes be a more cost-effective alternative [@Makelainen2016].

Wildlife in Kenya is still declining in particular within Kenya's PAs [@Western2009]. Nearly all indigenous large mammal species in Kenya are more abundant on multiple-use lands than inside parks and reserves. Wildlife and wildlife areas are increasing in Laikipia. Residents still suffer losses to wildlife, either through crop raiding, predation of livestock, damaging infrastructure or compromising human safety, but only derive minimal benefits [@Young2005; @Gadd2005; @Bond2014a]. 

Zebras share many of the same food and water resource needs as livestock and so the protection of zebra habitat would benefit both livestock and local people, but only few people were able to identify the direct benefits of Grevy's zebras. In addition, wildlife species can be beneficial to the local community by providing revenue through tourism or game ranching [@Sundaresan2012]. Combining wildlife with moderate livestock production may not only be economically optimal, but can help to preserve biodiversity at the same time [@Young1997a]. Outreach about the benefits of the species as well as its population decline is needed, local people that share the pasture-land with Grevy’s zebra must get involved and private and community-based measures need to be combined with PAs in order to prevent a further population decline [@Western2009; @Sundaresan2012].

# Synthesis

Africa's population is rapidly expanding and as a result land and natural resources are exploited at an alarming rate [@Edwards2014; @Caro2014; @Searchinger2015]. To foster future agricultural production [@Weng2013] and mineral exports [@Edwards2014] dozens of development corridors are being implemented. Various of the currently planned development corridors are likely to provide only a small benefit to society, but severly degrade African ecosystems and wildlife [@Laurance2015].

Biodiversity conservation requires ecologically representative and well-connected systems of effectively managed PAs, but often priorities in terms of ecosystem, endemic species, human pressure and the types of management effort have to be set [@Dewi2013]. The majority of global priority regions lie in low-income countries in the tropics, which can least afford the costs of establishing and enforcing protected areas. Many of the already existing PAs in these regions are struggling because they are lacking financial resources, which are needed to fulfill their conservation role [@Rodrigues2004]. Although a species may be covered by a PA, it does not have to be protected effectively, if adequate management to ensure the species’ long-term persistence is missing. Generally, the larger the proportion of a species’ range that overlaps with PAs, the higher the likelihood that the species is truly covered [@Rodrigues2004].

Ecosystem connectivity can provide organisms access to spatially distributed resources, reduce local extinctions and increase recolonization of habitat fragments, but on a large scale can also facilitate annual migrations and climate-driven range shifts. Thus, increasing landscape connectivity is fundamental for mitigating impacts of climate change and habitat fragmentation [@Rayfield2016; @Abrahms2016]. The identification and protection of wildlife corridors has become an important tool in conservation, as they can help to maintain landscape connectivity by promoting animal movement [@Gilbert-Norton2010]. However, this depends on the animals capability to utilise these corridors, which can be tested using animal movement data [@LaPoint2013].

In the past, the study of animal movement has mostly focused on the movement behaviours of individuals [@Fryxell2008; @Nathan2008]. In order to truly understand the environmental influence on animal movement, multiple individuals across a variety of environmental conditions need to be tracked. Predictive models of population spread and habitat selection can be used to deepen our understanding and may help to develop and implement better conservation strategies that account for the effects of climate and land use change [@Avgar2013; @Naidoo2012]. GPS tracking devices are commonly used for the study of animal movement, as they allow for frequent, automatic sampling over long periods of time [@Bjorneraas2010]. However, the effect of capture and release as well as the tag itself might have an impact on the animal. @Morellet2009 found that capture and handling and fitting of a GPS collar on roe deer affected the spatial behaviour, habitat use and overall activity level in the first 10 days. Tagging of an animal often causes pain, suffering and distress to the animal [@Hawkins2004]. Medium to large-sized wildlife, such as elephants, wildebeest and zebras, can be detected in open savanna using very high resolution satellite imagery (GeoEye-1) [@Pettorelli2014]. Individual zebras can be identified by their unique stripe pattern [@Grubb1981]. Scouts observed the areas that were heavily used by Grevy's zebra, which closely matched the areas inferred from analyses of GPS-collar data [@Low2009], questioning the need of GPS collars to study the movement of these animals.

Remote Sensing can provide information about spatio-temporal variation in vegetation and land-cover, which can affect animal movement [@Pettorelli2014]. In order to model small-scale and high-frequency movement, data on phenology, climate, food and water availability are needed at finer spatial, thematic, and temporal resolution [@Rose2015]. Pixel size for those satellites that provide daily observations tends to be between 250 and 1000 m, which is far coarser than the spatio-temporal resolution of GPS-collar-based movement data. The smallest observable feature that can be mapped has to be considerably larger than that, i.e. 3600 m$^{2}$ for Landsat imagery and 250000 m$^{2}$ for MODIS data. High resolution data is usually expansive and there is typically a mismatch between spatial and temporal resolution in RS data. The quality of RS data can further be influenced by haze, clouds and shadows [@Willis2015; @Zeller2012; @Neumann2015a]. 

Physical barriers, such as fences or roads, can influence the distribution and ranging behaviour of a species and so isolate populations, reduce genetic diversity, increase susceptibility to diseases and impede access to resources [@Bliss-Ketchum2016], which on the long-term can alter the viability of entire populations [@Cozzi2013]. It is important to understand the influence of barriers on the space use of an animal in order to mitigate the effects of such barriers. Responses to barriers will vary among species, as they depend on the animal's movement capabilities, its proximity to the barriers and its habitat preference [@Beyer2016]. Accurate informations on barriers are not easy to obtain and even if, they can change frequently [@Neumann2015a].

Large herbivores are thought to be detrimental for the maintainance of the functioning of savanna ecosystems [@Goheen2010]. Under a business-as-usual scenario, Geometric mean population abundance of terrestrial carnivore and ungulate species declines by 18-35\% and extinction risk rises for 8-23\%, while an alternative sustainable development scenario could reduce both extinction risk and population losses and lead to population increases [@Visconti2015].

Plains zebras are listed as "Near Threatened" and Grevy's zebras are listed as "Endangered" under the IUCN Red List of Species, as both species have undergone a considerable population decline in the recent past [@Moehlman2013; @King2016]. Without conservation actions ungulates would be off far worse [@Hoffmann2015]. PAs that integrate local people tend to be more effective at conservation as well as at socio-economic development outcomes [@Oldekop2015]. National Parks can provide a large recreational value, which can help to achieve nature conservation goals [@Schagner2016]. Engaging local communities in biodiversity conservation and monitoring can be an effective conservation approach, especially in rural Africa [@Dolrenry2016].

Habitat fragmentation and global warming are two of the most important anthropogenic impacts affecting natural ecosystems and the services they provide [@Barnes2015]. The boundaries for climate change and rate of biodiversity loss, within which humanity can operate safely, have already been crossed [@Rockstroem2009]. This calls for urgent action to alter our relationship with the planet we inhabit by stopping further habitat destruction and mitigating climate disruption [@Young2016a; @Steffen2011].

# References
