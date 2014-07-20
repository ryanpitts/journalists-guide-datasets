Federal Election Commission
===========================

The [Federal Election Commission](https://www.fec.gov/) provides data about candidates for federal office (U.S. House, U.S. Senate and President), committees formed by those candidates and groups to spend money on federal elections, and filings reporting contributions and expenditures made by both candidates and committees. It also maintains summary data about campaign finance, data about campaign finance law enforcement and federal election results.

The FEC is not the only federal entity that has a role in the campaign finance system; Senate candidates and party committees file reports first to the Secretary of the Senate, which then forwards them to the FEC (although some candidates [voluntarily file electronic reports](http://docquery.fec.gov/senate/)). The Internal Revenue Service provides data on the finances of some political groups that raise and spend money on certain state elections. But the FEC is the main repository of data for federal campaign finance activity, and it has several different types of data for download and use in reporting and analysis.

In This Guide
=============

* [Overview](#overview)
* [Electronic Filings](#electronic-filings)
	* [Parsing Electronic Filings](#parsing-electronic-filings)
	* [Headers](#headers)
	* [Amendments](#amendments)
* [Bulk FTP Data](#bulk-ftp-data)
	* [Summary files](#summary-files)
	* [Detailed files](#detailed-files)
* [Data Catalog](#data-catalog)
* [The More You Know](#the-more-you-know)
* [Authors](#authors)

Overview
==========

The Federal Election Commission offers three general types of downloadable campaign finance data: individual electronic filings in CSV format covering most committees, pipe-delimited bulk itemized data and summary files via FTP from all committees covering two-year election cycles and specialized CSV or XML files via its [Data Catalog](http://fec.gov/data/DataCatalog.do?format=html). Electronic filings are available in real time as they are filed, while the other two types are updated on a regular basis.

The base element of federal campaign finance data is the committee. Committees are the recipient of money and the spenders of money, and there are a number of different kinds of committees. Although most FEC rules apply to all committees, some committees have different limits or rules to follow, and these matter.

The second element is the filing, a report by a committee to the FEC. There are many different kinds of filings, but in general they cover 3 different types of information:

  1. The formation of committees and candidacies, and their details.
  2. The raising of money for campaigns.
  3. The spending of money on campaigns.
  
There is a consistent schedule for filings covering the last two types, and filings of the first type can be made at any time. In general, the FEC recognizes a roughly two-year election cycle that corresponds to U.S. House elections (where all 435 seats are up for election every 2 years). In the case of senators, who are elected to six year terms on a staggered basis, an election cycle may be considered to include the previous four years as well as the current two-year period. The election cycle is used not only as a logical boundary for calculating money raised and spent but also to calculate contribution limits for candidates and committees.

Electronic Filings
========

Most committees registered with the FEC are required to file all of their reports electronically. There are two significant exceptions: committees of U.S. Senate candidates (and two senatorial party committees), which file on paper with the Secretary of the Senate, and [committees that raise or spend less than $50,000 in a calendar year](http://fec.gov/ans/answers_filing.shtml#Do_I_need_to_file_electronically), or expect to do so. Electronic filing applies to U.S. House and presidential candidate committees, non-candidate political committees (typically knows as PACs), national, state and local political party committees registered with the FEC and individuals or organizations engaged in independent spending. Electronic filing was mandated in 2001.

Electronic filings can be found via the [FEC's search form](http://www.fec.gov/finance/disclosure/efile_search.shtml), which has a number of options for filtering the results to a particular committee, a particular date or more. The search results include the option to View or Download individual filings, which present the data in HTML and delimited formats, respectively. Individual filings contain all of the records for that filing, stacked on top of each other in varying delimited layouts ([A zip file containing the formats is on FEC.gov](http://www.fec.gov/elecfil/eFilingFormats.zip).) You can open a .fec file in a text editor or spreadsheet, but be aware of the variable layouts within a single file (and across time). This is precisely why we developed Fech to handle electronic filings. 

Even though committees file reports [on a regular schedule](http://www.fec.gov/info/report_dates.shtml), electronic filings occur nearly every day of the year. Some are amendments of previous filings, others are filed in advance (or after) a deadline, and others are filed as changes warrant. Filings that are amendments are indicated in the data, and serve as complete replacements for the original filings.

Parsing Electronic Filings
===========

For electronic filings submitted to the FEC after Jan. 3, 2008, there are two versions of raw data for the filing.

In one version, the fields in the filing are delimited by commas. In the other, the fields are delimited by ASCII 28 characters. (For filings submitted through Jan. 3, 2008, there is only one version -- the comma-delimited version.)

In most situations, using the version with comma-separated values (CSV) would be preferable; such files are readable by most spreadsheet programs, and most programming languages have built-in support for CSV parsing.

But the FEC makes it easier to access the ASCII 28-delimited version than the CSV version, so in many cases the added ease of getting to the ASCII 28-delimited version outweighs the benefits of using the CSV version.

Take filing No. 775739, for example. The ASCII 28-delimited version of this filing is available from the easily guessable URL [http://query.nictusa.com/dcdev/posted/775739.fec](http://query.nictusa.com/dcdev/posted/775739.fec)

The CSV version, however, has the URL [http://query.nictusa.com/showcsv/nicweb127546/775739.fec](http://query.nictusa.com/showcsv/nicweb127546/775739.fec) -- that number before the final slash makes it harder to determine programmatically what the URL will be.

If your intention is to work with these files using a programming language, it should be fairly easy to parse the file using a delimiter other than a comma. For example, in Ruby, you would do the following:

    >> require 'csv'
    => true
    >> csv = CSV.open('775739.fec', :col_sep=>"\034")
    => <#CSV io_type:File io_path:"775739.fec" encoding:ASCII-8BIT lineno:0 col_sep:"\x1C" row_sep:"\n" quote_char:"\"">

In Python, you would do:

    >>> csv.reader(open('775739.fec', 'r'), delimiter="\034")
    <_csv.reader object at 0x1004e2210>
    >>> reader = csv.reader(open('775739.fec', 'r'), delimiter="\034")

("\034" is the octal representation of the ASCII 28 character.)

Other programming languages should have similar facilities for setting the file's delimiter.

(The FEC also provides tools for converting the ASCII 28-delimited files into CSVs [here](http://www.fec.gov/support/DataConversionTools.shtml), though I can't vouch for how useful these might be.)

If you know only the filing's ID and prefer to download the CSV, the URL for accessing the link to that version would look like [http://query.nictusa.com/cgi-bin/dcdev/forms/DL/775739/](http://query.nictusa.com/cgi-bin/dcdev/forms/DL/775739/) -- just substitute the ID of the filing you're interested in for 775739.

Although it is possible to parse electronic filings with most languages' CSV libraries, there are several FEC-specific libraries, including [Fech](https://github.com/NYTimes/Fech) (Ruby), [read_FEC](https://github.com/jsfenfen/read_FEC) (Python) and [FEC Scraper Toolbox](https://github.com/cschnaars/FEC-Scraper-Toolbox) (Python).

Headers
=========

The first line in every electronic filing is the "header" row, which contains metadata [1] about the filing.

All the values in the header row are important to someone, but a few in particular are especially important to us:

_The FEC version number_ 
This is the value in the third column of the header row, and it tells us which set of field names and positions to use for each row type. In fact, we can't even parse the header row itself correctly without knowing the FEC version number, because the row's fields changed between versions five and six.

The FEC occasionally updates the version required for new filings [2] and makes available the field definitions for the new version. But older filings that were submitted before the update will remain in the FEC's filing system, and we'll need to parse them based on the version they used.

The version number currently required for electronic filers is 8.

For a list of field definitions, see Appendix A.

_The Report ID_
In filing versions 3 through 5, this was the value in the seventh column of the header row. Since version 6, the report ID has appeared in the sixth column.

The report ID is an indication of whether the filing is an amendment [3] -- that is, does it correct an error in an earlier filing.

If the filing is not an amendment, the report ID field will be blank.

If the filing is an amendment, the report ID will look like this: *FEC-763780*

The numbers after the hyphen in the report ID represent the ID [4] of the original filing that this one amends, even if the original filing has been amended previously.

_The Report Number_
In filing version 3 through 5, this was the value in the eighth column of the header row. Since version 6, the report number has appeared in the seventh column.

The report number is important only for amendments. If the filing is not an amendment, the field will be blank.

In an amendment, the report number represents the number of times the original filing has been amended. The report number is *1-indexed*, meaning that the first amendment to a filing will have report number 1, the second amendment will have report number 2, and so on.


[1] Definition of metadata.

[2] The last update was XXXXXXX. 

[3] For more information on amendments, see chapter XX.

[4] The *filing ID* is the several-digit number unique to each filing. It can be seen in the URL of an electronic filing on the FEC's website, and in the filenames of an electronic filing.

Amendments
===========

Any filing submitted to the FEC can be amended later by the filer.

Once an amendment is filed, it replaces the original filing and any previous amendments to the original filing completely.

## Is this an amendment?

In the section on [header rows](#headers), we learned that amendments will have a value in the Report Number field of the first line of the electronic filing. The value of the Report Number represents the number of times the original filing has been amended. The easiest way to determine whether any given filing is an amendment is to check whether the Report Number field is blank. If it is, we can move on, confident that this is an original filing. If the field contains a value, we know that the filing is an amendment.

## What's being amended?

The section on [header rows](#headers) also taught us that the Report ID field will contain a value on amended filings (and will be blank otherwise, just like the Report Number field):

> If the filing is an amendment, the report ID will look like this: *FEC-763780*

The Report ID tells us *which filing this one amends*.

For example, filing No. 776795 has this value in the Report ID field: FEC-772249. This means that it amends filing No. 772249. If we have previously saved filing No. 772249 somewhere, we should delete it and instead use the new filing.

Note that amendments themselves do not get amended; only the original filing is amended. If a filing is amended multiple times, when we save the latest amendment, we can discard both the original filing and any previous amendments. Previous amendments can be found by looking at the Report ID field; all amendments to the same original filing will have the same value in that field.


Bulk FTP Data
========

The FEC has offered bulk data for years, and [its offerings](http://www.fec.gov/finance/disclosure/ftp_download.shtml) include summary and detailed files covering committees, candidates and contributions. The bulk files are updated weekly, late on Sunday nights, so depending on your timing and needs the bulk files may not be suitable for every task. The advantage of the bulk files is that they are vetted by the FEC, with some of the records standardized (by adding FEC-issued committee ids, for example) and others removed to prevent duplicate records from appearing. The summary and detailed files are pipe-delimited, a relatively recent change for the FEC, and some older files may still be in fixed-width format.

Bulk data files are contained inside zip files stored on the FTP server, so retrieving them via a web application requires several steps. The FTP data is updated early Monday morning each week, and previous cycles are updated as well, since committees can amend filings from an earlier election cycle.

Summary files
========

The [summary files](http://www.fec.gov/finance/disclosure/ftpsum.shtml) include canonical election-cycle data for candidates and committees - one record for each candidate or committee per two-year election cycle, depending on the file selected. There are two candidate summary files -- one for campaigns that have elections in the current cycle, and one for all candidates no matter if they face election in the cycle or not -- and they can differ in amounts and timeliness. 

The [current campaigns file](ftp://ftp.fec.gov/FEC/webl12.zip) may be more timely, but also contains a single total for PAC contributions (compared to totals for different kinds of PACs in the other file) and some of its totals may contain double-counted transactions. More at the [data dictionary](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryWEBL.shtml).

The [all candidates file](ftp://ftp.fec.gov/FEC/weball12.zip) can be updated slightly less frequently than the current campaigns one, but it contains more detailed breakdowns of certain types of transactions as noted above. The possibility of double-counting some kinds of transactions - transfers to and from authorized committees of a candidate - also exists. More at the [data dictionary](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryWEBALL.shtml).

The [PAC summary file](ftp://ftp.fec.gov/FEC/2012/webk12.zip) provides the latest summary information on political action and party committees, including independent expenditures. More at the [data dictionary](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryWEBK.shtml).

The FEC previously used to generate summary files at the end of the election cycle for candidates and PACs that included totals for different types of PACs, but discontinued these files after the 2005-06 cycle. Files are available from 1979-80 through 2005-06. Party committee-only summary files exist from the 1991-92 cycle through the 2003-04 cycle. One of the most useful files, which contained a record for each combination of candidate recipient and PAC contributor/independent spender, covers the 1991-92 cycle through the 2001-02 cycle. A similar file exists for candidate-party activities during the same time period.

These summary files had been stored in fixed-width format but were converted to pipe-delimited format in late July 2012. [Fech-FTP](https://github.com/dwillis/fech-ftp) is a Ruby library that wraps many of the summary files and some of the detailed files described below. [fecmaster](https://github.com/lukerosiak/fecmaster) is a Python library for downloading and importing the bulk files.

There's one more thing to be aware of: the way that the FEC used to store its data (detailed and summary) relied on the use of [an "overpunch" character](http://www.fec.gov/finance/disclosure/ftpsum.shtml#overpunch) to represent negative amounts. This [recently changed for the detailed contribution files](http://www.fec.gov/blog/disclosure/entry/indiv_oth_and_pas2_file) and for the candidate and committee files, but it's possible that older summary files still contain such characters, and that the amount fields should be imported as text and then converted to numeric columns, accounting for negative amounts. There is a tutorial for [working with the FTP files using Microsoft Access](http://www.fec.gov/finance/disclosure/working_with_data_files.pdf).

Detailed files
========

The [detailed files](http://www.fec.gov/finance/disclosure/ftpdet.shtml) include cycle-specific data for committees, candidates, individual contributions and committee transactions to candidates and between committees. Each cycle, beginning with 1979-80, has five files with data representing that cycle. The current cycle and its immediate 2-3 preceding cycles also have three smaller tables that represent additions, changes and deletions to the individual contributions file. The FEC changed the format of these files from fixed-width to pipe-delimited in July 2012. These files are updated weekly on late Sunday evenings/early Monday mornings, so information submitted during the week before should be reflected in the next update. One advantage of using these files is that they represent "official" data that has been checked by the FEC. Nonetheless, there have been some errors

Committees
---------

Known as the [committee master file](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryCommitteeMaster.shtml), this has a record for each committee registered with the FEC during a cycle. The ID number assigned by the FEC to each committee is unique within the cycle, but committees often exist for years or even decades. If a committee is a campaign committee for a candidate for the House, Senate or President, it will include that candidate's ID number. A committee will be one of [several types](http://www.fec.gov/finance/disclosure/metadata/CommitteeTypeCodes.shtml). Other committees may have values for party affiliation, frequency of filings and connected organization, although these values are not universally present for each committee.

Candidates
---------

Known as the [candidate master file](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryCandidateMaster.shtml), this file contains one row for each candidate who either registered with the FEC or "appeared on a ballot list prepared by a state elections office." Key fields in this file include whether a candidate is an incumbent, challenger or seeking an open seat (although this field is not consistently populated), and the state and district the candidate is running in.

Candidate Committee Linkage
---------

A new offering as of July 2012, [this file](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryCandCmteLinkage.shtml) contains one row for each combination of candidate and committee during an election cycle. Candidates can have a primary committee, authorized committees, joint fundraising committees and other relationships. The linkage file helps keep track of all of those relationships. In particular, joint fundraising committees can benefit multiple candidates; previously the committee master file would only list one. Note: it does not include a link between candidates and their leadership committees.

Committee Contributions To Candidates
---------

[This file](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryContributionstoCandidates.shtml) contains one row for each contribution from a committee to a candidate and for each independent expenditure made by a committee about a candidate. It is a subset of the file containing all transactions between one committee and another. This file can be used to calculate things such as which candidate got the most PAC money and which candidates have received contributions from a specific committee.

Any Transaction from One Committee to Another
---------

[This file](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryCommitteetoCommittee.shtml) contains a row for each transaction between two committees, regardless of whether either committee is a candidate committee or not. For example, this file includes contributions from a corporate PAC to a national party committee in addition to contributions to candidate committees. The list of [transaction types](http://www.fec.gov/finance/disclosure/metadata/DataDictionaryTransactionTypeCodes.shtml) describes the kind of transaction each row represents. The quirk here is that in many cases, both sides of the transaction get separate records: one for the committee making the contribution (usually beginning with 2X) and another for the committee receiving the contribution (usually beginning with 1X). Using this file for SQL queries means including transaction type in some manner in pretty much every query; which types you want depends on a couple of factors, such as timeliness (contributing committees can file before recipient committees) or completeness (a recipient committee usually is the definitive account of what it has gotten).


Data Catalog
========

The data catalog is a collection of some of the summary files available via FTP as well as other files covering disbursements, independent expenditures and leadership PACs, among other subjects. The files are available in CSV or XML formats, and cover single cycles (mostly 2010 and 2012, although the summary files also include 2008 data). One advantage of the data catalog files is that they can be called directly from a web application without having to unzip them, but there are some drawbacks. [Independent Expenditures](http://fec.gov/data/IndependentExpenditure.do?format=html&election_yr=2014) include both original transactions and amendments, resulting in duplicate records in those cases. In another example, the [listing of leadership PACs](http://fec.gov/data/Leadership.do?format=html&election_yr=2014) contains an entry for the corporate PAC of Interactive Corp. Most of the data catalog files are updated daily, and they are the one place where it's possible to find [candidate disbursements](http://fec.gov/data/CandidateDisbursement.do?format=html&election_yr=2014) in statewide or district-level files. The files themselves are stored on the FEC's FTP server, so it's possible to grab them directly. The FEC also maintains [a blog about its data](http://fec.gov/blog/) that includes changes and additions to its data offerings.

The More You Know
==========

* The electronic filings are technically unofficial until the FEC processes them, and they will contain typos or incomplete information (or not be filed properly, particularly when it comes to lump sum expenditures, which must report both an unitemized total and then most itemizations. Think of a single credit card payment covering multiple transactions.). The agency can take several weeks or more to process filings from significant filing dates, such as quarterly deadlines. Even after the FEC processes filings and places transactions into the bulk FTP data, there may be errors - the most common is misidentified committee IDs, as electronic filings are not required to include committee or candidate IDs.

* The time lag for FEC processing is the biggest practical concern, but there are other issues with timing, particularly as it relates to filing schedules. Committees usually file either monthly or quarterly, with monthly deadlines on the 20th of each month and quarterly deadlines on April, July and October 15, followed by a year-end report due on Jan. 31. There also are reports due just before and after a primary, runoff, special or general election for any committee involved in that election.

* You'll also come across joint committees, which are almost required for most competitive races, especially Senate ones. These committees can solicit larger donations and then divide them among multiple recipients. Here's an example: a donor can give $40,000 to the "Ryan Pitts Victory Fund," of which $5,200 will go to Ryan's campaign and the remainder to Ryan's party national or Senate committee. The original donation and the ultimate receipts are *both* reported, so as a data user you will need to avoid double-counting. Depending on what you want to know, you should use either the original donation or the divided shares.

* State and local party committees can have federal and state accounts, but the FEC filing represents the federal portion (although it also includes joint spending, in which both the federal and state accounts pay for some expenses). FEC rules apply to donations to federal accounts of state & local party committees, but states have different rules for state accounts.

* Donors who are unaware of contribution limits and donate more money than is permitted will still have their names and contributions reported in FEC filings. Committees have to do this, and then they refund the money, usually in the same filing. Refunds should be classified as expenditures, but some committees list them as contributions with negative amounts.

* The person at the FEC you want to talk to in case of data issues is Paul Clark (pcclark@fec.gov). The press office is typically friendly and responsive for general questions.

Authors
==========

Derek Willis has been using federal campaign finance data since 1996, when he helped report on soft money donors in Florida for The Palm Beach Post. He is the co-author [an IRE book on covering campaign finance](http://www.amazon.com/Unstacking-Deck-Reporters-Campaign-Finance/dp/0976603756), researched [political non-profits](http://www.publicintegrity.org/2003/09/25/5564/silent-partners-special-report) for The Center for Public Integrity and developed The New York Times [Campaign Finance API](http://developer.nytimes.com/docs/campaign_finance_api/). Willis currently uses FEC data to write stories for [The Upshot](http://www.nytimes.com/upshot/). Reach him @derekwillis.

Aaron Bycoffe is data editor at The Huffington Post, where he has used FEC data to [find donors who have exceeded legal limits](http://www.huffingtonpost.com/2013/07/22/campaign-contribution-limits_n_3607672.html) and to build interactives. He previously worked at The Sunlight Foundation, where he tracked [super PACs](https://sunlightfoundation.com/blog/2011/08/01/super-pacs-raise-combined-26-million-first-half-year/) and other campaign finance vehicles. He's at @bycoffe.