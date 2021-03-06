# Overview of the NACA 0012-34 basic simulation case setup

---

The basic simulation setup of NACA 0012-34 airfoil consists of  **3 main directories**:
- _0_ directory
- _constant_ directory
- _system_ directory

In addition to these main directories the setup also contains 2 script files namely **Allrun** & **Allclean** and 1 **readme.md** file respectively.

---

### Let us start the listing of each directory and its subdirectories also other data files along with their description.

_0_ directory: This directory is nothing but the time directory folder. The input data conditions and boundary conditions in OpenFOAM are given in tensor fields which are read from and write into the time directories. Also we usually start our simulation at (t = 0). OpenFOAM  writes the field data using keyword entries such as dimensions, internalField, boundaryField. 
The data files included in the _0_ directory can be described as follows:
- **T** : Temperature (scalar) field file with uniform internalField.
- **U** : Velocity (vector) field file.
- **alphat** : Turbulent thermal diffusivity/conductivity for enthalpy equation (scalar) field.
- **k** : Turbulent kinetic energy (scalar) field.
- **omega** : Turbulence specific dissipation rate (scalar) field.
- **nut** : Turbulent Viscosity (scalar) field , Type: **nutkWallFunction**.
- **p** : Static pressure (scalar) field.


---

_constant_ directory: This directory contains full description of the files specifying physical properties for the application concerned, e.g. **thermophysicalProperties** and **turbulenceProperties**. 
The data files included in the _constant_ directory can be described as follows:

_triSurface_ subdirectory: It contains **NACA 0012-34.stl** file. The triSurface (triangulated surface) directory contains only the airfoil geometry based on which the mesh is generated in a later step. The actual mesh is stored in constant/polyMesh/.

1. **thermophysicalProperties**: The _thermophysicalProperties_ dictionary can be read by any solver that uses the thermophysical model library. A thermophysical model is constructed in OpenFOAM as a pressure-temperature system from which other properties are computed. There is one compulsory dictionary entry called _thermoType_ which specifies the complete thermophysical model that is used in the simulation. The thermophysical modelling starts with a layer that defines the basic equation of state and then adds further layers for the thermodynamic, transport and mixture modelling. 
- **thermoModel**: hePsiThermo - General thermophysical model calculation based on enthalpy (h)  or internal energy (e)  and compressibility.
- **mixture**: pureMixture - General thermophysical model calculation for passive gas mixtures.
- **transport**: constTransport - Constant transport properties.
- **thermo**: hConstThermo - Constant specific heat model with evaluation of enthalpy (h).
- **equationOfState**: perfectGas - Perfect gas equation of state.
- **specie**: containing number of moles, nMoles, of the specie, and molecular weight, molWeight in units of (g/mol).





2. **turbulenceProperties**: The _turbulenceProperties_ dictionary can be read by any solver that includes turbulence modelling. Within this file the inclusion of _simulationType_ keyword is there which controls the type of turbulence modelling to be used. It can be:
- **laminar**: Uses no turbulence models. 
- **RAS**: Uses Reynolds-averaged stress (RAS) modelling. 
- **LES**: Uses large-eddy simulation (LES) or detached-eddy simulation (DES) modelling.
In our setup we have chosen **kOmegaSST RAS model**.


---


_system_ directory: This directory is utilized for setting parameters associated with the solution procedure itself. Every system directory will be having **atleast 3 data files**:

1. **controlDict**: Here the run control parameters are set including start time = 0, end time = 0.15, time step = 5e-7 and parameters for data output.

2. **fvSchemes**: The discretisation schemes used in the solution may be selected at run-time. Here schemes like ddtSchemes,gradSchemes,divSchemes,laplacianSchemes,interpolationSchemes,snGradSchemes and wallDist are specififed.

3. **fvSolution**: The equation solvers, tolerances and other algorithm controls are set for the run.


In addition to these 3 main data files, _system_directory also contain some other important data files which are given as follows:



- **FOMachNo**: The _MachNo_ function object computes the Mach number as a volScalarField.

- **FOyPlus**: The _yPlus_ function object computes the near wall y^+1 for turbulence models.

- **blockMeshDict**: This data file is utilized for _blockMesh_ which is one of the most basic mesh generators in OpenFOAM. It relies on a single dictionary file _blockMeshDict_. As the name implies, blockMesh helps the user build the mesh with blocks. 

- **createPatchDict**: This data file is utilized for _createPatch_, a Utility to create patches out of selected boundary faces. Faces come either from existing patches or from a faceSet. 
   1. It Creates new patches (from selected boundary faces)
   2. Synchronise faces on coupled patches 
   3. Synchronises points on coupled boundaries also remove patches with 0 faces in them.

- **decomposeParDict**: When running a simulation in parallel, the geometry must first be decomposed (segmented) into individual geometries for each MPI process. These separate geometries are connected together with special processor boundary patches. Here we are using the _decomposePar_ utility which is a commonly used method to decompose domains and subsequently distribute the fields.

- **extrudeMeshDict**: _snappyHexMesh_ always generates 3D meshes (that's just how it is programmed), but we need a 2D mesh. The application extrudeMesh takes the lower and upper patches of the 3D mesh and extrudes a single cell layer (in our case). The specific extrution settings are defined in the extrudeMeshDict.

- **fvOptions**: This data file represents _fvOptions_ functionality in OpenFOAM is flexible framework to add various source terms to the governing equations without the need to rewrite the original source code. Many OpenFOAM applications contain equation systems that can be manipulated at run time via user-specified finite volume options, given by the shorthand _fvOptions_. These provide, e.g. additional source/sink terms or enforce constraints.


- **snappyHexMeshDict**: The actual mesh generator is called _snappyHexMesh_. The snappyHexMeshDict defines meshing options and parameters for snappyHexMesh.

- **solverInfo**: This file is utilized for The _solverInfo_ function object which reports the solver performance information for a list of fields such as residual fields, solver type, initial residual, final residual, number of solver iterations, convergence flag.


---


**Allrun**: It is a script file. This script file includes all the commands necessary for our case in the sequential order. This helps in the efficient testing of the code.

**Allclean**: It is a script file. It cleans the test case directory by deleting all files generated by meshing.

**README.md**: It is a readme file having Markdown format with plain-text-formatting syntax created for giving description about geometry generation of NACA 0012-34 airfoil. It also contains elaborative description of simulation conditions and some useful expressions which are necessary to carry out the compressible simulation of NACA 0012-34 airfoil.

---


 













































