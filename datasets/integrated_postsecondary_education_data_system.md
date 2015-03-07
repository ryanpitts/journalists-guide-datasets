# Integrated Postsecondary Education Data System #

The [Integrated Postsecondary Education Data System](http://nces.ed.gov/ipeds/) is a collection of surveys for most of the colleges and universities in the United States. It's conducted by the [National Center for Education Statistics](http://nces.ed.gov/), which is a part of the [U.S. Department of Education](http://www.ed.gov/).

## In This Guide ##

* [Universe](#universe)
* [Surveys](#surveys)
  * [Fall collection](#fall-collection)
    * Institutional Characteristics
    * Completions
    * 12-month Enrollment
  * [Winter collection](#winter-collection)
    * Student Financial Aid
    * Graduation Rates
    * 200% Graduation Rates
  * [Spring collection](#spring-collection)
* [Sources](#sources)
* [Release schedule](#release-schedule)
* [Data tools](#data-tools)
  * [Raw data files](#raw-data-files)
  * [Custom data files](#custom-data-files)
* [Authors](#authors)

## Universe ##

IPEDS includes all institutions participating in any Title IV federal student financial aid programs, such as federal loans, Pell Grants and work-study programs.

The non-Title IV U.S. service academies (West Point, the Naval Academy, the Air Force Academy and the Coast Guard Academy) also are included in IPEDS, as are other non-Title IV institutions that voluntarily report to IPEDS in order to be included in [College Navigator](http://nces.ed.gov/collegenavigator), which is a Department of Education tool geared toward prospective students and their parents.

## Surveys ##

There are nine survey components within IPEDS, each collected at a specific time of the year:

### Fall collection ###

Three survey components are collected in the fall and are usually due in October:

* **Institutional Characteristics**

  This really is the core component; everything else ultimately links back here.

  This is the survey component where institutions provide their names, locations and websites, for example, as well as what kinds of academic programs and student services they offer (and, at a high level, how much at least some of those academic programs cost).

  You'll almost always be pulling at least a couple of variables that were collected in this survey component, if for no other reason than you'll want to look at (or filter on) such basic information as what state a college is in or whether it's public or private.

* **Completions**

  This component is useful for finding, among other things, the number of degrees awarded in various fields or at various levels.

  This counts all degrees and certificates awarded in a one-year period (July through June, ending in the year in which this component is collected), and it is broken down by level (bachelor's, master's, etc.), race/ethnicity, gender and field of study.

  The Completions component also counts the _number of students_ receiving degrees and certificates (different from the number awarded, of course, since one student might receive multiple credentials that year), and that count is broken down by level, race/ethnicity, gender and age.

  The field of study is given as what's called a **CIP code**, which refers to the [Classification of Instructional Programs](http://nces.ed.gov/ipeds/cipcode/). These are codes of up to six digits long, getting more specific as the code gets longer. (The Completions component breaks down degrees and certificates awarded by the most specific, six-digit CIP codes, but it isn't hard to aggregate up as needed.)

  For example, the two-digit CIP code `14` refers to "Engineering", the four-digit `14.10` corresponds to "Electrical, Electronics and Communications Engineering" and the six-digit `14.1001` (the most specific) is for "Electrical and Electronics Engineering" (your standard electrical-engineering program).

* **12-month Enrollment**

  This component tells you how many individual students attended a given institution within a 12-month period (as you might expect).

  Specifically, this asks institutions for an _unduplicated_ headcount of all students enrolled from July through June, broken down by level (bachelor's, master's, etc.), race/ethnicity and gender. This also includes full-time equivalent enrollment figures for undergraduate students and for graduate students.

### Winter collection ###

Three survey components are collected in late winter, generally in February:

* **Student Financial Aid**

  This component includes data about undergraduate students who receive financial aid and how much aid those students receive. 

  The SFA component consists of multiple parts, each counting students and aid for a different subset of a given institution's undergraduate population. Most of these focus on subsets of first-time, full-time undergraduates who are seeking degrees or certificates.

* **Graduation Rates**

  This component counts the number of students who start a program at a given institution and complete that program there within a given amount of time.

  Lots of people are interested in this, but pay attention to what it's actually describing.

  First off, this only counts first-time, full-time students seeking degrees or certificates (your traditional freshman-type student). Second, the graduation figures in this component describe students who complete their programs within 150 percent of the normal completion time; that is, if a student starts a typical four-year bachelor's degree program, that student is counted as having graduated if he or she completes that degree within six years. (There's also information about students who complete their programs with 100 percent of normal time, if you're interested in (for example) students of four-year programs who actually manage to graduate within four years.)

  This also counts the number of students who start a program at that institution and then transfer out. (Because there's no federal system keeping track of individual students' outcomes, we can't figure out what happens to students after they transfer out. This means the graduation rate doesn't count all the people who graduate from _anywhere_--just those who graduate from the same place in which they started.)

  Since institutions can't predict the future, data from this component might seem a bit out of date at first glance; the information from a given year's SFA component describes students who started at that institution six years earlier (or three years earlier, in the case of two-year and less-than-two-year institutions).

* **200% Graduation Rates**

  This is very similar to the Graduation Rates component described above, but it also measures students who complete their programs within 200 percent of the normal completion time--as well as the 100-percent and the 150-percent totals.

  As with the Graduation Rates component, these don't get reported until a given year of entering freshmen (a "cohort", in IPEDS lingo) has been around for at least the period of time being measured; in other words, the latest year of 200% GR data describes students who entered eight years ago, in the case of four-year institutions.

### Spring collection ###

Finally (for one academic year, at least), the remaining survey components are collected in the spring, usually in April:

* **Fall Enrollment**

  This component counts how many students were enrolled in the preceding fall term.

  For institutions that don't work with traditional academic years (which are defined to include semester, trimester and quarter systems as well as "4-1-4" calendars that include a winter intersession between fall and spring semesters), this component instead counts students who were enrolled at any time from Aug. 1 to Oct. 31.

  Different parts of this component break down the information in different ways, but depending on what you're looking for, you can find stuff broken down by race/ethnicity, gender, full-time/part-time status, distance-education enrollment, level (undergraduate, graduate, etc.) and residence.

  Two of the other interesting things collected here are freshman students' states of residence and estimated student-to-faculty ratios for undergraduate programs.

  Watch out, though: The states of residence for freshmen (specifically, first-time, full-time students seeking degrees or certificates, also broken down by whether or not they graduated high school within the past 12 months) is optional in years where the fall occurred in an odd-numbered year. For example, the freshman-residence data for 2012-13 were required, but those data for 2011-12 were optional and generally shouldn't be used for large summary statistics or anything like that.

* **Finance**

  This component includes financial data for different institutions, such as revenues and expenses by type, endowments and amounts of scholarships.

  These are collected differently depending on an institution's control (public, private not-for-profit, private for-profit) and (in the case of public institutions) the standards the institution used for its internal accounting.  This means it's probably not wise to compare IPEDS finance figures between institutions without paying a very serious amount of attention to what you're doing.

* **Human Resources**

  This component counts institutions' employees by full-time/part-time status, instructional status (including tenure and academic rank, i.e., professor, assistant professor, etc.), race/ethnicity, gender and how many of those employees were newly hired.

  This also includes salary information for full-time, nonmedical instructional staff.

Finally, keep in mind that all of this is survey information; if you see something in IPEDS, it's ultimately self-reported (or based on something that is). There can be errors and inconsistencies in some fields, although NCES tries admirably to keep that to a minimum (more on that in the next section).

## Release schedule ##

IPEDS data are released according to when they were collected; for example, all
components collected in the fall are released together.

Each component gets released three times:

* **Preliminary**

  The first release, about six or seven months after the data were collected. (For example, the 2013-14 winter collection (closed Feb. 26, 2014) has a scheduled preliminary release in September 2014.)

  Preliminary data have not finished going through NCES quality control, and preliminary releases do not include any **imputed data**, which are NCES' attempts at filling in reasonable guesses for institutions that did not respond to the survey.

  NCES uses preliminary data to produce its "First Look" reports in order to release those reports in a relatively timely manner; those reports are then updated with provisional data once those are released.

* **Provisional**

  The second release, a few months after the preliminary release. (For example, the 2013-14 fall collection had preliminary and provisional releases both in the summer of 2014.)

  Provisional data include imputed data for those institutions that didn't respond to the survey, and all of the data have finished going through NCES quality control.

  In general, these are the tables you'll want to use if you want to use relatively reliable data for the most recently available year.

* **Final**

  The year after a given component gets collected, the reporting institutions have a chance to revise their responses (if they notice a mistake, etc.). Those edits go through NCES quality control again, and the data are rereleased as final.

  Because of this schedule, it takes at least a year and a half for data to go from collection to final release.

  NCES does not update its "First Look" reports when final data are released.

## Data tools ##

NCES makes IPEDS data available in a variety of forms in the [IPEDS Data Center](http://nces.ed.gov/ipeds/datacenter/), although the two options you'll probably use most often from that site are "Download Survey Data Files", which provides links to the raw data, and "Download Custom Data Files", which lets you select a list of institutions and a list of variables from various years to retrieve for those institutions.

### Raw data files ###

The raw files, or "survey data files" as they're known in the [IPEDS Data Center](http://nces.ed.gov/ipeds/datacenter/), are just that--full copies of IPEDS tables as NCES maintains them, available in a few different formats (Stata, SPSS and good ol' CSV) with good supporting documentation (the "dictionary" file listed with each table).

This gives you a lot of flexibility to use whatever tools and processes are familiar to you when analyzing this data; personally, I (JCM) prefer importing all of the CSVs into a MySQL database since that makes it especially simple to join various tables together.

Most tables are named with a prefix of a few letters (and sometimes numbers) followed by the academic year in which its contents were collected (and an optional suffix). For example, the table that simply lists names and addresses of colleges and universities (along with all kinds of other useful top-line things--such as whether they're public or private, two-year or four-year) always has the prefix `HD`, but the one collected in the fall of 2012 (i.e., the 2012-13 academic year) is called `HD2012`.

Only one table (the `HD{year}` table, also known in various places as the "header" or "directory" table) has useful human-readable identifiers such as institution name or address; all the rest expect you to join somehow on the `UNITID` field, which is the six-digit identifier for an institution that reports to IPEDS. It's released as part of the Institutional Characteristics survey, so it's in the first batch of tables you'll get for the current academic year; even if you're missing a lot of other tables, you'll have (or quickly go and get) this one.

(None of the UNITID values begins with a zero, so it's no big deal if you accidentally import your UNITID column as an integer--certainly less of a concern than for ZIP codes or FIPS codes. On that note, while the header table does include state postal abbreviations, other tables that refer to various states (such as in the context of freshman students' states of residence) use state FIPS codes for that purpose. Yes, FIPS codes also are in the header table.)

### Custom data files ###

TK

## Sources ##

* [2013-14 IPEDS Methodology Report](http://nces.ed.gov/pubs2014/2014067.pdf)
* [What are Title IV Programs?](http://federalstudentaid.ed.gov/site/front2back/programs/programs/fb_03_01_0030.htm)
* [Overview of IPEDS Data Release](http://nces.ed.gov/ipeds/resource/download/IPEDS_DataReleaseProcedures.pdf)

## Authors ##

Justin Myers learned about IPEDS in a past life as a developer on the data and interactives team at [The Chronicle of Higher Education](http://chronicle.com/) and [The Chronicle of Philanthropy](http://philanthropy.com/).
