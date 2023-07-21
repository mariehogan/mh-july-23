july 20 practice
================
Marie Hogan
2023-07-21

- <a href="#my-goal-make-a-calendar-using-the-calendr-package"
  id="toc-my-goal-make-a-calendar-using-the-calendr-package">My Goal: Make
  a Calendar Using the calendR Package</a>
  - <a href="#the-default-calendar-from-calendr-looks-like-this"
    id="toc-the-default-calendar-from-calendr-looks-like-this">The default
    calendar from calendR looks like this</a>
  - <a href="#customizing-the-date-range"
    id="toc-customizing-the-date-range">Customizing the Date Range</a>
  - <a href="#more-customization" id="toc-more-customization">More
    Customization</a>
  - <a href="#adding-a-background-image"
    id="toc-adding-a-background-image">Adding a Background Image</a>

### My Goal: Make a Calendar Using the calendR Package

A secondary goal is to continually commit and push my changes to a
Github repository as practice.

``` r
library(tidyverse)
library(calendR)
library(lubridate)
```

#### The default calendar from calendR looks like this

``` r
calendR()
```

![](mh-july-20-23-practice_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

I don’t like this. I want a dateless calendar for tracking work
progress. I also want it to be prettier. I am using [this r-coder
tutorial](https://r-coder.com/calendar-plot-r/) as my resource for
customization.

#### Customizing the Date Range

``` r
#start calendar today
starting_day <- today()
#end a week from today
ending_day <- today() + weeks()
#generate calendar
calendR(start_date = starting_day,end_date = ending_day)
```

![](mh-july-20-23-practice_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

I now want to remove the large numbers in the middle of the day boxes.

``` r
calendR(month = month(today()), year = year(today()),
        #color the weekends
        special.days = "weekend",
        special.col = "pink",
        low.col = "lightblue",
        
        #add labels to special days
        text = 
          c("landed","moved in","first day of work","today"),
        text.pos = c(3,8,10,day(today())),
        text.size = 2,
        text.col = "purple"
        )
```

![](mh-july-20-23-practice_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

I had trouble changing the color or text position or text size, even
though I am following the tutorial. I thought maybe it would help to
revert to a monthly rather than custom range calendar since there’s more
functionality with monthly calendars. See above: it may have helped?

This calendar will update the time frame to stay in the current month
and year, so long as you refresh it. The “today” label works the same
and will change as the date changes.

#### More Customization

``` r
calendR(month = month(today()), year = year(today()),
        #color the weekends
        special.days = "weekend",
        special.col = "pink",
        low.col = "lightblue",
        
        #add labels to special days
        text = 
          c("landed","moved in","first day of work","today"),
        text.pos = c(3,8,10,day(today())),
        text.size = 2.5,
        text.col = "purple",
        
        #set day number size smaller, match color
        day.size = 2,
        days.col = "purple"
        )
```

![](mh-july-20-23-practice_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

#### Adding a Background Image

``` r
calendR(month = month(today()), year = year(today()),
        
        #to save as pdf, uncomment the next line
        #pdf = TRUE,
        
        #color the weekends
        special.days = "weekend",
        special.col = "hotpink2",
        low.col = "lightblue",
        
        #set day number size smaller, match color
        day.size = 3,
        days.col = "azure4",
        
        
        #set background color
        bg.col  = "azure2",
        #set line thickness
        lwd = 2.5,
        #font style
        font.style = "bold",
        
        #add lunar calendar
        lunar = TRUE,
        lunar.col = "darkslategray4",
        lunar.size = 3
      
        )
```

![](mh-july-20-23-practice_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->
