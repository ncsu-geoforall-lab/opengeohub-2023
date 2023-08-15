# OpenGeoHub 2023: Parallelization of geoprocessing workflows in GRASS GIS and Python

This repository contains materials in the form of Jupyter notebooks for OpenGeoHub Summer School 2023.

## Abstract
High-resolution, continental-scale modeling enabled by modern, massive datasets, requires development of scalable geoprocessing workflows. To enable participants to effectively use available computational resources (laptop, desktop, institutional HPC), we will introduce basic parallelization concepts such as parallelization efficiency and scaling. We will explain various approaches to parallelization in GRASS GIS, an open source geoprocessing engine, that rely on OpenMP, Python and Bash.
In the hands-on part, participants will speed up an urban growth model by parallelizing different parts of this complex geoprocessing workflow using techniques that are easily applicable to a wide range of analyses and computational resources. The workshop will be running in a Jupyter Notebook environment using GRASS GIS Python API to run GRASS tools and visualize results of the analysis in a reproducible way.
Participants will be able to either run the workshop on their laptops (see instructions) or in a cloud environment (using WholeTale, no installation required).

## Agenda
Session 1: [Lecture](https://docs.google.com/presentation/d/1rNaDijIBTiLMaD3s33QQPJOP6ntXkUfdvhwuW81f2hM/) + Intro to parallelization with GRASS GIS ([intro_to_GRASS_parallelization.ipynb](intro_to_GRASS_parallelization.ipynb))

Session 2: Parallelization Case Study: Urban Growth Modeling ([FUTURES_case_study.ipynb](FUTURES_case_study.ipynb))

## How to run this workshop

The workshop is designed for linux environment that is typically used for computing in a cloud and on high-performance computing clusters. There are multiple options to run this hands-on workshop.
* Local installation (prepare before the workshop)
* OSGeoLive Virtual Machine (prepare before the workshop)
* Cloud environment (WholeTale or Google Colab)

### Locally
While most of the workshop material can be run on all platforms, some parts require tools that are typically harder to set up on Windows. Therefore we recommend to run this workshop locally in linux/unix environments.

#### Required software
* GRASS GIS >= v8.2.0
   * addons r.futures and r.mapcalc.tiled
* Python >= 3.7 with the following packages:
  * jupyterlab, scipy, pandas, tqdm, folium
* GNU Parallel
* htop (optional)

Once the software is installed, run:
```
git clone https://github.com/ncsu-geoforall-lab/opengeohub-2023
cd opengeohub-2023
jupyter lab
```
#### Notes for Linux 
Ubuntu users: use ubuntugis-unstable PPA to get latest GRASS GIS:
```
sudo add-apt-repository ppa:ubuntugis/ubuntugis-unstable
sudo apt update
sudo apt install grass grass-dev
```

Depending on GRASS version, installing addons may require subversion package. Addons can be installed with:
```
grass --tmp-location XY --exec g.extension r.futures
grass --tmp-location XY --exec g.extension r.mapcalc.tiled
```

#### Notes for MacOSX:
See GRASS GIS [download instructions](https://grass.osgeo.org/download/mac/)


### OSGeoLive Virtual Machine
[OSGeoLive](http://live.osgeo.org/en/index.html) allows you to try a wide variety of other open source geospatial software which you may find useful during the summer school. To set the VM up please follow [these instructions](http://live.osgeo.org/en/quickstart/virtualization_quickstart.html). _Note that setting up OSGeoLive requires to download a large file, which can take a while depending on your connection, so plan accordingly._
When setting up the VM, you need to specify resources the VM can use, please use at least 4 cpus, and generally, more resources will result in better user experience.

Once OSGeoLive is setup, please do these additional steps to get ready for the workshop:
```
# install additional packages
sudo apt -y install subversion parallel python-is-python3
# install addons
grass --tmp-location XY --exec g.extension r.futures
grass --tmp-location XY --exec g.extension r.mapcalc.tiled
# download workshop material
git clone https://github.com/ncsu-geoforall-lab/opengeohub-2023.git
cd opengeohub-2023
# open the intro notebook
jupyter notebook intro_to_GRASS_parallelization.ipynb
```

### Running in a cloud environment
The workshop can be run online in [WholeTale](https://wholetale.org/) and [Google Colab](https://colab.google/). This is a convenient way, since no installation is needed, however, there are resource limitations, e.g., Colab will give you only 2 cpus.

#### WholeTale
WholeTale is a scalable, open source, web-based platform for reproducible research.

1. Go to https://dashboard.wholetale.org/run/64c96871e6fabc2991d17f94
2. Log in (there are different options)
3. Run Tale (blue button at the top right)
4. Confirm Copy and Run Tale
5. If it keeps showing Importing... try to reload
6. Run Tale

#### Google Colab

In Colab:
1. File-> Open notebook
2. Select Github
3. Paste https://github.com/ncsu-geoforall-lab/opengeohub-2023/blob/main/colab_notebook.ipynb

In Google Colab we don't have pre-installed the software needed, so go ahead and execute the first part to install it. Also, in order to avoid repeating the installation, we merged both notebooks into one.
