Federal Election Commission
===========================

The [Federal Election Commission](https://www.fec.gov/) provides data about candidates for federal office (U.S. House, U.S. Senate and President), committees formed by those candidates and groups to spend money on federal elections, and filings reporting contributions and expenditures made by both candidates and committees. It also maintains summary data about campaign finance, data about campaign finance law enforcement and federal election results.

The FEC is not the only federal entity that has a role in the campaign finance system; Senate candidates and party committees file reports first to the Secretary of the Senate, which then forwards them to the FEC. The Internal Revenue Service provides data on the finances of some political groups that raise and spend money on certain state elections. But the FEC is the main repository of data for federal campaign finance activity, and it has several different types of data for download and use in reporting and analysis.

In This Guide
=============

* [Overview](#overview)
* [Electronic Filings](#electronic-filings)
* [Bulk FTP Data](#bulk-ftp-data)
* [Data Catalog](#data-catalog)

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

Bulk FTP Data
========

The FEC has offered bulk data for years, and [its offerings](http://www.fec.gov/finance/disclosure/ftp_download.shtml) include summary and detailed files covering committees, candidates and contributions. The bulk files are updated weekly, late on Sunday nights, so depending on your timing and needs the bulk files may not be suitable for every task. The advantage of the bulk files is that they are vetted by the FEC, with some of the records standardized (by adding FEC-issued committee ids, for example) and others removed to prevent duplicate records from appearing. The summary and detailed files are pipe-delimited, a relatively recent change for the FEC, and some older files may still be in fixed-width format.

Bulk data files are contained inside zip files stored on the FTP server, so retrieving them via a web application requires several steps. The FTP data is updated early Monday morning each week, and previous cycles are updated as well, since committees can amend filings from an earlier election cycle.

Data Catalog
========

The data catalog is a collection of some of the summary files available via FTP as well as other files covering disbursements, independent expenditures and leadership PACs, among other subjects. The files are available in CSV or XML formats, and cover single cycles (mostly 2010 and 2012, although the summary files also include 2008 data). One advantage of the data catalog files is that they can be called directly from a web application without having to unzip them, but there are some drawbacks. [Independent Expenditures](http://fec.gov/data/IndependentExpenditure.do?format=html&election_yr=2012) include both original transactions and amendments, resulting in duplicate records in those cases. In another example, the [listing of leadership PACs](http://fec.gov/data/Leadership.do?format=html&election_yr=2012) contains an entry for the corporate PAC of Interactive Corp. Most of the data catalog files are updated daily, and they are the one place where it's possible to find [candidate disbursements](http://fec.gov/data/CandidateDisbursement.do?format=html&election_yr=2012) in statewide or district-level files. The files themselves are stored on the FEC's FTP server, so it's possible to grab them directly. The FEC also maintains [a blog about its data](http://fec.gov/blog/) that includes changes and additions to its data offerings.