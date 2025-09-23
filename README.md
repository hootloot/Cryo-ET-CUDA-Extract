Cryo EM:  
Cryogenic electron tomography is an imaging technique used to visualize 3D structures of biological samples. A tomogram is a detailed 3D image of a cell, and contains many copies of the same molecule scattered thorughout the cellular environment.  
Possile implementations using CUDA:  
Subtomogram Extraction:  
- Cuts tomograms into smaller boxes into a subtomogram, centered on one exact molecule.

Subtomogram Averaging:
- After subtomograms are extracted, the next step is to computationally roate and shift each subtomogram so that all molecules are aligned in the same direction. (This is too complex for me, there are multi-million programs built off this)
- However, after alignment, subtomograms have to be average together.
- Where, the program should stack each subtomogram up and average density values at every single point in the 3D volume
- Remember, each molecule is in the same position in every subtomogram, features such as HA (hemagglutinin) or NA (neuraminidase) protiens (ex virus spikes) are going to be in the same place. Thus, when averaged, these features should reinforce each other.
- Through averaging, noise (electrons, instrument noise) are represents as dark or light pixels. When averaging thousands of these values, they may cancel out into the gray background.
- Output should be a 3D structure of the molecule. 

CUDA:
- Grids, blocks, threads
- Memory Hierarchy
- Assign one CUDA thread to each particle coordinate
- When averaging, we calculate the final value for each pixel by averaging a thread for each (x, y, z) position through thousands of subtomograms in parallel. 
