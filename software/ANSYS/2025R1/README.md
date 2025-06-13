### Building using Apptainer

1. Update the `ISO_DIR` variable in the definition file to point to the directory where the nine ANSYS ISO images are located. If the ISO files are already extracted, skip this step.
2. Update the `OUT_DIR` variable in the definition file to a temporary location where the ISO files can be/have been extracted to.
1. Build the image by running `apptainer build --fakeroot ANSYS-2025R1-Fluent-Container.sif ANSYS-2025R1-Fluent-Container.def`

To start Fluent run

```bash
apptainer exec --env ANSYSLMD_LICENSE_FILE=port@host ANSYS-2025R1-Fluent-Container.sif fluent
```

### Building using EasyBuild

1. Put the nine ANSYS ISO files and `ANSYS-2025R1-Fluent-Container.def` into the EasyBuild sourcepath.
2. Update `ANSYS-2025R1-Fluent-Container.eb` to specify the license server in the `local_license_server` variable.
3. Make sure `apptainer` is available. There may be some fiddling of `osdependencies` or `depends_on` required.
4. Run `eb ANSYS-2025R1-Fluent-Container.eb` to install the image

To start Fluent run

```bash
module load ANSYS/2025R1-Fluent-Container
fluent
```
