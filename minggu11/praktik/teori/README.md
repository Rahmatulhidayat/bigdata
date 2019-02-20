
# Clone Repo Pandas Cookbook

Doto Baliga@Arumbay MINGW64 /c
$ git clone https://github.com/PacktPublishing/Pandas-Cookbook.git
Cloning into 'Pandas-Cookbook'...
remote: Enumerating objects: 100, done.
remote: Total 100 (delta 0), reused 0 (delta 0), pack-reused 100
Receiving objects: 100% (100/100), 33.40 MiB | 460.00 KiB/s, done.
Resolving deltas: 100% (19/19), done.
Checking out files: 100% (70/70), done.


# Copy notebook Jupyter untuk bab 3

Copy -->> "Chapter 03 Beginning Data Analysis.ipynb" 
kemudian pindahkan ke direktori bigdata/minggu - 11/praktik

jalankan notebook :

(yakup_of_my_env) C:\bigdata\Minggu - 11\Praktik>jupyter notebook
[I 03:09:40.165 NotebookApp] JupyterLab extension loaded from C:\Users\Doto Baliga\Miniconda3\envs\yakup_of_my_env\lib\site-packages\jupyterlab
[I 03:09:40.166 NotebookApp] JupyterLab application directory is C:\Users\Doto Baliga\Miniconda3\envs\yakup_of_my_env\share\jupyter\lab
[I 03:09:40.180 NotebookApp] Serving notebooks from local directory: C:\bigdata\Minggu - 11\Praktik
[I 03:09:40.180 NotebookApp] The Jupyter Notebook is running at:
[I 03:09:40.180 NotebookApp] http://localhost:8888/?token=39fc4b16c3c61236b7db7c51287eda20bb9273bfae734a29
[I 03:09:40.181 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 03:09:40.336 NotebookApp]

# Kerjakan berbagai source code : 

import pandas as pd
import numpy as np
from IPython.display import display
pd.options.display.max_columns = 50


