## Run Python Meep in the Google Colab

Attach below code to the top of your notebook. 

```python
!pip install -q condacolab
import condacolab
condacolab.install()
!which conda

!conda create -n pmp -c conda-forge pymeep=*=mpi_mpich_* -y

!conda run -n pmp pip install autograd
!conda run -n pmp pip install nlopt
!conda run -n pmp pip install "numpy<2" --no-deps --force-reinstall

!conda run -n pmp pip install ipykernel

!conda run -n pmp python -m ipykernel install --user --name pmp --display-name "Python (pmp)"
```

``` python
%%bash
cat > script.py <<'EOF'
#!/usr/bin/env python
"""
Script for running Meep simulations with additional custom code.
Insert your custom Meep simulation code in the designated section below.
"""

import meep as mp
import meep.adjoint as mpa
import numpy as np
from autograd import numpy as npa
import nlopt
from matplotlib import pyplot as plt

# Print version information for verification
print("meep version:", mp.__version__)
print("numpy version:", np.__version__)

# ============================================================
# Insert your custom Meep code below
# ============================================================
# ---- Begin Meep code ----
#
# Add your custom Meep simulation code here.
#
# ---- End Meep code ----
# ============================================================
EOF

# Optional: display the contents of the generated script file
conda run -n pmp python -u script.py | tee output.txt
```



<details>
<summary>Previous version - Before March, 2025</summary>
<div markdown="1">

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

</div>
</details>


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

There may be compatibility issues between Meep and the current version of NumPy. After installation, please downgrade NumPy to a version below 2.0.

##  How to install C++ Meep easily (Ubuntu)

I don't see many people using C++ MEEP these days, so I'm expecting they'll struggle with the more involved setup when compared to Python.
I've set up a docker environment with all of the packages need to run C++ MEEP. 

There is no need for extra installation; simply download the updated docker image from docker hub.

Link: [Docker Image for Meep C++](https://hub.docker.com/r/latteishorse/eidl)


---
The Meep Docs installation codes are fine but a bit complicated for beginners. 
[Meep Docs](https://meep.readthedocs.io/en/latest/Installation/)

So, I shared the code because I want researchers who use Meep to be able to use it easily.
