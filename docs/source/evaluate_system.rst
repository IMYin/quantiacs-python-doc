Evaluating Your System
======================

Backtesting
-----------

Start testing your system by running python command:

``python path/to/trading_system.py``

The only requirement is to have the following at the end of your python file to make the trading system file self-executable:::

	# Evaluate trading system defined in current file.
	if __name__ == '__main__':
		import quantiacsToolbox
	   	results = quantiacsToolbox.runts(__file__)


Alternatively, you can always run the trading system straight from Python console:

``> import quantiacsToolbox``

``> returnDict = quantiacsToolbox.runts('/Path/to/your/TradingSystem.py')``

.. _tradingresults-label:

Trading Results
---------------

``runts`` loads the market data and calls your trading system for each day of the backtest with the most recent market data. It simulates the equity curve for your output values ``p``. The toolbox will return a dictionary of performance values and a plot of your system's performance.

``returnDict`` contains the following fields:

+------------------------------+-----------+--------------------------------------------------+
| Field                        | Data Type | Description                                      |
+==============================+===========+==================================================+
| returnDict['tsName']         | string    | a string that contains the name of your trading  |
|                              |           | system                                           |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['fundDate']       | list      | a list of the dates available to your trading    |
|                              |           | system                                           |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['fundTradeDates'] | list      | a list of the,dates traded by your trading       |
|                              |           | system                                           |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['fundEquity']     | list      | a list defining the equity of your portfolio     |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['marketEquity']   | list      | a list defining the equity earned in each market |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['marketExposure'] | list      | a list containing the equity made from each      |
|                              |           | market in settings['markets']                    |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['errorLog']       | list      | a list describing any errors made in evaluation  |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['runtime']        | float     | a float containing the time required to evaluate |
|                              |           | your system                                      |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['evalDate']       | int       | an int that describes the last date of           |
|                              |           | evaluation for your system (in YYYYMMDD format)  |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['stats']          | dict      | a dict containing the performance statistics of  |
|                              |           | your system                                      |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['settings']       | dict      | a dict containting the settings defined in       |
|                              |           | mySettings                                       |
+------------------------------+-----------+--------------------------------------------------+
| returnDict['returns']        | list      | a list defining the market returns of your       |
|                              |           | trading system                                   |
+------------------------------+-----------+--------------------------------------------------+

