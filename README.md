# Personal_Portfolio_Optimization

This repo is going to showcase the outcomes of investing $150,000 in each of three portfolios: a stock portfolio (focusing on tech companies), a crypto portfolio (focusing on some of the top cryptos), and an index portfolio. Each of these portfolios will have their initial capital of $150,000 evenly distributed among all of their assets.

After analyzing the performance of each portfolio and asset(s) per portfolio, sharpe ratios will be calculated in order to create a portfolio optimization model. This model will seek to strategically maximize returns while showcasing a strong ability to minimize downside risk where possible.

## Model setup

### Step 1 - Designing the portfolios as pandas dataframes

* Adjust timelines as desired via the start and end date variables
* Assign initial portfolio values (ideally using `portfolio_value` as the constant variable for all three portfolios)
* Specify the desired assets for each portfolio (i.e. which stocks will be analyzed in the stock portfolio, which cryptos will be analyzed in the crypto portfolio, etc.)
* Choose the method of capital distribution for assets (default is set to even distribution)
  * EX: A portfolio with `n` assets will have a distribution of `(1/n) * portfolio_value`

#### **A note on using variables**

* All variables with an `st_` prefix are utilized for stock-related variables
* All variables with a `cr_` prefix are utilized for crypto-related variables
* All variables with an `ind_` prefix are utilized for index-related variables

### Step 2 - Plotting & analyzing portfolio / asset performance

* Assign customizable upper / lower bounds to plot both portfolio and asset performance relative to desired profit margins, which can be customized per asset type
* Use the `portfolio_selection` and `asset_selection` functions to plot portfolio and asset performance relative to their type-specific bounds
  * **Note:** Currently fixing the reassignment of the `date_range` variable per execution of cell(s) that contain the `asset_selection` function. Cells that use the `asset_selection` function need to be run twice for now (once for variable reassignment, and again to show the correct plot for the asset specified)


[!Plotting portfolio and asset performance](https://user-images.githubusercontent.com/102639530/178553981-beb5d6c0-7526-468b-bdc1-ed77971c9261.mp4)


### Step 3 - Calculating Sharpe Ratio & KPIs

* Calculate annual sharpe ratios per portfolio (assuming a risk-free rate of 0) and numerous KPIs varying from simple cumulative returns to the standard deviation of daily returns
* Assign `n` number of iterations for the model to test (the model will use these iterations to discover the optimal allocation of assets per portfolio)
  * Default is set to 10,000 iterations
* Create numpy arrays to store each portfolio's returns, volatility measures, sharpe ratios, and other values

### Step 4 - Plotting `n` number of iterations & analyzing optimized portfolios
[!Test](https://user-images.githubusercontent.com/102639530/178357841-cc4aba59-600a-4341-8791-61016718f79e.mp4)

* Overlay scatterplots of all iterations for each portfolio
* Develop new pandas dataframes for optimized portfolios using the numpy arrays which hold the highest sharpe ratios
* Examine differences between optimized and standard portfolios per asset type
* Analyze performance of the model's favored assets, unfavored assets, and hedges as they compare to the standard portfolios to understand why the model chose to allocate more or less capital to certain assets

[!Waza](https://user-images.githubusercontent.com/102639530/178367809-35d9e605-4de8-4260-8637-8dee2938784c.mp4)

