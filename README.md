The Conflict Analyzer tool is part of an experiment infrastructure that aims to analyze conflict patterns and their frequency. 

More information here: http://twiki.cin.ufpe.br/twiki/bin/view/SPG/ConflictPatterns

If you have any questions please contact:

Paola Accioly - prga at cin.ufpe.br

Paulo Borba - phmb at cin.ufpe.br

Guilherme Cavalcanti - gjcc at cin.ufpe.br

Install and run: 

In order to run the conflicts analyzer you will need to have Java 7 or higher, groovy, maven and R installed in your machine. 
After that, you will need to clone the required projects from github and import then inside Eclipse IDE according 
to the instructions described below:

1- clone and build gitminer

    git clone https://github.com/prga/gitminer.git
    cd gitminer
    mvn clean compile package assembly:single
    cd ..

2- clone GremlinQuery and switch to right branch

    git clone https://github.com/prga/GremlinQuery.git

3-clone featurehouse (ssmerge) 

    git clone https://github.com/prga/featurehouse.git

4- clone conflictsanalyzer and checkout to CA_SemanticConflicts branch

    git clone https://github.com/prga/conflictsAnalyzer.git
    cd conflictsAnalyzer
    git fetch && git checkout CA_SemanticConflicts
    cd ..
    
    
5- clone joana
    
    git clone https://github.com/rsmbf/joana.git

After cloning those 5 projects (gitminer, GremlinQuery, featurehouse, conflictsAnalyzer, and joana), you need to import 4 projects
inside Eclipse IDE

5-Open Eclipse

6- Import project GremlinQuery

import ->maven->existing maven projects
select GremlinQuery folder and click open and then finish
install required plugins
restart eclipse

6.1 - if you have problems with groovy compiler mismatch do this

right click on project’s folder -> groovy-> fix compiler mismatch problems

right click on project’s folder -> maven -> update project

7- import featurehouse

import->general-> existing projects into workspace

select featurehouse folder, click open, check that all 4 projects are selected (CIDE_generateAST, CIDE2_ast, 
fstcomp, fstgen, fstmerge), and click finish

8- import joana

import->general-> existing projects into workspace

select joana folder, click open, and check that all projects are selected. Click finish

9- set an api baseline

http://help.eclipse.org/mars/index.jsp?topic=%2Forg.eclipse.pde.doc.user%2Ftasks%2Fapi_tooling_baseline.htm

10 -import conflictsAnalyzer

import-> existing projects into workspace

select conflictsAnalyzer folder, click open and then finish

9- Edit properties files and run conflictsAnalyzer project

Edit projectList file with the list of projects you wish to analyze, following the file pattern with one project per line

Edit configuration.properties file with the following information:

-gitminer.path, should be set to the path of gitminer project

-downloads.path, should be set to the path where you want to download projects revisions

-github.login, your github login

-github.password, your github password

-github.email, your github email 

-github.token, your github token to allow your login to make multiple requests to Github's API. Instructions to get your token
here https://help.github.com/articles/creating-an-access-token-for-command-line-use/

Edit importpath and exportpath variables from resultscript.r with the following information:

-importpath, should be set to the conflictsanalyzer folder

-exportpath, should be set to where you want to store the html with the results

run RunStudy.java class from conflictsAnalyzer project

if you have a this problem:

    Caused by: groovy.lang.GroovyRuntimeException: Conflicting module versions. Module [groovy-all is loaded in version 2.3.7
    and you are trying to load version 2.0.7

open the file pom.xml from GremlinQuery, edit the groovy-all property with the version number of the groovy compiler from your
workspace, save, and then right click GremlinQuery project -> maven-> update project

try to run RunStudy.groovy again
