# Installation of Apache Zeppelin on Ubuntu system

## Prerequisite
* Ubuntu system on virtual machine / dual boot system
* Only paste the command after `$` sign to your shell

## Step 1: Install homebrew
* Initiate your ubuntu system.
* Press `Ctrl` + `Alt` + `T` to open a terminal. 
* Paste the following command into it.
```shell
$ sudo apt install linuxbrew-wrapper
```
* Then press `Enter`.
* The installation should be complete quite shortly

## Step 2: Install java
* First check whether java has been installed
```shell
$ java -version
```
* The java has not been installed if following output appears
```console
Command 'java' not found, but can be installed with:
```
* in this case, type following command:
```shell
$ sudo apt install default-jre
```
* The java shoul be installed if following appears: (it is encouraged to double check the version after the installation)
```console
openjdk version "1.8.0_171"
OpenJDK Runtime Environment (build 1.8.0_171-8u171-b11-0ubuntu0.18.04.1-b11)
OpenJDK 64-Bit Server VM (build 25.171-b11, mixed mode)
```

## Step 3: Install everythin we need
In this part, you can see how powerful brew is.
### Requirement
* Scala
* Spark
* Zeppelini
### Command to run
Note that run the following **Line by Line**
```shell
$ brew install scala
$ brew install apache-spark
$ brew install apache-zeppelin
```

## Step 4: Run Zeppelin for the very first time
* At your zeppelin **bin** directory, type this to start zeppelin:
```shell
$ sh zeppelin-daemon.sh start
```
* Wait for a moment and navigate to port 8080 of your local host, which paste the following to your web browser:
`http://localhost:8080`
* Create a new note in your zeppelin, type something like the following to check whether your zeppelin is working properly
```scala
// should echo with Hellow World as output
println("Hello World")
// should have 2 as output
1 + 1
```

## Step 5: Zeppelin for future use
* When you reboot, you need to again locate where your zeppelin is, so type this to find out:
```shell
$ brew info apache-zeppelin
```
You should get something like this as your output:
```console
apache-zeppelin: stable 0.8.0, HEAD
Web-based notebook that enables interactive data analytics
https://zeppelin.apache.org
/home/linuxbrew/.linuxbrew/Cellar/apache-zeppelin/0.8.0 (32,936 files, 1GB) *
  Built from source on 2018-01-01 at 00:00:00
From: https://github.com/Linuxbrew/homebrew-core/blob/master/Formula/apache-zeppelin.rb
==> Options
--HEAD
	Install HEAD version
```
* `cd` to your zeppelin bin location, which in my case is:
```shell
$ cd /home/linuxbrew/.linuxbrew/Cellar/apache-zeppelin/0.8.0/bin
```
* start your zeppelin exactly as *Step 4*
* If you are kind of lazy, you might consider add an `alias` for your `cd` command

## Reference
* Day accessed: 2018/08/02 (in `yyyy/mm/dd` format)
* [locally install zeppelin on MacOS](https://dziganto.github.io/anaconda/shiro/spark/zeppelin/zeppelinhub/How-To-Locally-Install-Apache-Spark-And-Zeppelin/)
* [use brew on ubuntu](https://stackoverflow.com/questions/33353618/can-i-use-brew-on-ubuntu)
* [add a alias](https://superuser.com/questions/167221/can-i-add-a-shortcut-to-replace-a-path-in-linux)
* [install java on ubuntu, ref. 1](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04)
* [install java on ubuntu, ref. 2](https://poweruphosting.com/blog/install-java-ubuntu/)