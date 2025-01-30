# CT 2024/25 | Coursework 0 - Installation

**Instructors:** Amir Shaikhha, Jackson Woodruff \
**TAs:** Emilien Bauer, Kim Stonehouse, Maks Kret, Shideh Hashemian \
**Demonstrators:** Emilien Bauer, Maks Kret, Shideh Hashemian

## Introduction

**Tasks:**
1. Set up Python3 as well as git.
2. Set up a Python virtual environment.
3. Clone xDSL from a repository and run some tests.

In this coursework, we want to familiarize you with the testing process in xDSL that you will use during your work on Courseworks 1-3. That being said, during the Courseworks you will only work with an xDSL package as a dependency, hence you do not need to keep xDSL installed on your machine past this coursework.

## Installation 

We will be working with xDSL version v0.24.0 for all of the courseworks this year. We also recommend Python version 3.10.

**Note:** The following instructions outline installation for UNIX-based systems (Linux, MacOS). Windows itself is not supported for this coursework. If your primary machine runs Windows only, please consider using the DICE machines avaialble in Appleton Tower or the Windows Subsystem for Linux (WSL) on your local machine. 

### Python 3.10 installation
**If you are using DICE, feel free to skip this step, as Python3.10 is the default Python version installed on all DICE machines.**

<!-- Official [Python3.10.11 documentation](https://www.python.org/downloads/release/python-31011/) provides all of the necessary GUI installers for MacOS.  -->

Python3.10 should be available to download through the package manager of your respective Linux distributions, as well as through [Homebrew](https://brew.sh) on MacOS. 

After installing Python 3.10, you can verify your installation by running the following command. 
```bash
$ which python3.10 
.../Python.framework/Versions/3.10/bin/python3.10
```

### xDSL v0.24.0 repository clone

First, you will need to **clone** xDSL. 

---
#### If 'git' is not set-up on your machine

If you used 'git' with GitHub before, you will already have either an HTTPS access token, or an SSH key, if that is the case feel free to skip this part and go to [the section just below](#if-git-is-set-up-on-your-machine). If you do not have either, you will need to create this. You can use either, just follow the guides below:
  - To create an SSH key, use [this](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
  - To create an HTTPS token, use [this](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).
    At some point, you will be asked to specify what you want to do with the token: feel free to tick all the boxes.

  At this point you are ready! Create a new folder somewhere and within it clone xDSL:
  - if you used HTTPS above, use the command
    ```
    git clone https://github.com/xdslproject/xdsl.git
    ```
  - if you used SSH, use the command
    ```
    git clone git@github.com:xdslproject/xdsl.git
    ```

Now enter the repository directory: `cd xdsl`. If this is your first time using Git, you will need to set up a bit of configuration:
  ```
  git config --global user.name "your_github_username"
  git config --global user.email "your_github_email"
  ```
  This will set your username and email globally (for all repositories, unless they overwrite this), so all future GitHub repositories will already have this set up. If you do not wish to do that, just omit the `--global`.
  You can verify the setup using `git config -l`, which will just tell you what settings you set.

Run the following commands to change the version of xDSL:
```bash
/path/to/xdsl$ git checkout v0.24.0 # switching branches to the xDSL version 0.24.0

/path/to/xdsl$ git branch # verify that the branch has indeed been switched to v0.24.0, can escape the screen by pressing 'q'
```

---
#### If 'git' is set-up on your machine

In case you already have 'git' on your machine connected to your GitHub account, simply clone the xDSL repo and change the version:

```bash
# if you used HTTPS token to set up git, use the command
/path/to$ git clone https://github.com/xdslproject/xdsl.git

# if you used SSH key to set up git, use the command
/path/to$ git clone git@github.com:xdslproject/xdsl.git

/path/to$ cd xdsl

/path/to/xdsl$ git checkout v0.24.0 # switching branches to the xDSL version 0.24.0

/path/to/xdsl$ git branch # verify that the branch has indeed been switched to v0.24.0, can escape the screen by pressing 'q'
```

---

## Python Environment Set-up 

### Choice of an IDE

`PyCharm` is a popular choice for an IDE for Python, and it comes pre-installed in your DICE desktop environment.

If you decide to use `PyCharm`, in order to install the packages, you should open the embedded terminal (`Alt+F12` by default) and continue with the following instructions of the environment set-up.

**Note:** It is important to note here, that the choice of an IDE does not affect your ability to complete the coursework, and the following instructions can be completed entirely in your terminal.

### Python Environment Set-up 

You can create an isolated python environment using [venv](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment).
To set up `venv` for the assignment, follow the steps below (a summary is given below the bulleted list):

1. Set up a virtual environment for the assignment with `python3 -m venv env`.
   This creates a subdirectory called `env` in the current folder that creates an isolated version of Python.
2. Activate the virtual environment by [`source`ing](https://linuxcommand.org/lc3_man_pages/sourceh.html) the activation file: `source env/bin/activate`
3. Confirm that you are in the virtual environment by running `which python`. The output should be `/path/to/coursework/env/bin/python`.
4. Run `pip install -U -r requirements.txt` to install dependencies within the virtual environment.
5. Run `pip install -e .` to install the ChocoPy compiler as a package.
6. If you are using PyCharm, please configure PyCharm to work with the environment by following the instructions on
   this page of the PyCharm manual: [Configure a virtual environment](https://www.jetbrains.com/help/pycharm/creating-virtual-environment.html).

In summary, the process looks as follows:

```bash
/path/to/xdsl$ python3.10 -m venv env # set up virtual environment called `env`

/path/to/xdsl$ source env/bin/activate # run activation file

(env) /path/to/xdsl$ # (env) shows up

(env) /path/to/xdsl$ which python # confirm python path
/path/to/xdsl/env/bin/python

(env) /path/to/xdsl$ pip install --upgrade pip # upgrade pip

(env) /path/to/xdsl$ pip install -U -r requirements.txt # install dependencies

(env) /path/to/xdsl$ pip install -e . # install xdsl as a package (locally in the environment)

(env) /path/to/xdsl$ # get to hacking, and best of luck! :)
```

#### Using GitHub code spaces

Instead of cloning the repository to your local machine, you can also use GitHub codespaces to do your coursework. This is a beta-test, so it is an optional offer that is delivered on a best-effort basis. To use GitHub codespaces click on the green "Code" button at the top of this repository, select "code spaces" and create your personal codespace. Then enter the console and run:

```bash
$ export PATH=/home/codespace/.local/lib/python3.10/site-packages/bin/:$PATH
$ pip install -U -r requirements.txt # install dependencies
$ pip install -e . # install ChocoPy as a package
$ # get to hacking, and best of luck! :)
```

## Run the tests in xDSL

You can use `lit` to automatically test your code, which is included in the `requirements.txt`.

To run it locally, do:

```bash
(env) /path/to/xdsl$ lit -v tests/filecheck
```

This will examine recursively all the files with valid formats inside the above directory.
The `-v` flag adds a verbose output with more information in case some tests fail.

You can also leverage the `--timeout <seconds>` flag, in order to bound the time allowed for your test cases to run.
This way you can detect if your parser loops infinitely in some test cases.

For more details on the configuration of `lit`, see `tests/lit.cfg`.
For more info on `lit` check the [online documentation](https://filecheck.readthedocs.io/en/latest/01-what-is-filecheck.html).
