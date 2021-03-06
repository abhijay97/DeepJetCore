**For the bleeding-edge version of DeepJetCore check out the [updated installation](https://github.com/SwapneelM/DeepJetCore/blob/python-package/PYPKG.md)**

*For details, refer to the [presentations for DeepJet](https://drive.google.com/drive/folders/1l8Hu34hMYNc-YdgpCoAuqMzQ-qa5eCSJ?usp=sharing)*
*Check out the [DeepJetCore wiki](https://github.com/DL4Jets/DeepJetCore/wiki) for an introduction to the package.*

DeepJetCore: Package for training and evaluation of deep neural networks for HEP
===============================================================================

This package provides the basic functions for out-of-memory training, resampling, and basic evaluation. 
The actual training data structures and DNN models must be defined in an additional user package. The data structures (defining the structure of the training data as numpy arrays), must inherit from the TrainData class, and must be reachable in the PYTHONPATH as "from datastructure import * " .
A script to set it up will be provided eventually. For reference, please see: 
https://github.com/DL4Jets/DeepJet/tree/master/modules


Setup python packages (CERN)
==========
It is essential to perform all these steps on lxplus7. Simple ssh to 'lxplus7' instead of 'lxplus'

Pre-Installation: Anaconda setup (only once)
Download miniconda3
```
cd <afs work directory: you need some disk space for this!>
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
Please follow the installation process. If you don't know what an option does, please answer 'yes'.
After installation, you have to log out and log in again for changes to take effect.
If you don't use bash, you might have to add the conda path to your .rc file
```
export PATH="<your miniconda directory>/miniconda3/bin:$PATH"
```
This has to be only done once.


Installation:

```
mkdir <your working dir>
cd <your working dir>
git clone https://github.com/DL4Jets/DeepJetCore
cd DeepJetCore/environment
./setup_djcenv.sh #opt: gpu
```
For enabling gpu support add 'gpu' (without quotes) as an additional option to the last command.
This will take a while. Please log out and in again once the installation is finised.

Compiling DeepJetCore
===========

When the installation was successful, the DeepJetCore tools need to be compiled.
```
cd <your working dir>
cd DeepJetCore
source env.sh
cd compiled
make -j4
```

After successfully compiling the tools, log out and in again.
The environment is set up.


Usage
==========

DeepJetCore is only a set of tools and wrappers and does not provide ready-to-use training code.
However, an example package containing more specific code examples (referred to as 'subpackage' in the following) can be created once everything is compiled using the script ``createSubpackage.py``.
This subpackage will include an example dataset which gets generated on the fly (size about 150 MB).
More instructions are printed by the script creating the subpackage.
This subpackage can serve as a reference for own projects.



