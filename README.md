<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table Of Content

- [Uninstall Anaconda on Mac](#uninstall-anaconda-on-mac)
- [Install Anaconda on Mac](#install-anaconda-on-mac)
- [Conda](#conda)
  - [Env Shorthand Config](#env-shorthand-config)
  - [Create an env in current foler](#create-an-env-in-current-foler)
  - [Activate current folder's env](#activate-current-folders-env)
  - [Export current folder's env as yml file](#export-current-folders-env-as-yml-file)
- [Install, Update, Remove and List Packages](#install-update-remove-and-list-packages)
  - [Deactivate current folder's env](#deactivate-current-folders-env)
  - [Config env from `yml file`](#config-env-from-yml-file)
  - [Baby Usage](#baby-usage)

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

### Install, Update, Remove and List Packages
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
```sh
conda create --name conda-env python
conda create --name conda-env python=3.7
conda create --name conda-env python=3.7 numpy requests
conda activate conda-env
conda deactivate
conda env list
```

