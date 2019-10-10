## Statistical Programming and Open Science Methods Course

### Welcome! 

This is the repository to a brand-new and in-development statistical 
programming and open science course. It is being developed by me (Joachim 
Gassen) and is being offered under the research program of the [TRR 266 "Accounting for Transparency"](https://www.accounting-for-transparency.de).

It communicates how to develop data science applications that comply to the FAIR principles of open science. That means that they are findable, accessible, interoperable and reusable. After this course, participants should 
be able to conduct data-based research projects that enable others to contribute
and collaborate. This implies that they will

-	be able to use common collaboration tools in software development like 
Git and Github,
-	understand how to use functional and object-oriented programming approaches to develop accessible code,
-	be capable to develop test routines and debug code,
-	have gained an understanding on how to profile code,
-	have developed routines for standard data analysis tasks, like data scraping, cleaning and visualization, and
-	have understood how to package statistical applications so that they are portable across platforms.


### About the repository

This repository follows a "fork and pull request" workflow. Only I can 
commit to the repository directly. You can and should fork your 
own versions of this repository, make changes by committing to your repository
and then issue a pull request if you think that your changes should be included
in this repository.

The directory structure might grow over time. Currently we have ...

- `code`: This is where our code will go.
- `docker`: Contains the docker file for our IDE container.
- `docs`: Documents or link lists that might be helpful. 
- `slides`: The source code for the slides that I plan to use in class.
- `raw_data`: Here we will store data that we receive from external sources.
- `resources`: Other external documents that we might use

... and some directories that will store output from our coding adventures.
Do not commit anything to these directories.

- `data`: Here we will store data that is being generated by code.
- `output`: Here we will store all non-data output (e.g., tables and figures).


### Setting up the environment: The local way

You need the following to run the code of the repo (Installation links for 
Windows in brackets)

- git: https://gitforwindows.org
- R > 3.5.0: https://cloud.r-project.org
- Free version of Rstudio: https://rstudio.com/products/rstudio/download/ 
- RTools (including make, I hope): https://cran.r-project.org/bin/windows/Rtools/
  Make sure that you include the Rtools directory in your path (you are asked
  about this during the installation. *NOTE: If you happen other GNU tools
  installed already (Cygwin or MinGW), please do not install RTools.* Instead,
  verify that make is available and included in your path.
- Python3: https://www.python.org/downloads/

Fork the repo on GitHub if you have not done it already.

Once you have this up and running start RStudio. Create a new project ("File -> New Project -> Version Control"). Provide the link to your forked directory and 
choose a local directory that will receive the cloned repo. 

After cloning your fork, you will have to install several packages in R that 
the code relies on. Run the following in the R console (lower left corner).

```
install.packages(c('tidyverse', 'devtools', 'rmarkdown', 'kableExtra',
'ExPanDaR', 'ggmap', 'tidyr', 'tufte', 'showtext', 'cowplot', 'DiagrammeR',
'leaflet', 'widgetframe', 'zipcode', 'shiny', 'shinyjs', 'grid', 'gridExtra',
'ggwordcloud', 'tm', 'qrcode'), 
repos = c(CRAN = 'https://mran.microsoft.com/snapshot/2019-09-25'))

devtools::install_github('bergant/datamodelr')
devtools::install_github('wmurphyrd/fiftystater')
webshot::install_phantomjs()
```
Test whether you can run all code. In the Terminal (lower left corner) run:

```
make all
```

Continue with "Produce all Output" below.


### Setting up the environment: The docker way

First you need install docker. When you have
new version of MacOS or Windows 10 Professional/Enterprise installed: https://docs.docker.com/get-started/. *Read the introductions
for your operating system.* They are important.

If you happen to have an older/less expensive version of Windows then docker toolbox is your choice: https://docs.docker.com/toolbox/. *Read the introductions
for your operating system* They are important.

After installing docker, verify that it is running by opening a shell/terminal
and issuing the command `docker` (in the black toolbox window if you run docker
toolbox). You should see a help text. If you see the help text, change to the
project directory `docker` and follow the instruction in the Dockerfile.

Once you have logged into the docker instance on the "web page" running RStudio,
create a new project within the RStudio instance running in your container
("File -> New Project -> Existing Directory"). Select the `sposm` directory.

Add your forked repository as the main remote to git.

```
git remote remove origin
git remote add origin https://github.com/YOURACCOUNT/sposm.git
git remote -v
```

The last command verifies that the new remote points to your forked 
repo. 


### Produce all Output (data, slides and link list)

Now you have your `sposm` project initialized. Test whether you can run all code. In the Terminal (lower left corner) run:

```
make all
```

### Setting up git to allow syncing your fork with the main repository

To add the main repository as an additional repository with the name `upstream`, open the terminal (lower left corner) and add the remote.

```
git remote add upstream https://github.com/joachim.gassen/sposm.git
git remote -v
```

To keep your fork in sync with the main repository, you need to follow the
strategy explained here: https://help.github.com/en/articles/syncing-a-fork.


### Disclaimer

<p align="center">
<img src="resources/programming_meme.jpg" alt="A meme!" width="40%"/>
</p>

### 2019-10-10: Issue report

If you are having issues knitting the slides and are running R 3.6.0 or later, this may be because the compatible version of datamodelr is not yet available on the CRAN. To install datamodelr from GitHub, run:
1) install.packages("devtools") [NOTE: you may have devtools already installed]
2) devtools::install_github("bergant/datamodelr")

### 2019-10-10: Pull from Joachim Gassen's master
Once you have forked your repo from Joachim Gassen's master repo, you will need to pull updates from his master repo.

To pull from your master repo, use: git pull origin master.
To pull from Joachim Gassen's master repo, I found these instructions to be helpful: https://gist.github.com/CristinaSolana/1885435