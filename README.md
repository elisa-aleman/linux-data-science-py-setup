# Linux (or WSL) Python setup environment for Machine learning Laboratory

This is how I set up a fresh linux installation to start working in machine learning and programming. 

It is also useful for WSL (Windows Subsystem for Linux) and I will add comments for it as well.

I keep this tutorial handy in case I do a clean OS install or if I need to check some of my initial settings.

<!-- MarkdownTOC autolink="true" autoanchor="true" -->

- [WSL installation guide](#wsl-installation-guide)
    - [WSL: Paths to directories outside of the Linux environment](#wsl-paths-to-directories-outside-of-the-linux-environment)
- [Basic Settings](#basic-settings)
    - [Install basic apt and apt-get software](#install-basic-apt-and-apt-get-software)
    - [Install SublimeText](#install-sublimetext)
        - [Easy TeX math: Add paired $ signs to the keybinds](#easy-tex-math-add-paired--signs-to-the-keybinds)
    - [Easily transform 2 spaced indent to 4 spaced indent](#easily-transform-2-spaced-indent-to-4-spaced-indent)
- [Install Python with pyenv](#install-python-with-pyenv)
    - [Install virtualenv](#install-virtualenv)
    - [Useful Data Science libraries](#useful-data-science-libraries)
        - [Basic tasks:](#basic-tasks)
        - [Plotting:](#plotting)
        - [Basic data science and machine learning:](#basic-data-science-and-machine-learning)
        - [Data mining / text mining / crawling / scraping websites:](#data-mining--text-mining--crawling--scraping-websites)
        - [Natural language processing \(NLP\):](#natural-language-processing-nlp)
        - [Neural network and machine learning:](#neural-network-and-machine-learning)
        - [XGBoost](#xgboost)
        - [LightGBM](#lightgbm)
        - [MINEPY / Maximal Information Coefficient](#minepy--maximal-information-coefficient)
        - [Computer Vision \(OpenCV\)](#computer-vision-opencv)
            - [Install OpenCV with ffmpeg](#install-opencv-with-ffmpeg)
- [Install and setup Flask for Python Web Development](#install-and-setup-flask-for-python-web-development)
- [Setup Git](#setup-git)
    - [Check your branches in git log history in a pretty line](#check-your-branches-in-git-log-history-in-a-pretty-line)
    - [GitHub Markdown math expressions for README.md, etc.](#github-markdown-math-expressions-for-readmemd-etc)
    - [GitLab Markdown math expressions for README.md, etc.](#gitlab-markdown-math-expressions-for-readmemd-etc)
    - [Install Git Large File System](#install-git-large-file-system)
    - [Make a new Git \(LFS\) repository from local](#make-a-new-git-lfs-repository-from-local)
    - [Manage multiple GitHub or GitLab accounts](#manage-multiple-github-or-gitlab-accounts)
        - [WSL and Windows shared ssh keys](#wsl-and-windows-shared-ssh-keys)
- [Install and setup Ruby, Bundler and Jekyll for websites](#install-and-setup-ruby-bundler-and-jekyll-for-websites)
- [Install LaTeX and latexdiff](#install-latex-and-latexdiff)
- [Shell Scripting for convenience](#shell-scripting-for-convenience)
    - [Basic flag setup with getopts](#basic-flag-setup-with-getopts)
    - [Argparse-bash by nhoffman](#argparse-bash-by-nhoffman)
    - [LaTeX helpers](#latex-helpers)
- [Install Pandoc to convert/export markdown, HTML, LaTeX, Word](#install-pandoc-to-convertexport-markdown-html-latex-word)
- [Accessibility Stuff](#accessibility-stuff)
    - [Accessible Color Palettes with Paletton](#accessible-color-palettes-with-paletton)
    - [Reading tools for Neurodivergent people](#reading-tools-for-neurodivergent-people)
    - [Reading white PDFs](#reading-white-pdfs)
        - [Firefox](#firefox)
        - [Google Chrome](#google-chrome)
- [CUDA and GPU settings](#cuda-and-gpu-settings)

<!-- /MarkdownTOC -->

<a id="wsl-installation-guide"></a>
## WSL installation guide

https://www.groovypost.com/howto/install-windows-subsystem-for-linux-in-windows-11/

1. Open the cmd with administrator privileges
2. `wsl --install`
3. Restart computer
4. Make username under new Linux terminal

<a id="wsl-paths-to-directories-outside-of-the-linux-environment"></a>
### WSL: Paths to directories outside of the Linux environment

If in the above tutorial for separate git accounts, for example, you needed to use paths to locations in the Windows system, you can replace C: with /mnt/c/

<a id="basic-settings"></a>
## Basic Settings

Setup root password:
https://www.cyberciti.biz/faq/how-to-change-root-password-on-macos-unix-using-terminal/

```
sudo passwd root
```

- Set up the screen lock command so you can do it every time you stand up:
https://itsfoss.com/ubuntu-shortcuts/

- Set up your WiFi connection.
- For ease of use, make hidden files and file extensions visible.

Hidden files visibility:
I can't work without seeing hidden files, so in Ubuntu we can do `CTRL+H` and the hidden files will appear. 

To set it as the default:

https://help.ubuntu.com/stable/ubuntu-help/nautilus-views.html.en

<a id="install-basic-apt-and-apt-get-software"></a>
### Install basic apt and apt-get software

In order for most anything else to install properly, we need these first:

```
sudo apt update
sudo apt install \
    build-essential \
    curl \
    libbz2-dev \
    libffi-dev \
    liblzma-dev \
    libncursesw5-dev \
    libreadline-dev \
    libsqlite3-dev \
    libssl-dev \
    libxml2-dev \
    libxmlsec1-dev \
    llvm \
    make \
    tk-dev \
    wget \
    xz-utils \
    zlib1g-dev
```


<a id="install-sublimetext"></a>
### Install SublimeText

- Install SublimeText4 for ease of use (this is my personal favorite, but it's not necessary)

https://www.sublimetext.com/docs/linux_repositories.html

```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/sublimehq-archive.gpg

sudo apt-get update
sudo apt-get install sublime-text
```

- Paste the SublimeText4 preferences (my personal preferences)

```
{
    "ignored_packages":
    [
        "Vintage",
    ],
    "spell_check": true,
    "tab_size": 4,
    "translate_tabs_to_spaces": true,
    "copy_with_empty_selection": false
}
```

Also, Sublime Text is all about the plugins. Install Package Control by typing CTRL+Shift+P, then typing "Install Package Control"

Then here's some cool packages to try:

- [LaTeXTools](https://packagecontrol.io/packages/LaTeXTools)
- [MarkdownTOC](https://packagecontrol.io/packages/MarkdownTOC)
- [MarkdownPreview](https://packagecontrol.io/packages/MarkdownPreview)
- [MarkdownEditing](https://packagecontrol.io/packages/MarkdownEditing)
- [Alignment](https://packagecontrol.io/packages/Alignment)
- [IncrementSelection](https://packagecontrol.io/packages/Increment%20Selection)
- [Selection Evaluator](https://packagecontrol.io/packages/Selection%20Evaluator)
- [Paste as One Line](https://packagecontrol.io/packages/Paste%20as%20One%20Line)
- [Invert Current Color Scheme](https://packagecontrol.io/packages/Invert%20Current%20Color%20Scheme)
- [PackageResourceViewer](https://packagecontrol.io/packages/PackageResourceViewer)

Now, for the Invert Current Color Scheme, I have my own fork that works with Sublime Text 4, so use the PackageResourceViewer to replace the main python file with my code:
 
https://github.com/elisa-aleman/sublime-invert-current-color-scheme

In MarkdownTOC.sublime-settings, paste the following for hyperlink markdowns and compatibility with MarkdownPreview:

```
{
  "defaults": {
    "autoanchor": true,
    "autolink": true,
    "markdown_preview": "github",
    "uri_encoding": false
  },
}
```

<a id="easy-tex-math-add-paired--signs-to-the-keybinds"></a>
#### Easy TeX math: Add paired $ signs to the keybinds

I found myself needing paired $dollar signs$ for math expressions in either LaTeX, GitLab with KeTeX or GitHub also with a different syntax but still some interpretation of TeX.

Searching for [how to do it on macros](https://forum.sublimetext.com/t/snippet-wrap-current-line-or-selection/53285), I found this post about keybindings which is a way better solution:

https://stackoverflow.com/questions/34115090/sublime-text-2-trying-to-escape-the-dollar-sign

Which, as long as we implement the double escaped dollar sign solution, we can use freely.

- Preferences > Key Bindings:
- Add this inside the brackets:

```
// Auto-pair dollar signs
{ "keys": ["$"], "command": "insert_snippet", "args": {"contents": "\\$$0\\$"}, "context":
    [
        { "key": "setting.auto_match_enabled", "operator": "equal", "operand": true },
        { "key": "selection_empty", "operator": "equal", "operand": true, "match_all": true },
        { "key": "following_text", "operator": "regex_contains", "operand": "^(?:\t| |\\)|]|\\}|>|$)", "match_all": true },
        { "key": "preceding_text", "operator": "not_regex_contains", "operand": "[\\$a-zA-Z0-9_]$", "match_all": true },
        { "key": "eol_selector", "operator": "not_equal", "operand": "string.quoted.double", "match_all": true }
    ]
},
{ "keys": ["$"], "command": "insert_snippet", "args": {"contents": "\\$${0:$SELECTION}\\$"}, "context":
    [
        { "key": "setting.auto_match_enabled", "operator": "equal", "operand": true },
        { "key": "selection_empty", "operator": "equal", "operand": false, "match_all": true }
    ]
},
{ "keys": ["$"], "command": "move", "args": {"by": "characters", "forward": true}, "context":
    [
        { "key": "setting.auto_match_enabled", "operator": "equal", "operand": true },
        { "key": "selection_empty", "operator": "equal", "operand": true, "match_all": true },
        { "key": "following_text", "operator": "regex_contains", "operand": "^\\$", "match_all": true }
    ]
},
{ "keys": ["backspace"], "command": "run_macro_file", "args": {"file": "Packages/Default/Delete Left Right.sublime-macro"}, "context":
    [
        { "key": "setting.auto_match_enabled", "operator": "equal", "operand": true },
        { "key": "selection_empty", "operator": "equal", "operand": true, "match_all": true },
        { "key": "preceding_text", "operator": "regex_contains", "operand": "\\$$", "match_all": true },
        { "key": "following_text", "operator": "regex_contains", "operand": "^\\$", "match_all": true }
    ]
},
```

<a id="easily-transform-2-spaced-indent-to-4-spaced-indent"></a>
### Easily transform 2 spaced indent to 4 spaced indent

https://forum.sublimetext.com/t/can-i-easily-change-all-existing-2-space-indents-to-4-space-indents/40158/2

- Sublime text, lower right corner
- Click on Spaces
- Select the current space number
- Click Convert indentation to Tabs
- Select the desired space number
- Click Convert indentation to Spaces

<a id="install-python-with-pyenv"></a>
## Install Python with pyenv

Depending on your installation, you might already have a python, but it is better to avoid using it as it interacts with the system, so we install a local version with Pyenv. Pyenv also makes it so that pip and python are always matched for each other in the correct version.

This is specially useful if you need different versions for different projects (Maybe caused by tensorflow updates vs other libraries updates...), you should follow these tutorials:

https://github.com/pyenv/pyenv#installation

For Linux, we have to use the github distribution, clone it and install it with make. Then we add the paths to .bash_profile for bash or to .zprofile for zsh.

```
cd ~
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
cd ~/.pyenv && src/configure && make -C src
cd ~

source ~/.bash_profile
```

Now let's install and set the latest version:
```
pyenv install 3.10.7
pyenv global 3.10.7
```

And then we can add it to our PATH so that every time we open `python` it's the pyenv one and not the system one:

```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile

source ~/.bash_profile
```

That `eval` line I found out thanks to [this StackOverflow post](https://stackoverflow.com/questions/33321312/cannot-switch-python-with-pyenv)

We can confirm we are using the correct one:

```
pyenv versions
which python
python -V
which pip
pip -V
```

<a id="install-virtualenv"></a>
### Install virtualenv

Virtualenv allows me to install different libraries under pip for specific projects.

```
pip install virtualenv
```

Usage guide is here:<br>
https://mothergeo-py.readthedocs.io/en/latest/development/how-to/venv-win.html

<a id="useful-data-science-libraries"></a>
### Useful Data Science libraries

This is my generic fresh start install so I can work. Usually I'd install all of them in general, but recently I only install the necessary libraries under venv. There's more libraries with complicated installations in other repositories of mine, and you might not wanna run this particular piece of code without checking what I'm doing first. For example, you might have a specific version of Tensorflow that you want, or some of these you won't use. But I'll leave it here as reference.

<a id="basic-tasks"></a>
#### Basic tasks:

```
pip install numpy scipy jupyter statsmodels \
pandas pathlib tqdm retry openpyxl
```

<a id="plotting"></a>
#### Plotting:
```
pip install matplotlib adjustText plotly kaleido
```

<a id="basic-data-science-and-machine-learning"></a>
#### Basic data science and machine learning:
```
pip install sklearn sympy pyclustering
```

<a id="data-mining--text-mining--crawling--scraping-websites"></a>
#### Data mining / text mining / crawling / scraping websites:
```
pip install beautifulsoup4 requests selenium
```

<a id="natural-language-processing-nlp"></a>
#### Natural language processing (NLP):
```
pip install gensim nltk langdetect
```

For Japanese NLP tools see:
https://github.com/elisa-aleman/MeCab-python

For Chinese NLP tools see:
https://github.com/elisa-aleman/StanfordCoreNLP_Chinese

<a id="neural-network-and-machine-learning"></a>
#### Neural network and machine learning:
```
pip install tensorflow tflearn keras \
torch torchaudio torchvision \
optuna
```
<a id="xgboost"></a>
#### XGBoost 

To Install with CPU:
```
pip install xgboost
```

To Install with CUDA GPU integration:
```
git clone --recursive https://github.com/dmlc/xgboost
cd xgboost
mkdir build
cd build
cmake .. -DUSE_CUDA=ON
make -j8
cd ../python-package
python setup.py install
```

<a id="lightgbm"></a>
#### LightGBM

To Install with CPU:

```
pip install lightgbm
```

Install dependencies:
```
apt-get install libboost-all-dev
apt install ocl-icd-libopencl1
apt install opencl-headers
apt install clinfo
apt install ocl-icd-opencl-dev
```
Install with CUDA GPU integration:

```
pip install lightgbm --install-option=--gpu --install-option="--opencl-include-dir=/usr/local/cuda/include/" --install-option="--opencl-library=/usr/local/cuda/lib64/libOpenCL.so"
```

<a id="minepy--maximal-information-coefficient"></a>
#### MINEPY / Maximal Information Coefficient

For Minepy / Maximal Information Coefficient, we need the Visual Studio C++ Build Tools as a dependency, so install it first:<br>
https://visualstudio.microsoft.com/visual-cpp-build-tools/

```
pip install minepy
```

<a id="computer-vision-opencv"></a>
#### Computer Vision (OpenCV)

with CPU and no extra options:

```
python -m pip install -U opencv-python opencv-contrib-python
```


<a id="install-opencv-with-ffmpeg"></a>
##### Install OpenCV with ffmpeg

Install dependencies:

```
apt-get update
apt-get upgrade
apt-get install build-essential
apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
apt-get install libxvidcore-dev libx264-dev
apt-get install libgtk-3-dev
apt-get install libatlas-base-dev gfortran pylint
apt-get install python2.7-dev python3.5-dev python3.6-dev
apt-get install unzip
```

Now the ffmpeg dependency:
```
add-apt-repository ppa:jonathonf/ffmpeg-3
apt update
apt install ffmpeg libav-tools x264 x265
```

Check the version:
```
ffmpeg
```

Download and build opencv

```
wget https://github.com/opencv/opencv/archive/3.4.0.zip -O opencv-3.4.0.zip
wget https://github.com/opencv/opencv_contrib/archive/3.4.0.zip -O opencv_contrib-3.4.0.zip

unzip opencv-3.4.0.zip
unzip opencv_contrib-3.4.0.zip

cd  opencv-3.4.0
mkdir build_3.5
mkdir build
cd build
```

Make, but remember to replace Python versions:

```
which python
```

```
cmake -DCMAKE_BUILD_TYPE=Release \
    -D WITH_FFMPEG=ON \
    -D PYTHON3_EXECUTABLE=<path to your python> \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-3.4.0/modules \
    -D OPENCV_ENABLE_NONFREE=True ..

make -j8        #(where -j8 is for 8 cores in the server cpu)
make install
ldconfig
```



<a id="install-and-setup-flask-for-python-web-development"></a>
## Install and setup Flask for Python Web Development

I'm using this guide:
https://flask.palletsprojects.com/en/2.1.x/installation/#install-flask

For Web Development, it's apparently better to make a Virtual Environment to install flask project-wise instead of system or user level.

First we go to our project and make the virtual environment.

```
cd my-project
python -m venv venv
. venv/scripts/activate
```
it might also be
```
. venv/bin/activate
```
so if one fails try the other.

Activate results in the python and pip versions to be internal to the project now and active in the bash:

```
which python
>>> .... my-project\venv/Scripts/python

pip --version
pip 22.1 from c:\users\...\my-project\venv\lib\site-packages\pip (python 3.9)
```

So since this pip is empty, let's install ONLY what we need for the project:

```
pip install --upgrade pip
pip install selenium beautifulsoup4 pandas pathlib retry
pip install flask
```

Now let's test it:

I'm using this guide here:

https://flask.palletsprojects.com/en/2.1.x/quickstart/

Under: `my-project/python/hello.py`
```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"
```
Then in bash:

```
cd my-project/python
export FLASK_APP=hello
flask run
```
and it should return:

```
 * Serving Flask app 'hello' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
```

Unlike Jekyll, it won't update as you edit, unless you set up a development environment variable:

```
export FLASK_APP=hello
export FLASK_ENV=development
flask run
```

It will update, but you still have to click refresh on the screen.

```
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<h1>Hello, World!</h1>"
```

Now to make the project a package and keep running under the same structure as before, now I use this structure: (which by the way you can output with `tree -a -N -n --charset ascii | pbcopy` on the terminal if you install it with Homebrew with `brew install tree`).

```
my-project
|-- .gitignore
|-- README.md
|-- logs
|   `-- tasklog.md
|-- python
|   |-- ProjectPaths.py
|   |-- __pycache__
|   |-- package
|   |   |-- __init__.py
|   |   |-- __pycache__
|   |   `-- module.py
|   `-- tests
|       |-- 0_test.py
|       `-- __pycache__
|-- requirements.txt
`-- venv
```

`ProjectPaths.py` is just a bunch of methods I like to call to make directories without much hassle.

To run the tests and the files in the package, now the command is like this:

```
cd my-project/python
python -m tests.0_test
```

Notice that it's a `.` instead of a `/` and also there's no `.py`
It should now run and import as if from the parent directory `python`

<a id="setup-git"></a>
## Setup Git

Linux already has git installed, but we can update it and manage it with apt-get.

```
sudo apt-get update
sudo apt-get install git
```

Then setup the configuration. Make an account at [GitHub](https://github.com) to get a username and email associated with Git. Type the settings on the terminal. My settings are like this:

```
git config --global http.proxy http://{PROXY_HOST}:{PORT}
git config --global user.name {YOUR_USERNAME}
git config --global user.email {YOUR_EMAIL}
git config --global color.ui auto
git config --global merge.conflictstyle diff3
git config --global core.editor nano
git config --global core.autocrlf input
git config --global core.fileMode false
git config --global pull.ff only
```

This should make a file `~/.gitconfig` with the following text
```
# ~/.gitconfig

[http]
    proxy = http://{PROXY_HOST}:{PORT}
[user]
    name = YOUR_USERNAME
    email = YOUR_EMAIL
[color]
    ui = auto
[merge]
    conflictstyle = diff3
[core]
    editor = nano
    autocrlf = input
    fileMode = false
[pull]
    ff = only
[alias]
    adog = log --all --decorate --oneline --graph
```

That last one, `git adog` is very useful as I explain in [Check your branches in git log history in a pretty line](#check-your-branches-in-git-log-history-in-a-pretty-line)

<a id="check-your-branches-in-git-log-history-in-a-pretty-line"></a>
### Check your branches in git log history in a pretty line

This makes your history tree pretty and easy to understand inside of the terminal.
I found this in https://stackoverflow.com/a/35075021

```
git log --all --decorate --oneline --graph
```

Not everyone would be doing a git log all the time, but when you need it just remember: 
"A Dog" = git log --all --decorate --oneline --graph

Actually, let's set an alias:

```
git config --global alias.adog "log --all --decorate --oneline --graph"
```

This adds the following to the .gitconfig file:

```
[alias]
        adog = log --all --decorate --oneline --graph
```

And you run it like:

```
git adog
```

<a id="github-markdown-math-expressions-for-readmemd-etc"></a>
### GitHub Markdown math expressions for README.md, etc.

Following this guide, math is different in GitLab markdown than say, GitHub or LaTeX.
However, inside of the delimiters, it renders it using KaTeX, which uses LaTeX math syntax! 

https://docs.gitlab.com/ee/user/markdown.html#math

Inline: 
```
> $a^2 + b^2 = c^2$
```

Renders as: $a^2 + b^2 = c^2$

Block:
```
> $$a^2 + b^2 = c^2$$
```

Renders as:

$$a^2 + b^2 = c^2$$

But it only supports one line of math, so for multiple lines you have to do this:

```
> $$a^2 + b^2 = c^2$$
> <!-- (line break is important) -->
> $$c = \sqrt{ a^2 + b^2 }$$
```

Renders as:

$$a^2 + b^2 = c^2$$

$$c = \sqrt{ a^2 + b^2 }$$

It can even display matrices and the like:

```
> $$
> l_1 = 
> \begin{bmatrix}
>     \begin{bmatrix}
>         x_1 & y_1
>     \end{bmatrix} \\
>     \begin{bmatrix}
>         x_2 & y_2
>     \end{bmatrix} \\
>     ... \\
>     \begin{bmatrix}
>         x_n & y_n
>     \end{bmatrix} \\
> \end{bmatrix}
> $$
```

$$
l_1 = 
\begin{bmatrix}
    \begin{bmatrix}
        x_1 & y_1
    \end{bmatrix} \\
    \begin{bmatrix}
        x_2 & y_2
    \end{bmatrix} \\
    ... \\
    \begin{bmatrix}
        x_n & y_n
    \end{bmatrix} \\
\end{bmatrix}
$$


However, % comments will break the environment.

Math syntax in LaTeX:

https://katex.org/docs/supported.html

<a id="gitlab-markdown-math-expressions-for-readmemd-etc"></a>
### GitLab Markdown math expressions for README.md, etc.

Following this guide, math is different in GitLab markdown than say, GitHub or LaTeX.
However, inside of the delimiters, it renders it using KaTeX, which uses LaTeX math syntax! 

https://docs.gitlab.com/ee/user/markdown.html#math

Inline: 
```
> $`a^2 + b^2 = c^2`$
```

Renders as: $`a^2 + b^2 = c^2`$

Block:
```
> ```math
> a^2 + b^2 = c^2
> ```
```

Renders as:

```math
a^2 + b^2 = c^2
```

But it only supports one line of math, so for multiple lines you have to do this:

```
> ```math
> a^2 + b^2 = c^2
> ```
> ```math
> c = \sqrt{ a^2 + b^2 }
> ```
```

Renders as:

```math
a^2 + b^2 = c^2
```
```math
c = \sqrt{ a^2 + b^2 }
```

It can even display matrices and the like:

```
> ```math
> l_1 = 
> \begin{bmatrix}
>     \begin{bmatrix}
>         x_1 & y_1
>     \end{bmatrix} \\
>     \begin{bmatrix}
>         x_2 & y_2
>     \end{bmatrix} \\
>     ... \\
>     \begin{bmatrix}
>         x_n & y_n
>     \end{bmatrix} \\
> \end{bmatrix}
> ```
```

```math
l_1 = 
\begin{bmatrix}
    \begin{bmatrix}
        x_1 & y_1
    \end{bmatrix} \\
    \begin{bmatrix}
        x_2 & y_2
    \end{bmatrix} \\
    ... \\
    \begin{bmatrix}
        x_n & y_n
    \end{bmatrix} \\
\end{bmatrix}
```

However, % comments will break the environment.

Math syntax in LaTeX:

https://katex.org/docs/supported.html

<a id="install-git-large-file-system"></a>
### Install Git Large File System

This is for files larger than 50 MB to be able to be used in Git. Still, GitLFS has some limitations if you don't buy data packages to increase your usage limit. By default you get 1GB of storage and 1GB of bandwidth (how much you push or pull per month). For 5$USD, you can add a *data pack* that adds 50GB bandwith and 50GB Git LFS storage.

Now we need to install the git-lfs package to use it:

```
sudo apt install git-lfs
```

<a id="make-a-new-git-lfs-repository-from-local"></a>
### Make a new Git (LFS) repository from local

Now that we have Git and Python installed, we can make our first project. I like to leave this part of the tutorial in even if it doesn't classify as a setup because using Git and GitLFS was confusing at first.

First make a repository on GitHub with no .gitignore, no README and no license.
Then, on local terminal, cd to the directory of your project and initialize git
```
cd path/to/your/project
git init
```

If using Git LFS:
```
git lfs install
```
It's supposed to be ready, but first, let's make a few hooks executable
```
chmod +x .git/hooks/*
```

Make a .gitignore depending on which files you don't want in the repository and add it
```
git add .gitignore
```

If using Git LFS, add the tracking settings for this project (For example, heavy csv files in this case)
```
git lfs track "*.csv"
```

And then add them to git
```
git add .gitattributes
```

Commit these changes first
```
git commit -m "First commit, add .gitignore and .gitattributes"
```

Now add all the data from your local repository. `git add .` adds all the files in the folder.
```
git add .
```

Depending on the size of your project, it might be wiser to add it in parts instead of all at once. e.g.
```
git add *.py
git add *.csv
...
```
or
```
git add dir1
git add dir2
...
```

Check if all the paths are added
```
git status
```

Check if all the Git LFS files are tracked correctly
```
git lfs ls-files
```

If so, commit.
```
git commit -m "First data commit"
```

Set the new remote URL from the repository you created on GitHub. It'll appear with a copy button and everything, and end in .git
```
git remote add origin remote_repository_URL_here
```

Verify the new remote URL
```
git remote -v
```

Set upstream and then push only the lfs files to remote
```
git lfs push origin master
```

Afterwards push normally to upload everything
```
git push --set-upstream origin master
```

You only need to write --set-upstream origin master the first time for normal `push`, after this just write push. For git lfs you always have to write it.

<a id="manage-multiple-github-or-gitlab-accounts"></a>
### Manage multiple GitHub or GitLab accounts

Because I want to update my personal code when I find better ways to program at work, I want to push and pull from my personal GitHub account aside from the work GitLab projects. **CAUTION: DON'T UPLOAD COMPANY SECRETS TO YOUR PERSONAL ACCOUNT**

To be able to do this, I followed these guides:<br>
https://blog.gitguardian.com/8-easy-steps-to-set-up-multiple-git-accounts/


https://medium.com/the-andela-way/a-practical-guide-to-managing-multiple-github-accounts-8e7970c8fd46


https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token


1. Generate an SSH key
First, create an SSH key for your personal account:
```
ssh-keygen -t rsa -b 4096 -C "your_personal_email@example.com" -f ~/.ssh/<personal_key> 
```
Then for your work account:
```
ssh-keygen -t rsa -b 4096 -C "your_work_email@company.com" -f ~/.ssh/<work_key> 
```

2. Add a passphrase

Then add a passphrase and press enter, it will ask for it twice. Press enter again.

To update the passphrase for your SSH keys:

```
ssh-keygen -p -f ~/.ssh/<personal_key>
```

You can check your newly created key with:

```
ls -la ~/.ssh
```

which should output <personal_key> and <personal_key>.pub.

Do the same steps for the <work_key>.

3. Tell ssh-agent

The website has an -K tag that works for macOSX and such but we don't need it.

```
eval "$(ssh-agent -s)" && \
ssh-add ~/.ssh/<personal_key> 
ssh-add ~/.ssh/<work_key> 
```

4. Edit your SSH config

```
nano ~/.ssh/config
-----------nano----------
# Work account - default
Host <some_host_name_work>
  HostName <HOST>:<PORT>
  User git
  IdentityFile ~/.ssh/<work_key> 

# Personal account
Host <personal_host_name>
  HostName github.com
  User git
  IdentityFile ~/.ssh/<personal_key>

CTRL+O
CTRL+X
-------------------------
```

5. Copy the SSH public key

```
cat ~/.ssh/<personal_key>.pub | pbcopy
```

Then paste on your respective website settings, such as the GitHub SSH settings page. Title it something you'll know it's your work computer.

Same for your <work_key>

6. Structure your workspace for different profiles

Now, for each key pair (aka profile or account), we will create a .conf file to make sure that your individual repositories have the user settings overridden accordingly.
Let’s suppose your home directory is like that:

```
/myhome/
    |__.gitconfig
    |__work/
    |__personal/
```

We are going to create two overriding .gitconfigs for each dir like this:

```
/myhome/
|__.gitconfig
|__work/
     |_.gitconfig.work
|__personal/
    |_.gitconfig.pers
```

Of course the folder and filenames can be whatever you prefer.

7. Set up your Git configs

In the personal git projects folder, make `.gitconfig.pers`

```
nano ~/personal/.gitconfig.pers
---------------nano-----------------
# ~/personal/.gitconfig.pers
 
[user]
email = your_personal_email@example.com
name = Your Name
 
[github] #or gitlab or whatever
user = "personal-username"
 
[core]
sshCommand = “ssh -i ~/.ssh/<personal_key>”

```


```

# ~/work/.gitconfig.work
 
[user]
email = your_work_email@company.com
name = Your Name
 
[github] #or gitlab or whatever
user = "work_username"

[core]
sshCommand = “ssh -i ~/.ssh/<work_key>”


```

And finally add this to the end of your original main `.gitconfig` file:

```
[includeIf “gitdir:~/personal/”] # include for all .git projects under personal/ 
path = ~/personal/.gitconfig.pers
 
[includeIf “gitdir:~/work/”]
path = ~/work/.gitconfig.work
```

Now finally to confirm if it worked, go to any work project you have and type the following:

```
cd ~/work/work-project
git config user.email
```

It should be your work e-mail.

Now go to a personal project:

```
cd ~/personal/personal-project
git config user.email
```

And it should output your personal e-mail.

8. **To clone new projects**, specially private or protected ones, use the username before the website:

```
git clone https://<username>@github.com/<organization>/<repo>.git
```

If you have a 2 Factor Authentication, the clone might fail on the first try, because you need to generate a Personal Access Token.

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

And then copy and paste that as the password when the terminal asks you for user and password.s

And done! When you push or pull from the personal account you might encounter some 2 factor authorizations at login, but otherwise it's ready to work on both personal and work projects.

<a id="wsl-and-windows-shared-ssh-keys"></a>
#### WSL and Windows shared ssh keys

Do the whole thing on windows first, then follow these steps:

https://devblogs.microsoft.com/commandline/sharing-ssh-keys-between-windows-and-wsl-2/

1. Copy keys to WSL

```
cp -r /mnt/c/Users/<username>/.ssh ~/.ssh
```

2. Update permissions on the keys

```
chmod 600 ~/.ssh/id_rsa
```
Repeat for the other keys as well

3. Install keychain

```
sudo apt install keychain
```

4. Add keychain eval to .bash_profile for every key you have:

```
echo 'eval "$(keychain --eval --agents ssh id_rsa)"' >> ~/.bash_profile
echo 'eval "$(keychain --eval --agents ssh id_rsa_<personal_key>)"' >> ~/.bash_profile
echo 'eval "$(keychain --eval --agents ssh id_rsa_<work_key>)"' >> ~/.bash_profile
```

This will make it so that every time you start up the computer you have to type in the passwords for each of the keys, but they'll remain accessible after that.

5. Setup Git config to match

Copy .gitconfig from the Windows home to the WSL home folder.

Mirror the folder structure and sub-configuration files (e.g. .gitconfig.pers, .gitconfig.work).

Now any new folders created under WSL in these folders will have the same permissions.

However, if you want to access a git repository under the Windows environment through WSL, entering the paths to match will not be enough.

For example, even if you add: 

```
[includeIf “gitdir:/mnt/c/Users/<username>/personal/”] # include for all .git projects under personal/ 
path = /mnt/c/Users/<username>/personal/.gitconfig.pers
```
 Git will return an error like this:

```
fatal: detected dubious ownership in repository at '/mnt/c/Users/......'
To add an exception for this directory, call:

        git config --global --add safe.directory /mnt/c/Users/......
```

This happens because the path to the directory is different than expected, even if it points at the same directory.

https://stackoverflow.com/questions/73485958/how-to-correct-git-reporting-detected-dubious-ownership-in-repository-withou

This link explains that the newer versions of git are stricter with directory ownership.

This can be bypassed by setting this: **(However, only use this if you do not consider yourself at risk)**

```
git config --global safe.directory '*'
```

Now it is accessible from both ends!

If you mirrored the folders as well as added the windows folders, your configuration file should look like this:

```
[includeIf “gitdir:~/personal/”] # include for all .git projects under personal/ 
path = ~/personal/.gitconfig.pers
[includeIf “gitdir:/mnt/c/Users/<username>/personal/”] # include for all .git projects under personal/ 
path = /mnt/c/Users/<username>/personal/.gitconfig.pers
```

<a id="install-and-setup-ruby-bundler-and-jekyll-for-websites"></a>
## Install and setup Ruby, Bundler and Jekyll for websites

I also make websites on my free time, and lots of researchers have their projects on a github pages website. For this, I like to use Jekyll in combination with github pages. First lets install all our dependencies.

```
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Then, we have to add to the $PATH so that ruby gems are found:

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bash_profile
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bash_profile
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bash_profile
source ~/.bash_profile
```

Then install 

```
gem install bundler jekyll jekyll-sitemap
```

Now it's installed! Well, to make a Jekyll Github Page I followed this tutorial, so go ahead and do it:

https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll

Now, once you have your webiste repository and you're ready to test the jekyll serve, do the following:

```
cd (your_repository_here)
bundle init
bundle add jekyll
bundle add jekyll-sitemap
bundle add webrick
```

And then all that's left to do is to serve the website with jekyll!
Also for the sitemaps make sure to check this tutorial:

https://github.com/jekyll/jekyll-sitemap

And add this to your `_config.yml`
```
url: "https://example.com" # the base hostname & protocol for your site
plugins:
  - jekyll-sitemap
```

```
bundle exec jekyll serve
```

If you get an error like:
```
Could not find webrick-1.7.0 in any of the sources
Run `bundle install` to install missing gems.
```

Do as it says and just run:
```
bundle install
```

Now you can work on the website and look at how it changes on screen.

By the way, if you are hosting on GitHub Pages and have a custom domain, you need to add these to the DNS

```
Type    Name    Points to               TTL
a       @       185.199.108.153         600 seconds
a       @       185.199.109.153         600 seconds
a       @       185.199.110.153         600 seconds
a       @       185.199.111.153         600 seconds
cname   www     your-username.github.io 600 seconds   
```

<a id="install-latex-and-latexdiff"></a>
## Install LaTeX and latexdiff

```
sudo apt install texlive-latex-extra
sudo apt-get install latexdiff
```

This installs a few packages along with it, including latexdiff which I use a lot as a PhD student. 

For using these I've made a few helper files, which can be seen here:
https://github.com/elisa-aleman/latex_helpers

Also Install the SublimeText LaTeXTools package.

<a id="shell-scripting-for-convenience"></a>
## Shell Scripting for convenience

When it comes down to it, specially when working with LaTeX or git, you find yourself making the same commands over and over again. That takes time and frustration, so I find that making scripts from time to time saves me a lot of time in the future.


<a id="basic-flag-setup-with-getopts"></a>
### Basic flag setup with getopts

Once in a while those scripts will need some input to be more useful in as many cases as possible instead of a one time thing.

Looking for how to do this I ran across [a simple StackOverflow question](https://stackoverflow.com/questions/14447406/bash-shell-script-check-for-a-flag-and-grab-its-value), which led me to the `getopts` package and its tutorial:

[Getopts manual](https://archive.ph/TRzn4)

This is a working example:

```
while getopts ":a:" opt; do
  case $opt in
    a)
      echo "-a was triggered, Parameter: $OPTARG" >&2
      ;;
    \?)
      echo "Invalid option: -$OPTARG" >&2
      exit 1
      ;;
    :)
      echo "Option -$OPTARG requires an argument." >&2
      exit 1
      ;;
  esac
done

```

<a id="argparse-bash-by-nhoffman"></a>
### Argparse-bash by nhoffman

Now sometimes you'll want to have fancy arguments with both a shortcut name (-) and a long name (--), for example `-a` and `--doall` both pointing to the same command. In that case I recommend using nhoffman's implementation of Python's `argparse` in bash:

[argparse.bash by nhoffman on GitHub](https://github.com/nhoffman/argparse-bash)

<a id="latex-helpers"></a>
### LaTeX helpers

Personally, I find it tiring to try to compile a LaTeX document, only to have to run the bibliography, and then compile the document twice again so all the references are well put where they need to be, rather tiring. Also, I find that the output files are cluttering my space and I only need to see them when I run into certain errors.

Also, for academic papers, I used `latexdiff` commands quite a lot, and while customizable, I noticed I needed a certain configuration for most journals and that was it.

So I made [LaTeX helpers](https://github.com/elisa-aleman/latex_helpers), a couple of bash scripts that make that process faster.

So instead of typing

```
pdflatex paper.tex
bibtex paper
pdflatex paper.tex
pdflatex paper.tex
open paper.tex
rm paper.log paper.out paper.aux paper.... and so on
```

Every. Single. Time. 

I just need to type:
```
./latexcompile.sh paper.tex --view --clean
```

and if I needed to make a latexdiff I just:

```
./my_latexdiff.sh paper_V1-1.tex paper.tex --newversion="2" --compile --view --clean
```

And there it is, a latexdiff PDF right on my screen.

I would also commonly have several documents of different languages, or save my latexdiff command in another script, called `cur_compile_all.sh` or `cur_latexdiff.sh` so I didn't have to remember version numbers and stuff when working across several weeks or months.

Usually with code such as:

```
cd en
./latexcompile.sh paper.tex --view --clean --xelatex
cd ../es
./latexcompile.sh paper.tex --view --clean --xelatex
cd ../jp
./latexcompile.sh paper.tex --view --clean --xelatex
```

And so on, to save time.

<a id="install-pandoc-to-convertexport-markdown-html-latex-word"></a>
## Install Pandoc to convert/export markdown, HTML, LaTeX, Word

I discovered this tool recently when I was asked to share a PDF of my private GitLab MarkDown notes. Of course I wouldn't share the whole repository so that it can be displayed in GitLab for them, so I searched for an alternative. 

It can be installed in Windows, macOS, Linux, ChromeOS, BSD, Docker, ... it's really portable

Pandoc Install:  
https://pandoc.org/installing.html


Pandoc Manual:  
https://pandoc.org/MANUAL.html


Export to PDF syntax
```
pandoc test1.md -s -o test1.pdf
```

Note that it uses LaTeX to convert to PDF, so UTF-8 languages (japanese, etc.) might return errors.

```
pandoc test1.md -s -o test1.pdf --pdf-engine=xelatex
```

But it doesn't load the Font for Japanese... Also, the default margins are way too wide.

So, in the original markdown file preamble we need to add [Variables for LaTeX](https://pandoc.org/MANUAL.html#variables-for-latex):

```
---
title: "Title"
author: "Name"
date: YYYY-MM-DD
<!-- add the following -->
geometry: margin=1.5cm
output: pdf_document
CJKmainfont: IPAMincho
---
```

And voilà, the markdown is now a PDF.

I'm still unsure if it will process the GitHub or GitLab math environments, since the syntax is different.

Upon confirmation with the [User's Guide: Math](https://pandoc.org/MANUAL.html#math) section, it uses the GitHub math syntax.

Inline: `$x=3$`  
Renders as:  
$x=3$


Block:  `$$x=3$$`  
Renders as:  
$$x=3$$


<a id="accessibility-stuff"></a>
## Accessibility Stuff

<a id="accessible-color-palettes-with-paletton"></a>
### Accessible Color Palettes with Paletton 

When designing new things it's important to keep in mind color theory, as well as accessibility for the visually impaired and color blind people, etc. But that's so much time one could spend doing so much else, so here's a tool that can help with that and also visualizing how other people with different ranges of color vision would perceive it. It's called Paletton.

https://paletton.com

<a id="reading-tools-for-neurodivergent-people"></a>
### Reading tools for Neurodivergent people

There was a new tool developed called "Bionic Reading", which bolds the beginnings of words so that our eyes glide over them more easily, basically making a tool for speed reading without having to train specifically for that. Lots of neurodivergent people such as myself (I have ADHD and am autistic), have a hard time following long texts or focusing when there is too much information at the same time (say, with very small line spacing). This new tool has been praised by the ND (neurodivergent) community, since making it available for businesses or companies to use would mean more accessibility in everyday services...  or at least it was until they decided to charge an OUTRAGEOUS amount of money to implement it, making it obviously not attractive for companies to implement and therefore ruining it for everyone.

That is why someone decided to make "Not Bionic Reading" which is, legally speaking, not the same thing as Bionic Reading and therefore can be made available for everyone as Open Source.

Here's the usable link:
https://not-br.neocities.org/

Have fun reading!

<a id="reading-white-pdfs"></a>
### Reading white PDFs

<a id="firefox"></a>
#### Firefox

https://pncnmnp.github.io/blogs/firefox-dark-mode.html

> After hunting on the web for about 30 minutes, I found this thread on Bugzilla. It turns out starting with Firefox 60, extensions are no longer allowed to interact with the native pdf viewer. Determined, I decided to locally modify the CSS rendered by Firefox's PDF viewer. The steps for the same are:
>
> - Open Firefox and press Alt to show the top menu, then click on Help → Troubleshooting Information
> - Click the Open Directory button beside the Profile Directory entry
> - Create a folder named chrome in the directory that opens
> - In the chrome folder, create a CSS file with the name userContent.css
> - Open the userContent.css file and insert -

```
#viewerContainer > #viewer > .page > .canvasWrapper > canvas {
    filter: grayscale(100%);
    filter: invert(100%);
}
```

> - On Firefox's URL bar, type about:config.
> - Search for toolkit.legacyUserProfileCustomizations.stylesheets and set it to true.
> - Restart Firefox and fire up a PDF file to see the change!

<a id="google-chrome"></a>
#### Google Chrome

I found a solution in this post:

https://superuser.com/a/1527417


> The following snippet adds a div overlay to any browser tab currently displaying a PDF document.
> 1. Open up your browser's Dev tools then browser console.
> 2. Paste this JavaScript code in your browser console:

```
const overlay = document.createElement("div");

const css = `
    position: fixed;
    pointer-events: none;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: white;
    mix-blend-mode: difference;
    z-index: 1;
`
overlay.setAttribute("style", css);

document.body.appendChild(overlay);
```

> 3. Hit Enter
>
> Special thanks: https://www.reddit.com/r/chrome/comments/e3txhi/comment/fem1cto

<a id="cuda-and-gpu-settings"></a>
## CUDA and GPU settings

*In Progress*

---

That is all for now. This is my initial setup for the lab environment under a proxy. If I have any projects that need further tinkering, that goes on another repository / tutorial.

