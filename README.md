# Baseball Hacks
#### Tips & Tools for Dissecting and Analyzing Statistics
###### Joseph Adler

---

Publisher's [web page for this book](http://shop.oreilly.com/product/9780596009427.do), including [errata](https://www.oreilly.com/catalog/errata.csp?isbn=9780596009427) and [example code](https://resources.oreilly.com/examples/9780596009427/)

[`Lahman`](https://rdrr.io/cran/Lahman/) package in R

---

## 1. Basics of Baseball

* **01 : Score a Baseball Game** [P.4-12]
* **02 : Make a Box Score from a Score Sheet** [P.12-19]
* 03 : Keep Score, Project Scoresheet–Style
* **04 : Follow Pitches During a Game** [P.26-30]
* **05 : Follow the Game Online** [P.31-33]
* 06 : Add Baseball Searches to Firefox
* 07 : Find Images of Stadiums


## 2. Baseball Games from Past Years

* 08 : Get and Install MySQL
* 09 : Get an Access Database of Player and Team Statistics
* **10 : Get a MySQL Database of Player and Team Statistics** [P.49-54] ...[[baseballdatabank 2019 data used](http://www.seanlahman.com/baseball-archive/statistics/)]; [[Baseball-DataBank.org archived](https://web.archive.org/web/20180412211025/http://www.baseball-databank.org/)] [DEFINE KEYS]
* 11 : Make Your Own Stats Book
* 12 : Get Perl [REVISIT]
* **13 : Learn Perl** [P.67-74] ...[[Perl script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)]
* **14 : Get Historical Play-by-Play Data** [P.74-78] ...[[RetroSheet event files](https://www.retrosheet.org/game.htm)] [[Perl script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)]
* 15 : Make Box Scores or Database Tables from Play-by-Play Data with Retrosheet Tools ...[[Chadwick tools](http://chadwick.sourceforge.net/doc/index.html)] from [[Chadwick BB Bureau](http://chadwick-bureau.com/)] [[@chadwickbureau](https://twitter.com/chadwickbureau)]
* **16 : Use SQL to Explore Game Data** [P.84-91]
* 17 : Use Microsoft Access to Run SQL Queries
* 18 : Get a GUI for MySQL
* 19 : Move Data from a Database to Excel ...[SQL]
* 20 : Load Baseball Data into MySQL ...[[Perl script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)]
* 21 : Load Retrosheet Game Logs ...[[Retrosheet game logs](https://www.retrosheet.org/gamelogs/index.html)] [[`game_log_header.csv`](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)] [Perl]
* **22 : Make a Historical Play-by-Play Database** [P.107-110] ...[[Perl scripts](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)] [[Chadwick tools (cf. #15)](http://chadwick.sourceforge.net/doc/index.html)] [[`all_hdr.txt`](https://resources.oreilly.com/examples/9780596009427/)] [REVISIT]
* 23 : Use Regular Expressions to Identify Events [REVISIT]


## 3. Stats from the Current Season

* 24 : Use Microsoft Excel Web Queries to Get Stats
* 25 : 
* 26 : 
* 27 : 
* 28 : Get Recent Play-by-Play Data [*COULDN'T see MLB.com [Gameday](http://gd2.mlb.com/components/game/mlb/) xml files; my Perl install not working*]
* **29 : Find Data on Hit Locations** [P.151-157] ...[*needs data from #28*]


## 4. Visualize Baseball Statistics

* 30 : 
* 31 : Get R and R Packages
* 32 : Analyze Baseball with R
* **33 : Access Databases Directly from Excel or R** [P.170-180] ...[[ODBC drivers for 'Excel for Mac 2011'](https://support.office.com/en-us/article/odbc-drivers-that-are-compatible-with-excel-for-mac-9fa6bc7f-d19e-4f7f-9be4-92e85c77d712#ID0EAABAAA=Excel_for_Mac_2011)] : [[$100](https://uda.openlinksw.com/offers/order?uri=http%3A%2F%2Fdata.openlinksw.com%2Foplweb%2Foffer%2FOffer-UDALT-WKS-anyos-odbc-postgres-personal-2019-01%23this&type=buy&mode=u) / [$40](http://www.actualtech.com/product_opensourcedatabases.php) / [$?](https://www.simba.com/drivers/postgresql-odbc-jdbc/)] [[Office 2011 is 32-bit](https://answers.microsoft.com/en-us/msoffice/forum/msoffice_other-mso_mac-mso_mac2011/microsoft-office-2011-mac-64-bit-upgrade/f3d33d70-b717-427d-afba-b600bf28e9a2)] [REVISIT]
* **34 : Load Text Files into R** [P.180-182] ...[[R script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%204)]
* **35 : Compare Teams and Players with Lattices** [P.182-185] ...[[R script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%204)]
* 36 :
* **37 : Plot Spray Charts** [P.188-193] ...[*needs coord data from #29*]

---

[explore dB] 16(P.90);

[Retrosheet pbp; Chadwick(BEVENT)] 14(P.76) +15(P.83) +22(P.107);

[ODBC; RODBC/RMySQL; DBI] 33 +35(P.184)
