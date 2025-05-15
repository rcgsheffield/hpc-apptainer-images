# hpc-apptainer-images
Apptainer/Singularity image definitions for use on UoS HPC systems.

Image definitions for software are organised according easybuild/Lmod categorisation, e.g., the definition for an ANSYS 2025R1 container lives in `software/ANSYS/2025R1/ANSYS-2025R1-Container.def`.
Any files related to a specific piece of software, such as an easyconfig or module/lua file should be located alongside the container definition, e.g., `software/ANSYS/2025R1/ANSYS-2025R1-Container.eb`.
Shared files, such as easyblocks, should be located in `shared/`.
