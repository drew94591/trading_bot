# Trading Bot
This application implements an algorithmic trading strategy that uses machine learning to automate the trade decisions.  It then trains and tests this trading strategy between an SVC classifier base model and an Logical Regression model to determine the accuracy using each model.  Both the training and trading algorithms have been tuned by adjusting the size of the training dataset and/or adjusting the SMA input window to find the most optimized settings within the SVC base model.  An Evaluation Report has been created below which analyzes the findings upon comparing the two models.

---


## Technologies

This application leverages python 3.7 with the following libraries and packages:

* [pandas](https://github.com/pandas-dev/pandas) - A flexible and power data analysis/manipulation Python library used in financial calculations.

* [numpy](https://numpy.org) - The fundamental package for scientific computing in Python.

* [path](https://docs.python.org/3/library/pathlib.html) - Used to define file path

* [hvplot](https://pyviz-dev.github.io/hvplot/user_guide/Introduction.html) - Provides a high-level plotting API built on HoloViews that provides a general and consistent API for plotting data.

* [matplotlib](https://matplotlib.org/) - A comprehensive library for creating static, animated, and interactive visualizations in Python.

* [scikit-learn](https://scikit-learn.org/) - A Python machine learning library that provides supervised and unsupervised learning algorithms.

---

## Installation Guide

Before running the application first install the following dependencies.

```python
!pip install hvplot
!pip install -U scikit-learn
```

---

## Usage

To use the trading bot application you must first launch Jupyter Lab by executing the following command within Git Bash:

```python
jupyter lab
```

Within Jupyter Lab you should then be able to run and execute the following notebook:

``` python
machine_learning_trading_bot.ipynb
```

## Overview of the Analysis

* The purpose of the application is to see which learning model among the SVC classifier model and the Logical Regression Model performed the best in predicting the trading strategy returns versus the 
  actual returns.

* In addition, by adjusting the size of the training dataset and/or adjusting the SMA input window we are able to find the most optimal setting within the SVC base model for the trading strategy used.

## Results

* Baseline SVC Machine Learning Model:
  * SMA Fast with a 4 day moving average
  * SMA Slow with a 100 day moving average
  * 3 month training data
  * This baseline model had an accuracy precision score of 56% in predicting when to enter a trade and a precision score of 43% in predicting when to exit a trade.  Though a recall score of 4% on exiting 
    a trade is relatively low compared to the 96% recall score of entering a trade in it's prediction.  The overall accuracy F1-score is 55%.  I believe we can tweak the settings a little bit and get
    more optimal results.
  * Refer to the svc_returns_using_original_parameters.png plot

* Most Optimal settings for SVC Machine Learning Model:
  * By increasing the SMA Fast setting from a 4 day moving average to a 50 moving average
  * By increasing the SMA Slow setting from a 100 day moving average to a 200 moving average
  * By increasing the 3 month training data to a 6 month training data
  * The newly tuned model had an accuracy precision score of 57% in predicting when to enter a trade and a precision score of 45% in predicting when to exit a trade.  The recall score has improved from
    the baseline of 4% to now 35% in it's prediction on exiting a trade even though the entering a trade prediction recall score decreased slightly to 73%.  The overall accuracy F1-score remains 
    relatively the same at around 55%.
  * Refer to the svc_returns_optimized_settings.png plot
  
* Logical Regression Machine Learning Model with baseline settings:
  * SMA Fast with a 4 day moving average
  * SMA Slow with a 100 day moving average
  * 3 month training data
  * This logical regression model had an accuracy precision score of 56% in predicting when to enter a trade and a precision score of 44% in predicting when to exit a trade.  Although the recall score
    has improved tremendously from the baseline of 4% to now 33% upon predicting exiting a trade even though the entering a trade recall score decreased slightly to 66%.  The overall accuracy F1-score 
    also slightly dropped from 55% to 52%.
  * Refer to the lr_returns_using_original_parameters.png plot.
  
## Summary

* In summary, we can conclude that by using the SVC classifier model with the optimal settings of SMA Fast of 50 days and SMA Slow of 200 days and increasing the size of the training data set from
  3 months to 6 months we are able to achieve the most accurate predictions on the trading strategy returns. The SVC model at these settings was more accurate in predicting the returns compared to the
  Logical Regression model as well.

---

## Contributors

Brought to you by [Drew Herrera](https://www.linkedin.com/in/drew94591).

---

## License

Licensed under the MIT License. Copyright 2022 Drew Herrera.


