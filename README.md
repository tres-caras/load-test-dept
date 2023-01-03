# README
 
​
This README would normally document whatever steps are necessary to get you aplication up and running.
​
## Installation
---
Two way to install and run the load project, the options are `Taurus, Selenium and JMeter` and the other way is only `Jmeter`
​
* ## **Taurus, Selenium and JMeter**
​
    ### Mac OS
​
    ### Install Homebrew Package
​
    You can use brew package manager to install [Taurus](https://gettaurus.org/install/Installation/#Mac-OS):
​
    ```
    brew install bzt
    ```
​
    and to update it:
​
    ```
    brew upgrade bzt
    ```
​
    If your brew auto update is switched off don't forget to manage it manually.
​
    NOTE: There is an issue with brew installation connected with numpy. In order to avoid this problem we suggest installing Taurus using pip tool.
​
    To install Taurus with pip you need command line developers tools and Python 3.7+ installed. Then you need to install Cython if it is not installed using the following command:
​
    ```
    pip3 install Cython
    ```
​
    Then just install bzt:
​
​
    ```
    pip3 install bzt
    ```
​
    To upgrade, use:
​
​
    ```
    pip3 install --upgrade bzt
    ```
​
* ## **JMeter**
​
    Download [JMeter](https://jmeter.apache.org/download_jmeter.cgi) binary (Requires Java 8+) and [run](https://jmeter.apache.org/usermanual/get-started.html#running) Jmeter UI
​
    * Download apache-Jmeter.zip file
    * Unzip it
    * Open terminal-> go to apache-Jmeter/bin
    * sh `jmeter.sh`
​
    or
​
    Install JMeter using the following command
​
    ```
    brew install JMeter
    ```
    then open it using this
    ```
    open /usr/local/bin/jmeter
    ```
​
## Run Test
---
​
* ## **Taurus, Selenium and JMeter**
​
    open console on the root project and run the following command
​
    ```
    bzt load-test-v1-3-nav-Combined-JMeter-and-Selenium.yaml
    ```
    the yaml file have two parts, the actions commands of the Selenium test for UI and the call of the JMeter file that these running simultaneously.
​
* ## **JMeter**
    Run [Jmeter](https://jmeter.apache.org/usermanual/get-started.html) in GUI Mode and Open .jmx file on test -> JMX
    start the test using the start button 
    or
    open console on the .jmx file and run a basic command line parameter is
​
    ```
    jmeter -n -t your_script.jmx
    ```
​
## Report files
---
​
* ## **Taurus, Selenium and JMeter**
    After run the test and finish test, is add a new directory on the root project the following example format
    
    `2022-12-27_11-07-42.865059`
    
    on this directory have different log as reports and another files, but in the `output` directory have the JMeter .csv report file with the list of the request of the JMeter test (output the view result tree).  
​
* ## **JMeter**
​
    The `.csv` file add on the JMX directory with `20221227-135221` format, the .csv file is output the view result tree.
## **JMeter HTML Report**
​
### Steps
​
- On the root project directory, open the terminal and include the following command line
​
```
jmeter -n -t test/JMX/BZT\ Generated\ Test\ Plan.jmx
```
​
- Wait to finish the test.
​
- Move to the JMX directory `cd test/JMX` and lists all file `ll`
​
- Identify the last directory add with this form of name *20221227-135221* and enter this
​
- Add a new directory `mkdir html-report`
​
- Back to the root project and run the following command
<br />
​
```
jmeter -g test/JMX/20221228-134156/resultOutput.csv -o test/JMX/20221228-134156/html-report
```
​
- Go to the html-report directory `cd html-report` and open the `index.html` 
​
## NOTE
---
​
### Concurrency
​
* ## **Taurus, Selenium and JMeter**
    On the .yaml file have a lot of setting, but following are the important parts
​
    <details>
​
    * concurrency: 2  # all tests will be split into 2 processes - number of target concurrent virtual users
​
    * ramp-up: 30s  # time to reach target concurrency
​
    * hold-for: 59s  #  time to hold target concurrency
​
    </details>
​
​
* ## **JMeter**
​
    go to load-test-v1-nav-Http (bzm - Concurrency Thread Group) and setting the following input fields
​
    <details>
    
    * Target Concurrency: Total number of threads (users) in the test.
    
    * Ramp-up Time (min): Total ramp-up duration in minutes. You can also provide ramp-up duration in seconds by choosing ‘seconds’ in ‘Time Unit’ option given below the scenario chart.
    
    * Ramp-up Steps Count: Total number of steps in which a group of threads (users) will ramp-up.
    
    * Hold Target Rate Time (min): The steady-state when all the threads are active. This is also called as system monitoring window. If you want to monitor the system/application performance for 1 hour then the value for 
    hold target rate time will be 60 minutes or 3600 seconds. The ramp-up time does not add to this time.

    </details>