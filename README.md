## Run Python Meep in the Google Colab

Attach below code to the top of your notebook. 

```python
# install conda
!pip install -q condacolab
import condacolab
condacolab.install()
!which conda

# install meep (python)
!conda install -c conda-forge pymeep 

## Parallel Meep (MPI version)
!conda create -n pmp -c conda-forge pymeep=*=mpi_mpich_*
!conda activate pmp

# Install Additional Packages just in case
!pip install nlopt
```

Done.
Enjoy !


---

## How to install Python Meep locally (Ubuntu)

``` python

# install appropriate version of conda
# after installing conda, you need to restart the terminal

conda install -c conda-forge pymeep 

## Parallel Meep (MPI version)
conda create -n pmp -c conda-forge pymeep=*=mpi_mpich_*
conda activate pmp
```

---

##  How to install C++ Meep easily (Ubuntu)

I don't see many people using C++ MEEP these days, so I'm expecting they'll struggle with the more involved setup when compared to Python.
I've set up a docker environment with all of the packages need to run C++ MEEP. 

There is no need for extra installation; simply download the updated docker image from docker hub.

Link: [Docker Image for Meep C++](https://hub.docker.com/r/latteishorse/eidl)


---
The Meep Docs installation codes are fine but a bit complicated for beginners. 
[Meep Docs](https://meep.readthedocs.io/en/latest/Installation/)

So, I shared the code because I want researchers who use Meep to be able to use it easily.
