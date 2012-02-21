!SLIDE 
# Reading the Tea Leaves #
## Predicting the future with Ruby! ##
## ~ ##
### Roland Swingler :: @knaveofdiamonds :: LRUG feb 2012 ###

!SLIDE
![image](extrapolating.png)

!SLIDE 
# What is time series data? #

![image](initial_graph.png)

!SLIDE code

    @@@ ruby
    require 'tealeaves'

    @data   = [1.0, 2.3, ... 8.9]
    @period = 1

    TeaLeaves.forecast(@data, @period)
    # => 11.1

!SLIDE center
# Naïve Method #

![image](naive.png)

    @@@ ruby
    prediction = time_series.last

!SLIDE
# Moving Average #

    @@@ ruby
    [1,2,6,4,5].each_cons(3) do |slice|
    # yields slices
    # [1,2,6]
    # [2,6,4]
    # [6,4,5]

    slice.inject(&:+) / 3.0
    # => [3, 4, 5]

!SLIDE center

# What they look like #

![image](naive_graph.png)

!SLIDE

# Single Exponetial Smoothing #

![image](ses.png)

Initial Value for forecast:

![image](initial_f.png)

!SLIDE

# Single Exponetial Smoothing #

![image](ses_expansion.png)

alpha between 0.0 and 1.0

!SLIDE

# Trend #

![image](initial_graph_trend.png)

Can be Additive (Linear) or Multiplicative (Curved)

!SLIDE

# Add a trend term to SES #

![image](holt_forecast.png)

![image](holt_level.png)

Initial value for trend:

![image](initial_trend.png)

!SLIDE

# Trend might vary

![image](holt_trend.png)

!SLIDE

# Seasonality #

![image](initial_graph_season.png)

Can be Additive (Constant) or Multiplicative (Increasing)

!SLIDE

# Add in Seasonality #

![image](hw_forecast.png)

![image](hw_level.png)

trend calculation the same as before

!SLIDE

# Seasonality may vary #

![image](hw_season.png)

!SLIDE bullets center

# Finding the right model #

* Which type of trend, seasonality?
* How do we find alpha, beta and gamma?

!SLIDE

# Final tealeaf forecast #
![image](final_graph.png)

!SLIDE bullets center

# Use Cases #

!SLIDE bullets center

# Future #

* Change from Presentation Driven Development
* Better Optimization
* Confidence intervals
* More statistical methods

!SLIDE center
# Thanks! #

    gem install tealeaves

## Questions? ##
## ~ ##
### Roland Swingler :: @knaveofdiamonds :: LRUG feb 2012 ###