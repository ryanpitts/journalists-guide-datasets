American Community Survey
=========================

The [American Community Survey](https://www.census.gov/acs/www/) is a product of the [United States Census Bureau](http://census.gov). This ongoing survey collects data from a small percentage of the population each year, covering a variety of topics beyond the basic demographic information contained in the decennial Census. In addition to age, sex, and race, the ACS gathers data in categories like family type, housing, income, education, occupation, transportation, and veteran status.

Governmental agencies use ACS data to inform policy and decide how to allocate services. Because the survey asks questions about so many aspects of American life, it is also a rich source of stories for journalists.  For the largest geographies, [ACS summary data](https://www.census.gov/acs/www/data_documentation/summary_file/) is available going back to 2005. Estimates from smaller places were added in 2007 and 2009.

It is important to remember that the American Community Survey is, indeed, a survey, so the estimates in each release are derived from statistical sampling. Depending on the population of a place, or even the size of group for whom a specific survey question is relevant, the Census Bureau may need to compile more than one year's worth of responses in order to deliver statistically meaningful estimates.

In This Guide
=============

* [Releases: 1-year vs. 3-year vs. 5-year](#releases)
    * [Comparing ACS data from different releases](#comparing-acs-data-from-different-releases)
    * [Comparing ACS data from different geographies](#comparing-acs-data-from-different-geographies)
    * [Comparing ACS data over time](#comparing-acs-data-over-time)
* [Table universes](#table-universes)
* [Margins of error](#margins-of-error)
* [Summary levels](#summary-levels)
* [Finding ACS data](#finding-acs-data)
* [Authors](#authors)

Releases
========

The Census Bureau produces [three American Community Survey releases](https://www.census.gov/acs/www/guidance_for_data_users/estimates/) each year: the 1-year, the 3-year, and the 5-year. Choosing the appropriate release for your analysis depends on the size of place you are researching, as well as the precision of estimate you need.

### 1-year release
The 1-year release provides data for all geographies of population 65,000 and above. Estimates are generated from 12 months of survey responses, so while results are more current than the other two releases, they also represent the smallest sample size.

### 3-year release
The 3-year release provides data for all geographies of population 20,000 and above. Estimates are generated from 36 months of survey responses, so results are not as current as the 1-year release, but are more precise.

### 5-year release
The 5-year release provides data for all geographies regardless of size. If you are looking for information that goes down to the tract level, for instance, this is likely the release you want. Estimates are generated from 60 months of survey responses, so results are the least current, but most precise.

### Comparing ACS data from different releases
Any time you compare ACS data, it is important to keep the sampling method for each release in mind. The 2012 1-year release, for example, is derived from responses to the 2012 survey alone. The 2012 3-year release is derived from responses from 2010 through 2012, and the 2012 5-year release goes back further still, producing estimates based on data from 2008 through 2012.

Because of this, you should never compare data from different release levels.

### Comparing ACS data from different geographies
If you are comparing data from different places (even if they're the same type of geography), you'll need to get all your data from the release that contains the smallest place in your comparison.

A common example of this is performing a comparison of all counties in a state. Most states contain at least some small counties, with populations that aren't big enough to be included in the 1-year release. So if you go looking for 1-year data, you'll find some counties, but not all. (Maybe you only *want* to compare large counties, in which case you're fine.) But because you can't compare 1-year data from large counties against 3- or 5-year data from the smaller counties, if you want to analyze the complete set, you'll need to choose a single level that includes all of them.

### Comparing ACS data over time
The Census Bureau began collecting ACS data nearly a decade ago, providing a great opportunity to analyze the ways an area has changed over time. It is important, however, to keep the sampling methods for each release in mind.

Just as in comparisons of different geographies, when you are comparing data from different years, you should only compare within the same release level (e.g. 1-year vs 1-year, 3-year vs. 3-year, and 5-year vs. 5-year). In addition, you should only compare *adjacent* releases, that is, release where the sampled years do not overlap.

For example, the 2012 3-year release samples data from 2010 through 2012, and the 2011 3-year release samples data from 2009 through 2011. Because both contain data from the 2010 and 2011 ACS surveys (but not necessarily the same amount of data from either year), it is impossible to make significant statements about changes between these two releases.

The 2009 3-year release, however, samples data from 2007 through 2009. This makes it adjacent to the 2010-2012 data in the 2012 3-year release, so it would be fair to compare those two releases.

Thankfully, comparing 1-year releases is much simpler. Each 1-year release contains data from a single year, so looking at the 2007 through 2012 1-year release data would give you a nice 6-year timeline of change. Provided the geographies you are analyzing are big enough to exist in the 1-year datasets, of course.

Comparing 5-year release data over time, however, is currently impossible. The first 5-year release is from 2009, and samples surveys back through 2005. So there won't be adjacent data available until the 2014 5-year release.

Table universes
===============
Each table of data in the American Community Survey is derived from what the Census Bureau calls a "universe": the population from whom answers to a particular survey question are relevant. For a table like B01002 ("Median Age by Sex"), you'll see a universe of "Total Population," meaning the estimates in this table are derived from sampling everyone in the geography you are analyzing.

For a table like B24011 ("Occupation by Median Earnings for the Civilian Population"), however, the universe is "Civilian Employed Population 16 Years and Over With Earnings." Parsing that out, you can infer that the estimates in this table do not include data from military personnel, children under 16 years old, people who are unemployed, and volunteer workers.

Many ACS tables have a universe that is *not* "Total Population," which is important to track before citing figures. For example, if you were writing a story about how many people in your town heat their homes with wood, you would need to note that the universe for Table B25040 ("House Heating Fuel") is "Occupied Housing Units" &emdash; an estimate that doesn't even count people. So to derive a percentage figure, you would divide by the number of total occupied units, not total residents.

These universes also mean that you may have to search across multiple ACS releases to find all data for a specific place. For example, consider a county with 70,000 residents. That's big enough for the "Age by Sex" table (with a universe of "Total Population") to exist in the 1-year release. But it's unlikely that all 70,000 residents are civilians over 16 with jobs, so to find data for "Occupation by Median Earnings for the Civilian Population," you'd have to check the 3- or 5-year release.

Margins of error
================
Because ACS data for a given place is derived from a sample of its population, each estimate carries with it a margin of error. Depending on the place's population (or the size of a particular table universe), these margins of error can sometimes be quite high.

You should keep this relative lack of precision in mind when choosing language to describe this data. You wouldn't, for example, want to say "According to the 2012 American Community Survey, there are 975,139 twentysomethings living in Washington state." That particular statistic has a margin of error of +/- 10,119.6. It *would* however, be reasonable to say "about 14 percent of Washingtonians are in their 20s."

Margins of error are also important to consider when comparing places against one another. One county may have a higher estimated number of people with bachelor's degrees than another, but beware of overlapping margins of error. It may not be entirely accurate to write that the first county is outpacing the second.

The same goes for comparing groups of geographies. According to the estimates, County A may rank 4th in bachelor's degrees, but overlapping margins of error might mean that it *really* ranks anywhere between 3rd and 6th.

Summary levels
==============
The Census Bureau uses summary levels to classify [different types of geographies](https://www.census.gov/geo/reference/garm.html). These range in size from the entire nation (summary level 010) all the way down to census blocks (summary level 101). The smallest unit of geography in the ACS is the [block group](https://www.census.gov/geo/reference/gtc/gtc_bg.html) (summary level 150).

Some, but not all, summary levels are entirely contained by a parent summary level. For example. All states exist within the United States (of course), and all counties are contained by a specific state. All census places (or cities) are also contained by a state, but *not* necessarily by a county. A [chart of these parent/child relationships](http://mcdc.missouri.edu/allabout/sumlevs/) might be helpful here.

Summary levels can be [incredibly granular](http://factfinder2.census.gov/help/en/glossary/s/summary_level_code_list.htm), but here is a list of codes for the most common geographies you might want to analyze.

* 010: United States

* 020: Region

    These [divide states into four groups](https://www.census.gov/geo/reference/gtc/gtc_census_divreg.html): Northeast, Midwest, South, and West

* 030: Division

    These [further divide regions into nine groups](https://www.census.gov/geo/reference/gtc/gtc_census_divreg.html)

* 040: State

* 050: County

* 060: County Subdivision

    Different states divide counties in different ways for different reasons, so whether or not this summary level matters to a journalist is dependent on the states being investigated. For example, in New Jersey, county subdivisions provide data for more "town-like" places than the "place" (160) summary level.

* 140: Census Tract

    Fairly stable census-defined geographies with a target population of about 4000. Before every decennial census, the Census Bureau reviews the census tract map, and sometimes splits or joins tracts which have gone far from that target. For this reason, comparison of census tracts over time must be handled with caution. 

* 150: Block Group

    These are made up of Census blocks, and block groups are used to form Census tracts. As noted above, this is the smallest summary level for which the Census Bureau provides sample data. They generally have a population of 600 to 3,000.

* 160: Place

    The Census Bureau term for what you'd commonly refer to as a city. Some non-incorporated areas, known as "Census designated places" are also included in this tabulation.

* 250: American Indian Area/Alaska Native Area/Hawaiian Home Land

* 310: Metropolitan/Micropolitan Statistical Area

    Metropolitan statistical areas represent an urbanized core with a population of at least 50,000. Micropolitan statistical areas have a population of at least 10,000 but less than 50,000. The general census term for both metropolitan and micropolitan SAs is "core-based statistical areas" or CBSAs. By definition, CBSAs comprise a specific list of counties, although which counties are included in a CBSA changes based on population and economic change.

* 330: Combined Statistical Area

    These are [groupings of metropolitan or micropolitan statistical areas](https://www.census.gov/geo/reference/gtc/gtc_cbsa.html) that have "substantial employment interchange."

* 500: Congressional District

* 610: State House (Upper)

* 620: State House (Lower)

* 795: Public Use Microdata Area

    Commonly referred to as a [PUMA](https://www.census.gov/geo/reference/puma.html). These are geographically contiguous areas with a population of at least 100,000.

* 860: 5-digit ZIP Code Tabulation Area

   Technically, ZIP Codes are not defined geographically. However, most ZIP Codes can be drawn on a map, and they are a more familiar reference than Census tracts, so by popular demand, the Census Bureau produces data that fits people's intuitive sense of how ZIP Codes work.

* 950: School District (Elementary)

    Some states have school districts specifically for the elementary level.
    
* 960: School District (Secondary)

    Some states have school districts specifically for the secondary level.

* 970: School District (Unified)

    A school district that governs both elementary and secondary schools.

Finding ACS data
================
The Census Bureau provides [a range of products](https://www.census.gov/data/data-tools.html) based on ACS data, the most comprehensive of which is [American FactFinder](http://factfinder2.census.gov/faces/nav/jsf/pages/index.xhtml). Bulk data downloads are also available [directly](http://www2.census.gov/) or [via FTP](ftp://ftp2.census.gov/). American FactFinder isn't particularly easy to navigate, however, and bulk downloads require some complex joins before you can begin to look at the data.

You may have an easier time using [Census Reporter](http://censusreporter.org), a website built specifically for reporters, editors and newsroom developers interested in using ACS data. Census Reporter is a Knight News Challenge-funded project, and includes profile pages for all census geographies, comparison tools to help you explore tables and analyze collections of places, and visualizations for a more useful first look at the data.

Authors
=======

Ryan Pitts is director of code for [Knight-Mozilla OpenNews](http://opennews.org/), and Joe Germuska is chief nerd for [Knight Lab at Northwestern University](http://knightlab.northwestern.edu/). After working with Census data for newsroom stories and projects like [this 2010 decennial Census explorer](http://data.spokesman.com/census/2010/washington/) and [census.ire.org](http://census.ire.org), they were part of the team who built [Census Reporter](http://censusreporter.org).
