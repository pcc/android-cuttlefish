# Virtual Device for Android host-side utilities

This repository holds source for Debian packages that prepare a host to boot
[Cuttlefish](https://source.android.com/setup/create/cuttlefish), an Android
device that is designed to run on Google Compute Engine.

This package can be built directly with dpkg-buildpackage, but it is
designed to be built with:

    device/google/cuttlefish/tools/create_base_image.go

[Check out the AOSP tree](https://source.android.com/setup/build/downloading)
to obtain the script.

The Debian packages can be also built with the docker container whose Dockerfile
and build scripts are included in this repository. 

```
    ./build.sh --build_debs_only --rebuild_debs_verbose
```

The command will build the container, if needed, that builds the Debian packages,
and builds the Debian packages with the container. The resultant packages will be
located under the ```./out``` directory.
 
This repository also contains a Dockerfile that can be used to construct an
image for a privileged Docker container, which in turn can boot the cuttlefish
device.  Such a image allows one to develop for Cuttlefish without having to
install a number of packages directly on their host machine. For more details,
read the [BUILDING.md](BUILDING.md) file.
