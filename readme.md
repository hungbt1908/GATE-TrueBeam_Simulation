
# ⭐ About this project

# 🔧 Requirements
  * This application has been tested on VGate 9.0

# 🏃‍♂️ How to run
###### Run the application in single-mode
    ```c++
    Gate mac/main.mac
    ```
###### Run the application in parallel-mode:
* You have to install HTCondor on single machine:
    ```bash
    sudo apt-get update && apt-get install -y curl
    curl -fsSL https://get.htcondor.org | sudo /bin/bash -s -- --no-dry-run
    ```
    other way:
    ```bash
    sudo apt-get install htcondor -y
    sudo condor_master
    ```
    
* Checking the installation is sucesseful or not:
    ```bash
    condor_status
    # or
    condor_q
    ``` 
* Add new enviroments variables
    ```bash
    export GC_DOT_GATE_DIR=/home/gate
    export GC_GATE_EXE_DIR=/usr/share/gate/Gate-install/bin
    ```
* Install JobSplitter
    ```
    cd /usr/share/gate/Gate/cluster_tools
    cp -rf jobsplitter /home/gate
    cd /home/gate/jobsplitter
    make
    ```
* Add new line to the condor script:
    ```bash
    getenv         = True  
    ```
* Split the main file
    ```bash
    /home/gate/jobsplitter/gjs -numberofsplits 10 -clusterplatform condor -condorscript /home/gate/jobsplitter/script/condor.script mac/main.mac
    ```
    You will have 10 sub-inputs in .Gate folder (at GC_DOT_GATE_DIR).
* Submit jobs
    ```bash
    condor_submit mac/main.submit
    ```
# 🚀 About Me
**Bùi Tiến Hưng** - *hungbt1908@gmail.com*
1. Nuclear Engineering Lab, Hanoi University of Science and Technology (HUST).
2. Vietnam Atomic Energy Institute (VINATOM).