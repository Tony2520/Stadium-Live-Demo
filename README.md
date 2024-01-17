# Stadium Live Demo: My work for the past 8 months:

If you want to check out the app -> https://www.stadiumverse.com/

Stadium Live is a rising betting / fantasy mobile app with around 80k daily active user and 250K total downloads. With an engineering team of 8,
I hit the ground running and shipped multiple complex, end-to-end features. Below are 4 most note-worthy ones.

## Feature#1: User Profile Revamp📱

- Complete overhaul of old user profile
- Refractored old profile queries using graphql batching and caching for speedy performance gains 
- Smooth, animated scrolling components inspired by Twitter profiles

<table style="border: none;">
  <tr>
    <td style="border: none;"><img src="https://github.com/Tony2520/Stadium-Live-Demo/assets/117308186/dc46c19e-9479-48c6-a5b1-08e34521de76" alt="Old Profile" style="width: 200px;"></td>
    <td style="border: none;"><img src="https://github.com/Tony2520/Stadium-Live-Demo/assets/117308186/3d3308b5-0b7a-485d-b004-9cce3bdaa8ae" alt="New Profile" style="width: 200px;"></td>
  </tr>
</table>

## Installation :hammer_and_wrench:
Sup-Res requires Python 3.10+ to run.
Use the package manager [pip](https://pip.pypa.io/en/stable/) to install libraries. This process may take a long time.

```bash
pip install -r requirements.txt
```

## Usage :computer:
This tool allows you to generate charts for different cryptocurrencies and time frames using the Binance API.
When you run the code, main function will ask ticker and time frame and then the local web page will open where you can see the support-resistance levels, RSI, SMA, MACD, Fibonacci and candlestick patterns. 

You can run the script with arguments for the ticker and time frame you want to generate a chart for. To do this, enter the following command:
````python
python main.py <ticker> <timeframe>
````
For example, to generate a chart for the BTCUSDT ticker with a 1-hour time frame, you would enter:
````python
python main.py BTCUSDT 1H
````
You can also run the script without any arguments and then enter the ticker and time frame in the command line when prompted. To do this, enter the following command:

````python
python main.py 
````
If you want to generate charts for multiple pairs at once, you can use the `multiple_run.py` script located in the miniscripts directory. This script will generate charts for all the pairs listed in the `coin_list.csv` file. To run this script, enter the following command:
````python
python miniscripts/multiple_run.py
````

````
Supported Tickers: 
All Binance tickers
Supported Time Frames: 
1M, 3M, 5M, 15M, 30M, 1H, 2H, 4H, 6H, 8H, 12H, 1D, 3D, 1W (M: Minute, H: Hour, D: Day, W: Week)
````

If you want to share as a tweet, change api keys with yours in `git_tw_access.py` file, and change your user handle name. [Twitter API guide](https://developer.twitter.com/en/docs/twitter-api). Then uncomment `save` and `twitter` functions in `main.py`.

````python
# Twitter api keys -> https://developer.twitter.com/en/docs/twitter-api
twitter_api = 'YOUR-API'
twitter_key_secret = 'API-SECRET'
twitter_token = 'TOKEN'
twitter_token_secret = 'TOKEN-SECRET'
user_handle = '@HANDLE-NAME'
````

Pine Script file will be created after run successfully main function. 

Your python alias might be different like "py, python3", you should change your alias if you are using telegram-bot if your python alias is different. 

>By adjusting the sensitivity of the data in the code, you can obtain lines that are more precise.


![chart](https://user-images.githubusercontent.com/32988819/166165460-b1e2be3e-014c-4aea-83e6-c118075f68df.png)


 
## Main Motivation :books:
Those who are new to investing do so without any technical expertise. Additionally, individuals who have limited experience make their buys and sells in accordance with various charts and follow the price actions. The main focus of this work is technical analysis.

I worked on a piece of code that could be useful for users with little prior knowledge of price action. Don't invest if you really have no idea what you're doing. You should keep an eye on market trends before investing and try not to feel **FOMO**.

Zones rather than just lines typically represent supports and resistances. Markets push you toward points where you can stop your position, particularly in cryptocurrencies. Keep an eye out for breakouts with high volume, sudden price changes, and trend reversals. It is extremely risky to trade on new coin charts without support and resistance levels if you are investing in low volume coins.


![image](https://user-images.githubusercontent.com/32988819/166165539-5a4eea0a-456e-482d-aa56-96b5eaffc37a.png)


## Support-Resistance Lines :chart_with_downwards_trend:

You can draw a trustworthy line at a point where a pair has repeatedly failed to break it or has advanced by tapping it. The consensus is that this price should be touched at least twice and ideally three times. Reliability rises as the number of touches increases. If the price moves below the support line, this support will act as resistance. The opposite is also true. If the price breaks the resistance, it can work as support, but these situations should be fully supported by volume.

![28sep](https://user-images.githubusercontent.com/32988819/135044659-579b26c8-8141-41c2-9b4e-d3c99b41b571.png)


_28 September 2021 BTCUSDT Binance_

## Indicators :bar_chart:
[MA](https://www.investopedia.com/terms/m/movingaverage.asp), 
[RSI](https://www.investopedia.com/terms/r/rsi.asp), 
[MACD](https://www.investopedia.com/terms/m/macd.asp),
[Fibonacci Retracement Levels](https://www.investopedia.com/terms/f/fibonacciretracement.asp),
[Candlestick Patterns](https://www.elearnmarkets.com/blog/30-candlestick-charts-in-stock-market/)

Never rely solely on a single piece of information or indicator as this can be deceptive. Fundamental analysis should always be combined with technical analysis.

![legend](https://user-images.githubusercontent.com/32988819/168901021-81d885d4-19de-4ba6-a3d0-c69faf2ccbf5.png)

## Pine Script :bookmark_tabs:

Sup-Res supports Pine Script scripting language. Just **run** *main.py* file, then **copy** "./pinescript.txt" and **paste** *Tradingview Pine Script* section.
Also telegram bot works with Pine Script.

Here is the example Pine Script code:
````
//@version=5
indicator('Sup-Res BTCUSDT 1d', overlay=true)
plot(ta.sma(close, 50), title='50 SMA', color=color.new(color.blue, 0), linewidth=1)
plot(ta.sma(close, 100), title='100 SMA', color=color.new(color.purple, 0), linewidth=1)
plot(ta.sma(close, 200), title='200 SMA', color=color.new(color.red, 0), linewidth=1)
hline(18626.0, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
hline(18910.94, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
hline(19706.66, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
hline(20111.62, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
hline(21888.0, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
hline(22799.0, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
hline(24668.0, title="Lines", color=color.red, linestyle=hline.style_solid, linewidth=1)
````

## Contributing :handshake:
Pull requests are welcome, any contributions you make are greatly appreciated. Please open an issue with what you want changed before submitting a PR.

Follow [PEP 8 Coding Style guidelines](https://www.python.org/dev/peps/pep-0008/).

- Fork the Project
- Create your Feature Branch `git checkout -b feature/NewFeature`
- Commit your Changes `git commit -m 'Add some NewFeature'`
- Push to the Branch `git push origin feature/NewFeature`
- Open a Pull Request


## License :page_with_curl:
Sup-Res is licensed under the GNU General Public License v3.0
