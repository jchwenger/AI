# Deep Learning Installation Requirements

## 1 Installation

With Python, it is **essential to work with environments**, which work like isolated, separated spaces (if things break or get complicated, you can erase them and start over). Installing/uninstalling dependencies in your OS Python can lead to various kinds of software breaking down, it is highly not recommended.

Here are some [slides on Python Installation & environments](https://docs.google.com/presentation/d/1aTYSvpuYaE_dPIWwT_HEcYve7fsYpDtzix74d5-NvC4/edit?usp=sharing)

A comprehensive software to work with Python (and more) is [Anaconda](https://www.anaconda.com/). This is a GUI software, and will ship with many libraries that are useful in Data Science (it takes quite a bit of memory, however).

For less memory-greedy options, but requiring interacting with the terminal:
- [Miniconda](https://docs.conda.io/en/latest/miniconda.html) (the same as above, just does not install any libraries by default).
- [Miniforge](https://github.com/conda-forge/miniforge), recommended for Mac M1/2/3 users (this currently includes `mamba`, just below).
- [Mamba](https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html), a C++ reimplementation of `conda`, the package manager of Anaconda. Still in development, but resolves issues of speed found in Anaconda.

Launch Anaconda

Create a new python 3.x environment

```bash
$ conda create -n AI2024 python
```

Note: "AI2024" is just a name, you can pick whatever you like.

Command line: navigate to directory one level above anaconda3

```bash
$ conda activate AI2024 # after that your prompt will show the env
(AI2024) $ pip install --upgrade pip
(AI2024) $ pip install tensorflow
(AI2024) $ conda deactivate
```

All the details of the tensorflow installation with GPU can be found
[here](https://www.tensorflow.org/install/pip).

Return to Anaconda environment manager and install `matplotlib`.

Click on Anaconda Home screen and install Jupiter notebook.

You can also do this on the command line:

```bash
$ conda activate AI2024
(AI2024) $ conda install jupyter matplotlib
```

Check packages:

```bash
$ conda activate AI2024
(AI2024) $ conda list
(AI2024) $ conda deactivate
```

You might need to install pillow, the python imaging library, and scipy, when
we get to chapter 5. If anaconda fails to install pillow from the env manager,
use pip:

```bash
$ conda activate AI2024
(AI2024) $ conda install -c anaconda pillow
(AI2024) $ conda install -c anaconda scipy
(AI2024) $ conda deactivate
```

## 2 Running Jupyter

### 2.1 From Anaconda (recommended)

Launch anaconda, select your environment and launch a Jupyter notebook.

### 2.2 Jupyter, from the command line

Navigate to the folder where you keep your project files.

```bash
$ conda activate AI2024
(AI2024) $ jupyter lab
```

Press ctrl-c twice to close Jupyter and exit the conda environment.

### 2.3 From the command line (not conda)

Suppose tensorflow had been installed with VirtualEnv and pip, for instance like:

```bash
python3 -m venv env --prompt "AI2024"
source env/bin/activate
(AI2024) which pip # verify that pip is in located in env
(AI2024) pip install --upgrade pip
(AI2024) pip install tensorflow
```

[Here](https://docs.python.org/3/tutorial/venv.html) is the reference for virtual environments.

You will see a directory: AI2024 containing `bin`, `include` and `lib`.

```bash
$ source env/bin/activate
(AI2024) $ python
(AI2024) $ import tensorflow as tf
(AI2024) $ print ("TensorFlow version: " + tf.__version__)
(AI2024) $ # ...your python session...
(AI2024) $ quit()
(AI2024) $ deactivate
```
