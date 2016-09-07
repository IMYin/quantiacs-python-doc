Trading System Structure
========================

In Python, you have to define two functions: ``mySettings`` and ``myTradingSystem``. The toolbox relies on these two functions to run your trading system. ``mySettings`` contains the settings structure which stores all relevant information for the trading system. The toolbox allows for flexible data definitions, where you can request OPEN, HIGH, LOW, CLOSE, or VOL data for your system. A typical function definition is shown below: 

.. py:function:: def myTradingSystem(DATE, HIGH, CLOSE, VOL, exposure, equity, settings)

Your ``myTradingSystem`` function will be called each day of the backtesting period with the most recent data as arguments. The only requirements of ``myTradingSystem`` is to return an array of your trading system’s market positions for the next day and the settings data struct. Market positions, ``p``, is just an array of numbers [0 1 -1 …] that represents the trading positions you want to take (e.g., no position, buy, sell).

Arguments/Parameters
--------------------
Data can be requested for your trading system through the arguments of the function definition. The ``myTradingSystem`` function isn’t required to call any arguments, the example above is just a representation of various values that can be called.

+--------------+--------------------------------------------------+------------------+
| Parameter    | Description                                      | Dimensions       |
|              |                                                  | (rows x columns) |
+==============+==================================================+==================+
| **DATE**     | DATE,a date integer in the                       | Lookback x 1     |
|              | format YYYYMMDD                                  |                  |
+--------------+--------------------------------------------------+------------------+
| **OPEN**     | the first price of the session                   | Lookback x       |
|              |                                                  | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **HIGH**     | the highest price of the session                 | Lookback x       |
|              |                                                  | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **LOW**      | the lowest price of the session                  | Lookback x       |
|              |                                                  | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **CLOSE**    | the last price of the session                    | Lookback x       |
|              |                                                  | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **VOL**      | number of stocks/contracts                       | Lookback x       |
|              | traded per session                               | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **exposure** | the realized quantities of your trading system,  | Lookback x       |
|              | or all the trading positions you take            | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **equity**   | cumulative trading performance in each market,   | Lookback x       |
|              | reflects gains and losses                        | # of Markets     |
+--------------+--------------------------------------------------+------------------+
| **OI, R,     | Also available to be called as parameters,       |                  |
| RINFO**      | described in more detail under Market Data       |                  |
+--------------+--------------------------------------------------+------------------+

The data is structured with the most recent information in the last index or row. Where **lookback** is simply how many historical data points you want to load in each iteration of your trading system. Given the data is daily, lookback represents the maximum number of days of market data you want to have loaded. Now the two parameters that aren’t explicitly related to market data are **exposure** and **equity**. These two relate to trading in your simulated broker account. Whenever you make a trading position, that’s recorded in **exposure**. And whatever the market result of your trading position is, is then recorded in **equity**. Or simply put: **equity** is what you made with each market over your **lookback** period.
