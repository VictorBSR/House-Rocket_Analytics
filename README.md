# House Rocket - Price Analysis and Portfolio Recommendations

![icon](https://user-images.githubusercontent.com/42360197/207433028-735a3b18-1aa9-432f-9d16-6d2f027a0d64.png)

House Rocket is a fictional company focused on analyzing property data and conducting buy-sell operations to maximize profits, primarily considering:
- Property conditions and
- The time of year

This project presents a complete solution in the form of an interactive, cloud-hosted dashboard from the CEO’s perspective on the best available business deals in the market. The dashboard includes visualizations, descriptive statistical analysis, business insights, and purchase and sale recommendations.

**The interactive dashboard is accessible at: https://victorbsr-house-rocket-analytics-dashboard-a49566.streamlit.app/**


# 1. Description - Business Questions
To find the best business opportunities: purchase homes in good condition at low prices and resell them at a higher, fair price. The attractiveness and price of properties are directly influenced by attributes such as location, number of rooms, area, construction, and renovation dates.

**1. Which properties should the company acquire, and at what price?**

**2. For acquired properties, when is the best time to sell, and at what price?**

# 2. Dataset and Attributes
Originally downloaded from <url>https://www.kaggle.com/harlfoxem/housesalesprediction/discussion/207885</url>, the dataset contains property data from Seattle, USA.

Definitions of relevant attributes:

|    Attribute     |                         Description                            |
| :-------------: | :----------------------------------------------------------: |
|       id        |            	  Unique identifier for each property            |
|      date       |               Date of the property listing announcement      |
|      price      |                 Current sale price of the property           |
|    bedrooms     |                      Number of bedrooms                       |
|    bathrooms    |                     Number of bathrooms                      |
|   sqft_living   |    Interior area of the property in square feet  |
|    sqft_lot     |        Total land area of the property in square feet      |
|     floors      |                 Number of floors in the property                  |
|   waterfront    |     Indicates waterfront presence (0 = no, 1 = yes)     |
|      view       |   View quality of the property (0 = low, 4 = high) |
|    condition    | Overall condition quality of the property (0 = low, 5 = high) |
|      grade      | Quality of the property’s construction and design (1-3 = low, 4-10 = medium, 11-13 = high) |
|  sqft_basement  |      Basement area of the property in square feet  |
|    yr_built     |                  Year the property was built                 |
|  yr_renovated   |                Year the property was renovated                      |
|     zipcode     |                  ZIP code of the property’s location                |
|       lat       |                           Latitude                           |
|      long       |                          Longitude                           |
| sqft_livining15 | Interior living area in square feet for the 15 nearest neighbors |
|   sqft_lot15    | Lot area in square feet for the 15 nearest neighbors |


# 3. Business Assumptions
The following assumptions were made for the dataset and the project as a whole:
- Properties with more than 11 bedrooms were considered outliers and ignored.
- For most analyses (except price evolution over time), only the most recent record for each property was considered if it had multiple listings at different times.
- Zero values mean that the attribute is either absent or not applicable (e.g., no waterfront, not renovated, no basement, etc.), while one indicates the attribute’s presence.

# 4. Solution Plan
The following steps guided the project’s development:
1) Business Understanding
2) Data Import (via Kaggle)
3) Data Cleaning and Preparation
4) EDA (Exploratory Data Analysis) - creating visualizations and tables
5) Business Insight Development - hypotheses with potential business value
6) Purchase and Sale Recommendations

# 5. Main Business Insights
**Business insights** are hypotheses that involve analyzing and comparing two or more variables. Once reviewed, they yield a conclusion, typically in the form of charts and tables. If actionable (enabling business decisions that are advantageous), a hypothesis becomes a *business insight*.

| Hypothesis                                                     | Result  | Business Action Suggestion                                        |
| ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ |
| H1 - Properties with waterfront views are on average 25% more expensive | True | Prioritize purchasing properties with waterfront views if favorably priced   |
| H2 - Properties with waterfront views are around 10% cheaper when sold in winter or fall | True      | Monitor prices for these properties in these seasons for potential deals |
| H3 - Properties with basements are around 50% more expensive than those without | False | Having a basement is attractive but less impactful than expected (only 25%)    |
| H4 - The month-over-month price increase for the observed period is over 5% | True | Prioritize buying properties in months with price decreases  |
| H5 - Properties built before 1955 and renovated are priced 20% higher than those not renovated or built in a different period | True      | Buy older, renovated properties, as their resale price is about 32% above others   |

# 6. Results
Following the insights analysis, a table was created with purchase recommendations and sale price suggestions, as well as property maps organized by ZIP code and filter options. The criterion for determining property viability for purchase is if its ***sale price is equal to or lower than the median price in its region (ZIP code)*** and if the ***property condition is good or excellent***. The suggested ***sale price is set to be 30% above the acquisition cost if the purchase price is below the median for that season***, or 10% higher if not. This strategy seeks to take advantage of purchase opportunities significantly below the common price and to financially leverage sales according to seasonal variations.

The estimated profit for the company, if all business recommendations (all recommended buy-sell operations) were followed, would be approximately **$1,201,195,000.00**.

# 7. Conclusion
Business hypotheses that became business insights provided valuable understanding of the data, serving as a foundation for new company strategies to improve buying and selling operations. Some actionable steps are:
- Prioritize buying properties with waterfront views that are well-priced
- Purchase properties near water in fall and winter, selling them in spring and summer
- Prioritize buying older, non-renovated properties and renovating them, as their resale value increases significantly
Grouping properties by region allowed a visual and geographical analysis of their locations and enabled the use of regional median prices as a decisive parameter for business recommendations. The median was chosen as a baseline to minimize outlier effects, but using both average and median could be considered to assess price dispersion by region.

The main goal of answering the two business questions was successfully achieved, and the solution includes several interesting and interactive features and visualizations, allowing the CEO to perform various analyses as needed. The chosen platform for deployment may not be the best in terms of performance but meets the analytical premise and supports loading datasets from various sources, such as a local database, a web page, or even a data warehouse or data lake/data lakehouse. It is also scalable and adaptable for other datasets and company areas.

Future steps could involve expanding the analysis to other regions and datasets, creating new features, and performing a predictive price analysis for purchase and sale value increases represented by time series.

*(The company and logo are fictional, created exclusively for this project purpose.)*
