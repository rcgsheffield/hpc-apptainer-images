# hpc-apptainer-images
Apptainer/Singularity image definitions for use on UoS HPC systems.

Image definitions are organised according to rough type then easybuild/Lmod categorisation, e.g., the definition for an ANSYS 2025R1 container lives in `software/ANSYS/2025R1/ANSYS-2025R1-Container.def`.
Any files related to a piece of software, such as an easyconfig or module/lua file should be located alongside the container definition.
Any general shared files, such as an easyblock, should be in `shared/`.
