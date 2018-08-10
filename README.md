# dapper-dracut

## About
The Dapper Dracut package contains files necessary to build and install dracut, the tool used to build an initramfs image for kernels. This version ships a version of dracut which does not need to use the kernel crypto api, introduced in Linux 4.10. Dapper Secure Kernel Stable is kept at 4.9, and is missing this interface, so is incompatible with modern dracut versions. 

This repository maintains version 47 as shipped by Fedora 28 at commit https://src.fedoraproject.org/rpms/dracut/tree/3b5a03e5862e889e69df739d81b41fe413c57be9


## Building
To build this package, first install an RPM development chain:

```bash
$ sudo dnf install fedora-packager fedora-review

```

Next, setup rpmbuild directories with

```bash
$ rpmdev-setuptree
```
And place the file dapper-dracut.spec in the SPECS directory, and place all the other files in the SOURCES directory:
```bash
$ mv dapper-dracut.spec ~/rpmbuild/SPECS/
$ mv * ~/rpmbuild/SOURCES/
```

and finally, you can build RPMs and SRPMs with:
```bash
$ cd ~/rpmbuild/SPECS
$ sudo dnf builddep dapper-dracut.spec
$ rpmbuild -ba dapper-dracut.spec
```


