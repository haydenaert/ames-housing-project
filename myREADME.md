## How much do alternative housing options versus single family houses affect the price of a house in Ames, Iowa? 


# Background

Ames, Iowa is a moderately sized town about 30 miles north of Des Moines. It's known for being home to Iowa State University and also hosts the United States Department of Agriculture. 

In recent years, the city has experienced an influx of new residents. In 2019, it was ranked the 33rd Best Place to Live in the US for its commitment to health; it was named the healthiest city in the country in 2015. ([*source*](https://livability.com/best-places/top-100-best-places-to-live/2019/ia/ames)).

As the city continues to grow and attract more people with its wonderful combination of urban life and outdoor activities, the city needs to consider supporting the necesssary housing. In 2015, the City Council of Ames purchased 7 acres of land at 321 State Avenue with the intention of developing more affordable housing. Debates over what type of housing to build on this plot lof land began to rise at the beginning of this year ([*source*](https://www.amestrib.com/news/20200124/ames-residents-speak-out-against-multi-family-housing-on-state-avenue-at-open-house)). 

Residents are pushing for single family homes as opposed to multifamily homes because they insist multi-family homes are more attractive to renters who don't take care of their houses as much as a home owner would. This behavior is a negative externality for surrounding neighbors and some believe it lowers property value. With this in mind, the City Council continues to consider alternative options such as multi-family homes because they are more conducive for students and families who are seeking cheaper options. 
 
More recently, the City Council pushed proposals for development. ([*source*](https://www.amestrib.com/story/news/2020/10/23/ames-city-council-hear-affordable-housing-proposal-old-middle-school-lot/3714097001/)). The proposals that stood out the most were the MVAH Partners-Family Housing and Prairie Fire Development Corporation. To be accepted the council said the proposal would need a score of 155 on the Iowa Finance Authority's scoring system. 

This continues to raise concern among residents who argue there are too many rentals in the city and would rather have units that have stronger long term sustainability. Some residents have even started to look for housing outside of Ames in spite of these recent developments toward multi-family houses ([*source*](https://www.amestrib.com/story/news/2020/10/28/ames-city-council-state-avenue-low-income-housing-project/3759039001/)).

Residents believe single family homes retain more value than alternative options. The objective for this report is to determine the effects of single family houses and alternative housing options on housing prices. If housing prices is one of the determinants for the City Council's development plans, hopefully my findings can inform the them on which type of homes have a bigger positive effect on housing prices. 


# Summary 

The data for this report is from 2006-2010. It contains all sorts of categorical and numerical information regarding houses that were sold during that time period. 

Before I built a model, I cleaned all the data. The majority of the columns were categorical. Among these categorical variables, the values were either nominal or ordinal. For the nominal categorical values, I encoded all of them into a dummy variable and transformed each column so that each individual value would represent its own column. For the ordinal categorical variables, I encoded all of them on a scale from 1-N based on the number of ordinal values the variable had and the order of ranking. 

After I cleaned all my data, I only wanted model data that had a notable impact on price. I wrote a function that took in a variable and determined which value affected the mean of the sale price by more than 30%. For my continuous or discrete variables, I used a scatter plot to determine which variables had a high linear correlation with my target variable, sale price. 

Once I filtered the dataset into a smaller set of variables which I deemed important via the simple method from above, I instantiated a Linear Regression to observe the various relationships in the data. This was my baseline model. 

In order to observe the effects of single family homes and alternative options, I added the four alternative housing options to the baseline model: multi-family homes (that were originally single family homes), duplexes, townhouses that were end units, and townhouses that were inside units. I did not include the single family home because it is the reference variable. In other words, after running my regression and observing the coefficients for each of the alternative housing options, I will be able to interpret how much of an effect each option had with respect to the single family home variable. This is my final model. 

Again, the goal is to see how each alternative housing option affected the sale price of each house. 


## Data Dictionary 
| Feature                  | Type    | Data |  Description                                                 |
|--------------------------|---------|------|--------------------------------------------------------------|
| Street                   | nominal | Ames | type of road access to property (gravel or paved)            |  
| Central Air              | nominal | Ames | yes or no                                                    |
| Overall Quality          | ordinal | Ames | rates the overall material and finish of the house           |
| Basement Quality         | ordinal | Ames | evaluates the height of the basement                         |
| Kitchen Quality          | ordinal | Ames | kitchen quality                                              |
| Fireplace Quality        | ordinal | Ames | fireplace quality                                            |
| Basment Exp              | ordinal | Ames | refers to walkout or garden level walls                      |
| Heating Quality          | ordinal | Ames | heating quality and condition                                |
| Year Built               | int64   | Ames | original construction date                                   |
| Basemnt Full Baths       | int64   | Ames | basement full bathrooms                                      |
| Full Baths               | int64   | Ames | full bathrooms above grade                                   |
| Year Remodeled           | int64   | Ames | remodel date (same as construction date if none)             |
| Masonry Veneer (sqft)    | int64   | Ames | masonry veneer area in square feet                           |
| Basement Area (sqft)     | int64   | Ames | total square feet of basement area                           |
| 1st/2nd Floor Area (sqft)| int64   | Ames | total square feet of st and second floor                     |
| Garage Cars              | int64   | Ames | size of garage in car capacity                               |
| Building Type            | nominal | Ames | Style of dwelling                                            |


## Main Points, Findings, and Results

The r-squared value of my final model is 87%. This means the model accounts for 87% of the variability in the sale price of a house in Ames. Another metric to score the effectiveness of the model is the root mean squared error (RMSE). The RMSE is 27,583 which means the average error in the model's prediction is about $27k from the actual value in our observed data. 

In terms of the housing options, the model shows that each alternative housing option actually yields a lower sale price than would a sinyl famle home. Below is a table of the coefficients. 

| Building Type           | Coefficient  | Description                                                    |
|-------------------------|--------------|----------------------------------------------------------------|
| 2 Family Conversion     | -1963.61     | Two-family Conversion; originally built as one-family dwelling |
| Duplex                  | -3077.73     | Duplex                                                         |
| Townhouse (end unit)    | -3485.84     | Townhouse End Unit                                             |
| Townhouse (inside unit) | -4383.34     | Townhouse Inside Unit                                          |

According to the coefficients of the alternative housing options, single family homes have a bigger positive affect on sale prices, on average. For example, we can expect the sale price of a duplex to be approximately $3,077 less than a single family home, on average. 

## Observations and Conclusions

Based on the results of the linear regession, we can conclude that the residents who oppose the development of multi-family homes are correct; on average, single family homes sell for higher prices than alternative options. 

All in all, this report could provide more clarity to the City Council. It shows single family homes retain more value on average than alternative housing options. 

## Next Steps

As more and more people--primarily wealthy Boomers and their families--move inward from the borders of country, overlooked cities like Ames are poised to take advantage of the fruits of these migrations. While the city of Ames needs to take into consideration the current demands of its residents, which are primarily transient college students and visitors, it has a very unique opportunity to develop the infrastucture to attract more permanent residents and therefore encourage more long term commitment and value. 

For these reasons, it would be prudent to look at the demographics of incoming residents. Perhaps the number of migrants who could be classified as permanent residents have been increasing over the years, which would provide another reason to develop single family homes over multi-family homes. 

It's also important to keep in mind that this data is over 10 years old. A more recent version of this report ought to be conducted to reflect current prices and trends. 

Something else to keep in mind is there's a considerably high amount of single family homes in the data set compared to alternative options. It's possible that if Ames had more alternative housing options from 2006-2010, then the average prices of those houses could be higher on a relative basis. 

All in all, this report could provide more clarity to the City Council. It shows single family homes retain more value on average than alternative housing options. 

