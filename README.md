

### Cryo-EM

* Cryogenic electron tomography is an imaging technique used to visualize 3D structures of biological samples.
* A tomogram is a detailed 3D image of a cell and contains many copies of the same molecule scattered throughout the cellular environment.

### Possible implementations using CUDA

### Subtomogram Extraction

* Cuts tomograms into smaller boxes (subtomograms), each centered on one exact molecule.

### Subtomogram Averaging

* After subtomograms are extracted, the next step is to computationally rotate and shift each subtomogram so that all molecules are aligned in the same direction. (This is too complex for me; there are multi-million-line programs built on this.)
* After alignment, subtomograms are averaged together.
* The program should stack each subtomogram and average density values at every point in the 3D volume.
* Remember, each molecule is in the same position in every subtomogram; features such as HA (hemagglutinin) or NA (neuraminidase) proteins (e.g., virus spikes) will be in the same place. Thus, when averaged, these features reinforce each other.
* Through averaging, noise (electrons, instrument noise) is represented as dark or light pixels; when averaging thousands of these values, they may cancel into the gray background.
* Output should be a 3D structure of the molecule.

### CUDA

* Grids, blocks, threads
* Memory hierarchy
* Assign one CUDA thread to each particle coordinate.
* When averaging, compute the final value for each voxel (x, y, z) by processing thousands of subtomograms in parallel.

**Main fixes:** “thorughout → throughout,” “Possile → Possible,” “roate → rotate,” “average → averaged (when used as verb in past),” “protiens → proteins,” “are represents → is represented,” “ex → e.g.,” plus minor punctuation/wording for clarity.
