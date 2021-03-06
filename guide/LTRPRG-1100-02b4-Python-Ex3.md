Navigation :: [Previous Page](LTRPRG-1100-02b3-Python-Ex2.md) :: [Table of Contents](LTRPRG-1100-00-Intro.md#table-of-contents) :: [Next Page](LTRPRG-1100-02b5-Python-Ex4.md)

---

### Exercise 3: Deploying Useful Python Packages

#### Objectives

The objectives for this exercise are to:

* Understand which Python packages are already installed
* Install useful Python packages for the Network Programmability Ninja

When a Python virtual environment is installed, it is pretty bare bones, only including a local copy of the Python 
interpreter and a few Python packages.  You will need to update the Python packages and install new Python packages 
for this lab.

#### Step 1: Understanding which Python Packages are Installed

Once a virtual environment is created, a few specific packages are automatically installed. However, sometimes when 
going back into a project after not working on it for a while, it is useful to view which packages are already 
installed.

1.  Open the Git Bash terminal by double clicking the Git Bash icon on the desktop:
    
    ![Git Bash Icon](assets/GitBash-Icon.png)
    
    ![Git Bash Terminal](assets/GitBash-Term.png)

2.  Make sure that your terminal still shows the prepended project name `(pythonenv)`. If it does not, then activate 
the Python virtual environment you created earlier in this lab with the `source ~/lab/pythonenv/Scripts/activate` 
command, for example:
    
    ```
    $ source ~/lab/pythonenv/Scripts/activate
    (pythonenv) $
    ```

3. The pip tool is a software management system to install and maintain Python packages.  Before working with pip
in this virtual environment, ensure that pip is updated to the version tested when this lab was developed 
with the `python -m pip install --upgrade pip==19.1.1` command, for example: 
    
    ```
    $ python -m pip install --upgrade pip==19.1.1
    Collecting pip==19.1.1
      Using cached https://files.pythonhosted.org/packages/5c/e0/be401c003291b56efc5
    5aeba6a80ab790d3d4cece2778288d65323009420/pip-19.1.1-py2.py3-none-any.whl
    Installing collected packages: pip
      Found existing installation: pip 19.0.3
        Uninstalling pip-19.0.3:
          Successfully uninstalled pip-19.0.3
    Successfully installed pip-19.1.1
    (pythonenv) $
    ```
    
    If the pip tool is already up-to-date with the version specified, the command output above might look something 
    like the following:
    
     ```
    $ python -m pip install --upgrade pip==19.1.1
    Requirement already up-to-date: pip==19.1.1 in c:\users\administrator\lab\python
    env\lib\site-packages (19.1.1)
    (pythonenv) $
    ```

4. Now that pip has been updated in this virtual environment, it can be used to manage packages and modules in 
Python with the `pip` command.  Display a list of installed Python packages with the `pip list` command, for example:
    
    ```
    (pythonenv) $ pip list
    Package    Version
    ---------- -------
    pip        19.1.1
    setuptools 40.8.0
    (pythonenv) $
    ```
    
    As you can see here, this virtual environment is still "vanilla" with no additional Python packages installed.
    
Let's install some useful network programmability Python packages.

#### Step 2: Installing Useful Python Packages

There are plenty of useful packages when working with network programmability, for example, to name a few essentials:

* requests: This installs a library useful for making HTTP operations, which is necessary for working with REST APIs.
* ncclient: The ncclient library provides a client library for working with NETCONF, which we will discuss later in 
this lab.
* paramiko: Paramiko provides an implementation of SSHv2 in Python, enabling a Python script to interact with a 
network device over the SSH protocol.
* netmiko: Netmiko is a library that simplifies Paramiko for use with network devices such as those running Cisco 
IOS XE.
* ipaddress: This library allows Python to handle IP addresses with functions to effectively work with IP addresses and 
subnets.

1. You can use the pip tool to install packages into your Python virtual environment with the 
`pip install <package>` command, replacing `<package>` with a Python package name.  For example, use the command
`pip install netmiko` to install the latest version of the netmiko Python package (output truncated for brevity):
    
    ```
    (pythonenv) $ pip install netmiko
    Successfully installed asn1crypto-0.24.0 bcrypt-3.1.6 cffi-1.12.3 cryptography-2
    .7 netmiko-2.3.3 paramiko-2.4.2 pyasn1-0.4.5 pycparser-2.19 pynacl-1.3.0 pyseria
    l-3.4 pyyaml-5.1 scp-0.13.2 six-1.12.0 textfsm-0.4.1
    (pythonenv) $
    ```

2. You can use the pip tool to install a very specific version of a Python package, not just the latest version 
available at that time, with the `pip install <package>==<version>`, replacing `<package>` with a Python package name
and `<version>` with the specific version of the Python package.  For example, use the command 
`pip install setuptools==39.2.0` to install version 39.2.0 of the setuptools Python package:
        
    ```
    (pythonenv) $ pip install setuptools==39.2.0
    Collecting setuptools==39.2.0
      Using cached https://files.pythonhosted.org/packages/7f/e1/820d941153923aac1d4
    9d7fc37e17b6e73bfbd2904959fffbad77900cf92/setuptools-39.2.0-py2.py3-none-any.whl
    Installing collected packages: setuptools
      Found existing installation: setuptools 40.8.0
        Uninstalling setuptools-40.8.0:
          Successfully uninstalled setuptools-40.8.0
    Successfully installed setuptools-39.2.0
    (pythonenv) $
    ```
    
    Notice that if a version of the package is already installed, then pip will uninstall the package first, then 
    install the version specified.

3. In addition to using pip to install new packages, you can upgrade existing packages with the
`pip install -U <package>` command, replacing `<package>` with the Python package name.  For example, use the 
command `pip install -U setuptools` to upgrade the setuptools package installed in the last step to the latest version 
available:
    
    ```
    (pythonenv) $ pip install -U setuptools
    Collecting setuptools
      Downloading https://files.pythonhosted.org/packages/ec/51/f45cea425fd5cb0b0380
    f5b0f048ebc1da5b417e48d304838c02d6288a1e/setuptools-41.0.1-py2.py3-none-any.whl
    (575kB)
    Installing collected packages: setuptools
      Found existing installation: setuptools 39.2.0
        Uninstalling setuptools-39.2.0:
          Successfully uninstalled setuptools-39.2.0
    Successfully installed setuptools-41.0.1
    (pythonenv) $
    ```

4. You can only install one version of a Python package within a Python virtual environment.  When developing this 
lab, we froze the versions of the prerequisite Python packages installed to ensure that there were no 
incompatibilities and maintain consistency over time.
    
    Many times, projects list the specific Python package and version requirements so that repeatable installations are 
    consistent and compatible. This will typically show up as a file named `requirements.txt` and can often be found 
    at the root of a project's file structure. One of these files exists in the Git repository for this lab, which 
    will allow for a quick installation of all required packages.
    
    You install package requirements from a requirements file with the command `pip install -r <filename>`, replacing
    `<filename>` with the requirements file name, typically `requirements.txt`.  Use the command
    `pip install -r ~/lab/LTRPRG-1100/requirements.txt` to install the Python package requirements for this lab, for 
    example (output truncated for brevity):
    
    ```
    (pythonenv) $ pip install -r ~/lab/LTRPRG-1100/requirements.txt
    Successfully installed certifi-2019.3.9 chardet-3.0.4 cryptography-2.6.1 idna-2.
    8 lxml-4.3.3 ncclient-0.6.4 requests-2.22.0 urllib3-1.25.2
    ```
    
    Now all of the correct Python packages and versions should be installed. Confirm with the `pip list` command, for
    example:
    
    ```
    (pythonenv) $ pip list
    Package      Version
    ------------ --------
    asn1crypto   0.24.0
    bcrypt       3.1.6
    certifi      2019.3.9
    cffi         1.12.3
    chardet      3.0.4
    cryptography 2.6.1
    idna         2.8
    lxml         4.3.3
    ncclient     0.6.4
    netmiko      2.3.3
    paramiko     2.4.2
    pip          19.1.1
    pyasn1       0.4.5
    pycparser    2.19
    PyNaCl       1.3.0
    pyserial     3.4
    PyYAML       5.1
    requests     2.22.0
    scp          0.13.2
    setuptools   41.0.1
    six          1.12.0
    textfsm      0.4.1
    urllib3      1.25.2
    (pythonenv) $
    ```

Now that the lab virtual environment is active and has the prerequisite Python packages installed, it is a great time
to start trying out Python.

---

Navigation :: [Previous Page](LTRPRG-1100-02b3-Python-Ex2.md) :: [Table of Contents](LTRPRG-1100-00-Intro.md#table-of-contents) :: [Next Page](LTRPRG-1100-02b5-Python-Ex4.md)
