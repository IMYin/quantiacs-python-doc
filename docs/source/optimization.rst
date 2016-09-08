Optimization
============

To compute several different parameterizations of the same system we can use the ``optimize`` function. To use this feature, place a comment next to the parameter you wish to scan. Within the comment place the parameter domain and step-size between two pound signs (similar to the Matlab vector notation).

The optimizer takes each set of optimization parameters and runs a backtest to return the results (Sharpe Ratio, volatility, etc.) for each parameter value. This is essentially a brute-force method, so keep in mind computation time significantly increases when testing many variables at once or a large range of parameters. Nonetheless, the optimizer is useful for automating a test of several parameters when you’re looking for the best fit variable. The overall format looks like this:

.. code-block:: python

	emaPeriod = 30 #[20:5:90]#

In the above example, we see that the variable 'emaPeriod' will be tested from 20 to 90 in increments of 5, and will return the performance results from each run. This also allows you to extract any specific dictionary result that's found under Trading Results (see :ref:`tradingresults-label` section).

