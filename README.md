# Personal_Portfolio_Optimization_Model

A model that analyzes the outcomes of investing $150,000 in each of three portfolios: a stock portfolio, a crypto portfolio, and an index portfolio. After testing the performance of each portfolio and each asset per portfolio, sharpe ratios will be calculated in order to measure varying returns / volatility amounts over the course of 10,000 unique iterations. This model will then strategically optimize capital allocations in order to maximize returns while showcasing a strong ability to minimize downside risk.

## Model setup

### Step 1 - Designing the portfolios as pandas dataframes

[!Initial portfolio setup](https://user-images.githubusercontent.com/102639530/178574807-6b8e8edc-3299-43e0-be3d-85b5eab451cb.mp4)

* Adjust timelines as desired via the start and end date variables
* Assign initial portfolio values (ideally using `portfolio_value` as the constant variable for all three portfolios)
* Specify the desired assets for each portfolio (i.e. which stocks will be analyzed in the stock portfolio, which cryptos will be analyzed in the crypto portfolio, etc.)
* Choose the method of capital distribution for assets (default is set to uniform distribution)
  * EX: A portfolio with `n` assets will have a distribution of `(1/n) * portfolio_value`

#### **A note on using variables**

* All variables with an `st_` prefix are utilized for stock-related variables
* All variables with a `cr_` prefix are utilized for crypto-related variables
* All variables with an `ind_` prefix are utilized for index-related variables

### Step 2 - Plotting & analyzing portfolio / asset performance

[!Examining plot + asset performance](https://user-images.githubusercontent.com/102639530/178560643-c522127d-4953-4ffc-b6f0-232499896262.mp4)

* Assign customizable upper / lower bounds to plot both portfolio and asset performance relative to desired profit margins, which can be customized per asset type
* Use the `portfolio_selection` and `asset_selection` functions to plot portfolio and asset performance relative to their type-specific bounds
  * **Note (minor issue):** Currently fixing the reassignment of the `date_range` variable per execution of cell(s) that contain the `asset_selection` function. Cells that use the `asset_selection` function need to be run twice for now (once for variable reassignment, and again to show the correct plot for the asset specified). It appears that this issue was also affecting the `portfolio_selection` function only if this cell was executed after cell(s) that contained the `asset_selection` function.

### Step 3 - Calculating Sharpe Ratio & KPIs

[!Sharpe ratio and KPI calculations](https://user-images.githubusercontent.com/102639530/178582486-6ae5395e-ac95-4f4b-ba70-699f73406fac.mp4)

* Calculate annual sharpe ratios per portfolio (assuming a risk-free rate of 0) and numerous KPIs varying from simple cumulative returns to the standard deviation of daily returns
* Assign `n` number of iterations to the `number_ports` variable for the model to test (the model will use these iterations to discover the optimal capital allocation per asset for each portfolio, based on each asset's specific performance)
  * Default is set to 10,000 iterations
* Create nested numpy arrays to store each portfolio's returns, volatility measures, sharpe ratios, and other values per unique iteration

### Step 4 - Plotting `n` number of iterations & analyzing optimized portfolios

[!Discovering optimized portfolio stats](https://user-images.githubusercontent.com/102639530/178560667-2f612e6d-180b-4b14-b49b-b2d13b5f0a49.mp4)

* Create overlaid scatterplot of all `n` iterations per portfolio to compare optimized portfolio's return, volatility, and sharpe ratio compared to the remaining `n-1` iterations
* Develop new pandas dataframes for optimized portfolios by using the iteration that holds the highest sharpe ratio per portfolio. If desired, the exact iteration used can be customized based on the user's preferences
  * EX: Max_return + max_volatility or max_return + min_volatility combinations can be used if desired
    * **NOTE:** _At this time, manual customization is only recommended to users that are familiar with performing operations with nested numpy arrays._
* Examine differences between optimized and standard portfolios per asset type

### Step 5 - Analyzing the model's preferences between given assets per portfolio

[!Analyzing model's optimization decisions](https://user-images.githubusercontent.com/102639530/178560698-f1fc5215-f815-44e3-aa22-d18baf3dcc5e.mp4)

* Analyze performance of the model's favored assets, unfavored assets, and hedges as they compare to the asset's original performances
* Evaluate the financial statistics behind the model's decision-making capabilities (why the model chose to allocate more or less capital to certain assets)
