# Incredible_Stock_Trader
This repository includes code that not only creates an optimal algorithm for trading a stock, but also finds the most optimal stocks to trade with such an algorithm.

## Workflow
- The workflow diagram depicts how this code works. It currently shows some of the future ideas listed below in the Future Works section, which will be implemented soon.
![Workflow Diagram](workflow.drawio.svg)

## Stock Finder
- The StockFinder.ipynb script exemplifies the original idea behind the Incredible Stock Trader. It is comprised of an non-optimized version of the algorithm, which is as follows:
  - Checks for bullish MACD (5, 35, 5) Divergence along with a bullish RVI Divergence (10 day span). These two Technical Analysis Indicators (MACD and RVI) are used to determine the signal direction, meaning whether the stock will move up or down.
  - The other key part of the simple StockFinder.ipynb script is the use of two more technical indcators: ATR and ADX. These two indcators are used to determine signal strength. We only buy or sell on strong or meaningful signals. The widespread commonly used settings for ATR and ADX are implemented here: ATR Ratio >= 1 and ADX Signal >= 25.
- These signals on their default settings were enough to generate a list of roughly 500 stocks in which this kind of a trading strategy produces a higher level of profit than the underlying asset, as well as an overall Profitable Trade Ratio (more winning trades than losing ones).
 
## Parameter Optimizer
- The ParameterOptimizer.ipynb script is used as a robust "brute force" parameter optimization method. Remember those technical indicators from the StockFinder.ipynb? Well now, we are going to figure out if we can tweak them in any way to increase profit as well as increase the Profitable Trade Ratio.
- In order to figure out which parameters would be optimal for a given asset, I created a code that loops through over 10,000 different parameter combinations and ultimately stores the most optimized parameters for this trading strategy. This was backtested over the past year's stock data, and took around 2 weeks to run for 500 stocks.
- This code on GitHub is already powerful enough to consistently make a profit and outperform the stock market. My personal code (which I have not uploaded to GitHub for somemwhat obvious reasons) includes another technical indicator which made the profit margins go from really good to crazy good! Please message or email me if you would like to know more about that. (email: amoogat@gmail.com)

## Live Trader
- Using RobinStocks API, this code can actually be used to freely trade according to the buy and sell signals of the optimized algorithm. Because I do not have $25,000 in my Robinhood trading account (and the SEC requires this amount for daytrading), I must wait 24 hours to sell an asset after buying it. For this reason, I have implemented an email notification for those who don't want to risk being marked as a daytrader or who are tentative about letting a robot control their investment portfolio. Rest assured, I have backtested and livetested the LiveTrader.ipynb script and there is no difference between letting the script do the trading versus waiting for the daily emails at the end of the trading day.

## Future Works
- This project has taken much of the last year of my free time, as it involved learning about technical analysis, python, backtesting, etc.. There is a very good chance that I will be updating the code with the following improvements:
  - New Technical Indicator Optimization(s) - There is always more to learn, especially in the field of technical analysis. As I learn more, I will improve this aspect.
  - Stock Classifier - something to classify each stock, perhaps with volatility/sector/price action, as a means of determining optimal parameters for an untested stock without running all 10,000 variations of parameters. Ideally, I will limit the optimization range through a classification of these first 500 stocks, and then re-run all scripts on the remaining 4,500 stocks that can be traded on Robinhood.
  - Candlestick Analysis - I already have the code required to make this happen, I will add it at the end and backtest it. It could act as a multiplier, meaning if the Incredible Stock Trader algorithm is already telling us to buy, and the candlestick analysis is bullish (it looks good for the asset - i.e. Morning Doji Star), then we might choose to buy more of the asset than we would have normally.
  - News Sentiment Analysis - I already have this code as well, in which I use web scraping of Finviz in order to get the most recent news articles on a stock. The code then parses each word and phrase and gives an overall sentiment for the article. I also plan to use this as only a multiplier for the Incredible Stock Trader, and not as a final decision maker on whether to buy or sell.
