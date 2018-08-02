# This are my failed attempts in setting up local spark

## [Windows/Linux] Run jupyter scala with spark
* status: successfully installed jupyter scala kernel
* problem: cannot find a way to configure with spark as few people would try to use jupyter scala kernel working with spark
* For windows: please refer to this [link](https://stackoverflow.com/questions/35563545/how-do-i-install-scala-in-jupyter-ipython-notebook)
  * download the designated zip; navigate to the directory and then run the bat:
```shell
start jupyter-scala.bat
```
  * check if the kernel has been installed (you should find something like `scala211`):
```shell
jupyter kernelspec list
```
  * you can create a new notebook with Scala kernel after you relanuch jupyter notebook
* For Linux, just refer to the GitHub [repo](https://github.com/jupyter-scala/jupyter-scala#quick-start)

## [Windows] Run Spark-notebook
* status: notebook is not working
* problem: WebSocket lost, unresolved even after the shutdown of all firewall
* Please refer to this [link](http://spark-notebook.io/)
  * request a building from the official website and you can receive a link for download (waiting time is around 30 minuates in my case)
  * the spark and scala is built-in, but make you have java > 7
  * for running, refer to [here](https://github.com/spark-notebook/spark-notebook/blob/master/docs/quick_start.md)

## [Windows] Run window-ubuntu subsystem to pretend "windows" as linux
* status: subsystem is able to take some windows basic task, such as `mkdir`, but cannot function fully like Windows or Ubuntu
* problem: the ubuntu subsystem did not know about environment variables that set windows; windows powershell commands do not work, while many Linux command do not work as well
* run powershell as admin to install; for detail guides, please refer at [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
  * For jupyter notebook, please refers to my docs [here](jupyter_windows.md)
    * Anyhow you will eventually failed as ubuntu subsystem do not respond with your command
  * For zeppelin, please refer at apache official guideline at [here](https://zeppelin.apache.org/docs/0.7.2/install/install.html)
    * in windows way, the subsystem does not work with `.cmd` file
    * in linux way, the subsystem behaves strange and cannot exeute the command normally
  * in fact, I tried to install firefox into the subsystem
    * it worked, but unable to run with the command `firefox`
    ```console
    Error: no DISPLAY environment variable specified
    ```
    * however, checking version (run `firefox -v`) would give the right result
    ```console
    Mozilla Firefox 61.0.1
    ```
    * the DISPLAY can be set in [coventional ubuntu way](https://stackoverflow.com/questions/784404/how-can-i-specify-a-display), however further problems energes such as following, which discouraged me from invastigation after pointless trying for several days. For example:
    ```console
    Unable to init server: Broadway display type not supported: localhost:0.0
    Error: cannot open display: localhost:0.0
    ```

## [Windows] Run zeppelin locally
* status: so far, only `%md` intepreter is working in zeppelin on windows
* problem: unkown error each time, sometimes with `localhost`, and sometimes is `RunTimeException`
* supporting reference:
  * [part 1](https://hernandezpaul.wordpress.com/2016/01/24/apache-spark-installation-on-windows-10/)
  * [part 2](https://hernandezpaul.wordpress.com/2016/11/14/apache-zeppelin-installation-on-windows-10/)
* I cannot locate the problem even I have strictly follow the guide line, which prevented me from further trying after spent another few pointless days (felt like almost success everytime)

## [Windows/Linux] jupyter notebook with official spark kernel: [Toree](https://toree.incubator.apache.org/docs/current/user/quick-start/)
* status: able to install the kernel, but error message prompts out everytime when trying to use the notebook
* problem: 
  * windows: unknown error
  * linux: jupyter needs to be updated to > 5.0.0, however `conda` can only update to 4.4.0
* the installation process seems to be simple enough as under either windows or linux, installation only requires 2 command:
```shell
pip install toree
jupyter toree install --spark_home=/usr/local/bin/apache-spark/
```
  * the windows problems seems to be again related to the websocket, just as *spark-notebook*
  * the linux problem seems to be with conda [channel](https://conda.io/docs/user-guide/tasks/manage-channels.html), but there is no where to find the required package to install jupyter >= 5.0.0. So I think that the development team has not prepared this.