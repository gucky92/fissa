FISSA
=====

FISSA (Fast Image Source Separation Analysis) is a Python library for extracting
somatic signals from 2-photon calcium imaging data.
It requires images in tiff format as well as predefined ROIs around somas. 

FISSA offers the use of ICA and several NMF algorithms to do so, as well as 
ROI manipulation routines for generating neuropil ROIs. 

Currently, FISSA is only available for Python 2.7, and has been tested on
Ubuntu 15.04 and on Windows 7 with the
[WinPython 2.7.10.3](http://sourceforge.net/projects/winpython/files/WinPython_2.7/2.7.10.3/)
distribution.


Installation
------------

### Installation on Linux

You can download the package source from GitHub, and then install FISSA and its 
dependencies as follows:
```unix
git clone https://github.com/rochefort-lab/fissa.git
pip install -r fissa/require_first.txt
pip install -r fissa/requirements.txt
pip install -e fissa
```

To generate the plots in the iPython Notebooks, you will also need to install
the optional dependencies:
```unix
pip install -r fissa/optional.txt
```

If you wish, you can install FISSA and its dependencies into a virtual
environment.

#### Notes on dependencies of dependencies

* scipy requires a fortran compiler and LAPACK, which on Debian/Ubuntu can be
  installed with `sudo apt-get install gfortran libopenblas-dev`.

* shapely requires GEOS, which on Debian/Ubuntu can be installed with
  `sudo apt-get install libgeos-dev`.

* If you want to use version 3.0.0 of Pillow, you will need to install a JPEG
  library with `sudo apt-get install libjpeg-dev`. Alternatively, you can
  install version 2.9.0 of Pillow, which we also support.


### Installation on Windows

These instructions for installing FISSA on Windows assume you are using
WinPython for your Python environment, and has been tested with
WinPython 2.7.10.3, available from
<http://sourceforge.net/projects/winpython/files/WinPython_2.7/2.7.10.3/>.

From the `WinPython Command Prompt.exe`, which can be found in the WinPython
installation folder, you can download the FISSA source from GitHub and install
most of its dependencies as follows:
```unix
git clone https://github.com/rochefort-lab/fissa.git
pip install -r fissa/require_first.txt
pip install -r fissa/requirements_windows.txt
pip install -r fissa/optional.txt
```

If you don't have Git installed globally, you can't do all these steps in the
WinPython command prompt.
You can instead download a zipped copy of FISSA from GitHub and skip the first
step.
However, in this case you will also get an error when pip tries to install
nimfa, which can be resolved as described below.

Next, you need to download a windows specific version of shapely from
<http://www.lfd.uci.edu/~gohlke/pythonlibs/#shapely>.
Browse to where you downloaded the wheel (which should be named something like
`Shapely‑1.5.13‑cp27‑none‑win_amd64.whl`) and pip install it using the WinPython
command prompt:
```unix
pip install filename
```

If nimfa did not install with the first step above, you can download 
the nimfa zip from <https://github.com/marinkaz/nimfa/archive/v1.2.1.zip>.

Unzip the contained folder, and in folder above it do the following in 
the WinPython command prompt.
```unix
pip install -e nimfa-1.2.1
```

Finally, if everything above worked well, you can install FISSA as 
follows (from the folder above fissa).
```unix
pip install -e fissa
```


Folder Structure
----------------

### doc
Contains example code. You can load the notebooks as .ipynb directly in GitHub, 
or on your system if you know how to use ipython notebooks 
(http://ipython.org/ipython-doc/stable/notebook/index.html). 
You can also read the .html pages instead. 

### exampleData
Contains example data. It has two zips with region of interests from ImageJ. 
It also contains three tiff stacks, which have been downsampled and cropped 
from full data from the Rochefort lab. 

### fissa
Contains the toolbox. See the tutorial in doc for how to use it, and the
comments in the different modules inside FISSA.


Citing FISSA
------------

If you use FISSA for your research, please cite the following paper 
in any resulting publications:

_Paper in preparation_


License
-------

Unless otherwise stated in individual files, all code is
Copyright (c) 2015, Sander Keemink, Scott Lowe, and Nathalie Rochefort.
All rights reserved.

This program is currently closed source; you can not redistribute it unless
under the express permission of one of the copyright holders.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
POSSIBILITY OF SUCH DAMAGE.
