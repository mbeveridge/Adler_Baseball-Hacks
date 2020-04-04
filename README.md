# Baseball Hacks
#### Tips & Tools for Dissecting and Analyzing Statistics
###### Joseph Adler

---

### MyLinks for future use

Publisher's [web page for this book](http://shop.oreilly.com/product/9780596009427.do), including [errata](https://www.oreilly.com/catalog/errata.csp?isbn=9780596009427) and [example code](https://resources.oreilly.com/examples/9780596009427/)

[[Lahman's Baseball Database](http://www.seanlahman.com/baseball-archive/statistics/)] site for links to 'his' 'baseballdatabank' (csv and MySQL) ...I used "*2019 – comma-delimited version*"

"Lahman's Baseball Database" implemented **in PostgreSQL** - [michaeljaltamirano's GitHub repo](https://github.com/michaeljaltamirano/lahman-baseball-database-2016-postgresql)

[`Lahman`](https://rdrr.io/cran/Lahman/) package in R ...but currently only the (old) 2018 version in Anaconda

[RetroSheet](https://www.retrosheet.org/game.htm) play-by-play data files (event files) and a "[how to use](https://www.retrosheet.org/datause.txt)" list of fields etc

[Chadwick tools](http://chadwick.sourceforge.net/doc/index.html) website and [@chadwickbureau](https://twitter.com/chadwickbureau) from which I found [v0.7.2](https://github.com/chadwickbureau/chadwick/releases/tag/v0.7.2) of the tools

`cwevent -y 1975 -f 0,10,34 *.EV* > events.csv`
`cwgame -y 1975 -f 0,1 *.EV* > days.csv`
...command line entries from [CharlesRedmond course](https://www.udemy.com/course/baseball2/learn/lecture/3150524), to create 2 data tables with the Chadwick tools

`bdat <- inner_join(events,days,by=c("gameid"))` ...R code from [CharlesRedmond course](https://www.udemy.com/course/baseball2/learn/lecture/3151136) to join the 2 tables

---

### MyComments for future workings

[Retrosheet](https://www.retrosheet.org/game.htm) 'Regular Season Event Files' for 2019 '2019eve.zip' contained '2019eve' directory with 63 files. 30 were play-by-play details per home team (15 EVA and 15 EVN) and 30 were team rosters (and the other 3 were ALS2019.ROS; NLS2019.ROS; TEAM2019)

* `cwevent -y 2010 -f 0-96 *.EV* > events2010.csv` ...example entry used by me (cf. hack#22 P.108). [*What does the `2010` in `-y 2010` do? I accidentally ran this in directory of all 2010-2019 files and it processed all of them into output file (until appearing to run out of space mid-2018 at ~1.6M rows and 684MB), but no mention of `2010` in the output*] [2019-only output was 82MB]

* `cwgame -y 2019 -f 0-83 *.EV* > games2019.csv` ...example entry used by me. [*[Retrosheet](https://www.retrosheet.org/datause.txt) said there is a field84 (scorer name), but the 'cwgame' errormsg said max is field83 and [Chadwick](http://chadwick.sourceforge.net/doc/cwgame.html) agreed*] [1.2MB]

* `cat *.ROS > rosters2019.csv` ...example entry used by me (simply to merge all 30 roster files in the directory, having temporarily removed ALS2019.ROS and NLS2019.ROS) [*NOTE: hack#22 P.109 says "after 2002, these files included a team and position"*] [53kB]

---

### MyComments2 for future workings (trying to get it to work)

'events2019.csv' file of processed Retrosheet data. Remove "" (but it creates col header) using RStudio :
`events2019 <- read.csv("events2019.csv", header=FALSE)`
`write.csv(events2019, file="events2019_after-r.csv", quote=FALSE, row.names=FALSE)`

Copy all files to . [/tmp] directory (777 access permissions) using Bash :
`MBP-Mark:playbyplay markbeveridge$ rsync -av ~/Dropbox/repos/Adler_Baseball-Hacks/playbyplay_Retrosheet-data/2019eve/* .`

Import into events table in dB=pbp using psql :
`pbp=# COPY events FROM '/tmp/playbyplay/events2019_after-r.csv' DELIMITER ',' CSV HEADER;`

---

## 1. Basics of Baseball [P.1-38]

* **01 : Score a Baseball Game** [P.1-12]
* **02 : Make a Box Score from a Score Sheet** [P.12-19]
* 03 : Keep Score, Project Scoresheet–Style
* **04 : Follow Pitches During a Game** [P.26-30]
* **05 : Follow the Game Online** [P.31-33]
* 06 : Add Baseball Searches to Firefox
* 07 : Find Images of Stadiums


## 2. Baseball Games from Past Years [P.39-113]

* 08 : Get and Install MySQL
* 09 : Get an Access Database of Player and Team Statistics
* **10 : Get a MySQL Database of Player and Team Statistics** [P.49-54] ...[[baseballdatabank 2019 data used](http://www.seanlahman.com/baseball-archive/statistics/)]; [[Baseball-DataBank.org archived](https://web.archive.org/web/20180412211025/http://www.baseball-databank.org/)] [DEFINE KEYS]
* 11 : Make Your Own Stats Book
* 12 : Get Perl [REVISIT]
* **13 : Learn Perl** [P.67-74] ...[[Perl script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)]
* **14 : Get Historical Play-by-Play Data** [P.74-78] ...[[RetroSheet event files](https://www.retrosheet.org/game.htm)] [[Perl script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)] [*DIDN'T use Perl script - my Perl install not working*]
* **15 : Make Box Scores or Database Tables from Play-by-Play Data with Retrosheet Tools** ...[[Chadwick tools](http://chadwick.sourceforge.net/doc/index.html)] from [[Chadwick BB Bureau](http://chadwick-bureau.com/)] [[@chadwickbureau](https://twitter.com/chadwickbureau)]
* **16 : Use SQL to Explore Game Data** [P.84-91]
* 17 : Use Microsoft Access to Run SQL Queries
* 18 : Get a GUI for MySQL
* 19 : Move Data from a Database to Excel ...[SQL]
* 20 : Load Baseball Data into MySQL ...[[Perl script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)]
* 21 : Load Retrosheet Game Logs ...[[Retrosheet game logs](https://www.retrosheet.org/gamelogs/index.html)] [[`game_log_header.csv`](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)] [Perl]
* **22 : Make a Historical Play-by-Play Database** [P.107-110] ...[[Perl scripts](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%202)] [[Chadwick tools (cf. #15)](http://chadwick.sourceforge.net/doc/index.html)] [[`all_hdr.txt`](https://resources.oreilly.com/examples/9780596009427/)] [*DIDN'T use Perl script - my Perl install not working*]
* 23 : Use Regular Expressions to Identify Events [REVISIT with 'pbp' database]


## 3. Stats from the Current Season [P.114-157]

* 24 : Use Microsoft Excel Web Queries to Get Stats
* 25 : 
* 26 : 
* 27 : 
* 28 : Get Recent Play-by-Play Data [*COULDN'T see MLB.com [Gameday](http://gd2.mlb.com/components/game/mlb/) xml files; my Perl install not working*]
* **29 : Find Data on Hit Locations** [P.151-157] ...[*needs data from #28*]


## 4. Visualize Baseball Statistics [P.158-209]

* 30 : 
* 31 : Get R and R Packages
* 32 : Analyze Baseball with R
* **33 : Access Databases Directly from Excel or R** [P.170-180] ...[[ODBC drivers for 'Excel for Mac 2011'](https://support.office.com/en-us/article/odbc-drivers-that-are-compatible-with-excel-for-mac-9fa6bc7f-d19e-4f7f-9be4-92e85c77d712#ID0EAABAAA=Excel_for_Mac_2011)] : [[$100](https://uda.openlinksw.com/offers/order?uri=http%3A%2F%2Fdata.openlinksw.com%2Foplweb%2Foffer%2FOffer-UDALT-WKS-anyos-odbc-postgres-personal-2019-01%23this&type=buy&mode=u) / [$40](http://www.actualtech.com/product_opensourcedatabases.php) / [$?](https://www.simba.com/drivers/postgresql-odbc-jdbc/)] [[Office 2011 is 32-bit](https://answers.microsoft.com/en-us/msoffice/forum/msoffice_other-mso_mac-mso_mac2011/microsoft-office-2011-mac-64-bit-upgrade/f3d33d70-b717-427d-afba-b600bf28e9a2)] [REVISIT]
* **34 : Load Text Files into R** [P.180-182] ...[[R script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%204)]
* **35 : Compare Teams and Players with Lattices** [P.182-185] ...[[R script](https://resources.oreilly.com/examples/9780596009427/tree/master/baseball%20hacks%20code/chapter%204)]
* 36 :
* **37 : Plot Spray Charts** [P.188-193] ...[*needs coord data from #29*]
* 38 : Chart Team Stats in Real Time [P.193-199]
* 39 : Slice and Dice Teams with Cubes [P.200-209] [MAKE NOTES on Excel and OpenOffice?]


## 5. Formulas [P.210-309]

* 40 : Measure Batting with Batting Average ...[AVG]
* 41 : Measure Batting with On-Base Percentage ...[OBP]. P.41 says "*There are no caveats; it’s just the percentage of time the player reaches base*". However [Wikipedia](https://en.wikipedia.org/wiki/On-base_percentage) says NOT if "*due to fielding error, fielder's choice, dropped/uncaught third strike, fielder's obstruction, or catcher's interference*"
* 42 : Measure Batting with SLG ...[Slugging average]
* 43 : Measure Batting with OPS ...[On base plus slugging average]
* 44 : Measure Power with ISO ...[Isolated power]
* 45 : Measure Batting with Runs Created ...[RC]
* 46 : Measure Batting with Linear Weights ...[BR]
* 47 : Measure Pitching with ERA ...[Earned run average]
* 48 : Measure Pitching with WHIP ...[Walks plus hits per inning pitched]
* 49 : Measure Pitching with Linear Weights ...[PR]
* 50 : Measure Defense with Defensive Efficiency ...[DER]
* 51 : Measure Pitching with DIPS ...[defensive independent pitching stats]
* 52 : Measure Base Running Through EqBR ...[Equivalent Batter Runs] [*or extra base running percentage (XBRpct)*]
* 53 : Measure Fielding with Fielding Percentage ...[FCPT]


## 6. Sabermetric Thinking [P.310-409]

* 60 : Calculate Expected Runs


---

[explore dB] 16(P.90);

[ODBC; RODBC/RMySQL; DBI] 33 +35(P.184)
