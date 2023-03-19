# Grafana Source RPMs

Downloaded from [https://src.fedoraproject.org/rpms/grafana](https://src.fedoraproject.org/rpms/grafana).

## What is a source RPM

[https://blog.packagecloud.io/working-with-source-rpms](https://blog.packagecloud.io/working-with-source-rpms) quotes:

> A source RPM captures the source code and patches as they were at RPM build time.
>
> On RPM-based systems source RPMs are RPM files that contain a tarball of source code, patches, auxiliary files that are used during the build process, and a .spec file for generating the RPM.

## Extract the source RPM

From [https://unix.stackexchange.com/a/25802/544954](https://unix.stackexchange.com/a/25802/544954)

```shell
$ rpm2cpio grafana-7.5.15-4.fc36.src.rpm | cpio -idmv
```

## Recombining to get the RPM

Recombine the chunks

```shell
$ cd v7.5.15-4/
$ cat grafana-7.5.15-4.fc36.src.rpm.* > grafana-7.5.15-4.fc36.src.rpm
```

## Splitting when uploading the RPM

Split the src RPM into chunks of 50MB, because of Github's file limit of 100MB.

```shell
$ cd v7.5.15-4/
$ split -b 50MB -d grafana-7.5.15-4.fc36.src.rpm grafana-7.5.15-4.fc36.src.rpm.
```
