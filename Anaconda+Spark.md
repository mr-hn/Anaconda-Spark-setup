# Setting up Spark with Jupyter
This document lists down the steps to install the required packages to run Spark within Jupyter in a single cluster. I used this [post](https://blog.sicara.com/get-started-pyspark-jupyter-guide-tutorial-ae2fe84f594f) as referrence to create this repository.

It is assumed that the Linux is freshly installed. In case any of the listed binaries are already installed, that step can be skipped.
The linux commands provided below are all for Debian based distros.

- ### Download JDK
  Running Spark in standalone mode only requires Java to be installed on the cluster. 
  JDK can be downloaded with the following command in Ubuntu.
    
    `sudo apt-get install openjdk-8-jdk`
    
  Checking if it correctly installed  
    `javac -version`  
  The result should be  
    `javac 1.8.0_xxx`  
    
    
- ### Download the latest version of Anaconda
  The next step is to install Anaconda. It can be downloaded from [here](https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh). The Python version is 3.6. [This](https://www.continuum.io/downloads) is the link to the page.  
  Once downloaded, run the below command

    `bash Anaconda3-4.4.0-Linux-x86_64.sh`  
  
  Checking if correctly installed  
    `conda --version`  
  The result should be  
    `conda 4.3.21`  
    
  To make it easier later, we add Anaconda's home directory to the Path variable. The path needs to be altered as per your destination.    
    
    `echo "export PATH=/home/harish/myPackages/anaconda3/bin:$PATH" >> ~/.bashrc`  
      
- ### Downloading Spark binaries
  Spark can be downloaded from [here](https://d3kbcqa49mib13.cloudfront.net/spark-2.1.1-bin-hadoop2.7.tgz). The name of the downloaded file will contain referrences to Hadoop. The binaries are only configured to work with HDFS but will work perfect in standalone mode as well.  
  To untar the downloaded file
      
    `tar -xzf spark-X.Y.Z-bin-hadoopA.B.tgz`
    
  Adding Spark's home to the Path variable.  
    
    `echo "export SPARK_HOME=/home/harish/myPackages/spark-X.Y.Z-bin-hadoopA.B" >> ~/.bashrc`  
    `echo "export PATH=$SPARK_HOME/bin:$PATH" >> ~/.bashrc`   
    
  You should now be able to run spark in your terminal. Restart the terminal and command  
    `spark-shell`  or  
    `pyspark`

- ### Integrating Jupyter with Spark  
  The Pyspark driver needs to be configured to use Jupyter. Thus running `pyspark` will automatically open a Jupyter notebook.  
  
    `echo "export PYSPARK_DRIVER_PYTHON=jupyter" >> ~/.bashrc`  
    `echo "export PYSPARK_DRIVER_PYTHON_OPTS_hn='notebook'" >> ~/.bashrc`  
      
  Source the .bashrc file
  
  Running `pyspark` command should now open a Jupyter notebook where you can run Pyspark.
