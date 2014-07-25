# Integrated Postsecondary Education Data System #

The [Integrated Postsecondary Education Data System](http://nces.ed.gov/ipeds/) is a collection of surveys for most of the colleges and universities in the United States. It's conducted by the [National Center for Education Statistics](http://nces.ed.gov/), which is a part of the [U.S. Department of Education](http://www.ed.gov/).

The IPEDS collection is mandatory for any institution that participates in [federal student financial aid programs](http://en.wikipedia.org/wiki/Title_IV). Other institutions can (and do) choose to report to IPEDS, mostly because that's how they get included in federal data tools such as [College Navigator](http://nces.ed.gov/collegenavigator/) that are more geared toward prospective students and their families.

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
* [Authors](#authors)

## Universe ##

TK

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

  TK

* **Graduation Rates**

  TK

* **200% Graduation Rates**

  TK

### Spring collection ###

Finally (for one academic year, at least), the remaining survey components are collected in the spring, usually in April:

* **Fall Enrollment**

  TK

* **Finance**

  TK

* **Human Resources**

  TK

## Authors ##

Justin Myers is a developer on the data and interactives team at [The Chronicle of Higher Education](http://chronicle.com/) and [The Chronicle of Philanthropy](http://philanthropy.com/).
