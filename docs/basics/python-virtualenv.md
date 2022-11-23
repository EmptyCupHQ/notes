# Python Virtual Environments

[Virtualenv](https://virtualenv.pypa.io/en/latest/) is a tool which is used to create and manage **Virtual Environments** within python. 

A Virtual Environment is like a new isolated installation of python. Any package that you install will be downloaded and available only within the environment. The environment can easily be activated and deactivated on demand.

**Virtual Environments solves two major issues**

1. Version conflicts amongst the existing packages and the new packages
2. Tracking only the packages which are used by the project

Without virtual environments all the packages for every project that you make will be installed on your base python installation and clusters it, this makes it really hard to find the specific packages used in a project and sometimes different projects may require different versions of the same package which arises version conflict issues.


### **Installation**
- To check if virtualenv is installed on your system run `virtualenv --version` in the command line.
- If the output is something like `virtualenv 20.16.5 from ...` then you have virtualenv installed, skip to creation.
- If the output is something like `Command 'virtualenv' not found ...` you can install it via your package manager `sudo apt-get install python3-virtualenv` or via pip `pip install virtualenv`.

!!! note "venv vs virtualenv"
    [venv](https://docs.python.org/3/library/venv.html) is a minimal working version of [virtualenv](https://virtualenv.pypa.io/en/latest/) which has been incorporated to the python standard library.
    If you do not wish to install virtualenv, you can use `python -m venv` instead of `virtualenv`.<br>
    ex - `python -m venv venv` to create a virtual environment named venv.

### **Creation**
After we have installed virtualenv, now we should create the virtual environment using the command `virtualenv <NAME_OF_YOUR_ENVIRONMENT>`. The name you specify is going to be the name of the environment. 
After running the command, a folder with that name will be created which contains all the files and packages installed in that virtual environment.

After creating the virtual environment you should add it to the `.gitignore` file so that it does not get uploaded. For simplicity `venv` shall be used as the name for the environment as it is the usual name given for a virtual environment by convention and is pre-added to the `.gitignore` file. So the command would be `virtualenv venv`

### **Activation**
After creating the environment, it must be activated in order to use the isolated environment.

Due to the way POSIX derived shells work in Linux, it should be activated by sourcing the created setup file located at `<NAME_OF_YOUR_ENVIRONMENT>/bin/activate`, which in our case can be done by running the command `source venv/bin/activate`.

If you notice the commandline starts with `(venv)` that indicates, the virtual environment is successfully activated. This can be verified by running `which python` the output should be the location of the new python withing the venv.

If it does not work, try rechecking your steps and see which steps you missed. If you are getting any error message refer to [Getting Stuck](../stuck.md).
