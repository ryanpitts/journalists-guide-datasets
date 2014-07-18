IPEDS Data Center
=================

The Integrated Postsecondary Education Data System (IPEDS) is a Federal
clearinghouse for higher education data run by the [National Center for
Education Statistics] which is run by the [Institute of Education Sciences]
whish is run by the [Department of Education] which is run by the Illuminati.

If you're looking for higher education data, and not sure where to look, IPEDS
is a good place to start.

For a better intro to IPEDS, you should read the [wikipedia page]. This
document is more of a crash course written by an amateur.

  [National Center for Education Statistics]: http://nces.ed.gov/
  [Institute of Education Sciences]: http://ies.ed.gov/
  [Department of Education]: http://www.ed.gov/


Data Gotchas
------------

- **Quality**: It is important to understand that IPEDS collects and
  distributes data, but does not vet it. For example, I noticed that for one
  institution, SAT scores were dramatically different one year, and for another
  institution, their graduation rate was 0% for one year.
- **Shifting Definitions**: You'll quickly find that getting data over several
  years is difficult. Many variables change definition over the years. A good
  example is the race/ethnicity variables changed in 2008, and changed again in
  2010.
- **Different Definitions**: When comparing numbers from IPEDS data to a report
  from another source, the numbers may be different. For example, the full-time
  equivalent enrollment is often cited, but it's a number derived by a formula,
  and not everyone uses the same formula. It's important to note when you're
  using a derived variable.


### What institutions are in IPEDS?

Short answer is... any institution that wants federal dollars is in IPEDS.
Schools with multiple campuses usually have a separate entry for every campus,
but sometimes they'll be lumped together into one IPEDS id. In addition to the
IPEDS id, you may want to find the FICE code (this was used historically and
still the primary ID many reports reference) and the newer OPE id (only Title
IV schools have this).


### The Glossary

Navigating the system can be overwhelming. To help understand all the jaron,
there is a central [glossary]. When you generate reports, terms are also linked
to this glossary. For example, to calculate the full-time equivalent (FTE)
student headcount, one part-time undergrad student at a 4-year institution only
counts as 0.403543 person if they go to a public school, but 0.392857 parts of
a person if they go to a private school.

  [glossary]: http://nces.ed.gov/ipeds/glossary/


### Creating an IPEDS Data Center Account

While having an account isn't required, it is helpful. Signing up is free. Some
features are behind a login wall, and so is early access to provisional release
data.


Compare Individual Institutions
-------------------------------

If you're doing research, you're probably going to want to pull a lot of
variables about a lot of institutions. You should keep datafiles (`*.uid` for
institutions, and `*.mvl` for variables) offline so you can repeatedly generate
the same reports quickly. Don't be tempted to pick some institutions, pick some
variables, and then run away.

### Picking Institutions

The easiest way to pick institutions is to have files with the IPEDS ids
separated by commas handy. IPEDS also has a tool called "Create/Download an
institution group" *(login wall)* that's lets you download the output of the
institution selection process. Luckily, the files IPEDS hands out are in plain
text and easy to manipulate in your favorite text editor/excel. The *.uid files
are a pipe (`|`) separated file format with the columns: ID, Institution Name,
City, and State. But you only need the ID column.

### Picking Variables

This is similar to picking institutions. Use the "Create/Download a list of
variables" interface to pick a small number of related variables and save them
to a MVL file.

#### The Structure of the MVL File

The MVL file is a pipe (`|`) separated text file. There's a code, short name,
category, long name, and then a bunch of other fields. So if you saw these
lines:

    DRVEF2009_RV|DVEF01|Fall enrollment/retention rates|Adult age (25-64) enrollment, all students|||||||||||||09.23401|.|Cont|TN|N||745|||||
    DRVEF2010|DVEF01|Fall enrollment/retention rates|Adult age (25-64) enrollment, all students|||||||||||||10.23401|.|Cont|TN|N||745|||||

You could interpret it as:

* `DRVEF2009_RV` - `DRV` prefix means this is a **derived variable**. You'll
  notice it references a specific year. The `_RV` suffix means this variable
  was revised. This is the unique name for this variable for this year.
* `DVEF01` - This is a short name, like a slug, that describes this variable.
  See how both lines in the same share the same short name, category, and long
  name?
* `Fall enrollment/retention rates` - This is the category you'll find this
  variable.
* `Adult age (25-64) enrollment, all students` - This is a long name for this
  variable. Sometimes, you can often find a long description in the [glossary].
  For example, here's the [glossary entry for Fall Enrollment
  (EF)](http://nces.ed.gov/ipeds/glossary/index.asp?id=802) and [Retention
  rate](http://nces.ed.gov/ipeds/glossary/?charindex=R).
* the rest... I don't know.

### Generating Reports

_TODO_ what settings do you pick?

### Reading the Reports

_TODO_ expect tons of rows, need to build a parser just for the reports

### How to Update Your Old Reports

_TODO_
