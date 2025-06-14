# mixed-linear-arima-ohio-basin-water-quality
## Coupling an Econometric Mixed Linear Model with an Autoregressive Moving Average Using Regional Variables Applied to Water Quality of the Ohio Basin
Various financial instruments are used to account for the supply and demand of products derived from nature. Some examples include forward contracts, which are agreements between two or more parties for the buying and selling of biological products such as seeds, agricultural crops, etc. This is done to speed up the sales process for producing companies, as well as to ensure that purchasing companies receive a product in the future at an agreed-upon price. However, this tool also acts as insurance, given the various issues that can arise in the production chain. When dealing with nature-based products, it's important to note that there are exogenous problems that humans can rarely control, such as floods, droughts, earthquakes, etc.

With this in mind, we can consider this financial tool as insurance, where two or more parties commit to fulfilling their respective parts. It’s not hard to imagine that water also fits into this category of products, as many companies around the world rely on this substance to operate. From beverage companies to food producers, manufacturers, mining companies, and power generation firms.

Forward contracts are just one of many examples where we can find a connection between the most abundant object on Earth, water, and the world of finance and economics. Furthermore, with the opening of various fields of study aimed at demonstrating the effects of climate change on society, this connection becomes even more relevant.

In environmental economics, the Kuznets curve exists, which suggests that in the early stages of economic growth, pollution and environmental degradation tend to increase. However, as the economy develops and reaches high levels of income and well-being, there is a shift in priorities toward more social, technological, and environmental issues, reducing pollution in society.

By using the Real Gross Domestic Product (GDP), reducing the effects of money on total production to better observe the behavior of real variables such as capital and labor. This allow us to construct an econometric model inspired by the Kuznets curve to study water quality in one of the most important regions of the United States, due to its history and challenging future—the Ohio River Basin.

The Ohio River Basin is located in the United States and encompasses portions of 14 states, housing around 30 million people. The states it covers include Kentucky, Illinois, Indiana, Maryland, New York, North Carolina, Ohio, Pennsylvania, Tennessee, Virginia, and West Virginia. It is labeled as the third-largest river in the U.S., supporting various economic activities across the region, such as fishing, agriculture, industry, recreational activities, etc. It is also important to note that it serves as a source of drinking water and a home for various species.

This project attempts to conduct a spatiotemporal study of the Ohio River Basin, using data provided by the USGS and the EPA, to estimate the composition of the water, that is, pollutants/surface water. The goal is to show whether the water quality has improved over time or not. It is important to highlight that the time period compared is from 2018-2020 versus 2021-2023. Each year was compared quarterly in terms of the growth rate of the water composition, which was proposed as the variable to represent water quality.

This project is divided into three stages:

\- Econometric study between real GDP and the Toxic Release Inventory. (Presented in the Word document and in Python code for reuse)

- The data presented annually by the EPA(<https://www.epa.gov/toxics-release-inventory-tri-program>) shows the release of toxic pollutants into the environment by various companies across different industries and distributed throughout North America. This allows us to obtain the amount, in pounds, released into the environment by county and even by state. With this, we can establish a connection with our economic variable, the Real Gross Domestic Product (RGDP).
- To study the area, we analyzed the companies that pollute in the basin according to the information provided by the EPA, resulting in most of the being classified under the codes 21 and 311–316, 322–326 in the NAICS (North American Industry Classification System), which correspond to the Mining industry and the Non-Durable Goods Manufacturing industry.
- Using this data, we construct two econometric models, one for each industry, to calculate the amount of monthly toxic releases per county, using RGDP, CUANTI (the number of companies registered with the EPA per county), and the region of location as variables (δ_n= number of regions which can be divided the USA territory). Looking the equation as:
  
**lnTRIᵢₜ = 𝛿_2 + 𝛿_3 + 𝛿_4 + 𝛿_5 + 𝛿_6 + 𝛿_7 + lnTRI_i,t-1 + lnRGDPᵢₜ + lnCUANTIᵢₜ + εᵢₜ**
Where:

- lnTRIᵢₜ represents the toxic release inventory for county i at time t.
- lnRGDPᵢₜ, is the Real Gross Domestic Product per county i at time t.
- lnCUANTIᵢₜ, is the number of companies registered with the EPA per county i at time t.
- lnTRI_i,t-1, represents the lagged value of the toxic release inventory for past emissions impact.
- 𝛿, represents the regional variables (𝛿_2 = MidAtlantic, 𝛿_3 = The Southeast, 𝛿_4 =The Midwest,  𝛿_5 =The Rocky Mountains, 𝛿_6 = The Southwest, 𝛿_7 = The Pacific Coast).

The parameter estimation was conducted out using a linear mixed-effects model with an ARIMA (1, 1) structure, including random effects by county and regional variables smoothed using a first-order moving average. This estimation method was chosen because, unlike standard panel data models (with fixed or random effects), the inclusion of a lagged dependent variable in those models can lead to biased estimators. Additionally, other fixed effects models would eliminate the regional variables, making it impossible to evaluate their impact while also decreasing the model’s ability to generate accurate prediction.

\- Interpolation between GDP by industry and the industrial production index (Presented in the Word document and in Python code for reuse).

- Based on the index of industrial production published monthly by the FED (Federal Reserve System) and the RGDP published annually by the BEA (Bureau of Economic Analysis) by industry and by county, lineal interpolation is performed based on their relationship, justified by the fact that industrial production is a key component in the calculation of RGDP.

\- Maps of the Ohio River Basin showing the increase (or decrease) in composition rates, as well as area information (Presented above this text, also in the Word document and in Python code for reuse)

- The econometric model calculates the monthly toxic releases from the two selected industries by county around the basin, converting the previously annual variables into monthly ones. The results are then summed up to obtain the total per county, which is then compared to the monthly river water flow of the selected rivers, yielding the composition rate. Each river was chosen based on its territorial extent, according to the division of the Ohio Basin into hydrological sub regions.
- The years studied, from 2018 to 2023, will be divided into quarters to show the various meteorological conditions that occur each year. We will compare the quarters of 2018-2020 with those of 2021-2023, based on the growth rate of the water composition

The results show that, as indicated by the Kuznets curve, the region has reached a point where pollution has decreased compared to previous years due to regional progress, as observed in the econometric model results and the data itself. However, in some areas of the Ohio River Basin, the water composition has worsened because toxic emissions have increased in certain zones due to the opening of new industries, such as gas and oil mining companies. More importantly, this decline is due to the recent trend in the last few years of reduced flow in the region's most important rivers.
