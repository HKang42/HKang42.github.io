---
layout: post
title: COVID-19 Visualization
subtitle: Is it time to panic yet?
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
bigimg: https://www.cdc.gov/coronavirus/2019-ncov/images/home-banner.jpg
tags: [Coronavirus,COVID-19]
comments: true
---

Over the past month, news headlines worldwide have been dominated by a single topic, COVID-19. COVID-19 (colloquially called “the Coronavirus”) originated in mainland China where it infected tens of thousands over the course of several weeks. Since then it has spread abroad, appearing in countries like Iran, Italy, and The United States. The virus’ spread has stoked fear and panic around the world, leading many citizens of all countries to wonder if there’s a pandemic brewing in their own backyards. 

This begs the question: how far has the Coronavirus actually spread? And does it pose a serious and immediate threat?

To answer this question, I will use the [2019 Novel Coronavirus COVID-19 (2019-nCoV) Data Repository](https://github.com/CSSEGISandData/COVID-19) operated by the Johns Hopkins University Center for Systems Science and Engineering. The repository contains data sets that list the number of confirmed cases, recoveries, and deaths from COVID-19. Each data set presents the data as a daily cumulative total for states and countries around the world.

Using this data I was able to generate a geo-scatter plot to visualize the current geographic spread of COVID-19.

![GeoScatter](/img/a1.png){: .center-block :}

The area for each bubble represents the total number of confirmed cases for a country. Any country with at least 1 case has been filled with dark grey. In total, there are 79 bubbles. 

As we can see, the vast majority of cases are still confined to mainland China. There are some notable bubbles in South Korea, Italy, and Iran. However, most other countries have cases that number only in the low hundreds or lower. But how many cases are we looking at exactly?

<center>
| Rank |     Region     | Confirmed Cases |
|-----:|:--------------:|----------------:|
|    1 | Mainland China |           80271 |
|    2 |   South Korea  |            5621 |
|    3 |      Italy     |            3089 |
|    4 |      Iran      |            2922 |
|    5 |     Others*    |             706 |
</center>
 
 \*Others refers to the Diamond Princess Cruise ship.

From the above table, we can see that China dwarfs everyone else as far as number of cases. There's a steep drop off as we go down the list. The U.S. is number 10 with only 153 cases as of this post. Based on the current number and distribution of COVID-19 cases, it appears that while the virus may pose an imminent threat, the average American is quite unlikely to wake up tomorrow and find himself diagnosed with COVID-19. So readers may rest assured that they don't need to panic yet. However, the above data is merely a snapshot in time and doesn't tell us much about the future. So what does the virus' progress look like over time?

In order to answer that question, I plotted the cumulative total of confirmed cases, recoveries, and deaths both within mainland China and outside of China.

## <center>Mainland China \t\t\t Outside China</center>

![COVID_2](/img/COVID_2.jpg){: .center-block :}

This result may seem startling. While it looks like China will be fine going forward, the rest of the world is experiencing a rapid increase in the number of cases.

But this interpretation ignores 2 important things. One, it doesn't look at the story the graphs for mainland China portray. Two, it ignores the axis values. 

The graphs for mainland China show that amidst quarantine efforts, the virus' spread began to level off around 80,000 cases. The number of deaths follorwed a similar trend. While the number of recoveries is still increasing. Since COVID-19 only began to spread abroad after it had infected China, we should expect that the worldwide graphs will mirror China's BUT with a time delay. 

Looking at the axis values, it's important to note that the total number of confirmed cases is quite small relative to the total number of cases and the worldwide population. 

What happens if we redo the graph, but set the y-axis maximum equal to the total number of cases?

![COVID_3](/img/COVID_3.jpg){: .center-block :}

As we can see, the graph for cases outside China looks much less extreme. In fact, it looks like the beginning of the graph for China's cases. This is consistent with our statement earlier about the world graph mirroring China's with a time delay.

