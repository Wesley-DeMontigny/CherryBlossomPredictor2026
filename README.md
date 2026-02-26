# Cherry Blossom Peak Bloom Prediction
This is my submission to the annual [International Cherry Blossom Prediction Competition](https://competition.statistics.gmu.edu/), which challenges participants to predict the exact day of the peak Cherry Blossom bloom in different cities utilizing historical datasets, some of which have very few datapoints.

Accurately predicting bloom dates for sites with sparse historical data requires robust generalization. We address this by combining mixed-effects linear modeling with deep learning. First, bloom dates are detrended via a mixed linear model, allowing data-poor sites to borrow statistical strength from data-rich ones, while automatically accounting for site-specific baselines and global warming trends. Second, we capture local temperature idiosyncrasies by pre-training a stacked LSTM on historical NASA POWER temperature data and NOAA ENSO anomalies from 1980 onward. A secondary neural network then processes the LSTM’s latent representations (pooling the preceding 40 days of latent representations with exponentially decaying weights) alongside aggregated chill-hour proxy statistics. This network is trained via mean squared error loss to predict the residuals of the mixed linear model. By summing the mixed-effects projections and the predicted neural network residuals, we reconstruct the 2026 bloom dates. The resulting model achieves a Mean Absolute Error of approximately 4 days on the validation set, indicating strong predictive performance despite data scarcity.

These are the predictions of my model:
| City | DOY | Date |
|---|---|---|
| Kyoto | 89 | March 30 |
| Liestal | 86 | March 27 |
| New York City | 91 | April 1 |
| Vancouver | 81 | March 22 |
| Washington DC | 84 | March 25 |