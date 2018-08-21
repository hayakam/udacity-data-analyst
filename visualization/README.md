
# Analysis on the trend of flight cancellation in U.S. 2008

<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#1.-Summary" data-toc-modified-id="1.-Summary-1">1. Summary</a></span></li><li><span><a href="#2.-Design" data-toc-modified-id="2.-Design-2">2. Design</a></span><ul class="toc-item"><li><span><a href="#2-1.-Initial-Design" data-toc-modified-id="2-1.-Initial-Design-2.1">2-1. Initial Design</a></span><ul class="toc-item"><li><span><a href="#1.-Monthly-cancellation-trend-(When?)" data-toc-modified-id="1.-Monthly-cancellation-trend-(When?)-2.1.1">1. Monthly cancellation trend (When?)</a></span></li><li><span><a href="#2.-Cancellation-trend--by-cancellation-code-(Why?)" data-toc-modified-id="2.-Cancellation-trend--by-cancellation-code-(Why?)-2.1.2">2. Cancellation trend  by cancellation code (Why?)</a></span></li><li><span><a href="#3.-Cancellation-trend-by-airport-(Where?)" data-toc-modified-id="3.-Cancellation-trend-by-airport-(Where?)-2.1.3">3. Cancellation trend by airport (Where?)</a></span></li><li><span><a href="#4.-Cancellation-trend-by-carrier-(Who?)" data-toc-modified-id="4.-Cancellation-trend-by-carrier-(Who?)-2.1.4">4. Cancellation trend by carrier (Who?)</a></span></li><li><span><a href="#5.-Conclusion" data-toc-modified-id="5.-Conclusion-2.1.5">5. Conclusion</a></span></li></ul></li><li><span><a href="#2-2.-Revised-Design" data-toc-modified-id="2-2.-Revised-Design-2.2">2-2. Revised Design</a></span></li></ul></li><li><span><a href="#3.-Feedback" data-toc-modified-id="3.-Feedback-3">3. Feedback</a></span></li><li><span><a href="#4.-Resources" data-toc-modified-id="4.-Resources-4">4. Resources</a></span></li></ul></div>

## 1. Summary

This project anlyse the trend of flight cancellations in U.S. in 2008 based on [this data](http://stat-computing.org/dataexpo/2009/the-data.html). Trend was analysed from 4 different perspectives, when, where, who, and why the fligths were cancelled. Top factors for each perspective are identified and explained in the [project story](https://public.tableau.com/views/Flightsdataver3/Story1?:embed=y&:display_count=yes&publish=yes).

## 2. Design

### 2-1. Initial Design
The Story is to be consisted of below 5 slides:

#### 1. Monthly cancellation trend (When?)
    Consists of 3 charts that show total number of flights, number of cancelled flights, and cancellation ratio for each month respectively.
    
    
#### 2. Cancellation trend  by cancellation code (Why?)
    Consists of 2 charts:
    * bar chart that show the number of cancelled flights by cancellation code
    * bar chart by cancellation code with monthly breakdown 
    * Color-blind palete is to be used for coloring. This is applicable for all the later charts in this story.
    
    
#### 3. Cancellation trend by airport (Where?)
    Consists of 1 dashbord that contains 3 bar charts and 1 map:
    * bar chart that shows cancelled flights by month and cancellation code
    * horizontal bar chart that shows number of cancelled flights by origin airport
    * horizontal bar chart that shows number of cancelled flights by desitination airport
    * map with that shows the origin and destination airport and its size
    * 2 drop down boxes to filter the charts by month and cancellation code
    
#### 4. Cancellation trend by carrier (Who?)
    Consists of 1 dashbord that contains 2 bar charts:
    * horizontal bar chart that shows the number of cancelled flights by carrier, colored by cancellation code
    * bar chart that shows monthly breakdwon by cancellation code
    
#### 5. Conclusion
    Consists of 1 dashboard that contains all the charts used in previous slides to hilight the findings in previous slides. The dashboard has 2 drop down boxes for month and cancellation code, so that users can perform their own analysis on a single screen without going back and forth.

### 2-2. Revised Design

* Remove the "Cancellation trend by cancellation code" slide. I realaized that the cancellation code is not necessarily need to have a dedicated slide as it eventually included in other slides.
* Reduce the number of chart in each slide to reduce the repeated use of same chart.
* Remove the fliter drop boxes from each slides and combine them into the final slide.  In initial design, all the slides had filters so that users can perform any arbitrary view. However, I realized that it should be enough if such functions are inplemented only in the final dashboard.
* Add a drop box on the final dashboard to filter the data by `carrier`, in addition to existing dropdowns for `month` and `cancellation code`.

## 3. Feedback

Feedback from the colleague through Udacity DAND slack, on [Initial version](https://public.tableau.com/shared/S655XD8XR?:display_count=yes)

> Hey Masa, your project looks neat. The story is there, the visualizations look good, and the conclusion is well enforced. It has a lot of visualizations, maybe I am wrong but it feels like some of them are repeating. Maybe you can reduce the number of slides and visualizations. Best of Luck!
(https://udacitydatascience.slack.com/archives/C72AP9J3Y/p1530541225000118)


Following changes are made in the [final version](https://public.tableau.com/views/Flightsdataver3/Story1?:embed=y&:display_count=yes&publish=yes) after received above feedback:
* Number of the slides are reduced from 5 to 4 in order to eliminate repetition. 
* Reduced the number of chart in each slide to reducde repeating use of same chart.
* Removed fliter drop boxes from each slides and combine them into the final dashboard.
* Added a `carrier` drop box on the final dashboard, in addition to existing dropdowns for `month` and `cancellation` code.

## 4. Resources

* [Supplemental data](http://stat-computing.org/dataexpo/2009/supplemental-data.html):<BR> 
    `carriers.csv` and `airports.csv` are used as supplimental data.
* [Cancellation code](http://aspmhelp.faa.gov/index.php/Types_of_Delay): <BR> This is to explain types of delay but I believe it can also be used for cancellation.
* Related readings: [10 Worst Airports in America for Bad Weather](https://www.smartertravel.com/2012/01/18/10-worst-airports-in-america-for-bad-weather/)<BR>According to this article, Chicago O’Hare International Airport(ORD) has quite unique environment and weather condition often disrupts the flights schedule.
