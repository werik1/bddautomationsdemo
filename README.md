# Erik's BDD Test Automation Framework
Production-ready BDD test automation framework that utilizes Selenium WebDriver and JUnit. This framework enables rapid test script creation with a Selenium wrapper class that removes the need of writing low-level automation code. 

**I would love to show you this framework in detail. Please contact me for a demo: iltikinw@gmail.com**



## Pre-requisites

The execution environment must have the following tools installed locally

> * Download and install Chrome or Firefox browser
> * Download and install **[JDK v1.8+](https://www.oracle.com/java/techologies/downloads/)**
> * Download and install **[Apache Maven v3.0+](https://maven.apache.org/download.cgi)**
> * Download and install **[Git v2.0+](https://git-scm.com/downloads)**



## Project Dependencies

This automation framework depends on the following external libraries:

* **junit**: for running a test.
* **selenium-java**: for browser automation through Java code.
* **webdrivermanager**: for managing WebDriver binaries through Java code
* **cucumber-java**: for Cucumber Java language support.
* **cucumber-jvm-deps**: for Cucumber Java Runtime Environment support.
* **cucumber-junit**: for Cucumber JUnit test framework support.
* **javafaker**: for generating randomized test data on the fly.



## Framework Structures

#### Project Structures

```
|-features                         #  all feature files are stored here
|-images                           #  all images are stored here
|-report                           #  all the generated reports are here
|-src
    |---test
        |----java                  #  all the java source files needs to stored in this folder
            |-[+]stepdefinitions   #  java class package, all the step definitions classes will be stored here
            |-[+]utility           #  java class package, all the utility classes will be stored here
            |-TestRunner           #  java class, links feature files and step definitions, used to run feature files
|-.gitignore                       #  git ignore config file
|-pom.xml                          #  project object model file for the maven software
|-READMD.md                        #  you are currently viewing this file
```

![screenshot](/images/BDDframeworkscreenshot.png)

#### Internal Structures

Below is a diagram detailing the internal structure of the framework.

![screenshot](/images/BDDinternalstructure.png)



## How to Run Tests

All the test triggering is conducted by **`mvn`** commands. This framework supports test execution by multiple different browsers.

#### Supported Browsers:
| Browser         | Option String        |
|-----------------|----------------------|
| Chrome Headless | `-Dbrowser=headless` |
| Google Chrome   | `-Dbrowser=chrome`   |
| Mozilla Firefox | `-Dbrowser=firefox`  |
| Microsoft Edge  | `-Dbrowser=edge`     |

#### Execution Triggers
This framework supports various test triggers. This is to make CI/CD integration much simpler as the test execution details can be configurable at the command line.

Executing specific tests
```
mvn test -Dcucumber.options="--tags @smoke"
```
<br/>

If you want to trigger more than one test, just add desired cucumber tags separated with space
```
mvn test -Dcucumber.options="--tags @smoke @regression @e2e"
```
<br/>

If you want to trigger test(s) with preferred browser, you can do so with specifying the browser type
```
mvn test -Dcucumber.options="--tags @smoke" -Dbrowser=chrome
```



## How to view the report

### Generating the report
After the test execution, you can generate beautiful Cluecumber HTML test report by executing the
following maven command:
```
mvn cluecumber-report:reporting
```

All the test execution reports are available as an HTML report on the following folder after test execution. Please navigate to the report folder, click the generated-report folder, and open the index.html file with your preferred browser.
```
 report
   |--[generated-report] 
        |----index.html
```


**Sample Report:**
Please navigate to this folder to view the test execution result. A sample report will look like the following.

![screenshot](/images/BDDreportscreenshot.png)