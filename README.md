The Conflict Analyzer tool is part of an experiment infrastructure that aims to analyze conflict patterns and their frequency. 

More information here: https://conflictpredictor.github.io/onlineAppendix/

Install and run: 

In order to run the conflicts analyzer you will need to have Java 7 or higher, groovy and the Eclipse IDE installed in your machine. 
After that, you will need to clone the required projects from github and import then inside Eclipse IDE according to the instructions described below:

1- clone GremlinQuery 

    git clone https://github.com/prga/GremlinQuery.git

2-clone jfstmerge and checkout to  conflict_analyzer branch

    git clone https://github.com/conflictpredictor/jFSTMerge

3- clone conflictPredictor 

    git clone https://github.com/conflictpredictor/conflictPredictor


After cloning those  projects (GremlinQuery, JFSTMerge, and conflictPredictor), you need to import them inside Eclipse IDE

4-Open Eclipse

5- Import project GremlinQuery

import ->maven->existing maven projects
select GremlinQuery folder and click open and then finish
install required plugins
restart eclipse

5.1 - if you have problems with groovy compiler mismatch do this

right click on project’s folder -> groovy-> fix compiler mismatch problems

right click on project’s folder -> maven -> update project

6- import JFSTMerge

import->general-> existing Gradle project and follow Eclipse instructions

7 -import conflictsAnalyzer

import-> existing projects into workspace

select conflictsAnalyzer folder, click open and then finish

9- Edit properties files and run conflictsAnalyzer project

Edit projectList file with the list of projects you wish to analyze, following the file pattern with one project per line

Edit configuration.properties file with the following information:

-gitminer.path, should be set to the path where you want to download projects revisions

-downloads.path, should be set to the path where you want to download projects revisions

-github.login, your github login

-github.password, your github password

-github.email, your github email 

-github.token, your github token to allow your login to make multiple requests to Github's API. Instructions to get your token
here https://help.github.com/articles/creating-an-access-token-for-command-line-use/


run RunStudy.java class from conflictsAnalyzer project

if you have a this problem:

    Caused by: groovy.lang.GroovyRuntimeException: Conflicting module versions. Module [groovy-all is loaded in version 2.3.7
    and you are trying to load version 2.0.7

open the file pom.xml from GremlinQuery, edit the groovy-all property with the version number of the groovy compiler from your
workspace, save, and then right click GremlinQuery project -> maven-> update project

try to run RunStudy.groovy again
