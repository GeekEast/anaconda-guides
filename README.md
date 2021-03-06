<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table Of Content

- [Uninstall Anaconda on Mac](#uninstall-anaconda-on-mac)
- [Install Anaconda on Mac](#install-anaconda-on-mac)
- [Conda](#conda)
  - [Env Shorthand Config](#env-shorthand-config)
  - [Set no base env by default](#set-no-base-env-by-default)
  - [Create an env in current foler](#create-an-env-in-current-foler)
  - [Activate current folder's env](#activate-current-folders-env)
  - [Export current folder's env as yml file](#export-current-folders-env-as-yml-file)
  - [Install, Update, Remove and List Packages](#install-update-remove-and-list-packages)
  - [Deactivate current folder's env](#deactivate-current-folders-env)
  - [Config env from `yml file`](#config-env-from-yml-file)
  - [Baby Usage](#baby-usage)
- [Anaconda](#anaconda)
- [Create Remote Jupyter Notebook on Server](#create-remote-jupyter-notebook-on-server)
  - [Generate config](#generate-config)
  - [Modify config](#modify-config)
  - [Launch and enjoy](#launch-and-enjoy)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### [Uninstall Anaconda on Mac](https://www.jianshu.com/p/8747a347ea8b)
```sh
# Step 1 anaconda clean
conda install anaconda-clean && anaconda-clean

# Step 2 clean files
rm -rf ~/.anaconda_backup && rm /Applications/Anaconda-Navigator.app && rm -rf ~/anaconda
rm -rf ~/.condarc ~/.conda ~/.continuum

# Step 3 remove anaconda from path
code ~/.bash_profile # remove anything related to anaconda, conda then save
source ~/.bash_profile
```

### [Install Anaconda on Mac](https://docs.anaconda.com/anaconda/install/mac-os/)
- [Anaconda MacOS Installer](https://www.anaconda.com/distribution/#download-section)
  - Download 64-Bit Command Line Installer
```sh
bash <64-Bit Command Line Installer>
```

### [Conda](https://towardsdatascience.com/a-guide-to-conda-environments-bc6180fc533)
#### Env Shorthand Config
```sh
conda config --set env_prompt '({name})'
```

#### Set no base env by default
```sh
conda config --set auto_activate_base False
```

#### Create an env in current foler
```sh
conda create -p ./conda-env anaconda # create anaconda  env
conda create -p ./conda-env python=3.7 # create python 3.7 env
conda create -p ./conda-env anaconda python=3.7 # create anaconda with python 3.7
```


#### Activate current folder's env
```sh
conda activate ./conda-env
```

#### Export current folder's env as yml file
```sh
conda env export > environment.yml
```

#### Install, Update, Remove and List Packages
```sh
conda install pandas
conda install --channel conda-forge <package_name> # from sepcific channel
conda update pandas
conda remove pandas
conda list
```

#### Deactivate current folder's env
```sh
conda deactivate
```

#### Config env from `yml file`
```sh
conda env create -f environment.yml
```


#### Baby Usage
- create native python
```sh
conda create --name conda-env python
conda create --name conda-env python=3.7
conda create --name conda-env python=3.7 numpy requests
```
- create anaconda env
```sh
# create an env called conda-env based on anaconda and python3.7
conda create --name conda-env anaconda python=3.7
# list all conda envs
conda env list
# activate conda-env env
conda activate conda-env
# install pandas in current env
conda install pandas
# update pandas in current env
conda update pandas
# remove pandas in current env
conda remove pandas
# list all packages in current env
conda list
# quit current env
conda deactivate
```

### Anaconda
- Add `jupyter notebook` to path in Ubuntu
```sh
export PATH=~/anaconda3/bin:$PATH
```

### Create Remote Jupyter Notebook on Server
#### Generate config
```sh
jupyter notebook --generate-config
nano ~/.jupyter/jupyter_notebook_config.py
```
#### Modify config
```python
# more than below
c.NotebookApp.open_browser = False
c.NotebookApp.ip = '0.0.0.0'
c.NotebookApp.password = '<Your_Password>'
c.NotebookApp.token = '' # don't require
```
#### Launch and enjoy
```sh
nohup jupyter notebook
```

### Examples
#### Install spacy in conda-env
```sh
conda activate ./conda-env
pip install spacy # sometimes use pip
python -m spacy download en
```

### References
- [5 Minute Jupyter Notebook Server](https://lerner.co.il/2017/02/01/five-minute-guide-setting-jupyter-notebook-server/)
- [How to Install, Run, and Connect to Jupyter Notebook on a Remote Server](https://www.digitalocean.com/community/tutorials/how-to-install-run-connect-to-jupyter-notebook-on-remote-server)
