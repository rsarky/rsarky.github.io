---
layout: post
title: Does height play a role in climbing performance?
---

In this post we will try to see guage the role played by height and weight play in climber
performance. Climber performance, for our purposes, will be represented by the
maximum grade that a climber has climbed. The data for this analysis is sourced
from a [kaggle repository][1] that scraped data from [8a.nu][2]. After some
data cleaning we have around 14500 datapoints. We dont consider routes and
boulders separately here. Let's look at how features in
our data are distributed:

# Data Distribution
![feature-dist](/assets/img/feature-dist.png)

`age_at_start` describes at what age did the user start climbing. `xp` defines
the age at which he or she achieved the max grade defined in `max_grade`. 

# Correlations
![correlation](/assets/img/climber-correlation.png)

It is interesting to note that while height and maximum grade dont seem to be
correlated there is a statistically significant negative correlation (p << 0.5) 
between bmi and
performance of a climber. This makes sense as its not the height alone that has
an effect on climber performance but a combination of weight and height.
As expected, climber experience is positively correlated with the maximum grade achieved.

The following visualisation depicts the gradual shift to lower bmis with higher
grades

![bmi-grage](/assets/img/bmi-grade.png)


<br>
The following graph shows that though the years of experience contribute to a
higher maximum grade, the downward trend of bmi with performance persists
across all experience ranges.
![grade-bmi](/assets/img/grade-bmi-xp.png)

<br><br><br>
In conclusion we verify from the data that its not just height, but height
along with weight (bmi) that plays a role in determining a climber's performance.


[1]: https://www.kaggle.com/dcohen21/8anu-climbing-logbook
[2]: https://www.8a.nu/
