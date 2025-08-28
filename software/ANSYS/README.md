### Building using Apptainer

1. Update the `ISO_DIR` variable in the definition file to point to the directory where the nine ANSYS ISO images are located. If the ISO files are already extracted, skip this step.
2. Update the `OUT_DIR` variable in the definition file to a temporary location where the ISO files can be/have been extracted to.
1. Build the image by running `apptainer build --fakeroot ANSYS-$VERSION-Fluent-Container.sif ANSYS-$VERSION-Fluent-Container.def` where `$VERSION` is `2025R1`, `2025R2`, etc.

To start Fluent run

```bash
apptainer exec --env ANSYSLMD_LICENSE_FILE=port@host ANSYS-$VERSION-Fluent-Container.sif fluent
```

### Building using EasyBuild

1. Put the nine ANSYS ISO files and `ANSYS-$VERSION-Fluent-Container.def` into the EasyBuild sourcepath.
2. Update `ANSYS-$VERSION-Fluent-Container.eb` to specify the license server in the `local_license_server` variable.
3. Make sure `apptainer` is available. There may be some fiddling of `osdependencies` or `depends_on` required.
4. Run `eb ANSYS-$VERSION-Fluent-Container.eb` to build and install the image with EasyBuild.

To start Fluent run

```bash
module load ANSYS/$VERSION-Fluent-Container
fluent
```

### Updating the container for a new ANSYS version

1. Download the ISO images for the new version, checking their md5sums.
2. Calculate the sha256sums of the ISO images.
3. Start with the 2025R2 `.def` and `.sif` files and replace `2025R2` with the current version.
4. In the `.def` file replace `252` with the current version shorthand (this can be found from the `*.dvd` file names in the ISO images).
5. Calculate the sha256sum of the `.def` file.
6. In the `.eb` file update the `checksums` with the newly calculated sha256sums.
