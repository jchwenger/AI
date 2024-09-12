# Setting up a Deep Learning Workstation

## 1 Installation

Download and install [Anaconda](https://www.anaconda.com/) (or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) for less memory use).

Launch Anaconda

Create a new python 3.x environment

```
$ conda create -n AI2024 python
```

Note: "AI2024" is just a name, you can pick whatever you like.

Command line: navigate to directory one level above anaconda3

```
$ conda activate AI2024 # after that your prompt will show the env
(AI2024) $ pip install --upgrade pip
(AI2024) $ pip install tensorflow
(AI2024) $ conda deactivate
```

All the details of the tensorflow installation with GPU can be found
[here](https://www.tensorflow.org/install/pip).

Return to Anaconda environment manager and install matplotlib.

Click on Anaconda Home screen and install Jupiter notebook.

You can also do this on the command line:

```
$ conda activate AI2024
(AI2024) $ conda install matplotlib jupyter
```

Check packages (tensorflow and keras will not show in anaconda env
Manager):

```
$ conda activate AI2024
(AI2024) $ conda list
(AI2024) $ conda deactivate
```

You might need to install pillow, the python imaging library, and scipy, when
we get to chapter 5. If anaconda fails to install pillow from the env manager,
use pip:

```
$ conda activate AI2024
(AI2024) $ conda install -c anaconda pillow
(AI2024) $ conda install -c anaconda scipy
(AI2024) $ conda deactivate
```

## 2 Running

### 2.1 From Anaconda (recommended)

Launch anaconda, select your environment and launch a Jupyter notebook.

### 2.2 Jupyter, from the command line

Navigate to the folder where you keep your project files.

```
$ conda activate AI2024
(AI2024) $ jupyter lab # or jupyter notebook
```

Press ctrl-c twice to close Jupyter and exit the conda environment.

### 2.3 From the command line (not conda)

Suppose tensorflow had been installed with VirtualEnv and pip.

[Here](https://docs.python.org/3/tutorial/venv.html) is the reference for VirtualEnv.

You will see a directory: AI2024 containing bin, include and lib.

```
$ source ~/AI2024/bin/activate
(AI2024) $ python
(AI2024) $ import tensorflow as tf
(AI2024) $ print ("TensorFlow version: " + tf.__version__)
(AI2024) $ # ...your python session...
(AI2024) $ quit()
(AI2024) $ deactivate
$
```

## 3 Editing

### 3.1 Jupyter notebook

Simply open or add a notebook from the home screen.

Add markdown cells and code cells.

Use the text cells to split your code into blocks and provide a
commentary.

The [reference page](https://docs.jupyter.org/en/latest/).

### 3.2 Google Colaboratory (Colab)

You can create and run Jupyter notebooks in Google's online environment.
This allows you to gain free and immediate access to GPU or TPU
acceleration.

Be warned, the service is very popular, which has led Google to restrict
the offer somewhat, preventing people from doing long training jobs on
there (and they introduced paying options).

Tips:

-   Prioritise small experiments, keeping things interactive;
-   If you hit the GPU/TPU limit, create another Google account...
