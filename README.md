# README

# Maps

### Which partner’s Stars and OTHER PROJECT were used
The Stars code was provided by Hari. The OTHER PROJECT code was provided by Hari's Partner's.

### Partner division of labor
For this project, Hari worked primarily on the ways, nearest, and map commands, and parsing the database. Hari's Partner's worked primarily on the route command, A* search, the database parsing, 
and caching. We collaborated on these areas in many parts whenever the other asked for help. Both Hari's Partner's and Hari worked on writing system and JUnit tests, Checkstyle,
 commenting the code, and the README. This was an equal division of labor.

### Known bugs
There are no known bugs at this time.

### Design details specific to your code, including how you fit each of the prior project’s codebases together
We used Hari's REPL, so Hari's Partner's's OTHER PROJECT code had to be modified to fit his REPL's specifications. We stored the entire KDTree upon loading the 
database because it only takes 6 seconds for our biggest database. In addition, we used Google Guava Cache to store some information from the database 
that's used for searching for a route.  

### Any runtime/space optimizations you made beyond the minimum requirements
For this project, we use a KDTree to do the nearest neighbor search. We store the KDTree upon the uploading of the database. This way, we only need to create the KDTree once and we can continue utilizing it for the finding of nearest neighbors. 

In addition, we use a Guava Cache to store information that we pull from the database about nodes and ways. Because it can be time-intensive to access the database, this helps us limit the amount of time we actually enter the database and retrieve information.

For our A* search, we utilize a HashMap to store information about distances, since this allows us to access that information in near constant time. After we have found a path, we reconstruct it by using pointers to other nodes in the graph, allowing us to do our searches in a very timely manner.

Finally, in many instances in our code, we utilize techniques of short-circuiting to limit doing unnecessary comparisons. One example of this can be seen in AStar.java

### How to run your tests
JUnit tests can be run by entering `mvn test` into a terminal. They are also called by default with `mvn site` and `mvn package`. To temporarily run without tests while you are working on the ways command, run `mvn package -Dmaven.test.skip`. Once the ways command works, then you should be able run the package with tests.
Regarding our system tests, enter `./cs32-test tests/student/maps/*.test --timeout 120`. 
Tests found in `tests/student/maps/big_db` require `maps.sqlite3`, which cannot not be uploaded to GitHub due to its large size. 
In order to run the tests that require `maps.sqlite3`, you will need log into a department machine and place maps.sqlite3 in a newly created folder
 called `maps_big_db` in `ltmp`. 
To run them on other machines, you will need to edit all the files in `tests/student/maps/big_db` to contain the location you choose.
Once the file is there, run `./cs32-test tests/student/maps/big_db/*.test --timeout 120`.

### Any tests you wrote and tried by hand
The tests found in `AStarTest` as well as JUnit and system test involving `smallMaps.sqlite3` and `modifiedSmallMaps.sqlite3` (a database we created ourselves)
are written and tried by hand.

### How to build/run your program from the command line
The program can be built from the command line with `mvn package` and can be run with `./run` for the REPL version only. 
Following that, you simply need to enter the commands that you wish to run, and they should run.

We do not have GUI integration for this projct. Please make sure that you navigate to the folder containing the maps program. 
